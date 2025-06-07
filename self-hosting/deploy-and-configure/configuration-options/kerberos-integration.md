# Kerberos 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/kerberos-integration/)
{% endhint %}

Kerberos 集成身份验证允许 Bitwarden 用户在外部 MSSQL 数据库中使用集成的 AD 身份验证。

{% hint style="info" %}
本指南假定您已经导出了所需的 keytab 文件，该文件将用于 Bitwarden 服务器上的域身份验证。
{% endhint %}

## keytab 文件 <a href="#keytab-file" id="keytab-file"></a>

Bitwarden 服务器使用导出的 `keytab` 文件来验证域名。

1、从 Windows 域控制器中输入以下代码示例（根据需要可能会有所不同）：

```
ktpass /princ bitwarden@<EXAMPLE.DOMAIN> /mapuser "bitwarden" /pass super_secure_password_here /out bitwarden.keytab /crypto all /ptype KRB5_NT_PRINCIPAL /mapop set
```

2、文件生成后，将文件复制到下一章节中的 Bitwarden 服务器位置。

## Bitwarden 配置 <a href="#bitwarden-configuration" id="bitwarden-configuration"></a>

接下来，创建 Bitwarden 配置：

1、创建 Kerberos 目录：

```bash
mkdir /opt/bitwarden/bwdata/kerberos
```

2、将两个文件放入该目录：

1. 上一章节生成的 `keytab` 文件
2. `krb5.conf` 文件（示例如下）

3、创建 `krb5.conf` 文件：

```bash
nano /opt/bitwarden/bwdata/kerberos/krb5.conf
```

[这里](https://assets.contentful.com/7rncvj1f8mw7/dfAMaYL2JmdC3j0i4ZTPO/304e3d038d3a9c8cd1cbdd505c57d7c0/Generic_example)是一个示例文件。

[这里](https://assets.contentful.com/7rncvj1f8mw7/6TdaNaNKfcxcmIc0PfBipR/74364f58e11b12f59e4aff49c3899db4/TEST)是一个示例 TEST 文件。

检查这些值是否与您自己的值一致，以及是否可以从 Bitwarden 服务器访问 `kdc` 和 `admin_server`。

{% hint style="info" %}
在 `krb5.config` 文件中使用 `ticket_lifetime` 和 `renew_lifetime` 变量设置票据的有效期和续期值。如果票据有效期和票据续期都已过期，则无法重新验证票据。有关其他信息，请参阅 [Kerberos 文档](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/conf_files/krb5_conf.html)。
{% endhint %}

## 更新 Bitwarden <a href="#update-bitwarden" id="update-bitwarden"></a>

### global.override.env <a href="#global.override.env" id="global.override.env"></a>

要更新 Bitwarden，必须在 `global.override.env` 文件中添加一个额外的环境变量。

1、访问 `global.override.env`：

```bash
nano ~/global.override.env/
```

2、在 `global.override.env` 中添加以下变量：

```systemd
globalSettings__kerberosUser=bitwarden
```

{% hint style="info" %}
该变量应为用于域身份验证的 AD 用户，且应与您的域用户匹配。
{% endhint %}

### SQL 连接字符串 <a href="#sql-connection-string" id="sql-connection-string"></a>

替换 SQL 连接字符串，指向外部数据库并使用集成身份验证。 更改 SQL 服务器主机名和数据库名：

```systemd
globalSettings__sqlServer__connectionString="Data Source=tcp:example-sql-server.example.domain,1433;Initial Catalog=vault;Persist Security Info=False;Integrated Security=true;Multiple Active Result Sets=False;Connect Timeout=30;Encrypt=True;Trust Server Certificate=True"
```

### Docker 更新 <a href="#docker-updates" id="docker-updates"></a>

完成前面的设置步骤后，主机操作系统上就应该存在此配置文件了。接下来，修改 Bitwarden 的 Docker Compose 配置，为相关容器添加额外的卷挂载。这将确保在更新和更改主 docker-compose 文件后，配置仍能保留。Compose 提供了一个 `override` 文件，可以将你的本地变更合并到标准的 Bitwarden 配置中。

1、创建 override 文件：

```bash
nano /opt/bitwarden/bwdata/docker/docker-compose.override.yml
```

2、标准配置包括以下内容：

```docker
services:
	admin:
		volumes:
			- ../kerberos:/etc/bitwarden/kerberos
	sso:
		volumes:
			- ../kerberos:/etc/bitwarden/kerberos		
	identity:
		volumes:
			- ../kerberos:/etc/bitwarden/kerberos		
	api:
		volumes:
			- ../kerberos:/etc/bitwarden/kerberos		
	events:
		volumes:
			- ../kerberos:/etc/bitwarden/kerberos		
	
```

3、如果使用 SCIM，还必须包括：

```docker
	scim:
		volumes:
			- ../kerberos:/etc/bitwarden/kerberos	
```

4、完成后，保存文件。

## 启动 Bitwarden <a href="#starting-bitwarden" id="starting-bitwarden"></a>

设置完成后，您就可以启动 Bitwarden 了。如果尚未重新启动 Bitwarden 容器，请在设置完成后重新启动它：

```bash
./bitwarden restart
```

`admin` 容器将填充新的外部 MSSQL 数据库。如果您在内置的 `mssql` 容器中存储了任何信息，则需要通过数据库备份和还原或导出/导入将其迁移到新的外部数据库。

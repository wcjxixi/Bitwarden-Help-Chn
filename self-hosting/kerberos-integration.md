# =Kerberos 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/kerberos-integration/)
{% endhint %}

Kerberos 集成身份验证允许 Bitwarden 用户在外部 MSSQL 数据库中使用集成的 AD 身份验证。

{% hint style="info" %}
本指南假定您已经导出了所需的 keytab 文件，该文件将用于 Bitwarden 服务器上的域身份验证。
{% endhint %}

## keytab 文件 <a href="#keytab-file" id="keytab-file"></a>

Bitwarden 服务器使用导出的 `keytab` 文件来验证域。

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

### SQL 连接字符串 <a href="#sql-connection-string" id="sql-connection-string"></a>

### Docker 更新 <a href="#docker-updates" id="docker-updates"></a>

## 启动 Bitwarden <a href="#starting-bitwarden" id="starting-bitwarden"></a>

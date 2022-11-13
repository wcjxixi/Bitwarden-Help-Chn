# 备份您的托管数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/backup-on-premise/)
{% endhint %}

自托管 Bitwarden 时，您有责任实施自己的备份过程，以确保数据安全。

## 关于托管数据 <a href="#about-hosted-data" id="about-hosted-data"></a>

Bitwarden 的 Docker 容器使用卷映射来持久化主机上的所有重要数据，这意味着停止你的容器不会删除任何数据。另一方面，Docker 容器要被认为是短暂的，不持久化数据或状态。

所有的 Bitwarden 数据都存储在主机上相对于你安装 Bitwarden 的位置的 `./bwdata` 目录中。更多信息，请参阅[安装和部署](install-deploy-guides/install-and-deploy-linux.md)。

## 备份托管数据 <a href="#backup-hosted-data" id="backup-hosted-data"></a>

建议您备份并保护整个 `./bwdata` 目录。如果发生数据丢失，则需要此目录中包含的全部或部分数据来还原您的实例。

定期备份的 `./bwdata` 中特别重要的部分包括：

* `./bwdata/env` - 实例的环境变量，包括数据库和证书密码
* `./bwdata/core/attachments` - 实例的密码库项目的附件
* `./bwdata/mssql/data` - 实例的数据库数据

Bitwarden 将在运行时自动对 mssql 数据库容器进行夜间备份。

### 夜间数据库备份 <a href="#nightly-database-backups" id="nightly-database-backups"></a>

Bitwarden 会自动对 `mssql` 容器数据库进行夜间备份。备份保存在 `./bwdata/mssql/backups` 目录中并将保留 30 天。

如果发生数据丢失，您可以使用 `./bwdata/mssql/backups` 来还原其中一个夜间备份。

### 恢复夜间备份 <a href="#restore-a-nightly-backup" id="restore-a-nightly-backup"></a>

如果发生数据丢失，请完成以下步骤以恢复夜间备份。

1、从  `global.override.env` 中查找 `globalSettings__sqlServer__connectionString=...Password=` 的值以获取您的数据库密码。

2、使用 `docker ps` 命令标识 `mssql` 容器的容器 ID。

3、运行以下命令以为您的 `mssql` docker 容器打开一个 bash 会话：

```shell
docker exec -it bitwarden-mssql /bin/bash
```

现在，您的命令提示符应与 `bitwarden-mssql` 容器的已标识容器 ID 相匹配。

4、在容器中，找到要还原的备份文件。

{% hint style="info" %}
容器中的备份目录是从主机目录进行卷映射的。主机上的 `./bwdata/mssql/backups` 映射到容器中的 `etc/bitwarden/mssql/backups`。
{% endhint %}

例如，文件 `/etc/bitwarden/mssql/backups/vault_FULL_20201208_003243.BAK` 是 2020 年 12 月 8 日上午12:32 生成的备份。

5、使用以下命令启动 `sqlcmd` 实用程序：

```shell
/opt/mssql-tools/bin/sqlcmd -S localhost -U <sa> -P <sa-password>
```

其中的 `<sa>` 和 `<sa-password>` 分别匹配  `global.override.env` 中的 `User=` 和 `Password=` 的值。

6、在 `sqlcmd` 实用程序中，有两种备份选项：

* **离线备份**（_首选_）

运行下面的 SQL 命令：

```sql
1> use master
2> GO
1> alter database vault set offline with rollback immediate
2> GO
1> restore database vault from disk='/etc/bitwarden/mssql/backups/vault_FULL_{Backup File Name}.BAK' with replace
2> GO
​1> alter database vault set online
2> GO
1> exit
```

重启您的 Bitwarden 实例以完成恢复过程。

* **在线备份**

运行下面的 SQL 命令：

```sql
1> RESTORE DATABASE vault FROM DISK = '/etc/bitwarden/mssql/backups/vault_FULL_20200302_235901.BAK' WITH REPLACE
2> GO
```

重启您的 Bitwarden 实例以完成恢复过程。

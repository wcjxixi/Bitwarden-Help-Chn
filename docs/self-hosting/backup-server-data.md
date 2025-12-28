# 备份服务器数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/backup-on-premise/)
{% endhint %}

自托管 Bitwarden 时，您有责任实施自己的备份过程，以确保数据安全。尽管执行此操作所需的步骤取决于您的部署方式，但在所有情况下都建议您：

* 手动定期备份重要数据，包括配置数据、证书数据等。
* 确保执行自动重复的数据库备份。

{% hint style="success" %}
在使用内置数据库的 **Docker** 部署中，只要 `mssql` 容器正在运行，夜间备份就会运行。在 **Helm** 部署中，您需要在集群外部安排作业或在集群内创建 CronJob 对象，Bitwarden 提供了示例来帮助指导您的方法。
{% endhint %}

{% tabs %}
{% tab title="Docker" %}
## 手动备份 <a href="#manual-backups" id="manual-backups"></a>

Bitwarden 将在夜间自动备份 `mssql` 数据库容器（见下文），但是对于最完整的灾难恢复 (DR) 计划，您应该手动备份并确保整个 `./bwdata` 目录的安全。

需要定期备份的 `./bwdata` 中特别重要的部分包括：

* `./bwdata/env` - 实例的环境变量，包括数据库和证书密码
* `./bwdata/core/attachments` - 实例的密码库项目的附件
* `./bwdata/mssql/data` - 实例的数据库数据
* `./bwdata/core/aspnet-dataprotection` - 框架级数据保护，包括身份验证令牌和部分数据库列。

您还可以使用以下命令随时手动触发 `mssql` 数据库容器的备份：

```bash
docker exec -i bitwarden-mssql /backup-db.sh
```

## 自动数据库备份 <a href="#automatic-database-backups" id="automatic-database-backups"></a>

只要容器正在运行，Bitwarden 会自动对 `mssql` 容器数据库进行夜间备份。备份保存在 `./bwdata/mssql/backups` 目录中并将保留 30 天。

### 恢复数据库备份 <a href="#restore-a-database-backup" id="restore-a-database-backup"></a>

如果发生数据丢失，您可以使用 `./bwdata/mssql/backups` 来恢复夜间备份。请完成以下步骤来恢复夜间备份：

1、从  `global.override.env` 中查找 `globalSettings__sqlServer__connectionString=...Password=` 的值以获取您的数据库密码。

2、使用 `docker ps` 命令标识 `mssql` 容器的容器 ID。

3、运行以下命令为您的 `mssql` docker 容器打开一个 bash 会话：

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

* **离线备份**（首选）

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
{% endtab %}

{% tab title="Helm" %}
## 手动备份 <a href="#manual-backups" id="manual-backups"></a>

Bitwarden 提供了可用于定期备份数据库的示例作业（见下文），但是对于最完整的灾难恢复 (DR) 计划，您应该手动备份并确保更广泛的服务器数据的安全。

需要定期备份的特别重要的数据包括：

* 您的图表的 `my-values.yaml` 文件。
* 您的 [Kubernetes Secrets 对象](deploy-and-configure/helm/self-host-with-helm.md#create-a-secret-object)（通常为 `.yaml` 文件）。
* 为以下目的设置的任何持久卷 (PVC)：
  * `dataprotection`&#x20;
  * `attachments`&#x20;
  * `licenses`

## 定期数据库备份 <a href="#recurring-database-backups" id="recurring-database-backups"></a>

有多种方法可以为 Bitwarden 部署安排定期数据库备份。Bitwarden Helm Charts 存储库包含[一个用于备份预打包的 SQL 容器的示例](https://github.com/bitwarden/helm-charts/tree/main/examples)，其中包括：

* 创建一个 Kubernetes 作业对象 (`backup-job.yaml`)，该对象通过 Kubernetes Secrets 建立与数据库的连接，执行备份，并将生成的 `Vault.bak` 文件存储到持久卷 (PVC)，同时保留以前的备份。
* 创建一个 Bash 脚本 (`db-backup.sh`)，供集群外部的任务调度程序使用，它将运行 Kubernetes 作业并实时监控它。

## 恢复备份 <a href="#restoring-backups" id="restoring-backups"></a>

要恢复备份，请使用备份的 `my-values` 文件和 Kubernetes Secret 对象 `.yaml` 文件部署新的 Bitwarden Helm 安装。重新安装图表后，重新附加手动备份的持久卷 (PVC) 和 `Vault.bak` 数据库备份。
{% endtab %}
{% endtabs %}

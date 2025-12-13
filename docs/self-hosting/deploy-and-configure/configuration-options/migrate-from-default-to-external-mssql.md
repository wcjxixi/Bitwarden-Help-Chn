# 从默认迁移到外部 MSSQL

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/migrate-from-default-to-external-mssql/)
{% endhint %}

本指南将指导您完成将自托管 Bitwarden 实例从默认的 MSSQL Express 数据库迁移到[外部 MSSQL 数据库](connect-to-an-external-mssql-database.md)的过程。这个过程：

* 要求 Bitwarden 服务器停机。
* 要求同时对 Bitwarden 服务器和数据库具有管理访问权限。
* 要求您要迁移到的外部数据库是 MSSQL Server 2022。
* 要求可以从 Bitwarden 主机访问您要迁移到的外部数据库。

## 在 Docker 部署中迁移 <a href="#migrate-in-docker-deployments" id="migrate-in-docker-deployments"></a>

Docker 部署场景下，从默认的 MSSQL Express 数据库迁移到外部数据库，需要完成以下流程：

1、创建数据库的[手动备份](../../backup-server-data.md)：

```shellscript
docker exec -i bitwarden-mssql /backup-db.sh
```

容器中的备份目录卷映射到主机，因此您的备份将作为 `./bwdata/mssql/backups` 中的 `.BAK` 文件提供。

2、停止所有 Bitwarden 容器以确保迁移过程中数据的一致性：

```shellscript
# Bash
./bitwarden.sh stop

# PowerShell
.\bitwarden.ps1 -stop
```

3、将 `.BAK` 文件上传到可以导入到新的外部 MSSQL 数据库的位置。上传方法会因环境而异，但常用方法包括使用 SCP 或将文件复制到新数据库服务器上挂载的网络共享文件夹。

4、将 `.BAK` 文件还原到新的外部 MSSQL 数据库。还原方法会因环境而异，但常用方法包括使用 SMSS、T-SQL 或 sqlcmd。

5、确认 `sa` 账户已激活，并且您可以在新的外部 MSSQL 数据库中访问该账户的密码，因为该密码将用于应用程序访问还原后的数据库的连接字符串，以避免任何用户映射问题。

6、在环境变量文件 (`global.override.env`) 中，至少更新 Bitwarden 服务器使用的数据库连接字符串：

```systemd
globalSettings__sqlServer__connectionString="Data Source=your-sql-server.example.com,1433;Initial Catalog=database_name;User ID=sa;Password=sa_user_password;Encrypt=True;TrustServerCertificate=False;"
```

7、重新启动您的 Bitwarden 容器：

```shellscript
# Bash
./bitwarden.sh start

# PowerShell
.\bitwarden.ps1 -start
```

启动后：

* 通过登录然后创建一个测试项目，来验证服务器是否正常运行。
* 验证预期的密码库项目和用户账户是否已成功迁移。

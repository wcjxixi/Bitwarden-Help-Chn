# 数据库选项

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/database-options/)
{% endhint %}

## 服务器部署的默认数据库 <a href="#default-database-for-server-deployments" id="default-database-for-server-deployments"></a>

除统一 (Unified) 部署外，所有 Bitwarden 自托管服务器部署默认使用 MSSQL Express 镜像。这将您的加密密码库数据与应用程序容器一起部署，并通过确保更新、维护和备份与代码的其余部分同时进行，从而简化部署流程。此默认数据库不需要额外许可，并已按照 Bitwarden 标准预配置，以安全存储并自动备份密码库数据（了解更多）。

### 服务器部署使用外部数据库 <a href="#using-an-external-database-for-server-deployments" id="using-an-external-database-for-server-deployments"></a>

在默认使用 MSSQL Express 镜像的自托管服务器部署中，使用该容器是可选的。为了实现高可用性或利用现有基础设施，客户可以连接到外部 MSSQL 服务器或集群（了解更多），版本需为 2019 或更高版本，但建议使用 2022 或更高版本。

## 统一部署的数据库 <a href="#databases-for-unified-deployments" id="databases-for-unified-deployments"></a>

Bitwarden 统一 (Unified) 自托管部署不附带内置数据库，但可以连接到现有的 MySQL/MariaDB、MSSQL、SQLite 或 PostgreSQL 数据库（了解更多）。由于该数据库不与应用程序容器不在同一位置，因此从基础设施角度来看，数据库的维护（包括更新、维护和备份）需要单独管理。

## 可选的数据库任务 <a href="#optional-database-jobs" id="optional-database-jobs"></a>

### 数据库准备 <a href="#database-preparation" id="database-preparation"></a>

在非统一自托管部署中，Bitwarden 会检查构造的连接字符串中指定的数据库是否存在，如果不存在，则会创建它。此任务需要已配置的 SQL 用户在数据库服务器中具有管理员权限。权限不足将导致此任务失败。如果您正在部署自己的外部数据库，请通过在 `global.override.env` 文件中设置以下环境变量来禁用此部署步骤：

```bash
globalSettings__sqlServer__skipDatabasePreparation=true
```

### 数据库维护 <a href="#database-maintenance" id="database-maintenance"></a>

在所有自托管部署中，包括统一 (Unified) 部署，Bitwarden 会在数据库上运行计划任务，以执行常规维护，例如计算数据库统计信息和构建索引。这些任务需要已配置的 SQL 用户在数据库服务器中具有管理员权限。权限不足将导致此任务失败，并且失败信息会被记录到 `admin` 容器日志中。如果您希望以单独的用户身份运行这些维护任务，请通过在 `global.override.env` 文件中设置以下环境变量来禁用此行为：

```bash
globalSettings__sqlServer__disableDatabaseMaintenanceJobs=true
```

{% hint style="info" %}
如果您禁用了数据库维护任务，请定期手动检查数据库清理和索引创建。
{% endhint %}

# 连接到外部 MSSQL 数据库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/external-db/)
{% endhint %}

默认情况下，Bitwarden 的自托管实例将使用作为安装设置的正常部分而创建的 Microsoft SQL Server（MSSQL）数据库，但您也可以将 Bi​​twarden 配置为使用外部 MSSQL 数据库。

{% hint style="info" %}
目前，自托管 Bitwarden 实例支持 MSSQL 2017，但 Bitwarden 推荐的**最低** SQL 版本是 Server 2019。

Bitwarden **支持并推荐尽可能使用 SQL Server 2022**。由于对 Server 2017 的主流支持已于 [2022 年 10 月](https://learn.microsoft.com/zh-cn/lifecycle/products/sql-server-2017)结束，如果 Bitwarden 实现了特定 SQL Server 版本上不支持的功能，则将在此处和特定版本的**发布说明**中注明对特定 SQL Server 版本支持的弃用。
{% endhint %}

## 设置 <a href="#setup" id="setup"></a>

要使用外部数据库设置您的自托管实例：

1、创建一个新 MSSQL 数据库。

2、（**推荐**）为您的 `vault` 数据库创建一个专用 DBO。

3、作为 Bitwarden 服务器管理员，在编辑器中打开 `global.override.env` 文件：

```shell
nano bwdata/env/global.override.env
```

4、使用如下信息编辑 `globalSettings__sqlServer__connectionString=` 的值：

* 使用您的 MSSQL 服务器名称替换 `"Data Source=tcp:mssql,1443";` 中的值，例如 `"Data Source=protocol:server_url,port"`。
* 使用您的数据库名称替换 `Initial Catalog=vault` 中的 `vault`。
* 使用您的 DBO 用户 ID 替换 `User ID=sa;` 的值。
* 使用您的 DBO 密码替换 `Password=<default_pw>;` 的值。

5、将更改保存到 `global.override.env`。

6、启动 Bitwarden（`./bitwarden.sh start`）。

完成上述步骤后，您可以通过网页密码库创建一个新用户并查询外部 `vault` 数据库来测试连通性。

## 验证服务器证书 <a href="#validate-a-server-certificate" id="validate-a-server-certificate"></a>

如果您需要 Bitwarden 验证您的 MSSQL 数据库服务器的证书，请将证书挂载到您自托管的 Bitwarden 服务器的容器中。按如下操作：

1. 将您的 CA 根证书复制到 `./bwdata/ca-certificates`。
2. 运行 `./bitwarden.sh restart` 命令将证书应用到您的容器并重新启动服务器。

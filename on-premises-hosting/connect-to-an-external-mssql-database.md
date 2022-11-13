# 连接到外部 MSSQL 数据库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/external-db/)
{% endhint %}

默认情况下，Bitwarden 的自托管实例将使用作为安装设置的正常部分而创建的 Microsoft SQL Server（MSSQL）数据库，但您可以将 Bi​​twarden 配置为使用外部 MSSQL 数据库。

{% hint style="info" %}
目前，Bitwarden 的自托管安装仅支持 MSSQL 数据库。请继续关注此话题的未来更新。
{% endhint %}

## 设置 <a href="#setup" id="setup"></a>

要使用外部数据库设置您的自托管实例：

1、创建一个名为 `vault` 的新 MSSQL 数据库。

{% hint style="warning" %}
**必须**使用 `vault` 名称。其他数据库名称将会导致迁移失败。
{% endhint %}

2、（**推荐**）为您的 `vault` 数据库创建一个专用 DBO。

3、作为 Bitwarden 服务器管理员，在编辑器中打开 `global.override.env` 文件：

```shell
nano bwdata/env/global.override.env
```

4、使用如下信息编辑 `globalSettings__sqlServer__connectionString=` 的值：

* 使用您的 MSSQL 服务器名称替换 `"Data Source=tcp:mssql,1443";` 中的值，比如 `"Data Source=protocol:server_url,port"`。
* 使用您的 DBO 用户 ID 替换 `User ID=sa;` 的值。
* 使用您的 DBO 密码替换 `Password=<default_pw>;` 的值。

5、将更改保存到 `global.override.env`。

6、启动 Bitwarden（`./bitwarden.sh start`）。

完成上述步骤后，您可以通过网页密码库创建新用户并查询外部 `vault` 数据库来测试连通性。

## 验证服务器证书 <a href="#validate-a-server-certificate" id="validate-a-server-certificate"></a>

如果您需要 Bitwarden 验证您的 MSSQL 数据库服务器的证书，请将证书挂载到您自托管的 Bitwarden 服务器的容器中。按如下操作：

1. 将您的 CA 根证书复制到 `./bwdata/ca-certificates`。
2. 运行 `./bitwarden.sh restart` 命令将证书应用到您的容器并重新启动服务器。

# 连接到外部 MSSQL 数据库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/external-db/)
{% endhint %}

默认情况下，Bitwarden 的自托管实例将使用作为[安装设置](../docker/linux-standard-deployment.md)的正常部分而创建的 Microsoft SQL Server (MSSQL) 数据库，但您也可以将 Bi​​twarden 配置为使用外部 MSSQL 数据库。

{% hint style="info" %}
Bitwarden **仅支持并推荐 SQL Server 2022**。了解 [Windows](https://learn.microsoft.com/zh-cn/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2022?view=sql-server-ver17) 和 [Linux](https://learn.microsoft.com/zh-cn/sql/linux/sql-server-linux-setup?view=sql-server-ver16#supported-platforms) 上 SQL Server 的系统要求。

目前，Bitwarden 不支持 SQL Server 2025，并且对 Server 2017 和 Server 2019 的主流支持结束。如果 Bitwarden 实现了特定 SQL Server 版本上不可用的功能，则此处以及给定版本的[发行记录](../../../release-notes.md)中将注明不再支持特定 SQL Server 版本。
{% endhint %}

## 设置外部数据库 <a href="#setup-external-database" id="setup-external-database"></a>

要设置您的自托管实例使用外部数据库：

{% tabs %}
{% tab title="Docker" %}
1、创建一个新的 MSSQL 数据库。

2、（**推荐**）为您的数据库创建一个专用 DBO。

3、在您服务器的 `global.override.env` 文件中，使用如下信息编辑 `globalSettings__sqlServer__connectionString=` 的值：

* 使用您的 MSSQL 服务器名称替换 `"Data Source=tcp:mssql,1443";` 中的值，例如 `"Data Source=protocol:server_url,port"`。
* 使用您的数据库名称替换 `Initial Catalog=vault` 中的 `vault`。
* 使用您的 DBO 用户 ID 替换 `User ID=sa;` 中的 `sa`
* 使用您的 DBO 密码替换 `Password=<default_pw>;` 中的 `<default_pw>`。

4、将更改保存到 `global.override.env`。

5、启动 Bitwarden（`./bitwarden.sh start`）。

完成上述步骤后，您可以通过网页密码库创建一个新用户并查询外部 `vault` 数据库来测试连通性。
{% endtab %}

{% tab title="Helm" %}
1、创建一个新的 MSSQL 数据库。

2、（**推荐**）为您的数据库创建专用的 DBO。

3、在 `my-values.yaml` 配置文件中，设置值 `database.enabled: false` 以停止部署包含的 SQL pod。

4、在用于部署的 Kubernetes Secrets 对象中，使用以下信息设置 `globalSettings__sqlServer__connectionString=` 值：

{% hint style="info" %}
用于配置机密对象的方法可能取决于您的部署，例如 [AWS 部署](../helm/aws-eks-deployment.md)和 [Azure 部署](../helm/azure-aks-deployment.md)可能使用 CSI SecretProviderClass 来执行此操作。
{% endhint %}

* `Data Source=tcp:<SERVERNAME>,1433`，其中 `<SERVERNAME>` 是您的 MSSQL 服务器的名称。
* `Initial Catalog=<VAULT>`，其中 `<VAULT>` 是您的数据库名称。
* `Persist Security Info=False`。
* `User ID=<USER>`，其中 `<USER>` 是您的 DBO 用户 ID。
* `Password=<PASSWORD>`，其中 `<ASSWORD>` 是您的 DBO 密码。
* `Multiple Active Result Sets=False`。
* `Connect Timeout=30`。
* `Encrypt=True`。
* `Trust Server Certificate=true`。如果您要求 Bitwarden 服务器验证您的 MSSQL 服务器的证书，则可以将该值设置为 `false`。
{% endtab %}
{% endtabs %}

## 验证服务器证书 <a href="#validate-a-server-certificate" id="validate-a-server-certificate"></a>

要配置 Bitwarden 验证您的 MSSQL 数据库服务器的证书：

{% tabs %}
{% tab title="Docker" %}
1. 将您的 CA 根证书复制到 `./bwdata/ca-certificates`。
2. 运行 `./bitwarden.sh restart` 命令将证书应用到您的容器然后重启服务器。
{% endtab %}

{% tab title="Helm" %}
1、在 `my-values.yaml` 配置文件中，设置值 `caCertificate.enabled: true`。

2、创建一个包含您的证书文件的 ConfigMap 对象。最简单的方法是将 `preInstall` RawManifest 添加到 `my-values.yaml` 文件中，如下例所示：

```yml
rawManifests:
  preInstall:
  - kind: ConfigMap
    apiVersion: v1
    metadata:
      name: cacert
    data:
      rootca.crt: |
        -----BEGIN CERTIFICATE-----
         ...
        -----END CERTIFICATE-----
  postInstall:
```
{% endtab %}
{% endtabs %}

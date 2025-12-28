# 部署 Key Connector

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/deploy-key-connector/)
{% endhint %}

{% hint style="info" %}
Bitwarden 建议将[信任设备解密](../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md)作为 Key Connector 的替代选项，这样可以方便成员在无需主密码的情况下登录，并且不需要部署或管理密钥服务器。
{% endhint %}

本文将引导您完成在现有自托管环境中启用和配置 Key Connector 的过程。**在继续之前**，请仔细阅读[关于 Key Connector](about-key-connector.md) 一文，以确保完全了解 Key Connector 是什么、它的工作原理以及实施的影响。

Bitwarden 支持部署一个 Key Connector，供一个组织用于自托管实例。

## 要求 <a href="#requirements" id="requirements"></a>

{% hint style="danger" %}
加密密钥的管理非常敏感，**仅建议拥有可以安全支持部署和管理密钥服务器的团队和基础架构的企业使用**。
{% endhint %}

要使用 Key Connector，您必须：

* [拥有一个企业组织](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#enterprise-organizations)
* [拥有一个自托管的 Bitwarden 服务器](../)
* [拥有一个活跃的 SSO 实施](../../admin-console/login-with-sso/about-sso.md)
* [激活单一组织和单点登录策略](../../admin-console/oversight-visibility/enterprise-policies.md)

如果您的组织满足或能够满足这些要求，包括拥有可以支持密钥服务器管理的团队和基础设施，请[联系我们](https://bitwarden.com/contact)，我们将为您激活 Key Connector。

## 设置 & 部署 Key Connector <a href="#setup-and-deploy-key-connector" id="setup-and-deploy-key-connector"></a>

**您就 Key Connector 与我们联系后**，我们将与您主动联系以开启一个 Key Connector 相关的讨论。本文后续步骤必须与 Bitwarden 客户成功及实施专家协作完成。

### 获取新的许可证文件 <a href="#obtain-new-license-file" id="obtain-new-license-file"></a>

您就 Key Connector 与我们联系后，客户成功与实施团队的一名成员将为您的组织生成一个启用了 Key Connector 的许可证文件。当您的 Bitwarden 合作者指示您准备就绪时，请完成以下步骤以获取新的许可证：

1. 打开您的 Bitwarden Cloud 网页密码库，然后导航到您组织的**设置** → **订阅**界面。
2. 选择**下载许可证**按钮。
3. 当出现提示时，输入用于安装自托管服务器的安装 ID，然后选择**提交**。如果您不知道自己的安装 ID，可以从 `./bwdata/env/global.override.env` 中获取它。

不会立即需要您的许可证文件，但您需要[在后面的步骤中](deploy-key-connector.md#activate-key-connector)将其上传到您的自托管服务器。

### 初始化 Key Connector <a href="#initialize-key-connector" id="initialize-key-connector"></a>

为 Key Connector 准备 Bitwarden 服务器：

1、至少保存一个 `.bwdata/mssql` 的[备份](../backup-server-data.md)。使用 Key Connector 后，建议您获取一个之前的 Key Connector 备份映像的访问权限，以防出现问题。

{% hint style="info" %}
如果您使用的是[外部 MSSQL 数据库](../deploy-and-configure/configuration-options/connect-to-an-external-mssql-database.md)，请以适合您的实施方式备份您的数据库。
{% endhint %}

2、更新您的自托管 Bitwarden 安装以获取最新的更改：

```bash
./bitwarden.sh update
```

3、编辑 `.bwdata/config.yml` 文件并通过将 `enable_key_connector` 切换为 `true` 来启用密钥连接器。

```bash
nano bwdata/config.yml
```

4、重建您的自托管 Bitwarden 安装：

```bash
./bitwarden.sh rebuild
```

5、再次更新您的自托管 Bitwarden 安装以应用更改：

```
./bitwarden.sh update
```

### 配置 Key Connector <a href="#configure-key-connector" id="configure-key-connector"></a>

要配置 Key Connector：

1、编辑随 `./bitwarden.sh update` 一起下载的 `.bwdata/env/key-connector.override.env` 文件。

```bash
nano bwdata/env/key-connector.override.env
```

{% hint style="danger" %}
此文件将被预先填入默认值，以启动一个功能性的本地 Key Connector 设置，**但不建议在生产环境中使用这些默认值**。
{% endhint %}

2、在 `key-connector.override.env` 中，您需要为以下内容指定值：

* [端点](deploy-key-connector.md#endpoints)：Key Connector 可以与之通信的 Bitwarden 端点。
* [数据库](deploy-key-connector.md#database)：用于 Key Connector 存储和检索用户密钥的地方。
* [RSA 密钥对](deploy-key-connector.md#rsa-key-pair)：Key Connector 访问 RSA 密钥对以保护静态用户密钥。

#### 端点 <a href="#endpoints" id="endpoints"></a>

自动设置将基于您的安装配置填充端点的值，但还是建议您确认 `key-connector.override.env` 中的以下值对于您的设置是准确的：

```systemd
keyConnectorSettings__webVaultUri=https://your.bitwarden.domain.com
keyConnectorSettings__identityServerUri=https://your.bitwarden.domain.com/identity/
```

#### 数据库 <a href="#database" id="database"></a>

Key Connector 必须访问一个为您的组织成员存储已加密用户密钥的数据库。创建一个安全数据库来存储已加密的用户密钥，并将 `key-connector.override.env` 中 `keyConnectorSettings__database__` 的默认值替换为所选数据库的**要求的值**列中指定的值：

{% hint style="danger" %}
目前**不支持**从一个数据库迁移到另一个数据库。无论您选择哪个提供程序，请为数据库**实施一个频繁的自动备份计划**。
{% endhint %}

<table><thead><tr><th width="150">数据库</th><th>要求的值</th></tr></thead><tbody><tr><td>Local JSON（<strong>默认</strong>）</td><td><strong>不建议用于测试之外的其他场景。</strong><br><br><code>keyConnectorSettings__database__provider=json</code><br><code>keyConnectorSettings__database__jsonFilePath={File_Path}</code></td></tr><tr><td>Microsoft SQL Server</td><td><code>keyConnectorSettings__database__provider=sqlserver</code><br><code>keyConnectorSettings__database__sqlServerConnectionString={Connection_String}</code><br><br><a href="https://docs.microsoft.com/zh-cn/sql/connect/ado-net/connection-string-syntax?view=sql-server-ver15">了解如何格式化 MSSQL 连接字符串</a></td></tr><tr><td>PostgreSQL</td><td><code>keyConnectorSettings__database__provider=postgresql</code><br><code>keyConnectorSettings__database__postgreSqlConnectionString={Connection_String}</code><br><br><a href="https://www.npgsql.org/doc/connection-string-parameters.html">了解如何格式化 PostgreSQL 连接字符串</a></td></tr><tr><td>MySQL/MariaDB</td><td><code>keyConnectorSettings__database__provider=mysql</code><br><code>keyConnectorSettings__database__mySqlConnectionString={Connection_String}</code><br><br><a href="https://dev.mysql.com/doc/connector-net/en/connector-net-connections-string.html">了解如何格式化 MySQL 连接字符串</a></td></tr><tr><td>MongoDB</td><td><code>keyConnectorSettings__database__provider=mongo</code><br><code>keyConnectorSettings__database__mongoConnectionString={Connection_String}</code><br><code>keyConnectorSettings__database__mongoDatabaseName={DatabaseName}</code><br><br><a href="https://docs.mongodb.com/manual/reference/connection-string/">了解如何格式化 MongoDB 连接字符串</a></td></tr></tbody></table>

#### RSA 密钥对 <a href="#rsa-key-pair" id="rsa-key-pair"></a>

Key Connector 使用 RSA 密钥对来保护静态用户密钥。创建一个密钥对并将 `key-connector.override.env` 中 `keyConnectorSettings__rsaKey__` 和 `keyConnectorSettings__certificate__` 的默认值替换为您选择的实施所要求的值。

{% hint style="success" %}
RSA 密钥对的长度**必须至少**为 2048 位。
{% endhint %}

通常，您的选项包括授予 Key Connector 对包含密钥对的 X509 **证书**的访问权限，或授予 Key Connector 访问**密钥对**的直接访问权限：

{% tabs %}
{% tab title="证书" %}
要使用包含 RSA 密钥对的 X509 证书，请根据您的证书的存储位置指定所需的值（参阅**文件系统**、**操作系统证书存储**等）：

{% hint style="success" %}
证书**必须**作为 PKCS12 `.pfx` 文件提供，例如：

```bash
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout bwkc.key -out bwkc.crt -subj "/CN=Bitwarden Key Connector" -days 36500

openssl pkcs12 -export -out ./bwkc.pfx -inkey bwkc.key -in bwkc.crt -passout pass:{Password}
```

在所有证书实现中，您都需要此示例中显示的 `CN` 值。
{% endhint %}

### 文件系统（默认） <a href="#filesystem-default" id="filesystem-default"></a>

如果证书存储在运行 Key Connector 的机器的文件系统上，请指定以下值：

{% hint style="info" %}
默认情况下，Key Connector 密钥连接器将被配置一个 `.pfx` 文件，此文件位于 `etc/bitwarden/key-connector/bwkc.pfx`，拥有一个已生成的密码。**不建议**企业实现使用这些默认值。
{% endhint %}

```systemd
keyConnectorSettings__rsaKey__provider=certificate
keyConnectorSettings__certificate__provider=filesystem
keyConnectorSettings__certificate__filesystemPath={Certificate_Path}
keyConnectorSettings__certificate__filesystemPassword={Certificate_Password}
```

### Azure Blob **Storage** <a href="#azure-blob-storage" id="azure-blob-storage"></a>

如果证书被上传到 Azure Blob Storage 中，请指定以下值：

```systemd
keyConnectorSettings__rsaKey__provider=certificate
keyConnectorSettings__certificate__provider=azurestorage
keyConnectorSettings__certificate__azureStorageConnectionString={Connection_String}
keyConnectorSettings__certificate__azureStorageContainer={Container_Name}
keyConnectorSettings__certificate__azureStorageFileName={File_Name}
keyConnectorSettings__certificate__azureStorageFilePassword={File_Password}
```

将 `azureStorageConnectionString` 设置为可在 Azure 门户中从存储账户的 **Shared access signature** (SAS) （共享访问签名）页面生成的 **Connection string**（连接字符串）。SAS 必须具备：

* 允许的服务：Blob 和文件
* 允许的资源类型：服务、容器和对象
* 允许的权限：读取、写入和列举
* 允许的 blob 索引权限：读取/写入和筛选

### Azure **Key Vault** <a href="#azure-key-vault" id="azure-key-vault"></a>

如果证书被存储在 Azure Key Vault 中，请指定以下值：

{% hint style="info" %}
要使用 Azure Key Vault 存储您的 `.pfx` 证书，您需要创建一个活动目录**应用程序注册**。此应用程序注册必须：

* 授予委派 API 权限以访问 Azure Key Vault&#x20;
* 拥有一个已生成的客户端密码以允许被 Key Connector 访问
{% endhint %}

```systemd
keyConnectorSettings__certificate__provider=azurekv
keyConnectorSettings__certificate__azureKeyvaultUri={Vault_URI}
keyConnectorSettings__certificate__azureKeyvaultCertificateName={Certificate_Name}
keyConnectorSettings__certificate__azureKeyvaultAdTenantId={ActiveDirectory_TenantId}
keyConnectorSettings__certificate__azureKeyvaultAdAppId={AppRegistration_ApplicationId}
keyConnectorSettings__certificate__azureKeyvaultAdSecret={AppRegistration_ClientSecretValue}
```

### Hashicorp **Vault** <a href="#hashicorp-vault" id="hashicorp-vault"></a>

如果证书被存储在 Hashicorp Vault 中，请指定以下值：

{% hint style="info" %}
Key Connector 与 Hashicorp Vault KV2 存储引擎集成。根据此选项卡的顶部，证书文件应采用 PKCS12 格式，并以 Base64 编码存储为密码库中命名密钥的值。如果遵循 KV2 存储引擎的密码库 教程，除非另有指定，否则密钥名称可能是 `file`。
{% endhint %}

```systemd
keyConnectorSettings__rsaKey__provider=certificate
keyConnectorSettings__certificate__provider=vault
keyConnectorSettings__certificate__vaultServerUri={Server_URI}
keyConnectorSettings__certificate__vaultToken={Token}
keyConnectorSettings__certificate__vaultSecretMountPoint={Secret_MountPoint}
keyConnectorSettings__certificate__vaultSecretPath={Secret_Path}
keyConnectorSettings__certificate__vaultSecretDataKey={Secret_DataKey}
keyConnectorSettings__certificate__vaultSecretFilePassword={Secret_FilePassword}
```
{% endtab %}

{% tab title="云密钥对" %}
要使用云提供商或物理设备存储 RSA 2048 密钥对，请根据您选择的实施指定所需的值（请参阅 **Azure Key Vault**、**Google Cloud Key Management** 等）：

### Azure Key Vault

如果您使用 Azure Key Vault 来存储 RSA 2048 密钥对，请指定以下值：

{% hint style="info" %}
要使用 Azure Key Vault 存储您的 RSA 2048 密钥，您需要创建一个活动目录**应用程序注册**。此应用程序注册必须：

* 授予委派 API 权限以访问 Azure Key Vault&#x20;
* 拥有一个已生成的客户端密码以允许被 Key Connector 访问
{% endhint %}

```systemd
keyConnectorSettings__rsaKey__provider=azurekv
keyConnectorSettings__rsaKey__azureKeyvaultUri={Vault_URI}
keyConnectorSettings__rsaKey__azureKeyvaultKeyName={Key_Name}
keyConnectorSettings__rsaKey__azureKeyvaultAdTenantId={ActiveDirectory_TenantId}
keyConnectorSettings__rsaKey__azureKeyvaultAdAppId={AppRegistration_ApplicationId}
keyConnectorSettings__rsaKey__azureKeyvaultAdSecret={AppRegistration_ClientSecretValue}
```

[了解如何使用 Azure Key Vault 创建密钥对](https://docs.microsoft.com/zh-cn/azure/key-vault/keys/quick-create-portal)

### Google Cloud **Key Management**

如果您使用 Google Cloud Key Management 来存储 RSA 2048 密钥对，请指定以下值：

```systemd
keyConnectorSettings__rsaKey__provider=gcpkms
keyConnectorSettings__rsaKey__googleCloudProjectId={Project_Id}
keyConnectorSettings__rsaKey__googleCloudLocationId={Location_Id}
keyConnectorSettings__rsaKey__googleCloudKeyringId={Keyring_Id}
keyConnectorSettings__rsaKey__googleCloudKeyId={Key_Id}
keyConnectorSettings__rsaKey__googleCloudKeyVersionId={KeyVersionId}
```

[了解如何使用 Google Cloud Key Management Service 创建密钥环和非对称密钥](https://cloud.google.com/kms/docs/creating-asymmetric-keys)

### AWS Key **Management Service**

如果您使用 AWS Key Management Service (KMS) 来存储 RSA 2048 密钥对，请指定以下值：

```systemd
keyConnectorSettings__rsaKey__provider=awskms
keyConnectorSettings__rsaKey__awsAccessKeyId={AccessKey_Id}
keyConnectorSettings__rsaKey__awsAccessKeySecret={AccessKey_Secret}
keyConnectorSettings__rsaKey__awsRegion={Region_Name}
keyConnectorSettings__rsaKey__awsKeyId={Key_Id}
```

[了解如何使用 AWS KMS 创建非对称密钥](https://docs.aws.amazon.com/zh_cn/kms/latest/developerguide/asymm-create-key.html)
{% endtab %}

{% tab title="PKCS#11 HSM" %}
如果您使用带有 PKCS#11 提供程序的物理 HSM 设备来存储私钥，您将需要：

1、将配置为 PEM 编码证书的相应公钥上传到 Key Connector 容器可以访问的位置（请参阅**证书**选项卡）。

2、使用以下值配置 Key Connector，其中包含 PKCS#11 特定值（例如 `keyConnectorSettings__rsaKey__pkcs11...`）和特定于您选择的存储公钥的位置的值（例如 `keyConnectorSettings_certificate_...`）：

```systemd
keyConnectorSettings__rsaKey__provider=pkcs11
keyConnectorSettings__rsaKey__pkcs11Provider={Provider}
keyConnectorSettings__rsaKey__pkcs11SlotTokenSerialNumber={Token_SerialNumber}
keyConnectorSettings__rsaKey__pkcs11LoginUserType={Login_UserType}
keyConnectorSettings__rsaKey__pkcs11LoginPin={Login_PIN}

ONE OF THE FOLLOWING TWO:
keyConnectorSettings__rsaKey__pkcs11PrivateKeyLabel={PrivateKeyLabel}
keyConnectorSettings__rsaKey__pkcs11PrivateKeyId={PrivateKeyId}

OPTIONALLY:
keyConnectorSettings__rsaKey__pkcs11LibraryPath={path/to/library/file}
```

{% hint style="info" %}
Key Connector 可能需要访问特定文件，例如本地 PEM 证书或 PPKCS#11 驱动程序文件。默认情况下，目录 `./bwdata/key-connector` 挂载到位于 `/etc/bitwarden/key-connector` 的容器中，这意味着存储在主机操作系统中 `/opt/bitwarden/bwdata/key-connector/certificate.pem` 的证书文件可用于位于 `/etc/bitwarden/key-connector/certificate.pem` 的容器。Key Connector 配置必须引用其安装位置中的文件，如下例所示：

```systemd
keyConnectorSettings__certificate__filesystemPath=/etc/bitwarden/key-connector/certificate.pem
```
{% endhint %}

**在所有情况下都必需：**

* `keyConnectorSettings__rsaKey__provider=`：必须为 `pkcs11`.
* `keyConnectorSettings__rsaKey__pkcs11Provider=`：必须为 `yubihsm` 或 `opensc`。
* `keyConnectorSettings__rsaKey__pkcs11SlotTokenSerialNumber=`：用于识别要使用的令牌的序列号。
* `keyConnectorSettings__rsaKey__pkcs11LoginUserType=`：可以为 `user`、 `so` 或 `context_specific`。
* `keyConnectorSettings__rsaKey__pkcs11LoginPin=`：用于访问令牌的 PIN 码。
* `keyConnectorSettings__certificate__provider=`：可以为 `filesystem`, `azurestorage`, `azurekv` 或 `vault`。

**在某些情况下必需：**

* `keyConnectorSettings__rsaKey__pkcs11PrivateKeyLabel=`：（如果不使用 `...__pkcsPrivateKeyId=` 则为必需，请参见下文）您的私钥的标签或「别名」。
* `keyConnectorSettings__rsaKey__pkcs11PrivateKeyId=`：（如果不使用 `...__pkcs11PrivateKeyLabel=` 则为必需）您的私钥的唯一标识符。
* `keyConnectorSettings__certificate__filesystem...=`：如果将公钥存储在文件系统上，请设置 `...__certificate__filesystem...` 值（请参阅**证书**选项卡）。
* `keyConnectorSettings__certificate__azure...=`：如果将公钥存储在 Azure Blob 存储中，请设置所有 `...__certificate__azure...` 值（请参阅**证书**选项卡）。
* `keyConnectorSettings__certificate__azureKeyvault...=`：如果将公钥存储在 Azure Key Vault 中，请设置所有 `...__certificate__azureKeyvault..`. 值（请参阅**证书**选项卡）。
* `keyConnectorSettings__certificate__vault...=`：如果您将公钥存储在 Hashicorp Vault 中，请设置所有 `...__certificate__vault...` 值（请参阅**证书**选项卡）。

**可选：**

* `keyConnectorSettings__rsaKey__pkcs11LibraryPath=`：（可选）将 Key Connector 指向库文件，例如 `=/etc/bitwarden/libfxpkcs11.so`。这样做将取代 `keyConnectorSettings__rsaKey__pkcs11Provider=` 的值。
{% endtab %}
{% endtabs %}

### 确保 Key Connector 的安全 <a href="#securing-key-connector" id="securing-key-connector"></a>

建议 Key Connector 用户采取额外的安全措施，以保持数据库和数据传输的零知识加密。

* 使用 TLS 拦截代理的组织需要采取额外措施，以保持零知识加密。为确保安全，请将 Bitwarden URL 添加到代理的排除列表中，这将确保与 Key Connector 的数据传输在整个数据传输过程中保持加密和非登录状态。
* 加密机制之间的迁移并非总是可行的。
* 目前**不支持**从一个数据库迁移到另一个数据库。请确保为数据库执行频繁的自动备份计划。

{% hint style="danger" %}
加密密钥的管理非常敏感，**只建议拥有能安全支持部署和管理密钥服务器的团队和基础设施的企业使用**。
{% endhint %}

### 激活 Key Connector <a href="#activate-key-connector" id="activate-key-connector"></a>

现在 Key Connector 已[配置完成](deploy-key-connector.md#configure-key-connector)，并且您也拥有[启用了 Key Connector 的许可证](deploy-key-connector.md#obtain-new-license-file)，请完成以下步骤：

1、重新启动您的自托管 Bitwarden 安装以应用配置更改：

```bash
./bitwarden.sh restart
```

2、以组织**所有者**身份登录您的自托管 Bitwarden，然后导航至管理控制台的**计费** → **订阅**界面。

3、选择**更新许可证**按钮，然后上传[在前面的步骤中获取的](deploy-key-connector.md#obtain-new-license-file)启用了 Key Connector 的许可证。

4、如果您还没有准备好，请导航到**设置** → **策略**界面，启用[单一组织](../../admin-console/oversight-visibility/enterprise-policies.md#single-organization)和[要求单点登录身份验证](../../admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)策略。**这两项都是使用 Key Connector 的必要条件**。

5、导航至**设置** → **单点登录**界面。

{% hint style="success" %}
接下来的几个步骤假设您已经拥有一个使用 [SAML 2.0](../../admin-console/login-with-sso/sso-guides/generic-saml.md) 或 [OIDC](../../admin-console/login-with-sso/sso-guides/generic-oidc.md) 的、激活了 [SSO 登录](../../admin-console/login-with-sso/about-sso.md)的实施。**如果还没有**，请在继续之前先实施和测试 SSO 登录。
{% endhint %}

6、在**成员解密选项**部分，选择 **Key Connector**。

7、在 **Key Connector URL** 输入框中，输入 Key Connector 运行的地址（默认为 `https://your.domain/key-connector`），选然后择**测试**按钮以确保您可以访问 Key Connector。

8、滚动到屏幕底部然后选择**保存**。

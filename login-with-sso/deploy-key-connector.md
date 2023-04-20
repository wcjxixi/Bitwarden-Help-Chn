# 部署 Key Connector

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/deploy-key-connector/)
{% endhint %}

本文将引导您完成在现有自托管环境中启用和配置 Key Connector 的过程。**在继续之前**，请仔细阅读[关于 Key Connector](about-key-connector.md) 一文，以确保完全了解 Key Connector 是什么、它是如何工作的以及实施的影响。

## 要求 <a href="#requirements" id="requirements"></a>

{% hint style="warning" %}
加密密钥的管理非常敏感，**仅建议拥有可以安全支持部署和管理密钥服务器的团队和基础架构的企业使用**。
{% endhint %}

要使用 Key Connector，您必须：

* [拥有一个企业组织](../plans-and-pricing/about-bitwarden-plans.md#enterprise-organizations)
* [拥有一个自托管的 Bitwarden 服务器](../self-hosting/)
* [拥有一个活跃的 SSO 实施](about-login-with-sso.md)
* [激活单一组织和单点登录策略](../organizations/enterprise-policies.md)

如果您的组织满足或能够满足这些要求，包括拥有可以支持密钥服务器管理的团队和基础设施，请[联系我们](https://bitwarden.com/contact)，我们将为您激活 Key Connector。

## 设置和部署 Key Connector <a href="#setup-and-deploy-key-connector" id="setup-and-deploy-key-connector"></a>

您就 Key Connector 与我们联系后，我们将与您联系以启动一个 Key Connector 的讨论。本文中的步骤必须与 Bitwarden 客户成功与实施专家合作完成。

### 获取新的许可证文件 <a href="#obtain-new-license-file" id="obtain-new-license-file"></a>

您就 Key Connector 与我们联系后，客户成功与实施团队的一名成员将为您的组织生成一个启用了 Key Connector 的许可证文件。当您的 Bitwarden 合作者指示您准备就绪时，请完成以下步骤以获取新的许可证：

1. 打开您的 Bitwarden Cloud 网页密码库，然后导航到您组织的**设置** → **订阅**界面。
2. 选择**下载许可证**按钮。
3. 当出现提示时，输入用于安装自托管服务器的安装 ID，然后选择**提交**。如果您不知道自己的安装 ID，可以从 `./bwdata/env/global.override.env` 中检索它。

不会立即需要您的许可证文件，但您需要[在后面的步骤中](deploy-key-connector.md#activate-key-connector)将其上传到您的自托管服务器。

### 初始化 Key Connector <a href="#initialize-key-connector" id="initialize-key-connector"></a>

为 Key Connector 准备 Bitwarden 服务器：

1、至少保存一个 `.bwdata/mssql` 的[备份](../self-hosting/backup-your-hosted-data.md)。使用 Key Connector 后，建议您获取一个之前的 Key Connector 备份映像的访问权限，以防出现问题。

{% hint style="info" %}
如果您使用的是[外部 MSSQL 数据库](../self-hosting/connect-to-an-external-mssql-database.md)，请以适合您的实施方式备份您的数据库。
{% endhint %}

2、更新您的自托管 Bitwarden 安装以获取最新的更改：

```
./bitwarden.sh update
```

3、编辑 `.bwdata/config.yml` 文件并通过将 `enable_key_connector` 切换为 `true` 来启用密钥连接器。

```
nano bwdata/config.yml
```

4、重建您的自托管 Bitwarden 安装：

```
./bitwarden.sh rebuild
```

5、再次更新您的自托管 Bitwarden 安装以应用更改：

```
./bitwarden.sh update
```

### 配置 Key Connector <a href="#configure-key-connector" id="configure-key-connector"></a>

要配置 Key Connector：

1、编辑随 `./bitwarden.sh update` 一起下载的 `.bwdata/env/key-connector.override.env` 文件。

```
nano bwdata/env/key-connector.override.env
```

{% hint style="warning" %}
此文件将被预先填入默认值，以启动一个功能性的本地 Key Connector 设置，**但不建议在生产环境中使用这些默认值**。
{% endhint %}

2、在 `key-connector.override.env` 中，您需要为以下内容指定值：

* **端点**：Key Connector 可以与之通信的 Bitwarden 端点。
* **数据库**：用于 Key Connector 存储和检索用户密钥的地方。
* **RSA 密钥对**：Key Connector 访问 RSA 密钥对以保护静态用户密钥。

#### 端点 <a href="#endpoints" id="endpoints"></a>

自动设置将基于您的安装配置填充端点的值，但还是建议您确认 `key-connector.override.env` 中的以下值对于您的设置是准确的：

```
keyConnectorSettings__webVaultUri=https://your.bitwarden.domain.com
keyConnectorSettings__identityServerUri=https://your.bitwarden.domain.com/identity/
```

#### 数据库 <a href="#database" id="database"></a>

Key Connector 必须访问一个为您的组织成员存储已加密用户密钥的数据库。创建一个安全数据库来存储已加密的用户密钥，并将 `key-connector.override.env` 中 `keyConnectorSettings__database__` 的默认值替换为所选数据库的**要求的值**列中指定的值：

{% hint style="warning" %}
目前**不支持**从一个数据库迁移到另一个数据库。无论您选择哪个提供程序，请为数据库**实施一个频繁的自动备份计划**。
{% endhint %}

| 数据库                  | 要求的值                                                                                                                                                                                                                                                                                                                                                  |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Local JSON （**默认**）  | <p><strong>不建议用于测试之外的其他场景。</strong><br><br><code>keyConnectorSettings__database__provider=json</code><br><code>keyConnectorSettings__database__jsonFilePath={File_Path}</code></p>                                                                                                                                                                    |
| Microsoft SQL Server | <p><code>keyConnectorSettings__database__provider=sqlserver</code><br><code>keyConnectorSettings__database__sqlServerConnectionString={Connection_String}</code><br><br><a href="https://docs.microsoft.com/zh-cn/sql/connect/ado-net/connection-string-syntax?view=sql-server-ver15">了解如何格式化 MSSQL 连接字符串</a></p>                                     |
| PostgreSQL           | <p><code>keyConnectorSettings__database__provider=postgresql</code><br><code>keyConnectorSettings__database__postgreSqlConnectionString={Connection_String}</code><br><br><a href="https://www.npgsql.org/doc/connection-string-parameters.html">了解如何格式化 PostgreSQL 连接字符串</a></p>                                                                     |
| MySQL/MariaDB        | <p><code>keyConnectorSettings__database__provider=mysql</code><br><code>keyConnectorSettings__database__mySqlConnectionString={Connection_String}</code><br><br><a href="https://dev.mysql.com/doc/connector-net/en/connector-net-connections-string.html">了解如何格式化 MySQL 连接字符串</a></p>                                                                |
| MongoDB              | <p><code>keyConnectorSettings__database__provider=mongo</code><br><code>keyConnectorSettings__database__mongoConnectionString={Connection_String}</code><br><code>keyConnectorSettings__database__mongoDatabaseName={DatabaseName}</code><br><br><a href="https://docs.mongodb.com/manual/reference/connection-string/">了解如何格式化 MongoDB 连接字符串</a></p> |

#### RSA 密钥对 <a href="#rsa-key-pair" id="rsa-key-pair"></a>

Key Connector 使用 RSA 密钥对来保护静态用户密钥。创建一个密钥对并将 `key-connector.override.env` 中 `keyConnectorSettings__rsaKey__` 和 `keyConnectorSettings__certificate__` 的默认值替换为您选择的实施所要求的值。

{% hint style="info" %}
RSA 密钥对的长度**必须至少**为 2048 位。
{% endhint %}

通常，您的选项包括授予 Key Connector 对包含密钥对的 X509 **证书**的访问权限，或授予 Key Connector 访问**密钥对**的直接访问权限：

{% tabs %}
{% tab title="证书" %}
要使用包含 RSA 密钥对的 X509 证书，请根据您的证书的存储位置指定所需的值（参阅**文件系统**、**操作系统证书存储**等）：

{% hint style="success" %}
证书**必须**作为 PKCS12 `.pfx` 文件提供，例如：

```
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

```
keyConnectorSettings__rsaKey__provider=certificate
keyConnectorSettings__certificate__provider=filesystem
keyConnectorSettings__certificate__filesystemPath={Certificate_Path}
keyConnectorSettings__certificate__filesystemPassword={Certificate_Password}
```

### 操作系统证书存储 <a href="#os-certificate-store" id="os-certificate-store"></a>

如果证书存储在运行 Key Connector 的机器的操作系统证书存储中，请指定以下值：

```
keyConnectorSettings__rsaKey__provider=certificate
keyConnectorSettings__certificate__provider=store
keyConnectorSettings__certificate__storeThumbprint={Certificate_Thumbprint}
```

### Azure Blob **Storage** <a href="#azure-blob-storage" id="azure-blob-storage"></a>

如果证书被上传到 Azure Blob Storage 中，请指定以下值：

```
keyConnectorSettings__rsaKey__provider=certificate
keyConnectorSettings__certificate__provider=azurestorage
keyConnectorSettings__certificate__azureStorageConnectionString={Connection_String}
keyConnectorSettings__certificate__azureStorageContainer={Container_Name}
keyConnectorSettings__certificate__azureStorageFileName={File_Name}
keyConnectorSettings__certificate__azureStorageFilePassword={File_Password}
```

[了解如何格式化 Azure Blob 存储连接字符串](https://docs.microsoft.com/zh-cn/azure/data-explorer/kusto/api/connection-strings/storage#azure-blob-storage)

### Azure **Key Vault** <a href="#azure-key-vault" id="azure-key-vault"></a>

如果证书被存储在 Azure Key Vault 中，请指定以下值：

{% hint style="info" %}
要使用 Azure Key Vault 存储您的 `.pfx` 证书，您需要创建一个活动目录**应用程序注册**。此应用程序注册必须：

* 授予委派 API 权限以访问 Azure Key Vault&#x20;
* 拥有一个已生成的客户端密码以允许被 Key Connector 访问
{% endhint %}

```
keyConnectorSettings__certificate__provider=azurekv
keyConnectorSettings__certificate__azureKeyvaultUri={Vault_URI}
keyConnectorSettings__certificate__azureKeyvaultCertificateName={Certificate_Name}
keyConnectorSettings__certificate__azureKeyvaultAdTenantId={ActiveDirectory_TenantId}
keyConnectorSettings__certificate__azureKeyvaultAdAppId={AppRegistration_ApplicationId}
keyConnectorSettings__certificate__azureKeyvaultAdSecret={AppRegistration_ClientSecretValue}
```

### Hashicorp **Vault** <a href="#hashicorp-vault" id="hashicorp-vault"></a>

如果证书被存储在 Hashicorp Vault 中，请指定以下值：

```
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

{% tab title="密钥对" %}
要使用云提供商或物理设备存储 RSA 2048 密钥对，请根据您选择的实施指定所需的值（请参阅 **Azure Key Vault**、**Google Cloud Key Management** 等）：

### Azure Key Vault

如果您使用 Azure Key Vault 来存储 RSA 2048 密钥对，请指定以下值：

{% hint style="info" %}
要使用 Azure Key Vault 存储您的 RSA 2048 密钥，您需要创建一个活动目录**应用程序注册**。此应用程序注册必须：

* 授予委派 API 权限以访问 Azure Key Vault&#x20;
* 拥有一个已生成的客户端密码以允许被 Key Connector 访问
{% endhint %}

```
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

```
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

```
keyConnectorSettings__rsaKey__provider=awskms
keyConnectorSettings__rsaKey__awsAccessKeyId={AccessKey_Id}
keyConnectorSettings__rsaKey__awsAccessKeySecret={AccessKey_Secret}
keyConnectorSettings__rsaKey__awsRegion={Region_Name}
keyConnectorSettings__rsaKey__awsKeyId={Key_Id}
```

[了解如何使用 AWS KMS 创建非对称密钥](https://docs.aws.amazon.com/zh\_cn/kms/latest/developerguide/asymm-create-key.html)

### PKCS11 Physical HSM

如果您在 PKCS11 提供程序上使用一个物理 HSM 设备，请指定以下值：

```
keyConnectorSettings__rsaKey__provider=pkcs11
keyConnectorSettings__rsaKey__pkcs11Provider={Provider}
keyConnectorSettings__rsaKey__pkcs11SlotTokenSerialNumber={Token_SerialNumber}
keyConnectorSettings__rsaKey__pkcs11LoginUserType={Login_UserType}
keyConnectorSettings__rsaKey__pkcs11LoginPin={Login_PIN}

以下两者之一：
keyConnectorSettings__rsaKey__pkcs11PrivateKeyLabel={PrivateKeyLabel}
keyConnectorSettings__rsaKey__pkcs11PrivateKeyId={PrivateKeyId}
```

其中：

* `{Provider}` 可以为 `yubihsm` 或 `opensc`
* `{Login_UserType}` 可以为 `user`、`so` 或 `context_specific`

{% hint style="info" %}
如果您使用 PKCS11 提供程序将您的私钥存储在 HSM 设备上，则相关联的公钥必须是可用的，并使用**证书**选项卡中的任何选项配置为证书。
{% endhint %}
{% endtab %}
{% endtabs %}

### 激活 Key Connector <a href="#activate-key-connector" id="activate-key-connector"></a>

现在 [Key Connector 已配置完成](deploy-key-connector.md#configure-key-connector)，并且您也拥有[启用了 Key Connector 的许可证](deploy-key-connector.md#obtain-new-license-file)，请完成以下步骤：

1、重新启动您的自托管 Bitwarden 安装以应用配置更改：

```
./bitwarden.sh restart
```

2、以**组织所有者**身份登录您的自托管 Bitwarden，然后导航至组织**设置** → **订阅**界面。

3、选择**更新许可证**按钮，然后上传[在前面的步骤中获取的](deploy-key-connector.md#obtain-new-license-file)启用了 Key Connector 的许可证：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3fYAN71thZdXeRUNwBFfDC/e56e3e4c9f8d406da87eca5a8cccf64d/update-license.png?fm=webp&h=1296&q=50&w=2040" %}
更新您的许可证
{% endembed %}

4、导航到组织**管理**界面。

5、（如果您还没有）请导航到**策略**界面，然后启用[单一组](../organizations/enterprise-policies.md#single-organization)织和[单点登录验证](../organizations/enterprise-policies.md#single-sign-on-authentication)策略。**两者都需要使用 Key Connector**。

6、导航到**单点登录（SSO）**界面：

{% hint style="success" %}
接下来的几个步骤假设您已经拥有一个使用 [SAML 2.0](saml-2.0-configuration.md) 或 [OIDC](oidc-configuration.md) 的、激活了 [SSO 登录](about-login-with-sso.md)的实施。**如果还没有**，请在继续之前先实施和测试 SSO 登录。
{% endhint %}

7、在**成员解密选项**部分，选择 **Key Connector**。

8、在 **Key Connector URL** 输入框中，输入 Key Connector 运行的地址（默认为 `https://your.domain/key-connector`），选然后择**测试**按钮以确保您可以访问 Key Connector。

9、滚动到屏幕底部然后选择**保存**。

# Duo SAML

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-duo/)
{% endhint %}

本文是**专门针对 Duo** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](generic-saml.md)。

配置需要在 Bitwarden 网页 App 和 Duo 管理门户中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

{% hint style="success" %}
**已经是 SSO 专家？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/5zTphwdGyxRww5UaF3COLP/67104e859f8fcaad2aa4b185292971eb/saml-duo-sample.zip)
{% endhint %}

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

{% hint style="danger" %}
本文假定您已经使用身份提供程序设置了 Duo。如果还没有，请参阅 [Duo 文档](https://duo.com/docs/sso#saml)了解详情。
{% endhint %}

登录到 Bitwarden 网页 App，然后使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJAUVWIZAAB" %}
产品切换器
{% endembed %}

打开组织的**设置** → **单点登录**界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?_a=DAJAUVWIZAAB" %}
SAML 2.0 配置
{% endembed %}

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个，然后从**类型**下拉菜单中选择 **SAML**。保持此界面打开，以方便参考。

如果愿意，您可以在此阶段关闭**设置专属的 SP 实体 ID** 选项。这样做会从 SP 实体 ID 值中移除组织 ID，但大多数情况下都建议打开该选项。

{% hint style="success" %}
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 保护应用程序 <a href="#protect-an-application" id="protect-an-application"></a>

在继续之前，请参阅 [Duo 文档](https://duo.com/docs/sso#saml)以验证 Duo 单点登录是否已配置为使用您的 SAML 身份提供程序进行身份验证。

在 Duo 管理门户中，导航到 **Applications** 界面然后选择 **Protect an Application**。在搜索栏中输入 **Bitwarden**，然后为 **Bitwarden 2FA with SSO hosted by Duo** 应用程序选择 **Configure**：

{% embed url="https://bitwarden.com/assets/trkKdfpokzVAwdGxg6wa6/02ae03583eae5f96e4a6fbe90e70af14/2023-12-11_15-58-21.png?w=1200&fm=avif" %}
Duo Bitwarden 应用程序
{% endembed %}

为新创建的应用程序选择 **Activate and Start Setup**：

{% embed url="https://bitwarden.com/assets/38UnzJq3P4zVvB8wHpK62W/ff109380215fc7d82c25c960eecd3ec3/2023-12-11_16-00-38.png?w=1200&fm=avif" %}
Duo 激活和设置
{% endembed %}

在应用程序配置界面完成以下步骤和配置，其中的一些步骤和配置需要您从 Bitwarden 业务门户中获取：

{% embed url="https://bitwarden.com/assets/5OMLBklde4cADIvmgypSxe/64f00b2c483c471a9a5ead8da8f982e5/2023-12-11_16-09-16.png?w=1200&fm=avif" %}
DUO SAML 身份提供程序配置
{% endembed %}

### 元数据 <a href="#metadata" id="metadata"></a>

您不需要在 **Metadata** 部分编辑任何内容，但[稍后您需要引用这些值](duo-saml-implementation.md#identity-provider-configuration)：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3ob9jp2RJRhMaxOkRrWHKa/8a9b7c3cc3aa077e323353c8c0cab0ed/duo-urls.png?fm=webp&h=146&q=50&w=804" %}
配置 URL
{% endembed %}

### 下载 <a href="#downloads" id="downloads"></a>

选择 **Download certificate** 按钮以下载您的 X.509 证书，因为您需要在[稍后的配置中](duo-saml-implementation.md#identity-provider-configuration)使用它。

### 服务提供程序 <a href="#service-provider" id="service-provider"></a>

| 字段                                   | 描述                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Entity ID                            | <p>将此字段设置为从 Bitwarden SSO 配置界面中预先生成的 <strong>SP 实体 ID</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并且会根据您的设置而有所不同。</p>                                                                                                                                                                                                |
| Assertion Consumer Service (ACS) URL | <p>将此字段设置为从 Bitwarden SSO 配置界面中预先生成的<strong>断言消费者服务 (ACS) URL</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并且会根据您的设置而有所不同。</p>                                                                                                                                                                                        |
| Service Provider Login URL           | <p>将此字段设置为用户访问 Bitwarden 的登录 URL。<br><br>对于云托管客户，其始终为 <code>https://vault.bitwarden.com/#/sso</code> 或 <code>https://vault.bitwarden.eu/#/sso.</code>。对于自托管实例，这由您<a href="../../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">已配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/#/sso</code>。</p> |

### SAML 响应 <a href="#saml-response" id="saml-response"></a>

| 字段                  | 描述                                                                                                            |
| ------------------- | ------------------------------------------------------------------------------------------------------------- |
| NameID format       | 将此字段设置为 [SAML NameID 格式](https://docs.oracle.com/cd/E19316-01/820-3886/ggwbz/index.html)，以便 Duo 在 SAML 响应中发送。 |
| NameID attribute    | 将此字段设置为 Duo 属性，该属性用于在响应中填充 NameID。                                                                            |
| Signature algorithm | 将此字段设置为用于 SAML 声明和响应的加密算法。                                                                                    |
| Signing options     | 设置为 **Sign response** 或 **Sign assertion**,，或同时设置。                                                            |
| Map attributes      | 使用这些字段将 IdP 属性映射到 SAML 响应属性。无论您配置了哪个 NameID 属性，请将 IdP `Email Address` 属性映射到 `Email`，如下面的屏幕截图所示：               |

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2MQbtzmGaflBaCf0FIa2r9/914b2dec377d122deee4a65439689e2a/duo-mapping.png?fm=webp&h=238&q=50&w=727" %}
必需的属性映射
{% endembed %}

完成这些字段的配置后， **Save** 您的更改。

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已经在 Duo 管理门户网站中配置好了您所需要的一切。请返回 Bitwarden 网页 App 完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据在 Duo 管理门户中的[应用程序设置](duo-saml-implementation.md#protect-an-application)中所选择的选项配置以下字段：

| 字段                                 | 描述                                                                                                                                                                              |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | [NameID Format](https://docs.oracle.com/cd/E19316-01/820-3886/ggvxx/index.html) 被用在 SAML 请求（`NameIDPolicy`）中。将此字段设置为[已选择的 NameID 格式](duo-saml-implementation.md#saml-response)。 |
| Outbound Signing Algorithm         | 用于签名 SAML 请求的算法，默认为 `rsa-sha256`。                                                                                                                                               |
| Signing Behavior                   | SAML 请求是否/何时将被签名。默认，Duo 不要求对请求进行签名。                                                                                                                                             |
| Minimum Incoming Signing Algorithm | Bitwarden 在 SAML 响应中接受的最小签名算法。默认，Duo 使用 `rsa-sha256` 进行签名，因此请从下拉列表中选择该选项，除非您[选择了不同的选项](duo-saml-implementation.md#saml-response)。                                               |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名。如果您[选择了 **Sign assertion** 选项](duo-saml-implementation.md#saml-response)，请选中此框。                                                                       |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                                                                                      |

完成服务提供程序配置部分后，**保存**您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 Duo 管理门户以获取应用程序的值：

| 字段                                  | 描述                                                                                                                                                                                                                     |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                           | 输入您的 Duo 应用程序的 **Domain** 值，这可以从 Duo 应用程序[元数据部分](duo-saml-implementation.md#metadata)获取到。                                                                                                                              |
| Binding Type                        | 将此字段设置为 **HTTP post**。                                                                                                                                                                                                 |
| Single Sign On Service URL          | 输入您的 Duo 应用程序的 **Single Sign-On URL** 值，这可以从 Duo 应用程序[元数据部分](duo-saml-implementation.md#metadata)获取到。                                                                                                                  |
| Single Log Out Service URL          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发，但是您可以根据需要将其预先配置为您的 Duo 应用程序的 **Single Log-Out URL** 值 。                                                                                                                              |
| Artifact Resolution Service URL     | 对于 Duo 实现，您可以将此字段留空。                                                                                                                                                                                                   |
| X509 Public Certificate             | <p>黏贴已下载的<a href="duo-saml-implementation.md#downloads">证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>证书值区分大小写，多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm          | 将此字段设置为[已选择的 SAML 响应签名算法](duo-saml-implementation.md#saml-response)。                                                                                                                                                   |
| Disable Outbound Logout Requests    | SSO 登录当前还**不支持** SLO。该选项计划未来开发。                                                                                                                                                                                        |
| Want Authentication Requests Signed | Duo 是否要求 SAML 请求被签名。                                                                                                                                                                                                   |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**保存**您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../oversight-visibility/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**使用单点登录**按钮来进行测试：

{% embed url="https://bitwarden.com/assets/3BdlHeogd42LEoG06qROyQ/c68021df4bf45d72e9d37b1fbf5a6040/login.png?w=517&fm=avif" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](generic-saml.md#step-1-set-an-organization-identifier)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到您的源 IdP 的登录界面。

使用您的 IdP 登录和 Duo 双重身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

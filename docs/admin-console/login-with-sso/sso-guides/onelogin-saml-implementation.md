# OneLogin SAML

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-onelogin/)
{% endhint %}

本文是**专门针对** **OneLogin** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](generic-saml.md)。

配置需要在 Bitwarden 网页 App 和 OneLogin 门户中同时进行。操作过程中，我们建议同时打开这两个界面，并按照文档记录的步骤顺序完成操作。

{% hint style="success" %}
**已经是 SSO 专家了吗？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️** [下载示例](https://bitwarden.com/assets/mQMTlMcvpyBPzgAkgqDvg/ace51cc7a46379048140042282e6b24f/saml-onelogin-sample.zip)
{% endhint %}

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden [网页 App](https://bitwarden.com/help/getting-started-webvault/)，然后使用产品切换器打开管理控制台：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

打开组织的**设置** → **单点登录**界面：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?w=1036&#x26;fm=avif" alt=""><figcaption><p>SAML 2.0 配置</p></figcaption></figure></div>

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个，然后从**类型**下拉菜单中选择 **SAML**。保持此界面打开，以方便参考。

如果愿意，您可以在此阶段关闭**设置唯一的 SP 实体 ID** 选项。这样做会从 SP 实体 ID 值中移除组织 ID，但大多数情况下都建议打开该选项。

{% hint style="success" %}
还可以选择使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建 OneLogin 应用程序 <a href="#create-a-onelogin-app" id="create-a-onelogin-app"></a>

在 OneLogin 门户中，导航到 **Applications** 界面然后选择 **Add App** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/37OSt7e5j969j9ikvH8buI/3bf9fa6b57a45b357a9d2bc012d8a6af/ol-addapp.png?fm=webp&h=292&q=50&w=1071" %}
添加应用程序
{% endembed %}

在搜索栏中，键入 `saml test connector` 然后并择 **SAML Test Connector (Advanced)** 应用程序：

{% embed url="https://bitwarden.com/assets/hTfoABj2iirzB1X7UT69x/792d40ee9f9c7471be35d9cfda450c05/ol-addapp2.png?w=1071&fm=avif" %}
SAML Test Connector App
{% endembed %}

为您的应用程序指定一个专用于 Bitwarden 的 **Display Name**，然后选择 **Save** 按钮。

### 配置 <a href="#configuration" id="configuration"></a>

从左侧导航中选择 **Configuration** 然后配置以下的信息，您需要从 Bitwarden 业务门户获取其中的一些信息：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/12yP5ohPGhqcCZZdpwVDQd/7fc5661e4fb4954ad00246deae2fd9b1/ol-appconfig.png?fm=webp&h=404&q=50&w=898" %}
应用程序配置
{% endembed %}

| 应用程序设置                       | 描述                                                                                                                                            |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Audience (EntityID)          | <p>将此字段设置为预先生成的 <strong>SP 实体 ID</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并且会根据您的设置而有所不同。</p>            |
| Recipient                    | 将此字段设置为同样也用于 **Audience (Entity ID)** 设置的预先生成的 **SP 实体 ID**。                                                                                  |
| ACS (Consumer) URL Validator | 尽管被 OneLogin 标记为**必需**，但您实际上并不需要在此字段中输入信息以与 Bitwarden 集成。跳到下一个字段 **ACS (Consumer) URL**。                                                      |
| ACS (Consumer) URL           | <p>将此字段设置为预先生成的<strong>断言消费者服务 (ACS) URL</strong>。<br></p><p>此自动生成的值可以从组织的<strong>设置</strong> → 单<strong>点登录</strong>界面复制，并且会根据您的设置而有所不同。</p> |
| SAML initiator               | 选择 **Service Provider**。SSO 登录当前不支持 IdP 发起的 SAML 断言。                                                                                          |
| SAML nameID Format           | 将此字段设置您希望用于 SAML 断言的 [SAML NameID 格式](https://docs.oracle.com/cd/E19316-01/820-3886/ggwbz/index.html)。                                        |
| SAML signature element       | 默认，OneLogin 将签名 SAML 响应。您可以将其设置为 **Assertion** 或 **Both**。                                                                                    |

完成配置设置后，选择 **Save** 按钮。

### 参数 <a href="#parameters" id="parameters"></a>

从左侧导航中选择 **Parameters**，然后使用  **🞤Add** 图标创建以下自定义参数：

| 字段名称      | 值          |
| --------- | ---------- |
| email     | Email      |
| firstname | First Name |
| lastname  | Last Name  |

完成自定义参数后，选择 **Save** 按钮。

### SSO

从左侧导航中选择 **SSO** 并完成以下操作：

1、选择 X.509 证书下的 **View Details** 链接：

{% embed url="https://bitwarden.com/assets/7emKbivWUWKO1ufVC9Rkgu/0039e55d93ba69fadc8c39e0be3d8a07/Screen_Shot_2022-12-29_at_9.42.14_AM.png?w=769&fm=avif" %}
查看您的证书
{% endembed %}

在证书界面，下载或复制您的 X.509 PEM 证书，因为您[稍后需要使用它](onelogin-saml-implementation.md#identity-provider-configuration)。复制后，返回主 SSO 界面。

2、设置您的 **SAML Signature Algorithm**。

3、记下您的 **Issuer URL** 和 **SAML 2.0 Endpoint (HTTP)**。您[很快就需要使用这些值](onelogin-saml-implementation.md#identity-provider-configuration)。

### 访问权限 <a href="#access" id="access"></a>

从左侧导航中选择 **Access**。在 **Roles** 部分，为您希望能够使用 Bitwarden 的所有角色分配应用程序访问权限。大多数实现会创建一个专用于 Bitwarden 的角色，而不是选择基于包罗万象（例如，**Default**）或基于预先存在的角色进行分配。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6D4j0WofpBcvSCMB0rN4Db/5303beacbc3ce331dfddc6dc6b19d6ea/ol-roles.png?fm=webp&h=147&q=50&w=899" %}
角色分配
{% endembed %}

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已经在 OneLogin 门户网站中配置好了您所需要的一切。请返回 Bitwarden 网页 App 完成配置。

单点登录界面将配置分为两个部分：

* &#x20;**SAML 服务提供程序配置**将决定 SAML 请求的格式。
* &#x20;**SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据在 OneLogin 门户网站[设置期间](onelogin-saml-implementation.md#create-a-onelogin-app)所选择的选项配置以下字段：

| 字段                                 | 描述                                                                                                                                        |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | 将此字段设置为您[在应用程序配置期间](onelogin-saml-implementation.md#configuration)为 OneLogin **SAML nameID Format** 字段选择的内容。                              |
| Outbound Signing Algorithm         | 用于签名 SAML 请求的算法，默认为 `sha-256`。                                                                                                            |
| Signing Behavior                   | SAML 请求是否/何时将被签名。默认，OneLogin 不要求对请求进行签名。                                                                                                  |
| Minimum Incoming Signing Algorithm | 将此字段设置为您在[应用程序配置期间](onelogin-saml-implementation.md#configuration)为 OneLogin **SAML Signature Algorithm** 字段选择的内容。                        |
| Want Assertions Signed             | 如果您在[应用程序配置期间](onelogin-saml-implementation.md#configuration)将 OneLogin 中的 **SAML signature element** 设置为 **Assertion** 或 **Both**，请选中此框。 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                                                |

完成服务提供程序配置部分后，**保存**您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 OneLogin 门户网站以获取应用程序的值：

| 字段                                  | 描述                                                                                                                                                                                                                              |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                           | 输入您的 OneLogin **Issuer URL**，这可以从 [OneLogin 应用 SSO 界面](onelogin-saml-implementation.md#sso)获取。                                                                                                                                  |
| Binding Type                        | 设置为 **HTTP Post**（如 SAML 2.0Endpoint (HTTP) 中所示）。                                                                                                                                                                               |
| Single Sign On Service URL          | 输入您的 OneLogin **SAML 2.0 Endpoint (HTTP)**，这可以从 [OneLogin 应用 SSO 界面](onelogin-saml-implementation.md#sso)获取。                                                                                                                    |
| Single Log Out Service URL          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。但是您可以根据需要预先配置它。                                                                                                                                                                               |
| X509 Public Certificate             | <p>黏贴<a href="onelogin-saml-implementation.md#sso">获取到的 X.509 证书</a>one，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>证书值区分大小写，多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm          | 选择在 [OneLogin SSO](onelogin-saml-implementation.md#sso) 配置界面选择的签名算法。                                                                                                                                                            |
| Disable Outbound Logout Requests    | SSO 登录当前还**不支持** SLO。该选项计划未来开发。                                                                                                                                                                                                 |
| Want Authentication Requests Signed | OneLogin 是否要求 SAML 请求被签名。                                                                                                                                                                                                       |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**保存**您的工作。

{% hint style="success" %}
您可以通过激活[单点登录身份验证策略](../../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)来要求用户使用 SSO 登录。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，然后选择**使用单点登录**按钮进行测试：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3BdlHeogd42LEoG06qROyQ/c68021df4bf45d72e9d37b1fbf5a6040/login.png?w=517&#x26;fm=avif" alt=""><figcaption><p>登录选项界面</p></figcaption></figure></div>

输入[已配置的组织标识符](onelogin-saml-implementation.md#open-sso-in-the-web-app)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 OneLogin 的登录界面：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/58dRC3pPEm0bO8xtd2Tqzq/415b83d361b49c73550d0932ddca8576/ol-login.png?w=485&#x26;fm=avif" alt=""><figcaption><p>OneLogin 登录界面</p></figcaption></figure></div>

使用您的 OneLogin 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持未经请求的响应，因此从您的 IdP 发起登录将导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

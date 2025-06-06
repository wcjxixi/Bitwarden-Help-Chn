# OIDC 配置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/configure-sso-oidc/)
{% endhint %}

## 第 1 步：设置 SSO 标识符 <a href="#step-1-set-an-sso-identifier" id="step-1-set-an-sso-identifier"></a>

[使用 SSO 验证身份](../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md#login-using-sso)的用户将被要求输入一个**组织标识符**，该标识符指示要进行身份验证的组织（以及 SSO 集成）。要设置唯一的组织标识符：

1、登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到 **设置** → **单点登录**，然后为您的组织输入一个唯一的**标识符**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6pr4tqMnrLCvwDBMlba5x7/7ef7563f7017f58adffff5d15ac68512/2024-12-04_09-39-25.png?_a=DAJCwlWIZAAB" %}
输入标识符
{% endembed %}

3、继续执行**步骤 2：启用 SSO 登录**。

{% hint style="success" %}
此配置准备好使用后，您需要将这个值分享给用户。
{% endhint %}

## 第 2 步：启用 SSO 登录 <a href="#step-2-enable-login-with-sso" id="step-2-enable-login-with-sso"></a>

拥有 SSO 标识符后，您就可以继续启用和配置您的集成了。要启用 SSO 登录：

1、在 **设置** → **单点登录** 视图中，勾选**允许 SSO 身份验证**复选框：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?_a=DAJCwlWIZAAB" %}
SAML 2.0 配置
{% endembed %}

2、从**类型**下拉菜单中，选择 **OpenID Connect** 选项。如果您打算改用 SAML，请切换到 [SAML 配置指南](saml-2.0-configuration.md)。

{% hint style="success" %}
还有其他**成员解密选项**。了解[受信任的设备 SSO](../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 或 [Key Connector](../self-hosting/key-connector/about-key-connector.md) 使用入门。
{% endhint %}

## 第 3 步：配置 <a href="#step-3-configuration" id="step-3-configuration"></a>

从这一步开始，**实施将因提供程序的不同而不同**。跳转到我们的特定**实施指南**之一，以帮助您完成配置过程：

| 提供程序  | 指南                                                                                                            |
| ----- | ------------------------------------------------------------------------------------------------------------- |
| Azure | [Azure 实施指南](../admin-console/login-with-sso/implementation-guides/microsoft-entra-id-oidc-implementation.md) |
| Okta  | [Okta 实施指南](implementation-guides/okta-oidc-implementation.md)                                                |

### 配置参考资料 <a href="#configuration-reference-materials" id="configuration-reference-materials"></a>

以下部分将定义在单点登录配置界面的字段，其与您要集成的 IdP 无关。必须配置的字段将被标记（**必填**）。

{% hint style="success" %}
**除非您对 OpenID Connect 比较精通**，否则我们建议使用[上述实施指南](oidc-configuration.md#step-3-configuration)之一，而不是使用如下的通用素材。
{% endhint %}

| 字段                                                      | 描述                                                                                                                                                                                                                                                                                                       |
| ------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Callback Path                                           | （**自动生成**）用于验证自动重定向的 URL。对于云托管客户，其为 `https://sso.bitwarden.com/oidc-signin` 或 h`ttps://sso.bitwarden.eu/oidc-signin`。对于自托管实例，这取决于您[已配置的服务器 URL](../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain)，例如 `https://your.domain.com/sso/oidc-signin`。            |
| Signed Out Callback Path                                | （**自动生成**）用于注销自动重定向的 URL。对于云托管客户，其始终为 `https://sso.bitwarden.com/oidc-signedout` 或 `https://sso.bitwarden.eu/oidc-signedout`。对于自托管实例，这取决于您[已配置的服务器 URL](../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain)，例如 `https://your.domain.com/sso/oidc-signedout`。 |
| Authority                                               | （**必填**）您的授权服务器（"Authority"）的 URL，Bitwarden 将对其进行身份验证。例如 `https://your.domain.okta.com/oauth2/default` 或 `https://login.microsoft.com/<TENANT_ID>/v2.0`。                                                                                                                                                 |
| Client ID                                               | （**必填**）用于 OIDC 客户端的标识符。此值通常特定于构建的 IdP 应用程序集成，例如 [Azure 应用程序注册](../admin-console/login-with-sso/implementation-guides/microsoft-entra-id-oidc-implementation.md)或 [Okta Web 应用程序](implementation-guides/okta-oidc-implementation.md)。                                                                    |
| Client Secret                                           | （**必填**）与客户端 ID 结合使用以交换访问令牌的客户端密钥。此值通常特定于构建的 IdP 应用程序集成。例如 [Azure 应用程序注册](../admin-console/login-with-sso/implementation-guides/microsoft-entra-id-oidc-implementation.md)或 [Okta Web 应用程序](implementation-guides/okta-oidc-implementation.md)。                                                          |
| Metadata Address                                        | （**如果 Authority 无效则必填**）一个元数据 URL，Bitwarden 可以在此访问作为 JSON 对象的授权服务器元数据。例如 `https://your.domain.okta.com/oauth2/default/.well-known/oauth-authorization-server`。                                                                                                                                           |
| OIDC Redirect Behavior                                  | （**必填**）IdP 用于响应来自 Bitwarden 的身份验证请求的方法。选项包括 **Form POST** 和 **Redirect GET**。                                                                                                                                                                                                                           |
| Get Claims From User Info Endpoint                      | 如果您在 SSO 期间收到 URL 太长错误（HTTP 414）、截断的 URL 和/或失败，请启用此选项。                                                                                                                                                                                                                                                   |
| Additional/Custom Scopes                                | 定义要添加到请求中的自定义范围（逗号分隔）。                                                                                                                                                                                                                                                                                   |
| Additional/Custom User ID Claim Types                   | 定义用于用户识别的自定义声明类型键（逗号分隔）。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                                                                                                                                                                                         |
| Additional/Custom Email Claim Types                     | 定义用于用户电子邮件地址的自定义声明类型键（逗号分隔）。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                                                                                                                                                                                     |
| Additional/Custom Name Claim Types                      | 定义用于用户全名或显示名称的自定义声明类型键（逗号分隔）。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                                                                                                                                                                                    |
| Requested Authentication Context Class Reference values | 定义身份验证上下文类引用标识符（`acr_values`）（空格分隔）。按优先顺序列出 `acr_values`。                                                                                                                                                                                                                                                |
| Expected “acr” Claim Value in Response                  | 定义 Bitwarden 在响应中期望和验证的 `acr` 声明值。                                                                                                                                                                                                                                                                       |

### OIDC 属性和声明 <a href="#oidc-attributes-and-claims" id="oidc-attributes-and-claims"></a>

**账户布建需要一个电子邮件地址**，它可以作为下表中的任何属性或声明被传递。

还强烈建议使用一个唯一的用户标识符。如果没有，将使用电子邮箱来链接用户。

属性/声明按优先匹配的顺序排列，包括适用的 Fallback：

| 值          | 声明/属性                                                                                                                                                                                   | Fallback 声明/属性                                                        |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Unique ID  | <p>Configured Custom User ID Claims<br>NameID (when not Transient)<br>urn:oid:0.9.2342.19200300.100.1.1<br>Sub<br>UID<br>UPN<br>EPPN</p>                                                |                                                                       |
| Email      | <p>Configured Custom Email Claims<br>Email<br>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress<br>urn:oid:0.9.2342.19200300.100.1.3<br>Mail<br>EmailAddress</p>       | <p>Preferred_Username<br>Urn:oid:0.9.2342.19200300.100.1.1<br>UID</p> |
| Name       | <p>Configured Custom Name Claims<br>Name<br>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name<br>urn:oid:2.16.840.1.113730.3.1.241<br>urn:oid:2.5.4.3<br>DisplayName<br>CN</p> | First Name + “ “ + Last Name (see below)                              |
| First Name | <p>urn:oid:2.5.4.42<br>GivenName<br>FirstName<br>FN<br>FName<br>Nickname</p>                                                                                                            |                                                                       |
| Last Name  | <p>urn:oid:2.5.4.4<br>SN<br>Surname<br>LastName</p>                                                                                                                                     |                                                                       |

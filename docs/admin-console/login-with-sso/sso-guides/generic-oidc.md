# 通用 OIDC

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/configure-sso-oidc/)
{% endhint %}

## 第 1 步：设置 SSO 标识符 <a href="#step-1-set-an-sso-identifier" id="step-1-set-an-sso-identifier"></a>

[使用 SSO 验证身份](../../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md#login-using-sso)的用户将被要求输入一个 **SSO 标识符**，该标识符指示了要验证的组织（即 SSO 集成）。要设置唯一的 SSO 标识符：

1、登录到 Bitwarden [网页 App](https://bitwarden.com/help/getting-started-webvault/)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

2、导航到 **设置** → **单点登录**，然后为您的组织输入一个唯一的 **SSO 标识符**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6pr4tqMnrLCvwDBMlba5x7/7ef7563f7017f58adffff5d15ac68512/2024-12-04_09-39-25.png?w=1036&#x26;fm=avif" alt=""><figcaption><p>输入标识符</p></figcaption></figure></div>

3、继续执行**第 2 步：启用 SSO 登录**。

{% hint style="success" icon="lightbulb" %}
配置完成后，您需要将这个值分享给用户。
{% endhint %}

## 第 2 步：启用 SSO 登录 <a href="#step-2-enable-login-with-sso" id="step-2-enable-login-with-sso"></a>

拥有 SSO 标识符后，您就可以继续启用和配置您的集成了。要启用 SSO 登录：

1、在 **设置** → **单点登录**视图中，勾选**允许 SSO 身份验证**复选框：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/51wSToXTHHVmBCrLrE8T0E/85aa432ea19eadf0195317f4f233e973/2024-12-04_09-41-46.png?w=1036&#x26;fm=avif" alt=""><figcaption><p>OIDC 配置</p></figcaption></figure></div>

2、从**类型**下拉菜单中，选择 **OpenID Connect** 选项。如果您打算改用 SAML，请切换到 [SAML 配置指南](generic-saml.md)。

{% hint style="success" icon="lightbulb" %}
还可以选择使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 第 3 步：配置 <a href="#step-3-configuration" id="step-3-configuration"></a>

从这一步开始，具体实施方式会因提供程序而异。跳转到我们的具体**实施指南**之一，以帮助完成配置过程：

| 提供程序  | 指南                                                      |
| ----- | ------------------------------------------------------- |
| Azure | [Azure 实施指南](microsoft-entra-id-oidc-implementation.md) |
| Okta  | [Okta 实施指南](okta-oidc-implementation.md)                |

### 配置参考资料 <a href="#configuration-reference-materials" id="configuration-reference-materials"></a>

以下部分将定义在单点登录配置界面的字段，其与您要集成的 IdP 无关。必须配置的字段将被标记（**必填**）。

{% hint style="success" icon="lightbulb" %}
**除非您对 OpenID Connect 比较精通**，否则我们建议使用[上述实施指南](generic-oidc.md#step-3-configuration)之一，而不是使用如下的通用素材。
{% endhint %}

<table data-search="false"><thead><tr><th>字段</th><th>描述</th></tr></thead><tbody><tr><td>Callback Path</td><td>（<strong>自动生成</strong>）用于验证自动重定向的 URL。对于云托管客户，其为 <code>https://sso.bitwarden.com/oidc-signin</code> 或 h<code>ttps://sso.bitwarden.eu/oidc-signin</code>。对于自托管实例，这取决于您<a href="../../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">已配置的服务器 URL</a>，例如 <code>https://your.domain.com/sso/oidc-signin</code>。</td></tr><tr><td>Signed Out Callback Path</td><td>（<strong>自动生成</strong>）用于注销自动重定向的 URL。对于云托管客户，其始终为 <code>https://sso.bitwarden.com/oidc-signedout</code> 或 <code>https://sso.bitwarden.eu/oidc-signedout</code>。对于自托管实例，这取决于您<a href="../../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">已配置的服务器 URL</a>，例如 <code>https://your.domain.com/sso/oidc-signedout</code>。</td></tr><tr><td>Authority</td><td>（<strong>必填</strong>）您的授权服务器（"Authority"）的 URL，Bitwarden 将对其进行身份验证。例如 <code>https://your.domain.okta.com/oauth2/default</code> 或 <code>https://login.microsoft.com/&#x3C;TENANT_ID>/v2.0</code>。</td></tr><tr><td>Client ID</td><td>（<strong>必填</strong>）用于 OIDC 客户端的标识符。此值通常特定于构建的 IdP App 集成，例如 <a href="microsoft-entra-id-oidc-implementation.md">Azure App 注册</a>或 <a href="okta-oidc-implementation.md">Okta 网页 App</a>。</td></tr><tr><td>Client Secret</td><td>（<strong>必填</strong>）与客户端 ID 结合使用以交换访问令牌的客户端密钥。此值通常特定于构建的 IdP App 集成。例如 <a href="microsoft-entra-id-oidc-implementation.md">Azure App 注册</a>或 <a href="okta-oidc-implementation.md">Okta 网页 App</a>。</td></tr><tr><td>Metadata Address</td><td>（<strong>如果 Authority 无效则必填</strong>）一个元数据 URL，Bitwarden 可以在此访问作为 JSON 对象的授权服务器元数据。例如 <code>https://your.domain.okta.com/oauth2/default/.well-known/oauth-authorization-server</code>。</td></tr><tr><td>OIDC Redirect Behavior</td><td>（<strong>必填</strong>）IdP 用于响应来自 Bitwarden 的身份验证请求的方法。选项包括 <strong>Form POST</strong> 和 <strong>Redirect GET</strong>。</td></tr><tr><td>Get Claims From User Info Endpoint</td><td>如果您在 SSO 期间收到 URL 太长错误（HTTP 414）、截断的 URL 和/或失败，请启用此选项。</td></tr><tr><td>Additional/Custom Scopes</td><td>定义要添加到请求中的自定义范围（逗号分隔）。</td></tr><tr><td>Additional/Custom User ID Claim Types</td><td>定义用于用户识别的自定义声明类型键（逗号分隔）。定义后，会在返回标准类型之前搜索自定义声明类型。</td></tr><tr><td>Additional/Custom Email Claim Types</td><td>定义用于用户电子邮箱地址的自定义声明类型键（逗号分隔）。定义后，会在返回标准类型之前搜索自定义声明类型。</td></tr><tr><td>Additional/Custom Name Claim Types</td><td>定义用于用户全名或显示名称的自定义声明类型键（逗号分隔）。定义后，会在返回标准类型之前搜索自定义声明类型。</td></tr><tr><td>Requested Authentication Context Class Reference values</td><td>定义身份验证上下文类引用标识符（<code>acr_values</code>）（空格分隔）。按偏好顺序列出 <code>acr_values</code>。</td></tr><tr><td>Expected “acr” Claim Value in Response</td><td>定义 Bitwarden 在响应中期望和验证的 <code>acr</code> 声明值。</td></tr></tbody></table>

### OIDC 属性 & 声明 <a href="#oidc-attributes-and-claims" id="oidc-attributes-and-claims"></a>

**账户布建需要一个电子邮箱地址**，它可以作为下表中的任何属性或声明被传递。

还强烈建议使用一个唯一的用户标识符。如果没有，将使用电子邮箱来链接用户。

属性/声明按优先匹配的顺序排列，包括适用的 Fallback：

| 值          | 声明/属性                                                                                                                                                                                   | Fallback 声明/属性                                                        |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Unique ID  | <p>Configured Custom User ID Claims<br>NameID (when not Transient)<br>urn:oid:0.9.2342.19200300.100.1.1<br>Sub<br>UID<br>UPN<br>EPPN</p>                                                |                                                                       |
| Email      | <p>Configured Custom Email Claims<br>Email<br>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress<br>urn:oid:0.9.2342.19200300.100.1.3<br>Mail<br>EmailAddress</p>       | <p>Preferred_Username<br>Urn:oid:0.9.2342.19200300.100.1.1<br>UID</p> |
| Name       | <p>Configured Custom Name Claims<br>Name<br>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name<br>urn:oid:2.16.840.1.113730.3.1.241<br>urn:oid:2.5.4.3<br>DisplayName<br>CN</p> | First Name + “ “ + Last Name (see below)                              |
| First Name | <p>urn:oid:2.5.4.42<br>GivenName<br>FirstName<br>FN<br>FName<br>Nickname</p>                                                                                                            |                                                                       |
| Last Name  | <p>urn:oid:2.5.4.4<br>SN<br>Surname<br>LastName</p>                                                                                                                                     |                                                                       |

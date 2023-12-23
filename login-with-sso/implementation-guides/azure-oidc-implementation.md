---
description: 本文包含为 Azure OIDC 实施配置 Bitwarden SSO 登录的说明。
---

# Azure OIDC 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/oidc-azure/)
{% endhint %}

本文是**专门针对 Azure** 用于配置 OpenID 连接（OIDC） 方式的 SSO 登录的帮助。有关其他 OIDC IdP 方式配置 SSO 登录，或配置 SAML 2.0 方式的 Azure 的帮助，请参阅 [OIDC 配置](../oidc-configuration.md)或 [Azure SAML 实施](azure-saml-implementation.md)。

配置需要在 Bitwarden 网页密码库和 Azure 门户网站中同时进行。在您继续进行操作时，我们建议您随时准备好并按照记录的顺序完成步骤。

## 在网页密码库中打开 SSO <a href="#open-sso-in-the-web-vault" id="open-sso-in-the-web-vault"></a>

如果您是直接从 [OIDC 配置](../oidc-configuration.md)过来的，你应该[已经创建了一个组织 ID](../saml-2.0-configuration.md#step-1-set-an-organization-identifier) 并打开了 SSO 配置界面。如果你没有，请参考那篇文章，为 SSO 创建一个组织 ID。

导航到您组织的**管理** → **单点登录**界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6hhSOvtqAuWemfaN78atRv/f7b2d1732a25b110c1b7eb1296637453/sso-oidc1.png?fm=webp&h=612&q=50&w=822" %}
OIDC 配置
{% endembed %}

你不需要编辑此界面上的任何内容，但要保持打开以方便引用。

{% hint style="success" %}
如果您是自托管 Bitwarden，您可以选择性使用**成员解密选项**。此功能默认情况下被禁用，因此现在继续使用**主密码**解密，并了解如何在配置完成并成功运行后开始使用 [Key Connector](../about-key-connector.md)。
{% endhint %}

## 创建应用程序注册 <a href="#create-an-app-registration" id="create-an-app-registration"></a>

在 Azure 门户中，导航到 **App registrations** 并选择 **New registration** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6NVeq0dGoBAO8bhhE3zvsC/d107017a0858a388fc8a9b5038942608/azure-newapp.png?fm=webp&h=309&q=50&w=892" %}
创建应用程序注册
{% endembed %}

在 **Register an application** 界面上，为您的应用程序指定一个专用于 Bitwarden 的名称并指定哪些帐户能够使用该应用程序。此选择将决定哪些用户可以使用 Bitwarden SSO 登录。

### 注册重定向 URI <a href="#register-a-redirect-uri" id="register-a-redirect-uri"></a>

从导航中选择 **Authentication** ，然后选择 **Add a platform** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1m59mTJwNtfAmQbxIAQBLI/109cf3d0798ecab925ebca62731781e6/azure-redirecturis.png?fm=webp&h=534&q=50&w=1068" %}
注册重定向 URI
{% endembed %}

在配置平台界面上选择 **Web** 选项并在重定向 URI 输入框中输入您的 **Callback Path** 。

{% hint style="info" %}
回调路径可以从 Bitwarden SSO 配置界面中获取。对于云托管客户，这始终为 `https://sso.bitwarden.com/oidc-signin`。对于自托管实例，这取决于您[已配置的服务器 URL](../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain)，例如为 `https://your.domain.com/sso/oidc-signin`。
{% endhint %}

### 创建客户端密钥 <a href="#create-a-client-secret" id="create-a-client-secret"></a>

从导航中选择 **Certificates & secrets**，然后选择 **New client secret** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7wGy3TYoN71TVlDkdvUIMe/5e8d221a695ab34232892b6b309838ed/azure-newcert.png?fm=webp&h=744&q=50&w=1022" %}
创建客户端密钥
{% endembed %}

为证书指定一个专用于 Bitwarden 的名称，并选择一个到期时间范围。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已在 Azure 门户范围内配置好了你所需要的一切。回到 Bitwarden 网页密码库以配置以下字段：

| 字段                                                      | 描述                                                                                                                       |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Authority                                               | 输入 `https://login.microsoft.com/<TENANT_ID>/v2.0`，其中 `TENANT_ID` 是从应用程序注册的 Overview（概览）界面获取到的 **Directory (tenant) ID**。 |
| Client ID                                               | 输入应用程序注册的 **Application (client) ID**，这可以从 Overview（概览）界面中获取。                                                            |
| Client Secret                                           | 输入[已创建的客户端密钥](azure-oidc-implementation.md#create-a-client-secret)的 **Secret Value**。                                    |
| Metadata Address                                        | 对于 Azure 实现，您可以将此字段留空。                                                                                                   |
| OIDC Redirect Behavior                                  | 选择 **Form POST** 或 **Redirect GET**。                                                                                     |
| Get Claims From User Info Endpoint                      | 如果您在 SSO 期间收到 URL 太长错误 (HTTP 414)、截断的 URL 和/或失败，请启用此选项。                                                                  |
| Additional/Custom Scopes                                | 定义要添加到请求中的自定义范围（逗号分隔）。                                                                                                   |
| Additional/Custom User ID Claim Types                   | 为用户标识（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                           |
| Additional/Custom Email Claim Types                     | 为用户的电子邮件地址（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                      |
| Additional/Custom Name Claim Types                      | 为用户的全名或显示名称（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                     |
| Requested Authentication Context Class Reference values | 定义身份验证上下文类引用标识符（`acr_values`）（以空格分隔）。按优先顺序列出 `acr_values`。                                                               |
| Expected “acr” Claim Value in Response                  | 定义 Bitwarden 在响应中期望和验证的 `acr` 声明值。                                                                                       |

完成这些字段的配置后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://images.ctfassets.net/7rncvj1f8mw7/3TjmG99YArRXpsaBHH77Mt/0e4be9262c1a51be449880390ddd19f5/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实现已成功配置，您将被重定向到 Microsoft 登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/j1YuXioPGFIwxsqfxCrpm/d0185848b3812c22940c6c5956e0b2be/az-login.png?fm=webp&h=433&q=50&w=464" %}
Azure 登录界面
{% endembed %}



使用 Azure 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

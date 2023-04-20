---
description: 本文包含为 Okta OIDC 实施配置 Bitwarden SSO 登录的说明。
---

# Okta OIDC 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/oidc-okta/)
{% endhint %}

本文是**专门针对 Okta** 用于配置 OpenID 连接（OIDC） 方式的 SSO 登录的帮助。有关其他 OIDC IdP 方式配置 SSO 登录，或配置 SAML 2.0 方式的 Azure 的帮助，请参阅 [OIDC 配置](../oidc-configuration.md)或 [Okta SAML 实施](okta-saml-implementation.md)。

配置需要在 Bitwarden 网页密码库和 Okta 管理门户网站中同时进行。在您继续进行操作时，我们建议您随时准备好并按照记录的顺序完成步骤。

## 在网页密码库中打开 SSO <a href="#open-sso-in-the-web-vault" id="open-sso-in-the-web-vault"></a>

如果您是直接从 [OIDC 配置](../oidc-configuration.md)过来的，你应该[已经创建了一个组织 ID](../saml-2.0-configuration.md#step-1-set-an-organization-identifier) 并打开了 SSO 配置界面。如果你没有，请参考那篇文章，为 SSO 创建一个组织 ID。

导航到您组织的**管理** → **单点登录**界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6hhSOvtqAuWemfaN78atRv/f7b2d1732a25b110c1b7eb1296637453/sso-oidc1.png?fm=webp&h=612&q=50&w=822" %}
OIDC 配置
{% endembed %}

你不需要编辑此界面上的任何内容，但要保持打开以方便引用。

{% hint style="success" %}
如果您是自托管 Bitwarden，您可以选择性使用**成员解密选项**。此功能默认情况下被禁用，因此现在继续使用**主密码**解密，并了解如何在配置完成并成功运行后开始使用 [Key Connector](../key-connector/about-key-connector.md)。
{% endhint %}

## 创建 Okta 应用程序 <a href="#create-an-okta-app" id="create-an-okta-app"></a>

在 Okta 管理门户中，从导航中选择 **Applications** → **Applications**。在 Applications（应用程序）界面上，选择 **Create App Integration** 按钮。对于 Sign-on method（登录方式），选择 **OIDC - OpenID Connect**。对于 Application type（应用程序类型），选择 **Web Application**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7fGYbP4aawIh8eorrQF6b7/a52951b16123a3e2f4d7bb293ba22a20/okta-createapp.png?fm=webp&h=854&q=50&w=969" %}
创建应用程序集成
{% endembed %}

在 **New Web App Integration** 界面上，配置以下字段：

| 字段                     | 描述                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| App integration name   | 为应用程序指定一个专用于 Bitwarden 的名称。                                                                                                                                                                                                                                                                                                                                    |
| Grant type             | <p>启用以下<a href="https://developer.okta.com/docs/concepts/oauth-openid/#choosing-an-oauth-2-0-flow">授权类型</a>：<br><br>- 代表自己行事的客户 → <strong>Client Credentials</strong><br>- 代表用户行事的客户 → <strong>Authorization Code</strong></p>                                                                                                                                 |
| Sign-in redirect URIs  | <p>将此字段设置为您的 <strong>Callback Path</strong>，这可以从 Bitwarden SSO 配置界面获取。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/oidc-signin</code>。对于自托管实例，这取决于您<a href="../../../on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md#configure-your-domain">已配置的服务器 URL</a>，例如为 </p><p><code>https://your.domain.com/sso/oidc-signin</code>。</p> |
| Sign-out redirect URIs | 将此字段设置为您的 **Signed Out Callback Path**，这可以从 Bitwarden SSO 配置界面获取。                                                                                                                                                                                                                                                                                              |
| Assignments            | 使用此字段指定是所有群组还是仅选定的群组能够使用 Bitwarden SSO 登录。                                                                                                                                                                                                                                                                                                                     |

配置完成后，选择 **Next** 按钮。

### 获取客户端凭据 <a href="#get-client-credentials" id="get-client-credentials"></a>

在 Application 界面上，复制新创建的 Okta 应用程序的 **Client ID** 和 **Client secret**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6Q5iWqSrrXUp4s197bfyRt/d1d85d41c31ce60029d84fa6738372f8/okta-clientcredentials.png?fm=webp&h=582&q=50&w=851" %}
应用程序客户端凭据
{% endembed %}

[在下一步中](okta-oidc-implementation.md#back-to-the-web-vault)将需要使用这两个值。

### 获取授权服务器信息 <a href="#get-authorization-server-information" id="get-authorization-server-information"></a>

从导航中选择 **Security** → **API**。从 **Authorization Servers** 列表中，选择要用于此实现的服务器。在服务器的 **Settings** 选项卡上，复制 **Issuer** 和 **Metadata URI** 值：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7hUKbE9s9HGJUwbqC2W36u/11cee32a7b469a662ae35b9c3cc1a2ba/okta-authserver.png?fm=webp&h=636&q=50&w=866" %}
Okta 授权服务器设置
{% endembed %}

[在下一步中](okta-oidc-implementation.md#back-to-the-web-vault)将需要使用这两个值。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已在 Okta 管理门户范围内配置好了你所需要的一切。回到 Bitwarden 网页密码库以配置以下字段：

| 字段                                                      | 描述                                                                                                 |
| ------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Authority                                               | 为您的授权服务器输入[已获取到到的 Issuer URI](okta-oidc-implementation.md#get-authorization-server-information)。   |
| Client ID                                               | 为您的 Okta 应用程序输入[已获取到的 Client ID](okta-oidc-implementation.md#get-client-credentials)。              |
| Client Secret                                           | 为您的 Okta 应用程序输入[已获取到的 Client secret](okta-oidc-implementation.md#get-client-credentials)。          |
| Metadata Address                                        | 为您的授权服务器输入[已获取到到的 Metadata URI](okta-oidc-implementation.md#get-authorization-server-information)。 |
| OIDC Redirect Behavior                                  | 选择 **Redirect GET**。Okta 目前不支持 Form POST。                                                          |
| Get Claims From User Info Endpoint                      | 如果您在 SSO 期间收到 URL 太长错误 (HTTP 414)、截断的 URL 和/或失败，请启用此选项。                                            |
| Additional/Custom Scopes                                | 定义要添加到请求中的自定义范围（逗号分隔）。                                                                             |
| Additional/Custom User ID Claim Types                   | 为用户标识（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                     |
| Additional/Custom Email Claim Types                     | 为用户的电子邮件地址（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                |
| Additional/Custom Name Claim Types                      | 为用户的全名或显示名称（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                               |
| Requested Authentication Context Class Reference values | 定义身份验证上下文类引用标识符（`acr_values`）（以空格分隔）。按优先顺序列出 `acr_values`。                                         |
| Expected “acr” Claim Value in Response                  | 定义 Bitwarden 在响应中期望和验证的 `acr` 声明值。                                                                 |

完成这些字段的配置后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organization-basics/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://images.ctfassets.net/7rncvj1f8mw7/3TjmG99YArRXpsaBHH77Mt/0e4be9262c1a51be449880390ddd19f5/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 Okta 登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3Rh2Bg17sCE57xJsUKfqwN/4342c56fa656be94ef90dd620251a868/okta-login.png?fm=webp&h=620&q=50&w=427" %}
Okta 登录界面
{% endembed %}

使用 Okta 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

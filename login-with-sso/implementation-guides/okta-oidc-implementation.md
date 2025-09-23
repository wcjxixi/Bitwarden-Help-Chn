---
description: 本文包含为 Okta OIDC 实施配置 Bitwarden SSO 登录的说明。
---

# Okta OIDC 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/oidc-okta/)
{% endhint %}

本文是**专门针对 Okta** 用于配置 OpenID 连接（OIDC） 方式的 SSO 登录的帮助。有关其他 OIDC IdP 方式配置 SSO 登录，或配置 SAML 2.0 方式的 Azure 的帮助，请参阅 [OIDC 配置](../oidc-configuration.md)或 [Okta SAML 实施](okta-saml-implementation.md)。

配置需要在 Bitwarden 网页 App 和 Okta 管理门户网站中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJAUVWIZAAB" %}
产品切换器
{% endembed %}

从导航中选择**设置** → **单点登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?_a=DAJAUVWIZAAB" %}
SAML 2.0 配置
{% endembed %}

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个。否则，您不需要在此界面上编辑任何内容，但保持此界面打开，以方便参考。

{% hint style="success" %}
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建 Okta 应用程序 <a href="#create-an-okta-app" id="create-an-okta-app"></a>

在 Okta 管理门户中，从导航中选择 **Applications** → **Applications**。在 Applications（应用程序）界面上，选择 **Create App Integration** 按钮。对于 Sign-on method（登录方式），选择 **OIDC - OpenID Connect**。对于 Application type（应用程序类型），选择 **Web Application**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7fGYbP4aawIh8eorrQF6b7/a52951b16123a3e2f4d7bb293ba22a20/okta-createapp.png?fm=webp&h=854&q=50&w=969" %}
创建应用程序集成
{% endembed %}

在 **New Web App Integration** 界面上，配置以下字段：

| 字段                     | 描述                                                                                                                                                                                                                                                                                                                                                          |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| App integration name   | 为应用程序指定一个专用于 Bitwarden 的名称。                                                                                                                                                                                                                                                                                                                                 |
| Grant type             | <p>启用以下<a href="https://developer.okta.com/docs/concepts/oauth-openid/#choosing-an-oauth-2-0-flow">授权类型</a>：<br><br>- 代表自己行事的客户 → <strong>Client Credentials</strong><br>- 代表用户行事的客户 → <strong>Authorization Code</strong></p>                                                                                                                              |
| Sign-in redirect URIs  | <p>将此字段设置为您的 <strong>Callback Path</strong>，这可以从 Bitwarden SSO 配置界面获取。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/oidc-signin</code>。对于自托管实例，这取决于您<a href="../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">已配置的服务器 URL</a>，例如为 </p><p><code>https://your.domain.com/sso/oidc-signin</code>。</p> |
| Sign-out redirect URIs | 将此字段设置为您的 **Signed Out Callback Path**，这可以从 Bitwarden SSO 配置界面获取。                                                                                                                                                                                                                                                                                           |
| Assignments            | 使用此字段指定是所有群组还是仅选定的群组能够使用 Bitwarden SSO 登录。                                                                                                                                                                                                                                                                                                                  |

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
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织策略。[了解更多](../../admin-console/manage-shared-items/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**企业单点登录**按钮来进行测试：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BdlHeogd42LEoG06qROyQ/cab8e66d8745059e73c02739d9d2d744/2024-12-02_10-28-02.png?_a=DAJAUVWIZAAB" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Okta 登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3Rh2Bg17sCE57xJsUKfqwN/4342c56fa656be94ef90dd620251a868/okta-login.png?fm=webp&h=620&q=50&w=427" %}
Okta 登录界面
{% endembed %}

使用 Okta 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。Okta 管理员可以创建一个 [Okta Bookmark App](https://support.okta.com/help/s/article/How-do-you-create-a-bookmark-app?language=en_US)，这将直接链接到 Bitwarden 网络密码库登录页面。

1. 作为管理员，进入主导航栏上的 **Applications** 下拉菜单，选择 **Applications**。
2. 点击 **Browse App Catalog**。
3. 搜索 **Bookmark App** 然后单击 **Add Integration**。
4. 向应用程序添加以下设置：
   1. 为应用程序命名，如 **Bitwarden Login**。
   2. 在 **URL** 字段，提供 Bitwarden 客户端的 URL，如 `https://vault.bitwarden.com/#/login` 或 `your-self-hostedURL.com`。
5. 选择 **Done** 并返回应用程序仪表板，编辑新创建的应用程序。
6. 为应用程序分配人员和群组。您还可以为应用程序指定一个徽标，以便最终用户识别。 Bitwarden 徽标可在[此处](https://github.com/bitwarden/brand/tree/master)获取。

完成此过程后，被分配的人员和群组将在其 Okta 面板上拥有一个 Bitwarden 书签应用程序，该应用程序将直接链接到 Bitwarden 网络密码库登录页面。
{% endhint %}

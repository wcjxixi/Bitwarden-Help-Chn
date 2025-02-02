# ADFS OIDC 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/adfs-oidc-implementation/)
{% endhint %}

本文是**专门针对 Active Directory Federation Services (AD FS)** 用于配置 OpenID 连接（OIDC） 方式的 SSO 登录的帮助。有关其他 OIDC IdP 方式配置 SSO 登录，或配置 SAML 2.0 方式的 Azure 的帮助，请参阅 [OIDC 配置](../oidc-configuration.md)或 ADFS SAML 实施。

配置需要在 Bitwarden 网页 App 和 AD FS 服务器管理器中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

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

## 创建应用程序组 <a href="#create-an-application-group" id="create-an-application-group"></a>

在服务器管理器中，导航到 **AD FS Management** 并创建一个新的应用程序组：

1、在控制台树中，选择 **Application Groups**，然后从 Actions 列表中选择 **Add Application Group**。

2、在 Welcome 向导界面上，选择 **Server application accessing a web API**。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5X9h5j0BUUJ39NLtOqarjF/5948faaf2e497cc435b6da0f2e8ce610/adfs-oidc-1.png?fm=webp&h=580&q=50&w=712" %}
AD FS 添加应用程序组
{% endembed %}

3、在 Server Application 界面上：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1e87bYOhKpJ4cWuvlgrRL8/46389fb08be2d247303a55d5e17196d4/adfs-oidc-2.png?fm=webp&h=583&q=50&w=716" %}
AD FS 服务器应用程序界面
{% endembed %}

* 为服务器应用程序起一个 **Name**。
* 记下 **Client Identifier**。在后续步骤中需要此值。
* 指定一个 **Redirect URI**。对于云托管的客户，这始终是 `https://sso.bitwarden.com/oidc-signin`。对于自托管实例，这取决于您配置的服务器 URL，例如 `https://your.domain.com/sso/oidc-signin`。

4、在 Configure Application Credentials 界面上，记下 **Client Secret**。在后续步骤中需要此值。

5、在 Configure Web API 界面上：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/28pMbK9dUI9ZIfcwDaf4Dw/b0572921f857956d3a61077de352c555/adfs-oidc-3.png?fm=webp&h=582&q=50&w=723" %}
AD FS 配置 Web API 界面
{% endembed %}

* 为 Web API 起一个 **Name**。
* 将 **Client Identifier** 和 **Redirect URI**（参见步骤 3）添加到 Identifier list 中。

6、在 Apply Access Control Policy 界面上，为应用程序组设置适当的访问控制策略。

7、在 Configure Application Permissions 界面上，允许范围勾选 `allatclaims` 和 `openid`。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2PvGUtVgRfd0GLx1HG72Is/1e41e84f90fac6b20b4aaf93a9c38069/adfs-oidc-4.png?fm=webp&h=581&q=50&w=716" %}
AD FS 配置应用程序权限界面
{% endembed %}

8、完成添加应用程序组向导。

## 添加转换声明规则 <a href="#add-a-transform-claim-rule" id="add-a-transform-claim-rule"></a>

在服务器管理器中，导航到 **AD FS Management** 然后编辑已创建的应用程序组：

1、在控制台树中，选择 **Application Groups**。

2、在 Application Groups 列表中，右键单击已创建的应用程序组然后选择 **Properties**。

3、在 Applications 部分，选择 Web API 并选择 **Edit...** 。

4、导航到 **Issuance Transform Rules** 选项卡然后选择 **Add Rule...** 按钮。

5、在 Choose Rule Type 界面上，选择 **Send LDAP Attributes as Claims**。

6、在 Configure Claim Rule 界面上：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/67MOJ621dRTvbkVR5gyW7e/044d2b61f1df83069f961d30639f29b3/adfs-oidc-5.png?fm=webp&h=585&q=50&w=717" %}
AD FS 配置声明规则界面
{% endembed %}

* 给规则起一个 **Claim rule name**。
* 从 LDAP Attribute 下拉列表中，选择 **E-Mail-Addresses**。
* 从 Outgoing Claim Type 下拉列表中，选择 **E-Mail Address**。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已经配置好了 AD FS 服务器管理器所需要的一切。回到 Bitwarden 网页密码库以配置以下字段：

| 字段                                                      | 描述                                                                                                                                    |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Authority                                               | 输入附加了 `/adfs` 的 AD FS 服务器的主机名称，例如 `https://adfs.mybusiness.com/adfs`。                                                                 |
| Client ID                                               | 输入[获取到的 Client ID](pingfederate-saml-implementation.md#create-an-application-group)。                                                  |
| Client Secret                                           | 输入[获取到的 Client Secret](pingfederate-saml-implementation.md#create-an-application-group)。                                              |
| Metadata Address                                        | 输入附加了 `/.well-known/openid-configuration` 的指定 **Authority** 值，例如 `https://adfs.mybusiness.com/adfs/.well-known/openid-configuration`。 |
| OIDC Redirect Behavior                                  | 选择 **Redirect GET**。                                                                                                                  |
| Get Claims From User Info Endpoint                      | 如果您在 SSO 期间收到 URL 太长错误 (HTTP 414)、截断的 URL 和/或失败，请启用此选项。                                                                               |
| Custom Scopes                                           | 定义要添加到请求中的自定义范围（逗号分隔）。                                                                                                                |
| Custom User ID Claim Types                              | 为用户标识（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                        |
| Custom Email Claim Types                                | 为用户的电子邮件地址（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                   |
| Custom Name Claim Types                                 | 为用户的全名或显示名称（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                  |
| Requested Authentication Context Class Reference values | 定义身份验证上下文类引用标识符（`acr_values`）（以空格分隔）。按优先顺序列出 `acr_values`。                                                                            |
| Expected “acr” Claim Value in Response                  | 定义 Bitwarden 在响应中期望和验证的 `acr` 声明值。                                                                                                    |

完成这些字段的配置后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://images.ctfassets.net/7rncvj1f8mw7/3TjmG99YArRXpsaBHH77Mt/0e4be9262c1a51be449880390ddd19f5/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 AD FS SSO 登录界面。使用 AD FS 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

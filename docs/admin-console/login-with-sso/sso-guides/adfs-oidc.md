# ADFS OIDC

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/adfs-oidc-implementation/)
{% endhint %}

本文是**专门针对 Active Directory Federation Services (AD FS)** 用于配置 OpenID Connect (OIDC) 方式的 SSO 登录的帮助。有关其他 OIDC IdP 方式配置 SSO 登录，或配置 SAML 2.0 方式的 Azure 的帮助，请参阅 [OIDC 配置](generic-oidc.md)或 [ADFS SAML 实施](adfs-saml-implementation.md)。

配置需要在 Bitwarden 网页 App 和 AD FS 服务器管理器中同时进行。操作过程中，我们建议同时打开这两个界面，并按照文档记录的步骤顺序完成操作。

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden [网页 App](https://bitwarden.com/help/getting-started-webvault/)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

从导航中选择**设置** → **单点登录**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/51wSToXTHHVmBCrLrE8T0E/85aa432ea19eadf0195317f4f233e973/2024-12-04_09-41-46.png?w=1036&#x26;fm=avif" alt=""><figcaption><p>OIDC 配置</p></figcaption></figure></div>

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个。否则，您不需要在此界面上编辑任何内容，保持此界面打开，以方便参考。

{% hint style="success" %}
还可以选择使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建应用程序组 <a href="#create-an-application-group" id="create-an-application-group"></a>

在服务器管理器中，导航到 **AD FS Management** 并创建一个新的应用程序组：

1、在控制台树中，选择 **Application Groups**，然后从 Actions 列表中选择 **Add Application Group**。

2、在向导的欢迎界面上，选择 **Server application accessing a web API** 模版。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5X9h5j0BUUJ39NLtOqarjF/5948faaf2e497cc435b6da0f2e8ce610/adfs-oidc-1.png?w=800&#x26;fm=avif" alt=""><figcaption><p>AD FS 添加应用程序组</p></figcaption></figure></div>

3、在 Server Application 界面上：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1e87bYOhKpJ4cWuvlgrRL8/46389fb08be2d247303a55d5e17196d4/adfs-oidc-2.png?w=800&#x26;fm=avif" alt=""><figcaption><p>AD FS 服务器应用程序界面</p></figcaption></figure></div>

* 为服务器应用程序起一个 **Name**。
* 记下 **Client Identifier**。在后续步骤中需要此值。
* 指定一个 **Redirect URI**。对于云托管的客户，这是 `https://sso.bitwarden.com/oidc-signin` 或 `https://sso.bitwarden.eu/oidc-signin`。对于自托管实例，这取决于您配置的服务器 URL，例如 `https://your.domain.com/sso/oidc-signin`。

4、在 Configure Application Credentials 界面上，记下 **Client Secret**。在后续步骤中需要此值。

5、在 Configure Web API 界面上：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/28pMbK9dUI9ZIfcwDaf4Dw/b0572921f857956d3a61077de352c555/adfs-oidc-3.png?w=800&#x26;fm=avif" alt=""><figcaption><p>AD FS 配置网页 API 界面</p></figcaption></figure></div>

* 为 Web API 起一个 **Name**。
* 将 **Client Identifier** 和 **Redirect URI**（参见步骤 3）添加到 Identifier list 中。

6、在 Apply Access Control Policy 界面上，为应用程序组设置适当的访问控制策略。

7、在 Configure Application Permissions 界面上，允许范围勾选 `allatclaims` 和 `openid`。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2PvGUtVgRfd0GLx1HG72Is/1e41e84f90fac6b20b4aaf93a9c38069/adfs-oidc-4.png?w=800&#x26;fm=avif" alt=""><figcaption><p>AD FS 配置应用程序权限界面</p></figcaption></figure></div>

8、完成添加应用程序组向导。

## 添加转换声明规则 <a href="#add-a-transform-claim-rule" id="add-a-transform-claim-rule"></a>

在服务器管理器中，导航到 **AD FS Management** 然后编辑已创建的应用程序组：

1、在控制台树中，选择 **Application Groups**。

2、在 Application Groups 列表中，右键单击已创建的应用程序组然后选择 **Properties**。

3、在 Applications 部分，选择 Web API 并选择 **Edit...** 。

4、导航到 **Issuance Transform Rules** 选项卡然后选择 **Add Rule...** 按钮。

5、在 Choose Rule Type 界面上，选择 **Send LDAP Attributes as Claims**。

6、在 Configure Claim Rule 界面上：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/67MOJ621dRTvbkVR5gyW7e/044d2b61f1df83069f961d30639f29b3/adfs-oidc-5.png?w=800&#x26;fm=avif" alt=""><figcaption><p>AD FS 配置声明规则界面</p></figcaption></figure></div>

* 给规则起一个 **Claim rule name**。
* 从 LDAP Attribute 下拉列表中，选择 **E-Mail-Addresses**。
* 从 Outgoing Claim Type 下拉列表中，选择 **E-Mail Address**。

7、选择 **Finish**。

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已经配置好了 AD FS 服务器管理器所需要的一切。请返回 Bitwarden 网页 App 配置以下字段：

| 字段                                                      | 描述                                                                                                                                    |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Authority                                               | 输入附加了 `/adfs` 的 AD FS 服务器的主机名称，例如 `https://adfs.mybusiness.com/adfs`。                                                                 |
| Client ID                                               | 输入[获取到的 Client ID](adfs-oidc.md#create-an-application-group)。                                                                         |
| Client Secret                                           | 输入[获取到的 Client Secret](adfs-oidc.md#create-an-application-group)。                                                                     |
| Metadata Address                                        | 输入附加了 `/.well-known/openid-configuration` 的指定 **Authority** 值，例如 `https://adfs.mybusiness.com/adfs/.well-known/openid-configuration`。 |
| OIDC Redirect Behavior                                  | 选择 **Redirect GET**。                                                                                                                  |
| Get Claims From User Info Endpoint                      | 如果您在 SSO 期间收到 URL 太长错误 (HTTP 414)、截断的 URL 和/或失败，请启用此选项。                                                                               |
| Custom Scopes                                           | 定义要添加到请求中的自定义范围（逗号分隔）。                                                                                                                |
| Custom User ID Claim Types                              | 为用户标识（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                        |
| Custom Email Claim Types                                | 为用户的电子邮件地址（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                   |
| Custom Name Claim Types                                 | 为用户的全名或显示名称（逗号分隔）定义自定义声明类型键。定义后，会在返回标准类型之前搜索自定义声明类型。                                                                                  |
| Requested Authentication Context Class Reference values | 定义身份验证上下文类引用标识符（`acr_values`）（以空格分隔）。按优先顺序列出 `acr_values`。                                                                            |
| Expected “acr” Claim Value in Response                  | 定义 Bitwarden 在响应中期望和验证的 `acr` 声明值。                                                                                                    |

完成这些字段的配置后，**保存**您的工作。

{% hint style="success" %}
您可以通过激活[单点登录身份验证策略](../../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)来要求用户使用 SSO 登录。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，然后选择**使用单点登录**按钮进行测试：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3BdlHeogd42LEoG06qROyQ/c68021df4bf45d72e9d37b1fbf5a6040/login.png?w=517&#x26;fm=avif" alt=""><figcaption><p>登录选项界面</p></figcaption></figure></div>

输入[已配置的组织标识符](generic-oidc.md#step-1-set-an-sso-identifier)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 AD FS SSO 的登录界面。使用您的 AD FS 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持未经请求的响应，因此从您的 IdP 发起登录将导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

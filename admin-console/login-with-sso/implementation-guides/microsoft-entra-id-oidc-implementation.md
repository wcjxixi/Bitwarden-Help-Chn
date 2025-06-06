# Microsoft Entra ID OIDC 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/oidc-microsoft-entra-id/)
{% endhint %}

本文是**专门针对 Azure** 用于配置 OpenID 连接（OIDC） 方式的 SSO 登录的帮助。有关其他 OIDC IdP 方式配置 SSO 登录，或配置 SAML 2.0 方式的 Azure 的帮助，请参阅 [OIDC 配置](../../../login-with-sso/oidc-configuration.md)或 [Microsoft Entra ID SAML 实施](microsoft-entra-id-saml-implementation.md)。

配置需要在 Bitwarden 网页 App 和 Azure 门户网站中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

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
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../../login-with-sso/about-key-connector.md)。
{% endhint %}

## 创建应用程序注册 <a href="#create-an-app-registration" id="create-an-app-registration"></a>

在 Azure 门户中，导航到 **Microsoft Entra ID**。要创建新的应用程序注册，请选择 **New registration** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6NVeq0dGoBAO8bhhE3zvsC/d107017a0858a388fc8a9b5038942608/azure-newapp.png?fm=webp&h=309&q=50&w=892" %}
创建应用程序注册
{% endembed %}

完成如下字段：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/fA8tUAnlBC3eu7oKUOi5c/59c6956688f8f6cf84e5a0c1127ccc51/Register_an_application.png?_a=DAJCwlWIZAAB" %}
注册重定向 URI
{% endembed %}

1. 在 **Register an application** 页面，给您的应用程序取一个专用于 Bitwarden 的名称，并指定哪些账户可以使用该应用程序。这一选择将决定哪些用户可以使用 Bitwarden SSO 登录。
2. 从导航中选择 **Authentication**，然后选择 **Add a platform** 按钮。
3. 在配置平台界面上选择 **Web** 选项并在重定向 URI 输入框中输入您的 **Callback Path** 。

{% hint style="info" %}
回调路径可以从 Bitwarden SSO 配置界面中获取。对于云托管客户，这始终为 `https://sso.bitwarden.com/oidc-signin` 或 `https://sso.bitwarden.eu/oidc-signin`。对于自托管实例，这取决于您[已配置的服务器 URL](../../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain)，例如为 `https://your.domain.com/sso/oidc-signin`。
{% endhint %}

### 创建客户端密钥 <a href="#create-a-client-secret" id="create-a-client-secret"></a>

从导航中选择 **Certificates & secrets**，然后选择 **New client secret** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7wGy3TYoN71TVlDkdvUIMe/5e8d221a695ab34232892b6b309838ed/azure-newcert.png?fm=webp&h=744&q=50&w=1022" %}
创建客户端密钥
{% endembed %}

为证书指定一个专用于 Bitwarden 的名称，并选择一个到期时间范围。

### 创建管理员同意 <a href="#create-admin-consent" id="create-admin-consent"></a>

选择 **API permissions** ，然后单击 **✔︎Grant admin consent for {your directory}**。唯一需要的权限是默认添加的 Microsoft Graph > User.Read。

## 返回网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已在 Azure 门户范围内配置好了您所需要的一切。返回 Bitwarden 网页密码库以配置以下字段：

| 字段                                                      | 描述                                                                                                                       |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Authority                                               | 输入 `https://login.microsoft.com/<TENANT_ID>/v2.0`，其中 `TENANT_ID` 是从应用程序注册的 Overview（概览）界面获取到的 **Directory (tenant) ID**。 |
| Client ID                                               | 输入应用程序注册的 **Application (client) ID**，这可以从 Overview（概览）界面中获取。                                                            |
| Client Secret                                           | 输入[已创建的客户端密钥](microsoft-entra-id-oidc-implementation.md#create-a-client-secret)的 **Secret Value**。                       |
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
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../../organizations/enterprise-policies.md)。
{% endhint %}

### 额外的自定义申请类型 <a href="#additional-custom-claim-types" id="additional-custom-claim-types"></a>

如果您的 SSO 配置需要自定义声明类型，则需要额外的步骤才能让 Microsoft Entra ID 识别非标准声明。

1、在 Microsoft Entra ID 上，通过导航到 **Enterprise applications** → **App registrations** → **Token configuration** 来添加自定义申请类型。

2、选择 ✚**Add optional claim**，然后使用选定值创建新的可选声明。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2qFhIkcJvFpLLKyNEEJN5c/1e5477a6fe8cac0760eaa3897f0c208a/optional_claim_Entra.png?_a=DAJCwlWIZAAB" %}
Microsoft Entra ID 自定义声明
{% endembed %}

3、在 Bitwarden SSO 配置屏幕上，在相应的**自定义声明类型**字段中输入自定义声明字段的完全限定路径。例如：`https://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn`。

4、完成配置后，选择**保存**。

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**企业单点登录**按钮来进行测试：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BdlHeogd42LEoG06qROyQ/cab8e66d8745059e73c02739d9d2d744/2024-12-02_10-28-02.png?_a=DAJAUVWIZAAB" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](../../../login-with-sso/saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Microsoft 登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/j1YuXioPGFIwxsqfxCrpm/d0185848b3812c22940c6c5956e0b2be/az-login.png?fm=webp&h=433&q=50&w=464" %}
Azure 登录界面
{% endembed %}



使用 Azure 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

1. 培训您的组织成员如何[使用 SSO 登录](../../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)。


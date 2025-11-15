# Microsoft Entra ID SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/saml-microsoft-entra-id/)
{% endhint %}

本文是**专门针对 Azure** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页 App 和 Azure 控制台中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

{% hint style="success" %}
**已经是 SSO 专家？**&#x8DF3;过本文中的说明，然后下载快速配置以与您自己的配置进行比较。

**⬇️**[快速配置指南](https://assets.ctfassets.net/7rncvj1f8mw7/3dX9IKG6TQ9chQXJaVkP1w/4a84bf2b3a7eb68255e4924de7078b41/Soft_Guides__1_.pdf)
{% endhint %}

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden 网页 App，使用产品切换器打开管理控制台：

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

## 创建企业应用程序 <a href="#create-an-enterprise-application" id="create-an-enterprise-application"></a>

在 Azure 门户中，导航到 **Microsoft Entra ID** 然后从导航菜单中选择 **Enterprise applications**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/69h0vJlyvkF5J6tsKfQ7jd/4994ed3200bdce4b5faea87e1ac2de83/Enterprise_application.png?_a=DAJCwlWIZAAB" %}
企业应用程序
{% endembed %}

选择 **🞤New application** 按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7f6vbFmJRpfwDXbjHNKp1i/c314ef0bcbb68306858fa0f76da1e369/new_application.png?_a=DAJCwlWIZAAB" %}
创建新的应用程序
{% endembed %}

在 Microsoft Entra ID Gallery 界面，选择 **🞤Create your own application** 按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6oF8nrPsl7riqg3jWFDk7N/5cf08062f5656e0aee44ea627a2071c5/Create_your_own_application.png?_a=DAJCwlWIZAAB" %}
创建您自己的应用程序
{% endembed %}

在 Create your own application 界面，为应用程序指定一个唯一的、专用于 Bitwarden 的名称并选择 **Create** 按钮。

### 启用单点登录 <a href="#enable-single-sign-on" id="enable-single-sign-on"></a>

在应用程序概览界面，从导航菜单选择 **Single sign-on**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6Qn48f1wL7TLRfVfr2JG44/1db741ce68225229a69978bbf5a1c3ad/configure_single_sign_on.png?_a=DAJCwlWIZAAB" %}
配置单点登录
{% endembed %}

&#x20;在 Single sign-on 界面，选择 **SAML**。

## SAML 设置 <a href="#saml-setup" id="saml-setup"></a>

### 基本 SAML 配置 <a href="#basic-saml-configuration" id="basic-saml-configuration"></a>

选择 **Edit** 按钮并配置如下字段：

| 字段                                         | 描述                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Identifier (Entity ID)                     | <p>将此字段设置为预先生成的 <strong>SP Entity ID</strong>。<br><br></p>                                                                                                                                                                                                                                                                                           |
| Reply URL (Assertion Consumer Service URL) | <p>将此字段设置为预先生成的 <strong>Assertion Consumer Service (ACS) URL</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并根据设置而有所不同。</p>                                                                                                                                                                                           |
| Sign on URL                                | <p>将此字段设置为用户访问 Bitwarden 的登录 URL。<br><br>对于云托管客户，其始终为 <code>https://vault.bitwarden.com/#/sso</code> 或 <code>https://vault.bitwarden.eu/#/sso</code>。对于自托管实例，这由您<a href="../../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/#/sso</code>。</p> |

### 用户属性 & 声明 <a href="#user-attributes-and-claims" id="user-attributes-and-claims"></a>

Azure 构造的默认声明可用于 SSO 登录，但您可以选择使用此部分来配置 Azure 在 SAML 响应中使用的 NameID 格式。

选择 **Edit** 按钮并选择 **Unique User Identifier (Name ID)** 条目以编辑 NameID 声明：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/12hujApHx80QmzCJnfXXdY/5886d6acc55723d9b2531377048ba89a/desktop.png?_a=DAJCwlWIZAAB" %}
编辑 NameID 声明
{% endembed %}

选项包括默认、电子邮件地址、永久、未指定和 Windows 限定域名。有关详细信息，请参阅 [Microsoft Azure 文档](https://docs.microsoft.com/zh-cn/azure/active-directory/develop/active-directory-saml-claims-customization#editing-nameid)。

### SAML 签名证书 <a href="#saml-signing-certificate" id="saml-signing-certificate"></a>

下载 Base64 证书以在[后续步骤中](microsoft-entra-id-saml-implementation.md#identity-provider-configuration)使用。

### 设置您的应用程序 <a href="#set-up-your-application" id="set-up-your-application"></a>

复制或记下此部分中的 **Login URL** 和 **Azure AD Identifier**，以在[后续步骤中](microsoft-entra-id-saml-implementation.md#identity-provider-configuration)使用：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NZm0dZkDOJ6UbUu5lgtex/427c7467486c8135d6f51d5fb158e7da/Azure_URLS.png?_a=DAJCwlWIZAAB" %}
Azure URL
{% endembed %}

{% hint style="info" %}
如果在 SSO 登录时收到任何密钥错误，请尝试从联邦元数据 XML 文件中复制 X509 证书信息。
{% endhint %}

### 用户和群组 <a href="#users-and-groups" id="users-and-groups"></a>

从导航菜单选择 **Users and Groups**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6hYTEc8obu4V8EYLx35iGY/027a0345a5743b75b7b964ac538b9504/az-assign.png?fm=webp&h=524&q=50&w=1028" %}
分配用户或群组
{% endembed %}

选择 **Add user/group** 按钮，以分配用户或群组级别对 SSO 登录应用程序的访问权限。

## 返回网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，你已经在 Azure 门户范围内配置好了你所需要的一切。返回 Bitwarden 网页 App 来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

配置以下字段：

| 字段                                 | 描述                                                                                                                                                            |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | 默认，Azure 将使用电子邮件地址。如果您更改[这个设置](microsoft-entra-id-saml-implementation.md#user-attributes-and-claims)，请选择对应的值。否则，请将此字段设置为 **Unspecified** 或 **Email Address**。 |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                                                                                    |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                                                                                             |
| Minimum Incoming Signing Algorithm | 默认，Azure 将使用 RSA SHA-256 签名。请从下拉列表中选择 `rsa-sha256`。                                                                                                           |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名                                                                                                                                     |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                                                                    |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 Azure 门户以获取应用程序的值：

| 字段                                        | 描述                                                                                                                                                                                                                                          |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | 输入从 Azure 门户的[设置您的应用程序](microsoft-entra-id-saml-implementation.md#set-up-your-application)部分获取到的 **Azure AD Identifier**。                                                                                                                   |
| Binding Type                              | 设置为 **HTTP POST** 或 **Redirect**。                                                                                                                                                                                                           |
| Single Sign On Service URL                | 输入从 Azure 门户的[设置您的应用程序](microsoft-entra-id-saml-implementation.md#set-up-your-application)部分获取到的 **Login URL**。                                                                                                                             |
| Single Log Out Service URL                | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发，但如果您需要，可以将其预先配置为 **Logout URL**。                                                                                                                                                                           |
| Artifact Resolution Service URL           | Azure 当前不支持 Artifact 绑定，因此请将此字段留空。                                                                                                                                                                                                          |
| X509 Public Certificate                   | <p>黏贴<a href="microsoft-entra-id-saml-implementation.md#saml-signing-certificate">已下载的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 默认，Azure 将使用 RSA SHA-256 签名。请从下拉列表中选择 `rsa-sha256`。                                                                                                                                                                                         |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                                        |
| Disable Outbound Logout Requests          | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                                           |
| Want Authentication Requests Signed       | Azure 是否要求 SAML 请求被签名。                                                                                                                                                                                                                      |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../oversight-visibility/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**企业单点登录**按钮来进行测试：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BdlHeogd42LEoG06qROyQ/cab8e66d8745059e73c02739d9d2d744/2024-12-02_10-28-02.png?_a=DAJAUVWIZAAB" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Microsoft 的登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/j1YuXioPGFIwxsqfxCrpm/d0185848b3812c22940c6c5956e0b2be/az-login.png?fm=webp&h=433&q=50&w=464" %}
Azure 登录界面
{% endembed %}

使用您的 Azure 凭据进行身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。Entra ID SAML 管理员可以为用户设置一个[应用程序注册](https://learn.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy-configure-custom-home-page)，将其引导到 Bitwarden 网络密码库登录页面：

1. 通过导航到当前的 Bitwarden 企业应用程序，选择 **Properties** 并将 **Visible to users** 选项设置为 **No**，禁用 **All Applications** 页面中现有的 Bitwarden 按钮。
2. 在 **App Registrations** 中选择 **New Registration**，创建新的应用程序注册。
3. 为应用程序提供一个名称，如 **Bitwarden SSO**，但不要指定重定向 URL。选择 **Register** 完成表格。
4. 应用程序创建完成后，导航至导航菜单上的 **Branding & Properties**。
5. 向应用程序添加以下设置：
   1. 上传一个用于终端用户识别的徽标。您可以在[此处](https://github.com/bitwarden/brand)获取 Bitwarden 徽标。
   2. 将**主页 URL** 设为 Bitwarden 客户端登录页面，如 `https://vault.bitwarden.com/#/login`。

完成此过程后，分配的用户将拥有一个直接链接到 Bitwarden 网络密码库登录页面的 Bitwarden 应用程序。
{% endhint %}

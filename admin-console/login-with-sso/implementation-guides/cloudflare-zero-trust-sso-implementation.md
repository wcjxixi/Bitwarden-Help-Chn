# =Cloudflare Zero Trust SSO 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/cloudflare-zero-trust-sso-implementation/)
{% endhint %}

本文是**专门针对 Cloudflare Zero Trust** 用于配置 SSO 登录的帮助。Cloudflare Zero Trust 是一个基于云的身份和访问管理平台，可与多个身份提供程序 (IdP) 集成。您还可以配置安全访问平台的网关和隧道。

{% hint style="info" %}
Cloudflare Zero Trust 可与任何使用 SAML 2.0 或 OIDC SSO 配置的 IdP 一起配置。如果您不熟悉这些配置，请参阅这些文章：

* [SAML 2.0 配置](../../../login-with-sso/saml-2.0-configuration.md)
* [OIDC 配置](../../../login-with-sso/oidc-configuration.md)
{% endhint %}

## 为什么要使用 Cloudflare Zero Trust SSO？ <a href="#why-use-cloudflare-zero-trust-with-sso" id="why-use-cloudflare-zero-trust-with-sso"></a>

Cloudflare Zero Trust 是一个基于云的代理身份和访问管理平台，可与多个身份提供程序 (IdP) 集成。除了标准 IdP 外，使用 Cloudflare Zero Trust 的好处在于它能够为登录配置多个 IdP。Cloudflare Zero Trust 可以从多个单独的目录或一个目录中的用户集提供对 Bitwarden 的 SSO 访问。

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

{% hint style="info" %}
Cloudflare 仅支持通过访问应用网关的 SAML。这意味着必须在 Bitwarden 配置中选择 SAML 2.0。OIDC 身份验证仍可通过 IdP 和 Cloudflare 进行配置。
{% endhint %}

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
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../../login-with-sso/about-key-connector.md)。
{% endhint %}

## 创建 Cloudflare Zero Trust 登录方法 <a href="#create-a-cloudflare-zero-trust-login-method" id="create-a-cloudflare-zero-trust-login-method"></a>

## 创建 Cloudflare Zero Trust  应用程序 <a href="#create-a-cloudflare-zero-trust-application" id="create-a-cloudflare-zero-trust-application"></a>

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**企业单点登录**按钮来进行测试：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BdlHeogd42LEoG06qROyQ/cab8e66d8745059e73c02739d9d2d744/2024-12-02_10-28-02.png?_a=DAJAUVWIZAAB" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](../../../login-with-sso/saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Cloudflare Access 界面，您可以在其中选择登录要使用的 IDP：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5SyHu8lc0ZJqjpL4hF53ie/b0d661e6772b58f681c47b7b01ebbaa0/Screen_Shot_2022-10-12_at_5.15.39_PM__2_.png?_a=DAJCwlWIZAAB" %}
Cloudflare IdP 选择
{% endembed %}

选择 IdP 后，系统将引导您进入 IdP 登录页面。输入通过 IdP 登录时使用的信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7Avc5GWZaeGSk59v3rZ531/3be901d4f137012ef6d1e3cb13d9a4eb/Screen_Shot_2022-10-13_at_4.45.02_PM.png?_a=DAJCwlWIZAAB" %}
CFZT IdP 登录
{% endembed %}

使用 IdP 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

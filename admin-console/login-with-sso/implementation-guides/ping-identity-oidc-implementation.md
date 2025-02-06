# =Ping Identity OIDC 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ping-identity-oidc-implementation/)
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

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个。否则，您不需要在此界面上编辑任何内容，但保持此界面打开，以方便参考。

{% hint style="success" %}
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../../login-with-sso/about-key-connector.md)。
{% endhint %}

## 创建 OIDC App <a href="#create-saml-app" id="create-saml-app"></a>

### 添加应用程序 <a href="#add-application" id="add-application"></a>

### 配置应用程序 <a href="#configure-application" id="configure-application"></a>

## 资源 <a href="#resources" id="resources"></a>

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**企业单点登录**按钮来进行测试：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BdlHeogd42LEoG06qROyQ/cab8e66d8745059e73c02739d9d2d744/2024-12-02_10-28-02.png?_a=DAJAUVWIZAAB" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](../../../login-with-sso/saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Microsoft 登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/j1YuXioPGFIwxsqfxCrpm/d0185848b3812c22940c6c5956e0b2be/az-login.png?fm=webp&h=433&q=50&w=464" %}
Azure 登录界面
{% endembed %}



使用 P凭nP据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

1. 培训您的组织成员如何[使用 SSO 登录](../../../login-with-sso/using-login-with-sso.md)。

# Ping Identity OIDC

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ping-identity-oidc-implementation/)
{% endhint %}

本文是**专门针对 Ping Identity** 用于配置 OpenID Connect (OIDC) 方式的 SSO 登录的帮助。有关其他 OIDC IdP 方式配置 SSO 登录，或配置 SAML 2.0 方式的 Ping Identity 的帮助，请参阅 [OIDC 配置](generic-oidc.md)或 [Ping Identity SAML 部署](../../manage-members/scim/ping-identity-scim-integration.md)。

配置需要在 Bitwarden 网页 App 和 Ping Identity 管理员门户网站中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

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
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建 OIDC App <a href="#create-saml-app" id="create-saml-app"></a>

在 Ping Identity 管理员门户网站，选择 **Application** 和屏幕上方的 ✚图标以打开 **Add Application** 界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3upFJSqFSgStI3FB5hSIDH/0714a45788207aed199dc3f3df78e6dd/2024-07-22_16-14-00.png?_a=DAJCwlWIZAAB" %}
Ping Identity OIDC App
{% endembed %}

### 添加应用程序 <a href="#add-application" id="add-application"></a>

1、在 **Application Name** 字段中输入 Bitwarden 专用名称。还可根据需要添加所需的详细说明。

2、选择 **OIDC Web App** 选项，完成后选择 **Save**。

### 配置应用程序 <a href="#configure-application" id="configure-application"></a>

在 Application 界面，选择 **Configuration** 选项卡，然后选择屏幕右上方的 **Edit** 按钮。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7JxMu92pW8hFkRV7Mmh5Qr/870237c0d0580c7407973aeef0109d2c/2024-07-25_11-30-30.png?_a=DAJCwlWIZAAB" %}
Ping OIDC 配置编辑
{% endembed %}

在 Edit 界面，填写从 Bitwarden 单点登录界面获取的以下值：

| Ping Identity 字段 | 描述                                     |
| ---------------- | -------------------------------------- |
| Redirect URIs    | 复制并粘贴从 Bitwarden 单点登录页面获取的**回调路径**值。   |
| Signoff URLs     | 复制并粘贴从 Bitwarden 单点登录页面获取的**注销回调路径**值。 |

完成此步骤后，选择 **Save** 并返回 Ping Identity Application 界面上的 **Configuration** 选项卡。该界面上的其他值无需编辑。

## 资源 <a href="#resources" id="resources"></a>

在 Ping Identity Application 页面的 Resources 选项卡上，选择 **edit** 图标并启用以下允许范围：

* mail
* openid

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已在 Ping Identity 环境中配置好了您所需要的一切。请返回 Bitwarden 网页 App 配置以下字段：

| 值                                                       | 描述                                                                                             |
| ------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Authority                                               | 输入 `https://auth.pingone.eu/<TENANT_ID>`，其中 `TENANT_ID` 是 Ping Identity 上的 **Environment ID**。 |
| Client ID                                               | 输入从应用程序配置选项卡获取的应用程序**客户端 ID**。                                                                 |
| Client Secret                                           | 输入创建的客户端机密的机密值。在应用程序的配置选项卡上选择 **Generate New Secret**。                                         |
| Metadata Address                                        | 对于 Ping Identity 实施，您可以将此字段留空。                                                                 |
| OIDC Redirect Behavior                                  | 选择 **Form POST** 或 **Redirect GET**。                                                           |
| Get Claims From User Info Endpoint                      | 如果在 SSO 过程中收到 URL 太长错误（HTTP 414）、信任 URL 和/或失败，请启用此选项。                                          |
| Additional/Custom Scopes                                | 定义要添加到请求中的自定义作用域（以逗号分隔）。                                                                       |
| Additional/Custom Email Claim Types                     | 为用户的地址地址定义自定义声明类型键（以逗号分隔）。定义后，会先搜索自定义声明类型，然后再返回标准类型。                                           |
| Additional/Custom Name Claim Types                      | 为用户全名或显示名定义自定义声明类型键（以逗号分隔）。定义后，会先搜索自定义声明类型，然后再返回标准类型。                                          |
| Requested Authentication Context Class Reference values | 定义身 Authentication Context Class Reference 标识符 (`acr_values`)（以空格分隔）。按优先顺序列出 `acr_values`。     |
| Expected "acr" Claim Value in Response                  | 为 Bitwarden 定义在响应中预期和验证的 `acr` 声明值。                                                            |

完成这些字段的配置后，**保存**您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织策略。[了解更多](../../oversight-visibility/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**使用单点登录**按钮来进行测试：

{% embed url="https://bitwarden.com/assets/3BdlHeogd42LEoG06qROyQ/c68021df4bf45d72e9d37b1fbf5a6040/login.png?w=517&fm=avif" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](generic-oidc.md#step-1-set-an-sso-identifier)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Ping Identity 登录界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1QwyIzAp4JtyGwNLXZNXFI/6d1cc0ca3f278f46d7ad251ff2898dd4/2024-07-22_12-18-19.png?_a=DAJCwlWIZAAB" %}
Ping Identity SSO
{% endembed %}

使用 Ping 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

1. 培训您的组织成员如何[使用 SSO 登录](../../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)。

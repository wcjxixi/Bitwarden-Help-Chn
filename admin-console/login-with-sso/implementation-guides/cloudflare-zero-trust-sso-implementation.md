# Cloudflare Zero Trust SSO 实施

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
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建 Cloudflare Zero Trust 登录方法 <a href="#create-a-cloudflare-zero-trust-login-method" id="create-a-cloudflare-zero-trust-login-method"></a>

创建 Cloufdlare Zero Trust 登录方法：

1、导航至 [Cloudflare Zero Trust](https://dash.cloudflare.com/login) 然后登录或创建账户。

2、配置一个域名，作为用户访问应用程序或**应用程序启动器**的 URL，例如 `https://my-business.cloudflareaccess.com/`。从 Cloudflare Zero Trust 菜单中选择**设置** → **自定义页面**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4lN2NFw46RAynArFfiW3kD/6dfd8ef5b844347a60f9e230b9736450/2024-12-16_15-43-43.png?_a=DAJCwlWIZAAB" %}
团队域名设置
{% endembed %}

3、导航至**设置** → **身份验证** → **添加新内容**，开始配置第一种登录方法。

4、选择连接到 Cloudflare Zero Trust 的登录方法。如果您使用的 IdP 不在 IdP 列表中，请使用 SAML 或 OIDC 通用选项。本文将以 Okta 为例：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5Zk3txh2X9fhcPVpMZVJPC/18ad36aaf277af50df063c96f89804e8/Screen_Shot_2022-10-11_at_4.17.21_PM.png?_a=DAJCwlWIZAAB" %}
Cloudflare Zero Trust IdP 列表
{% endembed %}

{% hint style="info" %}
Google Workspace 用户应在此步骤中选择通用 **SAML** 设置。Google Workspace 登录方法可能会导致错误。
{% endhint %}

5、选择所选 IdP 登录方法后，请按照 Cloudflare 提供的产品内指南集成您的 IdP。

{% hint style="info" %}
如果您使用的 IdP 具有**支持群组**的功能，则必须**禁用**此选项。Bitwarden 不支持基于群组的声明，启用该选项将导致 Bitwarden 端出现 XML 元素错误。
{% endhint %}

## 创建 Cloudflare Zero Trust  应用程序 <a href="#create-a-cloudflare-zero-trust-application" id="create-a-cloudflare-zero-trust-application"></a>

配置好 IdP 后，您需要为 Bitwarden 创建一个 Cloudflare Zero Trust 应用程序。在本例中，我们将创建一个 SAML 应用程序：

1、导航至**访问权限** → **应用程序** → **添加应用程序**，然后选择 **SaaS**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/70oK8FUQYXpKEvX00NZ9ai/a065258c17b5b01360a6aed574ce2192/2024-07-08_10-46-37.png?_a=DAJCwlWIZAAB" %}
Cloufflare Zero Trust 添加应用程序
{% endembed %}

2、在下一个界面，添加应用程序名称，如 **Bitwarden**。然后，选择身份验证协议为 **SAML**。完成后，选择**添加应用程序**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1zm03fKF8Nqu30YbH7duoo/58e66188a1437c3339daee414d7f9bb3/2024-07-08_10-43-34.png?_a=DAJCwlWIZAAB" %}
Cloufflare Zero Trust 添加应用程序
{% endembed %}

3、在 Bitwarden 网页密码库中，打开您的组织并导航至**设置** → **单点登录**页面。使用来自网页密码库中的信息填写**配置应用程序**界面上的信息：

| 键                                  | 描述                                                |
| ---------------------------------- | ------------------------------------------------- |
| **Application**                    | 输入 `Bitwarden`.                                   |
| **Entity ID**                      | 将 Bitwarden 单点登录页面上的 **SP 实体 ID** 复制到此字段。         |
| **Assertion Consumer Service URL** | 将 Bitwarden 单点登录页面上的**断言消费者服务 (ACS)** URL 复制到此字段。 |
| **Name ID Format**                 | 从下拉菜单中选择**电子邮箱**。                                 |

{% hint style="info" %}
对于通用 OIDC 配置，Auth URL、令牌 URL 和证书 URL 可通过众所周知的 URL 定位。
{% endhint %}

4、向下滚动到**身份提供程序**菜单。选择您在上一节中配置的 IdP，向后滚动到顶部，然后选择**下一步**。

5、接下来，创建用户访问应用程序的访问策略。为每个策略填写**策略名称**、**操作**和**会话持续时间**字段。

6、您可以选择指定组策略（**访问权限** → **群组**）或明确的用户策略规则（如电子邮箱、「mails ending in」、「country」 或 「everyone」）。在下面的示例中，"匿名用户 "组已包含在策略中。还添加了一条附加规则，以包括以所选域名结尾的电子邮件：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2VCZsMzbeUtuO9jx1oh6g7/a1fbe343872934b796ce486cf46835fb/Screen_Shot_2022-10-12_at_10.55.31_AM.png?_a=DAJCwlWIZAAB" %}
Cloufflare Zero Trust 应用程序策略
{% endembed %}

{% hint style="info" %}
您还可以通过**应用程序启动器**申请应用用户访问权限，以使用 SSO 快捷方式访问 Bitwarden 登录。这可以通过导航至**身份验证** → **应用程序启动器** → **管理**进行管理。上例中的应用策略可在这里复制或生成。
{% endhint %}

7、配置好访问策略后，滚动到顶部并选择**下一步**。

8、在**设置**页面，复制以下值并将其输入 Bitwarden **单点登录**页面的相应字段：

| 键                              | 描述                                                                                                   |
| ------------------------------ | ---------------------------------------------------------------------------------------------------- |
| **SSO endpoint**               | <p>SSO 端点指示 SaaS 应用程序向何处发送登录请求。</p><p></p><p>此值将被输入到 Bitwarden 的<strong>单点登录服务 URL</strong> 字段中。</p> |
| **Access Entity ID or Issuer** | <p>访问实体 ID 或发行者是 SaaS 应用程序的唯一标识符。</p><p></p><p>该值将被输入到 Bitwarden 的<strong>实体 ID</strong> 字段中。</p>    |
| **Public key**                 | <p>公钥是用于验证您身份的访问公共证书。</p><p></p><p>该值将输入到 Bitwarden 的 <strong>X509 公共证书</strong>字段中。</p>             |

9、将值输入 Bitwarden 后，在 Bitwarden 单点登录屏幕上选择**保存**，然后在 Cloudflare 页面上选择**完成**以保存应用程序。

10、要在 Bitwarden 使用 SSO 登录页面创建书签，请选择**添加应用程序** → **书签**。检查书签是否在**应用程序启动器**中可见。

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

# Ping Identity SAML

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ping-identity-saml-implementation/)
{% endhint %}

本文是**专门针对 Ping Identity** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](generic-saml.md)。

配置需要在 Bitwarden 网页 App 和 Ping Identity 管理门户网站中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden 网页 App，然后使用产品切换器打开管理控制台：

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

## 创建 SAML 应用程序 <a href="#create-saml-app" id="create-saml-app"></a>

在 Ping Identity 管理员门户中，选择 **Application** 和屏幕上方的 ✚图标以打开 **Add Application** 界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6F36iKjI660tvX77XXXaOn/d983daff3168cca8b19da3d4ff2b934b/new_application.png?_a=DAJCwlWIZAAB" %}
Ping Identity 添加应用程序
{% endembed %}

1、在 **Application Name** 字段中输入 Bitwarden 专用名称。可根据需要添加所需的详细说明。

2、选择 **SAML Application** 选项，完成后再选择 **Configure**。

3、在 **SAML Configuration** 界面上选择 **Manually Enter**。使用 Bitwarden 单点登录界面上的信息配置以下字段：

| 字段        | 描述                                                                                                                                           |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| ACS URL   | <p>将此字段设置为预先生成的<strong>断言消费者服务 (ACS) URL</strong>。</p><p></p><p>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并根据设置而有所不同。</p> |
| Entity ID | <p>将此字段设置为预先生成的 <strong>SP 实体 ID</strong>。</p><p></p><p>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并根据设置而有所不同。</p>         |

选择 **Save** 以继续。

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已经在 Ping Identity 管理员门户范围内配置好了您所需要的一切。请返回 Bitwarden 网页 App 完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据 Ping Identity 应用程序 **Configuration** 页面提供的信息配置以下字段：

| 字段                                 | 描述                                                                                           |
| ---------------------------------- | -------------------------------------------------------------------------------------------- |
| Name ID Format                     | 将该字段设置为 Ping Identity 应用程序配置中指定的 **Subject Name ID** **Format**。                             |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                   |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                            |
| Minimum Incoming Signing Algorithm | 默认情况，Ping Identity 将使用 RSA SHA-256 签名。请从下拉列表中选择 `sha-256`。                                   |
| Expect signed assertions           | Bitwarden 是否要求 SAML 声明被签名。此设置应为**未选中**。                                                      |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此复选框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。 |

完成服务提供程序配置部分后，**保存**您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要您返回 Ping Identity Configuration 界面以获取应用程序的值：

| 字段                                  | 描述                                                                                                                                                                          |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                           | 设置为从 Ping Identity Configuration 界面获取到的 **Entity ID**。                                                                                                                      |
| Binding Type                        | 设置为 **HTTP POST** 或 **Redirect**。                                                                                                                                           |
| Single Sign On Service URL          | 设置为从 Ping Identity Configuration 界面获取到的 **Single Sign-on Service** URL。                                                                                                     |
| Single Log Out Service URL          | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发，但如果您需要，可以将其预先配置。                                                                                                                           |
| X509 Public Certificate             | <p>粘贴从应用程序界面获取的签名证书。移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>证书值区分大小写，多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm          | 默认，Ping Identity 将使用 RSA SHA-256 签名。请从下拉列表中选择 `sha-256`。                                                                                                                    |
| Disable Outbound Logout Requests    | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                           |
| Want Authentication Requests Signed | Ping Identity 是否要求 SAML 请求被签名。                                                                                                                                              |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**保存**您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织策略。[了解更多](../../oversight-visibility/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**使用单点登录**按钮来进行测试：

{% embed url="https://bitwarden.com/assets/3BdlHeogd42LEoG06qROyQ/c68021df4bf45d72e9d37b1fbf5a6040/login.png?w=517&fm=avif" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](generic-saml.md#step-1-set-an-organization-identifier)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Ping Identity 登录界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1QwyIzAp4JtyGwNLXZNXFI/6d1cc0ca3f278f46d7ad251ff2898dd4/2024-07-22_12-18-19.png?_a=DAJCwlWIZAAB" %}
Ping Identity SSO
{% endembed %}

使用 Ping 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

1. 培训您的组织成员如何[使用 SSO 登录](../../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)。

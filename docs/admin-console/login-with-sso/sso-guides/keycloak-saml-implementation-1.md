# Keycloak SAML

{% hint style="success" %}
Name对应的[官方文档地址](https://bitwarden.com/help/article/saml-keycloak/)
{% endhint %}

本文是**专门针对 Keycloak** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](generic-saml.md)。

配置需要在 Bitwarden 网页 App 和 Keycloak 门户网站中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

{% hint style="success" %}
**已经是 SSO 专家？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/6SVuB4OSxNq6QzGkuqGUd8/5ac1881e660cb456a60ca0da8433e814/saml-keycloak-sample.zip)
{% endhint %}

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden 网页 App，然后使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJAUVWIZAAB" %}
产品切换器
{% endembed %}

打开组织的**设置** → **单点登录**界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?_a=DAJAUVWIZAAB" %}
SAML 2.0 配置
{% endembed %}

如果还没有为您的组织创建专属的 **SSO 标识符**，请创建一个，然后从**类型**下拉菜单中选择 **SAML**。保持此界面打开，以方便参考。

如果愿意，您可以在此阶段关闭**设置专属的 SP 实体 ID** 选项。这样做会从 SP 实体 ID 值中移除组织 ID，但大多数情况下都建议打开该选项。

{% hint style="success" %}
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## Keycloak 设置 <a href="#keycloak-setup" id="keycloak-setup"></a>

登录到 Keycloak 然后选择 **Clients** → **Create Client**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2bBUv6v2343MxtsXC09lvm/1d3c30e4fbe95941ed0d8303f888a885/create_client.png?_a=DAJCwlWIZAAB" %}
创建客户端
{% endembed %}

在 Create Client 界面上，配置以下设置：

| 字段          | 描述                                                                                                                                 |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Client type | 选择 SAML。                                                                                                                           |
| Client ID   | <p>将此字段设置为预先生成的 <strong>SP 实体 ID</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并且会根据您的设置而有所不同。</p> |
| Name        | 输入您为 Keycloak 客户端选择的名称。                                                                                                            |

填写完 **General Settings** 页面的必填字段后，单击 **Next**。

在 **Login settings** 页面，填写以下字段：

| 字段                  | 描述                                                                                                                                            |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Valid Redirect URLs | <p>将此字段设置为预先生成的<strong>断言消费者服务 (ACS) URL</strong>。<br></p><p>此自动生成的值可以从组织的<strong>设置</strong> → 单<strong>点登录</strong>界面复制，并且会根据您的设置而有所不同。</p> |

选择 **Save**。

选择 Keys 选项卡，将 **Client signature required** 选项切换为 **Off**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/RZd8WRbn45BIbiyqN7UzR/1337005dbd6c68e1d8b68ee99b1dcdc9/keys_confifg.png?_a=DAJCwlWIZAAB" %}
Keycloak 密钥配置
{% endembed %}

最后，在 Keycloak 主导航上选择 **Realm settings**，然后选择 **Keys** 选项卡。找到 **RS256** 证书并选择 **Certificate**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2Codsw3P2MWiMHRctDckTF/fc55404f24ceade2663cdef01caa7528/2023-09-25_16-33-13.png?_a=DAJCwlWIZAAB" %}
Keycloak RS256 证书
{% endembed %}

[后面的章节](keycloak-saml-implementation-1.md#back-to-the-web-app)将需要此证书的值。

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已经在 Keycloak 门户网站范围内配置好了您所需要的一切。请返回 Bitwarden 网页 App，然后从导航中选择**设置** → **单点登录**。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

在 **SAML 服务提供程序配置**部分完成以下字段：

| 字段                                 | 描述                                                                                                                                     |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | 选择 **Email Address**。                                                                                                                  |
| Outbound Signing Algorithm         | Bitwarden 用来签署 SAML 请求的算法。                                                                                                             |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                                                                      |
| Minimum Incoming Signing Algorithm | 选择 Keycloak 客户端[被配置为用于](keycloak-saml-implementation-1.md#additional-keycloak-settings)签署 SAML 文档或声明的算法。                               |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名。如果开启，请确保配置了 Keycloak 客户端的 [Sign Assertions](keycloak-saml-implementation-1.md#additional-keycloak-settings)。 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                                             |

在 **SAML 身份提供程序配置**部分完成以下字段：

| 字段                                  | 描述                                                                                                                                                                                                                                            |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                           | 输入之前在客户端上创建的 Keycloak 领域的 URL，例如 `https://<keycloak_domain>/realms/<realm_name`。此字段区分大小写。                                                                                                                                                     |
| Binding Type                        | 选择 **Redirect**。                                                                                                                                                                                                                              |
| Single Sign On Service URL          | 输入您的主 SAML 处理 URL，例如 `https://<keycloak_domain>/realms/<realm_name>/protocol/saml`。                                                                                                                                                           |
| Single Log Out Service URL          | SSO 登录当前**不支持** SLO。该选项计划未来开发，但是如果您愿意，可以将其预先配置为您的 **Logout URL**。                                                                                                                                                                             |
| X509 Public Certificate             | <p>黏贴<a href="keycloak-saml-implementation-1.md#download-your-certificate">已下载的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>证书值区分大小写，多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm          | 选择 Keycloak 客户端[被配置为用于](keycloak-saml-implementation-1.md#settings)签署 SAML 文档或声明的算法。                                                                                                                                                          |
| Disable Outbound Logout Requests    | SSO 登录当前**不支持** SLO。该选项计划未来开发。                                                                                                                                                                                                                |
| Want Authentication Requests Signed | Keycloak 是否要求 SAML 请求被签名。                                                                                                                                                                                                                     |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**保存**您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织策略。[了解更多](../../oversight-visibility/enterprise-policies.md)。
{% endhint %}

## 其他 Keycloak 设置 <a href="#additional-keycloak-settings" id="additional-keycloak-settings"></a>

在 Keycloak 客户端设置选项卡上，还有其他配置选项可用：

| 字段                  | 描述                                      |
| ------------------- | --------------------------------------- |
| Sign Documents      | 指定 SAML 文档是否应由 Keycloak 领域签署。           |
| Sign Assertions     | 指定 SAML 断言是否应由 Keycloak 领域签名。           |
| Signature Algorithm | 如果启用了**签署断言**，请选择要签署的算法（默认为 `sha-256`）。 |
| Name ID Format      | 选择 Keycloak 在 SAML 响应中使用的名称 ID 格式。      |

完成设置后，选择**保存**。

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**使用单点登录**按钮来进行测试：

{% embed url="https://bitwarden.com/assets/3BdlHeogd42LEoG06qROyQ/c68021df4bf45d72e9d37b1fbf5a6040/login.png?w=517&fm=avif" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](generic-saml.md#step-1-set-an-organization-identifier)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Keycloak 登录界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1FOJPAvRf0NCpJleOtMA8e/cc981e5933250dcab63a3f518370a24f/keycloak-login.png?_a=DAJCwlWIZAAB" %}
Keycloak 登录界面
{% endembed %}

使用 Keycloak 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

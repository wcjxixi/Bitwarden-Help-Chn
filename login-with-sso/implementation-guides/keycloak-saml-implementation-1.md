# =Keycloak SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-keycloak/)
{% endhint %}

本文是**专门针对 Keycloak** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页 App 和 Keycloak 门户网站中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

{% hint style="success" %}
**已经是 SSO 专家？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/6SVuB4OSxNq6QzGkuqGUd8/5ac1881e660cb456a60ca0da8433e814/saml-keycloak-sample.zip)
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
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 和 [Key Connector](../about-key-connector.md)。
{% endhint %}

## 创建客户端 <a href="#create-a-client" id="create-a-client"></a>

在 Keycloak 门户中，创建一个新的客户端：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2bBUv6v2343MxtsXC09lvm/715000043c6152c7c11b60dfe22d4ca6/keycloak-createclient.png?fm=webp&h=645&q=50&w=1320" %}
创建客户端
{% endembed %}

在 **Add Client** 界面上，配置以下设置：

| 字段                   | 描述                                                                                                                                                                                                                                                                                                                                         |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Client ID            | <p>将此字段设置为从 Bitwarden SSO 配置界面中预先生成的 <strong>SP Entity ID</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2</code>；对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2</code>。</p> |
| Client Protocol      | 选择 `saml`。                                                                                                                                                                                                                                                                                                                                 |
| Client SAML Endpoint | 输入您的主 SAML 处理 URL，例如 `https://<keycloak_domain>/auth/realms/master/protocol/saml`。                                                                                                                                                                                                                                                         |

完成后，选择 **Save** 按钮。

### 设置 <a href="#settings" id="settings"></a>

在 **Settings** 选项卡上，配置以下选项：

| 字段                         | 描述                                                                                                                                                                                                                                                                                                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name                       | 给客户端取一个唯一的、专用于 Bitwarden 的名称。                                                                                                                                                                                                                                                                                                                                    |
| Enabled                    | 切换到 **On**。                                                                                                                                                                                                                                                                                                                                                      |
| Sign Documents             | 指定 SAML 文档是否应由 Keycloak 领域签名。                                                                                                                                                                                                                                                                                                                                    |
| Sign Assertions            | 指定 SAML 声明是否应由 Keycloak 领域签名。                                                                                                                                                                                                                                                                                                                                    |
| Signature Algorithm        | 如果启用了 **Sign Assertions**，请选择签名的算法（默认为 `sha-256`）。                                                                                                                                                                                                                                                                                                               |
| Name ID Format             | 选择要在 SAML 响应中使用的 Keycloak 的名称 ID 格式。                                                                                                                                                                                                                                                                                                                             |
| Valid Redirect URLs        | <p>将此字段设置为从 Bitwarden SSO 配置界面获取到的预先生成的断言消费者服务（ACS）URL。<br></p><p>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2/your-org-id/Acs</code>；对于自托管实例，这取决于您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">已配置的服务器 URL</a>，例如 <code>https://your.domain.com/sso/saml2/your-org-id/Acs</code>。</p> |
| Base URL                   | <p>将此字段设置为用户访问 Bitwarden 的登录 URL。<br><br>对于云托管客户，其始终为 <code>https://vault.bitwarden.com/#/sso</code>。对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/#/sso</code>。</p>                                                           |
| Master SAML Processing URL | 如果没有自动填写，请将此字段设置为您的主 SAML 处理 URL，例如 `https://<keycloak_domain>/auth/realms/master/protocol/saml`。                                                                                                                                                                                                                                                                |

#### 细粒度 SAML 端点配置 <a href="#fine-grain-saml-endpoint-configuration" id="fine-grain-saml-endpoint-configuration"></a>

在 **Fine Grain SAML Endpoint Configuration** 界面，配置 **Assertion Consumer Service POST Binding URL** 或者 **Assertion Consumer Service Redirect Binding URL**。您将在后面的步骤中选择是使用 HTTP POST 还是 Redirect（重定向），因此请配置为您想要使用的那一种：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1ZkpIMOh9ZWqH1av35xeyg/14bd91d2d56949af424eb166e6014d63/keycloak-samlendpoint.png?fm=webp&h=432&q=50&w=1550" %}
配置 SAML 端点
{% endembed %}

对于任一字段，将其设置为从 Bitwarden SSO 配置界面获取到的预先生成的断言消费者服务（ACS）URL。对于云托管客户，其始终为 `https://sso.bitwarden.com/saml2/your-org-id/Acs`；对于自托管实例，这取决于您已配置的服务器 URL，例如 `https://your.domain.com/sso/saml2/your-org-id/Acs`。

### 映射 <a href="#mappers" id="mappers"></a>

选择 **Mappers** 选项卡并创建以下所有映射：

{% tabs %}
{% tab title="X500 GivenName" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2HfeA08gzKLWdJGQmdUVjn/d4eaf8d288e5c428627e53e7cc1f3158/x500-givenname.png?fm=webp&h=423&q=50&w=604" %}
X500 GivenName 映射器
{% endembed %}
{% endtab %}

{% tab title="X500 Surname" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/75lRSv7DqvnT9PTYlinnBl/670dc6e49e7cc53a4bb8647fde4f7cea/x500-surname.png?fm=webp&h=423&q=50&w=604" %}
X500 Surname 映射器
{% endembed %}
{% endtab %}

{% tab title="X500 Email" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5yOEzFhuh4SIPJ9plul01Y/7b9faed63acb624d7d2351a31909470d/x500-email.png?fm=webp&h=423&q=50&w=604" %}
X500 Email 映射器
{% endembed %}
{% endtab %}

{% tab title="Groups" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3znNtjQn8BeA220LedNZlO/8bd43c6b430fadba6ed88093583e4e0c/groups.png?fm=webp&h=485&q=50&w=604" %}
Groups 映射器
{% endembed %}
{% endtab %}

{% tab title="Role List" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2xZQkwZIfbFyQUmUHDX1Ve/b162accca482c04eeb50f87e596b2e76/rolelist.png?fm=webp&h=434&q=50&w=604" %}
Role List 映射器
{% endembed %}


{% endtab %}
{% endtabs %}

### 下载证书 <a href="#download-your-certificate" id="download-your-certificate"></a>

从导航中，选择 **Realm Settings** → **Keys** 然后获取您的证书：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1JwzSbwmDa7VEcVs63VWfu/54fa98e8253d91d5d49327ab7f67989b/keycloak-getcert.png?fm=webp&h=388&q=50&w=1351" %}
获取 Keycloak 证书
{% endembed %}

在[后面的步骤](keycloak-saml-implementation-1.md#identity-provider-configuration)中您将需要此证书。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，你已经在 Keycloak 门户网站范围内配置好了你所需要的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

配置以下字段：

| 字段                                 | 描述                                                                                                                       |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Name ID Format                     | 选择您在[配置 Keycloak 客户端](keycloak-saml-implementation-1.md#settings)时所选择的名称 ID 格式。                                          |
| Outbound Signing Algorithm         | Bitwarden 用来签署 SAML 请求的算法。                                                                                               |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                                                        |
| Minimum Incoming Signing Algorithm | 选择 Keycloak 客户端[被配置为用于](keycloak-saml-implementation-1.md#settings)签署 SAML 文档或声明的算法。                                     |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名。如果开启，请确保配置了 Keycloak 客户端的 [Sign Assertions](keycloak-saml-implementation-1.md#settings)（签名声明）。 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                               |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供者配置通常会要求您返回 Keycloak 门户网站以获取客户端的值：

| 字段                                        | 描述                                                                                                                                                                                                                                   |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Entity ID                                 | 输入之前创建客户端的 Keycloak 领域的 URL，例如 `https://<keycloak_domain>/auth/realms/master`。                                                                                                                                                       |
| Binding Type                              | 选择 **HTTP POST** 或 **Redirect**。                                                                                                                                                                                                     |
| Single Sign On Service URL                | 输入您的主 SAML 处理 URL，例如 `https://<keycloak_domain>/auth/realms/master/protocol/saml`。                                                                                                                                                   |
| Single Log Out Service URL                | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发，但是如果您愿意，您可以使用您的 **Logout URL** 预先配置它。                                                                                                                                                               |
| Artifact Resolution Service URL           | 将此字段留空，Keycloak SAML 仅支持 HTTP POST 和 Redirect（重定向）。                                                                                                                                                                                  |
| X509 Public Certificate                   | <p>黏贴<a href="keycloak-saml-implementation-1.md#download-your-certificate">已下载的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 选择 Keycloak 客户端[被配置为用于](keycloak-saml-implementation-1.md#settings)签署 SAML 文档或声明的算法。                                                                                                                                                 |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                                 |
| Disable Outbound Logout Requests          | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                                    |
| Want Authentication Requests Signed       | Keycloak 是否要求 SAML 请求被签名。                                                                                                                                                                                                            |

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://images.ctfassets.net/7rncvj1f8mw7/3TjmG99YArRXpsaBHH77Mt/0e4be9262c1a51be449880390ddd19f5/sso-button-lg.png?w=376\&h=92\&q=50\&fm=webp)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 Keycloak 的登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1FOJPAvRf0NCpJleOtMA8e/cc981e5933250dcab63a3f518370a24f/keycloak-login.png?fm=webp&h=535&q=50&w=775" %}
Keycloak 登录界面
{% endembed %}

使用 Keycloak 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

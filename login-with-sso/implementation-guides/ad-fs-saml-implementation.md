# AD FS SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-adfs/)
{% endhint %}

本文是**专门针对 Active Directory Federation Services (AD FS)** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页密码库和 AD FS 服务器管理器中同时进行。在您继续进行操作时，我们建议您随时准备好并按照记录的顺序完成步骤。

{% hint style="success" %}
**已经是 SSO 专家？**跳过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/5892IOGrU7B9lvBmN0P0xl/5719d49a8f15bcf9f6371fbd28827f17/saml-adfs-sample.zip)
{% endhint %}

## 在网页密码库中打开 SSO <a href="#open-sso-in-the-web-vault" id="open-sso-in-the-web-vault"></a>

如果你是直接从 [SAML 2.0 配置](../saml-2.0-configuration.md)过来的，你应该[已经创建了一个组织 ID](../saml-2.0-configuration.md#step-1-set-an-organization-identifier) 并打开了 SSO 配置界面。如果你没有，请参考那篇文章，为 SSO 创建一个组织 ID。

导航到您组织的**管理** → **单点登录**界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/20720mRAluo6crSdTiYJrn/62165bae24b421d4b8bbbdf601a18468/sso-saml1.png?fm=webp&h=652&q=50&w=822" %}
SAML 2.0 配置
{% endembed %}

你不需要编辑此界面上的任何内容，但要保持打开以方便引用。

{% hint style="success" %}
如果您是自托管 Bitwarden，您可以选择性使用**成员解密选项**。此功能默认情况下被禁用，因此现在继续使用**主密码**解密，并了解如何在配置完成并成功运行后开始使用 [Key Connector](../about-key-connector.md)。
{% endhint %}

## 创建信赖方信任 <a href="#create-a-relying-party-trust" id="create-a-relying-party-trust"></a>

在 AD FS 服务器管理器中，选择 **Tools** → **AD FS Management** → **Action** → **Add Relying Party Trust**。在向导中，进行如下的选择：

1、在 Welcome（欢迎）界面，选择 **Claims Aware**。

2、在 Select Data Source（选择数据来源）界面，选择 **Enter data about the relying party manually**。

3、在Specify Display Name（指定显示名称）界面，输入一个专用于 Bitwarden 的显示名称。

4、在 Configure URL（配置 URL）界面，选择 **Enable support for SAML 2.0 WebSSO protocol**。

* 在 **Relying party SAML 2.0 SSO service URL** 输入框中，输入从 Bitwarden SSO 配置界面获取到的断言消费者服务（ACS）URL。\
  对于云托管客户，其始终为 `https://sso.bitwarden.com/saml2/your-org-id/Acs`；对于自托管实例，这取决于您[已配置的服务器 URL](../../self-hosting/install-and-deploy-guides/install-and-deploy-linux.md#configure-your-domain)，例如 `https://your.domain.com/sso/saml2/your-org-id/Acs`。

5、在 **Choose Access Control Policy** 界面，选择

6、在 **Configure Identifiers** 界面，添加 SP 实体 ID（从 Bitwarden SSO 配置界面获取）作为依赖方信任标识符。

对于云托管客户，其始终为 `https://sso.bitwarden.com/saml2`；对于自托管实例，这取决于您[已配置的服务器 URL](../../self-hosting/install-and-deploy-guides/install-and-deploy-linux.md#configure-your-domain)，例如 `https://your.domain.com/sso/saml2`。

7、在 **Choose Access Control Policy** 界面，选择所需的策略（默认为 **Permit Everyone**）。

8、在 **Ready to Add Trust** 界面，查看您的选择。

### 高级选项 <a href="#advanced-options" id="advanced-options"></a>

创建依赖方信任后，您可以通过从左侧文件导航器中选择 **Relying Party Trusts** 并选择正确的显示名称来进一步配置其设置。

#### 哈希算法 <a href="#hash-algorithm" id="hash-algorithm"></a>

要更改 **Secure hash algorithm**（默认为 SHA-256），请导航到 **Advanced** 选项卡：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/55udgWPsUtxhl465HMFGV7/2d0dcb14562599aca669d60d00cf8b5a/saml-adfs3.png?fm=webp&h=654&q=50&w=1024" %}
设置一个安全的哈希算法
{% endembed %}

#### 端点绑定 <a href="#endpoint-binding" id="endpoint-binding"></a>

要更改端点 **Binding**（默认为 POST），请导航到 **Endpoints** 选项卡并选择已配置的 ACS URL：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/N2pjHd1LxGhH0h0620BfV/c1280e20044b6f36758c56ea22d6935f/saml-adfs4.png?fm=webp&h=764&q=50&w=1023" %}
编辑端点
{% endembed %}

### 编辑声明颁发规则 <a href="#edit-claim-issuance-rules" id="edit-claim-issuance-rules"></a>

构建声明颁发规则以确保将适当的声明（包括名称 ID）传递给 Bitwarden。以下选项卡演示了示例规则：

{% tabs %}
{% tab title="规则 1" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4AVKGRDotEE4DmHnYUQ7dH/78a16406fa80d28b0b3b3db8ffb54d8c/saml-adfs5.png?fm=webp&h=943&q=50&w=1031" %}
ADFS 规则 1
{% endembed %}
{% endtab %}

{% tab title="规则 2" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6B5hyOKQYJwLYOy0NdsXbW/1906a568bf8e59cdb9c5122c0a1a0c48/saml-adfs6.png?fm=webp&h=933&q=50&w=1024" %}
ADFS 规则 2
{% endembed %}
{% endtab %}

{% tab title="规则 3" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5MXoJkIzw0EUgj4ImrctYK/fa8d5bd0d3e11d6a40f7ce1b28667680/saml-adfs7.png?fm=webp&h=941&q=50&w=1028" %}
ADFS 规则 3
{% endembed %}
{% endtab %}
{% endtabs %}

### 获取证书 <a href="#get-certificate" id="get-certificate"></a>

在左侧的文件导航器中，选择 **AD FS** → **Service** → **Certificates** 打开证书列表。选择 **Token-signing** 证书，导航到其 **Details** 选项卡，然后选择 **Copy to File…** 按钮以导出 Base-64 编码的令牌签名证书：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7lfIJtH8gWTtOlyGucLa7o/fd30e57b1aef292139049f7e4ab27038/saml-adfs8.png?fm=webp&h=879&q=50&w=984" %}
获取令牌签名证书
{% endembed %}

在[后面的步骤中](ad-fs-saml-implementation.md#identity-provider-configuration)您将需要此证书。

### 获取联合服务标识符 <a href="#get-federation-service-identifier" id="get-federation-service-identifier"></a>

在左侧的文件导航器中，选择 **AD FS**，然后从右侧的选项菜单中选择 **Edit Federation Service Properties**。在 Federation Service Properties（联合服务属性）窗口中，复制 **Federation Service Identifier**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5pU9gOjjO9GwHDFocB3pia/007256b6b85837e6b8fab4f79d72681f/saml-adfs9.png?fm=webp&h=687&q=50&w=993" %}
获取联合服务标识符
{% endembed %}

在[后面的步骤中](ad-fs-saml-implementation.md#identity-provider-configuration)您将需要此标识符。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，你已经在 AD FS 服务器管理器范围内配置好了你所需要的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

在服务提供程序配置部分，配置以下字段：

| 字段                                 | 描述                                                                                                                  |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | 选择构建[声明颁发规则](ad-fs-saml-implementation.md#edit-claim-issuance-rules)时选择的 **Outgoing Name ID Format**（请参阅**规则 3**）。  |
| Outbound Signing Algorithm         | Bitwarden 用来签署 SAML 请求的算法。                                                                                          |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                                                   |
| Minimum Incoming Signing Algorithm | 默认，AD FS 将使用 **SHA-256** 签名。从下拉列表中选择 SHA-256，除非您已[将 AD FS 配置为使用不同的算法](ad-fs-saml-implementation.md#hash-algorithm)。 |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名。                                                                                          |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                          |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 AD FS 服务器管理器以获取相应的值：

| 字段                                        | 描述                                                                                                                                                                                                                    |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | 输入获取到的 [Federation Service Identifier](ad-fs-saml-implementation.md#get-federation-service-identifier)（联合服务标识符）。请注意，这**可能不使用 HTTPS**。                                                                                 |
| Binding Type                              | 默认，AD FS 使用 HTTP POST 端点绑定。除非您已[将 AD FS 配置为使用不同的方法](ad-fs-saml-implementation.md#endpoint-binding)，否则请选择 **HTTP POST**。                                                                                               |
| Single Sign On Service URL                | 输入 SSO 服务端点。该值可以从 AD FS 管理器的 **Service** → **Endpoints** 选项卡中获取，默认情况下应以 `http://` 开头并以 `/adfs/services/ls` 结尾。                                                                                                        |
| Artifact Resolution Service URL           | 仅当您选择 **Artifact** 作为您的信赖方信任的[端点绑定方法](ad-fs-saml-implementation.md#endpoint-binding)时才使用此字段。                                                                                                                          |
| X509 Public Certificate                   | <p>黏贴<a href="ad-fs-saml-implementation.md#get-certificate">已下载的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 默认情，AD FS 将使用 SHA-256 签名。从下拉列表中选择 **SHA-256**，除非您已[将 AD FS 配置为使用不同的算法](ad-fs-saml-implementation.md#hash-algorithm)。                                                                                                  |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                  |
| Disable Outbound Logout Requests          | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                     |
| Want Authentication Requests Signed       | AD FS 是否要求 SAML 请求被签名。                                                                                                                                                                                                |

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://images.ctfassets.net/7rncvj1f8mw7/3TjmG99YArRXpsaBHH77Mt/0e4be9262c1a51be449880390ddd19f5/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 AD FS SSO 的登录界面。使用 AD FS 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

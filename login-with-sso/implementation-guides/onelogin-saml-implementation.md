# OneLogin SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-onelogin/)
{% endhint %}

本文是**专门针对** **OneLogin** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页密码库和 OneLogin 门户中同时进行。在您继续进行操作时，我们建议您随时准备好并按照记录的顺序完成步骤。

{% hint style="success" %}
**是 SSO 专业人士？**请跳过本文中的说明，然后下载配置示例的截图以与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/mQMTlMcvpyBPzgAkgqDvg/ace51cc7a46379048140042282e6b24f/saml-onelogin-sample.zip)
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

## 创建 OneLogin 应用程序 <a href="#create-a-onelogin-app" id="create-a-onelogin-app"></a>

在 OneLogin 门户中，导航到 **Applications** 界面然后选择 **Add App** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/37OSt7e5j969j9ikvH8buI/3bf9fa6b57a45b357a9d2bc012d8a6af/ol-addapp.png?fm=webp&h=292&q=50&w=1071" %}
添加应用程序
{% endembed %}

为您的应用程序指定一个专用于 Bitwarden 的 **Display Name**，然后选择 **Save** 按钮。

### 配置 <a href="#configuration" id="configuration"></a>

从左侧导航中选择 **Configuration** 然后配置以下的信息，您需要从 Bitwarden 业务门户获取其中的一些信息：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/12yP5ohPGhqcCZZdpwVDQd/7fc5661e4fb4954ad00246deae2fd9b1/ol-appconfig.png?fm=webp&h=404&q=50&w=898" %}
应用程序配置
{% endembed %}

| 应用程序设置                       | 描述                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Audience (EntityID)          | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>SP Entity ID</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2</code>。对于自托管实例，这由您<a href="../../on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2</code>。</p>                                                     |
| Recipient                    | 将此字段设置为同样也用于 **Audience (Entity ID)** 设置的预先生成的 **SP Entity ID**。                                                                                                                                                                                                                                                                                                                         |
| ACS (Consumer) URL Validator | 尽管被 OneLogin 标记为必需，但您实际上并不需要在此字段中输入信息以与 Bitwarden 集成。跳到下一个字段 **ACS (Consumer) URL**。                                                                                                                                                                                                                                                                                                     |
| ACS (Consumer) URL           | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>Assertion Consumer Service (ACS) URL</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2/your-org-id/Acs</code>。对于自托管实例，这由您<a href="../../on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain/sso/saml2/your-org-id/Acs</code>。</p> |
| SAML initiator               | 选择 **Service Provider**。SSO 登录当前不支持 IdP 发起的 SAML 声明。                                                                                                                                                                                                                                                                                                                                     |
| SAML nameID Format           | 将此字段设置您希望用于 SAML 声明的 [SAML NameID 格式](https://docs.oracle.com/cd/E19316-01/820-3886/ggwbz/index.html)。                                                                                                                                                                                                                                                                                   |
| SAML signature element       | 默认，OneLogin 将签名 SAML 响应。您可以将其设置为 **Assertion** 或 **Both**。                                                                                                                                                                                                                                                                                                                               |

完成配置设置后，选择 **Save** 按钮。

### 参数 <a href="#parameters" id="parameters"></a>

从左侧导航中选择 **Parameters**，然后使用  **🞤Add** 图标创建以下自定义参数：

| 字段名称      | 值          |
| --------- | ---------- |
| email     | Email      |
| firstname | First Name |
| lastname  | Last Name  |

完成自定义参数后，选择 **Save** 按钮。

### SSO

从左侧导航中选择 **SSO** 并完成以下操作：

1、选择 X.509 证书下的 **View Details** 链接：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7emKbivWUWKO1ufVC9Rkgu/d85cb9e978dc70876e60e10765fc2254/ol-viewcert.png?fm=webp&h=492&q=50&w=1005" %}
查看您的证书
{% endembed %}

在证书界面，下载或复制您的 X.509 PEM 证书，因为您[稍后需要使用它](onelogin-saml-implementation.md#identity-provider-configuration)。复制后，返回主 SSO 界面。

2、设置您的 **SAML Signature Algorithm**。

3、记下您的 **Issuer URL** 和 **SAML 2.0 Endpoint (HTTP)**。您[很快就需要使用这些值](onelogin-saml-implementation.md#identity-provider-configuration)。

### 访问权限 <a href="#access" id="access"></a>

从左侧导航中选择 **Access**。在 **Roles** 部分，为您希望能够使用 Bitwarden 的所有角色分配应用程序访问权限。大多数实现会创建一个专用于 Bitwarden 的角色，而不是选择基于包罗万象（例如，**Default**）或基于预先存在的角色进行分配。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6D4j0WofpBcvSCMB0rN4Db/5303beacbc3ce331dfddc6dc6b19d6ea/ol-roles.png?fm=webp&h=147&q=50&w=899" %}
角色分配
{% endembed %}

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已经在 OneLogin 门户网站中配置了所需的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据在 OneLogin 门户网站[设置期间](onelogin-saml-implementation.md#create-a-onelogin-app)所选择的选项配置以下字段：

| 字段                                 | 描述                                                                                                                                        |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | 将此字段设置为您[在应用程序配置期间](onelogin-saml-implementation.md#configuration)为 OneLogin **SAML nameID Format** 字段选择的内容。                              |
| Outbound Signing Algorithm         | 用于签名 SAML 请求的算法，默认为 `sha-256`。                                                                                                            |
| Signing Behavior                   | SAML 请求是否/何时将被签名。默认，OneLogin 不要求对请求进行签名。                                                                                                  |
| Minimum Incoming Signing Algorithm | 将此字段设置为您[在应用程序配置期间](onelogin-saml-implementation.md#configuration)为 OneLogin **SAML Signature Algorithm** 字段选择的内容。                        |
| Want Assertions Signed             | 如果您在[应用程序配置期间](onelogin-saml-implementation.md#configuration)将 OneLogin 中的 **SAML signature element** 设置为 **Assertion** 或 **Both**，请选中此框。 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                                                |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 OneLogin 门户网站以获取应用程序的值：

| 字段                                        | 描述                                                                                                                                                                                                                     |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | 输入您的 OneLogin **Issuer URL**，这可以从 [OneLogin 应用 SSO 界面](onelogin-saml-implementation.md#sso)获取。                                                                                                                         |
| Binding Type                              | 设置为 **HTTP Post**（如 SAML 2.0Endpoint (HTTP) 中所示）。                                                                                                                                                                      |
| Single Sign On Service URL                | 输入您的 OneLogin **SAML 2.0 Endpoint (HTTP)**，这可以从 [OneLogin 应用 SSO 界面](onelogin-saml-implementation.md#sso)获取。                                                                                                           |
| Single Log Out Service URL                | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。但是您可以根据需要预先配置它。                                                                                                                                                                      |
| Artifact Resolution Service URL           | 对于 OneLogin 实现，您可以将此字段留空。                                                                                                                                                                                              |
| X509 Public Certificate                   | <p>黏贴<a href="onelogin-saml-implementation.md#sso">获取到的 X.509 证书</a>one，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 选择在 [OneLogin SSO](onelogin-saml-implementation.md#sso) 配置界面选择的签名算法。                                                                                                                                                   |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                   |
| Disable Outbound Logout Requests          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                     |
| Want Authentication Requests Signed       | OneLogin 是否要求 SAML 请求被签名。                                                                                                                                                                                              |

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 OneLogin 的登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/58dRC3pPEm0bO8xtd2Tqzq/415b83d361b49c73550d0932ddca8576/ol-login.png?fm=webp&h=519&q=50&w=485" %}
OneLogin 登录界面
{% endembed %}

使用您的 OneLogin 凭据进行身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

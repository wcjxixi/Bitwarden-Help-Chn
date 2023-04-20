# Auth0 SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-auth0/)
{% endhint %}

本文是**专门针对 Auth0** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页密码库和 Auth0 门户网站中同时进行。在您继续进行操作时，我们建议您随时准备好并按照记录的顺序完成步骤。

{% hint style="success" %}
**已经是 SSO 专家？**跳过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/773hQzr7eXdIfIxVW0jX9N/9ecac2c76559e1dc6cecb88e41ac8783/saml-auth0-sample.zip)
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

## 创建 Auth0 应用程序 <a href="#create-an-auth-0-application" id="create-an-auth-0-application"></a>

在 Auth0 门户中，使用应用程序菜单来创建一个 **Regular Web Application**（常规的 Web 应用程序）：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3EsE3HTVqocRvC1f2XSWbt/9077b5bc7801de7270372594e62b7aad/auth0-createapp.png?fm=webp&h=400&q=50&w=1040" %}

点击 **Setting** 标签并配置以下信息，其中一些信息您需要从 Bitwarden 业务门户中获取：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6MMUA6fh1HBgeEa1lCWXc5/4dc49064bcd846f5973595fed3f525e9/auth0-appsettings.png?fm=webp&h=569&q=50&w=860" %}
Auth0 设置
{% endembed %}

| Auth0 设置                             | 描述                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name                                 | 给此应用程序取一个专用于 Bitwarden 的名称。                                                                                                                                                                                                                                                                                                                                                               |
| Domain                               | 请注意此值。在[后面的步骤中](auth0-saml-configuration.md#identity-provider-configuration)您将需要它。                                                                                                                                                                                                                                                                                                        |
| Application Type                     | 选择 **Regular Web Application**。                                                                                                                                                                                                                                                                                                                                                           |
| Token Endpoint Authentication Method | 选择 **Post** (HTTP Post)，它将映射到[稍后配置](auth0-saml-configuration.md#identity-provider-configuration)的 **Binding Type** 属性。                                                                                                                                                                                                                                                                    |
| Application Login URI                | <p>将此字段设置为从 Bitwarden SSO 配置界面中预先生成的 <strong>SP Entity ID</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2</code>；对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/install-and-deploy-linux.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2</code>。</p>                                                        |
| Allowed Callback URLS                | <p>将此字段设置为从 Bitwarden SSO 配置界面中预先生成的 <strong>Assertion Consumer Service (ACS) URL</strong>。<br><br>对于云托管客户，其始终为<code>https://sso.bitwarden.com/saml2/your-org-id/Acs</code>；对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/install-and-deploy-linux.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2/your-org-id/Acs</code>。</p> |

### Grant Types

在 **Advanced Settings** → **Grant Types** 部分，确保选择了以下授权类型（可以预先选择）：

![应用程序授权类型](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/cheatsheets/saml-auth0/auth0-advancedsettings.png)

### Certificates

在 **Advanced Settings** → **Certificates** 部分，复制或下载您的签名证书。你现在还不需要用它做任何事情，但需要[稍后引用](auth0-saml-configuration.md#identity-provider-configuration)它。

![Auth0 证书](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/cheatsheets/saml-auth0/auth0-certificate.png)

### Endpoints

&#x20;不需要在 **Advanced Settings** → **Endpoints** 部分编辑任何东西，但你需要这个 SAML 端点，以便[稍后引用](auth0-saml-configuration.md#identity-provider-configuration)它。

{% hint style="info" %}
在较小的窗口中，**Endpoints** 选项卡可能会消失在浏览器的边缘。如果您找不到它，请单击 **Certificates** 选项卡，然后按右方向键键（→）。
{% endhint %}

![Auth0 端点](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/cheatsheets/saml-auth0/auth0-endpoints.png)

## 配置 Auth0 规则 <a href="#configure-auth-0-rules" id="configure-auth-0-rules"></a>

创建规则来定制你的应用程序的 SAML 响应行为。虽然 Auth0 提供了[多个选项](https://auth0.com/docs/protocols/saml-protocol/customize-saml-assertions#saml-assertion-attributes)，但这里将只关注那些专门映射到 Bitwarden 的选项。要创建一个自定义 SAML 配置规则集，请使用 **Auth Pipeline → Rules** 菜单来 **Create**（创建）规则：

![Auth0 规则](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/cheatsheets/saml-auth0/auth0-settings.png)

以下任何项目均可配置：

| Key                    | 描述                                                                                                                                                                                                                                                                                       |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `signatureAlgorithm`   | <p>Auth0 使用此算法对 SAML 声明或响应进行签名。默认为 <code>rsa-sha1</code>，您也可以将值设置为 <code>rsa-sha256</code>。<br><br>如果您更改了这个值，您必须：<br>-将 <code>digestAlgorithm</code>  设置为 <code>sha256</code>。<br>-（在 Bitwarden 中）将 <strong>Minimum Incoming Signing Algorithm</strong> 设置为 <code>rsa-sha256</code>。</p> |
| `digestAlgorithm`      | 此算法用于计算 SAML 声明或响应的摘要。默认为 `sha-1`。如果您更改了  `signatureAlgorithm` 的值，您还应该将此值设置为 `sha256`.                                                                                                                                                                                                   |
| `signResponse`         | 默认，Auth0 将仅对 SAML 声明进行签名。将此属性设置为 `true` 可对 SAML 响应（而不是声明）进行签名。                                                                                                                                                                                                                           |
| `nameIdentifierFormat` | 默认为 `urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified`。您可以将值设置为[任一 SAML NameID 格式](https://docs.oracle.com/cd/E19316-01/820-3886/ggwbz/index.html)。如果这样做了，请将 SP **Name ID Format** 字段更改为相应的选项（参阅[这里](auth0-saml-configuration.md#service-provider-configuration)）。                  |

使用像下面这样的 **Script**（脚本）来实现这些规则。如需帮助，请参阅 [Auth0 文档](https://auth0.com/docs/protocols/saml-protocol/customize-saml-assertions#customize-saml-assertions-with-rules)。

```
function (user, context, callback) {
    context.samlConfiguration.signatureAlgorithm = "rsa-sha256";
    context.samlConfiguration.digestAlgorithm = "sha256";
    context.samlConfiguration.signResponse = "true";
    context.samlConfiguration.nameIdentifierFormat = "urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress"
    context.samlConfiguration.binding = "urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect";
    callback(null, user, context);
}
```

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，你已经在 Auth0 门户网站配置好了你所需要的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

除非您已配置了[自定义规则](auth0-saml-configuration.md#configure-auth-0-rules)，否则您的服务提供重新配置就已经完成了。如果您配置了自定义规则或要对实现做进一步的更改，请编辑相关字段：

| 字段                                 | 描述                                                                                                                                            |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | [NameID Format](https://docs.oracle.com/cd/E19316-01/820-3886/ggvxx/index.html) 用于在 SAML 请求（`NameIDPolicy`）中指定。要忽略它，请设置为 **Not Configured**。  |
| Outbound Signing Algorithm         | 用于签名 SAML 请求的算法，默认为 `rsa-sha256`。                                                                                                             |
| Signing Behavior                   | SAML 请求是否/何时将被签名。默认，Auth0 不要求对请求进行签名。                                                                                                         |
| Minimum Incoming Signing Algorithm | Bitwarden 在 SAML 响应中接受的最小签名算法。默认，Auth0 使用 `rsa-sha1` 进行签名，因此请从下拉列表中选择该选项，除非您配置了[自定义签名规则](auth0-saml-configuration.md#configure-auth-0-rules)。 |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名。默认，Auth0 对 SAML 声明进行签名，因此，除非您配置了[自定义签名规则](auth0-saml-configuration.md#configure-auth-0-rules)，否则请选中此框。              |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                                                    |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 Auth0 门户以获取应用程序的值：

| 字段                                        | 描述                                                                                                                                                                                                                                  |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | 输入您的 Auth0 应用程序的 **Domain** 值（参考[此处](auth0-saml-configuration.md#create-an-auth-0-application)），使用前缀 `urn:`，例如，`urn:bw-help.us.auth0.com`。                                                                                          |
| Binding Type                              | 选择 **HTTP POST** 以匹配在您的 Auth0 应用程序中指定的 [Token Endpoint Authentication Method](auth0-saml-configuration.md#create-an-auth-0-application) 的值。                                                                                         |
| Single Sign On Service URL                | 输入您的 Auth0 应用程序的 **SAML Protocol URL**（参阅 [Endpoints](auth0-saml-configuration.md#endpoints)）。例如，`https://bw-help.us.auth0.com/samlp/HcpxD63h7Qzl420u8qachPWoZEG0Hho2`。                                                             |
| Single Log Out Service URL                | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发，但是您可以根据需要预先配置它。                                                                                                                                                                                   |
| Artifact Resolution Service URL           | 输入您的 Auth0 应用程序的 **SAML Metadata URL**（参阅 [Endpoints](auth0-saml-configuration.md#endpoints)）。例如，`https://bw-help.us.auth0.com/samlp/metadata/HcpxD63h7Qzl420u8qachPWoZEG0Hho2`.                                                    |
| X509 Public Certificate                   | <p>黏贴已复制的 <a href="auth0-saml-configuration.md#certificates">Signing Certificate</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 默认，Auth0 使用 `RSA-SHA1` 签名， 因此，除非您配置了[自定义签名规则](auth0-saml-configuration.md#configure-auth-0-rules)，否则请从下拉列表中选择 `RSA-SHA1` 选项。                                                                                                        |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                                |
| Disable Outbound Logout Requests          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                                  |
| Want Authentication Requests Signed       | Auth0 是否要求 SAML 请求被签名。                                                                                                                                                                                                              |

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 Auth0 的登录界面：

![Auth0 登录界面](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/cheatsheets/saml-auth0/auth0-login.png)

使用您的 Auth0 凭据进行身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

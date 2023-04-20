# SAML 2.0 配置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/configure-sso-saml/)
{% endhint %}

## 第 1 步：设置组织标识符 <a href="#step-1-set-an-organization-identifier" id="step-1-set-an-organization-identifier"></a>

使[用 SSO 验证身份](../../my-account/log-in-and-unlock/using-login-with-sso.md#login-using-sso)的用户将被要求输入一个**组织标识符**，该标识符表明要验证的组织（以及 SSO 集成）。要设置唯一的组织标识符：

1、登录到您的[网页密码库](https://vault.bitwarden.com/)并打开您的组织。

2、打开**设置**选项卡然后为您的组织输入一个唯一的**标识符**。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6pr4tqMnrLCvwDBMlba5x7/7febd98161d60656c9bc5ab57508be02/org-id.png?fm=webp&h=568&q=50&w=1017" %}
输入一个标识符
{% endembed %}

3、在退出此页面之前**保存**您的更改。

{% hint style="success" %}
此配置准备好使用后，您需要将这个值分享给用户。
{% endhint %}

## 第 2 步：启用 SSO 登录 <a href="#step-2-enable-login-with-sso" id="step-2-enable-login-with-sso"></a>

拥有组织标识符后，您可以继续启用和配置集成。要启用 SSO 登录：

1、从组织密码库中，导航到**管理**选项卡并从左侧菜单中选择**单点登录**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/51wSToXTHHVmBCrLrE8T0E/70700e2bbbf8ed9ec51fc02d72f2aecb/manage-sso.png?fm=webp&h=472&q=50&w=783" %}
启用 SSO
{% endembed %}

2、在单点登录界面，勾选**允许 SSO 身份验证**复选框。

3、从**类型**下拉菜单中，选择 **SAML 2.0** 选项。如果您打算改用 OIDC，请切换到 [OIDC 配置指南](oidc-configuration.md)。

{% hint style="success" %}
如果您是自托管 Bitwarden，您可以选择性使用**成员解密选项**。此功能默认情况下被禁用，因此现在继续使用**主密码**解密，并了解如何在配置完成并成功运行后开始使用 [Key Connector](key-connector/about-key-connector.md)。
{% endhint %}

## 第 3 步：配置 <a href="#step-3-configuration" id="step-3-configuration"></a>

从这里开始，**实施将因提供程序而异**。跳转到我们的特定**实施指南**之一，以帮助完成配置过程：

| 提供程序         | 指南                                                                             |
| ------------ | ------------------------------------------------------------------------------ |
| AD FS        | [AD FS 实施指南](implementation-guides/ad-fs-saml-implementation.md)               |
| Auth0        | [Auth0 实施指南](implementation-guides/auth0-saml-configuration.md)                |
| AWS          | [AWS 实施指南](implementation-guides/aws-saml-implementation.md)                   |
| Azure        | [Azure 实施指南](implementation-guides/azure-saml-implementation.md)               |
| Duo          | [Duo 实施指南](implementation-guides/duo-saml-implementation.md)                   |
| Google       | [Google 实施指南](implementation-guides/google-saml-implementation.md)             |
| JumpCloud    | [JumpCloud 实施指南](implementation-guides/jumpcloud-saml-implementation.md)       |
| Keycloak     | [Keycloak 实施指南](implementation-guides/keycloak-saml-implementation-1.md)       |
| Okta         | [Okta 实施指南](implementation-guides/okta-saml-implementation.md)                 |
| OneLogin     | [OneLogin 实施指南](implementation-guides/onelogin-saml-implementation.md)         |
| PingFederate | [PingFederate 实施指南](implementation-guides/pingfederate-saml-implementation.md) |

### 配置参考资料 <a href="#configuration-reference-materials" id="configuration-reference-materials"></a>

以下部分将定义在单点登录配置界面的字段，其与您要集成的 IdP 无关。必须配置的字段将被标记（**必填**）。

{% hint style="success" %}
**除非您对 SAML 2.0 非常熟悉**，否则我们建议使用[上述实施指南](saml-2.0-configuration.md#step-3-configuration)之一，而不是以下的通用素材。
{% endhint %}

单点登录界面将配置分为两个部分：

* &#x20;**SAML 服务提供程序配置**将确定 SAML 请求的格式。
* &#x20;**SAML 身份提供程序配置**将确定 SAML 响应的预期格式。

#### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

| 字段                                   | 描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SP Entity ID                         | （**自动生成**）用于身份验证请求的 Bitwarden 端点。对于云托管客户，其始终为 `https://sso.bitwarden.com/saml2`。对于自托管实例，这取决于您[已配置的服务器 URL](../../on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md#configure-your-domain)，例如 `https://your.domain.com/sso/saml2`。                                                                                                                                                                                                                                                      |
| SAML 2.0 Metadata URL                | （**自动生成**）Bitwarden 端点的元数据 URL。对于云托管客户，其始终为 `https://sso.bitwarden.com/saml2/your-org-id`。对于自托管实例，这取决于您[已配置的服务器 URL](../../on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md#configure-your-domain)，例如 `https://your.domain.com/sso/saml2/your-org-id`。                                                                                                                                                                                                                                |
| Assertion Consumer Service (ACS) URL | （**自动生成**）从 IdP 发送 SAML 声明的位置。对于云托管客户，其始终为 `https://sso.bitwarden.com/saml2/your-org-id/Acs`。对于自托管实例，这取决于您[已配置的服务器 URL](../../on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md#configure-your-domain)，例如 `https://your.domain.com/sso/saml2/your-org-id/Acs`。                                                                                                                                                                                                                         |
| Name ID Format                       | <p>Bitwarden 请求 SAML 声明的格式。选项包括：</p><p>-Unspecified (<em>默认</em>)</p><p>-Email Address</p><p>-X.509 Subject Name</p><p>-Windows Domain Qualified Name</p><p>-Kerberos Principal Name</p><p>-Entity Identifier</p><p>-Persistent</p><p>-Transient</p>                                                                                                                                                                                                                                                       |
| Outbound Signing Algorithm           | <p>Bitwarden 用于签署 SAML 请求的算法。选项包括：<br>-<a href="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256">http://www.w3.org/2001/04/xmldsig-more#rsa-sha256</a> (<em>默认</em>)<br>-<a href="http://www.w3.org/2000/09/xmldsig#rsa-sha1">http://www.w3.org/2000/09/xmldsig#rsa-sha1</a><br>-<a href="http://www.w3.org/2000/09/xmldsig#rsa-sha384">http://www.w3.org/2000/09/xmldsig#rsa-sha384</a><br>-<a href="http://www.w3.org/2000/09/xmldsig#rsa-sha512">http://www.w3.org/2000/09/xmldsig#rsa-sha512</a></p> |
| Signing Behavior                     | <p>是否/何时签署 SAML 请求。选项包括：<br>-If IdP Wants Authn Requests Signed (<em>默认</em>)<br>-Always<br>-Never</p>                                                                                                                                                                                                                                                                                                                                                                                                     |
| Minimum Incoming Signing Algorithm   | Bitwarden 将在 SAML 响应中接受的算法的最小强度。                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Want Assertions Signed               | 如果 Bitwarden 期望来自 IdP 的响应被签名，请选中此复选框。                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Validate Certificates                | 当使用来自你的 IdP 的通过受信任的 CA 颁发的受信任和有效的证书时，请选中此复选框。自签名证书可能会失败，除非在 Bitwarden SSO 登录 docker 镜像中配置了正确的信任链。                                                                                                                                                                                                                                                                                                                                                                                                          |

#### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

| 字段                                        | 描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | （_必填_）您的身份服务器或 IdP 实体 ID 的地址或 URL。                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Binding Type                              | <p>IdP 用于响应 Bitwarden SAML 请求的方法。选项包括：<br>-Redirect (<em>推荐</em>)<br>-HTTP POST<br>-Artifact</p>                                                                                                                                                                                                                                                                                                                                                                                                           |
| Single Sign On Service URL                | (_必填，如果 Entity ID 不是 URL_) 您的 IdP 发布的 SSO URL。                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Single Log Out Service URL                | SSO 登录目前**不支持** SLO。该选项计划在未来使用，但我们强烈建议预先配置该字段。                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Artifact Resolution Service URL           | （_必填，如果 Binding Type 是 Artifact_）用于工件解析协议（Artifact Resolution Protocol）的 URL。                                                                                                                                                                                                                                                                                                                                                                                                                              |
| X509 Public Certificate                   | <p>（<em>必填</em>）X.509 Base-64 编码的证书的主体部分。不要包括 CER/PEM 格式的证书的 <code>-----BEGIN CERTIFICATE-----</code> 与 <code>-----END CERTIFICATE-----</code> 之间的行或部分。</p><p></p><p>此字段中额外的空格、回车符和其他无关字符将导致证书验证失败。<strong>仅</strong>复制证书数据到此字段中。</p>                                                                                                                                                                                                                                                                      |
| Outbound Signing Algorithm                | <p>您的 IdP 用于签署 SAML 响应/声明的算法。选项包括：<br>-<a href="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256">http://www.w3.org/2001/04/xmldsig-more#rsa-sha256</a> (<em>默认</em>)<br>-<a href="http://www.w3.org/2000/09/xmldsig#rsa-sha1">http://www.w3.org/2000/09/xmldsig#rsa-sha1</a><br>-<a href="http://www.w3.org/2000/09/xmldsig#rsa-sha384">http://www.w3.org/2000/09/xmldsig#rsa-sha384</a><br>-<a href="http://www.w3.org/2000/09/xmldsig#rsa-sha512">http://www.w3.org/2000/09/xmldsig#rsa-sha512</a></p> |
| Allow Unsolicited Authentication Response | SSO 登录目前**不支持**未经请求（由 IdP 发起）的 SSO 声明。此复选框计划在未来使用。                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Disable Outbound Logout Requests          | SSO 登录目前**不支持** SLO。该选项计划在未来使用，但我们强烈建议预先配置该字段。                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Want Authentication Requests Signed       | 如果您的 IdP 希望来自 Bitwarden SAML 的请求被签名，请选中此复选框。                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

#### SAML 属性和声明 <a href="#saml-attributes-and-claims" id="saml-attributes-and-claims"></a>

**帐户布建要求一个电子邮件地址**，它可以作为下表中的任何属性或声明被传递。

还强烈建议使用一个唯一的用户标识符。如果没有，将使用电子邮件来链接用户。

属性/声明按优先匹配的顺序排列，包括适用的 Fallback：

| 值          | 声明/属性                                                                                                                                                  | Fallback 声明/属性                                                        |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| Unique ID  | <p>NameID (when not Transient)<br>urn:oid:0.9.2342.19200300.100.1.1<br>Sub<br>UID<br>UPN<br>EPPN</p>                                                   |                                                                       |
| Email      | <p>Email<br>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress<br>urn:oid:0.9.2342.19200300.100.1.3<br>Mail<br>EmailAddress</p>        | <p>Preferred_Username<br>Urn:oid:0.9.2342.19200300.100.1.1<br>UID</p> |
| Name       | <p>Name<br>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name<br>urn:oid:2.16.840.1.113730.3.1.241<br>urn:oid:2.5.4.3<br>DisplayName<br>CN</p> | First Name + “ “ + Last Name (see below)                              |
| First Name | <p>urn:oid:2.5.4.42<br>GivenName<br>FirstName<br>FN<br>FName<br>Nickname</p>                                                                           |                                                                       |
| Last Name  | <p>urn:oid:2.5.4.4<br>SN<br>Surname<br>LastName</p>                                                                                                    |                                                                       |

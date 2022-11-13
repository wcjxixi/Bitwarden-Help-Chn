# \*在您的 IdP 上配置 Bitwarden（SAML 2.0）

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-providers/)、[GitHub 地址](https://github.com/bitwarden/help/blob/master/\_articles/login-with-sso/saml-providers.md)
{% endhint %}

## 服务提供程序配置映射 <a href="#service-provider-configuration-mapping" id="service-provider-configuration-mapping"></a>

| **Bitwarden 字段**                     | **Azure AD 字段**                            | **JumpCloud 字段**              | **OneLogin 字段**               | **G-Suite 字段**                   | **Okta 字段**                                        |
| ------------------------------------ | ------------------------------------------ | ----------------------------- | ----------------------------- | -------------------------------- | -------------------------------------------------- |
| SP Entity ID （Bitwarden SSO 服务自动生成）  | Identifier (Entity ID)                     | SP Entity ID                  | Audience (EntityID)           | Entity ID                        | Audience Restriction                               |
| Assertion Consumer Service (ACS) URL | Reply URL (Assertion Consumer Service URL) | ACS URL                       | ACS (Consumer) URL            | ACS URL                          | Single Sign On URL, Recipient URL, Destination URL |
| Name ID Format                       | Name ID                                    | SAMLSubject NameId Format     | Name ID                       | Name ID: G-Suite + Bitwarden 需匹配 | Name ID Format                                     |
| Outbound Signing Algorithm           | Azure + Bitwarden 需匹配                      | Signature Algorithm           | OneLogin + Bitwarden 需匹配      | G-Suite + Bitwarden 需匹配          | Signature Algorithm + Bitwarden 需匹配                |
| Signing Behavior                     | 使用默认值，如果 IdP 请求，Bitwarden 将签名              | 使用默认值，如果 IdP 请求，Bitwarden 将签名 | 使用默认值，如果 IdP 请求，Bitwarden 将签名 | G-Suite + Bitwarden 需匹配          | Digest Algorithm + Bitwarden 需匹配                   |

## 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

| **Bitwarden 字段**                | **Azure AD 字段**       | **JumpCloud 字段**          | **OneLogin 字段**          | **G-Suite 字段**                 | **Okta 字段**                         |
| ------------------------------- | --------------------- | ------------------------- | ------------------------ | ------------------------------ | ----------------------------------- |
| Entity ID                       | Azure AD Identifier   | IdP Entity ID             | Issuer URL               | Entity ID                      |                                     |
| Binding Type                    | Azure + Bitwarden 需匹配 | JumpCloud + Bitwarden 需匹配 | OneLogin + Bitwarden 需匹配 | G-Suite + Bitwarden 需匹配        | Okta + Bitwarden 需匹配                |
| Single Sign On Service URL      | Login URL             | IDP URL                   | SAML 2.0 Endpoint (HTTP) | SSO URL                        |                                     |
| Single Log Out Service URL      | Logout URL            | 可选                        | SLO Endpoint (HTTP)      | N/A                            |                                     |
| Artifact Resolution Service URL | 可选                    | 可选                        | 可选                       | 可选                             | 可选                                  |
| X509 Public Certificate         | Certificate (Base64)  | 激活后下载，在“IDP 证书有效”下可用      | X.509 Certificate        | Certificate（下载 PEM 文件，以文本形式打开） | x.509 Certificate                   |
| Outbound Signing Algorithm      | Azure + Bitwarden 需匹配 | Signature Algorithm       | Azure + Bitwarden 需匹配    | 使用复选框以关闭/打开                    | Signature Algorithm + Bitwarden 需匹配 |

## 示例配置截图 <a href="#screenshots-of-sample-configurations" id="screenshots-of-sample-configurations"></a>

{% file src="../.gitbook/assets/bitwarden_export (1).csv" %}
Okta 示例下载
{% endfile %}

{% hint style="info" %}
本表格旨在方便查找某些字段和值。根据你的组织的策略和程序，某些配置和提供程序的版本可能会而有所不同。如果您在为您的 Bitwarden 组织配置 SSO 登录时遇到困难，请[联系我们](https://bitwarden.com/contact/)以获取协助。
{% endhint %}

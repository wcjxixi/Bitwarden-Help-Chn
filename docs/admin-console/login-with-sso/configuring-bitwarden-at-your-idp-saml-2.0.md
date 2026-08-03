# \*在您的 IdP 上配置 Bitwarden (SAML 2.0)

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-providers/)、[GitHub 地址](https://github.com/bitwarden/help/blob/master/_articles/login-with-sso/saml-providers.md)
{% endhint %}

## 服务提供程序配置映射 <a href="#service-provider-configuration-mapping" id="service-provider-configuration-mapping"></a>

| Bitwarden 字段                    | Azure AD 字段                                | JumpCloud 字段                  | OneLogin 字段                   | G-Suite 字段                       | Okta 字段                                            |
| ------------------------------- | ------------------------------------------ | ----------------------------- | ----------------------------- | -------------------------------- | -------------------------------------------------- |
| SP 实体 ID （Bitwarden SSO 服务自动生成） | Identifier (Entity ID)                     | SP Entity ID                  | Audience (EntityID)           | Entity ID                        | Audience Restriction                               |
| 断言消费者服务 (ACS) URL               | Reply URL (Assertion Consumer Service URL) | ACS URL                       | ACS (Consumer) URL            | ACS URL                          | Single Sign On URL, Recipient URL, Destination URL |
| 名称 ID 格式                        | Name ID                                    | SAMLSubject NameId Format     | Name ID                       | Name ID: G-Suite + Bitwarden 需匹配 | Name ID Format                                     |
| 出站签名算法                          | Azure + Bitwarden 需匹配                      | Signature Algorithm           | OneLogin + Bitwarden 需匹配      | G-Suite + Bitwarden 需匹配          | Signature Algorithm + Bitwarden 需匹配                |
| 签名行为                            | 使用默认值，如果 IdP 请求，Bitwarden 将签名              | 使用默认值，如果 IdP 请求，Bitwarden 将签名 | 使用默认值，如果 IdP 请求，Bitwarden 将签名 | G-Suite + Bitwarden 需匹配          | Digest Algorithm + Bitwarden 需匹配                   |

## 身份提供程序配置映射 <a href="#identity-provider-configuration-mapping" id="identity-provider-configuration-mapping"></a>

<table data-search="false"><thead><tr><th>Bitwarden 字段</th><th>Azure AD 字段</th><th>JumpCloud 字段</th><th>OneLogin 字段</th><th>G-Suite 字段</th><th>Okta 字段</th></tr></thead><tbody><tr><td>实体 ID</td><td>Azure AD Identifier</td><td>IdP Entity ID</td><td>Issuer URL</td><td>Entity ID</td><td></td></tr><tr><td>绑定类型</td><td>Azure + Bitwarden 需匹配</td><td>JumpCloud + Bitwarden 需匹配</td><td>OneLogin + Bitwarden 需匹配</td><td>G-Suite + Bitwarden 需匹配</td><td>Okta + Bitwarden 需匹配</td></tr><tr><td>单点登录服务 URL</td><td>Login URL</td><td>IDP URL</td><td>SAML 2.0 Endpoint (HTTP)</td><td>SSO URL</td><td></td></tr><tr><td>单点注销服务 URL</td><td>Logout URL</td><td>可选</td><td>SLO Endpoint (HTTP)</td><td>N/A</td><td></td></tr><tr><td>工件解析服务 URL</td><td>可选</td><td>可选</td><td>可选</td><td>可选</td><td>可选</td></tr><tr><td>X509 公共证书</td><td>Certificate (Base64)</td><td>激活后下载，在「IDP 证书有效」下可用</td><td>X.509 Certificate</td><td>Certificate（下载 PEM 文件，以文本形式打开）</td><td>x.509 Certificate</td></tr><tr><td>出站签名算法</td><td>Azure + Bitwarden 需匹配</td><td>Signature Algorithm</td><td>Azure + Bitwarden 需匹配</td><td>使用复选框以关闭/打开</td><td>Signature Algorithm + Bitwarden 需匹配</td></tr></tbody></table>

## 示例配置截图 <a href="#screenshots-of-sample-configurations" id="screenshots-of-sample-configurations"></a>

Okta 示例：

```
folder,favorite,type,name,notes,fields,login_uri,login_username,login_password,login_totp
Social,1,login,Twitter,,,twitter.com,me@example.com,password123,
,,login,My Bank,Bank PIN is 1234,"PIN: 1234
Question 1: Blue",https://www.wellsfargo.com/home.jhtml,john.smith,password123456,
,,login,EVGA,,,https://www.evga.com/support/login.asp,hello@bitwarden.com,fakepassword,TOTPSEED123
,,note,My Note,"This is a secure note.

Notes can span multiple lines.",,,,,
```

{% file src="../../../.gitbook/assets/bitwarden_export (1).csv" %}
Okta 示例下载
{% endfile %}

{% hint style="info" %}
本表格旨在方便查找某些字段和值。某些配置和提供程序版本可能有所不同，具体取决于您的组织的策略和规则。如果您在为您的 Bitwarden 组织配置 SSO 登录时遇到困难，请[联系我们](https://bitwarden.com/contact/)以获取协助。
{% endhint %}

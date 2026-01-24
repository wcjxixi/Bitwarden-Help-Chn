# SSO FAQ

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/sso-faqs/)
{% endhint %}

本文包含了关于 **SSO** 的常见问题 (FAQ)。有关 SSO 的更多高级信息，请参考[关于 SSO](about-sso.md)。

## 日常使用 <a href="#everyday-use" id="everyday-use"></a>

### 问：更改我的 IdP 密码会更改我的 Bitwarden 主密码吗？ <a href="#q-will-changing-my-idp-password-change-my-bitwarden-master-password" id="q-will-changing-my-idp-password-change-my-bitwarden-master-password"></a>

**答：**&#x4E0D;会，当用户更改用于 IdP 的密码时，用户的主密码不会更改。

### 问：如果我的组织使用 SSO，我仍可以使用主密码验证吗？ <a href="#q-can-i-still-authenticate-with-my-master-password-if-my-organization-uses-sso" id="q-can-i-still-authenticate-with-my-master-password-if-my-organization-uses-sso"></a>

**答：**&#x9664;非组织已激活[要求单点登录身份验证](../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)策略，否则具有[用户角色](../manage-members/member-roles.md)的成员仍然可以使用主密码进行身份验证（如果他们有主密码），但某些[解密选项](sso-decryption-options.md)可能会移除或阻止他们拥有的主密码。

### 问：我仍然需要使用 Bitwarden 目录连接器吗？ <a href="#q-do-i-still-need-to-use-bitwarden-directory-connector" id="q-do-i-still-need-to-use-bitwarden-directory-connector"></a>

**答：**&#x5982;果您直接在 Bitwarden 中管理 Bitwarden 群组和集合分配，则无需使用目录连接器。但是，如果您希望群组和用户能自动与您的组织目录同步，我们建议将 SSO 登录和目录连接器结合使用以获得最完整的解决方案。

### 问：每次登录时是否都需要输入 SSO 标识符吗？ <a href="#q-do-i-need-to-enter-my-organization-identifier-every-time-i-login" id="q-do-i-need-to-enter-my-organization-identifier-every-time-i-login"></a>

**答：**&#x4E0D;需要。将包含标识符的 URL 添加为书签，例如 `https://vault.bitwarden.com/#/sso?identifier=my-identifier`，这样您就不必每次登录时都输入它。管理员还可以设置[声明域名](../oversight-visibility/claimed-domains/claimed-domains.md)，以便在成员的电子邮件地址具有匹配域名的情况下自动绕过此步骤。

## 配置 <a href="#configuration" id="configuration"></a>

### 问：SSO 与 SCIM 或目录连接器兼容吗？ <a href="#q-is-sso-compatible-with-scim-or-directory-connector" id="q-is-sso-compatible-with-scim-or-directory-connector"></a>

**答：**&#x662F;的。组织可以选择利用其中任何一个来同步群组和群组成员资格。

### 问：如何更改预先生成的 SSO 配置的值？ <a href="#q-how-do-i-change-pre-generated-sso-configuration-values" id="q-how-do-i-change-pre-generated-sso-configuration-values"></a>

**答：**&#x901A;过更改 `.bwdata/config.yml` 中的 `url:` 值如何运行 `./bitwarden.sh rebuild` 命令以应用您的更改，即可在自托管环境中更改预先生成的 SSO 配置值，包括 **SP 实体 ID**、**SAML 2.0 元数据 URL**、**ACS URL** 和**回调路径**。

这些无法在云上更改，但云端组织可以设置是从单点登录配置页面生成唯一的还是通用的 **SP 实体 ID**。

### 问：SSO 标识符有何用途？ <a href="#q-what-is-the-sso-identifier-used-for" id="q-what-is-the-sso-identifier-used-for"></a>

**答：**&#x53;SO 标识符用于指示在某些成员登录流程中使用 SSO 登录组织。该值是人类可读的，并且应该向成员表明它附属于您的组织。管理员可以设置[声明域名](../oversight-visibility/claimed-domains/claimed-domains.md)，以便在成员的电子邮件地址具有匹配域名的情况下自动绕过此步骤。

## 可支持性 <a href="#supportability" id="supportability"></a>

### 问：Bitwarden 支持 OAuth 2.0吗？ <a href="#q-does-bitwarden-support-oauth-2-0" id="q-does-bitwarden-support-oauth-2-0"></a>

**答：**&#x42;itwarden 支持 OpenID Connect，但目前不支持 OAuth。

### 问：SSO 可以在 Bitwarden 自托管服务器上使用吗？ <a href="#q-will-sso-work-with-a-self-hosted-bitwarden-server" id="q-will-sso-work-with-a-self-hosted-bitwarden-server"></a>

**答：**&#x53EF;以。只要服务器可以访问您的身份服务器即可。

### 问：SSO 可以在混合云环境下工作吗？ <a href="#q-will-sso-work-across-hybrid-cloud-environments" id="q-will-sso-work-across-hybrid-cloud-environments"></a>

**答：**&#x53EF;以。只要服务器可以访问您的身份服务器即可。

### 问：如果我的身份提供程序离线，用户仍然可以做身份验证吗？ <a href="#q-if-my-identity-provider-goes-offline-can-members-still-authenticate" id="q-if-my-identity-provider-goes-offline-can-members-still-authenticate"></a>

**答：**&#x5982;果您的身份提供程序离线，如果[成员拥有主密码](sso-decryption-options.md)并且[组织的策略选项](../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)允许，则可以使用电子邮箱和主密码登录。

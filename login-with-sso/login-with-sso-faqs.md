# SSO 登录常见问题

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/sso-faqs/)
{% endhint %}

本文包含了关于 **SSO 登录**的常见问题（FAQ）。

有关 **SSO 登录**的更多高级信息，请参考[关于 SSO 登录](about-login-with-sso.md)。

## 使用 SSO 登录 <a href="#using-login-with-sso" id="using-login-with-sso"></a>

### 问：为什么 SSO 登录需要主密码？ <a href="#q-why-does-login-with-sso-require-my-master-password" id="q-why-does-login-with-sso-require-my-master-password"></a>

**答：**SSO 登录允许您的员工使用您现有的身份提供程序 (IdP) 来**验证**他们的身份（即证明他们就是他们所说的那个人）。与其他工具相比，SSO 登录的独特之处在于它保留了我们的端到端零知识加密模型。Bitwarden 的任何人都不应该拥有您的密码库数据的访问权限，以及重要的是，您的身份提供程序也不应该。

这就是为什么 Bitwarden 的 SSO 登录**将验证和解密分开**的原因。您的 IdP 可以确认 Alice 实际上是 Alice，但不能也不应该拥有工具来解密 Alice 的密码库。只有 Alice 可以拥有这个工具，而且很方便，这就是她的主密码！

实际上，这意味着任何时候员工使用 SSO 登录 Bitwarden，他们都需要使用他们的主密码来解密他们的密码库，从而保护您的企业的关键凭据和机密。

{% hint style="info" %}
**自托管 Bitwarden 的组织**可以利用 [Key Connector](about-key-connector.md) 为 Bitwarden 客户端提供解密密钥，_以代替_要求用户使用他们的主密码来解密密码库数据。在[此处](member-decryption-options.md)以及[此处](about-key-connector.md)了解更多信息。
{% endhint %}

### 问：更改我的 SSO 密码会影响我的 Bitwarden 主密码吗？ <a href="#q-will-changing-my-sso-password-affect-my-bitwarden-master-password" id="q-will-changing-my-sso-password-affect-my-bitwarden-master-password"></a>

**答：**不会，您的主密码将保持不变。必须使用您的主密码来解密密码库数据，除非您的组织使用 [Key Connector](about-key-connector.md) 来自托管解密密钥。

### 问：SSO 身份验证可以代替我的主密码和电子邮件吗？ <a href="#q-does-sso-authentication-replace-my-master-password-and-email" id="q-does-sso-authentication-replace-my-master-password-and-email"></a>

**答：**不能。SSO 登录利用您现有的身份提供程序（IdP）来验证您进入Bitwarden 的身份，但是您的主密码和电子邮件仍然必须输入，以用于解密您的密码库数据，除非您的组织使用 [Key Connector](about-key-connector.md) 来自托管解密密钥。

### 问：如果我的组织启用了 SSO，我仍可以使用主密码登录吗？ <a href="#q-can-i-still-log-in-with-my-master-password-if-my-organization-has-sso-enabled" id="q-can-i-still-log-in-with-my-master-password-if-my-organization-has-sso-enabled"></a>

**答：**默认情况下，是可以的，您可以使用您的电子邮件地址和主密码登录 Bitwarden。但是，如果您的组织同时启用了[单一组织](../organizations/enterprise-policies.md#single-organization)和[单点登录验证](../organizations/enterprise-policies.md#single-sign-on-authentication)策略，或者您的组织使用了 [Key Connector](about-key-connector.md)，则所有非管理员用户都会被要求使用 SSO 登录。

### 问：SSO 登录对新用户如何工作（及时）？ <a href="#q-how-does-login-with-sso-work-for-new-users-just-in-time" id="q-how-does-login-with-sso-work-for-new-users-just-in-time"></a>

**答：**使用 SSO 登录到其组织的新用户将被置于其组织的接受状态，直到得到管理员的确认。如果随后将该用户手动分配或通过 Bitwarden 目录连接器分配给群组，届时他们将获得相应的共享项目的访问权限。

### 问：我仍然需要使用 Bitwarden 目录连接器吗？ <a href="#q-do-i-still-need-to-use-bitwarden-directory-connector" id="q-do-i-still-need-to-use-bitwarden-directory-connector"></a>

**答：**如果您直接在 Bitwarden 中管理 Bitwarden 群组和集合分配，则无需使用目录连接器。但是，如果您希望群组和用户能自动与您的组织目录同步，我们建议将 SSO 登录和目录连接器结合使用以获得最完整的解决方案。

### 问：每次登录时是否都需要输入我的组织标识符？ <a href="#q-do-i-need-to-enter-my-organization-identifier-every-time-i-login" id="q-do-i-need-to-enter-my-organization-identifier-every-time-i-login"></a>

**答：**不需要！将您的组织标识符作为您的企业单点登录页面的查询字符串，并将企业单点登录页面加入书签，将省去您每次输入的麻烦。示例：

* 对于云托管实例：`https://vault.bitwarden.com/#/sso?identifier=your-org-id`
* 对于自托管实例：`https://your.domain.com/#/sso?identifier=your-org-id`

### 问：如何更改预先生成的 SSO 配置的值？ <a href="#q-how-do-i-change-pre-generated-sso-configuration-values" id="q-how-do-i-change-pre-generated-sso-configuration-values"></a>

**答：**通过更改 `.bwdata/config.yml` 中的 `url:` 值并运行 `./bitwarden.sh rebuild` 命令以应用您的更改。可以在自托管环境中更改预先生成的 SSO 配置值，包括 **SP 实体 ID**、**SAML 2.0 元数据 URL**、**ACS URL** 和**回调路径**。

## 安全 <a href="#security" id="security"></a>

### 问：SSO 登录如何与零知识模型协同工作？ <a href="#q-how-does-login-with-sso-work-with-the-zero-knowledge-model" id="q-how-does-login-with-sso-work-with-the-zero-knowledge-model"></a>

**答：**Bitwarden SSO 登录仅执行用户身份认证，而不用于解密用户数据。添加 SSO 功能并不会将任何进一步的个人身份信息引入到 Bitwarden 数据库中。

## 计费 <a href="#billing" id="billing"></a>

### 问：哪些计划提供 SSO 登录功能？ <a href="#q-what-plans-offer-login-with-sso" id="q-what-plans-offer-login-with-sso"></a>

**答：**仅当前的企业计划提供此功能。参阅[这里](../plans-and-pricing/premium-renewal.md)以了解更多信息。

### 问：如何升级我的计划，使我可以使用 SSO 登录功能？ <a href="#q-how-do-i-upgrade-my-plan-so-that-i-can-use-login-with-sso" id="q-how-do-i-upgrade-my-plan-so-that-i-can-use-login-with-sso"></a>

**答：**[联系我们](https://bitwarden.com/contact/)并从**主题**下拉列表中选择**升级/更改计划**。我们强烈建议您通过[开始 7 天企业免费试用](../plans-and-pricing/start-a-free-trial-of-bitwarden-enterprise.md)来测试 SSO 登录。

### 问：我想测试 SSO 登录功能。如果我决定我不需要它，我可以恢复到我的经典 2019 计划吗？ <a href="#q-i-would-like-to-test-login-with-sso-if-i-decide-i-dont-need-it-can-i-revert-to-my-classic-2019-pla" id="q-i-would-like-to-test-login-with-sso-if-i-decide-i-dont-need-it-can-i-revert-to-my-classic-2019-pla"></a>

**答：**很遗憾，一旦您升级，我们无法将您恢复到经典 2019 计划。我们建议创建一个新的组织，开始 [7 天企业免费试用](../plans-and-pricing/start-a-free-trial-of-bitwarden-enterprise.md)，以测试在您的主要组织之外使用 SSO 登录。

## 可支持性 <a href="#supportability" id="supportability"></a>

### 问：Bitwarden 支持 OAuth 2.0吗？ <a href="#q-does-bitwarden-support-oauth-2-0" id="q-does-bitwarden-support-oauth-2-0"></a>

**答：**Bitwarden 支持 OpenID Connect，但目前不支持 OAuth。

### 问：SSO 登录可以在 Bitwarden 自托管实例上使用吗？ <a href="#q-will-login-with-sso-work-with-a-self-hosted-instance-of-bitwarden" id="q-will-login-with-sso-work-with-a-self-hosted-instance-of-bitwarden"></a>

**答：**是的。SSO 登录适用于自托管实例，无论实例是在本地还是在您自己的云中，只要实例可以访问您的身份服务器即可。

### 问：使用SSO登录是否可以在混合云环境下工作？ <a href="#q-does-login-with-sso-work-across-hybrid-cloud-environments" id="q-does-login-with-sso-work-across-hybrid-cloud-environments"></a>

答：可以。SSO 登录只要求能够从您的 Bitwarden 实例连接到您的身份提供程序。它可以用于云或本地身份提供程序，以及云或自托管的 Bitwarden 实例。

### 问：如果我的身份提供程序离线，用户可以使用 SSO 登录认证进入 Bitwarden 吗？ <a href="#q-if-my-identity-provider-is-offline-can-users-user-login-with-sso-to-authenticate-into-bitwarden" id="q-if-my-identity-provider-is-offline-can-users-user-login-with-sso-to-authenticate-into-bitwarden"></a>

**答：**如果您的身份提供程序离线，用户必须使用他们的电子邮件和主密码登录。随着我们为组织启用更多的认证控制机制，这一点可能会在未来发生变化。

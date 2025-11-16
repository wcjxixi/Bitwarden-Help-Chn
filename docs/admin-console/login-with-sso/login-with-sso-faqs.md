# SSO 登录 FAQ

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/sso-faqs/)
{% endhint %}

本文包含了关于 **SSO 登录**的常见问题 (FAQ)。有关 **SSO 登录**的更多高级信息，请参考[关于 SSO 登录](about-login-with-sso.md)。

## 使用 SSO 登录 <a href="#using-login-with-sso" id="using-login-with-sso"></a>

### 问：SSO 身份验证可以代替我的主密码和电子邮箱吗？ <a href="#q-does-sso-authentication-replace-my-master-password-and-email" id="q-does-sso-authentication-replace-my-master-password-and-email"></a>

**答：**&#x5982;果您的组织正在使用[受信任设备 SSO](trusted-devices/about-trusted-devices.md) 或使用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 自托管解密密钥，则 SSO 登录工作流程确实可以取代输入主密码登录的需要。在标准 SSO 工作流程中，Bitwarden 会利用您现有的身份提供程序 (IdP) 对您进行身份验证，但您仍必须输入主密码和电子邮箱才能解密您的密码库数据。

### 问：为什么 SSO 登录需要主密码？ <a href="#q-why-does-login-with-sso-require-my-master-password" id="q-why-does-login-with-sso-require-my-master-password"></a>

**答：**&#x9664;非您的企业使用受信设备 SSO，否则用户在使用 SSO 登录时必须输入主密码才能解密他们的密码库，从而保护企业的关键凭据和机密。

SSO 登录保留了我们的端到端零知识加密模型；Bitwarden 的任何人都没有您的密码库数据的访问权限，重要的是，**您的身份提供程序也没有**。这就是为什么 Bitwarden 的 SSO 登录要**将身份验证和解密分开**的原因。您的 IdP 可以确认 Alice 确实是 Alice，但不能也不应该拥有解密 Alice 密码库的工具。只有 Alice 才能拥有这种工具，在标准的 SSO 登录流程中，这就是她的主密码。[了解使用受信任设备 SSO 时如何解密数据](trusted-devices/about-trusted-devices.md#how-it-works)。

{% hint style="info" %}
Bitwarden 为企业提供了两种解决方案，允许经过批准的企业成员在不使用主密码的情况下访问他们的 Bitwarden 账户：

**受信任设备 SSO** 是一项功能，允许使用 SSO 登录的组织创建并存储成员设备的加密密钥，从而无需输入主密码。[了解更多有关受信任设备 SSO 的信息](trusted-devices/about-trusted-devices.md)。

**自托管 Bitwarden 组织**可利用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 向 Bitwarden 客户端提供解密密钥，而无需用户使用主密码对密码库数据进行解密。在[这里](member-decryption-options.md)和[这里](../../self-hosting/key-connector/about-key-connector.md)了解更多信息。
{% endhint %}

### 问：更改我的 SSO 密码会影响我的 Bitwarden 主密码吗？ <a href="#q-will-changing-my-sso-password-affect-my-bitwarden-master-password" id="q-will-changing-my-sso-password-affect-my-bitwarden-master-password"></a>

**答：**&#x4E0D;会，您的主密码将保持不变。必须使用您的主密码来解密密码库数据，除非您的组织使用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 来自托管解密密钥。

### 问：如果我的组织启用了 SSO，我仍可以使用主密码登录吗？ <a href="#q-can-i-still-log-in-with-my-master-password-if-my-organization-has-sso-enabled" id="q-can-i-still-log-in-with-my-master-password-if-my-organization-has-sso-enabled"></a>

**答：**&#x9ED8;认情况下，是可以的，您可以使用您的电子邮件地址和主密码登录 Bitwarden。但是，如果您的组织同时启用了[单一组织](../oversight-visibility/enterprise-policies.md#single-organization)和[单点登录验证](../oversight-visibility/enterprise-policies.md#single-sign-on-authentication)策略，或者您的组织使用了 [Key Connector](../../self-hosting/key-connector/about-key-connector.md)，则所有非管理员用户都会被要求使用 SSO 登录。

### 问：新用户如何使用 SSO 登录（即时）？ <a href="#q-how-does-login-with-sso-work-for-new-users-just-in-time" id="q-how-does-login-with-sso-work-for-new-users-just-in-time"></a>

答：在 IdP 中授权使用 Bitwarden 应用程序以及在 Bitwarden 登录页面上选择了**登录** → **企业 SSO** 的新用户将被置于其组织的`接受`状态，直到管理员确认。

当该用户被手动或通过 Directory Connector 分配到一个组群时，他们将获得相应共享项目的访问权限。 如果您希望成员不使用主密码，而只能使用受信任设备，建议使用 JIT 配置。

### 问：我仍然需要使用 Bitwarden 目录连接器吗？ <a href="#q-do-i-still-need-to-use-bitwarden-directory-connector" id="q-do-i-still-need-to-use-bitwarden-directory-connector"></a>

**答：**&#x5982;果您直接在 Bitwarden 中管理 Bitwarden 群组和集合分配，则无需使用目录连接器。但是，如果您希望群组和用户能自动与您的组织目录同步，我们建议将 SSO 登录和目录连接器结合使用以获得最完整的解决方案。

### 问：每次登录时是否都需要输入 SSO 标识符吗？ <a href="#q-do-i-need-to-enter-my-organization-identifier-every-time-i-login" id="q-do-i-need-to-enter-my-organization-identifier-every-time-i-login"></a>

**答：**&#x4E0D;需要！如果您的组织使用[域名验证](claimed-domains.md)，则无需输入此标识符。否则，管理员应分发以下 URL（其中 `{your-sso-identifier}` 是您的组织的 SSO 标识符），以自动将用户重定向到 SSO 登录界面：

* 对于 US 云托管实例：`https://vault.bitwarden.com/#/sso?identifier={your-sso-identifier}`
* 对于 EU 云托管实例：`https://vault.bitwarden.eu/#/sso?identifier={your-sso-identifier}`
* 对于自托管实例：`https://your.domain.com/#/sso?identifier={your-sso-identifier}`

### 问：如何更改预先生成的 SSO 配置的值？ <a href="#q-how-do-i-change-pre-generated-sso-configuration-values" id="q-how-do-i-change-pre-generated-sso-configuration-values"></a>

**答：**&#x901A;过更改 `.bwdata/config.yml` 中的 `url:` 值并运行 `./bitwarden.sh rebuild` 命令以应用您的更改。可以在自托管环境中更改预先生成的 SSO 配置值，包括 **SP 实体 ID**、**SAML 2.0 元数据 URL**、**ACS URL** 和**回调路径**。

## 安全 <a href="#security" id="security"></a>

### 问：SSO 登录如何与零知识模型协同工作？ <a href="#q-how-does-login-with-sso-work-with-the-zero-knowledge-model" id="q-how-does-login-with-sso-work-with-the-zero-knowledge-model"></a>

**答：**&#x4F7F;用 SSO 凭证登录 Bitwarden 仅执行用户身份验证，并不解密用户数据。在大多数情况下，通过使用[受信任设备 SSO](trusted-devices/about-trusted-devices.md) 时的设备密钥完成解密，或通过使用主密码完成解密，而主密码则由用户全权负责。自托管 Bitwarden 组织也可以使用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 作为解密密码库数据的替代手段。添加 SSO 功能不会在 Bitwarden 数据库中引入更多个人身份信息。

## 计费 <a href="#billing" id="billing"></a>

### 问：哪些方案提供 SSO 登录功能？ <a href="#q-what-plans-offer-login-with-sso" id="q-what-plans-offer-login-with-sso"></a>

**答：**&#x4F01;业方案提供此功能。

### 问：如何升级我的方案，以便使用 SSO 登录？ <a href="#q-how-do-i-upgrade-my-plan-so-that-i-can-use-login-with-sso" id="q-how-do-i-upgrade-my-plan-so-that-i-can-use-login-with-sso"></a>

**答：**&#x5728;管理控制台中，导航至**订阅** → **计费**页面然后选择**升级方案**。我们强烈建议您开始 [7 天企业免费试用](../../plans-and-pricing/start-an-enterprise-trial-with-your-bitwarden-account.md)，以测试 SSO 登录。

## 可支持性 <a href="#supportability" id="supportability"></a>

### 问：Bitwarden 支持 OAuth 2.0吗？ <a href="#q-does-bitwarden-support-oauth-2-0" id="q-does-bitwarden-support-oauth-2-0"></a>

**答：**&#x42;itwarden 支持 OpenID Connect，但目前不支持 OAuth。

### 问：SSO 登录可以在 Bitwarden 自托管实例上使用吗？ <a href="#q-will-login-with-sso-work-with-a-self-hosted-instance-of-bitwarden" id="q-will-login-with-sso-work-with-a-self-hosted-instance-of-bitwarden"></a>

**答：**&#x662F;的。SSO 登录适用于自托管实例，无论实例是在本地还是在您自己的云中，只要实例可以访问您的身份服务器即可。

### 问：SSO 登录是否可以在混合云环境下工作？ <a href="#q-does-login-with-sso-work-across-hybrid-cloud-environments" id="q-does-login-with-sso-work-across-hybrid-cloud-environments"></a>

答：可以。SSO 登录只要求能够从您的 Bitwarden 实例连接到您的身份提供程序。它可以用于云或本地身份提供程序，以及云或自托管的 Bitwarden 实例。

### 问：如果我的身份提供程序离线，用户可以使用 SSO 登录验证进入 Bitwarden 吗？ <a href="#q-if-my-identity-provider-is-offline-can-users-user-login-with-sso-to-authenticate-into-bitwarden" id="q-if-my-identity-provider-is-offline-can-users-user-login-with-sso-to-authenticate-into-bitwarden"></a>

**答：**&#x5982;果您的身份提供程序离线，用户必须使用他们的电子邮箱和主密码登录。随着我们为组织启用更多的验证控制机制，这一点可能会在未来发生变化。

# 新设备登录保护

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/new-device-verification/)
{% endhint %}

{% hint style="info" %}
从 **2025 年 3 月 4 日**开始，从新设备登录时，将会提示进行这个新的验证。这一变更最初将反应在网页 App 中，随着用户更新到最新的发行版本，将逐步扩展到其他 Bitwarden App 中。
{% endhint %}

为确保您的账户安全，Bitwarden 将对**未使用**[**两步登录**](../two-step-login/setup-guides/two-step-login-methods.md)**的用户**要求额外的验证。**当从一个以前未登录过的设备登录时**，在您输入 Bitwarden 主密码后，系统会提示您输入发送到您账户电子邮箱的一次性验证码，以完成登录过程。例如，如果您登录的是以前使用过的移动 App 或浏览器扩展，则不会收到此提示。

除非频繁登录新的设备，否则大多数用户不会收到此提示。只有新设备或清除浏览器 cookie 后才需要进行此验证。

如果您经常访问电子邮箱，获取此验证码应该很简单。如果您不想依赖您的 Bitwarden 账户电子邮箱进行验证，您可以通过[验证器 App](../two-step-login/setup-guides/two-step-login-via-authenticator.md)、[硬件密钥](../two-step-login/setup-guides/two-step-login-via-yubikey.md)或不同的[电子邮箱](../two-step-login/setup-guides/two-step-login-via-email.md)来[设置两步登录](../two-step-login/setup-guides/two-step-login-methods.md)。

## FAQ

### 何时会发生？ <a href="#when-will-this-happen" id="when-will-this-happen"></a>

从 **2025 年 3 月 4 日**开始，新设备登录时将会提示进行新的验证。这一变更最初将反应在网页 App 中，在用户更新到最新的发布版本将后扩展到其他 Bitwarden App 中。

### Bitwarden 为什么要实施这一举措？ <a href="#why-is-bitwarden-implementing-this" id="why-is-bitwarden-implementing-this"></a>

Bitwarden 正在实施这一变更，以增强未激活[两步登录](../two-step-login/setup-guides/two-step-login-methods.md)功能的用户的安全性。如果有人获取了您的密码，在没有二次验证（发送到您邮箱的验证码）的情况下，他们仍然无法登录您的账户。这个额外的层级有助于保护您的数据不受黑客攻击，因为黑客通常会利用弱密码或暴露的密码来获得未经授权的访问。

### 何时会提示我进行此验证？ <a href="#when-will-i-get-prompted-for-this-verification" id="when-will-i-get-prompted-for-this-verification"></a>

只有在使用新的设备登录时，才会提示您进行此验证。如果您登录的是以前使用过的设备，则您不会收到提示。

### 什么设备被视为新的设备？ <a href="#what-is-considered-a-new-device" id="what-is-considered-a-new-device"></a>

新设备是指以前没有用来登录过您的 Bitwarden 账户的任何设备。这可能包括您从未登录过的新手机、平板、计算机或浏览器扩展。当您从新设备登录时，系统会要求您通过发送到您电子邮箱的一次性代码验证您的身份。

会触发新设备的其他情况包括：

* 卸载并重新安装移动 App、桌面 App 或浏览器扩展将触发新设备。
* 清除浏览器 cookie 将为网页 App 触发新设备，但不会为浏览器扩展触发新设备。
* 在虚拟桌面基础架构 (VDI) 中使用浏览器扩展，在每次会话后重置用户配置文件存储。在这种情况下，[本地存储](../../security/storage.md#on-your-local-machine)不会持久化。

### 我的电子邮箱凭据保存在 Bitwarden 中。我会被锁定在 Bitwarden 之外吗？ <a href="#my-email-credentials-are-saved-in-bitwarden.-will-i-be-locked-out-of-bitwarden" id="my-email-credentials-are-saved-in-bitwarden.-will-i-be-locked-out-of-bitwarden"></a>

对于未启用两步登录的用户，仅在新设备上会要求电子邮箱验证码。在之前已登录过的设备上，您不会收到此提示，您可以像往常一样使用您的账户电子邮箱和主密码登录。

如果您登录到新设备，您的 Bitwarden 账户电子邮箱将收到一个一次性验证码。如果您可以访问您的电子邮箱（例如，在手机上已持久登录的电子邮箱），然后您就可以获取一次性验证码来登录了。登录到新设备后，系统不会再提示您输入验证码。

如果您经常使用保存在 Bitwarden 中的凭据登录电子邮箱，或者不希望依赖电子邮箱进行验证，您应该设置独立于 Bitwarden 账户电子邮箱的[两步登录方式](../two-step-login/setup-guides/two-step-login-methods.md)。这包括验证器 App、安全密钥或使用不同电子邮箱的基于电子邮箱的两步登录。激活任何 2FA 方法都将使用户退出基于电子邮箱的新设备验证。已激活 2FA 的用户还应将其 Bitwarden [恢复代码](../two-step-login/recovery-codes.md)保存在安全的地方。

### 哪些人被排除在基于账户电子邮箱的新设备验证之外？ <a href="#who-is-excluded-from-this-account-email-based-new-device-verification" id="who-is-excluded-from-this-account-email-based-new-device-verification"></a>

不包括以下类别的登录：

* 已经设置了两步登录的用户。
* 已经使用了 SSO、通行密钥或 API 密钥登录的用户。
* 自托管用户。
* 从以前登录过的设备登录的用户。
* 从**设置** → **我的账户**界面选择退出的用户（**不建议**）。

### 我的组织使用 SSO，我的用户是否必须完成新设备验证？ <a href="#my-organization-users-sso-do-my-users-have-to-complete-new-device-verification" id="my-organization-users-sso-do-my-users-have-to-complete-new-device-verification"></a>

不需要。使用 SSO 登录的用户不会被要求在新设备上验证登录。但是，如果用户未启用两步登录，不通过 SSO 而是使用用户名和密码登录，则他们会被要求验证新设备。

### 我不想与 Bitwarden 分享我的真实电子邮箱，我该如何设置我的账户？ <a href="#i-do-not-want-to-share-my-real-email-with-bitwarden-how-can-i-set-up-my-account" id="i-do-not-want-to-share-my-real-email-with-bitwarden-how-can-i-set-up-my-account"></a>

希望保持匿名的用户有多种选择：

* 使用非电子邮箱方式的两步登录选项，包括验证器 App、安全密钥或使用不同电子邮箱的基于电子邮箱的两步登录。
* 使用电子邮箱别名转发服务。
* 自托管 Bitwarden。

Bitwarden 鼓励用户拥有一个有效的电子邮箱，因为 Bitwarden 会发送诸如登录尝试失败等重要的安全警报。

### 如果我在新设备上使用 2FA 恢复代码（因为我丢失了 2FA 访问权限），我是否仍然需要接受新设备验证？ <a href="#if-i-use-the-2fa-recovery-code-on-a-new-device-because-ive-lost-my-2fa-access-will-i-still-be-subjec" id="if-i-use-the-2fa-recovery-code-on-a-new-device-because-ive-lost-my-2fa-access-will-i-still-be-subjec"></a>

Bitwarden 正在更新恢复代码流程，以便当您提交密码和恢复代码时，您将登录到网页 App 并进入 2FA 设置页面。如果您担心被锁定，应避免在隐身浏览器或具有不可靠的网络连接的设备上执行此流程，以确保您可以在登录会话中完成所有必要的设置步骤。

### 我想选择退出！有什么选择吗？ <a href="#i-want-to-opt-out-is-there-an-option-to" id="i-want-to-opt-out-is-there-an-option-to"></a>

这是为未启用两步登录的用户增加的额外安全措施。未启用两步登录的用户更容易受到攻击者的未经授权的访问，因为即使密码强度高且唯一，也可能通过多种方式被泄露。例如，常见的方法包括：

* **钓鱼攻击**：网络犯罪分子使用欺骗性电子邮件或网站诱骗您泄露密码。
* **社会工程攻击**：攻击者可能通过电话、短信或其他方式试图操纵或欺骗您泄露您的密码。
* **暴力破解攻击**：攻击者使用自动化工具反复尝试猜测密码。
* **键盘记录或恶意软件**：如果您的设备感染了恶意软件或键盘记录器，攻击者可能会在您不知情的情况下记录您的每一次按键，包括您的密码。

通过新设备验证，即使您的密码通过上述某种方式泄露，攻击者仍然需要获取第二个验证因素（即您电子邮箱中的一次性代码）。这大大降低了未经授权访问的可能性。

新设备验证的设计比传统的两步登录更少干扰。它仅适用于从未使用过的设备或客户端登录时，因此大多数用户不会遇到这一额外步骤，因为他们通常会在日常设备上登录。验证过程使用您的电子邮箱（许多人会在手机或电脑上保持邮箱登录状态），因此获取代码既快速又简单。

具有以下情况的用户可能会遇到一些挑战：

* 未启用两步登录。
* 将电子邮箱密码存储在 Bitwarden 中。
* 频繁卸载并重新安装 Bitwarden。
* 在所有地方都退出了电子邮箱登录。

只有同时满足上述所有条件的用户才会受到此安全更新的影响。如果用户确实被锁定账户，可以联系 Bitwarden 的客户支持团队。

如果用户不希望使用新设备验证，强烈建议启用其他两步登录方式（验证器 App、硬件密钥或不同的电子邮箱）之一来保护您的账户。

如果用户不希望使用新设备验证，也不想设置其他两步登录方式，并且不希望账户有任何安全保护，可以通过导航到**设置** → **我的账户**页面并滚动到**危险区域**部分选择退出。我们必须强调，**强烈不建议这样做**，因为这会使您的账户容易受到各种攻击。

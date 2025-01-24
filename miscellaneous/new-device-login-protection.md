# 新设备登录保护（2025 年初）

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/new-device-verification/)
{% endhint %}

为确保您的账户安全，2025 年初开始，Bitwarden 将对**未使用两步登录的用户**要求额外的验证。**当从一个新的设备登录或清除浏览器 cookie 后**登录，在您输入 Bitwarden 主密码后，系统会提示您输入发送到您账户电子邮箱的一次性验证码，以完成登录过程。

如果您不想依赖您的 Bitwarden 账户电子邮箱，您可以设置独立于账户电子邮箱的两步登录，例如验证器 App、硬件钥匙或通过不同电子邮箱的两步登录。

## FAQ

### 何时实施？ <a href="#when-will-this-happen" id="when-will-this-happen"></a>

这一变更将从 2025 年 2 月开始生效。

### Bitwarden 为什么要实施这一举措？ <a href="#why-is-bitwarden-implementing-this" id="why-is-bitwarden-implementing-this"></a>

使用弱主密码或重复使用的主密码以及没有两步登录的用户面临的风险更大。Bitwarden 的目的是在此类用户首次登录设备时增加一层身份验证，从而提高用户的安全性。

### 我的电子邮箱凭据保存在 Bitwarden 中。我应该担心循环依赖吗？ <a href="#my-email-credentials-are-saved-in-bitwarden.-should-i-be-worried-about-a-circular-dependency" id="my-email-credentials-are-saved-in-bitwarden.-should-i-be-worried-about-a-circular-dependency"></a>

用户可以设置一个独立于 Bitwarden 账户电子邮箱的 2FA 方法，包括验证器 App、安全钥匙或使用不同电子邮箱的基于电子邮箱的两步登录。激活任何 2FA 方法都将使用户退出基于电子邮箱的新设备验证。对于未启用 2FA 的用户，他们需要在 Bitwarden 之外保留对电子邮箱账户的访问权限。例如，用户可以将自己的电子邮箱密码写在紧急恢复表上，并将其保存在安全的物理位置。已启用 2FA 的用户应将其 Bitwarden [恢复代码](../two-step-login/recovery-codes.md)保存在安全的地方。

### 哪些人被排除在基于账户电子邮件的新设备验证之外？ <a href="#who-is-excluded-from-this-account-email-based-new-device-verification" id="who-is-excluded-from-this-account-email-based-new-device-verification"></a>

不包括以下类别的登录：

* 已经设置了两步登录的用户。
* 已经使用了 SSO、通行密钥或 API 密钥登录的用户。
* 自托管用户。
* 从以前登录过的设备登录的用户。

### 我的组织使用 SSO，我的用户是否必须完成新设备验证？ <a href="#my-organization-users-sso-do-my-users-have-to-complete-new-device-verification" id="my-organization-users-sso-do-my-users-have-to-complete-new-device-verification"></a>

不需要。使用 SSO 登录的用户不会被要求在新设备上验证登录。但是，如果用户不通过 SSO 而使用用户名和密码登录，只要未设置两步登录，就会被要求验证新设备。

### 我不想与 Bitwarden 共享我的真实电子邮箱，我该如何设置我的账户？ <a href="#i-do-not-want-to-share-my-real-email-with-bitwarden-how-can-i-set-up-my-account" id="i-do-not-want-to-share-my-real-email-with-bitwarden-how-can-i-set-up-my-account"></a>

希望保持匿名的用户有多种选择：

* 使用多种两步登录选项中的一种或多种来保护您的账户安全，其中很多都是免费的。
* 使用电子邮箱别名转发服务。
* 自行托管 Bitwarden。

Bitwarden 鼓励用户拥有一个有效的电子邮箱，因为 Bitwarden 会发送诸如登录尝试失败等重要的安全警报。

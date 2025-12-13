# 为何要使用两步登录？

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/bitwarden-field-guide-two-step-login/)
{% endhint %}

两步登录（也称为双重身份验证或 2FA）是网站和 App 常用的一种安全技术，用于保护您的敏感数据。使用两步登录的网站会要求您除了输入用户名和密码外，还要输入一个额外的「令牌」（也称为验证码或一次性密码 (OTP)）来验证您的身份，该令牌通常从不同的设备上获取。

如果没有辅助设备令牌的物理访问权限，恶意行为者即使知道了您的用户名和密码，他们也无法访问网站：

{% embed url="https://bitwarden.com/assets/6E6lpxB8UfXU7V6YcW40S3/b89a863ed448d1b90e42ac6c25140edd/fg-1.png?w=960&fm=avif" %}
基本两步登录流程
{% endembed %}

通常，拥有敏感数据（例如您的网上银行账户）的网站或 App 会尝试在登录界面之外通过以下方式验证您的身份：

* 将包含令牌的 SMS / 文本信息发送到移动设备上。
* 要求提供由移动设备上的验证器 App（例如 [Bitwarden Authenticator](../../bitwarden-authenticator/bitwarden-authenticator.md)）生成的令牌。
* 从物理安全钥匙（例如 YubiKey）中查找令牌。

## 我该如何使用两步登录？ <a href="#how-should-i-use-two-step-login" id="how-should-i-use-two-step-login"></a>

安全性通常需要在保护和便利之间进行权衡，因此最终取决于您！通常，使用两步登录的两个最重要的用途：

**1、**[**保护 Bitwarden** ](field-guide-for-two-step-login.md#securing-bitwarden)

Bitwarden 支持多种两步登录方式，您可以使用这些方式来保护密码库数据的安全。启用两步登录后，将要求您在每次登录时，除了输入主密码外，还要完成第二步。

**2、**[**保护重要的网站**](field-guide-for-two-step-login.md#securing-important-websites)

通过在登录时要求使用临时一次性密码 (TOTP) 来保护单个网站。您可以使用 Bitwarden 存储和生成 TOTP。

## 保护 Bitwarden <a href="#securing-bitwarden" id="securing-bitwarden"></a>

由于您的密码管理器存储了您的所有登录信息，我们强烈建议您使用两步登录来保护它。这样做可以保护您的所有登录信息，以防止恶意行为者访问您的密码库，即使他们获取了您的主密码。

启用两步登录将要求您在每次登录时，除了输入您的主密码外，还要完成第二步。解锁密码库时您无需完成第二步，仅登录时需要。

{% embed url="https://bitwarden.com/assets/1fc7ZMSHr1grocnEitdwua/1fbdceda08b4a6c59b17a96b366ffacd/fg-2.png?w=960&fm=avif" %}
两步登录访问 Bitwarden
{% endembed %}

Bitwarden 为免费账户提供了好几种两步登录方式，包括：

* FIDO（任何经过 FIDO2 WebAuthn 认证的钥匙）
* 验证器 App（如 [Bitwarden Authenticator](../../bitwarden-authenticator/bitwarden-authenticator.md)）
* 电子邮箱

对于高级用户，Bitwarden 还提供了好几种高级的两步登录方式：

* Duo Security 的 Duo Push、短信、电话和安全钥匙
* YubiKey（任何 4/5 系列设备或 YubiKey NEO/NFC）

使用我们的**设置指南**，[了解有关选项的更多信息](setup-two-step-login/two-step-login-methods.md)，或获取设置任何方式的帮助。

{% hint style="info" %}
由于 SIM 劫持等漏洞，Bitwarden 不支持 SMS 2FA。我们不建议对其他账户使用 SMS 2FA，除非它是唯一可用的方法。建议使用任何一种第二个因素而不是不使用，但多数替代方案比 SMS 2FA 更安全。
{% endhint %}

## 保护重要的网站 <a href="#securing-important-websites" id="securing-important-websites"></a>

Bitwarden 可能不是您使用的唯一一个具有两步登录选项的网站或 App，两步登录选项对于存储敏感信息（例如，信用卡或银行账号）的网站特别有用。大多数网站的两步登录选项都位于**设置**、**安全**或**隐私**菜单中。

激活两步登录时，通常会打开一个二维码，比如 Reddit 的这个：

![2FA 二维码](../../../.gitbook/assets/reddit-2fa-setup.png)

使用验证器 App 扫描这个代码后，就能使 App 生成轮换的 6 位数令牌，您可以用此令牌来验证您的身份，比如这个由 [Bitwarden Authenticator](../../bitwarden-authenticator/bitwarden-authenticator.md) 生成的令牌：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/kBDOyVjNB2DiINm7FHk0r/13b3f7bceb014df08b84246256451322/IMG_5440.png?_a=DAJCwlWIZAAB" %}
TOTP 令牌
{% endembed %}

### 使用 Bitwarden Authenticator <a href="#use-bitwarden-authenticator" id="use-bitwarden-authenticator"></a>

Bitwarden Authenticator 是一款移动身份验证 App，您可以用它在使用双因素身份验证 (2FA) 的网站和 App 上验证您的身份。Bitwarden Authenticator 可以从 iOS App Store 和 Google Play Store 下载。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5WsEwCqHd3BmAKTGdhXpQZ/bc84335eeb3655916781b1dd7cd4f4f1/fg-5.png?_a=DAJCwlWIZAAB" %}
使用 Bitwarden Authenticator 进行两步登录
{% endembed %}

有关设置和使用 Bitwarden Authenticator 的更多信息，请参阅[这篇文章](../../bitwarden-authenticator/bitwarden-authenticator.md)。

### 使用集成身份验证 <a href="#use-integrated-authentication" id="use-integrated-authentication"></a>

作为替代方案，Bitwarden Password Manager 为高级用户（包括付费组织（家庭、团队或企业）的成员）提供了一个内置的身份验证器。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4XRROCzbnmkN2EM9iO7MLX/3cf42adb04c450c833cd7d8aad836665/fg-3.png?_a=DAJCwlWIZAAB" %}
使用 Bitwarden 两步登录
{% endembed %}

有关使用集成身份验证的帮助，请参阅[这篇文章](../../password-manager/your-vault/security-tools/totp.md)。

### 什么时候我应该使用独立的 App 而不是集成的身份验证器？

只有独立 App 允许您为自己的 Bitwarden 账户设置 2FA，但您可以使用其中任何一款 App 为您的所有其他账户存储和生成验证码。目前只有集成的身份验证器允许您在团队成员之间共享生成的令牌。它们可以一起使用，也可以分开使用，这取决于您的安全偏好。

## 2FA 安全密钥和通行密钥 <a href="#id-2fa-security-keys-and-passkeys" id="id-2fa-security-keys-and-passkeys"></a>

FIDO2 安全密钥是一种流行且安全的选项，用于将 2FA 添加到您的 Bitwarden 账户。如果您还不熟悉 FIDO2 安全密钥，请[访问 FIDO 联盟网站](https://fidoalliance.org/fido2/)，了解有关 FIDO2 的更多信息。

YubiKey 设备是一种与 FIDO 身份验证协议配合使用的安全密钥，并且可以有多种用例。其中两种用途是作为 2FA 安全钥匙或[通行密钥](https://bitwarden.com/blog/what-are-passkeys-and-passkey-login/)。

* **2FA 安全密钥**：使用 YubiKey 作为 2FA 安全密钥将充当身份验证过程中的附加设备。这将伴随另一种主要的身份验证方法（例如主密码）。YubiKey 安全密钥必须物理插入才能提供身份验证凭据。
* **通行密钥**：通行密钥是一对加密密钥或公私加密密钥，用于验证登录。使用单一通行密钥，可以替代创建用户名、密码并向账户添加 2FA。在创建通行密钥期间，YubiKey 能够作为通行密钥生成器来创建通行密钥登录所需的公钥和私钥。在[此处](https://www.yubico.com/resources/glossary/what-is-a-passkey/)了解有关更多使用 YubiKey 作为通行密钥的信息。

对于 Bitwarden，YubiKey 设备等安全密钥的主要用途是提供 2FA 身份验证。

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经是两步登录的专家了，我们建议你：

* [设置两步登录](setup-two-step-login/two-step-login-methods.md)
* [获取高级会员以使用高级两步登录方式](https://vault.bitwarden.com/#/?premium=purchase)
* [设置 Bitwarden authenticator](../../password-manager/your-vault/security-tools/totp.md)
* [为团队和企业设置两步登录](setup-two-step-login/two-step-login-methods.md#two-step-login-for-teams-and-enterprise)

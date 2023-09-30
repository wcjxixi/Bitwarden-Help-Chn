# 两步登录现场指南

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/bitwarden-field-guide-two-step-login/)
{% endhint %}

## 什么是两步登录？ <a href="#what-is-two-step-login" id="what-is-two-step-login"></a>

两步登录（也称为双因素验证或 _2FA_）是一种越来越常见的安全技术，被网站和应用程序用来保护您的敏感数据。使用两步登录的网站会要求您除了输入用户名和密码外，还要输入一个额外的「令牌」（也称为验证码或一次性密码 (OTP)）来验证您的身份，该令牌通常从不同的设备上获取。

如果他们无法从您的辅助设备上访问令牌，恶意行为者即使知道了您的用户名和密码，他们也无法访问网站：

{% embed url="https://bitwarden.com/_gatsby/image/c94b8d98db4e25b087c13ae5b3380ffe/df3d74ff52a7f409cfdddc70d8d1be60/fg-1.webp?eu=db8f50e1b29dfcd60739a3d06c716469b43f50a3a85430823860edfd47a196d020f44d5721c072e57d6d52dad3e340ec66cf2d611abad0de96ba4bf0ef61a20152d250b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af855a34b6f6ee5c6da7fd1085153852a24b16f864d893c16116e79fb819ecb3baad0dc5c8e67f0e408ef73773244a4c5ae82cbfa5e75025267f174634d0ef0690&a=w%3D850%26h%3D478%26fm%3Dwebp%26q%3D75&cd=2023-09-26T13%3A34%3A24.243Z" %}
基本两步登录流程
{% endembed %}

通常情况下，拥有敏感数据的网站或应用程序（例如，您的在线银行账户）会试图在登录屏幕之外验证您的身份，比如使用如下方式之一：

* 将包含令牌的 SMS/文本信息发送到移动设备上
* 要求提供由移动设备上的验证器应用程序（例如 Authy）生成的令牌
* 从物理安全钥匙（例如 Yubikey）中查找令牌

## 我应该使用两步登录？ <a href="#how-should-i-use-two-step-login" id="how-should-i-use-two-step-login"></a>

安全性通常需要在保护和便利之间进行权衡，因此最终取决于您！通常，使用两步登录的两个最重要的用途：

**1、**[**保护 Bitwarden** ](field-guide-for-two-step-login.md#securing-bitwarden)

Bitwarden 支持多种两步登录方式，您可以使用这些方式来保护密码库数据的安全。启用两步登录后，将要求您在每次登录时，除了输入主密码外，还要完成第二步。

**2、**[**保护重要的网站**](field-guide-for-two-step-login.md#securing-important-websites)

通过在登录时要求使用临时一次性密码 (TOTP) 来保护单个网站。您可以使用 Bitwarden 存储和生成 TOTP。

## 保护 Bitwarden <a href="#securing-bitwarden" id="securing-bitwarden"></a>

由于您的密码管理器存储了您的所有登录信息，我们强烈建议您使用两步登录来保护它。这样做可以保护您的所有登录信息，以防止恶意行为者访问您的密码库，即使他们获取了您的主密码。

启用两步登录将要求您在每次登录时，除了输入您的主密码外，还要完成第二步。解锁密码库时您无需完成第二步，仅登录时需要。

{% embed url="https://bitwarden.com/_gatsby/image/42078bb55230ce62e57a2aa4f313c8fe/df3d74ff52a7f409cfdddc70d8d1be60/fg-2.webp?eu=8edd04b3b7cdaad5086fa6813976356ae93f05a9a8543fd2346decf91aadcc842dfa4a5725912be4286c09d9d5b145e866902e674debd88c93ee4ea7e835f90e52d15fed64ba77025629c7f6b5a604473dcf4e5fabdb8c4ce32e78cbfaeaea214e055f35fb3eeed0afea6020f39d7167aea9a16c3b91ed22e14456098c1f6efd32e897b44e7d968cb148adb9bdf77c94d8b36a4211c4a63323214c4a58b97fbdacbb06243d20440f32ceac5bce68c4b06a49682b0c561ca13027d24bbb3266&a=w%3D850%26h%3D478%26fm%3Dwebp%26q%3D75&cd=2023-09-26T13%3A34%3A41.244Z" %}
两步登录访问 Bitwarden
{% endembed %}

Bitwarden 为免费账户提供了好几种两步登录方式，包括：

* FIDO（任何经过 FIDO2 WebAuthn 认证的钥匙）
* 验证器应用程序（如 [2FAS](https://2fas.com/)、[Ravio](https://raivo-otp.com/) 或 [Aegis](https://getaegis.app/)）
* 电子邮件

对于高级会员账户，Bitwarden 还提供了好几种高级两步登录方式：

* Duo Security 的 Duo Push、短信、电话和安全钥匙
* YubiKey（任何 4/5 系列设备或 YubiKey NEO/NFC）

使用我们的**设置指南**，[了解有关选项的更多信息](two-step-login-methods.md)，或获取设置任何方式的帮助。

{% hint style="info" %}
由于 SIM 劫持等漏洞，Bitwarden 不支持 SMS 2FA。我们不建议对其他账户使用 SMS 2FA，除非它是唯一可用的方法。建议使用任何一种第二个因素而不是不使用，但多数替代方案比 SMS 2FA 更安全。
{% endhint %}

## 保护重要的网站 <a href="#securing-important-websites" id="securing-important-websites"></a>

Bitwarden 可能不是你使用的唯一一个具有两步登录选项的网站或应用，两步登录选项对于存储敏感信息（例如，信用卡或银行账号）的网站特别有用。可以在大多数具有两步登录选项的网站的**设置**、**安全**或**隐私**菜单中找到它。

激活两步登录时，通常会打开一个二维码，比如 Reddit 的这个：

![2FA 二维码](../.gitbook/assets/reddit-2fa-setup.png)

使用验证器应用程序扫描这个代码后，就能使程序生成轮换的 6 位数令牌，你可以用此令牌来验证你的身份，比如这个由 Authy 生成的令牌：

![TOTP 令牌](../.gitbook/assets/reddit-token.png)

### 使用 Authy <a href="#use-authy" id="use-authy"></a>

要使用 Authy 设置 Reddit 的两步登录，请点击**添加账户**按钮，并扫描您的网站或应用程序呈现的二维码。扫描二维码将生成你的 6 位数令牌。在**验证码**输入框中输入此代码，即可完成使用 Authy 的两步登录设置。

{% embed url="https://bitwarden.com/_gatsby/image/a4d83215c3377d9a6370efa6aea6b97a/df3d74ff52a7f409cfdddc70d8d1be60/fg-5.webp?eu=8e8655b7ea9aafd65e3ba98b6b76626ae46e01aba85965d36967e1a91efb998575f31a52739678e22f6d59dcdae714bb32952b6748bb8688c9be4bfcee60fc0e54d60bbd33b42104592ac6a8e4a60e433bce1c0af38a9a09f06f7addb4bae17518021e29ae7abc81b9ae3531b9d67964bebea52b6f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32bec2f171364a68380f36bcf229bc05e1e264742142344000f5646ed153a93e6590e1f3a05edd7d72b0afca327483c5f882bf1bff2f22e0d071fe9f3e644e53fb&a=w%3D850%26h%3D478%26fm%3Dwebp%26q%3D75&cd=2023-09-26T13%3A37%3A44.237Z" %}
使用 Authy 的两步登录
{% endembed %}

通常，你会得到下载恢复代码的选项。下载恢复代码对于防止你失去对两步登录令牌的访问至关重要，即使你丢失安装了 Authy 的设备。

下次登录 Reddit 时，你会被要求输入来自 Authy 的验证码来验证身份。验证码每 30 秒轮换一次，所以恶意行为者在无法访问你的物理设备的情况下，将无法获取你的代码。

{% hint style="info" %}
Authy 是 Bitwarden 推荐的验证器应用程序，因为它拥有任一个设备的验证器备份功能。即使你丢失了安装 Authy 的设备，备份也能防止你失去对两步登录令牌的访问。在 Authy 程序的  **Accounts** 界面打开 **Authenticator Backups** 开关，即可使用该功能。

其他验证器应用程序包括 [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en) 和 [FreeOTP](https://freeotp.github.io/)，从 2020 年 5 月 7 日起，Google Authenticator 包含了验证码在跨 Android 设备上的可移植性功能。
{% endhint %}

### 使用 Bitwarden 验证器 <a href="#use-bitwarden-authenticator" id="use-bitwarden-authenticator"></a>

作为 Authy 的替代方案，Bitwarden 为包括付费组织（家庭、团队或企业）成员在内的高级用户提供了一个内置的验证器。

与其他验证器应用一样，iOS 版和 Android 版的 Bitwarden 可以扫描二维码并生成 6 位数的令牌。使用 Bitwarden 验证器来保护网站的安全时，将保存一个与该登录项目一起轮换的 6 位数令牌。您也可以手动从任何 Bitwarden 应用中将您的验证码加密保存到密码库项目中。

{% embed url="https://bitwarden.com/_gatsby/image/a28bd1d4119fd42fe2e82d8e429733b3/df3d74ff52a7f409cfdddc70d8d1be60/fg-3.webp?eu=8c8a06e7e7c1af8e073af48b3b27316bb43906afa85265d73f66b0a61ea097d524f0190729c178b62d6b5388d7e547b9679370691aed868f96b818a5e367aa0000870ebc34b6710f582ec3fee6a30f4c3dcf125ff486c900a53c26d5b3e5e4774a014d23fe7bbe85b9ff3d37b48a2f36e3e5ac762186eb3bea0d410d964926a927a5c39a654fad8de55bacf8b0fc4dd29ba573540681f2632a2a0b1847e945d9c7cd773b6b771d004bccda25ce38e9b14160093c5b5755f56568d406a83d34cbe6f8f70b8b7c7de3fd9f3978d5c1a885ef49ae2269b1983aaa9c7b2459&a=w%3D850%26h%3D478%26fm%3Dwebp%26q%3D75&cd=2023-09-26T13%3A36%3A14.257Z" %}
使用 Bitwarden 的两步登录
{% endembed %}

有关设置和使用 Bitwarden 验证器的更多信息，请参阅 [Bitwarden 验证器](../your-vault/totp.md)。

### 为何要使用 Bitwarden 验证器？ <a href="#why-use-bitwarden-authenticator" id="why-use-bitwarden-authenticator"></a>

可以理解的是，一些用户对使用 Bitwarden 进行令牌认证持怀疑态度。请记住，安全往往涉及到保护和便利之间的权衡，所以最好的解决方案取决于你自己。一般来说，使用 Bitwarden 验证器有两个原因：

**1、便利性**

Bitwarden 移动应用和浏览器扩展提供自动填写验证码的功能。当您使用 Bitwarden 自动填写用户名和密码时，它会自动将验证码复制到您的剪贴板上，以方便粘贴。

如果您使用的是浏览器扩展，您可以将登录键盘快捷键（Windows：`Ctrl + Shift + L` / macOS：`Cmd + Shift + L`）和粘贴快捷键（Windows：`Ctrl + V` / macOS：`Cmd + V`）连在一起，实现快速登录。

**2、共享**

对于组织来说，使用 Bitwarden 验证器进行令牌验证的一大好处是能够在团队成员之间共享生成的令牌。这使得组织可以通过两步登录保护他们的账户，而不会牺牲多个用户访问该账户的能力，也不需要两个员工之间协调以不安全的方式共享令牌。

## 2FA 安全钥匙和通行密钥 <a href="#2fa-security-keys-and-passkeys" id="2fa-security-keys-and-passkeys"></a>

FIDO2 安全钥匙是一种流行且安全的选项，用于将 2FA 添加到您的 Bitwarden 账户。如果您不熟悉 FIDO2 安全钥匙，请[访问 FIDO 联盟网站](https://fidoalliance.org/fido2/)，了解有关 FIDO2 的更多信息。

YubiKey 设备是一种与 FIDO 身份验证协议配合使用的安全钥匙，并且可以有多种用例。两种用途是作为 2FA 安全钥匙或通行密钥。

* **2FA 安全钥匙**：使用 YubiKey 作为 2FA 安全钥匙将充当身份验证过程中的附加设备。这将伴随另一种主要的身份验证方法（例如主密码）。YubiKey 安全钥匙必须物理插入才能提供身份验证凭据。
* **通行密钥**：通行密钥是一对或公私密钥，用于验证登录。使用单一通行密钥，而不是创建用户名、密码并向账户添加 2FA。在创建通行密钥期间，YubiKey 能够作为通行密钥生成器来创建通行密钥登录所需的公钥和私钥。在[此处](https://www.yubico.com/resources/glossary/what-is-a-passkey/)了解有关使用 YubiKey 作为通行密钥的更多信息。

对于 Bitwarden，YubiKey 设备等安全钥匙的主要用途是提供 2FA 身份验证。

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经是两步登录的专家了，我们建议你：

* [设置两步登录](two-step-login-methods.md)
* [获取高级会员以使用高级两步登录方式](https://vault.bitwarden.com/#/?premium=purchase)
* [设置 Bitwarden 验证器](../your-vault/totp.md)
* [为团队和企业设置两步登录](two-step-login-methods.md#two-step-login-for-teams-and-enterprise)

# FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/authenticator-faqs/)
{% endhint %}

## 问：新的 Bitwarden Authenticator 是 Bitwarden Password Manager 的一部分吗？ <a href="#q-is-the-new-bitwarden-authenticator-part-of-bitwarden-password-manager" id="q-is-the-new-bitwarden-authenticator-part-of-bitwarden-password-manager"></a>

**答**：Bitwarden Authenticator 是一个独立的移动 App，每个人都可以使用，无论他们是否使用 Bitwarden Password Manager。Bitwarden Password Manager 将保留一个集成的验证器，供高级用户或付费组织成员使用。

## 问：我可以使用 Bitwarden Authenticator 为我的 Bitwarden 账户添加 2FA 功能吗？ <a href="#q-can-i-use-the-bitwarden-authenticator-to-add-2fa-to-my-bitwarden-account" id="q-can-i-use-the-bitwarden-authenticator-to-add-2fa-to-my-bitwarden-account"></a>

**答**：可以！因为 Bitwarden Authenticator 允许您在 Bitwarden 账户外存储代码，所以这个 App 可以用来为您的 Bitwarden 账户添加 2FA。

## 问：如何将此 App 设置为我在 iOS 上的默认验证码 App？ <a href="#q-how-do-i-set-this-app-as-my-default-verification-code-app-on-ios" id="q-how-do-i-set-this-app-as-my-default-verification-code-app-on-ios"></a>

**答**：运行 iOS 16 以上版本的 iOS 用户可以将任何应用程序设置为默认应用程序，以便在直接从相机 App 扫描验证码时存储验证码，包括 [Bitwarden Authenticator](bitwarden-authenticator.md) 和 Password Manager [集成验证](../your-vault/totp.md)。要进行设置：

1. 打开设备上的 iOS **设置** App。
2. 点击**通用**。
3. 点击**自动填充与密码**。
4. 点击**密码选项**。
5. 从**验证码**部分的**设置验证码**下拉菜单中选择一个 App。

## 问：与集成的验证器相比，我应该在什么时候使用这个独立的 App？ <a href="#q-when-should-i-use-this-standalone-app-as-opposed-to-the-integrated-authenticator" id="q-when-should-i-use-this-standalone-app-as-opposed-to-the-integrated-authenticator"></a>

**答**：除了使用独立 App 为您的 Bitwarden 账户设置 2FA 外，您还可以使用其中任何一个 App 为您的所有其他账户存储和生成验证码。它们可以一起使用，也可以单独使用，这取决于您的安全偏好。

## 问：我的数据如何存储和保护？ <a href="#q-how-is-my-data-stored-and-protected" id="q-how-is-my-data-stored-and-protected"></a>

**答**：您的验证密钥（有时称为「安全秘钥」或「TOTP 种子」）和所有相关元数据都存储在您设备上的本地数据库中。这些数据不会同步到 Bitwarden 服务器。您的数据将由您设备的云备份系统（如 iCloud 或 Google One）进行备份。要保护您的 App 中的数据，您还可以设置生物识别登录。

## 问：如何备份和恢复我的数据？ <a href="#q-how-do-i-backup-and-restore-my-data" id="q-how-do-i-backup-and-restore-my-data"></a>

**答**：您设备的云备份系统（如 iCloud 或 Google One）会对您的数据进行加密备份。要恢复数据，请恢复您设备的云备份。

## 问：如何确定我正在使用的 Bitwarden Authenticator 版本？ <a href="#q-how-do-i-determine-what-version-of-bitwarden-authenticator-im-using" id="q-how-do-i-determine-what-version-of-bitwarden-authenticator-im-using"></a>

**答**：要确定您使用的 Bitwarden Authenticator 版本，请打开「设置」选项卡然后向下滚动到「关于」部分。

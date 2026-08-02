# Bitwarden Authenticator

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-authenticator/)
{% endhint %}

Bitwarden Authenticator 是一款独立的 App，可为支持身份验证 App 双重身份验证 (2FA) 的登录生成基于时间的一次性密码 (TOTP)。它默认使用 SHA-1 算法生成 5 到 10 位数的代码，并每 30 秒轮换一次。

Bitwarden 提供[两种身份验证器](bitwarden-authenticator.md#bitwarden-authenticator-he-password-manager-ji-cheng-shen-fen-yan-zheng-qi-you-shen-me-qu-bie)：Bitwarden Authenticator App 和 Password Manager [集成的身份验证器](../password-manager/your-vault/security-tools/totp.md)。Bitwarden Authenticator 可供所有人使用，无论是否拥有 Bitwarden Password Manager 账户。如果您使用这两个 App，则可以在 Authenticator 和 Bitwarden 密码库之间[同步代码](totp-sync.md)。同步后，您的代码将标注为**本地代码**或标注为您的账户电子邮件地址：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4fMWMI0YBJQybhhyOlV0Zb/2bb912b6e9a6f38818cc37d8a0f982b4/2025-05-21_10-13-39.png?w=780&#x26;fm=avif" alt=""><figcaption><p>Bitwarden iOS Authenticator App</p></figcaption></figure></div>

## 安装 Bitwarden Authenticator <a href="#install-bitwarden-authenticator" id="install-bitwarden-authenticator"></a>

Bitwarden Authenticator 可在 iOS 和 Android 设备上使用。要开始使用，请从您的设备的 App 商店下载该 App：

* iOS：[App Store](https://apps.apple.com/us/app/bitwarden-authenticator/id6497335175) (iOS 15+)
* Android：[Google Play](https://play.google.com/store/apps/details?id=com.bitwarden.authenticator\&pli=1) (Android 9+)

{% hint style="info" %}
在 iOS 16+ 上，您可以将 [Bitwarden Authenticator](bitwarden-authenticator.md) 或 Password Manager [集成的身份验证](../password-manager/your-vault/security-tools/totp.md)设置为默认的验证码 App，以便直接从相机 App 扫描代码。要进行此设置：

1. 打开设备上的 iOS **设置** App。
2. 点击**通用**。
3. 点击**自动填充与密码**。
4. 点击**密码选项**。
5. 在**验证码**部分中，从**设置验证码**下拉菜单中选择一个 App。
{% endhint %}

## 添加代码 <a href="#add-codes" id="add-codes"></a>

您可以通过多种方式向 Authenticator 添加代码。如果您已在 Password Manager 中保存了验证码，请[同步 App](totp-sync.md#sync-codes-saved-in-your-bitwarden-vault) 以在 Authenticator 中自动显示这些代码。对于新的代码，请扫描二维码或手动输入代码密钥：

{% tabs %}
{% tab title="扫描二维码" %}
&#x20;在 Bitwarden Authenticator App 中：

1. 点击 <i class="fa-plus">:plus:</i> 添加图标。
2. 将相机对准二维码。扫描将自动进行。
3. 选择**保存在这里**（仅在 Authenticator 中）或是**保存到 Bitwarden**（保存为 Password Manager 中的登录项目）。
{% endtab %}

{% tab title="手动添加代码" %}
在 Bitwarden Authenticator App 中：

1. 点击 <i class="fa-plus">:plus:</i> 添加图标。
2. 点击屏幕底部的**手动输入密钥**。
3. 在**名称**字段中输入网站或 App 的名称。
4. 输入网站或 App 提供的**验证器密钥**。某些服务将此称为「机密密钥」或「TOTP 种子」。
5. 选择**保存在这里**（仅在 Authenticator 中）或是**保存到 Bitwarden**（保存为 Password Manager 中的登录项目）。
{% endtab %}
{% endtabs %}

{% hint style="success" icon="lightbulb" %}
如果您在 Authenticator 中创建了本地代码，稍后想要将其添加到您的密码库，请[将代码复制到 Password Manager](totp-sync.md#move-and-sync-local-codes-to-your-bitwarden-vault)。
{% endhint %}

## 编辑代码 <a href="#edit-codes" id="edit-codes"></a>

要编辑从密码库同步的代码，请[更新 Password Manager 中的登录项目](../password-manager/your-vault/vault-items/vault-items.md#manage-items)。对于仅存储在 Authenticator 中的本地代码，长按该代码然后选择**编辑**以访问以下选项：

* 编辑**名称**或**密钥**。
* 添加**用户名**。当您在同一网站拥有多个账户并且每个账户需要单独的验证码时，请使用此字段。
* 打开**收藏**，可将该代码移动到 App 主界面的顶部，方便快速访问。
* 更改用于生成代码的**算法**。Bitwarden Authenticator 默认使用 SHA-1。
* 更改代码的**刷新周期**。Bitwarden Authenticator 默认使用 30 秒。
* 更改代码的**位数**。Bitwarden Authenticator 默认使用 6 位数字。

{% hint style="success" icon="lightbulb" %}
**算法**、**刷新周期**和**位数**由您使用验证码的网站决定。除非该网站要求或允许您自定义验证码行为，否则请勿更改这些设置。
{% endhint %}

## 使用代码 <a href="#use-codes" id="use-codes"></a>

要使用验证码，请打开 Bitwarden Authenticator 然后点击某个条目以复制验证码。然后，将代码粘贴到您登录时的验证提示中。

## 将代码传输到新的移动设备 <a href="#transfer-codes-to-a-new-mobile-device" id="transfer-codes-to-a-new-mobile-device"></a>

当您获得新的移动设备时，您需要转移 TOTP，以便它们显示在 Bitwarden Authenticator 中。使用与您的设置相匹配的方法：

* 对于本地代码，在您的旧设备上[导出 Bitwarden Authenticator 数据](import-and-export.md#export-data)。在您的新设备上，[将文件导入到 Authenticator](import-and-export.md#import-data)。
* 对于旧设备上已经与 Password Manager 同步的所有代码，请在您的新设备上[设置同步](totp-sync.md)。这将提取附加到已保存的登录项目的所有验证码。或者，将位于密码库中的 TOTP [导出为 .json 文件](../password-manager/import-and-export/export-vault-data.md)，然后在您的新设备上，[将文件导入到 Authenticator](import-and-export.md#import-data)。

## FAQ <a href="#frequently-asked-questions" id="frequently-asked-questions"></a>

<details>

<summary>Bitwarden Authenticator 和 Password Manager 集成身份验证器有什么区别？</summary>

独立的 [Bitwarden Authenticator](https://bitwarden.com/download/#bitwarden-authenticator) App 和密码管理器[集成的身份验证器](../password-manager/your-vault/security-tools/totp.md)存储并生成 TOTP。根据您的安全偏好，您可以一起、独立、或在它们之间切换使用这些 App。同时使用时，请决定是保持代码连接还是单独管理。主要区别包括：

<table><thead><tr><th width="100">特性</th><th>Authenticator</th><th>密码管理器集成身份验证器</th></tr></thead><tbody><tr><td>谁可以使用它</td><td>所有人。不要求 Bitwarden 账户</td><td><p>免费版账户可以存储密钥。</p><p></p><p>高级版用户和付费版组织的成员可以存储密钥并生成 TOTP 代码。</p></td></tr><tr><td>主要用途</td><td>喜欢将 2FA 代码与密码管理器分开存储的任何人，以及想要生成 TOTP 代码的免费 Bitwarden 账户</td><td>便捷的一体化密码和 2FA 管理</td></tr><tr><td>平台</td><td>仅限移动端，iOS 和 Android</td><td>所有 Bitwarden 客户端，包括移动 App、浏览器扩展、桌面 App 和网页 App</td></tr><tr><td>默认存储</td><td><p>您的本地设备</p><p></p><p>*如果您的 <a href="totp-sync.md">Password Manager 允许身份验证器同步</a>和/或您主动<a href="totp-sync.md#move-and-sync-local-codes-to-your-bitwarden-vault">将本地代码复制到您的密码库</a>，则这些代码也会存储在您的 Bitwarden 密码库中。</p></td><td>您的 Bitwarden 密码库</td></tr><tr><td>App 之间同步</td><td>可以手动<a href="totp-sync.md#move-and-sync-local-codes-to-your-bitwarden-vault">将本地代码复制到 Password Manager</a> 以允许同步，并且可以<a href="totp-sync.md#sync-codes-saved-in-your-bitwarden-vault">自动与 Password Manager 中的代码同步</a></td><td>可以自动<a href="totp-sync.md#sync-codes-saved-in-your-bitwarden-vault">与 Authenticator 中的代码同步</a></td></tr></tbody></table>

</details>

<details>

<summary>我可以使用 Bitwarden Authenticator 将 2FA 添加到我的 Bitwarden 账户吗？</summary>

可以！因为 Bitwarden Authenticator 允许您在 Bitwarden 账户外存储代码，所以这个 App 可以用来[将 2FA 添加到您的 Bitwarden 账户](../account/two-step-login/setup-two-step-login/two-step-login-via-authenticator.md)。

如果执行此操作，请在身份验证器中将代码保存为**本地代码**，以防止其同步到您的密码库。将代码同步到其要保护的同一个密码库可能会将您锁定。

</details>

<details>

<summary>如何更改 Authenticator App 的外观？</summary>

转到**设置** → **主题**。您可以选择**浅色**模式、**深色**模式或您的设备的**默认（系统）**。

在 Android 中，您还可以打开**使用动态颜色**以使 Bitwarden 的配色方案与您的壁纸相匹配。

</details>

<details>

<summary>我的数据如何存储和保护？</summary>

您的验证密钥（有时称为「机密秘钥」或「TOTP 种子」）和所有相关元数据都存储在您设备上的本地未加密数据库中。这些数据不会同步到 Bitwarden 服务器。您的数据将由您设备的云备份系统（如 iCloud 或 Google One）进行备份。要保护您的 App 中的数据，您还可以设置生物识别登录。

</details>

<details>

<summary>如何备份和恢复我的 TOTP 数据？</summary>

您设备的云备份系统（如 iCloud 或 Google One）会对您的数据进行加密备份。要恢复数据，请恢复您设备的云备份。

您还可以[导出身份验证器数据](import-and-export.md#export-data)并将其安全地存储为备份。

</details>

<details>

<summary>我使用的是哪个版本的 Bitwarden Authenticator？</summary>

要了解您正在使用的 Bitwarden Authenticator 版本，请转到**设置**然后向下滚动到**关于**部分。

</details>

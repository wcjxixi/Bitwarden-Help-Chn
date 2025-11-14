# Bitwarden Authenticator

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-authenticator/)
{% endhint %}

Bitwarden Authenticator 是一款移动身份验证 App（在 [iOS](https://apps.apple.com/us/app/bitwarden-authenticator/id6497335175) 和 [Android](https://play.google.com/store/apps/details?id=com.bitwarden.authenticator\&pli=1) 上可用），可用于在使用双重身份验证 (2FA) 的网站和 App 上验证您的身份。Bitwarden Authenticator 生成 5-10 位基于时间的一次性密码 (TOTP)，默认使用 SHA-1 并每 30 秒轮换一次。

{% embed url="https://bitwarden.com/assets/4fMWMI0YBJQybhhyOlV0Zb/2bb912b6e9a6f38818cc37d8a0f982b4/2025-05-21_10-13-39.png?w=780&fm=avif&q=80" %}
Bitwarden iOS Authenticator App
{% endembed %}

Bitwarden Authenticator 可以用作完全独立的 App，也可以设置为[与 Bitwarden password Manager 同步](totp-sync.md)。同步后，您的代码将标注为**本地代码**或由您的账户电子邮件地址标注。

## 添加代码 <a href="#add-codes" id="add-codes"></a>

如果设置为与 Password Manager 同步，Authenticator 将自动添加并更新存储在 Password Manager 中的验证码。使用 Authenticator App，您还可以**扫描二维码**或**手动添加代码**，并选择是将其保存在本地还是保存在 Password Manager 中：

{% tabs %}
{% tab title="扫描二维码" %}
&#x20;在 Bitwarden Authenticator 中：

1. 点击 ✚图标。
2. 将相机对准二维码。扫描将自动进行。
3. 选择**保存在这里**（表示仅保存在 Authenticator 中）或是**保存到 Bitwarden**（表示保存为 Password Manager 中的登录项目）。
{% endtab %}

{% tab title="手动添加代码" %}
在 Bitwarden Authenticator 中：

1. 点击 ✚图标。
2. 点击屏幕底部的**手动输入密钥**。
3. 在**名称**字段中输入网站或 App 的名称。
4. 输入网站或 App 提供的**验证器密钥**。某些服务将此称为「机密密钥」或「TOTP 种子」。
5. 选择**保存在这里**（表示仅保存在 Authenticator 中）或是**保存到 Bitwarden**（表示保存为 Password Manager 中的登录项目）。
{% endtab %}

{% tab title="从 Password Manager 同步" %}
要从 Bitwarden Password Manager 同步 TOTP：

1. 确保您的设备上已同时安装了 Bitwarden Authenticator 和 Bitwarden Password Manager，并在 Password Manager 中登录了您要同步的账户。
2. 在 Password Manager 中，导航到**设置** → **账户安全**，然后打开**允许验证器同步**选项。
3. 在 Bitwarden Authenticator 中，确认 Password Manager 中存储的任何 TOTP 都列在您的 Bitwarden 账户标题下，而不是在**本地代码**下。

{% hint style="info" %}
身份验证器同步功能适用于 Android 版本 12 或更高版本。
{% endhint %}

{% hint style="info" %}
您可以与任意多个 Bitwarden Password Manager 账户同步，但需要为每个账户分别切换**允许验证器同步**选项。
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="success" %}
当您有新的移动设备时，您可以：

* 从 Bitwarden Authenticator 导出数据，然后将数据导入新设备。[了解方法](import-and-export.md)。
* 从 Bitwarden Password Manager 中设置同步，以提取所有已保存的登录项目中附加的验证码。[了解方法](totp-sync.md)。
{% endhint %}

### 将代码复制到 Password Manager <a href="#copy-codes-to-password-manager" id="copy-codes-to-password-manager"></a>

长按条目并点击**复制到 Bitwarden** 选项，可将本地代码从 Authenticator 复制到 Password Manager。此操作将打开 Password Manager，允许您将代码附加到现有项目或创建新项目。

## 编辑代码 <a href="#edit-codes" id="edit-codes"></a>

长按**验证码**界面的**本地代码**，或编辑 Bitwarden Password Manager 中的同步项目，以对其进行更改。对于本地代码，您可以：

* 编辑附加的**名称**或**密钥**。
* 将项目指定为**收藏**，这样它就会移动到验证码界面的顶部，以方便访问。
* 将**用户名**添加到项目中。当您在同一网站拥有多个账户并且每个账户需要单独的验证码时，请使用此字段。
* 更改用于生成代码的**算法**。Bitwarden Authenticator 默认使用 SHA-1。
* 更改代码的**刷新周期**。Bitwarden Authenticator 默认使用 30 秒。
* 更改代码的**位数**。Bitwarden Authenticator 默认使用 6 位数字。

{% hint style="success" %}
**算法**、**刷新周期**和**位数**由您使用验证码的网站决定。除非该网站要求或允许您自定义验证码行为，否则请勿更改这些设置项目。
{% endhint %}

## 使用代码 <a href="#use-codes" id="use-codes"></a>

要在该账户的机密存储在 Bitwarden Authenticator 中后使用验证码，请打开 Bitwarden Authenticator 并点击该条目以将其验证码复制到剪贴板。然后，将验证码粘贴到您要登录的网站或 App 的输入框中。

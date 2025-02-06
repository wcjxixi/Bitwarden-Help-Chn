# 集成的验证器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/integrated-authenticator/)
{% endhint %}

Password Manager 集成身份验证是 [Bitwarden Authenticator](../bitwarden-authenticator/bitwarden-authenticator.md) 等专用身份验证应用程序的替代解决方案，您可以使用它来验证使用两步登录的网站和应用程序的身份。集成身份验证使用 SHA-1 生成 6 位数的[基于时间的一次性密码](https://en.wikipedia.org/wiki/Time-based_One-time_Password_algorithm) (TOTP)，每 30 秒轮换一次。

{% hint style="info" %}
密钥存储适用于所有账户。但 TOTP 验证码的生成要求高级会员或付费组织（家庭、团队或企业）成员资格。

> **\[译者注]**：
>
> 上面这句话的意思是所有账户都可以将支持双重验证 (2FA) 的网站或服务加入验证器密钥 (TOTP) 字段，但以后要使用自动生成的 TOTP 验证码，则需要高级会员或付费组织账户。
>
> Bitwarden 的 TOTP 相当于 [Authy](https://authy.com/) 或 [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en) 等专用验证器应用程序。对于支持两步验证的网站或服务，你可以使用专用验证器应用程序生成验证码，也可以使用 Bitwarden 的 TOTP 生成验证码。
{% endhint %}

如果您不熟悉用于两步登录的 TOTP 的使用，请参阅[两步登录现场指南](../two-step-login/field-guide-for-two-step-login.md)以了解更多信息。

## 生成 TOTP 代码 <a href="#generate-totp-codes" id="generate-totp-codes"></a>

在 Bitwarden Password Manager 中，你可以使用两种方式生成 TOTP：

* 通过在 Bitwarden 移动应用或浏览器扩展中[扫描二维码](totp.md#scan-a-qr-code)
* 通过在任一个 Bitwarden 应用程序中[手动输入安全代码](totp.md#manually-enter-a-secret)

### 通过扫描 QR 码 <a href="#scan-a-qr-code" id="scan-a-qr-code"></a>

完成以下步骤，以从您选择的应用程序设置集成身份验证：

{% tabs %}
{% tab title="iOS 或 Android App" %}
1、**编辑**要为其生成 TOTP 的密码库项目。

2、点击 **📷 设置 TOTP** 按钮。

3、扫描 QR 码，然后点击**保存**以开始生成 TOTP。
{% endtab %}

{% tab title="浏览器扩展" %}
1、**编辑**要为其生成 TOTP 的密码库项目。

2、选择 **📷 TOTP** 按钮。它将从当前网页扫描验证器二维码。完整的二维码必须在屏幕上可见。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7vTPBRNX8Q1xxOZsqFxWBQ/f5e30d5811348f89d94b3a278210059c/2024-02-01_17-18-10.png?_a=BAJFJtWIB" %}
浏览器 TOTP 扫描
{% endembed %}

3、扫描 QR 码，然后点击**保存**以开始生成 TOTP。
{% endtab %}
{% endtabs %}

设置完成后，集成身份验证将持续每 30 秒轮换生成 6 位数的 TOTP，您可以将其作为两步登录连接网站或应用程序的第二步。您可以随时使用编辑项目界面上的 **📷** 图标来编辑 TOTP 种子。

### 通过手动输入安全密钥 <a href="#manually-enter-a-secret" id="manually-enter-a-secret"></a>

完成以下步骤，以从 iOS 或 Android A手pA动p输入安全密钥：

1. **编辑**要为其生成 TOTP 的密码库项目。
2. 点击 **📷 设置 TOTP** 按钮。
3. 在此界面底部点击**手动输入代码**连接。
4. 将安全密钥粘贴到**验证器密钥**字段中，然后点击**添加 TOTP**。

设置完成后，集成身份验证将持续每 30 秒轮换生成 6 位数的 TOTP，您可以将其作为两步登录连接网站或 App 的第二步。您可以随时使用编辑项目界面上的 **📷** 图标来编辑 TOTP 种子。

## 使用生成的代码 <a href="#use-generated-codes" id="use-generated-codes"></a>

{% hint style="success" %}
TOTP 依赖于基于时间的代码生成。如果您的设备与服务器相比，其时间不正确，它将生成不起作用的代码。如果您的 TOTP 代码有问题，请将设备的时间和时区设置为**自动**。
{% endhint %}

Bitwarden 浏览器扩展将自动填充您的 TOTP 代码，除非**页面加载时自动填充**选项处于活动状态。在这种情况下，浏览器扩展程序还会将 TOTP 代码复制到剪贴板，以便轻松粘贴到表单中。移动应用程序只会在自动填充后自动将 TOTP 代码复制到您设备的剪贴板。

在浏览器扩展上，您还可以从上下文菜单复制 TOTP 代码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5YmvBLK63g2xMnUewNVjOg/a63aec8b36ac65d6d91acf666fc8406f/2024-10-29_11-11-51.png?_a=DAJCwlWIZAAB" %}
浏览器扩展上下文菜单
{% endembed %}

{% hint style="success" %}
自动 TOTP 复制功能可以通过**设置** → **选项** → **自动复制 TOTP** 将其关闭，其默认为开启状态。此外，使用附近的**清除剪贴板**选项以设置清除复制的值的间隔时间。
{% endhint %}

### 查看 TOTP 代码 <a href="#viewing-totp-codes" id="viewing-totp-codes"></a>

{% hint style="success" %}
只要您能访问您的 Bitwarden 密码库，即使您在离线状态下登录 Bitwarden，也能查看生成的代码。
{% endhint %}

所有 Bitwarden App 都会在密码库项目中显示轮换的 TOTP 代码，其可以像用户名或密码一样将其复制和粘贴：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/41IqtUVMLh7MLxwwNU2ZpD/b9fc56ddc82ab78130305c0751aac0ca/2024-12-02_14-55-24.png?_a=DAJCwlWIZAAB" %}
复制 TOTP 代码
{% endembed %}

移动应用程序还有一个专用的验证码界面，其中列出了用于快速复制的活动 TOTP：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3MRb58qhCFvVHVjPaxMk6R/227fae64af8e1a13e6c86a74412929eb/2025-01-21_17-13-12.png?_a=DAJCwlWIZAAB" %}
移动端验证码界面
{% endembed %}

### 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

TOTP 代码是根据您设备的系统时钟生成的。如果您生成的代码不起作用，最可能的原因是您的设备时钟与 Bitwarden 服务器的时钟不同步。要重新同步设备上的时钟：

{% tabs %}
{% tab title="Windows" %}
导航到**开始** → **设置** → **时间和语言** → **日期和时间**，关闭然后重新打开**自动设置时间**选项。

如果这不起作用，请使用以下 PowerShell 命令设置您的时区，确保将时区名称替换为[此列表](https://learn.microsoft.com/zh-cn/windows-hardware/manufacture/desktop/default-time-zones?view=windows-11#time-zones)中正确的时区名称，然后重新启动计算机：

```bash
Set-TimeZone -Id "Central Standard Time"
```

```bash
Restart-Computer
```
{% endtab %}

{% tab title="macOS" %}
导航至**系统设置** → **常规** → **日期和时间**，关闭然后重新打开**自动设置时间和日期**以及**使用当前位置自动设置时区**选项。
{% endtab %}

{% tab title="Android" %}
导航至**设置** → **系统** → **日期和时间**，关闭然后重新打开**自动设置时间**选项。
{% endtab %}

{% tab title="iOS" %}
导航至**设置** → **常规** → **日期和时间**，关闭然后重新打开**自动设置**选项。
{% endtab %}
{% endtabs %}

## 支持的更多参数 <a href="#support-for-more-parameters" id="support-for-more-parameters"></a>

默认情况下，Bitwarden 使用 SHA-1 生成 6 位数 TOTP 代码，并且每 30 秒轮换一次，但有些网站或服务的 TOTP 代码会要求不同的参数。参数可以在 Bitwarden 中通过手动编辑您的密码库项目的 `otpauth://totp/` URI 来定制。

| 参数        | 描述              | 值                                  | 示例                 |
| --------- | --------------- | ---------------------------------- | ------------------ |
| Algorithm | 用于生成 TOTP 的加密算法 | <p>-sha1<br>-sha256<br>-sha512</p> | `algorithm=sha256` |
| Digits    | 生成的 TOTP 的位数    | 1-10                               | `digits=8`         |
| Period    | 轮换 TOTP 的秒数     | 必须 > 0                             | `period=60`        |

示例：

```
otpauth://totp/Test:me?secret=JBSWY3DPEHPK3PXP&algorithm=sha256&digits=8&period=60
```

在[此处](https://github.com/google/google-authenticator/wiki/Key-Uri-Format)了解更多有关 `otpauth://` URI 的使用的信息。

## 在 iOS 上设置为默认 <a href="#set-a-default-on-ios" id="set-a-default-on-ios"></a>

运行 iOS 16+ 的 iOS 用户可以将任何应用程序设置为直接从相机 App 扫描代码时存储验证码的默认应用程序，包括 [Bitwarden Authenticator](../bitwarden-authenticator/bitwarden-authenticator.md) 和 Password Manager [集成身份验证](totp.md)。要进行此设置：

1. 在您的设备上打开 iOS **设置** App。
2. 点击**通用**。
3. 点击**自动填充和密码**。
4. 在**验证码**部分，从**设置验证码**下拉菜单中选择 **Bitwarden**。

## Azure 和 Office 365 <a href="#azure-and-office-365" id="azure-and-office-365"></a>

默认情况下，Microsoft Azure 和 Office 365 账户需要使用 Microsoft Authenticator 用于 TOTP。如果您想使用 Bitwarden Authenticator 为您的 Microsoft Azure 或 Office 365 账户生成 TOTP，您需要完成以下步骤：

1、在 Microsoft 中，导航至您的账户设置页面。根据您的账户是个人账户还是企业账户，这可能是 `account.microsoft.com` 或 `myaccount.microsoft.com`。

2、根据您的账户是个人账户还是企业账户，打开您的**安全仪表板**或选择**安全信息**。如果您正在浏览**安全仪表板**，您还需要从该界面中选择**两步验证**。

{% embed url="https://bitwarden.com/_gatsby/image/ddb1c6fb67c45232ab67ea76f0e28aca/684599a3378fc51acd1d29f150dcb312/Screen%20Shot%202023-02-23%20at%2010.24.27%20AM.webp?eu=da8e53b0b1c1ad830b6fa5846f70333ae16b05a2fd5060856b62edfe4dfdcb8525a01a5d289c7eb6796b5dd9d0e046b367952a344bbbd7d8c9e91ff3e930f90951850ebd61b22401042d91f9e3fc04463cc54c0aa783c801a2642087b6b2e4764f501d7eac2fb8d7e4af3365e58b7c32bfe7f4786f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32bfedba78193f7b13007187cf2c9900ced67a7f1d5c144004fe67398204fe6b6096b6fca40fd87f2ee9abcc37728ec7af81ee1cfd2b70b5d044fac06e2f5062cf4bf2f814f5d26605138128e7974fdd52415a4182028b203edb3f30fd7a9aa119c4&a=w%3D850%26h%3D473%26fm%3Dwebp%26q%3D75&cd=2023-02-23T18%3A54%3A12.978Z" %}
开启 2FA
{% endembed %}

3、选择两步验证的**打开**按钮或**添加登录方式**按钮，然后从下拉列表中选择 **Authenticator 应用程序**。

4、在设置过程中，您会看到一个验证方法的下拉菜单。选择**验证器应用程序**或**应用程序**。

5、继续，直到您看到蓝色的不同的身份验证器应用程序超链接。看到超链接时选择它。

6、继续，直到您看到二维码，此时您可以按照[此处](totp.md#scan-a-qr-code)的说明进行操作。

## Steam 令牌 TOTP

> **\[译者注]**：[Steam](https://store.steampowered.com/) 游戏平台（蒸汽平台）是美国电子游戏商[威尔乌](https://www.valvesoftware.com/) (Valve) 于 2003 年 9 月 12 日推出的数字发行平台。Steam 被认为是全世界的电脑游戏界最大的数字发行平台。有关 Steam Guard（Steam 令牌）的详细信息，请参阅 [Steam 令牌](https://help.steampowered.com/zh-cn/faqs/view/06B0-26E6-2CF8-254C)。

Bitwarden Authenticator (TOTP) 可以用作 Steam 的 TOTP 生成的另一种方式，该方式使用 `steam://` 前缀后面跟随您的安全密钥。

生成的 `steam://` TOTP 默认是 5 位数的字母数字组合型，而不是传统的 6 位数字型 TOTP。

{% hint style="danger" %}
要使用这个功能，您需要使用第三方工具手动提取你的 Steam 账户的密钥。有一些工具（如 [SteamTimeIdler](https://github.com/SteamTimeIdler/stidler/wiki/Getting-your-'shared_secret'-code-for-use-with-Auto-Restarter-on-Mobile-Authentication#getting-shared-secret-from-ios-windows) 和 [Steam Desktop Authenticator](https://github.com/Jessecar96/SteamDesktopAuthenticator) 等）可以帮助您完成这个操作，但此类**提取工具不受 Bitwarden 或 Steam 官方的支持**。使用这些工具，风险自负。
{% endhint %}

# Bitwarden 验证器 (TOTP)

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/authenticator-keys/)
{% endhint %}

Bitwarden 验证器是 Authy 等专用验证应用程序的替代解决方案，您可以使用它来验证使用两步登录的网站和应用程序的身份。Bitwarden 验证器使用 SHA-1 生成 6 位数的[基于时间的一次性密码](https://en.wikipedia.org/wiki/Time-based\_One-time\_Password\_algorithm)（TOTP），每 30 秒轮换一次。

{% hint style="info" %}
验证器密钥（TOTP）存储可用于所有账户。但 TOTP 验证码的生成要求高级会员或付费组织（家庭、团队或企业）成员资格。

> \[**译者注**]：
>
> 上面这句话的意思是所有账户都可以将支持双重验证（2FA）的网站或服务加入验证器密钥（TOTP）字段，但以后要使用自动生成的 TOTP 验证码，则需要高级会员或付费组织账户。
>
> Bitwarden 的 TOTP 相当于 [Authy](https://authy.com/) 或 [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en) 等专用验证器应用程序。对于支持两步验证的网站或服务，你可以使用专用验证器应用程序生成验证码，也可以使用 Bitwarden 的 TOTP 生成验证码。
{% endhint %}

如果您不熟悉用于两步登录的 TOTP 的使用，请参阅[两步登录现场指南](../two-step-login/field-guide-for-two-step-login.md)以了解更多信息。

## 生成 TOTP 代码 <a href="#generate-totp-codes" id="generate-totp-codes"></a>

每个支持验证器 TOTP 或双因素认证（2FA）的网站处理配置的方式不一样。从你要访问的每个单独的网站或服务（例如 google.com、github.com）开始设置。

在 Bitwarden 中，你可以使用两种方式生成 TOTP：

* 通过在 Bitwarden 移动应用中[**扫描二维码**](totp.md#scan-a-qr-code)
* 通过在任一个 Bitwarden 应用程序中[**手动输入一个安全代码**](totp.md#manually-enter-a-secret)

### 通过扫描 QR 码 <a href="#scan-a-qr-code" id="scan-a-qr-code"></a>

完成以下步骤，以从 iOS 或 Android 应用程序设置 Bitwarden 验证器：

1. **编辑**要为其生成 TOTP 的密码库项目。
2. 点击 **📷 设置 TOTP** 按钮。
3. 扫描 QR 码，然后点击**保存**以开始生成 TOTP。

设置完成后，Bitwarden 验证器将持续每 30 秒轮换生成 6 位数的 TOTP，您可以将其作为两步登录连接网站或应用程序的第二步。您可以随时使用编辑项目界面上的 **📷** 图标来编辑 TOTP 种子。

### 通过手动输入安全密钥 <a href="#manually-enter-a-secret" id="manually-enter-a-secret"></a>

完成以下步骤，以从 iOS 或 Android 应用程序手动输入安全密钥：

1. **编辑**要为其生成 TOTP 的密码库项目。
2. 点击 **📷 设置 TOTP** 按钮。
3. 在此界面底部点击**手动输入代码**连接。
4. 将安全密钥粘贴到**验证器密钥**字段中，然后点击**添加 TOTP**。

从任一个 Bitwarden 应用中设置 Bitwarden 验证器，从网站或应用中复制秘钥（通常可作为二维码的替代），并将其粘贴到相应的密码库项目的**认证器密钥（TOTP）**字段中。

设置完成后，Bitwarden 验证器将持续每 30 秒轮换生成 6 位数的 TOTP，您可以将其作为两步登录连接网站或应用程序的第二步。您可以随时使用编辑项目界面上的 **📷** 图标来编辑 TOTP 种子。

## 使用生成的代码 <a href="#use-generated-codes" id="use-generated-codes"></a>

{% hint style="success" %}
TOTP 依赖于基于时间的代码生成。如果您的设备与服务器相比，其时间不正确，它将生成不起作用的代码。如果您的 TOTP 代码有问题，请将设备的时间和时区设置为**自动**。
{% endhint %}

Bitwarden 移动应用程序和浏览器扩展程序将在自动填充后自动将 TOTP 代码复制到您的设备剪贴板上，除非**启用页面加载时自动填充**选项处于活动状态。在自动填充成功后，立即从剪贴板上粘贴以使用您的 TOTP，或如果使用浏览器扩展，则使用上下文菜单：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5YmvBLK63g2xMnUewNVjOg/fbaaf6ff2987bee4623ef65952809085/be-totpcopy.png?fm=webp&h=526&q=50&w=865" %}
浏览器扩展上下文菜单
{% endembed %}

{% hint style="success" %}
自动 TOTP 复制功能可以通过**设置** → **选项** → **自动复制 TOTP** 将其关闭，其默认为开启状态。此外，使用附近的**清除剪贴板**选项以设置清除复制的值的间隔时间。
{% endhint %}

### 查看 TOTP 代码 <a href="#viewing-totp-codes" id="viewing-totp-codes"></a>

所有 Bitwarden 应用程序都会在密码库项目中显示轮换的 TOTP 代码，其可以像用户名或密码一样将其复制和粘贴：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/41IqtUVMLh7MLxwwNU2ZpD/0a50f89342c3de1fae6ac0adc2c8c8f3/totpcode.png?fm=webp&h=340&q=50&w=730" %}
复制 TOTP 代码
{% endembed %}

移动应用程序还有一个专用的验证码界面，其中列出了用于快速复制的活动 TOTP：

{% embed url="https://bitwarden.com/_gatsby/image/1597f6f1a3435f7c8dbb113ba53f7da4/f733d76482dc17b25769efd395e73745/bitwarden-ios-trio-totp.webp?eu=dd8653eee6c8f980593da3873921696de53e04fefa5334d46f66e3fc4ead9ed42df71a0721c02ee42e6e5ad882e643eb60947e331db8d48cc1e84df7ee60a30b51840ee834b32404057ac1aae2f704413e974e5fa683cc5ba03823d0edb2b2711955482bfd7aea88eca83c62badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec365f151e1a50ac75c8d3f462095f73200a7db3f45ea57e97e53a1c33260c5f55a5653ed55dad6b67c6b2a8f05adf7a7fe0adc96579d2cbb1d2b45eeb7b34b39a79b4db64391349ee4af2a13fa89624184edf7d&a=w%3D850%26h%3D654%26fm%3Dwebp%26q%3D75&cd=2022-12-09T19%3A02%3A40.330Z" %}
移动端验证码界面
{% endembed %}

## 支持的更多参数 <a href="#support-for-more-parameters" id="support-for-more-parameters"></a>

默认情况下，Bitwarden 使用 SHA-1 生成 6 位数 TOTP 代码，并且每 30 秒轮换一次，但有些网站或服务的 TOTP 代码会要求不同的参数。参数可以在 Bitwarden 中通过手动编辑你的密码库项目的 `otpauth://totp/` URI 来定制。

| 参数        | 描述              | 值                                  | 示例                 |
| --------- | --------------- | ---------------------------------- | ------------------ |
| Algorithm | 用于生成 TOTP 的密码算法 | <p>-sha1<br>-sha256<br>-sha512</p> | `algorithm=sha256` |
| Digits    | 生成的 TOTP 的位数    | 1-10                               | `digits=8`         |
| Period    | 轮换 TOTP 的秒数     | 必须 > 0                             | `period=60`        |

示例：

```
otpauth://totp/Test:me?secret=JBSWY3DPEHPK3PXP&algorithm=sha256&digits=8&period=60
```

在[此处](https://github.com/google/google-authenticator/wiki/Key-Uri-Format)了解有关 `otpauth://` URI 的使用的更多信息。

## iOS 上的 Bitwarden 验证器 <a href="#bitwarden-authenticator-on-ios" id="bitwarden-authenticator-on-ios"></a>

运行 iOS 16+ 的 iOS 用户还可以将 Bitwarden 设置为默认应用程序，用于在直接从相机应用程序扫描代码时存储验证码。要进行设置：

1. 在您的设备上打开 iOS **设置**应用程序。
2. 点击**密码**。
3. 点击**密码选项**。
4. 从**设置验证码使用：**列表中，选择 **Bitwarden**。

启用后，相机应用程序中的二维码将具有一个**在 Bitwarden 中打开**的按钮。点击时，您将能够选择是否将验证器密钥添加到新的或现有的密码库项目中。创建或编辑项目后，请确保在关闭前先保存。

{% embed url="https://bitwarden.com/_gatsby/image/807611fe56c4ea40c21ce113752cec2a/98d33f830e7906b43839217dde1793e1/Screenshot%202023-03-15%20at%2010.01.02%20AM.webp?eu=df8b01b0e7caad8e0d3aa6813e206161e53805adfa0731846f30eda81cae99d720a51e06249578b32f6d5ad987b644bf31927c661ee9d5d993b411a2ef3dab0b53d50be66deb34431168cee1afac5b143f935946f2c79e59e02e2790a6ade9255d4f1b69f629fedbedff3d39f78430319fd6f86834abe123b2722723a91073a862bfee864001eb9bb94de8b0eea80a9e99b6250e46d3a160707045165fb97fb3a4b1512339215f38668cfa0d9922cee9787363235c5c1ef76427d150943d75ace5fbbf5dd8647be3c7b84c6ec69df9&a=w%3D250%26h%3D415%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.721Z" %}
添加新的或现有的验证码
{% endembed %}

当您在 iOS 上自动填填充登录时，TOTP 代码将自动复制到您的剪贴板。将您的 TOTP 代码粘贴到验证代码字段中以完成登录。

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

> \[**译者注**]：[Steam](https://store.steampowered.com/) 游戏平台（蒸汽平台）是美国电子游戏商[威尔乌](https://www.valvesoftware.com/)（Valve）于 2003 年 9 月 12 日推出的数字发行平台。 Steam 被认为是全世界的电脑游戏界最大的数字发行平台。有关 Steam Guard（Steam 令牌）的详细信息，请参阅 [Steam Support](https://support.steampowered.com/kb\_article.php?ref=4020-ALZM-5519\&l=simplified%20chinese)。

Bitwarden 验证器（TOTP）可以用作 Steam 的 TOTP 生成的另一种方式，该方式使用 `steam://` 前缀后面跟随您的 Steam 密钥：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1Rp8AcaNWen3DklMAhF9WT/7541d630b64ec5d9f53c46127bf30624/steam-totp.png?fm=webp&h=298&q=50&w=726" %}
Steam TOTP 生成
{% endembed %}

生成的 `steam://` TOTP 默认是 5 位数的字母数字型，与传统的 6 位数字型 TOTP 不同。

{% hint style="danger" %}
要使用这个功能，你需要使用第三方工具手动提取你的 Steam 账号的密钥。如 [SteamTimeIdler](https://github.com/SteamTimeIdler/stidler/wiki/Getting-your-'shared\_secret'-code-for-use-with-Auto-Restarter-on-Mobile-Authentication#getting-shared-secret-from-ios-windows) 和 [Steam Desktop Authenticator](https://github.com/Jessecar96/SteamDesktopAuthenticator) 等工具可以帮助你完成这个功能，但是这类**提取工具不受 Bitwarden 或 Steam 官方的支持**。使用这些工具，风险自负。
{% endhint %}

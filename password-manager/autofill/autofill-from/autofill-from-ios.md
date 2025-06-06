# 从 iOS App 自动填充

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-ios/)
{% endhint %}

Bitwarden 可以自动填充您的密码和通行密钥，以便您可以无缝登录网站和 App，同时维护强大而安全的密码。自动填充功能通过检测与您登录的服务相匹配的密码库项目，以减少了您在登录过程中的复制和粘贴操作。

自动填充通行密钥（包括创建新的通行密钥时 Bitwarden 发出提示）要求 iOS 17.0 或更高版本。

{% hint style="success" %}
大多数自动填充方案都依赖登录项目的 URI 属性。如果您不熟悉 URI，请阅读 [URI 的使用](../troubleshoot-autofill/forming-uris-for-autofill.md)一文。

请注意，移动端的自动填充当前不支持自定义字段。
{% endhint %}

## 设置自动填充 <a href="#setup-auto-fill" id="setup-auto-fill"></a>

iOS 上的自动填充有几种行为：

* **键盘自动填充**：（推荐）使用此选项可以在任何 iOS App（包括网页浏览器）中通过一个键盘按钮或上滑提示来使用 Bitwarden 自动填充。
* **浏览器 App 扩展自动填充**：使用此选项仅可以在网页浏览器 App（例如 Safari）中通过分享菜单来使用 Bitwarden 自动填充。
* **长按文本字段**：使用此选项可在更多地点从 Bitwarden 自动填充。

{% hint style="success" %}
如果设备的[密码库超时行为](../../../account/log-in-and-unlock/vault-timeout-options.md#vault-timeout-action)设置为**注销**，并且您仅启用了需要 NFC（例如带 NFC 的 YubiKey）的[两步登录方式](../../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)，则当前无法在 iOS 上使用自动填充，因为 iOS 不允许 NFC 输入中断自动填充工作流。

要么将您的密码库超时行为改为**锁定**，要么启用另一种两步登录方式。
{% endhint %}

{% hint style="info" %}
如果您使用的 Argon2id 的 KDF 内存值高于 48 MB，则每次启动 iOS 自动填充或通过共享表单创建新的 Send 时，都会显示警告对话框。要避免出现此消息，请在[此处](../../../security/kdf-algorithms.md#argon2id)调整 Argon2id 设置或启用[生物识别解锁](../../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#enable-unlock-with-biometrics)。
{% endhint %}

### 键盘自动填充 <a href="#keyboard-auto-fill" id="keyboard-auto-fill"></a>

要在 iOS 上激活键盘自动填充密码，请完成以下步骤。这也将激活用于通行密钥自动填充的上滑菜单：

1、打开设备上的 iOS **⚙️设置** App 然后**通用**。

2、点击**自动填充与密码**。&#x20;

3、打开**自动填充密码和通行密钥**开关，然后从**自动填充自：**&#x5217;表中选中 **Bitwarden**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5jxVP3WslH4ppIdFq9viqX/613fbbb9eacbb14f56c0fbcee17bc9a1/2025-01-22_11-00-15.png?_a=DAJCwlWIZAAB" %}
设置 iOS 的自动填充
{% endembed %}

{% hint style="success" %}
我们强烈建议在**自动填充自：**&#x5217;表中禁用任何其他自动填充服务（例如钥匙串）。
{% endhint %}

**让我们测试一下自动填充以确保其可以正常工作：**

4、打开一个您当前未登录的 App 或网站。

5、在登录界面点击用户名或密码字段。键盘将上滑出一个匹配的登录 (`my_username`) 或 **🔑密码**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/vQG8BTWlHg2AQxBlXe4S3/63f2a5e9c32c2f38b29ec0ab0af24d57/autofill-ios.jpeg?_a=BAJFJtWIB" %}
iOS 上的自动填充
{% endembed %}

如果显示一个[匹配的登录](../troubleshoot-autofill/forming-uris-for-autofill.md)，请点击以自动填充。如果显示 **🔑密码**按钮，请点击它浏览您的密码库以搜索要使用的登录项目。如果显示 **🔑密码**按钮，可能是因为您的密码库中没有具有匹配 URI 的项目。

{% hint style="success" %}
遇到 `Biometric unlock disabled pending verification of master password`（生物识别解锁已禁用，等待验证主密码） 消息吗？了解[该怎么做](../auto-fill-faqs.md#q-what-do-i-do-about-biometric-unlock-disabled-pending-verification-of-master-password)。
{% endhint %}

### 浏览器 App 扩展自动填充 <a href="#browser-app-extension-auto-fill" id="browser-app-extension-auto-fill"></a>

要启用 iOS 上的浏览器 App 扩展自动填充：

1、打开 Bitwarden iOS  App 然后点击 **⚙️设置**。

2、点击**自动填充**。

3、在自动填充部分点击 **App 扩展**选项。&#x20;

4、点击**启用 App 扩展**按钮。&#x20;

5、从上滑出的分享菜单中，点击 **Bitwarden**。&#x20;

绿色的`扩展已激活！`消息指示已成功激活此选项。

**让我们测试一下 App 扩展以确保其可以正常工作：**

6、打开您设备的网页浏览器并导航一个您当前未登录的网站。

7、点击**分享**图标。

8、向下滚动并点击 **Bitwarden** 选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3Icxd3YqcXjBrjHVAeluwm/8be732b1ed2adebfd0a7af00f7150a97/extension.png?_a=BAJFJtWIB" %}
共享菜单中的 Bitwarden
{% endembed %}

{% hint style="info" %}
如果启用了[使用生物识别解锁](../../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)，则首次点击此选项时，系统将提示您验证您的主密码。
{% endhint %}

9、Bitwarden 界面将在您的设备上向上滑出，并列出此网站的[匹配登录项目](../troubleshoot-autofill/forming-uris-for-autofill.md)。点击该项目以自动填充。

{% hint style="success" %}
如果未列出登录项目，则可能是因为您的密码库中没有与 [URI 匹配](../troubleshoot-autofill/forming-uris-for-autofill.md)的项目。
{% endhint %}

### 长按文本字段 <a href="#long-press-a-text-field" id="long-press-a-text-field"></a>

通过长按任何文本字段，可以从 Bitwarden 自动填充数据，只要键盘自动填充选项处于激活状态：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/77glhnjH87Z6PKscElWtZy/f9229264859577c0490cf423237f8502/2025-01-22_11-05-33.png?_a=DAJCwlWIZAAB" %}
iOS 上长按文本字段
{% endembed %}

## 自动填充期间切换账户 <a href="#switch-accounts-during-autofill" id="switch-accounts-during-autofill"></a>

如果您[登录了多个账户](../../../account/log-in-and-unlock/more-log-in-options/account-switching.md)，您的移动 App 将默认尝试自动填充当前活动账户的凭据。在自动填充过程中，您可以通过轻按头像气泡从一个账户切换到另一个账户。

## 使用通行密钥 <a href="#using-passkeys" id="using-passkeys"></a>

### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

要使用下述功能，请打开 iOS **设置** App 然后导航至**密码** → **密码选项**。打开以下选项：

* 打开**自动填充密码和通行密钥**。
* 在**密码和通行密钥来源：** 列表中打开 **Bitwarden**。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，iOS App 将提示您存储此通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6rccoaRtUBbEnUjQxfSTNi/d033196df75950bae5bd7a20e8a7edd2/passkey-ios-1__1_.png?_a=BAJFJtWIB" %}
创建通行密钥
{% endembed %}

选择**继续**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**其他选项**，或者选择**其他登录选项**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

如果该服务已存在一个通行密钥，Bitwarden 将允许您通过选择 **➕** 图标以创建一个新的项目来保存新的通行密钥，或覆盖现有的通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6L5s6XBFjvaaEiDZ68m00Q/a130745c2276068fd0be066a47a34684/passkey-ios-2__1_.png?_a=BAJFJtWIB" %}
保存或覆盖通行密钥
{% endembed %}

{% hint style="info" %}
每个登录项目只能保存一个通行密钥。如果一个凭证保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的密钥，请在网站上启动通行密钥登录。移动 App 将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/b6fY5o4CBxhW4ZjDIpanR/56ffdbf1ff93b7387be273bc7df15e6b/passkey-ios-3__1_.png?_a=BAJFJtWIB" %}
使用通行密钥登录
{% endembed %}

选择**继续**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**其他选项**，或者选择**其他登录选项**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

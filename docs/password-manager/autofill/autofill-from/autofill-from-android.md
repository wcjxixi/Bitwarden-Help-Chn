# 从 Android App 自动填充

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-android/)
{% endhint %}

Bitwarden 可以自动填充您的密码和通行密钥，以便您可以无缝登录网站和 App，同时维护强大而安全的密码。自动填充功能通过检测与您登录的服务相匹配的密码库项目，以减少了您在登录过程中的复制和粘贴操作。

移动端自动填充当前不支持自定义字段和拆分登录工作流程（当用户名和密码字段显示在单独的界面上时）。

{% hint style="info" %}
在 Android 上，Password Manager 使用网站（例如 `https://gmail.com`）在网络浏览器中自动填充，以及使用包名称（例如 `com.google.android.gm`）在已安装的应用程序中自动填充。

对于已安装的应用程序，请务必**仅安装并自动填充来自受信任来源**（例如 Google Play Store 或 F-Droid）**的应用程序**，因为恶意应用程序可能会模仿知名应用程序的包名称。[了解更多](../troubleshoot-autofill/forming-uris-for-autofill.md#obtaining-uris-for-mobile-apps)。
{% endhint %}

## 设置自动填充 <a href="#set-up-autofill" id="set-up-autofill"></a>

根据您设备上所运行的 Android 版本，有几种不同的方式来启用 Bitwarden 上的自动填充功能。要设置自动填充：

1、导航至**设置** → **自动填充**。

2、点击**自动填充服务**以允许 Bitwarden 使用您保存的登录信息登录您设备上的 App。

3、当您的设备要求您提供用于密码、通行密钥和自动填充的首选服务时，请选择 **Bitwarden**。

4、返回 Bitwarden **设置** → **自动填充**界面，选择以下**显示自动填充建议**选项之一：

* **内嵌**：此选项将在键盘中建议自动填充的凭据。
* **弹出**：此选项将在输入字段的弹出窗口中建议自动填充的凭据。

5、如果您使用 Brave 或 Chrome 作为网页浏览器，请打开**使用 Brave 自动填充集成**或**使用 Chrome 自动填充集成**选项，以确保自动填充功能在这些浏览器中能正常工作。在下面了解更多。

{% hint style="info" %}
这些选项将禁用浏览器内置的自动填充功能。
{% endhint %}

6、如果您想使用快速操作磁贴，请打开**使用无障碍**。当您的设备将您带到**无障碍**菜单时，也请在该位置打开 Bitwarden。

{% hint style="success" %}
快速操作磁贴不需要在 Bitwarden 中打开**自动填充服务**，这意味着如果这是您的首选方式，您可以跳过前面的步骤，但您需要使用 **✏️**图标编辑磁贴，以将 Bitwarden 磁贴选项放置在符合您使用习惯的位置。
{% endhint %}

{% hint style="info" %}
有问题吗？请参阅我们的 [Android 自动填充故障排除](../troubleshoot-autofill/troubleshooting-android-auto-fill.md)指南。如果您仍然无法使用 Android 自动填充功能，请[联系我们](https://bitwarden.com/contact/)。
{% endhint %}

## 自动填充方式 <a href="#autofill-methods" id="autofill-methods"></a>

### 内嵌 <a href="#inline" id="inline"></a>

此方式在键盘中建议自动填充的凭据：

{% embed url="https://bitwarden.com/assets/2LxDxR7KcVd68U9UydYxat/e02408654528f4262a293de61e1439bb/2025-07-30_10-56-55.png?w=771&fm=avif" %}
Android 内嵌自动填充
{% endembed %}

如果您没有看到建议：

* 确保您使用的是 Android 11+ 和兼容的 IME (Input Method Editor)。
* 检查您使用的键盘 IME 是否支持内嵌。

### 弹出 <a href="#popup" id="popup"></a>

当设备聚焦于包含匹配登录项的输入框时，此方法会叠加显示弹出菜单。若密码库处于解锁状态，您将获得立即自动填充或打开密码库的选项：

{% embed url="https://bitwarden.com/assets/1fIoPhOLMcXzvd0Y8aw1pm/642f9f722291f2de3daf93f2fd9a6450/2025-07-30_10-59-13.png?w=705&fm=avif" %}
Android 弹出自动填充
{% endembed %}

\
您将看到两个选项。第一个（上面的我的登录项目）将使用匹配的 URI 自动填充第一个登录（上面的 `my_username`）。第二个（上面的 **Bitwarden**）将允许您从具有匹配 URI 的登录列表中进行选择。

此方法需要 Android 8+。

### 浏览器集成 <a href="#browser-integrations" id="browser-integrations"></a>

如果您使用 Brave 或 Chrome 作为网页浏览器，请打开**使用 Brave 自动填充集成**或**使用 Chrome 自动填充集成**选项，以确保自动填充功能在这些浏览器中能正常工作。此操作将引导您进入相应浏览器的设置界面，您需在此启用此选项以使用第三方服务。

这是 Chrome 所必需的，以便它能够安全地使用 Bitwarden 通过其受保护的自动填充系统自动填充密码，并且要求在 Bitwarden 中启用**自动填充服务**，并且安装的 Chrome App 版本至少为 135。这些选项将禁用浏览器内置的自动填充功能，转而使用 Bitwarden。

{% hint style="info" %}
Bitwarden 会自动检测您是否正在使用 **Edge、Opera 或 Samsung Internet**，无需为这些浏览器启用集成选项，并且会在这些浏览器中使用改进后的自动填充逻辑。

在使用 Edge、Opera 或 Samsung Internet 时，请务必仅自动填充受信任且合法的网站，因为存在一个漏洞，该漏洞可能导致凭据被自动填充到恶意网站的嵌入式或隐藏的 iframe 中。
{% endhint %}

{% embed url="https://bitwarden.com/assets/1Qm4g428OlYOBvzAxKwUNU/77106f75d8f5af42bed8bde4db9dc325/2025-07-30_13-14-04.png?w=892&fm=avif" %}
启用浏览器集成
{% endembed %}

### 快速操作磁贴 <a href="#quick-action-tiles" id="quick-action-tiles"></a>

快速操作磁贴使用 Android 无障碍服务，让您能在通知下拉设置菜单中直接访问自动填充操作。快速操作磁贴不需要在 Bitwarden 中打开**自动填充服务**，但您需要使用 **✏️**图标编辑磁贴，以将 Bitwarden 磁贴选项放置在符合您使用习惯的位置：

{% embed url="https://bitwarden.com/assets/7MHfjTUrRjdLtBoyL3Ukz2/7980adfc9de7b6b2659f1955d3d987fd/2025-07-30_11-07-51.png?w=745&fm=avif" %}
Android 快速操作磁贴
{% endembed %}

要使用快速操作磁贴，请导航至需要自动填充的页面或 App，向下滑动以访问磁贴，然后点击要使用的磁贴。

## 兼容模式 <a href="#compatibility-mode" id="compatibility-mode"></a>

启用**为浏览器自动填充使用兼容模式**选项后，将启用一种安全性较低的自动填充逻辑，该逻辑与更多浏览器兼容，尤其是 Edge、Opera 和 Samsung Internet 浏览器。

兼容模式允许 Bitwarden 从地址栏检测匹配的 URI 来进行自动填充，而不仅仅是从表单的属性（例如用户名或密码）中检测。这有助于自动填充在更广泛的场景下工作，但也会在某些浏览器中引入风险。

{% hint style="danger" %}
在某些浏览器中启用兼容模式会引入一个漏洞，该漏洞可能允许恶意网站将凭据自动填充到嵌入式或隐藏的 iframe 中：

* Chrome、Brave 和 Firefox 将始终使用标准的自动填充逻辑，无论是否启用此选项，从而确保您获得最大程度的保护。
* Edge、Opera 和 Samsung Internet 将使用安全性较低的自动填充逻辑。如果您启用此选项，请务必仅在受信任的合法网站上使用自动填充功能。
{% endhint %}

## 自动填充期间切换账户 <a href="#switch-accounts-during-autofill" id="switch-accounts-during-autofill"></a>

如果您[登录了多个账户](../../../account/log-in-and-unlock/more-log-in-options/account-switching.md)，您的移动 App 将默认尝试自动填充当前活动账户的凭据。在自动填充过程中，您可以通过轻按头像气泡从一个账户切换到另一个账户。

## 使用通行密钥 <a href="#using-passkeys" id="using-passkeys"></a>

### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

将 Bitwarden 应用程序更新到最新版本后，转到**设置** → **自动填充**然后点击**通行密钥管理**以访问 Android 设置，将 Bitwarden 配置为您的通行密钥提供程序。

请注意，Android 系统不允许 Bitwarden 等第三方通行密钥提供程序支持基于通行密钥的 2FA（又称「不可发现凭据」）；Bitwarden 存储的通行密钥只能用作主要登录凭据。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，Android 应用程序将提示您存储此通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4mBZ6s599BKxzn86CDwBhH/e2a313ab3dc263cd93f5da24e7cad778/passkey-android-1__1_.png?_a=BAJFJtWIB" %}
创建通行密钥
{% endembed %}

选择**创建**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**以另一种方式保存**，或者选择**更多已保存的登录**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

如果该服务已存在一个通行密钥，Bitwarden 将允许您通过选择 **➕** 图标以创建一个新的项目来保存新的通行密钥，或覆盖现有的通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/m8rHHqT8hmuEY7wB9WKld/573de4ef230d2d9cdbdcd94574b55168/passkey-android-2__1_.png?_a=BAJFJtWIB" %}
保存或覆盖通行密钥
{% endembed %}

{% hint style="info" %}
每个登录项目只能保存一个通行密钥。如果一个凭据保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的密钥，请在网站上启动通行密钥登录。移动 App 将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

{% embed url="https://bitwarden.com/assets/m8rHHqT8hmuEY7wB9WKld/573de4ef230d2d9cdbdcd94574b55168/passkey-android-2__1_.png?w=500&fm=avif" %}
保存或覆盖通行密钥
{% endembed %}

选择**登录**以使用您的通行密钥。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**以另一种方式保存**，或者选择**更多已保存的登录**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

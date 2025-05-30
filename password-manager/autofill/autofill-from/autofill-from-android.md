# 从 Android App 自动填充

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-android/)
{% endhint %}

Bitwarden 可以自动填充您的密码和通行密钥，以便您可以无缝登录网站和 App，同时维护强大而安全的密码。自动填充功能通过检测与您登录的服务相匹配的密码库项目，以减少了您在登录过程中的复制和粘贴操作。

{% hint style="success" %}
大多数自动填充方案都依赖登录项目的 URI 属性。如果您不熟悉 URI，请阅读 [URI 的使用](../troubleshoot-autofill/forming-uris-for-autofill.md)一文。

请注意，移动端的自动填充当前不支持自定义字段。
{% endhint %}

## 设置自动填充 <a href="#setup-auto-fill" id="setup-auto-fill"></a>

根据你设备上所运行的 Android 版本， 有几种不同的方式来启用 Bitwarden 上的自动填充功能。使用以下选项之一：

| 选项        | 要求的版本...      | 要求先启用...                               |
| --------- | ------------- | -------------------------------------- |
| 自动填充服务    | Android 8+    | -                                      |
| 内嵌自动填充    | Android 11+   | 自动填充服务，支持内嵌的 IME (Input Method Editor) |
| Draw-Over | Android 6+    | 无障碍                                    |
| 无障碍       | 所有 Android 版本 | -                                      |

### 自动填充服务 <a href="#autofill-service" id="autofill-service"></a>

当聚焦在设备上具有[匹配的登录项目](../troubleshoot-autofill/forming-uris-for-autofill.md)的输入字段时，自动填充服务（要求 Android 8+）将叠加一个弹出窗口。密码库被解锁后，系统会为您提供立即自动填充或打开密码库的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1fIoPhOLMcXzvd0Y8aw1pm/543758a75a52f952772945bf3a43a40b/Android.png?_a=DAJCwlWIZAAB" %}
Android 自动填充服务
{% endembed %}

您将看到两个选项。第一个（上图中的 **GitHub**）将使用匹配的 URI 自动填充第一个登录（上图中的 `Username`）。第二个（上图中的 **使用 Bitwarden 自动填充**）将允许您从具有匹配 URI 的登录列表中进行选择。

要启用自动填充服务：

1. 打开 Bitwarden Android App 然后点击 **⚙️设置**标签。
2. 点击**自动填充服务**选项。
3. 切换**自动填充服务**选项。您将被自动重定向到 Android 设置界面。
4. 从自动填充服务列表中，点击 **Bitwarden**。

将提示您确认信任 Bitwarden。点击**确定**将使 Bitwarden 可以阅读屏幕上的内容，以知道何时提供自动填充。从[我们的这篇博客文章](https://bitwarden.com/blog/post/the-oreo-autofill-framework)中了解更多信息。

**自动填充服务不起作用？**&#x53C2;阅[自动填充服务疑难解答](../troubleshoot-autofill/troubleshooting-android-auto-fill.md#troubleshooting-the-autofill-service)。

### 内嵌自动填充 <a href="#inline-autofill" id="inline-autofill"></a>

{% hint style="info" %}
需先启用**自动填充服务**，才能启用内嵌自动填充。
{% endhint %}

内嵌自动填充（要求 Android 11+、兼容的 IME (Input Method Editor) 并且已启用**自动填充服务**）将自动填充服务叠加层移动至键盘中：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2LxDxR7KcVd68U9UydYxat/e13bbf0b49f9a4b50b3b0d93fdd2aea8/inline.png?_a=DAJCwlWIZAAB" %}
GBoard 中的内嵌自动填充
{% endembed %}

要启用内嵌自动填充：

1. 打开 Bitwarden Android App 然后点击 **⚙️设置**标签。
2. 点击**自动填充**选项。
3. 点击**自动填充服务**选项。
4. 切换**使用内嵌自动填充**选项。

如果您的自动填充叠加层没有移至键盘中，请检查您使用的 IME 是否支持内嵌。

### 快速磁贴 (QuickTile) <a href="#quicktiles" id="quicktiles"></a>

{% hint style="info" %}
要使用快速磁贴 (QuickTile) 自动填充功能，还必须启用无障碍自动填充：

1. 打开 Bitwarden Android App，点击 **⚙️设置**选项卡。
2. 点击**自动填充**选项。
3. 点击**自动填充服务**选项。
4. 切换**使用无障碍功能**选项。您将被自动重定向到 Android 的设置界面。
5. 在服务或已下载 App 列表中，点击 **Bitwarden** 并将**使用 Bitwarden** 从关闭切换为开启。

将提示您接受允许设备上的 Bitwarden 的权限。点击**允许**将让 Bitwarden 读取屏幕上的内容，以知道何时提供自动填充。
{% endhint %}

通过快速设置面板，您可以整理应用程序，以便快速访问。 将 Bitwarden 添加到 "快速设置 "面板，以自动填充登录论坛。 要将 Bitwarden 添加到 "快速设置"，请执行以下操作

1、从屏幕顶部向下拉，访问快速设置。点击 **✏️**图标。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7MHfjTUrRjdLtBoyL3Ukz2/c737ea4deed71212ae30242bb2b217d9/2025-01-22_14-52-15.png?_a=DAJCwlWIZAAB" %}

2、滚动直至找到 Bitwarden 自动填充磁贴。按住 Bitwarden 磁贴，将其拖动到快速磁贴菜单。

3、选择一个登录论坛输入。

4、从设备顶部向下轻扫，然后点击 Bitwarden 自动填充快速磁贴。

5、您将被带到 Bitwarden App 中的自动填充页面。选择要自动填充的凭据。

{% hint style="success" %}
仍有问题吗？请参阅我们的 [Android 自动填充故障排除](../troubleshoot-autofill/troubleshooting-android-auto-fill.md)指南。如果您仍然无法使用 Android 自动填充功能，请[联系我们](https://bitwarden.com/contact/)。
{% endhint %}

### ~~无障碍~~ <a href="#accessibility" id="accessibility"></a>

~~当聚焦在设备上的输入字段时，无障碍方式将叠加一个弹出窗口，用于打开您的密码库来浏览~~[~~匹配的登录项目~~](../troubleshoot-autofill/forming-uris-for-autofill.md)~~：~~

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5M8b0oAB3G1eLNv307fWNi/bac88b0acd1815d4fec2dc9b721e596b/drawover.png?_a=BAJFJtWIB" %}
无障碍弹出窗口
{% endembed %}

~~要启用无障碍方式：~~

1. ~~打开 Bitwarden Android 应用程序并点击 **⚙️设置**标签。~~
2. ~~点击**自动填充服务**选项。~~
3. ~~切换**使用无障碍**选项。您将被自动重定向到 Android 设置界面。~~
4. ~~在服务或已下载应用程序列表中，点击 **Bitwarden** 并切换**使用 Bitwarden** 关 → 开。~~

~~将提示您接受允许设备上的 Bitwarden 权限。点击**允许**将使 Bitwarden 可以阅读屏幕上的内容，以了解何时提供自动填充。~~

{% hint style="warning" %}
~~如果您使用 Android 6+，您也可以启用 **Draw-Over**。~~

~~**无障碍不起作用？**&#x53C2;阅~~[~~无障碍服务疑难解答~~](../troubleshoot-autofill/troubleshooting-android-auto-fill.md#troubleshooting-the-accessibility-service)~~。~~
{% endhint %}

### ~~Draw-Over~~ <a href="#draw-over" id="draw-over"></a>

{% hint style="info" %}
~~需先启用**无障碍**，才能启用 Draw-Over。~~
{% endhint %}

~~当聚焦在设备上的输入字段时，Draw-Over（_要求在 Android 6+ 上使用无障碍_）将叠加一个弹出窗口，用于打开您的密码库来浏览~~[~~匹配的登录项目~~](../troubleshoot-autofill/forming-uris-for-autofill.md)~~：~~

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5M8b0oAB3G1eLNv307fWNi/bac88b0acd1815d4fec2dc9b721e596b/drawover.png?_a=BAJFJtWIB" %}
无障碍弹出窗口
{% endembed %}

~~要启用 Draw-Over 方式：~~

1. ~~打开 Bitwarden Android 应用程序并点击 **⚙️设置**标签。~~
2. ~~点击**自动填充服务**选项。~~
3. ~~切换**使用 Draw-Over** 选项。您将被自动重定向到 Android 设置界面。~~
4. ~~从列表中点击 **Bitwarden** 并切换**允许在其他应用程序上绘制**选项。~~

{% hint style="success" %}
~~**仍然有问题？**&#x8BF7;参阅我们的~~ [~~Android 自动填充疑难解答~~](../troubleshoot-autofill/troubleshooting-android-auto-fill.md)~~突破指南。~~

~~如果您仍然无法使用 Android 自动填充功能，请~~[~~联系我们~~](https://bitwarden.com/contact)~~。~~
{% endhint %}

## 自动填充期间切换账户 <a href="#switch-accounts-during-autofill" id="switch-accounts-during-autofill"></a>

如果您[登录了多个账户](../../../your-vault/account-switching.md)，您的移动 App 将默认尝试自动填充当前活动账户的凭据。在自动填充过程中，您可以通过轻按头像气泡从一个账户切换到另一个账户。

## 使用通行密钥 <a href="#using-passkeys" id="using-passkeys"></a>

### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

将 Bitwarden 应用程序更新到最新版本后，转到**设置** → **自动填充**然后点击**通行密钥管理**以访问 Android 设置，将 Bitwarden 配置为您的通行密钥提供程序。

{% hint style="danger" %}
为了将 Bitwarden 激活为您的首选通行密钥提供程序，可能需要进行以下操作：

* 对于 Chrome 用户：
  * 导航至 `chrome://flags`，然后在 **Android 凭据管理**下选择**启用第三方行密钥提供程序**。如果未显示此选项，则可能需要更新浏览器。
* 更新到最新版本后，禁用并重新启用 Bitwarden 作为自动填充提供程序。
* 更改上述设置后重新启动您的手机。
* 移除存储在 Google Password Manager 中的任何通行密钥，因为 Android 系统会优先选择该提供程序（确保不要删除任何会导致账户被锁住的重要的通行密钥）。

另请注意，Android 系统不允许 Bitwarden 等第三方通行密钥提供程序支持基于通行密钥的 2FA（又称「不可发现凭据」）；Bitwarden 存储的通行密钥只能用作主要登录凭据。

此外，虽然仅支持用于网页浏览器的通行密钥，但对 App 的支持即将在未来的版本中推出。
{% endhint %}

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

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2COiWur13OpX1QZ7Fy0tbR/65e2b4d39e2387fdcb0ba380ab52fa04/passkey-android-3__1_.png?_a=BAJFJtWIB" %}
使用通行密钥登录
{% endembed %}

选择**登录**以使用您的通行密钥登录。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**以另一种方式保存**，或者选择**更多已保存的登录**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

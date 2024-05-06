# Android 上的自动填充登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-android/)
{% endhint %}

Bitwarden 可以自动填充您的密码，以便您可以无缝登录网站和应用程序，同时维护强大而安全的密码。自动填充通过检测与您登录的服务相匹配的密码库项目，以减少您在登录过程中的复制和粘贴操作。

如果您使用[账户切换](../../../your-vault/account-switching.md)，将使用最后一个活动账户的项目来自动填充。

{% hint style="success" %}
大多数自动填充方案都依赖登录项目的 URI 属性。如果您不熟悉 URI，请阅读 [URI 的使用](../../../auto-fill/using-uris.md)一文。

请注意，移动端的自动填充当前不支持自定义字段。
{% endhint %}

## 账户切换时的自动填充 <a href="#auto-fill-while-account-switching" id="auto-fill-while-account-switching"></a>

如果您使用[账户切换](../../../your-vault/account-switching.md)，您的移动应用程序将默认尝试从当前的活动账户来自动填充凭据。在 Android 上，您可以在自动填充期间通过点击头像气泡从一个账户切换到另一个账户：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3bN7xwY4iOL4UoywSAi8Vq/58c5529af388736a1f5ace002bfba542/attempt5.gif?fm=gif&h=324&q=50&w=652" %}
Android 账户切换
{% endembed %}

## 设置自动填充 <a href="#setup-auto-fill" id="setup-auto-fill"></a>

根据你设备上所运行的 Android 版本， 有几种不同的方式启用 Bitwarden 上的自动填充：

| 选项        | 要求的版本...      | 要求先启用...                               |
| --------- | ------------- | -------------------------------------- |
| 自动填充服务    | Android 8+    | -                                      |
| 内嵌自动填充    | Android 11+   | 自动填充服务，支持内嵌的 IME (Input Method Editor) |
| Draw-Over | Android 6+    | 无障碍                                    |
| 无障碍       | 所有 Android 版本 | -                                      |

### 自动填充服务 <a href="#autofill-service" id="autofill-service"></a>

当聚焦在设备上具有[匹配的登录项目](../../../auto-fill/using-uris.md)的输入字段时，自动填充服务（要求 Android 8+）将叠加一个弹出窗口。密码库被解锁后，系统会为您提供立即自动填充或打开密码库的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1fIoPhOLMcXzvd0Y8aw1pm/7be8b29042323210b92ab7b8113fe792/only-autofill-service.png?_a=BAJFJtWIB" %}
Android 自动填充服务
{% endembed %}

您将看到两个选项。第一个（上图中的 **Twitter**）将使用匹配的 URI 自动填充第一个登录名（上图中的 `my_username`）。第二个（上图中的 **使用 Bitwarden 自动填充**）将允许您从具有匹配 URI 的登录列表中进行选择。

要启用自动填充服务：

1. 打开 Bitwarden Android 应用程序并点击 **⚙️设置**标签。
2. 点击**自动填充服务**选项。
3. 切换**自动填充服务**选项。您将被自动重定向到 Android 设置界面。
4. 从自动填充服务列表中，点击 **Bitwarden**。

将提示您确认信任 Bitwarden。点击**确定**将使 Bitwarden 可以阅读屏幕上的内容，以了解何时提供自动填充。从[我们的这篇博客文章](https://bitwarden.com/blog/post/the-oreo-autofill-framework)中了解更多信息。

**自动填充服务不起作用？**参阅[自动填充服务疑难解答](../../../auto-fill/troubleshooting-android-auto-fill.md#troubleshooting-the-autofill-service)。

### 内嵌自动填充 <a href="#inline-autofill" id="inline-autofill"></a>

{% hint style="info" %}
需先启用**自动填充服务**，才能启用内嵌自动填充。
{% endhint %}

内嵌自动填充（要求 Android 11+、兼容的 IME (Input Method Editor) 并且已启用**自动填充服务**）将自动填充服务叠加层移动至键盘中：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2LxDxR7KcVd68U9UydYxat/e13bbf0b49f9a4b50b3b0d93fdd2aea8/inline.png?fm=webp&h=281&q=50&w=378" %}
GBoard 上的内嵌自动填充
{% endembed %}

要启用内嵌自动填充：

1. 打开 Bitwarden Android 应用程序并点击 **⚙️设置**标签。
2. 点击**自动填充服务**选项。
3. 切换**使用内嵌自动填充**选项。

如果您的自动填充叠加层没有移至键盘中，请检查您使用的 IME 是否支持内嵌。

### 无障碍 <a href="#accessibility" id="accessibility"></a>

当聚焦在设备上的输入字段时，无障碍方式将叠加一个弹出窗口，用于打开您的密码库来浏览[匹配的登录项目](../../../auto-fill/using-uris.md)：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5M8b0oAB3G1eLNv307fWNi/bac88b0acd1815d4fec2dc9b721e596b/drawover.png?_a=BAJFJtWIB" %}
无障碍弹出窗口
{% endembed %}

要启用无障碍方式：

1. 打开 Bitwarden Android 应用程序并点击 **⚙️设置**标签。
2. 点击**自动填充服务**选项。
3. 切换**使用无障碍**选项。您将被自动重定向到 Android 设置界面。
4. 在服务或已下载应用程序列表中，点击 **Bitwarden** 并切换**使用 Bitwarden** 关 → 开。

将提示您接受允许设备上的 Bitwarden 权限。点击**允许**将使 Bitwarden 可以阅读屏幕上的内容，以了解何时提供自动填充。

{% hint style="warning" %}
如果您使用 Android 6+，您也可以启用 **Draw-Over**。

**无障碍不起作用？**参阅[无障碍服务疑难解答](../../../auto-fill/troubleshooting-android-auto-fill.md#troubleshooting-the-accessibility-service)。
{% endhint %}

### Draw-Over <a href="#draw-over" id="draw-over"></a>

{% hint style="info" %}
需先启用**无障碍**，才能启用 Draw-Over。
{% endhint %}

当聚焦在设备上的输入字段时，Draw-Over（_要求在 Android 6+ 上使用无障碍_）将叠加一个弹出窗口，用于打开您的密码库来浏览[匹配的登录项目](../../../auto-fill/using-uris.md)：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5M8b0oAB3G1eLNv307fWNi/bac88b0acd1815d4fec2dc9b721e596b/drawover.png?_a=BAJFJtWIB" %}
无障碍弹出窗口
{% endembed %}

要启用 Draw-Over 方式：

1. 打开 Bitwarden Android 应用程序并点击 **⚙️设置**标签。
2. 点击**自动填充服务**选项。
3. 切换**使用 Draw-Over** 选项。您将被自动重定向到 Android 设置界面。
4. 从列表中点击 **Bitwarden** 并切换**允许在其他应用程序上绘制**选项。

{% hint style="success" %}
**仍然有问题？**请参阅我们的 [Android 自动填充疑难解答](../../../auto-fill/troubleshooting-android-auto-fill.md)突破指南。

如果您仍然无法使用 Android 自动填充功能，请[联系我们](https://bitwarden.com/contact)。
{% endhint %}

## 使用通行密钥 (beta) <a href="#using-passkeys" id="using-passkeys"></a>

### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

在 Google Play 商店中打开 Bitwarden 密码管理器，然后点击**加入测试版**中的**加入**。Bitwarden 应用程序更新到 Beta 版本后，转到**设置** → **自动填充**并点击**通行密钥管理**以访问 Android 设置，将 Bitwarden 配置为您的通行密钥提供程序。

{% hint style="danger" %}
在 Android 上使用 Bitwarden 通行密钥目前处于测试阶段。要将 Bitwarden 激活为您的首选通行密钥提供程序，可能需要做以下操作：

* 在您的网络浏览器标识（例如 `chrome://flags`）中启用第三方通行密钥提供程序。
* 更新到最新版本后，禁用然后重新启用 Bitwarden 作为您的自动填充提供程序。
* 更改上述设置后重启您的手机。
* 移除 Google 密码管理器中存储的所有通行密钥，因为 Android 会优先选择此提供程序。

另请注意，Android 不允许 Bitwarden 等第三方通行密钥提供商支持基于通行密钥的 2FA（也称为「不可发现的凭据」）。

此外，虽然支持网络浏览器通行密钥，但对应用程序的支持很快就会在未来的测试版本中推出。
{% endhint %}

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或应用程序上创建新的通行密钥时，Android 应用程序将提示您存储此通行密钥：

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
每个登录项目只能保存一个通行密钥。如果一个凭证保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的密钥，请在网站上启动密钥登录。移动应用程序将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2COiWur13OpX1QZ7Fy0tbR/65e2b4d39e2387fdcb0ba380ab52fa04/passkey-android-3__1_.png?_a=BAJFJtWIB" %}
使用通行密钥登录
{% endembed %}

选择**登录**以使用您的通行密钥登录。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**以另一种方式保存**，或者选择**更多已保存的登录**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

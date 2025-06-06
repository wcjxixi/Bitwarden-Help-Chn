# 使用 PIN 码解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/unlock-with-pin/)
{% endhint %}

您可以设置 PIN 码作为解锁密码库的方法。PIN 码只能用于解锁密码库，登录时仍需使用主密码或使用设备登录，以及任何已启用的[两步登录方式](../../two-step-login/setup-guides/two-step-login-methods.md)。

使用PIN码解锁不是访问 Bitwarden 账户的无密码方法，如果您不清楚两者的区别，请参阅[理解锁与登录](unlock-with-pin.md#understanding-unlock-vs-log-in)。

{% hint style="info" %}
在 **5 次** PIN 尝试失败后，Bitwarden App 将自动注销您的账户。
{% endhint %}

## 启用 PIN 码解锁 <a href="#enable-unlock-with-pin" id="enable-unlock-with-pin"></a>

可以为 Bitwarden 浏览器扩展、移动 App 和桌面 App 启用 PIN 码解锁：

{% hint style="info" %}
使用 PIN 码会降低保护应用程序的本地密码库数据库的加密级别。如果您担心设备的本地数据会受到攻击，您可能需要重新考虑使用 PIN 码是否方便。
{% endhint %}

{% tabs %}
{% tab title="浏览器扩展" %}
要为浏览器扩展启用 PIN 码解锁：

1、打开 **⚙️设置**标签。

2、向下滚动到安全部分然后勾选**使用 PIN 码解锁**复选框。

3、在输入框中输入所需的 PIN 码。PIN 码可以是任意字符（a-z、0-9、$、# 等）的组合。

{% hint style="success" %}
如果您共享您的设备，请务必使用超过 4 位的 PIN 来创建强 PIN 或避免使用容易猜到的数字（例如出生日期）。
{% endhint %}

4、预先选中的**浏览器重启时使用主密码锁定**选项将要求您在浏览器重新启动时输入主密码而不是 PIN 码。如果您希望能够在浏览器重新启动时使用 PIN 码解锁，请取消选中此选项。

设置后，您可以通过禁用和重新启用使用 PIN 码解锁来更改您的 PIN。

当您**注销**浏览器扩展程序时，您的使用 PIN 码解锁设置将被清除，您需要重新启用使用 PIN 码解锁。
{% endtab %}

{% tab title="移动端" %}
要为移动应用程序启用 PIN 解锁：

1、打开 **⚙️设置**标签。

2、向下滚动到安全部分然后点击**使用 PIN 码解锁**选项。

3、在输入框中输入所需的 PIN 码。PIN 码可以是任意数字 (0-9) 的组合。

{% hint style="success" %}
如果您共享您的设备，请务必使用超过 4 位的 PIN 来创建强 PIN 或避免使用容易猜到的数字（例如出生日期）。
{% endhint %}

4、将出现一个询问您是否当应用程序重新启动时要求使用主密码解锁的对话框。点击**是**，要求您在应用程序重启后使用主密码而不是 PIN 码。点击**否**，在应用程序重启后使用 PIN 码解锁。

设置后，您可以通过禁用和重新启用使用 PIN 码解锁来更改您的 PIN。

当您**注销**移动应用程序时，您的使用 PIN 码解锁设置将被清除，您需要重新启用使用 PIN 码解锁。
{% endtab %}

{% tab title="桌面端" %}
使用 PIN 码解锁是为登录到桌面应用程序的每一个账户单独设置的。要启用使用 PIN 码解锁：

1、打开您的**设置**（WIndows 上为**文件** → **设置**，macOS 上为 **Bitwarden** → **偏好设置**）。

2、向下滚动到安全部分然后勾选**使用 PIN 码解锁**复选框。

3、在输入框中输入所需的 PIN 码。PIN 码可以是任意字符（a-z、0-9、$、＃ 等）的组合。

{% hint style="success" %}
如果您共享您的设备，请务必使用超过 4 位的 PIN 来创建强 PIN 或避免使用容易猜到的数字（例如出生日期）。
{% endhint %}

4、预先选中的**重启时使用主密码锁定**选项将要求您在应用程序重新启动时输入主密码而不是 PIN 码。如果您希望能够在应用程序重新启动时使用 PIN 码解锁，请取消选中此选项。

设置后，您可以通过禁用和重新启用使用 PIN 码解锁来更改您的 PIN。

当您**注销**桌面应用程序时，您的使用 PIN 码解锁设置将被清除，您需要重新启用使用 PIN 码解锁。
{% endtab %}
{% endtabs %}

{% hint style="info" %}
当如果您关闭了**重启时使用主密码锁定**选项，Bitwarden 应用程序在进入锁定状态时可能无法完全清除应用程序内存中的敏感数据。如果您担心设备的本地内存受到盗用，您应该保持**重启时使用主密码锁定**选项处于打开状态。
{% endhint %}

## 理解解锁与登录 <a href="#understanding-unlock-vs-log-in" id="understanding-unlock-vs-log-in"></a>

要理解为什么解锁和登录是不一样的，首先要记住 Bitwarden 在服务器上[从不存储任何未经加密的数据](../../../security/data/encrypted-data.md)，这一点很重要。**当您的密码库既未解锁也未登录时**，您的密码库数据只以[加密形式](../../../security/encryption/encryption-protocols.md)存在于服务器上。

### 登录 <a href="#logging-in" id="logging-in"></a>

**登录** Bitwarden 可以获取已加密的密码库数据，并在本地设备上解密。在实践中，这意味着两件事：

1、登录时始终需要使用主密码或[使用设备登录](../more-log-in-options/log-in-with-device.md)，以获取解密密码库数据所需的[账户加密密钥](../../../security/encryption/encryption-key-rotation.md)。

在此阶段也需要使用[任何已启用的两步登录方式](../../two-step-login/setup-guides/two-step-login-methods.md)。

2.、登录时始终需要连接到互联网（或者，如果是自托管，则需要连接到服务器），以便将加密的密码库下载到磁盘，随后在设备内存中进行解密。

### 解锁 <a href="#unlocking" id="unlocking"></a>

只有在已登录的情况下才能**解锁**。 这就意味着，根据上述章节，您的设备在磁盘上存储了**已加密**的密码库数据。在实践中，这意味着两件事：

1、您不需要您的主密码。虽然主密码可以用来解锁密码库，但 PIN 码和生物识别等其他方法也可以用来解锁密码库。

{% hint style="info" %}
当您设置 PIN 码或生物识别时，从 PIN 码或生物识别因素中派生的新加密密钥将用于加密[账户加密密钥](../../../security/encryption/encryption-key-rotation.md)，您登录后即可访问该密钥，并将其存储在磁盘<mark style="color:red;">ª</mark>。

**解锁**密码库会使用 PIN 码或生物识别密钥解密内存中的账户加密密钥。解密后的账户加密密钥将用于解密内存中的所有密码库数据。

**锁定**密码库会导致删除所有已解密的密码库数据，包括已解密的账户加密密钥。

ª - 如果使用**重启时使用主密码锁定**选项，此密钥只会存储在内存中，而不会存储在磁盘上。
{% endhint %}

2、您不需要连接到互联网（或者，如果是自托管，则不需要连接到服务器）。

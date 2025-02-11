# 使用生物识别解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/biometrics/)
{% endhint %}

Bitwarden 可以被配置为接受生物识别的的方式来解锁您的密码库。

生物识别**只能用于解锁**您的密码库，**登录**时您仍然会被要求使用您的主密码或使用设备登录，以及任何已启用的[两步登录方式](../two-step-login/two-step-login-methods.md)。如果您不清楚两者的区别，请向参阅[理解解锁与登录](unlock-with-pin.md#understanding-unlock-vs-log-in)。

{% hint style="success" %}
生物识别功能是设备和/或操作系统内置安全性的一部分。Bitwarden 利用本地 API 来执行这种验证，因此 **Bitwarden 不会从设备上接收任何生物识别信息**。
{% endhint %}

## 启用生物识别解锁 <a href="#enable-unlock-with-biometrics" id="enable-unlock-with-biometrics"></a>

可以在移动端、桌面端和浏览器扩展上为 Bitwarden 启用使用生物识别解锁：

{% tabs %}
{% tab title="移动端" %}
### 在移动端启用 <a href="#enable-for-mobile" id="enable-for-mobile"></a>

生物识别解锁支持 Android（Google Play 或 FDroid）上的[指纹解锁](https://support.google.com/nexus/answer/6285273?hl=zh-Hans)或[面部解锁](https://support.google.com/pixelphone/answer/9517039?hl=zh-Hans)，iOS 上的[触控 ID](https://support.apple.com/zh-cn/HT201371) 和[面容 ID](https://support.apple.com/zh-cn/HT208109)。

要为您的移动设备启用生物识别解锁：

1、在设备的原生设置（例如 iOS **⚙️设置** App）中，确保您的生物识别方式已打开。

2、在 Bitwarden App 中，打开 **⚙️设置**选项卡。

3、打开账户安全部分，然后点击您想要启用的生物识别选项。此界面上可用的内容取决于您的设备的硬件功能以及已启用的功能（**步骤 1**），例如：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7FDRtrf7LkC22dzf3ErsR4/3c176fd1ddb2a3d188817d7e1f795adf/2025-01-21_15-16-44.png?_a=DAJCwlWIZAAB" %}
移动端生物识别解锁
{% endembed %}

点击该选项将提示输入您的生物识别信息（例如面部或指纹）。成功启用生物识别解锁后，切换按钮将被填充。

### 禁用待处理的主密码验证 <a href="#disabled-pending-master-password-verification" id="disabled-pending-master-password-verification"></a>

如果您收到一条「用于自动填充的生物识别解锁已禁用，等待验证您的主密码」消息：

1. 暂时关闭 Bitwarden 中的自动填充。
2. 在 Bitwarden 中重新启用生物识别。
3. 在 Bitwarden 中重新打开自动填充。
{% endtab %}

{% tab title="桌面端" %}
### 在桌面端启用 <a href="#enable-for-desktop" id="enable-for-desktop"></a>

生物识别解锁支持 Windows 上的 [Windows Hello](https://support.microsoft.com/zh-cn/help/4028017/windows-learn-about-windows-hello-and-set-it-up) PIN、面部识别或[其他符合 Windows Hello 生物识别要求的硬件](https://docs.microsoft.com/zh-cn/windows-hardware/design/device-experiences/windows-hello-biometric-requirements)，以及 macOS 上的[触控 ID](https://support.apple.com/zh-cn/HT207054)。

生物识别解锁是为[登录到桌面 App 的每一个账户](account-switching.md)单独设置的。要启用生物识别解锁：

1、在设备的原生设置（例如 macOS **⚙️系统首选项** App）中，确保您的生物识别方式已打开。

{% hint style="success" %}
Windows 用户可能需要安装 [Microsoft Visual C++ 可再发行软件包](https://support.microsoft.com/zh-cn/help/2977003/the-latest-supported-visual-c-downloads)，然后才能在桌面偏好设置中打开 Windows Hello。

请注意，当您第一次在机器上激活 Windows Hello 时，后台可能会出现「确保这是您」的必要提示，如果未确认，则会超时：

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4E03e08rL4VzqmOE7T5Rg2/9000a8b08ce9fd7a2e4a19656048bf3c/45f12ceb-b723-4a40-b18a-74bb2e1b0078.png?_a=DAJCwlWIZAAB" alt="Windows Hello 提示" data-size="original">
{% endhint %}

2、在 Bitwarden App 中，打开**设置**（Windows：**文件** → **设置**；macOS：**Bitwarden** → **首选项**）。

3、在安全部分，选择您想要启用的生物识别选项。此界面上可用的内容取决于您的设备的硬件功能以及已打开的功能（**步骤 1**）。在 Linux 上，这将始终是**使用系统身份验证解锁**。示例：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3bWLKsgOXmGNVTyBvoMd4/fa489a39cfb4ab0d61fca90406eb6fbf/windows.png?_a=DAJCwlWIZAAB" %}
使用 Windows Hello 解锁
{% endembed %}

4、可选。选择**应用启动时需要密码（或 PIN）**&#x6216;**应用启动时要求生物识别**选项，以设置桌面应用程序在启动时的行为方式。

{% hint style="success" %}
如果您使用的是 Windows，Bitwarden 建议使用**在启动后首次登录时需要密码（或 PIN）**，以最大限度地提高安全性。
{% endhint %}

如果您这两个选项都不使用，您只需在登录界面选择**使用生物识别解锁**按钮以提示您输入生物识别选项：

{% embed url="https://bitwarden.com/_gatsby/image/30dc27d7fd7f73f2e3d07b0a35f5e7a5/80f86093740ec4a04cfb3c5730ac376e/hello-unlock.webp?eu=dc8c03b3e7c0ff84096bf5d56e73353bb33b06a8fe0267843a30e7fe49a19c8f24f21c5124932fe42e3c5cd6dbe044bc61ce29674de6d2d2c9bf10f3bc3cff0c59db1eaa27f07a184e7299afe7a0455b3b824c09e2c09d4ce0732c81a1acb03247035a71a92cb0dcabae2a1ed3de6a678ffec17400b5e3199b120c25cc1977837bbfc58b6016e69db74eede2ecaf01cccae07e004888f6672a701d4b0bbb2aeef3ad5c2465751f467090f307943a88f6624b&a=w%3D500%26h%3D347%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A21%3A54.594Z" %}
使用 Windows Hello 解锁
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
### 关于浏览器扩展中的生物识别 <a href="#about-biometrics-in-browser-extensions" id="about-biometrics-in-browser-extensions"></a>

通过与 Bitwarden 桌面 App 的整合，生物识别解锁支持浏览器扩展。在实际操作中，这意味着：

1. **对于所有浏览器扩展**，在继续操作之前，您需要先在桌面端启用生物识别解锁。**对于除 Safari 之外的其他扩展**，Bitwarden 桌面 App 必须已登录并且已经在运行，才能在浏览器扩展中使用生物识别解锁。
2. 浏览器扩展支持与桌面相同的生物识别选项：对于 Windows，通过 [Windows Hello](https://support.microsoft.com/zh-cn/help/4028017/windows-learn-about-windows-hello-and-set-it-up) PIN、面部识别或[其他符合 Windows Hello 生物识别要求的硬件](https://docs.microsoft.com/zh-cn/windows-hardware/design/device-experiences/windows-hello-biometric-requirements)，对于 macOS， 通过[触控 ID](https://support.apple.com/zh-cn/HT207054)。

在启用整合之前，需要记住两件事，即**权限**和**可支持性**，如下文所述：

**权限**

为了促进这一整合，**除 Safari 外**的浏览器扩展将询问您以接受一个新的权限，以便 Bitwarden `communicate with cooperating native applications（与本机应用程序进行通信）`。这个权限是安全的，但也是**可选的**，它将启用生物识别技术解锁所需的集成。

拒绝此权限，您将只能使用不带生物识别解锁的普通功能的浏览器扩展。

**支持性**

生物识别解锁支持 **基于 Chromium** 的浏览器（Chrome、Edge、Opera、Brave 等）、Firefox 87+、和 Safari 14+ 上的扩展程序。生物识别解锁**当前不受支持**：

* Firefox ESR（Firefox v87+ 可以正常工作）。
* Microsoft App Store 桌面 App（从 [bitwarden.com/download](https://bitwarden.com/download) 获取的侧面加载的 Windows 桌面应用程序可以正常工作）。
* 侧面加载的 macOS 桌面 App（App Store 桌面 App 可以正常工作）。

> **\[译者注]**：**侧面加载 (side-loaded) 的大致理解**：从非官方 App Store 或从网络上下载安装的应用程序，就叫做侧面加载的应用程序。

### 在浏览器扩展上启用 <a href="#enable-for-browser-extensions" id="enable-for-browser-extensions"></a>

要为您的浏览器扩展启用生物识别解锁：

{% hint style="success" %}
在继续操作之前，必须在您的桌面应用程序中启用生物识别（Windows Hello 或触控 ID）。如果在您的桌面应用程序中没有看到 Windows Hello 选项，则可能需要安装 [Microsoft Visual C++ 可再发行软件包](https://support.microsoft.com/zh-cn/topic/%E6%9C%80%E6%96%B0%E6%94%AF%E6%8C%81%E7%9A%84-visual-c-%E4%B8%8B%E8%BD%BD-2647da03-1eea-4433-9aff-95f26a218cc0)。此外，**如果您使用的是 Safari**，则可以直接跳至**步骤 4**。

请注意，当您第一次在机器上激活 Windows Hello 时，后台可能会出现「确保这是您」的必要提示，如果未确认，则会超时：

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4E03e08rL4VzqmOE7T5Rg2/9000a8b08ce9fd7a2e4a19656048bf3c/45f12ceb-b723-4a40-b18a-74bb2e1b0078.png?_a=DAJCwlWIZAAB" alt="Windows Hello 提示" data-size="original">
{% endhint %}

1、在 Bitwarden 桌面 App 中，导航到设置（Windows：**文件** → **设置**；macOS：**Bitwarden** → 设置）。

2、向下滚动到**选项**部分并选中**启用浏览器整合**复选框。

{% hint style="info" %}
（可选）选中**要求浏览器整合验证**选项，当激活整合时，将要求唯一的指纹验证步骤。
{% endhint %}

3、在浏览器中，导航到扩展管理器（例如 `chrome://extensions` 或 `brave://extensions`），打开 Bitwarden，然后切换**允许访问文件 URL** 选项。

并不是所有的浏览器都需要开启这个，所以您可以随意跳过这一步，只有在后续的步骤不起作用的时候再回退到这一步将其开启。

4、在浏览器扩展中，打开 **⚙️设置**选项卡。

5、选择**账户安全**然后选中**使用生物识别解锁**复选框。

{% hint style="success" %}
在此阶段可能会提示您允许 Bitwarden `communicate with cooperating native applications`（与本机应用程序进行通信）。这个权限是安全的，但也是**可选的**，并且如上所述，它仅使浏览器扩展能够与桌面端通信。
{% endhint %}

桌面 App 会提示您输入生物特征数据。这样做将完成初始设置过程。如果您选择要求验证（**步骤 2**），则需要批准指纹验证检查。

6、如果您希望浏览器扩展在启动时自动提示生物识别输入，请确保启用**启动时提示生物识别**选项。

当您打开浏览器扩展程序时，它会自动提示您输入生物识别信息。如果您关闭了此提示选项（**步骤 6**），请使用解锁界面上的**使用生物识别解锁**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4jRsXEv6GdtcLfbqmaRGlP/5085abb2134c885268bebacd1bde5779/2024-10-29_09-30-49.png?_a=DAJCwlWIZAAB" %}
浏览器扩展使用生物识别解锁
{% endembed %}

{% hint style="success" %}
要使用生物识别解锁浏览器扩展，您的桌面应 App 需要已登录但无需解锁。
{% endhint %}

### 禁用待处理的主密码验证 <a href="#disabled-pending-master-password-verification" id="disabled-pending-master-password-verification"></a>

如果您收到一条「用于自动填充的生物识别解锁已禁用，等待验证您的主密码」消息：

1. 暂时关闭 Bitwarden 中的自动填充。
2. 在 Bitwarden 中重新启用生物识别。
3. 在 Bitwarden 中重新打开自动填充。
{% endtab %}
{% endtabs %}

## 理解解锁与登录 <a href="#understanding-unlock-vs-log-in" id="understanding-unlock-vs-log-in"></a>

要理解为什么解锁和登录是不一样的，首先要记住 Bitwarden 在服务器上[从不存储任何未经加密的数据](../security/vault-data.md)，这一点很重要。**当您的密码库既未解锁也未登录时**，您的密码库数据只以[加密形式](../security/encryption.md)存在于服务器上。

### 登录 <a href="#logging-in" id="logging-in"></a>

**登录** Bitwarden 可以获取已加密的密码库数据，并在本地设备上解密。在实践中，这意味着两件事：

1、登录时始终需要使用主密码或[使用设备登录](log-in-with-device.md)，以获取解密密码库数据所需的[账户加密密钥](../security/account-encryption-key.md)。

在此阶段也需要使用[任何已启用的两步登录方式](../two-step-login/two-step-login-methods.md)。

2.、登录时始终需要连接到互联网（或者，如果是自托管，则需要连接到服务器），以便将加密的密码库下载到磁盘，随后在设备内存中进行解密。

### 解锁 <a href="#unlocking" id="unlocking"></a>

只有在已登录的情况下才能**解锁**。 这就意味着，根据上述章节，您的设备在磁盘上存储了**已加密**的密码库数据。在实践中，这意味着两件事：

1、您不需要您的主密码。虽然主密码可以用来解锁密码库，但 PIN 码和生物识别等其他方法也可以用来解锁密码库。

{% hint style="info" %}
当您设置 PIN 码或生物识别时，从 PIN 码或生物识别因素中派生的新加密密钥将用于加密[账户加密密钥](../security/account-encryption-key.md)，您登录后即可访问该密钥，并将其存储在磁盘<mark style="color:red;">ª</mark>。

**解锁**密码库会使用 PIN 码或生物识别密钥解密内存中的账户加密密钥。解密后的账户加密密钥将用于解密内存中的所有密码库数据。

**锁定**密码库会导致删除所有已解密的密码库数据，包括已解密的账户加密密钥。

ª - 如果使用**重启时使用主密码锁定**选项，此密钥只会存储在内存中，而不会存储在磁盘上。
{% endhint %}

2、您不需要连接到互联网（或者，如果是自托管，则不需要连接到服务器）。

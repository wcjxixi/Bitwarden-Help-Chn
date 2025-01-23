# 使用生物识别解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/biometrics/)
{% endhint %}

Bitwarden 可以被配置为接受生物识别的的方式来解锁您的密码库。

生物识别**只能用于解锁**您的密码库，**登录**时您仍然会被要求使用您的主密码和任何已启用的[两步登录方式](../two-step-login/two-step-login-methods.md)。如果不确定两者之间的区别，请向下滚动至[理解解锁与登录](unlock-with-pin.md#understanding-unlock-vs-log-in)。

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

1、在设备的原生设置（例如 iOS **⚙️设置**应用程序）中，确保您的生物识别方式已打开。

2、在 Bitwarden 应用程序中，打开 **⚙️设置**选项卡。

3、向下滚动到**安全**部分，然后点击您想要启用的生物识别选项。此界面上可用的内容取决于您的设备的硬件功能以及已启用的功能（**步骤 1**），例如：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7FDRtrf7LkC22dzf3ErsR4/6de09c0d80e81012000b1f4e8a6573d8/ios_faceid.jpeg?fm=webp&h=490&q=50&w=500" %}
在 iOS 中启用面容 ID
{% endembed %}

点击该选项将提示输入您的生物识别信息（即面部或指纹）。成功启用生物识别解锁后将显示绿色的`已启用`状态指示器（如图所示）。

### 禁用待处理的主密码验证 <a href="#disabled-pending-master-password-verification" id="disabled-pending-master-password-verification"></a>

如果您收到一条「用于自动填充的生物识别解锁已禁用，等待验证您的主密码」消息：

1. 暂时关闭 Bitwarden 中的自动填充。
2. 在 Bitwarden 中重新启用生物识别。
3. 在 Bitwarden 中重新打开自动填充。
{% endtab %}

{% tab title="桌面端" %}
### 在桌面端启用 <a href="#enable-for-desktop" id="enable-for-desktop"></a>

生物识别解锁支持 Windows 上的 [Windows Hello](https://support.microsoft.com/zh-cn/help/4028017/windows-learn-about-windows-hello-and-set-it-up) PIN、面部识别或[其他符合 Windows Hello 生物识别要求的硬件](https://docs.microsoft.com/zh-cn/windows-hardware/design/device-experiences/windows-hello-biometric-requirements)，以及 macOS 上的[触控 ID](https://support.apple.com/zh-cn/HT207054)。

生物识别解锁是为登录到桌面应用程序的每一个账户单独设置的。要启用生物识别解锁：

1、在设备的原生设置（例如 macOS **⚙️系统首选项**应用程序）中，确保您的生物识别方式已打开。

{% hint style="success" %}
Windows 用户可能需要安装 [Microsoft Visual C++ 可再发行软件包](https://support.microsoft.com/zh-cn/help/2977003/the-latest-supported-visual-c-downloads)，然后才能在桌面偏好设置中打开 Windows Hello。
{% endhint %}

2、在 Bitwarden 应用程序中，打开**设置**（Windows：**文件** → **设置**；macOS：**Bitwarden** → **首选项**）。

3、在**安全**部分，选择您想要启用的生物识别选项。此界面上可用的内容取决于您的设备的硬件功能以及已打开的功能（**步骤 1**），例如：

{% embed url="https://bitwarden.com/_gatsby/image/91ce97e4d6323abcab3193e6d8e7fa50/8696fca6dea8cee9b9af15af980cdf3c/windows.webp?eu=dbdc59e6b29ca9d30e6ba8823e21683fb26954f9a85636d13567b2aa4cf99b8526a6115327c179e02c6b5ddd87b443e831c32d611db8d08ec5ea18fce866fe0d508a5ce634e6750e022291f9e6a1551369cf1e5da7d2cf5aa2692086b0e1b2711d021b2caf7cbc84e6f17120f0c0252df5effb7f3297e866b3560805885b24b827a5ce8b7701e98cee4ca9bcefff0190dbe0320412bc8f4e61203377059a53ddc1fb76376654145f2a98fe5ccf68c7b5354f37715a0e51f7333cd103a83d38c3e0fba7088b7c2db3fed67629d897f1c7ae04ec7421&a=w%3D500%26h%3D315%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A21%3A55.603Z" %}
使用 Windows Hello 解锁
{% endembed %}

4、可选。选择**应用启动时需要密码（或 PIN）**&#x6216;**应用启动时要求生物识别**选项，以设置桌面应用程序在启动时的行为方式。

{% hint style="success" %}
如果您使用的是 Windows，Bitwarden 建议使用**在启动后首次登录时需要密码（或 PIN）**，以最大限度地提高安全性。后，桌面应用程序将自动提示您使用生物识别来解锁您的密码库。您可以从同一菜单中使用**不提示...**&#x9009;项来关闭自动提示：
{% endhint %}

如果您这两个选项都不适使用，您只需在登录界面选择**使用生物识别解锁**按钮以提示您输入生物识别选项：

{% embed url="https://bitwarden.com/_gatsby/image/30dc27d7fd7f73f2e3d07b0a35f5e7a5/80f86093740ec4a04cfb3c5730ac376e/hello-unlock.webp?eu=dc8c03b3e7c0ff84096bf5d56e73353bb33b06a8fe0267843a30e7fe49a19c8f24f21c5124932fe42e3c5cd6dbe044bc61ce29674de6d2d2c9bf10f3bc3cff0c59db1eaa27f07a184e7299afe7a0455b3b824c09e2c09d4ce0732c81a1acb03247035a71a92cb0dcabae2a1ed3de6a678ffec17400b5e3199b120c25cc1977837bbfc58b6016e69db74eede2ecaf01cccae07e004888f6672a701d4b0bbb2aeef3ad5c2465751f467090f307943a88f6624b&a=w%3D500%26h%3D347%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A21%3A54.594Z" %}
使用 Windows Hello 解锁
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
### 关于浏览器扩展中的生物识别 <a href="#about-biometrics-in-browser-extensions" id="about-biometrics-in-browser-extensions"></a>

通过与 Bitwarden 桌面应用程序的整合，生物识别解锁支持浏览器扩展。在实际操作中，这意味着：

1. **对于所有浏览器扩展**，在继续操作之前，您需要先在桌面端启用生物识别解锁。**对于除 Safari 之外的其他扩展**，Bitwarden 桌面应用程序必须已登录并且已经在运行，才能在浏览器扩展中使用生物识别解锁。
2. 浏览器扩展支持与桌面相同的生物识别选项：对于 Windows，通过 [Windows Hello](https://support.microsoft.com/zh-cn/help/4028017/windows-learn-about-windows-hello-and-set-it-up) PIN、面部识别或[其他符合 Windows Hello 生物识别要求的硬件](https://docs.microsoft.com/zh-cn/windows-hardware/design/device-experiences/windows-hello-biometric-requirements)，对于 macOS， 通过[触控 ID](https://support.apple.com/zh-cn/HT207054)。

在启用整合之前，需要记住两件事，即**权限**和**可支持性**，如下文所述：

**权限**

为了促进这一整合，**除 Safari 外**的浏览器扩展将询问您以接受一个新的权限，以便 Bitwarden `communicate with cooperating native applications（与本机应用程序进行通信）`。这个权限是安全的，但也是**可选的**，它将启用生物识别技术解锁所需的集成。

拒绝此权限，您将只能使用不带生物识别解锁的普通功能的浏览器扩展。

**支持性**

生物识别解锁支持 **基于 Chromium** 的浏览器（Chrome、Edge、Opera、Brave等）、Firefox 87+、和 Safari 14+ 上的扩展程序。生物识别解锁**当前不支持**：

* Firefox ESR（Firefox v87+ 可以正常工作）。
* Microsoft App Store 桌面应用程序（从 [bitwarden.com/download](https://bitwarden.com/download) 获取的侧面加载的 Windows 桌面应用程序可以正常工作）。
* 侧面加载的 macOS 桌面应用程序（App Store 桌面应用程序可以正常工作）。

> **\[译者注]**：**侧面加载 (side-loaded) 的大致理解**：从非官方 App Store 或从网络上下载安装的应用程序，就叫做侧面加载的应用程序。

### 在浏览器扩展上启用 <a href="#enable-for-browser-extensions" id="enable-for-browser-extensions"></a>

要为您的浏览器扩展启用生物识别解锁：

{% hint style="success" %}
在继续操作之前，必须在您的桌面应用程序中启用生物识别（Windows Hello 或触控 ID）。如果在您的桌面应用程序中没有看到 Windows Hello 选项，则可能需要安装 [Microsoft Visual C++ 可再发行软件包](https://support.microsoft.com/zh-cn/topic/%E6%9C%80%E6%96%B0%E6%94%AF%E6%8C%81%E7%9A%84-visual-c-%E4%B8%8B%E8%BD%BD-2647da03-1eea-4433-9aff-95f26a218cc0)。此外，**如果您使用的是 Safari**，则可以直接跳至**步骤 4**。
{% endhint %}

1、在 Bitwarden 桌面应用程序 中，导航到设置（Windows：**文件** → **设置**；macOS：**Bitwarden** → **首选项**）。

2、向下滚动到**选项**部分并选中**启用浏览器整合**复选框。

{% hint style="info" %}
（可选）选中**要求浏览器整合验证**选项，当激活整合时，将要求特殊的指纹验证步骤。
{% endhint %}

3、在浏览器中，导航到扩展管理器（例如 `chrome://extensions` 或 `brave://extensions`），打开 Bitwarden，然后切换**允许访问文件 URL** 选项。

并不是所有的浏览器都需要开启这个，所以您可以随意跳过这一步，只有在后续的步骤不起作用的时候再回退到这一步将其开启。

4、在浏览器扩展中，打开 **⚙️设置**选项卡。

5、向下滚动到**安全**部分并选中**使用生物识别解锁**复选框。

{% hint style="success" %}
在此阶段可能会提示您允许 Bitwarden `communicate with cooperating native applications（与本机应用程序进行通信）`。这个权限是安全的，但也是**可选的**，并且如上所述，它仅使浏览器扩展能够与桌面端通信。
{% endhint %}

桌面应用程序会提示您输入生物特征数据。这样做将完成初始设置过程。如果您选择要求验证（**步骤 2**），则需要批准指纹验证检查。

6、如果您希望浏览器扩展在启动时自动提示生物识别输入，请确保启用**启动时提示生物识别**选项。

当您打开浏览器扩展程序时，它会自动提示您输入生物识别信息。如果您打开提示选项（**步骤 6**），请使用解锁界面上的**使用生物识别解锁**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/de0a7b3e1bc571179539036da0efa0c9/005f0ea13af6c403286a9db55310df84/be-bio-unlock.webp?eu=8c8955b3e1c1f4d10c60f6d63a75363cb13a05a3ab5130823d60e2ae1eab9ed223fa485776c778b62d685cdb80b242be63cf7b6510e78289c9bc1aa5b835f90a53845beb35b073050228c4adb9f353453ac11d0df7d69d5aa63e72d2e5e7b2731d014e28fe72ba86e9ad3f3cf4c76f71e0a9b9773893fc2da30c0d109d4932bf31ffd3c06d4baad1b75db1b5a8f3089b94ba6a005fdfa957611f39595e9a79fff6ce5223787411394292cf47913497bf384d69770f0c55ff326fd406ae6f38c7e2f9f20bdd2e7ee3fdcf30269991fb9dbf43f33733b99378fad9253a505a&a=w%3D766%26h%3D555%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A21%3A55.609Z" %}
使用生物识别解锁
{% endembed %}

{% hint style="success" %}
您的桌面应用程序需要登录但无需解锁即可使用生物识别解锁浏览器扩展。
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

**登录**到 Bitwarden 检会获取已加密的密码库数据然后在您的设备上本地解密。在实践中，这意味着两件事：

1. 登录将始终要求使用您的主密码，因为您的主密码是解密密码库数据所需的密钥来源。此外，由于解密是一项需要保护的操作，因此在此阶段要求使用[任何已启用的两步登录方式](../two-step-login/two-step-login-methods.md)。
2. 登录将始终要求您连接到互联网（或者，如果您是自托管，则连接到服务器），因为您需要访问已加密的密码库才能获取它以进行本地解密。

### 解锁 <a href="#unlocking" id="unlocking"></a>

**解锁**只能在您已经登录时使用。换句话说，只有当您的密码库数据已经存储（已加密）在您的设备上时。因为您的密码库已经下载：

1. 您不需要从您的主密码中派生解密密钥，因此您可以自由地使用其他访问方式，例如 [PIN 码](unlock-with-pin.md)和[生物识别](unlocking-with-biometrics.md)。\
   如果您使用 PIN 码或生物识别，当您的密码库被锁定时，会使用从 PIN 或操作系统的生物识别子系统派生的加密密钥，将密码库数据重新加密，并安全地存储在磁盘上。这允许在您的密码库被锁定时加密存储密码库数据，而不需要您的主密码来解密它。
2. 您不需要连接到互联网（或者，如果您是自托管，则不需要连接到服务器）。

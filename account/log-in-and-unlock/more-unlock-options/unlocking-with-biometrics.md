# =使用生物识别解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/biometrics/)
{% endhint %}

使用桌面 App、浏览器扩展和移动 App 中的生物识别，可以快速安全地访问您的密码库。使用标准方式（例如[主密码](../your-master-password.md)或[受信任设备](../using-single-sign-on/add-a-trusted-device.md)）登录后，然后使用生物识别[解锁您的密码库](../understand-log-in-vs-unlock.md)。

生物识别功能是设备和/或操作系统内置安全性的一部分。Bitwarden 利用本地 API 来执行这种验证，因此 **Bitwarden 永远不会收到您的生物识别数据**。

{% hint style="info" %}
安全设置是按账户设置的。要为[多个账户](../more-log-in-options/account-switching.md)（例如个人和组织账户）启用生物识别解锁，请对每个账户重复这些步骤。
{% endhint %}

## 为桌面 App 设置生物识别 <a href="#set-up-biometrics-for-desktop-app" id="set-up-biometrics-for-desktop-app"></a>

要在桌面 App 中设置生物识别：

{% tabs %}
{% tab title="Windows" %}
生物识别解锁支持 Windows 上的 [Windows Hello](https://support.microsoft.com/zh-cn/help/4028017/windows-learn-about-windows-hello-and-set-it-up) PIN、面部识别或[其他符合 Windows Hello 生物识别要求的硬件](https://docs.microsoft.com/zh-cn/windows-hardware/design/device-experiences/windows-hello-biometric-requirements)。从 [Bitwarden 下载](https://bitwarden.com/download/#downloads-desktop)安装的 Windows 桌面 App 支持此选项。如果桌面 App 是从 Microsoft Store 安装的，则生物识别将不起作用。

要启用生物识别解锁：

1、

2、

3、

4、
{% endtab %}

{% tab title="macOS" %}

{% endtab %}

{% tab title="Linux" %}



{% endtab %}
{% endtabs %}

## 为浏览器扩展设置生物识别 <a href="#set-up-biometrics-for-browser-extension" id="set-up-biometrics-for-browser-extension"></a>

{% tabs %}
{% tab title="Chromium-based & FireFox" %}

{% endtab %}

{% tab title="Safari" %}

{% endtab %}
{% endtabs %}

## 为移动 App 设置生物识别 <a href="#set-up-biometrics-for-mobile" id="set-up-biometrics-for-mobile"></a>

生物识别解锁支持 iOS 上的[触控 ID](https://support.apple.com/zh-cn/HT201371) 和[面容 ID](https://support.apple.com/zh-cn/HT208109) 以及 Android（Google Play 或 FDroid）上的[指纹解锁](https://support.google.com/nexus/answer/6285273?hl=zh-Hans)或[面部解锁](https://support.google.com/pixelphone/answer/9517039?hl=zh-Hans)。

{% hint style="info" %}
在 Android 上，Bitwarden 要求您的生物识别因素为 [3 类](https://source.android.com/docs/security/features/biometric?hl=zh-cn)。指纹阅读器通常为 3 类，但面部识别系统的类别根据设备制造商和型号而有所不同。
{% endhint %}

要为您的移动设备设置生物识别解锁：

1、在设备的系统设置（例如 iOS 的**设置** App）中，打开生物识别方式。

2、点击 Bitwarden App 然后点击 **⚙️设置**图标。

3、点击**账户安全**。

4、点击**使用面容 ID 解锁**或**使用生物识别解锁**（可用的功能取决于您设备的硬件功能以及您之前在设备的系统设置中打开的功能）。

5、出现提示时输入您的生物识别信息，例如您的面部或指纹。成功设置生物识别解锁后，切换按钮将被填充。

## 使用生物识别解锁 <a href="#use-unlock-with-biometrics" id="use-unlock-with-biometrics"></a>

{% tabs %}
{% tab title="Windows & Linux 桌面端" %}

{% endtab %}

{% tab title="macOS 桌面端" %}

{% endtab %}

{% tab title="浏览器扩展" %}

{% endtab %}

{% tab title="移动端" %}

{% endtab %}
{% endtabs %}

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

如果出现「生物识别解锁已禁用，等待验证您的主密码」错误：

1. 暂时关闭 Bitwarden 中的自动填充功能。
2. 按照上述步骤在 Bitwarden 中设置生物识别。
3. 在 Bitwarden 中重新打开自动填充功能。

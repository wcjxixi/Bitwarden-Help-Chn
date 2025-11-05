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
要启用生物识别解锁：

1、

2、

3、

4、

5、
{% endtab %}

{% tab title="Linux" %}
要启用生物识别解锁：

1、

2、

3、
{% endtab %}
{% endtabs %}

## 为浏览器扩展设置生物识别 <a href="#set-up-biometrics-for-browser-extension" id="set-up-biometrics-for-browser-extension"></a>

{% tabs %}
{% tab title="Chromium-based & FireFox" %}
### 1) 激活集成 <a href="#id-1-activate-the-integration" id="id-1-activate-the-integration"></a>

1、

2、

3、

4、

### 2) 激活扩展生物识别 <a href="#id-2-activate-extension-biometrics" id="id-2-activate-extension-biometrics"></a>

1、

2、

3、

4、

5、

6、

7、
{% endtab %}

{% tab title="Safari" %}
要启用生物识别解锁：

1. 选择 **⚙️设置**图标。
2. 选择**账户安全**。
3. 如果出现确认窗口，请输入设备的密码并点击**始终允许**。
4. 选中**使用生物识别解锁**。
5. 出现提示时，输入您的触控 ID。
6. （可选）选中**启动时要求生物识别**，以便在浏览器扩展首次打开时使用生物识别，跳过初始解锁界面。

{% hint style="success" %}
要在每次激活桌面 App 和浏览器扩展之间的集成时要求指纹验证：

1. 打开桌面 App 并转到 **Bitwarden** → **设置**。
2. 选中**要求浏览器集成验证**。
3. 在浏览器扩展中启用生物识别解锁时，您将被要求在设置过程中输入您的指纹。
{% endhint %}
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
要使用 Windows 或 Linux 桌面 App 访问您的密码库：

1、使用主密码或 PIN 码登录。

2、选择**使用 Windows Hello 解锁**或**使用系统身份验证解锁**：

{% embed url="https://bitwarden.com/assets/7n73BtZuBKI2lrmTMGJUqk/cf42eacad0651a4cf1b12ba786a2f362/Windows_Hello.png?w=400&fm=avif" %}
使用 Windows Hello 解锁
{% endembed %}

3、输入您配置的生物识别信息。

{% hint style="info" %}
当您首次打开或重新启动 Windows 和 Linux 桌面 App 时，生物识别选项将显示为灰色。请使用标准方式（例如主密码或 PIN 码）解锁密码库。首次登录并解锁后，您可以使用生物识别来解锁您的密码库。
{% endhint %}
{% endtab %}

{% tab title="macOS 桌面端" %}
如果您在设置过程中选中了 **App 启动时要求触控 ID**，您将被立即提示输入触控 ID。

如果您在设置过程中未选中 **App 启动时要求触控 ID**：

1、使用主密码或 PIN 码登录。

2、选择**使用触控 ID 解锁**：

{% embed url="https://bitwarden.com/assets/2c5pB6gzPsvqDA46W2cODn/46c5bad230d8a5deb7f31e2861bdae0d/Unlock_with_Touch_ID.png?w=400&fm=avif" %}
使用触控 ID 解锁
{% endembed %}

3、输入您的触控 ID。
{% endtab %}

{% tab title="浏览器扩展" %}
要使用浏览器扩展访问您的密码库：

1、登录 Bitwarden 桌面 App 并解锁您的密码库。

2、保持桌面 App 仍在后台运行，打开 Bitwarden 浏览器扩展。

3、（可选）如果您之前在桌面 App 中启用了**要求浏览器集成验证**，请在出现提示时输入您的指纹。

4、取决于在桌面 App 设置期间是否中选中了**启动时要求生物识别**：

* 如果选中此设置，系统会立即提示您输入生物识别信息。
* 如果**未选中**此设置，请选择**使用生物识别解锁**然后输入您配置的生物识别信息：

{% embed url="https://bitwarden.com/assets/4UeYGO9saN15Jg3xLQmv5y/bfdb5e552b33009d219b1c1b7accd26b/Unlock_with_Biometrics_Browser.png?w=400&fm=avif" %}
浏览器使用生物识别解锁
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
当 Bitwarden 移动 App 首次打开时，请在出现提示时输入您的指纹或面容 ID。
{% endtab %}
{% endtabs %}

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

如果出现「生物识别解锁已禁用，等待验证您的主密码」错误：

1. 暂时关闭 Bitwarden 中的自动填充功能。
2. 按照上述步骤在 Bitwarden 中设置生物识别。
3. 在 Bitwarden 中重新打开自动填充功能。

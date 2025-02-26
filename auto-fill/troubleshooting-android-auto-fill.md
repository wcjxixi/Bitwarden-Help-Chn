# Android 自动填充故障排除

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-android-troubleshooting/)
{% endhint %}

根据您设备上所运行的 Android 版本，有几种不同的方式启用 Bitwarden 上的自动填充：

| 选项            | 要求的版本...       | 要求同时启用...        |
| ------------- | -------------- | ---------------- |
| 自动填充服务        | Android 8+     | -                |
| 内嵌自动填充        | Android 11+    | 自动填充服务，支持内嵌的 IME |
| ~~Draw-Over~~ | ~~Android 6+~~ | ~~无障碍~~          |
| 无障碍           | 所有 Android 版本  | -                |

有关在 Android 上设置自动填充的说明，请参阅 [Android 上的自动填充登录](../password-manager/auto-fill/auto-fill-basics/auto-fill-logins-on-android.md)。

## 自动填充服务故障排除 <a href="#troubleshooting-the-autofill-service" id="troubleshooting-the-autofill-service"></a>

如果当您的设备聚焦在用户名或密码输入字段时，Bitwarden 自动填充服务叠加层不可见，您的设备可能需要启用特定于设备的设置：

**对于华为/荣耀设备**，启用 Dropzone：

1. 打开华为/荣耀优化器 App（也称为「手机管家」）。
2. 点击底部一行中间的 **Dropzone**。
3. 向右滑动切换开关以允许使用 Dropzone。

**对于 Oppo 和其他设备**，启用浮动窗口：

1. 打开 Android 设置 App
2. 导航到**隐私/安全**。
3. 找到**浮动窗口**或**应用管理**并点击打开。
4. 向右滑动切换开关以允许浮动窗口。

## 无障碍服务故障排除 <a href="#troubleshooting-the-accessibility-service" id="troubleshooting-the-accessibility-service"></a>

使用无障碍服务遇到的最常见的问题是，**安卓电池优化**设置会自动关闭服务（如无障碍服务）以保护电池。要解决这个问题，**请关闭针对 Bitwarden 的电池优化**。

如果您持续遇到无障碍服务的问题：

1. 请再次检查您的电池优化设置。如果针对 Bitwarden 的电池优化处于开启状态，请将其关闭。
2. 如果您使用电池保护程序或任务管理器应用程序，请尝试将其禁用，看看是否会有所改变。如果有，请将 Bitwarden 添加到例外列表中。
3. 检查内置的任务管理器。你需要调出正在运行的应用程序视图，然后按住应用程序图标或向上滑动 Bitwarden 应用程序，然后选择锁定。

请注意，如果你曾经强制停止了 Bitwarden 应用程序，该服务也会停止。

{% hint style="success" %}
此网站 [https://dontkillmyapp.com/](https://dontkillmyapp.com/)，或许可以帮助您确定设备的默认电池优化配置。
{% endhint %}

## ~~Draw-Over 疑难解答~~ <a href="#troubleshooting-draw-over" id="troubleshooting-draw-over"></a>

~~Draw-Over 与 Bitwarden 自动填充功能的交互方式有所不同，具体取决于您所使用的 Android 版本。如果遇到问题，请根据下表进行检查：~~

| 版本             | 描述                                    |
| -------------- | ------------------------------------- |
| ~~Android 5~~  | ~~**不可用**，默认授予权限。~~                   |
| ~~Android 6~~  | ~~**要求**使用无障碍，因为弹出式窗口是唯一可用的选项。~~      |
| ~~Android 7+~~ | ~~**可选**。如果您只想使用自动填充快速操作磁贴而不使用弹出窗口。~~ |

{% hint style="info" %}
如果您仍然无法使用 Android 自动填充功能，请[联系我们](https://bitwarden.com/contact)。
{% endhint %}

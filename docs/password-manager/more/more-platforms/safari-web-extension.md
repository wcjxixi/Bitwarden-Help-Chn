# Safari 网页扩展

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/install-safari-app-extension/)
{% endhint %}

Bitwarden Safari 网页扩展是以前的设计用于 [Safari 14](https://developer.apple.com/documentation/safariservices/safari_web_extensions/converting_a_safari_app_extension_to_a_safari_web_extension?language=objc) 的 App 扩展的移植。Safari 网页扩展与 App Store 上的 Bitwarden 桌面 App 打包在一起。

{% hint style="info" %}
由于 Apple 的变更，Safari 现在限制 Safari 网页扩展的使用，**只能使用通过 Mac App Store 下载获取的网页扩展**。从 [2021-03-11 版本](../../../release-notes.md#2021-03-11)开始，用户将无法使用从 [bitwarden.com/download](https://bitwarden.com/download) 或任何其他非 App Store 来源的 `.dmg` 安装获取的 Bitwarden Safari 扩展。

**如果您使用的是 Safari 14 及之前的版本**，则可以继续使用 `.dmg` 安装，通过单击**更多桌面安装选项**从 [bitwarden.com/download](https://bitwarden.com/download) 下载。将 `.dmg` 保留在 Applications 文件夹之外，可以同时使用较旧的 Safari 扩展和最新的桌面 App。
{% endhint %}

Safari 网页扩展具有与以前的 App 扩展完全相同的功能。有关 Safari 网页扩展和 App 扩展之间区别的开发人员详细信息，请点击[这里](https://developer.apple.com/documentation/safariservices/safari_web_extensions/converting_a_safari_app_extension_to_a_safari_web_extension?language=objc)。

## 启用扩展 <a href="#enable-the-extension" id="enable-the-extension"></a>

启用 Safari 网页扩展之前，至少要运行一次桌面 App。在 Safari 中：

1. 打开**偏好设置**窗口。
2. 导航到**扩展**页面。
3. 选中 **Bitwarden** 复选框，然后在确认对话框中选择**开启**。

{% hint style="info" %}
这些说明适用于桌面网页浏览器的浏览器扩展，点击[此处](../../autofill/autofill-from/autofill-from-ios.md#browser-app-extension-auto-fill)了解如何为 iOS 上的移动网页浏览器设置扩展。
{% endhint %}

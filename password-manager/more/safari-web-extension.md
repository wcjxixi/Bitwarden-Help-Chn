# Safari 网页扩展

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/install-safari-app-extension/)
{% endhint %}

Bitwarden Safari 网页扩展是以前的设计用于 [Safari 14](https://developer.apple.com/documentation/safariservices/safari\_web\_extensions/converting\_a\_safari\_app\_extension\_to\_a\_safari\_web\_extension?language=objc) 的_应用程序扩展_的移植。Safari 网页扩展与 App Store 上的 Bitwarden 桌面应用程序打包在一起。

{% hint style="info" %}
由于苹果公司的更改，Safari 现在限制 Safari 网页扩展的使用，**只能使用通过 Mac App Store 下载获取的应用扩展**。从 [2021-03-11 版本](../../release-notes.md#2021-03-11)开始，用户将无法使用从 [bitwarden.com/download](https://bitwarden.com/download) 或任何其他非 App Store 来源的 `.dmg` 安装获取的 Bitwarden Safari 扩展。

**如果您使用的是 Safari 14 及之前的版本**，则可以继续使用 `.dmg` 安装，通过单击**更多桌面安装选项**从 [bitwarden.com/download](https://bitwarden.com/download) 下载。将 `.dmg` 保留在 Applications 文件夹之外，可以同时使用较旧的 Safari 扩展和最新的桌面应用程序。
{% endhint %}

Safari 网页扩展具有与以前的应用程序扩展完全相同的功能。有关 Safari 网页扩展和应用程序扩展之间区别的开发人员详细信息，请点击[这里](https://developer.apple.com/documentation/safariservices/safari\_web\_extensions/converting\_a\_safari\_app\_extension\_to\_a\_safari\_web\_extension?language=objc)。

## 启用扩展 <a href="#enable-the-extension" id="enable-the-extension"></a>

启用 Safari 网页扩展之前，至少要运行一次桌面应用程序。在 Safari 中：

1. 打开**偏好设置**窗口。
2. 导航到**扩展**页面。
3. 选中 **Bitwarden** 复选框，然后在确认对话框中选择**开启**。

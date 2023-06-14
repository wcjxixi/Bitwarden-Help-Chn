# 使用网站图标时的隐私

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/website-icons/)
{% endhint %}

_当您为存储在 Bitwarden 密码库中的网站登录信息下载图标时，Bitwarden 不会收集任何信息。_

## 使用网站图标 <a href="#using-website-icons" id="using-website-icons"></a>

当 Bitwarden 在您的密码库中显示一个带有关联网站（参阅 [URI 的使用](../auto-fill/using-uris.md)）的[登录项目](../your-vault/vault-items.md)时，它会尝试为其附带一个图形图标。网站图标可帮助您使用可识别的图标轻松识别密码库中的特定登录项目，其通常由该网站的徽标或品牌形象表示。

### 关于图标服务器 <a href="#about-the-icon-server" id="about-the-icon-server"></a>

Bitwarden 图标服务器为这些网站图标提供传递端点。如果您在设备上使用网站图标，则 Bitwarden 将为您的密码库中具有的 URI 类似于网站（例如 `google.com` 或 `https://google.com`，但不是 `google` 或 `http://localhost`）的类型为「登录」的每个项目，向 `icons.bitwarden.net` 发出请求。

图标服务器前面有一个 CDN，该 CDN 在世界各地的 Cloudflare 边缘节点上缓存图标。对同一图标的后续请求可能会命中 CDN 缓存，而不是直接命中图标服务器。如果在其密码库中具有相同网站的另一个 Bitwarden 用户在您之前请求了该图标，则您的请求可能实际上不会命中 Bitwarden 的图标服务器。

{% hint style="info" %}
如果您是自托管 Bitwarden，图标不会缓存到 CDN。所有请求将始终直接命中您的图标容器。
{% endhint %}

### 隐私问题 <a href="#privacy-considerations" id="privacy-considerations"></a>

因为对图标图像的请求包含存储在您的密码库中的网站的主机名，所以此功能将可能「泄漏」原本受密码保护的信息到 Bitwarden 服务器和/或 CDN 端点，了解这一点很重要。图标请求的示例如下所示：

`https://icons.bitwarden.net/google.com/icon.png`

**图标服务器端点不会记录或收集有关图标图像请求的任何信息。**但是，您必须牢记这一点，因为除了审查我们的[开源代码库](https://github.com/bitwarden)之外，我们没有其他方式可以公开证明这一点。

## 禁用网站图标 <a href="#disabling-website-icons" id="disabling-website-icons"></a>

我们了解某些具有隐私意识的用户可能不希望使用网站图标功能。我们提供了在所有 Bitwarden 客户端应用程序上禁用网站图标的选项：

* **网页密码库：**设置 → 选项 → 显示网站图标
* **浏览器扩展：**设置 → 选项 → 显示网站图标
* **移动应用程序：**设置 → 选项 → 显示网站图标
* **桌面应用程序：**设置 → 选项 → 显示网站图标

禁用网站图标功能后，Bitwarden 会选择为您显示一个通用的本地访问图标（<img src="../.gitbook/assets/earth_icon.png" alt="" data-size="line">），这对于存储在您密码库中的所有登录项目都是相同的。

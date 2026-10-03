# =Bitwarden 重新设计 Beta 版

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/redesign-beta/)
{% endhint %}

Bitwarden 正在更新 App 的外观和体验，目前**面向云端用户推出 Chrome 浏览器扩展和桌面 App 的 Beta 版**。该 Beta 版需[主动选择加入](redesign-beta.md#join-the-beta)，可与您当前的 Bitwarden 云端账户配合使用，并且您可随时切换回正式版本。

## 有哪些变化 <a href="#whats-changing" id="whats-changing"></a>

此 Beta 版为您的密码库引入了全新的外观和导航方式。以下是您可以期待的内容：

### 新的密码库术语 <a href="#new-vault-terminology" id="new-vault-terminology"></a>

**组织**现在称为**密码库**，每个密码库在导航菜单中都有自己的名称。原本显示「密码库」的地方，现在将显示您组织的名称，例如「Acme Corp」。**集合**现在称为**共享文件夹**。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6K8cAenzwAWRFHUfEH7qQK/aa2de13ac228c746b9ff69dbb347c27b/2026-09-22_09-24-03.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>（Beta 版）共享文件夹</p></figcaption></figure></div>

{% hint style="success" icon="lightbulb" %}
这些只是名称上的更改。谁可以访问哪些项目，以及共享和权限的工作方式，均保持不变。
{% endhint %}

### 重新设计的导航 <a href="#redesigned-navigation" id="redesigned-navigation"></a>

侧边导航进行了重新组织，新增的「密码库」切换器让您可以更轻松地在个人密码库、您所属的任何其他密码库或两者之间切换视图。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6L9tVPVN5BPWSTuEqUvNGV/be4d1237bc9875f80a7c8fcd8a9556e2/2026-09-22_09-07-22.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>（Beta 版）重新设计的导航</p></figcaption></figure></div>

{% hint style="success" icon="lightbulb" %}
导入凭据是新用户最重要的第一步之一！因此，我们将**导入**按钮直接移到了桌面 App 的核心「项目」视图中（网页 App 正式发布后，也会将其移到该视图中）：

<img src="https://bitwarden.com/assets/rkAIYmIQbxj8m1YofyeH1/256ca500e993a1b00a84b6bf09fced38/2026-09-22_09-19-10.png?w=1400&#x26;fm=avif" alt="" data-size="original">

在浏览器扩展和移动 App 中，导入功能位于 App 的**设置**菜单的同一位置。
{% endhint %}

### 组合的搜索和筛选 <a href="#combined-search-and-filter" id="combined-search-and-filter"></a>

在您的密码库中，搜索和筛选功能现在集成在一个工具栏中，直接位于项目列表中，而不是两个独立的控件。搜索和筛选功能协同工作，因此，如果启用了 `Acme Corp` 密码库筛选然后搜索 `Email`，则会找到您有权访问的 `Shared Newsletter Email` 登录，但不会找到您自己的 `Work Email`（只要它不位于共享文件夹中）。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3vOMPXLwJ95gfT9g5x6RWP/d9e60285f792b1641b5d5f63f4162a27/2026-09-28_09-28-57.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>（Beta 版）搜索和筛选</p></figcaption></figure></div>

在上面的截图中，桌面 App 启用了密码库筛选器，但浏览器扩展没有启用。启用的筛选器会以可关闭的标签形式显示，因此始终可以清楚地看到当前 App 的筛选条件，并且在离开列表后再返回时，筛选器选择会保留。

{% hint style="success" icon="lightbulb" %}
Beta 版中还新增了一些键盘快捷键。使用 `Cmd/Ctrl+F` 进行搜索，以及使用 `Esc` 清除筛选。
{% endhint %}

## 加入 Beta 版 <a href="#join-the-beta" id="join-the-beta"></a>

此 Beta 版适用于浏览器扩展和桌面 App。您只需从以下任一位置下载测试版 App 即可：

* Chrome 浏览器扩展：[此处下载](https://chromewebstore.google.com/detail/bitwarden-password-manage/hccnnhgbibccigepcmlgppchkpfdophk?pli=1)（**要求** Chrome 版本 134+）。
* 桌面 App：[此处下载](https://github.com/bitwarden/clients/releases/tag/desktop-v2026.9.1-beta.1)。
  * 在 Windows 系统上，下载 `.exe` 文件。
  * 在 macOS 上，下载 `.dmg` 文件。

安装完成后，像往常一样登录您的 Bitwarden 云服务器（US 或 EU），无需额外的账户或服务器设置。

{% hint style="info" %}
Beta 版**不适用于自托管 Bitwarden 服务器**。
{% endhint %}

**我们强烈建议**您停用正式版 Bitwarden 浏览器扩展，以避免 App 在自动填充和 2FA 等功能上相互竞争；同时卸载正式版桌面 App，以避免它们在生物识别上相互竞争。您应该一次只激活**每种 App 的其中一个版本**。

对于 macOS 桌面 App，可能会提示您将操作系统密码保存到钥匙串中，以便 Beta 版 App 可以访问安全存储。我们建议选择**始终允许**。

### 发送[^1]反馈 <a href="#send-feedback" id="send-feedback"></a>

我们很想知道您对 Beta 版的看法：

* 要分享您的 Beta 版体验，请[填写调查问卷](https://docs.google.com/forms/d/e/1FAIpQLSdSVNSLkHTt399Okh_WbdZOZ01iEAcpH5-rFbz4sJDIgqe1Og/viewform)并在[社区论坛帖子](https://community.bitwarden.com/t/try-out-the-redesigned-bitwarden-apps-now-in-beta/102516)中分享您的体验。
* 要报告错误，请选择**新建话题**然后使用**浏览器扩展 Beta 版错误报告**或**桌面 Beta 版错误报告**模板，[在 GitHub 上创建一个话题](https://github.com/bitwarden/clients/issues)。

### 已知问题 <a href="#known-issues" id="known-issues"></a>

### 退出 Beta 版 <a href="#leave-the-beta" id="leave-the-beta"></a>

[^1]: 

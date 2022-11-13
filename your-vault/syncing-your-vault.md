# 同步密码库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/vault-sync/)
{% endhint %}

通过任何 Bitwarden 客户端应用程序添加、编辑或删除[密码库项目](vault-items.md)后，都会自动推送更改到您的 Bitwarden 服务器，无论是云托管还是自托管。

为了将这些更改拉取到另一个 Bitwarden 客户端应用程序，您的密码库将需要同步。

## 自动同步 <a href="#what-is-vault-syncing" id="what-is-vault-syncing"></a>

您的个人[网页密码库](../getting-started/getting-started-webvault.md)中的项目将始终保持同步。组织密码库的项目将跨用户和客户端应用程序每 30 分钟自动同步一次。

Bitwarden 客户端应用程序（桌面应用程序、浏览器扩展、移动应用程序和 CLI）将在登录时自动同步，并在解锁时定期同步。您也可以[手动同步](syncing-your-vault.md#what-is-vault-syncing-1)您的密码库，以立即拉取更改。

{% hint style="success" %}
当您在新设备上安装了 Bitwarden，只需登录到您现有的账户，就会自动拉取您的最新密码库数据。
{% endhint %}

## 手动同步 <a href="#what-is-vault-syncing" id="what-is-vault-syncing"></a>

要从 Bitwarden 客户端应用程序手动同步密码库：

{% tabs %}
{% tab title="浏览器扩展" %}
### 从浏览器扩展同步 <a href="#sync-browser-extensions" id="sync-browser-extensions"></a>

选择 **⚙️设置**标签，选择**同步**选项然后点击**立即同步密码库**按钮。
{% endtab %}

{% tab title="移动端" %}
### 从移动应用程序同步 <a href="#sync-mobile-apps" id="sync-mobile-apps"></a>

打开 **⚙️设置**标签，点击**同步**选项并点击**立即同步密码库**。

切换**启用刷新时同步**选项，以允许在 **🔒我的密码库**选项卡上使用下拉手势来同步密码库。
{% endtab %}

{% tab title="桌面端" %}
### 从桌面应用程序同步 <a href="#sync-desktop-apps" id="sync-desktop-apps"></a>

从菜单栏选择**文件** → **同步密码库**。

{% hint style="info" %}
只会同步[当前活动的帐户](account-switching.md)。
{% endhint %}
{% endtab %}

{% tab title="CLI" %}
### 从 CLI 同步 <a href="#sync-the-cli" id="sync-the-cli"></a>

使用 `sync` 命令来手动同步您的密码库：

```
bw sync
```

更多详情，请参阅 **** Bitwarden [CLI 文档](../getting-started/bitwarden-cli.md)。
{% endtab %}
{% endtabs %}

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

如果密码库同步无法正常运行，请检查以下内容：

### 时间戳不匹配 <a href="#mismatched-timestamp" id="mismatched-timestamp"></a>

如果您的设备时间不正确，则可能会同步失败。 Bitwarden 使用TLS/SSL，如果时间戳不匹配，则客户端应用程序将无法连接到服务器。

### VPN 或广告拦截器干扰 <a href="#vpn-or-ad-blocker-interference" id="vpn-or-ad-blocker-interference"></a>

某些情况下，VPN 或广告拦截器等浏览器扩展可能会干扰客户端应用程序与服务器之间的连接。使用 Bitwarden 浏览器扩展通常会观察到此问题。

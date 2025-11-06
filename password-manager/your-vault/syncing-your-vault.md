# 同步密码库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/vault-sync/)
{% endhint %}

通过任何 Bitwarden App 添加、编辑或删除[密码库项目](vault-items/vault-items.md)后，都会自动推送更改到您的 Bitwarden 服务器，无论是云托管还是自托管。

为了将这些更改拉取到另一个 Bitwarden App，您的密码库将需要同步。

## 自动同步 <a href="#automatic-sync" id="automatic-sync"></a>

您的个人[网页密码库](../../getting-started/getting-started-webvault.md)拥有的项目将始终保持同步。组织拥有的项目将跨用户和客户端应用程序每 30 分钟自动同步一次。

Bitwarden App（桌面 App、浏览器扩展、移动 App 和 CLI）将在登录时自动同步，并在解锁时定期同步。您也可以[手动同步](syncing-your-vault.md#what-is-vault-syncing-1)您的密码库，以立即拉取更改。

{% hint style="success" %}
当您在新设备上安装了 Bitwarden，只需登录到您现有的账户，就会自动拉取您的最新密码库数据。
{% endhint %}

## 手动同步 <a href="#manual-sync" id="manual-sync"></a>

要从 Bitwarden App 手动同步密码库：

{% tabs %}
{% tab title="浏览器扩展" %}
在 **⚙️设置**标签页，选择**密码库**然后使用**立即同步密码库**按钮。
{% endtab %}

{% tab title="移动端" %}
打开 **⚙️设置**标签，点击**其他**选项然后点击**立即同步密**。

切换**启用刷新时同步**选项，以允许在 **🔒我的密码库**选项卡上使用下拉手势来同步密码库。
{% endtab %}

{% tab title="桌面端" %}
从菜单栏选择**文件** → **同步密码库**。

{% hint style="info" %}
只有[当前活动的账户](../../account/log-in-and-unlock/more-log-in-options/account-switching.md)会同步，但即使密码库被锁定，账户也能被同步。
{% endhint %}
{% endtab %}

{% tab title="CLI" %}
使用 `sync` 命令来手动同步您的密码库：

```batch
bw sync
```

更多详情，请参阅 Bitwarden [CLI 文档](../developer-tools/cli/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

如果密码库同步无法正常运行，请检查以下内容：

### 时间戳不匹配 <a href="#mismatched-timestamp" id="mismatched-timestamp"></a>

如果您的设备时间不正确，则可能会同步失败。 Bitwarden 使用TLS/SSL，如果时间戳不匹配，则客户端应用程序将无法连接到服务器。

### VPN 或广告拦截器干扰 <a href="#vpn-or-ad-blocker-interference" id="vpn-or-ad-blocker-interference"></a>

某些情况下，VPN 或广告拦截器等浏览器扩展可能会干扰客户端应用程序与服务器之间的连接。使用 Bitwarden 浏览器扩展通常会观察到此问题。

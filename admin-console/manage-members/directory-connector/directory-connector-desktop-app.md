# 目录连接器桌面 App

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/directory-sync-desktop/)
{% endhint %}

目录连接器桌面 App 是一个独立的桌面应用程序，可用于从一系列目录服务同步用户、群组以及群组关联。

{% embed url="https://bitwarden.com/help/images/directory-connector/app.png" %}
目录连接器桌面应用程序
{% endembed %}

目录连接器也适用于作为 [CLI 工具](directory-connector-cli.md)。桌面 App 和 CLI [共享数据库和配置](directory-connector-file-storage.md)，因此不建议在一台机器上**同时**使用。建议使用[桌面 App](directory-connector-desktop-app.md) 完成配置和测试，然后使用 [CLI](directory-connector-cli.md) [调度自动同步](schedule-a-sync.md)到生产组织。

## 入门 <a href="#getting-started" id="getting-started"></a>

要开始使用目录连接器桌面 App：

1、从我们的 [GitHub 发布页面](https://github.com/bitwarden/directory-connector/releases)或使用以下官方链接之一下载最新版本的 App：

* ​![](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-M2XqgFI6fAcTD0lL3MZ%2F-M2lgIMT8p-h_KydT0nq%2F-M2lmjhiYHSJ5-sYyb6Z%2Fos-windows-24.png?alt=media\&token=0d9e6b96-ec16-4dc0-a39a-a78fdfb0e33a)[Windows Installer（.exe）](https://vault.bitwarden.com/download/?app=connector\&platform=windows)​
* ​​![](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-M2XqgFI6fAcTD0lL3MZ%2F-M2lgIMT8p-h_KydT0nq%2F-M2lmjhiYHSJ5-sYyb6Z%2Fos-windows-24.png?alt=media\&token=0d9e6b96-ec16-4dc0-a39a-a78fdfb0e33a)[Windows Portable（.exe）](https://vault.bitwarden.com/download/?app=connector\&platform=windows\&variant=portable)​
* ​​![](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-M2XqgFI6fAcTD0lL3MZ%2F-M2lgIMT8p-h_KydT0nq%2F-M2lmd9QDMlX1Sn3aHOo%2Fapple-24.png?alt=media\&token=e90fd6d0-5ca3-43a7-9818-441b86ae2147)[macOS（.dmg）](https://vault.bitwarden.com/download/?app=connector\&platform=macos)​
* ​​![](https://files.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-M2XqgFI6fAcTD0lL3MZ%2F-M2lgIMT8p-h_KydT0nq%2F-M2lmhr5ffWYeEG74jXf%2Flinux-24.png?alt=media\&token=26403b17-eb24-4721-8c42-b6fb70164cc2)[Linux（.AppImage）](https://vault.bitwarden.com/download/?app=connector\&platform=linux)

2、如果您使用的是 Bitwarden 的自托管版本或使用 [EU 服务器](../../../security/server-geographies.md)，请在登录前设置目录连接器使用的服务器 URL：

1. 在登录界面上，选择 **Setting**。
2. 在 **Server URL** 字段中，输入带 `https://` 的 Bitwarden 实例的域名。例如，`https://vault.bitwarden.eu` 或 `https://your.domain.bitwarden.com`。
3. 选择 **Save**。

3、使用您的[组织 API 密钥](../../../organizations/bitwarden-public-api.md#authentication)登录目录连接器。如果您没有 API 密钥，请联系[组织的所有者](../member-roles.md)。

4、在 **⚙️Setting** 选项卡上，连接到您的目录并配置[同步选项](sync-options-and-filters.md)。此过程基于所使用的目录而有所不同，请参阅以下文章之一以获取说明：

* [使用 AD 或 LDAP 同步](sync-with-active-directory-or-ldap.md)
* [使用 Microsoft Entra ID 同步](sync-with-microsoft-entra-id.md)
* [使用 Google Workspace 同步](sync-with-google-workspace.md)
* [使用 Okta 同步](sync-with-okta.md)
* [使用 OneLogin 同步](sync-with-onelogin.md)

{% hint style="success" %}
如果您要重新配置同步选项，而不是第一次设置它们，请导航到 **More** 选项卡然后选择 **Clear Sync Cache** 按钮以防止与之前的同步操作发生潜在冲突（[了解更多](clear-sync-cache.md)）。
{% endhint %}

5、在 **⚙️Setting** 选项卡上，从 Organization 下拉列表中选择您的组织。

6、**执行同步测试**。以检查您的目录连接和同步选项是否已成功配置并按预期工作：

1. 打开 🎨**Dashboard** 选项卡。
2. 选择 **Test Now** 按钮。

同步测试将查询目录服务器并将结果打印到仪表板。结果包含的内容：

* 将从目录中同步的用户列表。
* 将从目录中同步的群组列表。
* 根据用户在目录中的状态而将禁用的用户列表。
* 根据用户在目录中的状态而将从组织中删除的用户列表。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6HK5d7qPL22HYTHbgRS1tp/42127d0fde4fea4f645ea7ce807ebadc/Screenshot_2024-08-19_at_1.44.23_PM.png?_a=DAJCwlWIZAAB" %}
目录连接器测试同步
{% endembed %}

如果打印的结果符合您的预期，您就可以[开始同步](directory-connector-desktop-app.md#sync-with-directory-connector)了。

## 使用目录连接器同步 <a href="#sync-with-directory-connector" id="sync-with-directory-connector"></a>

目录连接器可用于运行一次性[手动同步](directory-connector-desktop-app.md#perform-a-manual-sync)或[自动同步轮询](directory-connector-desktop-app.md#start-automatic-sync)：

### 手动同步 <a href="#manual-sync" id="manual-sync"></a>

要运行从您的目录到 Bitwarden 组织的一次性手动同步，请打开 🎨**Dashboard** 选项卡然后选择 **🔄Sync Now** 按钮。

已同步的用户将被邀请加入您的组织，并且将立即创建群组。

### 自动同步 <a href="#automatic-sync" id="automatic-sync"></a>

只要应用程序处于打开状态，自动同步就会根据[同步选项](sync-options-and-filters.md)中指定的时间**间隔**轮询您的目录。如果您退出或关闭应用程序，自动同步轮询将停止。

要使用目录连接器启动自动同步轮询，请打开 🎨**Dashboard** 选项卡然后选择 ▶︎**Start Sync** 按钮。

{% hint style="info" %}
如果您使用的是[团队入门版](../../../plans-and-pricing/password-manager/about-bitwarden-plans.md#teams-starter-organizations) 计划，则只能同步 10 个成员。如果您尝试同步超过 10 名成员，目录连接器将显示错误并停止同步。

**该计划已不再提供购买**。此错误不适用于团队计划。
{% endhint %}

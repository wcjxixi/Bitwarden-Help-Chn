# 关于目录连接器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/directory-sync/)
{% endhint %}

## 什么是目录连接器？ <a href="#what-is-directory-connector" id="what-is-directory-connector"></a>

Bitwarden 目录连接器 App 通过从一系列源目录服务中提取信息，自动为您的 Bitwarden 组织布建用户、群组和群组关联。已配置的用户将收到加入组织的邀请，随后可完成正常的[入职流程](../organizations/user-management.md#onboard-users)。

当用户从源目录中被禁用时，目录连接器可被配置为从 Bitwarden 组织中移除用户。这不会删除他们的 Bitwarden 账户，但他们将失去对组织的所有访问权限。

{% hint style="info" %}
目录连接器功能适用于**团队**和**企业**组织。要使用目录连接器，您必须有权访问您的[组织 API 密钥](../organizations/bitwarden-public-api.md#authentication)，该密钥只​​能由[组织所有者](../admin-console/user-management/member-roles-and-permissions.md)获取并使用 [Bitwarden Send](../bitwarden-send/about-send.md) 安全共享。
{% endhint %}

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6RFsU5sJGDLMPawg64sBqM/85c9e9f6e7758944d76c8ecb79ca4af9/Marketing_Diagram_2024__1_.png?_a=DAJCwlWIZAAB" %}
目录连接器图示
{% endembed %}

目录连接器同步操作可以按需运行，也可以按配置的时间间隔自动运行。目录连接器应用程序可以作为代理安装在托管目录的服务器、管理员的工作站或任何其他可以访问源目录的桌面设备上。

目录连接器支持从以下来源同步：

* [Active Directory](sync-with-active-directory-or-ldap.md)
* [任何基于 LDAP 的目录](sync-with-active-directory-or-ldap.md)
* [Microsoft Entra ID](../admin-console/user-management/directory-connector/sync-with-microsoft-entra-id.md)
* [Google Workspace](sync-with-google-workspace.md)
* [Okta](sync-with-okta.md)
* [OneLogin](sync-with-onelogin.md)

## 目录连接器应用程序 <a href="#directory-connector-applications" id="directory-connector-applications"></a>

目录连接器可作为跨平台的[桌面 App](directory-connector-desktop-app.md) 和[命令行界面（CLI）](directory-connector-cli.md)使用。桌面 App 和 CLI [共享数据库和配置](directory-connector-file-storage.md)，因此不建议在一台机器上**同时**使用。建议使用[桌面 App](directory-connector-desktop-app.md) 完成配置和测试，然后使用 [CLI](directory-connector-cli.md) [调度自动同步](schedule-a-sync.md)到生产组织。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7r6eylncijFasEUrKXe2Hk/b6eec60c8a6452a300eeba5272c46ea4/app.png?_a=DAJCwlWIZAAB" %}
目录连接器桌面 App
{% endembed %}

## 下载目录连接器 <a href="#download-directory-connector" id="download-directory-connector"></a>

使用下面的链接下载目录连接器。

{% tabs %}
{% tab title="桌面版应用程序" %}
从我们的 [GitHub 发布页面](https://github.com/bitwarden/directory-connector/releases)或使用以下官方链接下载最新版本的目录连接器桌面 App：

* <img src="../.gitbook/assets/os-windows-24.png" alt="" data-size="line"> [ Windows Installer（.exe）](https://vault.bitwarden.com/download/?app=connector\&platform=windows)
* <img src="../.gitbook/assets/os-windows-24.png" alt="" data-size="line"> [ Windows Portable（.exe）](https://vault.bitwarden.com/download/?app=connector\&platform=windows\&variant=portable)
* <img src="../.gitbook/assets/apple-24.png" alt="" data-size="line"> [ macOS（.dmg）](https://vault.bitwarden.com/download/?app=connector\&platform=macos)
* <img src="../.gitbook/assets/linux-24.png" alt="" data-size="line"> [ Linux（.AppImage）](https://vault.bitwarden.com/download/?app=connector\&platform=linux)
{% endtab %}

{% tab title="CLI" %}
从以下链接下载最新版本的目录连接器 CLI：

* <img src="../.gitbook/assets/os-windows-24.png" alt="" data-size="line">[ Windows CLI（.exe）](https://vault.bitwarden.com/download/?app=connector\&platform=windows\&variant=cli-zip)
* <img src="../.gitbook/assets/apple-24.png" alt="" data-size="line">[ macOS CLI](https://vault.bitwarden.com/download/?app=connector\&platform=macos\&variant=cli-zip)
* <img src="../.gitbook/assets/linux-24.png" alt="" data-size="line">[ Linux CLI](https://vault.bitwarden.com/download/?app=connector\&platform=linux\&variant=cli-zip)
{% endtab %}
{% endtabs %}

## 源代码 <a href="#source-code" id="source-code"></a>

与 Bitwarden 的所有内容一样，目录连接器也是开源的，并托管在 GitHub 的[https://github.com/bitwarden/directory-connector](https://github.com/bitwarden/directory-connector) 上。

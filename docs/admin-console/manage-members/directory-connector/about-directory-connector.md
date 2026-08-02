# 关于 Directory Connector

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/directory-sync/)
{% endhint %}

{% hint style="info" %}
本文仅讨论邀请用户和管理您的订阅席位数量的可用方法之一：

* 所有组织都可以[手动邀请用户](../user-management.md)和更新[席位数量](../../../plans-and-pricing/manage-subscription-seats-in-your-organization.md)。
* 团队版和企业版组织可以使用 [SCIM](../scim/about-scim.md)。
* 团队版和企业版组织可以使用 [Directory Connector](about-directory-connector.md)。
* 企业版组织可以[使用 JIT](../../login-with-sso/jit-provisioning.md)。
{% endhint %}

Bitwarden Directory Connector App：

* 通过从选定的源目录服务中提取信息，在您的 Bitwarden 组织中**自动配置用户、群组和群组关联**。已配置的用户将收到加入组织的邀请，随后可完成正常的[入职流程](../user-management.md#onboard-users)中的接受和确认步骤。
* 当用户从源目录中被禁用时，**可被配置为从 Bitwarden 组织中移除用户**。这不会删除他们的 Bitwarden 账户，但他们将失去对组织的所有访问权限。
* **可按需运行**，或按配置的时间间隔**自动运行**。

## 应用程序 <a href="#applications" id="applications"></a>

Directory Connector 可作为跨平台的[桌面 App](directory-connector-desktop-app.md) 和[命令行界面（CLI）](directory-connector-cli.md)使用。桌面 App 和 CLI [共享数据库和配置](directory-connector-file-storage.md)，因此不建议在一台机器上**同时**使用。

推荐的路径是使用[桌面 App](directory-connector-desktop-app.md) 完成配置和测试，然后使用 [CLI](directory-connector-cli.md) [调度自动同步](schedule-a-sync.md)到您的生产组织。

Directory Connector 可以**安装在能够访问源目录的任何桌面设备上**，包括作为代理安装在托管目录的服务器上，或管理员的工作站上。

{% hint style="info" %}
要使用 Directory Connector，您必须能够访问[组织 API 密钥](../../bitwarden-public-api.md#authentication)，该密钥只能由[组织所有者](../member-roles.md)获取，并使用 [Bitwarden Send](../../../password-manager/bitwarden-send/about-send.md) 安全共享。
{% endhint %}

### 下载 <a href="#download" id="download"></a>

立即下载 Directory Connector：

{% tabs %}
{% tab title="桌面 App" %}
从 [GitHub](https://github.com/bitwarden/directory-connector/releases) 或使用以下链接下载最新版本的 Directory Connector 桌面 App：

* <i class="fa-windows">:windows:</i> [Windows Installer (.exe)](https://bitwarden.com/download/?app=connector\&platform=windows)
* <i class="fa-windows">:windows:</i> [Windows Portable (.exe)](https://bitwarden.com/download/?app=connector\&platform=windows\&variant=portable)
* <i class="fa-apple">:apple:</i> [macOS (ARM64) (.dmg)](https://bitwarden.com/download/?app=connector\&platform=macos) | [macOS (x64) (.dmg)](https://bitwarden.com/download/?app=connector\&platform=macos\&variant=x64dmg)
* <i class="fa-linux">:linux:</i> [Linux (.AppImage)](https://bitwarden.com/download/?app=connector\&platform=linux)
{% endtab %}

{% tab title="CLI" %}
从以下链接下载最新版本的 Directory Connector CLI：

* <i class="fa-windows">:windows:</i> [Windows CLI (.exe)](https://bitwarden.com/download/?app=connector\&platform=windows\&variant=cli-zip)
* <i class="fa-apple">:apple:</i> [macOS CLI](https://bitwarden.com/download/?app=connector\&platform=macos\&variant=cli-zip)
* <i class="fa-linux">:linux:</i> [Linux CLI](https://bitwarden.com/download/?app=connector\&platform=linux\&variant=cli-zip)
{% endtab %}
{% endtabs %}

与 Bitwarden 的所有产品一样，Directory Connector 是开源的，并托管在 GitHub 上：[github.com/bitwarden/directory-connector](https://github.com/bitwarden/directory-connector)。

## 源代码 <a href="#source-code" id="source-code"></a>

与 Bitwarden 的所有产品一样，Directory Connector 也是开源的，并托管在 GitHub 上 [https://github.com/bitwarden/directory-connector](https://github.com/bitwarden/directory-connector)。

## 源目录 <a href="#source-directories" id="source-directories"></a>

Directory Connector 支持从以下源目录进行同步：

* [Active Directory](sync-with-ldap-or-ad.md)
* [任何基于 LDAP 的目录](sync-with-ldap-or-ad.md)
* [Microsoft Entra ID](sync-with-microsoft-entra-id.md)
* [Google Workspace](sync-with-google-workspace.md)
* [Okta](sync-with-okta.md)
* [OneLogin](sync-with-onelogin.md)

### 更改电子邮箱地址 <a href="#changing-email-addresses" id="changing-email-addresses"></a>

{% hint style="info" %}
使用[受信任设备](../../login-with-sso/trusted-devices/about-trusted-devices.md)的组织成员无法更改其电子邮箱地址，除非通过[账户恢复](../account-recovery/about-account-recovery.md)获得主密码。

使用 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md) 的组织成员无法更改其电子邮箱地址。成员账户需要被[删除](../revoke-remove/delete-member-accounts.md)并重新配置，以适应电子邮箱地址的变更。提醒用户在删除账户前导出数据，并在使用新电子邮箱地址配置完成后重新导入其数据。
{% endhint %}

使用 Directory Connector 配置的成员可以在 Bitwarden 和源目录中更改其账户电子邮箱地址，但需遵循以下步骤：

* 首先在 Bitwarden 中更改电子邮箱地址，请前往**设置** → **我的账户**（[了解更多](../../../password-manager/more/password-manager-faqs.md#q-how-do-i-change-my-email-address)）。
* 在 Bitwarden 中更改电子邮箱后，管理员可以在目录中更改用户值。
* 重新同步目录以实施更改。

{% hint style="info" %}
如果在更新 Bitwarden 电子邮箱之前，用户电子邮箱地址已在 IdP 或 AD 上更新并同步，则更新后的电子邮箱将被视为新用户。
{% endhint %}

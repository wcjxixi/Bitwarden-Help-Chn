# 发行记录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/releasenotes/)
{% endhint %}

Bitwarden 认为源代码透明是像我们这样的安全解决方案的一个绝对要求。请访问以下 GitHub 链接查看完整、详细的发行记录：

* [Server Releases](https://github.com/bitwarden/server/releases)
* [Web Releases](https://github.com/bitwarden/clients/releases)
* [Desktop Releases](https://github.com/bitwarden/clients/releases)
* [Browser Extension Releases](https://github.com/bitwarden/clients/releases)
* [Android Releases](https://github.com/bitwarden/android/releases)
* [iOS Releases](https://github.com/bitwarden/ios/releases)
* [CLI Releases](https://github.com/bitwarden/clients/releases)
* [Directory Connector Releases](https://github.com/bitwarden/directory-connector/releases)

## 发行公告

Bitwarden 会在初始发布后逐步更新每个客户端应用程序（桌面端、浏览器扩展、移动端等），以及自托管服务器，以确保功能的有效性和稳定性。因此，客户端应用程序和自托管服务器将在初始发布后逐步获得所列的功能。请查看 Bitwarden [软件发布支持](security/software-development/software-release-support.md)文档。

{% hint style="success" %}
您也可以订阅 [Bitwarden Status RSS feed](https://status.bitwarden.com/) 以获取服务更新，包括发行窗口的公告。
{% endhint %}

## 2025.10.0

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.10.0、浏览器扩展 2025.10.0、移动端 2025.10.0、桌面端 2025.10.0、CLI 2025.10.0）

### Password Manager

* **Edge、Opera 和 Vivaldi 浏览器的直接导入功能**：通过 Edge、Opera 和 Vivaldi 浏览器的[直接导入](password-manager/import-and-export/import-guides/import-data-from-chrome.md#import-directly-from-browser)功能，快速安全地将数据迁移至 Bitwarden。
* **我的项目**：当启用[强制组织数据所有权策略](admin-console/oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)时，所有项目 将归组织所有。受此策略约束的成员现在可以将项目保存至新的[我的项目](password-manager/vault-basics/organization-members/my-items.md)位置，既保障了成员隐私，又确保了管理员能在成员离开组织后转移数据。
* **简化单点登录用户登录界面**：采用[要求单点登录策略](admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)的组织成员，若他们曾在该设备完成过身份验证，登录界面中其他验证选项将自动灰显。

### Secrets Manager

* **新的事件日志**：当机器账户被创建、删除，或有用户/群组被分配至其名下，以及用户/群组被移除时，Secrets Manager 现将[记录相关事件](admin-console/oversight-visibility/event-logging/event-logs.md#secrets-manager-events)。

### 自托管 <a href="#self-host" id="self-host"></a>

* **新的环境变量**：现提供用于配置刷新令牌处理的[新环境变量](self-hosting/deploy-and-configure/configuration-options/environment-variables.md#refresh-token-variables)，允许用户在自托管服务器上设定身份验证令牌的有效期和超时时间。

## 2025.9.2

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.9.1）

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **成员邀请函主题行更新**：更新了加入组织的邀请的[电子邮件主题行](security/trusted-communications/emails-from-bitwarden-servers.md#critical-member-emails)。
* **税务 ID 提醒**：如果您是征收[增值税 (VAT)](plans-and-pricing/tax-calculation.md#value-added-tax-vat) 国家的企业主或提供商管理员，并且尚未添加税务 ID，您将在管理控制台、付款详细信息和提供商门户页面上看到一个横幅。单击**添加税务 ID** 以使用组织的税务 ID 更新账单详细信息。

### Secrets Manager

* **Terraform 提供商**：Bitwarden Secrets Manager 现在提供 Terraform 提供商，能够为您的 Terraform 基础架构获取、创建和管理 Secrets Manager 的机密。[了解更多](secrets-manager/integrations/terraform-provider.md)有关 Terraform 提供商的信息。

## Secrets Manager Kubernetes Operator 1.0.0

* **更新默认的映射机密行为**：Kubernetes Operator 的新默认行为只会同步映射到 `BitwardenSecret` 对象中的机密，除非使用 `onlyMappedSecrets: false` 另作指定。[了解更多](secrets-manager/integrations/secrets-manager-kubernetes-operator.md)有关 Secrets Manager Kubernetes Operator 的信息。

## 2025.9.0

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.9.0、浏览器扩展 2025.9.0、移动端 2025.9.0、桌面端 2025.9.0、CLI 2025.9.0）

### Password Manager

* **使用浏览器扩展批准设备**：使用浏览器扩展审批新的[受信任设备](account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)和[设备登录](account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)请求。
* **CXP for iOS 26**：iOS 26 的用户现在可以直接导入或导出 Bitwarden 和任何其他支持 [Fido 凭证交换协议](https://fidoalliance.org/specifications-credential-exchange-specifications/?lang=zh-hans)的 iOS App。了解更多有关导入和[导出](import-export/export-vault-data.md)的信息。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **集合设置更新**：某些集合管理设置已重新命名，现在打开或关闭时将记录更详细的事件。[了解更多](admin-console/manage-shared-items/collections/collection-settings.md)。
* **组织 SSH 密钥**：使用 Bitwarden SSH 代理创建的 SSH 密钥现在可以在组织集合中存储和共享。[了解更多](password-manager/developer-tools/ssh/ssh-agent.md)有关 Bitwarden SSH 代理的信息。

## 2025.8.1

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.8.2、移动 2025.8.1）

{% hint style="info" %}
**Helm 图表版本更新**：对于 Bitwarden 自托管 Helm 图表，CalVer 版本方案 (2025.8.0) 将于 2025 年 11 月 13 日废弃。在此日期之后，将仅支持和发布 SemVer 版本。

您现在就可以开始使用 SemVer 1.0.0，但请注意，在 2025 年 11 月 13 日之前，您必须在升级时始终指定 `--version <semver-version>`：

```bash
helm upgrade self-host-bsfyr9bpzk bitwarden/self-host --version <semver-version> -n bitwarden
```
{% endhint %}

### Password Manager

* **Android 的支付卡自动填充**：Bitwarden Android App 现在可以自动填充支付卡，例如借记卡或信用卡。[了解更多](password-manager/autofill/more-autofill-options/auto-fill-cards-and-identities.md)。
* **2FA 失败时的电子邮件**：用户现在将收到一封电子邮件，通知他们被两步登录阻止的失败的登录尝试。如果您收到这些电子邮件，请立即将主密码更新为强、唯一且从未使用过的主密码。[了解更多](security/trusted-communications/emails-from-bitwarden.md)。

### Secrets Manager

* **新的事件日志**：Secrets Manager 现在会在访问、创建、编辑或删除工程时记录事件日志。[了解更多](admin-console/oversight-visibility/event-logging/event-logs.md)。

## 2025.8.2

（此次所列版本号**仅包含浏览器扩展 & 桌面 App**。下一个包含服务器更新的版本将恢复为典型的版本进程 (2025.8.1)）

* 为了进一步防范恶意网站，内嵌自动填充菜单现在总是显示在网页其他内容的上方。

## 2025.8.0

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.8.0、浏览器扩展 2025.8.0、移动端 2025.8.0、桌面端 2025.8.0、CLI 2025.8.0）

{% hint style="info" %}
为确保与最新的 Bitwarden 版本兼容，请更新您的客户端和自托管服务器。根据 [Bitwarden 软件发布支持](security/software-development/software-release-support.md)政策，保持软件为最新版本将有助于保持完全兼容、支持和解锁最新的 Bitwarden 功能。
{% endhint %}

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **禁用支付卡项目类型策略**：添加了一项企业策略，允许企业组织限制支付卡项目类型的使用。[了解更多](admin-console/oversight-visibility/enterprise-policies.md#remove-card-item-type)。

### Password Manager

* **内嵌自动填充密码生成器改进**：内嵌自动填充密码生成器现在可立即将生成的密码保存为新的登录项目。[了解更多](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#inline-auto-fill-menu)有关内嵌自动填充的信息。
* **改进的项目视图**：添加了对查看密码库项目的改进。更新包括在密码库项目顶部显示收藏夹和其他重要信息。[了解更多](your-vault/vault-items.md)有关密码库项目的信息。
* **Android 现在要求使用 HTTPS**：Android Password Manager App 现在要求使用 HTTPS 连接到服务器。这一更改只会影响没有 SSL/TLS 证书的 Bitwarden 服务器自托管用户。[了解更多](self-hosting/deploy-and-configure/configuration-options/certificate-options.md)有关证书的信息。
* **生物识别解锁更新**：桌面 App 重新启动后，现在必须首先使用 PIN 或主密码等生物识别以外的方法解锁，然后才能使用生物识别解锁。[了解更多](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)有关生物识别解锁的信息。

## 2025.7.3

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.7.2）

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **成员视图性能改进**：优化了成员视图的加载时间，尤其是对于拥有大量成员的组织而言。

### 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

* **计费更新**：尚未在**计费** → **订阅**页面上添加付款方式的提供商应尽快添加付款方式。具有未支付账单的提供商现在将在未支付账单到期 30 天后被暂停服务，包括暂停客户组织。对于尚未添加有效付款方式的提供商，添加一个有效付款方式将确保服务的无缝延续。

### 自托管 <a href="#self-host" id="self-host"></a>

* **弃用的日志记录方式**：对于自托管用户，Bitwarden 中与 `syslog` 的直接集成（通过覆盖 `enabledglobalSettings__syslog__destination` 启用）已被弃用，转而与 Docker 的 `syslog` 驱动程序集成。使用弃用方法的用户将收到警告日志，通知他们这一变更。了解更多。

## 2025.7.1

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.7.1、浏览器扩展 2025.7.0、桌面端 2025.7.1、CLI 2025.7.0）

### Password Manager

* **URI 匹配检测警告更新**：选择使用高级选项**开始于**和**正则表达式**设置 URI 匹配检测的用户将看到一个警告对话，以确认他们了解与这些自动填充选项相关的潜在安全风险。了解更多。
* **针对新用户的屏幕提示 - 浏览器扩展**：为帮助新用户，浏览器扩展中添加了屏幕提示。这些提示将有助于向新用户介绍浏览器扩展的功能和组件。了解更多。
* **浏览器扩展权限更新**：Firefox 和 Safari 上的浏览器扩展现在需要通知权限才能支持设备登录。
* **Android 上的 Chromium 集成**：如果您使用 Brave 或 Chrome 浏览器，请切换新的**使用 Brave 自动填充集成**或**使用 Chrome 自动填充集成**选项。了解更多。

### Secrets Manager

* **新的机密事件**：现在会在创建、编辑或删除机密时记录事件日志。了解更多。

## 2025.7.0

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.7.0）

### Password Manager

* **Password Depot 17 导入**：Password Depot 17 已被添加到可直接导入 Bitwarden Password Manager 的格式列表中。了解更多。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **策略重命名**：**移除个人密码库**策略已重命名为**执行组织数据所有权**策略。了解更多。
* **成员权限更新**：拥有**管理账户恢复**权限的组织成员可以重置组织成员的主密码。该权限可与**管理用户**权限分开授予。了解更多。

## 2025.6.2

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.6.1、浏览器扩展 2025.6.0、桌面端 2025.6.0、CLI 2025.6.0）

{% hint style="info" %}
**使用旧版加密方案的账户不再受支持**：2017 年之前创建且 2023 年以来未登录过网页 App 的老账户，因使用了旧版加密方案，这些账户将不再受支持。仅两年内无任何使用记录的休眠账户会受到影响。[了解更多](miscellaneous/legacy-user-support.md)。
{% endhint %}

{% hint style="danger" %}
**自托管的 Kerberos 身份验证支持通知**：在某些部署模式下，自托管服务器版本 2025.6.0-2025.6.2 对 **Kerberos** 外部数据库身份验证的支持会出现中断，这将在即将发布的自托管版本中得到修复，使用 Kerberos 身份验证的客户应等到下一个版本发布后再升级他们的自托管部署，除非 Bitwarden 支持另有说明。
{% endhint %}

### Password Manager

* **添加和编辑项目时浏览器扩展的持久化**：现在，浏览器扩展对项目数据的更改操作将有最长 2 分钟的缓存周期，即使点击其他区域或最小化扩展窗口也不会丢失更改的数据。
* **浏览器扩展通知重新设计**：浏览器扩展通知有了新的外观和体验。[了解更多](password-manager/autofill/autofill-from/autosave-from-browser-extensions.md)。
* **移动版 App 高级故障排除**：在移动 App 中，用户现在可以选择本地临时记录 App 事件，以帮助排除 Bitwarden App 中的意外行为。[了解更多](password-manager/more/yu-bitwarden-zhi-chi-pai-chu-yi-dong-duan-gu-zhang.md)。

### Bitwarden Authenticator

* **使用 Password Manager 同步 TOTP**：用户现在可以选择在 Bitwarden Authenticator 和 Bitwarden Password Manager 之间无缝同步验证码数据。[了解更多](bitwarden-authenticator/totp-sync.md)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **成员权限更新**：**管理账户恢复**自定义角色权限将授予重置组织成员主密码的权限。成员界面上的任何其他操作也需要**管理用户**权限。了解更多有关[自定义角色](admin-console/manage-members/member-roles.md#custom-role)的信息。

## 2025.6.1

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.6.0、自托管 2025.6.1）

### 自托管 <a href="#self-host" id="self-host"></a>

* **Helm 无根容器**：Helm 部署现在可以在无根模式下运行 Bitwarden。[了解更多](self-hosting/deploy-and-configure/helm/self-host-with-helm.md#rootless-requirements)。

## 2025.5.3

### 自托管 <a href="#self-host" id="self-host"></a>

* **SQL 版本支持**：2025.5.3 版将是最后一个支持 SQL Server 2019 的 Bitwarden 版本。Bitwarden 完全支持 SQL Server 2022。

## 2025.5.2

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.5.1、浏览器扩展 2025.5.1、桌面端 2025.5.0、iOS 2025.5.0、Android 2025.5.0、CLI 2025.5.0）

{% hint style="info" %}
Bitwarden 客户端即将迎来重要变更！请注意：若长期未更新，旧版本将无法正常运行（尤其影响 CLI 用户）。为了提升安全性和可维护性，请务必将所有已安装客户端升级至最新版本。
{% endhint %}

### Password Manager

* **更新了通知设计**：浏览器扩展通知已更新为全新的视觉设计。[了解更多](password-manager/autofill/autofill-from/autosave-from-browser-extensions.md)。
* **支持从桌面和 CLI 导出附件**：现在可以通过桌面 App 和 CLI 将个人密码库文件附件导出为 `.zip` 压缩包。[了解更多](your-vault/file-attachments.md)。
* **Android 动态颜色支持**：Bitwarden Android App 现在支持根据壁纸自动应用配色方案。[了解更多](miscellaneous/change-app-theme.md#yi-dong-duan)。
* **SSH 批准设置**：在桌面 App 上，启用了 SSH 代理的用户可使用一项新的设置：可以指定 Bitwarden 何时要求您授权访问存储在密码库中的 SSH 凭据。[了解更多](password-manager/developer-tools/ssh/ssh-agent.md)有关 SSH 代理设置的信息。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **组织赞助的家庭计划**：组织可以直接为员工个人电子邮箱账户（包括非当前组织成员的员工）发放赞助版家庭计划。[了解更多](admin-console/more/organization-sponsored-families-plans.md)有关赞助版家庭计划的信息。
* **集合权限调整**：「可以编辑」和「可以编辑，隐藏密码」权限现默认允许用户删除集合项目，除非启用了新增的「限制为具有「管理集合」权限的成员可以删项目」选项。[了解更多](admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)有关集合权限的信息。
* **新的集合管理设置**：为了增加权限定制，添加了一个新的集合管理设置：「限制为具有「管理集合」权限的成员可以删项目」选项。[了解更多](admin-console/manage-shared-items/collections/collection-settings.md)有关集合管理设置的信息。

## 2025.5.0

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.5.0、浏览器扩展 2025.5.0）

### Password Manager

* **增强的 PIN 要求**：在浏览器扩展中，用于解锁的 PIN 现在必须至少为 4 个字符。这将在未来的版本中逐步更新到其他客户端。
* **从网页和浏览器导出附件**：在网页 App 和浏览器扩展中，现在可以创建包含文件附件的 `.zip` 导出。这将在未来的版本中逐步添加到其他客户端。[了解更多](your-vault/file-attachments.md)。
* **搜索结果中的嵌套集合**：嵌套集合现在包含在搜索结果中，使查找相关项目变得更容易。[了解更多](admin-console/manage-shared-items/collections/about-collections.md)有关集合的信息。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **组织功能预览**：团队、家庭和免费组织的管理控制台现在将显示更高订阅层级所含功能的预览。

## 2025.4.3

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.4.1、浏览器扩展 2025.4.0、桌面端 2025.4.2、CLI 2025.4.0）

此次发布包含：

### Password Manager

* **设备批准时浏览器扩展中的持久性**：现在，即使您点击退出或最小化扩展程序窗口以使用网页 App 批准请求，浏览器扩展程序也会等待最多两分钟才能获得批准。
* **桌面端主密码重新提示更新**：当某个项目的主密码重新提示选项处于活动状态时，桌面 App 现在会将所有字段（而不仅仅是隐藏的字段）置于成功验证之后。[了解更多](your-vault/vault-items.md#protect-individual-items)。
* **移动 App 的高级故障排除**：在移动 App 中，打开飞行记录器以本地临时记录 App 事件，以帮助排除 Bitwarden App 中的意外行为。[了解更多](password-manager/more/yu-bitwarden-zhi-chi-pai-chu-yi-dong-duan-gu-zhang.md)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **外部 ID 显示更新**：外部 ID 现在只有在通过 SCIM、Bitwarden Directory Connector 或 API 配置后，才会显示在群组、集合和成员对话框中。了解更多有关 [Directory Connector](admin-console/manage-members/directory-connector/about-directory-connector.md) 的信息。
* **成员 SSO 外部 ID**：对于配置为使用 SSO 的成员，成员 SSO 外部 ID 将显示在成员对话框中。

## 2025.4.0

此次发布包含：

### Password Manager

* **Edge 导出 (csv)**：Edge (csv) 导出已添加到可导入 Bitwarden Password Manager 的格式列表中。[了解更多](password-manager/import-and-export/import-data.md)。

## 2025.3.3

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.3.1、浏览器扩展 2025.3.2、桌面端 2025.3.2、CLI 2025.3.0）

此次发布包含：

### Password Manager

* **浏览器扩展筛选器持久性**：为了在浏览器扩展和网页之间导航时获得更好的体验，搜索条件和筛选器现在可持续两分钟，或者直到您更改浏览器扩展中的活动选项卡。
* **浏览器扩展的加载时间**：我们进行了几项改进，以改善浏览器扩展的加载时间。[了解更多](getting-started/getting-started-browserext.md)有关 Bitwarden 浏览器扩展的信息。
* **重新排序网站 URI**：在网页 App 和浏览器扩展的「编辑登录」视图中，您现在可以使用拖放 (**≡**) 按钮来重新排序网站 URI，以获得更好的视觉组织效果。
* **Linux 桌面支持 FIDO2 两步登录**：Linux 桌面 App 现在支持使用 FIDO2 通行密钥的两步登录。[了解更多](account/two-step-login/setup-guides/two-step-login-via-fido.md)。
* **SSH 代理转发**：Bitwarden 桌面 App 上 SSH 代理转发的支持已得到改进。[了解更多](password-manager/developer-tools/ssh/ssh-agent.md)有关 Bitwarden SSH 代理的信息。

## 2025.3.0

此次发布包含：

### 我的账户 <a href="#my-account" id="my-account"></a>

* **新设备验证，新账户宽限期**：新创建的账户在创建后的 24 小时内将不受新设备登录保护。[了解更多](account/log-in-and-unlock/new-device-protection.md)。

### Password Manager

* **登录请求横幅通知**：设备登录请求现在会在等待批准期间在网页 App 中显示一个横幅通知。[了解更多](account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)有关设备登录的信息。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **域名验证更名**：面向企业组织的「域名验证」已更名为「声明域名」。[了解更多](admin-console/login-with-sso/claimed-domains.md)。
* **声明账户**：当企业组织声明一个域名时，具有与此域名匹配的电子邮箱的所有成员账户现在也将被组织声明，允许管理员删除账户。被声明的账户还有一些其他账户操作限制。[了解更多](admin-console/oversight-visibility/claimed-domains/claimed-accounts.md)。
* **报告中未分配的项目**：组织拥有的未分配给集合的项目现在会列出互动链接，以便在组织密码库健康状况报告中进一步查看。

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

* **移至 GitHub Container Registry**：容器镜像已从 Docker Hub 移至 GitHub Container Registry。如果您正在使用非 `bitwarden.sh` 或 `bitwarden.ps1` 脚本方法进行部署，请将镜像引用更新为 GitHub Container Registry URL（例如 `ghcr.io/bitwarden/image_name:version`）。

## 2025.2.1

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.2.2、浏览器扩展 2025.2.2、桌面端 2025.2.1、CLI 2025.2.0）

此次发布包含：

### 我的账户 <a href="#my-account" id="my-account"></a>

* **新设备登录保护**：为确保您的账户安全，Bitwarden 将逐步开始要求未使用两步登录或 SSO 的用户进行额外的验证。[了解更多](account/log-in-and-unlock/new-device-protection.md)。
* **恢复密码使用更新**：使用恢复密码时，虽然仍需要您的电子邮箱地址和主密码，但现在将自动登录您的密码库并停用两步登录，而不是仅停用两步登录。[了解更多](account/two-step-login/recovery-codes.md#use-your-recovery-code)。
* **适用于 macOS 桌面的 FIDO2 两步登录**：macOS 桌面 App 现在支持使用 FIDO2 通行密钥的两步登录。[了解更多](account/two-step-login/setup-guides/two-step-login-via-fido.md)。

### Password Manager

* **「点击以自动填充」设置已移动**：浏览器扩展上的「点击以自动填充」设置已移至**设置** → **外观**选项卡。[了解更多](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#zi-ding-yi-zi-dong-tian-chong-xing-wei)。
* **阻止 iOS 上的重复通行密码**：在 iOS 上无法保存与 Bitwarden 密码库中已存储的现有用户名和服务相匹配的重复通行密钥。现有通行密钥可能会被修改或覆盖。[了解更多](password-manager/autofill/more-autofill-options/autofill-passkeys.md#using-passkeys-with-bitwarden)有关创建通行密钥的信息。
* **企业单点登录更新**：在单点登录工作流程的第一步添加了「使用单点登录」按钮，以简化企业单点登录。[了解更多](account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md#login-using-sso)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **「禁用 PIN 码解锁」策略**：企业组织现在可以一个设置策略，禁止成员在客户端 App 中使用 PIN 码解锁。[了解更多](admin-console/oversight-visibility/enterprise-policies.md)。
* **策略不合规变更**：以前因不合规而从组织中删移除成员的策略，现在将改为撤销这些成员的访问权限。[了解更多](admin-console/manage-members/user-management.md#revoke-access)。
* **适用于设备批准请求的电子邮件通知**：每当组织成员提交可信设备批准请求时，管理员现在都会收到一封电子邮件。[了解更多](admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md)。

### 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

* **将现有组织添加到提供商门户**：如果提供商用户也是组织的所有者，现在可以将现有组织添加到提供商门户。[了解更多](provider-portal/get-started-with-provider-portal.md#add-an-existing-organization)。

## 2025.2.0

（所列版本号为 Bitwarden 服务器的版本号，在此周期中发布的其他版本号还包括 Web 2025.2.1）

{% hint style="info" %}
为确保账户安全，在即将发布的版本中，**对于没有使用两步登录的用户**，Bitwarden 将对其要求额外的验证。希望避免新设备验证工作流的用户可以：

* 按照[此页面](account/two-step-login/setup-guides/two-step-login-methods.md)上的任何指南预先设置两步登录。
* 从**设置** → **我的账户** → **危险操作区**界面中退出此功能。

[了解更多](account/log-in-and-unlock/new-device-protection.md)。
{% endhint %}

此次发布包含：

### Password Manager

* **提高了导入项目的限制**：提高了 Password Manager 导入项目的数量限制。[了解更多](password-manager/import-and-export/import-data.md)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **集合权限更新**：
  * **集合权限名称已更新**：更新了集合权限名称，使其更加清晰明了。[了解更多](admin-console/manage-members/member-roles.md#permissions)。
  * **更新「编辑项目、隐藏密码」权限**：为提高安全性，「编辑项目、隐藏密码」权限将不再允许用户将集合中的项目分配到另一个集合。

## 2025.1.2

（版本号为 Bitwarden 网页 App 的版本号，本周期发布的其他版本号分别为服务器 2025.1.4、桌面端 2025.1.4、浏览器扩展 2025.1.3、CLI 2025.1.3、iOS 2025.1.2 和 Android 2025.1.1）

此次发布包含：

### Password Manager

* **更改密码库项目所有者**：在网页 App 上，现在您可以直接从编辑窗口通过将其所有者更改为您所属的任何组织来共享密码库项目。[了解更多](password-manager/vault-basics/organization-members/sharing.md)。
* **屏蔽浏览器扩展的自动填充**：现在可以专门指示浏览器扩展不允许在某些域名上进行自动填充。[了解更多](password-manager/autofill/more-autofill-options/blocking-autofill.md)。
* **移动版 Bitwarden Send 更新**：移动 App 上的 Bitwarden Send 选项已不再支持设置有效期和停用 Send，这与浏览器扩展目前提供的功能一致。在未来的版本中，其他客户端也将停止对这些选项的支持。[了解更多](bitwarden-send/send-lifespan.md)。

### 计划 & 定价 <a href="#plans-and-pricing" id="plans-and-pricing"></a>

* **重启组织订阅**：已终止或失效的 Bitwarden 订阅现在有 7 天的宽限期，用户可以重新激活订阅。了解更多有关[组织续费](plans-and-pricing/organization-renewal.md)的信息。

## 2025.1.1

此次发布包含：

### Password Manager

* **SSH 代理**：Bitwarden 用户现在可以直接使用 Bitwarden Password Manager 安全地存储和生成 SSH 密钥。[了解更多](password-manager/developer-tools/ssh/ssh-agent.md)有关 Bitwarden SSH 代理的信息。
* **使用网页设备批准**：使用网页 App 批准新的受信任设备和设备登录请求。[了解更多](account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)。
* **更新了桌面端的生成器**：桌面 App 上的密码和用户名生成器的用户界面已更新，以反映其他 Bitwarden App 的最新设计。[了解更多](password-manager/vault-basics/generator.md)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **SSO 外部 ID 被添加到公共 API 响应中**：返回组织成员数据的公共 API 响应现在将在适用时包含其 SSO 外部标识符。[了解更多](https://bitwarden.com/help/api/)。

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

* **旧用户加密密钥迁移**：更新到服务器版本 `2025.1.3` 时，自托管服务器将要求具有现有旧加密密钥的用户（通常是 2021 年之前创建的不经常使用网页 App 的账户）登录网页 App 迁移旧加密密钥。

{% hint style="info" %}
受影响的用户将被注销，并被阻止登录非网页 Bitwarden 客户端，直到他们通过登录 Bitwarden 网页 App 完成迁移。**为确保您的用户不会失去服务，Bitwarden 建议：**

1. 尽快将您的自托管服务器升级到版本 `2025.1.0`。
2. 通知用户应在此更新后登录网页 App ，以确保在被 `2025.1.3` **强制执行之前**迁移现有的旧密钥。
3. 在收到通知后的一段时间内，安排将托管服务器升级到版本 `2025.1.3`，以允许用户迁移现有的旧密钥。
{% endhint %}

## 2025.1.0

此次发布包含：

### Password Manager

* **更多自动填充自定义选项**：浏览器扩展现在具有更多选项来自定义您的自动填充体验，包括选择项目卡片而不是「**填充**」按钮来自动填充，以及多个快速复制操作。[了解更多](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#zi-ding-yi-zi-dong-tian-chong-xing-wei)。
* **Snap Store 桌面 App 生物识别解锁**：通过 Snap Store 下载的密码管理桌面 App 现在支持生物识别解锁。[了解更多](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#zhuo-mian-duan)。
* **TOTP 代码的内嵌自动填充**：内嵌自动填充菜单现在可用于选择 TOTP 代码。[了解更多](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#use-the-inline-auto-fill-menu)有关内嵌自动填充菜单的信息。
* **iOS 上长按自动填充**：在 iOS 18+ 上长按任何文本字段即可从 Bitwarden 自动填充。[了解更多](password-manager/autofill/autofill-from/autofill-from-ios.md)。
* **新的公共 API 操作**：`/public/organization/subscription` 端点添加了一个 GET 操作。[了解更多](organizations/bitwarden-public-api.md)有关 Bitwarden 公共 API 的信息。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **移除免费的 Bitwarden 家庭赞助策略**：该策略允许企业组织阻止用户通过他们的组织兑换赞助的家庭计划。[了解更多](plans-and-pricing/password-manager/redeem-families-sponsorship.md)。
* **集成页面**：管理控制台导航菜单中添加了集成页面。集成页面提供了Bitwarden SSO 集成、事件管理等常用的帮助中心链接！

### 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

* **提供商成员不再能导出客户密码库**：为了提高客户组织的安全性和私密性，提供商成员将不再具有导出客户密码库的权限。

## 2024.12.0

{% hint style="info" %}
2025 年，Bitwarden 将开始逐步停止对 FIDO 通用第二因素 (U2F) 密钥的支持，这些密钥可以在网页 App 的**两步登录** → **管理 FIDO2 WebAuthn** 视图中识别为标记为「**迁移自 FIDO**」。如果您目前使用的是已迁移的 U2F 密钥，请移除并重新注册该密钥，以便自动[将其设置为 WebAuthn](account/two-step-login/setup-guides/two-step-login-via-fido.md)。
{% endhint %}

此次发布包含：

### Password Manager

* **浏览器扩展和网页 App 用户界面更新**：重新设计了 Bitwarden Password Manager 浏览器扩展的用户界面，同时包含网页 App 用户界面的一些增强的样式更改。[了解更多](https://bitwarden.com/blog/bringing-intuitive-workflows-and-visual-updates-to-the-bitwarden-browser/)。
* **网页 App 视图项目面板**：网页 App 现在将打开项目到「查看」面板，而不是直接打开「编辑」面板。只有拥有项目编辑权限的用户才能使用「编辑」按钮更改密码库项目。[了解更多](your-vault/vault-items.md)。
* **iOS 18.0+ 自动填充 TOTP 代码**：iOS 18.0（或更新版本）上的 Bitwarden 键盘自动填充功能现在可以在登录表单中自动填充 TOTP 代码。[了解更多](password-manager/autofill/autofill-from/autofill-from-ios.md)有关 iOS 自动填充的更多信息。
* **PasswordXP .csv 导入器**：PasswordXP .csv 已被添加到可导入 Bitwarden Password Manager 的格式列表中。[了解更多](secrets-manager/import-export/import-data.md)。
* **Netwrix Password Secure .csv 导入器**：Netwrix Password Secure .csv 已被添加到可导入 Bitwarden Password Manager 的格式列表中。[了解更多](secrets-manager/import-export/import-data.md)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **适用于团队组织的 SCIM**：团队组织现在可以使用跨域身份管理系统 (SCIM) 自动从源目录配置成员和群组。此前，这仅适用于企业组织。[了解更多](admin-console/manage-members/scim/about-scim.md)。

## 2024.11.0

此次发布包含：

### 我的账户 <a href="#my-account" id="my-account"></a>

* **所有客户端注册期间的电子邮箱验证**：使用任何 Bitwarden 客户端创建新 Bitwarden 账户的用户现在将被要求在创建主密码之前验证其电子邮邮箱。[了解更多](account/create-bitwarden-account.md)。

### Password Manager

* **内联自动填充菜单密码生成**：现在，在填写账户创建或密码更新字段时，可使用内联自动填写菜单轻松生成密码。[了解更多](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md)。
* **支付卡和身份的内联自动填充菜单选项**：您现在可以打开或关闭将支付卡和身份作为建议包含在内联自动填写菜单中的选项。[了解更多](password-manager/autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-the-inline-menu)。
* **iOS 复制和粘贴更新**：Bitwarden iOS 复制和粘贴功能添加了多个更新，以方便使用。
* **改进了非官方服务器的错误处理**：为了帮助使用非官方 Bitwarden 服务器的用户，添加了新的错误消息以帮助识别连接到非官方服务器时的错误。
* **暂时移除桌面 App 上的「允许屏幕捕获」开关**：为改善该功能的使用体验，已暂时移除 macOS 和 Windows 桌面 App 上的该功能。目前，桌面 App 将通过截图和屏幕共享捕获。
* **增加密码短语的最少单词数**：密码短语生成器现在要求生成的密码短语至少包含 6 个单词（移动客户端除外）。[了解更多](password-manager/vault-basics/generator.md#password-types)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **集合管理设置更新**：限制所有者和管理员创建和删除集合的设置已被分离为两个单独的设置，分别用于每种操作。[了解更多](admin-console/manage-shared-items/collections/collection-settings.md#collection-management-settings)有关集合管理的信息。
* **删除集合项目需要「可以管理」权限**：现在删除集合项目需要「可以管理」权限。具有「可以编辑」权限的用户不再具有该权限。[了解更多](admin-console/manage-members/member-roles.md#permissions)有关成员权限的信息。

## 2024.10.4

此次发布包含：

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **限制对 `bw list org-members` 命令的访问**：此命令以及 Vault Management API 中的等效端点现在仅限于所有者、管理员和具有「管理用户」权限的自定义用户。

### 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

* **计费系统迁移**：从本月开始，现有的提供商将开始迁移到更新的客户组织计费系统。[了解更多](provider-portal/provider-billing.md)。

## 2024.10.2

此次发布包含：

### 我的账户 <a href="#my-account" id="my-account"></a>

* **注册期间的电子邮箱验证**：通过网页 App 创建 Bitwarden 账户的用户现在将被要求在创建主密码之前验证其电子邮箱。[了解更多](account/create-bitwarden-account.md)。

### Password Manager

* **使用生物识别解锁 - Linux 浏览器扩展**：Linux 用户现在可以在基于 Chromium 的浏览器上使用 Bitwarden 浏览器扩展的生物识别解锁功能。[了解更多](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#enable-unlock-with-biometrics)。
* **桌面 App 阻止屏幕捕获**：默认情况下，Windows 和 macOS 的桌面 App 现在将阻止屏幕捕获和录制。[了解更多](getting-started/getting-started-desktop.md#xia-yi-bu)。
* **在桌面端同步锁定的密码库**：即使活动账户被锁定，桌面 App 现在也可以手动同步。[了解更多](your-vault/syncing-your-vault.md#manual-sync)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **Microsoft Sentinel 集成**：新的本地集成可用于 Microsoft Sentinel 安全信息和事件管理 (SIEM)。该集成提供了跨身份验证、组织活动和密码库项目的全面事件覆盖。[了解更多](admin-console/oversight-visibility/siem-integrations/microsoft-sentinel-siem.md)。
* **Ping Identity SCIM 支持**：Bitwarden 组织现已正式支持 Ping Identity 跨域身份管理 (SCIM) 系统。使用 Ping Identity SCIM 集成来自动配置 Bitwarden 组织中的成员和群组。[了解更多](admin-console/login-with-sso/implementation-guides/ping-identity-saml-implementation.md)。
* **UI 改进升级计划**：为简化将您的组织升级到另一个计划的流程，对 UI 进行了改进。[了解更多](admin-console/organizations-overview.md#upgrade-an-organization)。
* **为允许的应用程序策略自动登录用户**：这项新策略将允许 IdP 管理员启用非 SSO 应用程序，以便在从其 IdP 面板启动时自动登录用户。[了解更多](admin-console/oversight-visibility/enterprise-policies.md#automatically-log-in-users-for-allowed-applications)。

## 2024.9.2

此次发布包含：

### Password Manager

* **现在，网页 App 默认将下载 PDF 附件**：作为项目附件存储的 PDF 将下载到您的设备上进行查看，而不是在新的浏览器选项卡中打开。[了解更多](your-vault/file-attachments.md)。

### Secrets Manager

* **新的机器账户视图**：机器账户有一个新的**配置**选项卡，可以快速查看配置应用程序以使用机器账户时可能需要的信息。[了解更多](secrets-manager/your-secrets/machine-accounts.md#configuration-information)。

## 2024.9.1

此次发布包含：

### Password Manager

* **通行密钥的内联自动填充菜单**：使用内联自动填充菜单通过通行密钥进行身份验证。[了解更多](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#use-the-inline-auto-fill-menu)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **成员访问报告**：企业组织可使用成员访问报告来监控组织成员对群组、集合和项目的访问情况。[了解更多](your-vault/vault-health-reports.md#member-access)。
* **移除用户事件的修复**：现在可以正确记录通过公共 API 或目录连接器移除用户的事件。

## 2024.8.2

此次发布包含：

### Password Manager

* **iOS 原生移动 App**：通过 Apple App Store 下载的 Password Manager 移动 App 已升级为原生移动应用程序。[了解更多](miscellaneous/native-mobile-apps.md)。
* **用于密码保护导出的密码生成器**：Bitwarden 现在可以为受密码保护的导出生成唯一密码。[了解更多](import-export/encrypted-exports.md#create-an-encrypted-export)有关密码保护导出的更多信息。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **Rapid7 SIEM 集成**：Bitwarden 组织现在可以使用 Rapid7 进行安全信息和事件管理 (SIEM)。[了解更多](admin-console/oversight-visibility/siem-integrations/rapid7-siem.md)。

## 2024.8.0

{% hint style="info" %}
在未来的发布中，通过 Apple App Store 和 Google Play Store 下载的 Password Manager 移动 App 将升级为原生移动 App。[了解更多](miscellaneous/native-mobile-apps.md)。
{% endhint %}

此次发布包含：

### Password Manager

* **自动填充支付卡和身份**：现在可以使用其他自动填充方式填充支付卡和身份：
  * 使用键盘快捷键自动填充支付卡和身份。[了解更多](password-manager/autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-keyboard-shortcuts)。
  * 使用内嵌自动填充菜单填充支付卡和身份。[了解更多](password-manager/autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-the-inline-menu)。
* **使用生物识别解锁 Linux 桌面 App**：使用 Polkit 的 Linux 用户现在可以在 Bitwarden 桌面 App 上使用生物识别解锁功能。[了解更多](getting-started/getting-started-desktop.md#linux)。

### Secrets Manager

* **显示机器账户、工程和机密的总数**：Secrets Manager 导航栏现在将显示您有权访问的机器账户、工程和机密的总数。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **更改成员解密选项时的其他支持选项**：如果您的组织从受信任设备 SSO 迁移到主密码解密，系统将在用户下次登录时提示创建主密码，而不是要求管理员事先分配主密码。[了解更多](admin-console/login-with-sso/trusted-devices/about-trusted-devices.md#impact-on-master-passwords)。

### 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

* **UI 改进**：「人员」页面已重命名为「成员」页面，提供商门户的配色方案也已更改为以与管理控制台匹配。

## 2024.7.3

此次发布包含：

### Secrets Manager

* **新的 Secrets Manager 登录页面**：快速了解有关 Secrets Manager 的更多信息并直接从网页 App 注册该产品。[了解更多](secrets-manager/get-started/secrets-manager-quick-start.md)。

### 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

* **限制提供商对密码库项目的访问**：为了提高客户的安全性和隐私性，提供商用户可能不再直接查看、管理或创建客户组织的保管库中的项目。但是，提供商用户可以将库数据直接导入到客户组织。

## 2024.7.2

此次发布包含：

### 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

* **新提供商的合并计费**：在此版本之后加入 Bitwarden 的提供商的计费程序现已简化，并仅通过提供商门户进行管理。现有提供商将在未来版本中迁移到新的计费系统。[了解更多](provider-portal/provider-portal-overview.md)。

## 2024.7.1

此次发布包含：

### Password Manager

* **移除通行密钥用户验证**：最近的更新要求在浏览器扩展上使用通行密钥时进行用户验证，该更新已暂时回退。
* **启用了 PRF 的通行密钥将在账户加密密钥轮换后继续有效**：如果用户轮换了他们的账户加密密钥，使用通行密钥登录 Bitwarden 时使用的 PRF 密钥现在继续有效。[了解更多](security/encryption/encryption-key-rotation.md#rotate-your-encryption-key)。
* **紧急联系人和提供商的邀请说明**：受信任的紧急联系人和提供商用户在接受邀请后，现在将进入「需要确认」状态，使您的下一步操作更清晰。
* **批量分配项目到集合**：现在，您可以从密码库视图中将项目批量分配到组织的集合中。此功能的前一版本称为「移动到组织」。[了解更多](your-vault/vault-items.md#assign-to-collections)。
* **重命名将项目添加到文件夹**：在密码库视图中，将项目添加到文件夹的选项已从「移动所选」重命名为「添加到文件夹」。[了解更多](your-vault/folders.md#move-items-to-a-folder)。
* **弃用桌面 App 设置**：桌面应 App 现在默认可以批准设备登录。[了解更多](account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)。
* **改进的 SSO 标识符工作流程**：管理员现在可以分发企业单点登录界面的 URL，并将其 SSO 标识符作为查询参数包含在内，以自动将组织成员重定向到 IdP，从而获得更简化的 SSO 体验。[了解更多](login-with-sso/login-with-sso-faqs.md#q-do-i-need-to-enter-my-organization-identifier-every-time-i-login)。

### Secrets Manager

* **添加对机密的直接访问权限**：现在可以直接授予人员和机器账户对机密的访问权限，而不需要项目作为中介。[了解更多](secrets-manager/your-secrets/secrets.md)。

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

{% hint style="info" %}
用户应在 2024.10.x 版本之前将自托管服务器至少升级到此版本，以确保与使用密码库项目密钥的客户端兼容。
{% endhint %}

* **支持批量设备批准**：自托管 Bitwarden 服务器现在支持用于受信任设备 SSO 的批量设备批准。[了解更多](admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md#bulk-approve-requests)。

### 安全 <a href="#security" id="security"></a>

* **密码库项目秘钥**：添加了额外的加密层，其形式是为每个单独的密码库项目生成新的加密密钥。[了解更多](security/bitwarden-security-whitepaper.md#how-vault-data-is-encrypted)。

### 计划 & 定价 <a href="#plans-and-pricing" id="plans-and-pricing"></a>

* **按月计费的组织账单更新**：按月计费的团队和企业组织将看到按比例分配的席位数调整包含在下一次生成的月度账单中，而不是在席位数变化时新生成的账单中。
* **按年计费的组织账单更新**：按年计费的团队和企业组织将看到按比例分配的席位数调整包含在每月一次的调整账单中，而不是在席位数变化立即生成的单独账单中。

## 2024.6.3

此次发布包含：

### Password Manager

* **批量批准可信任设备 SSO**：管理员和所有者现在可以使用[网页 App](admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md#bulk-approve-requests) 或 [CLI](password-manager/developer-tools/cli/password-manager-cli.md#device-approval) 批量批准可信设备请求。
* **陈旧的用户加密密钥迁移**：2021 年之前创建的 Bitwarden 账户已将其账户加密密钥迁移到 Bitwarden 的更现代化的用户对称密钥。这些用户将被从非网页 Bitwarden 客户端注销，直到他们通过登录 Bitwarden 网页客户端完成迁移。[了解更多](security/encryption/encryption-protocols.md)有关 Bitwarden 加密的信息。

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

* **支持更多集合管理选项**：自托管 Bitwarden 服务器现在支持**所有者和管理员可以管理所有集合和项目**集合管理选项。[了解更多](admin-console/manage-shared-items/collections/collection-settings.md)。

## 2024.6.1

此次发布包含：

### Password Manager

* **集合管理更新**：添加了集合管理选项，允许您决定是否自动向管理员和所有者提供对组织中所有集合及其项目的管理权限。[了解更多](admin-console/manage-shared-items/collections/collection-settings.md)。

## 2024.6.0

此次发布包含：

### Password Manager

* **通行密钥用户验证**：当使用存储的通行密钥登录时，浏览器扩展现在可能会提示用户使用生物识别、PIN 或主密码进行验证。[了解更多](password-manager/autofill/more-autofill-options/autofill-passkeys.md#liu-lan-qi-kuo-zhan)。
* **产品内入门**：Password Manager 的新用户现在将看到一个入门模块，以帮助他们快速开始保护凭据。
* **浏览器扩展设置重组**：使用浏览器扩展上新重组的设置界面可以快速定位和修改浏览器扩展设置。
* **Firefox 扩展在隐私窗口中获得完整功能**：在 Firefox 隐私窗口中使用 Bitwarden 浏览器扩展不再有任何限制。[了解更多](miscellaneous/use-bitwarden-in-firefoxs-private-mode.md)。
* **增加产品切换器的位置**：用于在 Password Manager、管理控制台、Secrets Manager 和提供商门户之间切换的产品切换器现在也可以在导航的左下角找到。
* **浏览器扩展和桌面端的密码保护导出**：浏览器扩展和桌面端应用程序现在可以导出受密码保护的加密导出。[了解更多](import-export/encrypted-exports.md#create-an-encrypted-export)。

### Bitwarden Authenticator

* **导入到 Bitwarden Authenticator**：将数据从 Google Authenticator、LastPass Authenticator、Raivo 以及 2FAS 等其他各种身份验证 App 直接导入到 Bitwarden Authenticator。[了解更多](bitwarden-authenticator/import-and-export.md)。

### Secrets Manager

* **开始 Secrets Manager 试用**：开始 Secrets Manager 企业版试用，以测试概念验证，并获得对 SSO 和 SCIM 集成、企业策略、自托管、事件日志和优先级支持等企业功能。[立即注册 Secrets Manager 7 天免费试用](https://vault.bitwarden.com/#/register?org=enterprise\&layout=secretsManager)。
* **Secrets Manager Kubernetes Operator (beta)**：使用 Bitwarden Secrets Manager Kubernetes Operator 安全高效地将 Secrets Manager 集成到 Kubernetes 工作流中。[了解更多](secrets-manager/integrations/secrets-manager-kubernetes-operator.md)。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **集合管理更新**：添加了一个集合管理选项，允许您决定是否自动向管理员和所有者提供对组织中所有集合及其中的项目的管理权限。[了解更多](admin-console/manage-shared-items/collections/collection-settings.md)。
* **通过 API 配置自定义用户**：现在可以通过公共 API 配置组织成员的自定义角色权限。[了解更多](https://bitwarden.com/help/api/)。

## 2024.5.0

此次发布包含：

### Password Manager

* **从我的密码库克隆组织项目**：具有「可以管理」权限的用户现在可以从其密码库视图克隆组织所拥有的项目。[了解更多](your-vault/vault-items.md#clone)。
* **浏览器扩展平台升级**：从本周开始，Password Manager 浏览器扩展将开始逐步升级到名为 Manifest V3 的新扩展平台，从 1% 的用户开始，并在整个 5 月份逐步增加。不论是启动此升级或完成升级后，您都无需采取任何行动。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **Splunk Cloud 集成**：Bitwarden 事件日志 App 可用于 Splunk Cloud Classic 和 Splunk Cloud Victoria 上的信息和事件管理。[了解更多](admin-console/oversight-visibility/siem-integrations/splunk-siem.md)。

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

* **集合管理和弃用经理角色**：自托管服务器现在可以访问集合管理功能，具有「经理」角色的用户将迁移到具有新的「可以管理」权限的「用户」角色。[了解更多](admin-console/manage-shared-items/collections/collection-settings.md)。

{% hint style="info" %}
如果是自托管，请在云端组织中设置[集合管理设置](admin-console/manage-shared-items/collections/collection-settings.md)，然后[更新自托管服务器的许可证](self-hosting/licensing.md#update-organization-license)以将这些设置转移到您的自托管组织。
{% endhint %}

## 2024.4.2

此次发布包含：

### Password Manager

* **在移动 App 上使用通行密钥**：Password Manager 移动 App 现在可以使用通行密钥创建和登录。此功能适用于 iOS 系统，Android 系统为测试版。[了解更多](password-manager/autofill/more-autofill-options/autofill-passkeys.md)。
* **删除已存储的通行密钥**：现在可以使用 Bitwarden 浏览器扩展和桌面 App 删除存储在 Bitwarden 登录项目中的通行密钥。[了解更多](password-manager/autofill/more-autofill-options/autofill-passkeys.md)。

### Secrets Manager

* **新的集成页面**：通过 Secrets Manager 网页 App 中的新页面快速访问 Secrets Manager 集成。
* **Secrets Manager CLI Docker 映像**：Bitwarden Secrets Manager CLI 现在已作为 Docker 镜像的形式提供。[了解更多](secrets-manager/developer-tools/secrets-manager-cli.md)。

## Bitwarden Authenticator

介绍全新的 Bitwarden Authenticator 独立移动 App。使用 Bitwarden Authenticator 生成用于 App 和网站双因素身份验证的验证码。从应用商店下载或[了解更多](bitwarden-authenticator/bitwarden-authenticator.md)。

## 2024.4.1

此次发布包含：

### Password Manager

* **删除存储的通行密钥**：现在可以从 Bitwarden 网页 App 的**密码库项目** → **编辑**界面中删除存储在 Bitwarden 登录项目中的通行密钥。[了解更多](password-manager/autofill/more-autofill-options/autofill-passkeys.md#delete-vault-item-passkey)。

### Secrets Manager

* **「服务账户」现在为「机器账户」**：服务账户已重命名为机器账户。

## 2024.3.1

{% hint style="success" %}
[最近迁移到新的权限结构](admin-console/manage-shared-items/collections/collection-settings.md#collection-management-settings)，为您的组织带来了更大的集合管理灵活性，未分配给[集合](admin-console/manage-shared-items/collections/about-collections.md)的密码库项目现在不再显示在您的 Password Manager 的**所有密码库**视图中了。[了解如何访问这些项目](miscellaneous/unassigned-vault-items-moved-to-admin-console.md)。
{% endhint %}

此次发布包含：

### Password Manager

* **Bitwarden App 可使用新的语言**：在社区翻译人员的贡献下，Bitwarden App 现在提供了新的语言选项！[点击这里](password-manager/more/localization.md)查看完整的语言列表。[了解更多](https://contributing.bitwarden.com/contributing/#localization-l10n)关于 Bitwarden 本地化的信息。
* **桌面 App 硬件加速**：Bitwarden 桌面 App 现在可以选择打开或关闭硬件加速以优化性能。该设置默认启用。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **批量将项目分配到集合**：从管理控制台可以将组织项目批量分配到集合。[了解更多](admin-console/manage-shared-items/collections/about-collections.md#collections-ji-he-storing-passkeys-cun-chu-mi-ma-vault-administration-import-export-autofill-bitward)。

## 2024.3.0

此次发布包含：

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

* **适用于 Linux 部署的新的日志功能**：使用标准 `bitwarden.sh` shell 脚本的 Linux 部署现在可以使用新选项来下载压缩日志文件（参阅[这里](self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#script-commands-reference)）。

## 2024.2.3

此次发布包含：

### Password Manager

* **网页 App 导航更新**：Bitwarden 网页 App 已完全重新设计！我们希望您能喜欢这个新的体验（[了解更多](https://bitwarden.com/blog/bitwarden-design-updating-the-navigation-in-the-web-app/)）。
* **Duo 2FA 登录更新**：Duo 为用户和管理员引入了通用提示。启用该服务的 Duo 管理员会发现 Duo 2FA 登录流程稍微有一些变化（参阅[这里](account/two-step-login/setup-guides/two-step-login-via-duo.md)）。

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

* **支持使用通行密钥登录 (Beta)**：自托管 Bitwarden 服务器现在支持使用通行密钥登录功能（参阅[这里](account/log-in-and-unlock/more-log-in-options/log-in-with-passkeys.md)）。

## 2024.2.2

此次发布包含：

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **适用于终端用户的集合管理**：组织现在可以选择允许所有用户创建和管理他们自己的集合。此选项位于 **组织信息**界面，现有组织可选择加入，2024.2.2 之后创建的组织可选择退出（参阅[这里](admin-console/manage-shared-items/collections/collection-settings.md)）。
* **弃用经理角色**：开启集合管理后，具有**经理**角色的组织用户将被迁移到**用户**角色，并获得对其分配的集合进行管理的新权限（参阅[这里](admin-console/manage-members/member-roles.md)）。

### Secrets Manager

* **Ansible 集成**：使用 Bitwarden Secrets Manager 检索机密并将其注入您的 playbook 剧本中（参阅[这里](secrets-manager/integrations/ansible.md)）。

## 2024.2.0

此次发布包含：

### Password Manager

* **浏览器扩展的 TOTP 捕获**：使用 Bitwarden 浏览器扩展扫描网页并保存 TOTP 验证器二维码（参阅[这里](your-vault/totp.md#scan-a-qr-code)）。
* **增加导入项目数量上限**：Bitwarden Password Manager 的导入相对之前，现在可以包含大约两倍的数据量（参阅[这里](password-manager/import-and-export/import-data.md)）。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **组织唯一的 SP 实体 ID**：使用 SSO SAML 的组织现在可以升级其实体 ID，升级后的实体 ID 对于其组织来说是唯一的。这样做需要在 IdP 上重新配置（参阅[这里](login-with-sso/saml-2.0-configuration.md)）。

### 计划 & 定价 <a href="#plans-and-pricing" id="plans-and-pricing"></a>

* **自动税率计算**：用于订阅的税率现在将由我们的支付分包商根据地理位置自动计算。Bitwarden 收取的小计将保持不变，但您可能会注意到您的含税月度账单将有所变化。

## 2024.1.2

此次发布包含：

### Password Manager

* **适用于自托管的通行密钥存储**：现在可以将通行密钥存储在自托管的 Bitwarden 服务器中（参阅[这里](password-manager/autofill/more-autofill-options/autofill-passkeys.md)）。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **通过公共 API 获得更多集合权限**：现在，您可以使用公共 API 向用户隐藏任意集合的密码（参阅[这里](https://bitwarden.com/help/api/)）。

## 2024.1.0

此次发布包含：

### 我的账户 <a href="#my-account" id="my-account"></a>

* **使用通行密钥登录 (Beta)**：通行密钥可以作为使用主密码和电子邮件的替代方法来登录 Bitwarden 网页 App （参阅[这里](account/log-in-and-unlock/more-log-in-options/log-in-with-passkeys.md)）。

### Password Manager

* **浏览器扩展程序的账户切换**：使用 Bitwarden 浏览器扩展程序时，最多可登录 5 个账户并在这些账户之间无缝切换（参阅[这里](account/log-in-and-unlock/more-log-in-options/account-switching.md)）。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **通过公共 API 配置订阅**：使用新的公共 API 端点来配置订阅信息，例如席位数、最大自动扩展和存储（参阅[这里](https://bitwarden.com/help/api/)）。
* **更多组织升级路径**：更多 Bitwarden 组织现在可以升级到不同的订阅，而无需联系支持人员。

## 使用 Helm GA 自托管 <a href="#self-host-with-helm-ga" id="self-host-with-helm-ga"></a>

Bitwarden 现在可以使用 Helm Chart 在 Kubernetes 部署中自托管（参阅[这里](self-hosting/deploy-and-configure/helm/self-host-with-helm.md)）。

## 2023.12.1

此次发布包含：

### Password Manager

* **自动填充菜单**：通过打开新的内联自动填充菜单，在浏览网页时自动填充凭据（参阅[这里](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#inline-auto-fill-menu)）。

## 2023.12.0

此次发布包含：

### Password Manager

* **关闭使用通行密钥提示的选项**：您现在可以选择浏览器扩展是否要求保存和使用通行密钥（参阅[这里](password-manager/autofill/more-autofill-options/autofill-passkeys.md#turn-off-passkey-prompt)）。
* **移动设备上的 ForwardEmail 支持**：移动 App 上的用户名生成器的转发电子邮件别名提供程序现在支持 ForwardEmail（参阅[这里](password-manager/vault-basics/generator.md#generate-a-username)）。
* **密码库健康报告更新**：组织成员现在可以在个人密码库健康报告中看到自己拥有**可编辑**权限的组织拥有的项目。

### 管理控制台 <a href="#admin-console" id="admin-console"></a>

* **Elastic 集成**：Bitwarden 组织现在可以使用 Elastic 进行安全信息和事件管理 (SIEM)（参阅[这里](admin-console/oversight-visibility/siem-integrations/elastic-siem.md)）。
* **CLI 事件日志**：从网页 App 查看的事件日志现在会指明哪些事件是由 Bitwarden CLI 记录的。

## 2023.10.0

此次发布包含：

### Password Manager

* **保存通行密钥到您的密码库**：现在可以将通行密钥存储在您的 Bitwarden 密码库中了！使用 Bitwarden 浏览器扩展存储并使用通行密钥登录（参阅[这里](password-manager/autofill/more-autofill-options/autofill-passkeys.md)）。
* **LastPass 直接导入器**：使用浏览器扩展或桌面 App 将数据从 LastPass 直接导入到 Bitwarden（参阅[这里](password-manager/import-and-export/import-guides/import-data-from-lastpass.md#import-to-bitwarden)）。
* **从浏览器扩展和桌面 App 导入**：现在可以从浏览器扩展和桌面 App 将数据导入到 Bitwarden，包括如果您是使用 LastPass SSO 的团队成员（参阅[这里](password-manager/import-and-export/import-data.md)）。
* **移动端设置重组**：移动 App 上的「设置」选项卡已重新组织为更直观的类别。
* **支持自托管别名提供程序**：Password Manager 客户端上的用户名生成器现在可以连接到自托管 Addy.io 和 SimpleLogin 实例（参阅[这里](password-manager/vault-basics/generator.md#simplelogin)）。
* **通过上下文菜单自动填充支付卡和身份**：现在可以使用浏览器扩展的上下文菜单自动填充支付卡和身份（参阅[这里](password-manager/autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-the-context-menu)）。

### Secrets Manager

* **支持自托管**：企业组织现在可以自行托管 Secrets Manager（参阅[这里](secrets-manager/get-started/manage-your-organization.md#zi-tuo-guan)）。
* **全新的事件日志视图**：现在可以直接从服务账户视图访问服务账户事件日志（参阅[这里](secrets-manager/your-secrets/machine-accounts.md#service-account-events)）。

## 2023.9.0

此次发布包含：

* **FIDO2 WebAuthn 现已成为免费的两步登录选项**：用于两步登录的 FIDO2 WebAuthn 方法已扩展到免费账户。现在，所有 Bitwarden 用户都可以使用兼容的 FIDO2 WebAuthn 凭证（如那些与硬件安全钥匙绑定的设备）来提高登录的安全性（参阅[这里](account/two-step-login/setup-guides/two-step-login-via-fido.md)）。
* **组织成员电子邮件验证**：当组织成员[接受加入邀请](admin-console/manage-members/user-management.md#accept)时，或如果他们是使用[域验证](admin-console/login-with-sso/claimed-domains.md)的组织成员，他们的电子邮件将自动通过验证。
* **导出更新**：密码库数据的 JSON 导出现在将包括适用项目的密码历史记录（参阅[这里](import-export/export-vault-data.md)）。
* **CLI 密码生成器选项**：使用 CLI 生成密码时增加了自定义密码复杂度的选项标志（参阅[这里](password-manager/vault-basics/generator.md#cli)）。
* **ProtonPass JSON 导入器**：ProtonPass JSON 已添加到可用于直接导入 Bitwarden Password Manager 的格式列表中（参阅[这里](import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)）。
* **桌面 App 主题更新**：桌面 App 的暗色主题已更新！

## 2023.8.2

此次发布包含：

* **受信任设备 SSO**：受信任设备 SSO 允许用户使用 SSO 进行身份验证，以及使用存储的加密密钥解密其密码库，而无需输入主密码（参阅[这里](admin-console/login-with-sso/trusted-devices/about-trusted-devices.md)）。
* **经理集合访问权限**：为了降低对非必要数据的可见性，经理现在只能查看分配给他们的集合。

## 2023.8.0

此次发布包含：

* **Secrets Manager - 全面上市**：Bitwarden Secrets Manager 现已全面上市，使开发人员、DevOps 和网络安全团队能够大规模集中存储、管理、自动化和部署机密。了解有关 [Secrets Manager 计划](plans-and-pricing/secrets-manager/secrets-manager-plans.md)和[注册](plans-and-pricing/secrets-manager/sign-up-for-secrets-manager.md)的更多信息。
* **导入到文件夹或集合**：从**工具** → **导入数据**界面，将数据直接导入到现有文件夹，或者如果您是组织成员，将数据直接导入到集合。

## 2023.7.1

此次发布包含：

* **Secrets Manager - CLI 更新**：添加了用于编辑和创建工程和机密的新命令，并且 CLI 使用的语法已重新构建（参阅[这里](secrets-manager/developer-tools/secrets-manager-cli.md)）。
* **EU（欧盟）云**：带有密码库数据存储的 Bitwarden 云服务器现已在欧盟提供（参阅[这里](security/server-geographies.md)）。

## 2023.7.0

此次发布包含：

* **用于自托管的设备登录**：连接到自托管服务器的 Bitwarden 应用程序现在可以通过向已注册设备发送身份验证请求来登录，而不是使用主密码（参阅[这里](account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)）。
* **Forward Email 别名集成**：将 Bitwarden 用户名生成器连接到 [Forward Email](https://forwardemail.net/)，以便轻松创建电子邮件别名（参阅[这里](password-manager/vault-basics/generator.md#username-types)）。
* **浏览器扩展 TOTP 自动填充**：浏览器扩展现在将自动填充 TOTP 代码，除非您使用了在页面加载时自动填充功能（参阅[这里](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#totp-auto-fill)）。
* **在 \<textarea> 中使用自动填充**：Bitwarden App 现在可以将凭据自动填充到 HTML 的 `<textarea>` 元素中。
* **从密码库页面创建文件夹和集合**：现在可以从主**密码库**页面使用**新建**按钮创建文件夹和集合。

### 机密管理器 Beta <a href="#secrets-manager-beta" id="secrets-manager-beta"></a>

此次发布包含：

* **Secrets Manager - 服务账户写入权限**：现在服务账户可以被授予对工程和机密的写入权限（参阅[这里](secrets-manager/your-secrets/machine-accounts.md)）。
* **Secrets Manager - 批量用户管理**：现在可以将组织成员批量添加到 Secrets Manager（参阅[这里](secrets-manager/get-started/secrets-manager-quick-start.md#give-members-access)）。

{% hint style="success" %}
服务账户的写​​入访问权限的充分利用取决于即将发布的 [CLI](secrets-manager/developer-tools/secrets-manager-cli.md) 版本。目前，这只是在 UI 中提供了此选项。请继续关注[发行说明](release-notes.md)以获取更多信息。
{% endhint %}

## 2023.5.0

{% hint style="danger" %}
从 **2023.5.0** 版本开始，Password Manager 桌面 App 将不再支持 Windows 8.1 及更早版本或 Windows Server 2012 及更早版本。

这些操作系统的用户可以在[此处](https://github.com/bitwarden/clients/releases)下载 2023.4.0 桌面 App，并且必须禁用自动更新（在[此处](your-vault/general-faqs.md#q-can-i-turn-off-automatic-updates-for-bitwarden)了解更多信息）。我们建议升级到受支持的操作系统，因为 Bitwarden 云服务器不能保证长期支持旧的客户端版本，并且将来可能会给您带来安全风险。
{% endhint %}

此次发布包含：

* **环境选择器**：改进了将 Bitwarden App 连接到自托管服务器的工作流程。参阅[这里](self-hosting/connect-clients/connect-individual-clients.md)。
* **Password Manager - 改进了德语 HTML 的自动填充**：德语 HTML 字段现在可用于自动填充。参阅[这里](https://github.com/bitwarden/clients/pull/4210)。
* **Secrets Manager - 在机密创建期间创建工程**：您现在可以在机密创建菜单中创建新的工程。参阅[这里](secrets-manager/your-secrets/secrets.md)。
* **自托管 - 阐明有关服务器许可证的措辞**：有 60 天的宽限期来上传新许可证以替换过期的许可证。参阅[这里](self-hosting/licensing.md#update-organization-license)。
* **低 KDF 警告**：当用户的 KDF 迭代次数低于行业建议值（目前为 600,000 次迭代）时，网页 App 中将出现一个新的警告。参阅[这里](security/encryption/encryption-key-derivation.md#low-kdf-iterations)。

### 机密管理器 Beta <a href="#secrets-manager-beta" id="secrets-manager-beta"></a>

此次发布包含：

* **Secrets Manager - 在创建机密期间创建工程**：您现在可以在机密创建菜单中创建新的工程。参阅[这里](secrets-manager/your-secrets/secrets.md)。

## 2023.4.0

此次发布包含：

* **Splunk 集成**：Bitwarden 组织现在可以使用自托管的 Splunk Enterprise 进行安全信息和事件管理 (SIEM)。在[此处](admin-console/oversight-visibility/siem-integrations/splunk-siem.md)了解如何开始使用 Splunk。
* **改进的经销商计费**：Bitwarden 经销商现在是唯一有权查看其客户组织的计费、订阅或付款信息的实体。参阅[这里](plans-and-pricing/bitwarden-resellers.md)。
* **主密码要求策略更新**：如果启用，主密码要求策略现在可以设置为提示现有的不合规用户更新他们的主密码。参阅[这里](admin-console/oversight-visibility/enterprise-policies.md#master-password-requirements)。
* **密码库超时策略更新**：密码库超时策略现在提供了指定密码库超时动作的选项。参阅[这里](admin-console/oversight-visibility/enterprise-policies.md#vault-timeout)。
* **桌面端 - 新的生物识别选项**：您现在可以选择是在 App 启动时要求主密码还是在打开时允许生物识别。参阅[这里](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
* **桌面端 - Windows Hello 安全改进**：解决了与 Windows Hello 和 Windows Credential Manager 相关的漏洞。作为一项附加措施，我们建议使用新选项以在 App 启动时要求输入主密码。参阅[这里](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
* **浏览器扩展 - 改进的表单检测**：改进了表单检测的逻辑，并针对浏览器扩展的通知栏解决了错误报告。有关技术细节，请参阅[这里](https://github.com/bitwarden/clients/pull/4798)。

## 2023.3.0

此次发布包含：

* **域验证**：组织可以验证域（例如 `mycompany.com`）的所有权，允许用户在使用 SSO 登录时跳过组织标识符步骤。参阅[这里](admin-console/login-with-sso/claimed-domains.md)。
* **浏览器扩展 - 改进的自动填充安全性**：浏览器扩展现在不允许在页面加载时自动填充不受信任的 iframe。浏览器扩展还会在手动自动填充、使用上下文菜单或使用键盘快捷键时警告用户有关不受信任的 iframe，并在自动填充 HTTP 站点时警告用户，该站点需要基于该项目的已保存 URI 的 HTTPS。参阅[这里](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md)。
* **主密码安全性检查**：用户现在可以在创建账户或在网页密码库上更改主密码时通过 Have I Been Pwned 检查已知的数据泄露，以查找他们预期的主密码。参阅[这里](your-vault/vault-health-reports.md#data-breach-report-individual-vaults-only)。
* **主密码长度要求**：现在主密码的长度必须至少为 12 个字符。此规则将对新的 Bitwarden 账户和[更改主密码](account/log-in-and-unlock/your-master-password.md#change-your-master-password)的任何用户强制执行。
* **激活自动填充策略**：对于企业组织，激活自动填充策略将自动为组织的新成员和现有成员打开页面加载时的自动填充。参阅[这里](admin-console/oversight-visibility/enterprise-policies.md#activate-auto-fill)。
* **浏览器扩展 - 改进的通知栏**：用于将未检测到的项目添加到您的密码库的通知栏现在为遵守删除单个密码库策略的用户提供了更直观的工作流程。参阅[这里](getting-started/getting-started-browserext.md#auto-save-a-login)。
* **iOS - 选择 Bitwarden 获取验证码**：iOS 16+ 用户现在可以将 Bitwarden 设置为直接从相机 App 扫描代码时用于存储验证码的默认应用程序。参阅[这里](your-vault/totp.md#bitwarden-authenticator-on-ios)。
* **移动端 - 在 App 内更改语言**：不同于在设备操作系统上设置语言，用户可以在 Bitwarden 移动 App 中更改语言。参阅[这里](password-manager/more/localization.md#change-app-language)。

### 机密管理器 Beta <a href="#secrets-manager-beta" id="secrets-manager-beta"></a>

Bitwarden 机密管理器现在作为公开测试版提供。参阅[此处](secrets-manager/secrets-manager-overview.md)了解如何开始。

## 2023.2.0

此次发布包含：

{% hint style="info" %}
**自托管公告**

在此版本中，我们已迁移到新的 [SQL 客户端](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)，该客户端需要一个有效的证书或在 `global.override.env` 中设置的[连接字符串](self-hosting/deploy-and-configure/configuration-options/environment-variables.md#included-variables)中存在 `TrustServerCertificate=True`。请在更新您的服务器之前检查这些。
{% endhint %}

* **Argon2**：您现在可以从**账户设置** → **安全** → **密钥**页面将用于派生账户主密钥的算法更改为 Argon2id。参阅[这里](security/encryption/encryption-key-derivation.md)。

{% hint style="info" %}
**2023-02-14**：2023.2.0 及以后版本的 Bitwarden 客户端支持 Argon2，通过网页密码库切换到 Argon2 可能意味着其他客户端在更新之前无法加载您的密码库。通常在发布后一周内更新这些客户端。
{% endhint %}

* **增加了 PBKDF2 的默认 KDF 迭代**：按照 [OWASP](https://zh.wikipedia.org/zh-cn/OWASP) 的建议，新的 Bitwarden 账户将为 PBKDF2 使用 600,000 次 KDF 迭代。现有的账户可以手动增加此数值。参阅[这里](security/encryption/encryption-protocols.md#changing-kdf-iterations)。
* **主密码安全检查**：在移动 App、浏览器扩展和桌面 App 上创建账户的新用户现在可以通过 HIBP 检查已知的数据泄露，以了解他们的潜在主密码。这将在以后的版本中被带到网页密码库。参阅[这里](your-vault/vault-health-reports.md#data-breach-report-individual-vaults-only)。
* **组织密码库更新**：作为改进网页密码库 UI 的持续努力的一部分，一些组织管理功能进行了重新设计，例如用于项目和集合管理的合并**密码库**视图，以及专用的**成员**和**群组**视图。
* **在其他客户端上使用设备登录**：现在可以在其他客户端上使用设备登录。登录请求现在也可以从浏览器扩展、桌面 App 和移动 App 发起，现在也可以从桌面 App 获得批准。参阅[这里](account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)。
* **自托管组织的自动许可证同步**：自托管组织可以启用自动许可证同步，以便自动更新计费和订阅更改，而不必手动重新上传许可证。参阅[这里](self-hosting/licensing.md#update-a-renewed-organization-license)。
* **用于 Bitwarden 统一的 SQLite 数据库选项**：SQLite 现在是 Bitwarden 统一自托管部署的可用数据库选项。参阅[这里](self-hosting/deploy-and-configure/docker/unified-deployment-beta.md)。
* **更新了自托管安装程序 URL**：用于下载自托管服务器安装程序的 URL 已更改。Linux 参阅[这里](self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#install-bitwarden)，Windows 参阅[这里](self-hosting/deploy-and-configure/docker/windows-standard-deployment.md#install-bitwarden)。
* **Psono 导入器 (json)**：新的导入选项可用于 Psono (json) 导出。参阅[这里](import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

## 2023.1.0

此次发布包含：

* **Apple Watch 上的 Bitwarden**：Bitwarden 添加了 Apple Watch 支持，以提供访问 TOTP 登录代码的附加选项。参阅[这里](miscellaneous/apple-watch-totp.md)。
* **新的环境变量**：一个用于为所有者和管理员强制执行要求 SSO 身份验证策略的环境变量现在可用于自托管服务器。参阅[这里](self-hosting/deploy-and-configure/configuration-options/environment-variables.md#optional-variables)。
* **Bitwarden unified - 支持自定义数据库端口**：统一部署现在支持使用新的环境变量在自定义端口上运行数据库。参阅[这里](self-hosting/deploy-and-configure/docker/unified-deployment-beta.md#environment-variables)。
* **Passsky 导入器 (json)**：新的导入选项可用于未加密的 Passsky (json) 导出。参阅[这里](import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。
* **自定义头像颜色**：从网页密码库的**账户设置** → **我的账户**页面更改您的头像颜色。

## 2022.12.0

此次发布包含：

* **浏览器扩展 - 主题通知栏**：主题通知栏已添加到 Bitwarden 浏览器扩展中以匹配流行的颜色主题。
* **浏览器扩展 - UI 更新**：已对 Bitwarden 浏览器扩展进行了 UI 更新。
* **Apple Watch 上的 Bitwarden (Beta)**：Apple Watch 上的 Bitwarden 将以测试版形式提供给通过 TestFlight 注册的用户，并将提供访问 TOTP 登录代码的附加选项。在[这里](miscellaneous/apple-watch-totp.md)了解更多。

### Bitwarden 统一自托管部署 (Beta) <a href="#bitwarden-unified-self-host-deployment-beta" id="bitwarden-unified-self-host-deployment-beta"></a>

Bitwarden 很高兴地宣布推出为自托管用户提供一个新的选项的测试版本。对于希望在自己的服务器上控制和部署 Bitwarden 的用户，Bitwarden 统一部署是轻量和灵活的选择。有关测试版的更多信息，请参阅[这里](self-hosting/deploy-and-configure/docker/unified-deployment-beta.md)。

## 2022.11.2

此次发布包含：

* **设备登录**：通过向您已注册的移动设备发送身份验证请求而不是使用您的主密码来登录网页密码库（参阅[这里](account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)）。

## 2022.11.0

{% hint style="info" %}
此次发布不包括对浏览器扩展的更新，该扩展将保留在版本 2022.10.1。
{% endhint %}

此次发布包含：

* **组织密码库更新**：作为改进网页密码库 UI 的持续努力的一部分，某些组织管理功能已被移动，例如转移到专用的**计费**和**报告**选项卡中。
* **登录流程更新**：为了适应新的登录选项，登录流程已分为两个界面。
* **SCIM 更新**：SCIM 触发的事件现在将被记录为 `SCIM` 而不是 `Unkown`，并且 SCIM API 密钥现在默认会被混淆。
* **从 iOS 应用扩展生成用户名和密码**：现在可以从 iOS App 扩展「即时」生成用户名和密码，在使用浏览器等 App 时可从「共享」菜单访问。
* **用于移动设备的新主题**：流行的 Solarized Dark 主题已引入移动设备。
* **目录连接器 - 用于 Google Workspace 的群组筛选器查询**：查询参数可被用于 Google Workspace 的群组筛选器中（参阅[这里](admin-console/manage-members/directory-connector/sync-with-google-workspace.md#specify-sync-filters)）。
* **性能优化**：我们改进了网页密码库的加载时间和访问具有数千个密码库项目的账户时的体验。

## 2022.10.0

此次发布包含：

* **受密码保护的加密导出**：加密的 `.json` 导出现在可以使用您选择的密码进行加密。密码保护的导出可以导入任何 Bitwarden 账户（参阅[这里](import-export/encrypted-exports.md)）。
* **移动端用户名生成器**：用户名生成器现在可用于 Bitwarden 移动端 App（参阅[这里](password-manager/vault-basics/generator.md#generate-a-username)）。
* **DuckDuckGo 电子邮件别名集成**：将 Bitwarden 用户名生成器连接到 DuckDuckGo，以便轻松创建电子邮件别名（参阅[这里](password-manager/vault-basics/generator.md#username-types)）。
* **DuckDuckGo macOS 浏览器集成**：我们与 DuckDuckGo 合作创建了与他们[即将推出的 macOS 浏览器](https://spreadprivacy.com/introducing-duckduckgo-for-mac/)的集成！请继续关注他们何时启动此功能的更多信息。
* **SCIM 更新**：被撤销的用户将不再占据您组织中的许可席位（参阅[这里](admin-console/manage-members/scim/about-scim.md#revoking-and-restoring-access)）。

## 2022.9.0

此次发布包含：

* **Fastmail 电子邮件别名集成**：将 Bitwarden 用户名生成器连接到 Fastmail，以方便创建其电子邮件别名（参阅[这里](password-manager/vault-basics/generator.md#username-types)）。
* **提供商门户更新**：提供商门户主界面现在具有每一个客户组织的一目了然的席位和计划报告。
* **组织密码库导出事件**：当所有者或管理员执行密码库导出时，该操作现在将记录在组织的事件日志中（参阅[这里](admin-console/oversight-visibility/event-logging/event-logs.md#organization-events)）。
* **浏览器扩展 - 支持预配置环境 URL**：自托管客户现在可以为浏览器扩展预配置环境 URL，通过使用端点管理来部署您的配置，从而简化最终用户的部署（参阅[这里](broken-reference)）。
* **移动端 - 更新至 Bitwarden Authenticator**：移动 App 现在有一个验证码界面，可让您快速轻松地访问您的所有 TOTP（参阅[这里](your-vault/totp.md#viewing-totp-codes)）。我们还改进了通过移动 App 将 TOTP 代码添加到密码库项目的过程（参阅[这里](your-vault/totp.md#scan-a-qr-code)）。
* **CLI - `serve` 来源保护**：`serve` 命令现在将默认阻止任何使用 `Origin` 标头发出的请求（参阅[这里](password-manager/developer-tools/cli/password-manager-cli.md#serve)）。

## 2022.8.1

此次发布包含：

* **用于企业组织的 SCIM**：企业组织现在可以使用跨域身份管理系统 (SCIM) 从源目录自动配置成员和群组（参阅[这里](admin-console/manage-members/scim/about-scim.md)）。
* **用于登录尝试失败的 hCaptcha**：如果我们检测到连续 9 次失败的登录尝试，现在您将收到一封电子邮件并需要完成 hCaptcha 验证。

## 2022.8.0

此次发布包含：

* **用户撤销**：组织现在可以在不完全移除用户的情况下暂时撤销用户对组织的访问权限（参阅[这里](admin-console/manage-members/user-management.md#revoke-access)）。
* **企业策略更新**：企业策略名称和描述已更新，以更好地描述它们对您的组织的影响（参阅[这里](admin-console/oversight-visibility/enterprise-policies.md)）。
* **设置和首选项更新**：一些 App 设置和首选项的名称和描述已更新，更加直观。

## 2022.6.0

此次发布包含关键功能和可用性改进，使 Bitwarden 在旅途中更加出色：

* **自动填充期间的账户切换 (iOS)**：在自动填充期间通过点击头像按钮快速切换到另一个账户，现在可在 Android 和 iOS 上使用（参阅[这里](password-manager/autofill/autofill-from/autofill-from-ios.md)）。
* **移动端的密码库筛选器**：在移动 App 上，您现在可以按密码库筛选项目。
* **组织成员高级状态**：组织成员现在可以在收到邀请后立即使用高级功能，例如高级 2FA 方式，而无需确认。
* **可访问性改进**：此版本包括一些更改，这些更改将通过辅助技术提高 Bitwarden 的性能，包括具有 [hCaptcha 无障碍访问](https://dashboard.hcaptcha.com/signup?type=accessibility)的用户能够使用其无障碍 Cookie 跳过 hCaptcha 挑战（现在可用于桌面和移动 App）。

## 2022.5.0

{% hint style="info" %}
**我们启用了新的版本编号！**

随着我们进入接近每月一次的发布周期，为了更容易跟踪许多 Bitwarden App 的版本，我们已经采用了一个新的版本编号系统，此版本编号系统将**由所有客户端共用**。此次发布是 `2022.5.0`，因为它是 2022 年 (`2022.`) 5 月 (`.5.`) 的基础发布 (`.0`)。
{% endhint %}

此次发布包含：

* **网页密码库 UI 更新**：网页密码库已收到设计方面的更新，包括改进的个人和组织密码库项目筛选。这是一个由多个部分组成的项目的第一阶段，此项目将同时更新个人用户和组织的网页密码库。
* **用于自托管企业组织的家庭赞助**：现在可以为自托管的企业组织成员发放家庭组织赞助（参阅[这里](self-hosting/deploy-and-configure/optional-features/self-hosting-families-sponsorships.md)）。
* **用户名生成器 - 转发的电子邮件别名类型**：将用户名生成器与 SimpleLogin、AnonAddy 或 Firefox Relay 集成，以自动同时创建用户名和相应的电子邮件别名（参阅[这里](password-manager/vault-basics/generator.md#username-types)）。
* **项目链接**：复制一个项目的 URL 时，将作为直接链接提供给组织成员或在文档中使用（参阅[这里](admin-console/manage-shared-items/link-to-an-item.md)）。
* **自动填写期间的账户切换**：在 Android 系统中，通过点击头像气泡，以在自动填写过程中快速切换到另一个账户（参阅[这里](password-manager/autofill/autofill-from/autofill-from-android.md#auto-fill-while-account-switching)）。
* **客户组织计费的变化**：从这个发布版本开始，只有[提供商](provider-portal/get-started-with-provider-portal.md)用户可以查看[客户组织](provider-portal/get-started-with-provider-portal.md#client-organizations)的计费信息。

## 2022-04-26 <a href="#id-2022-04-26" id="id-2022-04-26"></a>

桌面端 1.33.0，浏览器扩展 1.58.0，移动端 2.18.0，CLI 1.22.0，目录连接器 2.10.1

{% hint style="info" %}
**支持性公告**

在此版本中，从 App Store 下载的 macOS 桌面 App 要求 macOS Mojave (10.14) 或更高版本。从 [bitwarden.com/download](https://bitwarden.com/download/) 和 Github 获得的 `.dmg` 安装程序不受此限制。
{% endhint %}

* **用于浏览器和桌面端的生成器**：使用基于电子邮件的约定（如附加寻址）或使用随机单词为新凭据生成用户名（参阅[这里](password-manager/vault-basics/generator.md)）。
* **CLI - 新的 `serve` 选项**：使用 `--hostname` 选项将您的 API 网页服务器安全地绑定到主机（参阅[这里](password-manager/developer-tools/cli/password-manager-cli.md#serve)）。

## 2022-04-19

服务器 1.48.0，Web 2.28.0

此此最新的发布包含社区要求的功能以及更新网页密码库 UI 的多部分工作的开始。客户端 App（浏览器扩展、移动、桌面和 CLI）的更新将在后续版本中发布：

* **用于网页密码库的用户名生成器**：使用基于电子邮件的约定（如附加寻址）或使用随机单词为新凭据生成用户名。后续版本将包括用于浏览器扩展和桌面 App 的用户名生成器（参阅[这里](password-manager/vault-basics/generator.md)）。
* **网页密码库 - 报告页面**：我们更新了报告页面的位置和风格，以便更轻松地查找报告结果并对其采取行动（参阅[这里](your-vault/vault-health-reports.md)）。
* **macOS 和 Safari 导入器的改进**：我们修复了一些导致 macOS 和 Safari 导入器无法正确导入 URL 和备注的问题。
* **可访问性改进**：此版本包括一些通过屏幕阅读器等辅助技术提高 Bitwarden 性能的更改。

## 2022-03-22

浏览器扩展 1.57.0，移动端 2.17.0

继上周的发布之后，针对移动 App 和浏览器扩展发布了以下内容：

* **移动端添加账户切换功能**：在 Android 和 iOS 上使用 Bitwarden 时，最多可登录 5 个账户并在它们之间无缝切换（参阅[这里](account/log-in-and-unlock/more-log-in-options/account-switching.md)）。
* **支持 Firefox 隐私模式**：此版本包含对 Firefox 隐私窗口更强大的支持（参阅[这里](miscellaneous/use-bitwarden-in-firefoxs-private-mode.md)）。

## 2022-03-15 <a href="#id-2021-10-26" id="id-2021-10-26"></a>

服务器 1.47.0、Web 2.27.0，桌面端 1.32.0，CLI 1.22.0，目录连接器 2.9.11

此最新版本侧重于对单个应用程序的改进，以便您可以完全按照自己的需要使用 Bitwarden。移动 App 和浏览器扩展的更新将在后续版本中发布：

* **来自 CLI 的密码库管理 API**：使用全新的 CLI 命令 `serve`，您可以对一整套密码库管理端点进行 API 调用（参阅[这里](password-manager/developer-tools/cli/password-manager-cli.md#serve)）。
* **CLI 导出命令的更改**：`export` 不再要求主密码，您现在可以使用 `--password` 参数为加密导出设置自定义加密/解密密码（参阅[这里](password-manager/developer-tools/cli/password-manager-cli.md#export)）。
* **新的导入器**：我们为 Dashlane `.csv` 文件和 1Password .`1pux` 文件（要求 1Password v8.5+）增加了自定义导入器。
* **Myki 导入器的改进**：参阅[这里](https://github.com/bitwarden/jslib/pull/707)。
* **弃用工件绑定**：出于安全考虑，已删除 SAML SSO 配置的工件绑定（参阅[这里](https://github.com/bitwarden/server/pull/1885)）。
* **支持 Docker Compose v2**

## 2022-02-08 <a href="#id-2021-10-26" id="id-2021-10-26"></a>

服务器 1.46.0、Web 2.26.0，桌面端 1.31.0，浏览器扩展 1.56.0，移动端 2.16.0，CLI 1.21.0，目录连接器 2.9.9

2022 年初始，Bitwarden 很高兴地发布以下内容：

* **桌面端账户切换**：在 Bitwarden 桌面 App 中一次性登录最多 5 个账户。此功能在 Bitwarden App 中分阶段推出，很快将适用于更多其他 App（参阅[这里](account/log-in-and-unlock/more-log-in-options/account-switching.md)）。
* **iOS 上的 Send**：现在可以直接从 iOS 的共享菜单分享 Bitwarden Send（参阅[这里](bitwarden-send/create-a-send.md)）。
* **从移动端删除账户**：您现在可以从移动 App 中删除您的 Bitwarden 账户（参阅[这里](plans-and-pricing/delete-an-account-or-organization.md)），但您为什么要这样做？
* **新的图标**：我们使用全新的图标更新了所有 Bitwarden App 的外观和体验。尽情欣赏！
* **目录连接器 - Azure AD 同步性能**：针对 Azure Active Directory 的目录连接器同步，性能已得到提升。与 Azure AD 同步的组&#x7EC7;_&#x5C06;不&#x518D;_&#x9700;要更改其同步配置。
* **后端改进**：我们一直在努力改进 Bitwarden 平台的总体性能和稳定性，这将在未来推出一些很棒的新功能。

## 2012-12-07 <a href="#id-2021-10-26" id="id-2021-10-26"></a>

服务器 1.45.0、Web 2.25.0，桌面端 1.30.0，浏览器扩展 1.55.0，移动端 2.15.0，CLI 1.20.0

Bitwarden 很自豪地宣布在 12 月的版本中增加了新的企业功能，为企业计划增加了灵活性和价值。

* &#x20;[**Key Connector**](self-hosting/key-connector/about-key-connector.md)：(_仅适用于自托管组织_）当使用带有客户管理加密的 SSO 登录时，作为使用主密码解密密码库的一个替代方案，自托管 Key Connector 应用程序向 Bitwarden 客户端提供加密密钥（参阅[这里](self-hosting/key-connector/about-key-connector.md)）。
* **用于企业的家庭**：(_目前仅适用于云托管组织，未来版本的自托管_）从这个版本开始，企业组织的成员可以兑换一个与最多 5 个朋友或家庭成员共享的免费 [Bitwarden 家庭组织](plans-and-pricing/password-manager/about-bitwarden-plans.md#families-organizations)。家庭组织包括所有 6 个用户的所有高级功能和无限制的安全数据共享（参阅[这里](plans-and-pricing/password-manager/redeem-families-sponsorship.md)）。
* **MacOS 和 Safari 导入器**：我们为从 Safari 和 macOS 导出的密码增加了一个自定义导入器（详情见[这里](password-manager/import-and-export/import-guides/import-data-from-macos-and-safari.md)）。
* **新的自定义字段类型**：链接型自定义字段可用于解决您的浏览器扩展在自动填写特定网站的用户名和密码时遇到的问题，方法是将用户名和密码链接到定制的表单元素（参阅[此处](password-manager/autofill/more-autofill-options/auto-fill-custom-fields.md#using-linked-custom-fields)）。
* **浏览器扩展 - 自动填充时解锁密码库**：当您尝试在密码库被锁定时使用上下文菜单或键盘快捷键进行自动填充，现在将提示您解锁密码库，并在解锁后自动填写您的凭证。

## 2021-10-26 <a href="#id-2021-10-26" id="id-2021-10-26"></a>

服务器 1.44.0，Web 2.24.0，桌面端 1.29.0，浏览器扩展 1.54.0，移动端 2.14.0，CLI 1.19.0

很高兴 Bitwarden 团队发布了一系列新功能和更新，以继续我们让个人和企业的密码管理变得简单易用的使命：

{% hint style="info" %}
**弃用公告**：业务门户已弃用。企业组织可以通过组织**管理**选项卡配置[策略](admin-console/oversight-visibility/enterprise-policies.md)和 [SSO 登录](login-with-sso/about-login-with-sso.md)。
{% endhint %}

* **密码库超时策略**：密码库超时策略将为您组织的所有成员应用最长的密码库超时持续时间（参阅[这里](admin-console/oversight-visibility/enterprise-policies.md#vault-timeout)）。
* **禁用个人密码库导出策略**：禁用个人密码库导出策略将禁止您组织的非所有者/非管理员成员导出私人密码库数据（参阅[这里](admin-console/oversight-visibility/enterprise-policies.md#disable-personal-vault-export)）。
* **自动扩展组织席位**：团队和企业组织将在邀请新用户时自动扩展用户席位。组织可以设置扩展限制，以防止席位数量超过指定的数量（参阅[这里](admin-console/manage-members/user-management.md)）。
* **自定义密码库超时**：您现在可以为密码库超时指定自定义时间范围（小时和分钟）（参阅[这里](account/log-in-and-unlock/vault-timeout-options.md#vault-timeout)）。
* **自定义角色 - 改进的集合权限**：自定义角色的集合管理权限已扩展为包括对用户是否可以创建、编辑或删除已分配的集合或所有集合的精细控制（参阅[这里](account/log-in-and-unlock/vault-timeout-options.md#vault-timeout)）。
* **管理员密码重置 - 重置后更新密码**：管理员重置的密码现在必须由他们所属的用户在登录 Bitwarden 时立即更新（参阅[这里](admin-console/manage-members/account-recovery/about-account-recovery.md#after-a-password-reset)）。
* **浏览器扩展 - 自动填充 Span 元素**：浏览器扩展现在可以在 HTML `<span>` 元素的 innerText 中自动填充[自定义字段](your-vault/custom-fields.md)（参阅[这里](password-manager/autofill/more-autofill-options/auto-fill-custom-fields.md#html-span-elements)）。
* &#x20;**浏览器扩展 - 自动生物识别提示**：浏览器扩展现在可以在打开时自动提示您生物识别输入。您可以从 **⚙️设置**菜单切换此行为（参阅[这里](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)）。
* **网页密码库 - 黑暗模式**：网页密码库现在拥有黑暗模式（参阅[这里](miscellaneous/change-app-theme.md)）。
* **CLI - `generate` 密码短语选项**：`bw generate --passphrase` 命令现在包含 `--capitalize` 和 `--includeNumber` 选项（参阅[这里](password-manager/developer-tools/cli/password-manager-cli.md#generate)）。

## 2021-09-21

服务器 1.43.0，Web 2.23.0，桌面端 1.28.3，浏览器扩展 1.53.0，移动端 2.13.0，CLI 1.18.1

Bitwarden 的最新版本侧重于对现有功能进行经常性的改进：

* **移动设备上的 FIDO2 WebAuthn**：iOS 和 Android 现在支持通过 FIDO2 WebAuthn 进行两步登录（参阅[这里](account/two-step-login/setup-guides/two-step-login-via-fido.md)）。
* **管理员密码重置 - 自动注册改进**：自动注册策略选项现在会阻止用户撤销管理员密码重置（参阅[这里](admin-console/manage-members/account-recovery/about-account-recovery.md#automatic-enrollment)）。
* **浏览器扩展 - 从保存栏中选择文件夹**：您现在可以直接从浏览器扩展的保存提示中选择要将项目保存到哪个[文件夹](your-vault/folders.md)（参阅[这里](getting-started/getting-started-browserext.md#add-a-login)）。
* **浏览器扩展 - 上下文菜单项目自定义字段**：您现在可以直接从浏览器扩展的上下文菜单中复制 HTML 元素名称，以便轻松创建自定义字段（参阅[这里](your-vault/custom-fields.md#custom-field-names)）。
* **网页密码库 - 策略位置更改**：现在只能从组织的**管理 → 策略**界面配置[企业策略](admin-console/oversight-visibility/enterprise-policies.md)，而不能从业务门户配置。
* **CAPTCHA 验证**：从这个版本开始，我们将开启 [hCaptcha](https://www.hcaptcha.com/about) 验证以防止诸如撞库之类的机器人攻击。请注意，CLI 中的挑战与其他客户端应用程序中的挑战不同（有关 CLI 的详细信息，请参阅[此处](password-manager/developer-tools/cli/cli-authentication-challenges.md)）。

## 2021-08-18 <a href="#id-2021-06-29" id="id-2021-06-29"></a>

{% hint style="success" %}
有兴趣成为提供商吗？首先，我们要求：

* 您的企业有一个活跃的企业组织。
* 您的企业有一个客户准备在您的提供商下入职。

如果您还没有准备好开始成为提供商，Bitwarden 团队希望支持您作为一个经销商或客户的 Bitwarden 之旅。

[联系我们](https://bitwarden.com/contact)
{% endhint %}

Bitwarden 的最新版本专注于使托管服务提供商 (MSP) 能够支持其客户的密码管理需求：

* **提供商门户**：提供商门户网站允许托管服务提供商 (MSP) 和经销商代表客户创建和管理组织。使用该门户，提供商可以无缝地支持多个客户的凭证管理（参阅[这里](provider-portal/get-started-with-provider-portal.md)）。
* **共享用词的变化**：我们将**共享**按钮更新为**移动到组织**，以明确共享项目是由组织所拥有的。此外，我们还将「已共享项目」的指示符号（）更改为与集合的指示符号（）保持一致。
* **CLI `move` 命令**：为了与上述条目保持一致，CLI 的 `share` 命令已被更改为 `move`（参阅[这里](password-manager/developer-tools/cli/password-manager-cli.md#move)）。

## 2021-06-29 <a href="#id-2021-06-29" id="id-2021-06-29"></a>

Bitwarden 团队很高兴地宣布推出管理员密码重置功能，这是一项最新功能，旨在帮助需要大规模地确保密码安全的企业。此次发布包括：

* **管理员密码重置**：企业组织可以注册管理员密码重置功能，以允许指定的管理员重置组织用户的主密码（参阅[这里](admin-console/manage-members/account-recovery/about-account-recovery.md)）。
* **主密码重新提示**：使用新的主密码重新提示选项，要求验证您的主密码才能查看被用户指定的敏感密码库项目。（参阅[这里](your-vault/vault-items.md#protect-individual-items)）。
* **批量用户管理**：组织所有者和管理员现在可以从组织中批量重新发送邀请、确认已接受的用户以及移除用户（参阅[这里](admin-console/manage-members/user-management.md#onboard-users)）。
* **事件日志导出**：直接从网页密码库导出事件日志（参阅[这里](admin-console/oversight-visibility/event-logging/event-logs.md#export-events)）。
* **目录连接器 API 密钥认证**：从此版本开始，目录连接器的用户将需要使用[组织 API 密钥](organizations/bitwarden-public-api.md#authentication)才能登录。
* **目录连接器同步限制增加**：目录连接器现在可以同步无限数量的用户或群组，之前的限制被设置为 2000。要同步 2000 以上的用户或群组，请切换到新的同步选项（参阅[这里](admin-console/manage-members/directory-connector/sync-options-and-filters.md#large-syncs)）。
* **页面加载时自动填充功能的增强**：浏览器扩展的页面加载时自动填充功能已升级，可以更灵活地满足用户的独特需求（参阅[这里](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#on-page-load)）。
* **更多 CLI 选项**：我们添加了一些新的 CLI 选项，包括轻松检索密码库项目的备注 (`bw get notes <id>`) 和设置 Send 的最大访问计数的功能 (`bw send create --maxAccessCount <#>`)。
* **Web 开发人员自动填充排除**：网页开发贡献者现在可以通过向 `<input>` 元素添加 `data-bwignore` 属性（例如 `data-bwignore="true"`）来阻止浏览器扩展自动填充给定的表单元素。

## 2021-05-11 <a href="#id-2021-05-11" id="id-2021-05-11"></a>

很高兴 Bitwarden 团队发布了一系列新功能和更新，以继续我们让个人和企业的密码管理变得简单易用的使命：

* **Send 隐私 & 安全选项**：使用新的 Send 隐私选项以对接收者隐藏您的电子邮件地址（参阅[这里](bitwarden-send/send-privacy.md#hide-email)）。为了防止滥用，文件 Send 现在将需要一个经过验证的电子邮件地址。此外，企业组织可以实施一条新的策略来设置隐藏电子邮件选项的可用性（参阅[这里](admin-console/oversight-visibility/enterprise-policies.md#send-options)）。
* **FIDO 更新 & 扩展支持**：我们的 FIDO 实施已经从 FIDO U2F 升级为 FIDO2 WebAuthn，但现有的 FIDO U2F 密钥将保留其完整性。对 FIDO 的支持已经扩展到更多的浏览器扩展和 Windows 桌面应用程序（参阅[这里](account/two-step-login/setup-guides/two-step-login-via-fido.md)）。
* **用于密钥的自定义字段**：自定义字段的值已经升级到支持多达 5000 个字符，允许存储像 RSA 4096 位 SSH 密钥这样的密钥（参阅[这里](your-vault/custom-fields.md#custom-fields-for-keys)）。
* **文件大小增加**：现在可以创建最大 500 MB 的文件附件或文件 Send。由于设备限制，移动 App 仍采用旧的 100 MB 限制。
* **禁用浏览器扩展计数器**：使用 **⚙️设置 → 选项**菜单中的新开关来禁用浏览器扩展的角标计数器（参阅[这里](password-manager/autofill/autofill-from/autofill-from-browser-extensions.md)）。
* **Safari 的生物识别**：Safari 网页扩展现在包含对 Safari 14+ 生物识别解锁的支持（参阅[这里](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)）。
* **搜索国际化**：现在可以使用 1 个字符搜索密码库，改善了使用 1 个字符单词的语言（如简体中文和繁体中文）的使用体验。
* **弱密码报告排序**：弱密码报告现在按照密码弱性的严重程度来排序（参阅[这里](your-vault/vault-health-reports.md#weak-passwords-report)）。

{% hint style="warning" %}
由于附件升级，通过最新的客户端上传的附件无法在旧版本的客户端上打开。如果您发现您无法访问最近创建的附件，请将您的客户端升级到最新版本（**提示**：云网页密码库总是为最新版本）。

**冻结的或旧版的客户端**，包括 Safari 13（或更早）macOS 桌面 App 和 App 扩展，将不支持访问这些附件。
{% endhint %}

{% hint style="info" %}
自从 2020 年实施软删除以来，我们一直在耐心地对待回收站。**从 2021 年 5 月 15 日开始**，我们将激活夜间作业，该作业将永久删除您的回收站中已存在 30 天或更长时间的项目。

在 2021 年 5 月 15 日之前，我们建议您在回收站中进行挖掘，以寻找您可能想要恢复的任何内容！
{% endhint %}

## 2021-03-11 <a href="#id-2021-03-11" id="id-2021-03-11"></a>

Bitwarden 自豪地宣布我们发布了 Bitwarden Send，一个用于短暂共享的端到端加密解决方案。此次发布包括：

* **Bitwarden Send**：Bitwarden Send 是一个用于短暂共享的端到端加密解决方案。在我们的网站和帮助中心有很多关于 Send 的资料，但您可以从[这里](bitwarden-send/about-send.md)开始。
* **FIDO U2F 支持 Edge**：FIDO U2F 方式的两步登录现在可以用于微软 Edge 中的网页密码库和浏览器扩展（参阅[这里](account/two-step-login/setup-guides/two-step-login-via-fido.md)）。
* **浏览器扩展中的域名排除**：Bitwarden 浏览器扩展现在可以对其明确不提供记住密码的域名进行配置（参阅[这里](password-manager/autofill/more-autofill-options/exclude-domains.md)）。
* **改进的导入错误消息**：最近有很多人迁移到 Bitwarden，所以我们清理了一个导入错误的消息，以帮助您更快地解决问题（参阅[这里](password-manager/import-and-export/import-data.md#length-related-import-errors)）。
* **Safari 网页扩展移植**：我们的 Safari App 扩展已经正式移植到 Safari 14 以上版本的网页扩展中使用。由于 Safari 的变化，网页扩展的使用现在仅限于那些通过 Mac App Store 下载获取的 App（参阅[这里](miscellaneous/safari-web-extension.md)）。

## 2021-01-19 发行后的更新 <a href="#id-2021-01-19-post-release-update" id="id-2021-01-19-post-release-update"></a>

{% hint style="info" %}
如果您拥有最新版 (2021-01-19) 的桌面 App，则浏览器扩展的生物识别解锁**仅适用于基于 Chromium 的浏览器**（比如 Chrome、Edge）上安装的 v1.48.0 版本的浏览器扩展。

当您的浏览器扩展更新到这个版本时，您可能会被要求接受一个新的权限，以便 Bitwarden `Communicate with cooperating native applications（与本机应用程序通信）`。这个权限是安全的，也是**可选的**，它允许浏览器扩展与 Bitwarden 桌面 App 进行通信，而这是启用生物识别解锁所必需的（参阅[这里](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#browser-extensions)）。拒绝此权限也将允许您使用 v1.48.0 扩展，只是不带生物识别解锁功能。

**生物识别解锁当前不适用于：**

* 版本低于 87 的 Firefox 浏览器扩展
* Microsoft App Store 桌面 App（从 [bitwarden.com/download](https://bitwarden.com/download) 获取的侧面加载的 Windows 桌面 App 可以正常工作）
* 侧面加载的 macOS 桌面 App（App Store 桌面 App 可以正常工作）

Bitwarden 团队正在调查这些问题，并将随着情况的进展提供更新。
{% endhint %}

## 2021-01-19

自 2021 年的第一个主要版本以来，Bitwarden 团队合并了多项重大改进，以满足所有用户的关键需求，其中包括：

* **紧急访问**：Bitwarden 新增的紧急访问功能使用户可以指定和管理受信任的紧急联系人，紧急联系人可以在零知识/零信任环境中请求访问其密码库（参阅[这里](account/log-in-and-unlock/more-log-in-options/emergency-access.md)）。
* **加密导出**：个人用户和组织现在可以将密码库数据导出到加密的 `.json` 文件中（参阅[这里](import-export/encrypted-exports.md)）。
* **新的角色**：现在可以使用自定义角色来对用户权限进行粒度控制（参阅[这里](admin-console/manage-members/member-roles.md#custom-role)）。
* **新的企业策略**：现在，企业组织可以使用个人所有权策略（参阅[这里](admin-console/oversight-visibility/enterprise-policies.md#personal-ownership)）。
* **浏览器扩展的生物识别解锁**：通过与本机桌面应用程序的集成，您现在可以使用生物识别输入来解锁基于 Chromium 的浏览器扩展（参阅[这里](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#browser-extensions)）。

## 2020-11-12

最新版本的 Bitwarden 为所有客户端应用程序添加了与 SSO 相关的增强功能，包括：

* **新的企业策略**：单一组织和单点登录 (SSO) 认证策略现在可供企业组织使用（参阅[这里](admin-console/oversight-visibility/enterprise-policies.md)）。
* **用于 CLI 的 API 密钥**：使用从您的网页密码库中新获得的 API 密钥来验证进入 Bitwarden CLI（参阅[这里](password-manager/developer-tools/cli/personal-api-key.md)）。
* **SSO 入职改进**：我们对用户通过 SSO 入职的方式进行了一些改进，以预防潜在的安全风险（参阅[这里](https://github.com/bitwarden/server/pull/945)）。
* **GDPR 确认**：从现在开始，Bitwarden 的新用户在注册时将被要求确认隐私政策。
* **Android 11 内嵌自动填充**：对于使用 Android 11+ 的设备，启用自动填充服务将为也支持[此功能](https://developer.android.com/guide/topics/text/ime-autofill#workflow)的 IME 显示内嵌建议（参阅[这里](https://github.com/bitwarden/mobile/pull/1145)）。

## 2020-09-30

最新版本的 Bitwarden 为所有客户端应用程序以及网页密码库业务门户增加了备受期待的 **SSO 登录**功能。阅读这篇[博客文章](https://bitwarden.com/blog/post/bitwarden-launches-sso-authentication/)了解关于 SSO 登录的更多信息，同时也可参考我们的[文档](login-with-sso/)。

## 2020 早期 <a href="#early-2020-releases" id="early-2020-releases"></a>

在 2020 年 03 月至 09 月之间发布了以下项目：

* [企业策略](admin-console/oversight-visibility/enterprise-policies.md)
* [密码库超时选项](account/log-in-and-unlock/vault-timeout-options.md)
* [回收站功能](your-vault/vault-items.md#delete-a-vault-item)
* [密码查看权限 - ](admin-console/manage-members/member-roles.md#granular-access-control)[隐藏密码](admin-console/manage-members/member-roles.md#granular-access-control)
* [桌面版应用程序的触控 ID/Windows Hello](account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#desktop-applications)

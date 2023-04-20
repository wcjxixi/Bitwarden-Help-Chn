# 发行记录

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/releasenotes/)
{% endhint %}

Bitwarden 相信，源代码的透明度是诸如像我们这样的安全解决方案的一个绝对要求。访问以下 GitHub 链接查看详细的发行记录：

* [Server Releases](https://github.com/bitwarden/server/releases)
* [Web Releases](https://github.com/bitwarden/web/releases)
* [Desktop Releases](https://github.com/bitwarden/desktop/releases)
* [Browser Extension Releases](https://github.com/bitwarden/browser/releases)
* [Mobile Releases](https://github.com/bitwarden/mobile/releases)
* [CLI Releases](https://github.com/bitwarden/cli/releases)
* [Directory Connector Releases](https://github.com/bitwarden/directory-connector/releases)

## 发行公告

Bitwarden 会逐步更新每一个客户端应用程序（桌面端、浏览器扩展、移动端等），以及自托管服务器，以确保功能的有效性和稳定性。因此，客户端应用程序和自托管服务器将在初始发布后逐步获得所列的功能。

{% hint style="success" %}
您也可以订阅 [Bitwarden Status RSS feed](https://status.bitwarden.com/) 以获取服务更新，包括发行窗口的公告。
{% endhint %}

## 2023.3.0

此次发布包含：

* **域名验证**：组织可以验证域名（例如 `mycompany.com`）的所有权，允许用户在使用 SSO 登录时跳过组织标识符步骤。参阅这里。
* **浏览器扩展 - 改进的自动填充安全性**：浏览器扩展现在不允许在页面加载时自动填充不受信任的 iframe。浏览器扩展还会在手动自动填充、使用上下文菜单或使用键盘快捷键时警告用户有关不受信任的 iframe，并在自动填充 HTTP 站点时警告用户，该站点需要基于该项目的已保存 URI 的 HTTPS。参阅这里。
* **主密码安全性检查**：用户现在可以在创建帐户或在 Web 密码库上更改主密码时通过 Have I Been Pwned 检查已知的数据泄露，以查找他们预期的主密码。参阅这里。
* **主密码长度要求**：现在主密码的长度必须至少为 12 个字符。此规则将对新的 Bitwarden 帐户和更改主密码的任何用户强制执行。
* **激活自动填充策略**：对于企业组织，激活自动填充策略将自动为组织的新成员和现有成员打开页面加载时的自动填充。参阅这里。
* **浏览器扩展 - 改进的通知栏**：用于将未检测到的项目添加到您的密码库的通知栏现在为遵守删除单个密码库策略的用户提供了更直观的工作流程。参阅这里。
* **iOS - 选择 Bitwarden 获取验证码**：iOS 16+ 用户现在可以将 Bitwarden 设置为直接从相机应用程序扫描代码时用于存储验证码的默认应用程序。参阅这里。
* **移动端 - 在应用程序内更改语言**：不同于在设备操作系统上设置语言，用户可以在 Bitwarden 移动应用程序中更改语言。参阅这里。

### 机密管理器 (Beta) <a href="#secrets-manager-beta" id="secrets-manager-beta"></a>

Bitwarden 机密管理器现在作为公开测试版提供。在此处了解如何开始。

## 2023.2.0

此次发布包含：

{% hint style="info" %}
**自托管公告**

在此版本中，我们已迁移到新的 [SQL 客户端](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)，该客户端需要一个有效的证书或在 `global.override.env` 中设置的[连接字符串](on-premises-hosting/configure-environment-variables.md#included-variables)中存在 `TrustServerCertificate=True`。请在更新您的服务器之前检查这些。
{% endhint %}

* **Argon2**：您现在可以从**帐户设置** → **安全** → **密钥**页面将用于派生帐户主密钥的算法更改为 Argon2id。参阅[这里](security/kdf-algorithms.md)。

{% hint style="info" %}
**2023-02-14**：2023.2.0 及以后版本的 Bitwarden 客户端支持 Argon2，通过网页密码库切换到 Argon2 可能意味着其他客户端在更新之前无法加载您的密码库。通常在发布后一周内更新这些客户端。
{% endhint %}

* **增加了 PBKDF2 的默认 KDF 迭代**：按照 [OWASP](https://zh.wikipedia.org/zh-cn/OWASP) 的建议，新的 Bitwarden 帐户将为 PBKDF2 使用 600,000 次 KDF 迭代。现有的帐户可以手动增加此数值。参阅[这里](security/encryption.md#changing-kdf-iterations)。
* **主密码安全检查**：在移动应用程序、浏览器扩展和桌面应用程序上创建账户的新用户现在可以通过 HIBP 检查已知的数据泄露，以了解他们的潜在主密码。这将在以后的版本中被带到网页密码库。参阅[这里](password-manager/vault-administration/vault-health-reports.md#data-breach-report-individual-vaults-only)。
* **组织密码库更新**：作为改进网页密码库 UI 的持续努力的一部分，一些组织管理功能进行了重新设计，例如用于项目和集合管理的合并**密码库**视图，以及专用的**成员**和**群组**视图。
* **在其他客户端上使用设备登录**：现在可以在其他客户端上使用设备登录。登录请求现在也可以从浏览器扩展、桌面应用程序和移动应用程序发起，现在也可以从桌面应用程序获得批准。参阅[这里](my-account/log-in-and-unlock/log-in-with-device.md)。
* **自托管组织的自动许可证同步**：自托管组织可以启用自动许可证同步，以便自动更新计费和订阅更改，而不必手动重新上传许可证。参阅[这里](on-premises-hosting/licensing-for-paid-features.md#update-a-renewed-organization-license)。
* **用于 Bitwarden 统一的 SQLite 数据库选项**：SQLite 现在是 Bitwarden 统一自托管部署的可用数据库选项。参阅[这里](on-premises-hosting/install-deploy-guides/install-and-deploy-unified-beta.md)。
* **更新了自托管安装程序 URL**：用于下载自托管服务器安装程序的 URL 已更改。Linux 参阅[这里](on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md#install-bitwarden)，Windows 参阅[这里](on-premises-hosting/install-deploy-guides/install-and-deploy-windows.md#install-bitwarden)。
* **Psono 导入器 (json)**：新的导入选项可用于 Psono (json) 导出。参阅[这里](password-manager/import-and-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

## 2023.1.0

此次发布包含：

* **Apple Watch 上的 Bitwarden**：Bitwarden 添加了 Apple Watch 支持，以提供访问 TOTP 登录代码的附加选项。参阅这里。
* **新的环境变量**：一个用于为所有者和管理员强制执行要求 SSO 身份验证策略的环境变量现在可用于自托管服务器。参阅[这里](on-premises-hosting/configure-environment-variables.md#optional-variables)。
* **Bitwarden unified - 支持自定义数据库端口**：统一部署现在支持使用新的环境变量在自定义端口上运行数据库。参阅[这里](on-premises-hosting/install-deploy-guides/install-and-deploy-unified-beta.md#environment-variables)。
* **Passsky 导入器 (json)**：新的导入选项可用于未加密的 Passsky (json) 导出。参阅[这里](password-manager/import-and-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。
* **自定义头像颜色**：从 Web 密码库的**帐户设置** → **我的帐户**页面更改您的头像颜色。

## 2022.12.0

此次发布包含：

* **浏览器扩展 - 主题通知栏**：主题通知栏已添加到 Bitwarden 浏览器扩展中以匹配流行的颜色主题。
* **浏览器扩展 - UI 更新**：已对 Bitwarden 浏览器扩展进行了 UI 更新。
* **Apple Watch 上的 Bitwarden（测试版）**：Apple Watch 上的 Bitwarden 将以测试版形式提供给通过 TestFlight 注册的用户，并将提供访问 TOTP 登录代码的附加选项。在[这里](password-manager/more/apple-watch-totp.md)了解更多。

### Bitwarden 统一自托管部署 (Beta) <a href="#bitwarden-unified-self-host-deployment-beta" id="bitwarden-unified-self-host-deployment-beta"></a>

Bitwarden 很高兴地宣布推出为自托管用户提供一个新的选项的测试版本。对于希望在自己的服务器上控制和部署 Bitwarden 的用户，Bitwarden 统一部署是轻量和灵活的选择。有关测试版的更多信息，请参阅[这里](on-premises-hosting/install-deploy-guides/install-and-deploy-unified-beta.md)。

## 2022.11.2

此次发布包含：

* **设备登录**：通过向您已注册的移动设备发送身份验证请求而不是使用您的主密码来登录网页密码库（参阅[这里](my-account/log-in-and-unlock/log-in-with-device.md)）。

## 2022.11.0

{% hint style="info" %}
此次发布不包括对浏览器扩展的更新，该扩展将保留在版本 2022.10.1。
{% endhint %}

此次发布包含：

* **组织密码库更新**：作为改进 Web 密码库 UI 的持续努力的一部分，某些组织管理功能已被移动，例如转移到专用的**账单**和**报告**选项卡中。
* **登录流程更新**：为了适应新的登录选项，登录流程已分为两个界面。
* **SCIM 更新**：SCIM 触发的事件现在将被记录为 `SCIM` 而不是 `Unkown`，并且 SCIM API 密钥现在默认会被混淆。
* **从 iOS 应用扩展生成用户名和密码**：现在可以从 iOS 应用扩展「即时」生成用户名和密码，在使用浏览器等应用时可从「共享」菜单访问。
* **用于移动设备的新主题**：流行的 Solarized Dark 主题已引入移动设备。
* **目录连接器 - 用于 Google Workspace 的群组筛选器查询**：查询参数可被用于 Google Workspace 的群组筛选器中（参阅[这里](admin-console/user-management/directory-connector/sync-with-google-workspace.md#specify-sync-filters)）。
* **性能优化**：我们改进了 Web 密码库的加载时间和访问具有数千个密码库项目的帐户时的体验。

## 2022.10.0

此次发布包含：

* **受密码保护的加密导出**：加密的 `.json` 导出现在可以使用您选择的密码进行加密。密码保护的导出可以导入任何 Bitwarden 帐户（参阅[这里](password-manager/import-and-export/encrypted-exports.md)）。
* **移动端用户名生成器**：用户名生成器现在可用于 Bitwarden 移动端应用程序（参阅[这里](password-manager/vault-basics/username-password-generator.md#generate-a-username)）。
* **DuckDuckGo 电子邮件别名集成**：将 Bitwarden 用户名生成器连接到 DuckDuckGo，以便轻松创建电子邮件别名（参阅[这里](password-manager/vault-basics/username-password-generator.md#username-types)）。
* **DuckDuckGo macOS 浏览器集成**：我们与 DuckDuckGo 合作创建了与他们[即将推出的 macOS 浏览器](https://spreadprivacy.com/introducing-duckduckgo-for-mac/)的集成！请继续关注他们何时启动此功能的更多信息。
* **SCIM 更新**：被撤销的用户将不再占据您组织中的许可席位（参阅[这里](admin-console/user-management/scim/about-scim.md#revoking-and-restoring-access)）。

## 2022.9.0

此次发布包含：

* **Fastmail 电子邮件别名集成**：将 Bitwarden 用户名生成器连接到 Fastmail，以方便创建其电子邮件别名（参阅[这里](password-manager/vault-basics/username-password-generator.md#username-types)）。
* **提供商门户更新**：提供商门户主界面现在具有每一个客户组织的一目了然的席位和计划报告。
* **组织密码库导出事件**：当所有者或管理员执行密码库导出时，该操作现在将记录在组织的事件日志中（参阅[这里](admin-console/organization-basics/event-logs.md#organization-events)）。
* **浏览器扩展 - 支持预配置环境 URL**：自托管客户现在可以为浏览器扩展预配置环境 URL，通过使用端点管理来部署您的配置，从而简化最终用户的部署（参阅[这里](on-premises-hosting/configure-clients-centrally.md#liu-lan-qi-kuo-zhan)）。
* **移动端 - 更新至 Bitwarden Authenticator**：移动端应用程序现在有一个验证码界面，可让您快速轻松地访问您的所有 TOTP（参阅[这里](password-manager/vault-basics/totp.md#viewing-totp-codes)）。我们还改进了通过移动应用程序将 TOTP 代码添加到密码库项目的过程（参阅[这里](password-manager/vault-basics/totp.md#scan-a-qr-code)）。
* **CLI - `serve` 来源保护**：`serve` 命令现在将默认阻止任何使用 `Origin` 标头发出的请求（参阅[这里](password-manager/getting-started/bitwarden-cli.md#serve)）。

## 2022.8.1

此次发布包含：

* **用于企业组织的 SCIM**：企业组织现在可以使用跨域身份管理系统 (SCIM) 从源目录自动配置成员和群组（参阅[这里](admin-console/user-management/scim/about-scim.md)）。
* **用于登录尝试失败的 hCaptcha**：如果我们检测到连续 9 次失败的登录尝试，现在您将收到一封电子邮件并需要完成 hCaptcha 验证。

## 2022.8.0

此次发布包含：

* **用户撤销**：组织现在可以在不完全移除用户的情况下暂时撤销用户对组织的访问权限（参阅[这里](admin-console/user-management/user-management.md#revoke-access)）。
* **企业策略更新**：企业策略名称和描述已更新，以更好地描述它们对您的组织的影响（参阅[这里](admin-console/organization-basics/enterprise-policies.md)）。
* **设置和首选项更新**：一些应用程序设置和首选项的名称和描述已更新，更加直观。

## 2022.6.0

此次发布包含关键功能和可用性改进，使 Bitwarden 在旅途中更加出色：

* **自动填充期间的帐户切换 (iOS)**：在自动填充期间通过点击头像按钮快速切换到另一个帐户，现在可在 Android 和 iOS 上使用（参阅[这里](password-manager/auto-fill/auto-fill-logins-on-ios.md)）。
* **移动端的密码库筛选器**：在移动应用程序上，您现在可以按密码库筛选项目。
* **组织成员高级状态**：组织成员现在可以在收到邀请后立即使用高级功能，例如高级 2FA 方式，而无需确认。
* **可访问性改进**：此版本包括一些更改，这些更改将通过辅助技术提高 Bitwarden 的性能，包括具有 [hCaptcha 无障碍访问](https://dashboard.hcaptcha.com/signup?type=accessibility)的用户能够使用其无障碍 Cookie 跳过 hCaptcha 挑战（现在可用于桌面和移动应用程序）。

## 2022.5.0

{% hint style="info" %}
**我们启用了新的版本编号！**

随着我们进入接近每月一次的发布周期，为了更容易跟踪许多 Bitwarden 应用程序的版本，我们已经采用了一个新的版本编号系统，此版本编号系统将**由所有客户端共用**。此次发布是 `2022.5.0`，因为它是 2022 年 (`2022.`) 5 月 (`.5.`) 的基础发布 (`.0`)。
{% endhint %}

此次发布包含：

* **网页密码库 UI 更新**：网页密码库已收到设计方面的更新，包括改进的个人和组织密码库项目筛选。这是一个由多个部分组成的项目的第一阶段，此项目将同时更新个人用户和组织的网页密码库。
* **用于自托管企业组织的家庭赞助**：现在可以为自托管的企业组织成员发放家庭组织赞助（参阅[这里](on-premises-hosting/self-hosting-families-sponsorships.md)）。
* **用户名生成器 - 转发的电子邮件别名类型**：将用户名生成器与 SimpleLogin、AnonAddy 或 Firefox Relay 集成，以自动同时创建用户名和相应的电子邮件别名（参阅[这里](password-manager/vault-basics/username-password-generator.md#username-types)）。
* **项目链接**：复制一个项目的 URL 时，将作为直接链接提供给组织成员或在文档中使用（参阅[这里](admin-console/more/link-to-an-item.md)）。
* **自动填写期间的账户切换**：在安卓系统中，通过点击头像气泡，以在自动填写过程中快速切换到另一个账户（参阅[这里](password-manager/auto-fill/auto-fill-logins-on-android.md#auto-fill-while-account-switching)）。
* **客户组织计费的变化**：从这个发布版本开始，只有[提供商](provider-portal/get-started-with-provider-portal.md)用户可以查看[客户组织](provider-portal/get-started-with-provider-portal.md#client-organizations)的账单信息。

## 2022-04-26 <a href="#2022-04-26" id="2022-04-26"></a>

_桌面端 1.33.0，浏览器扩展 1.58.0，移动端 2.18.0，CLI 1.22.0，目录连接器 2.10.1_

{% hint style="info" %}
**支持性公告**

在此版本中，从 App Store 下载的 macOS 桌面应用程序要求 macOS Mojave (10.14) 或更高版本。从 [bitwarden.com/download](https://bitwarden.com/download/) 和 Github 获得的 `.dmg` 安装程序不受此限制。
{% endhint %}

* **用于浏览器和桌面端的生成器**：使用基于电子邮件的约定（如附加寻址）或使用随机单词为新凭据生成用户名（参阅[这里](password-manager/vault-basics/username-password-generator.md)）。
* **CLI - 新的 `serve` 选项**：使用 `--hostname` 选项将您的 API 网页服务器安全地绑定到主机（参阅[这里](password-manager/getting-started/bitwarden-cli.md#serve)）。

## 2022-04-19

_服务器 1.48.0，Web 2.28.0_

此此最新的发布包含社区要求的功能以及更新网页密码库 UI 的多部分工作的开始。客户端应用程序（浏览器扩展、移动、桌面和 CLI）的更新将在后续版本中发布：

* **用于网页密码库的用户名生成器**：使用基于电子邮件的约定（如附加寻址）或使用随机单词为新凭据生成用户名。后续版本将包括用于浏览器扩展和桌面应用程序的用户名生成器（参阅[这里](password-manager/vault-basics/username-password-generator.md)）。
* **网页密码库 - 报告页面**：我们更新了报告页面的位置和风格，以便更轻松地查找报告结果并对其采取行动（参阅[这里](password-manager/vault-administration/vault-health-reports.md)）。
* **macOS 和 Safari 导入器的改进**：我们修复了一些导致 macOS 和 Safari 导入器无法正确导入 URL 和备注的问题。
* **可访问性改进**：此版本包括一些通过屏幕阅读器等辅助技术提高 Bitwarden 性能的更改。

## 2022-03-22

_浏览器扩展 1.57.0，移动端 2.17.0_

继上周的发布之后，针对移动应用程序和浏览器扩展发布了以下内容：

* **移动端添加帐户切换功能**：在 Android 和 iOS 上使用 Bitwarden 时，最多可登录 5 个帐户并在它们之间无缝切换（参阅[这里](my-account/log-in-and-unlock/account-switching.md)）。
* **支持 Firefox 隐私模式**：此版本包含对 Firefox 隐私窗口更强大的支持（参阅[这里](password-manager/more/use-bitwarden-in-firefoxs-private-mode.md)）。

## 2022-03-15 <a href="#2021-10-26" id="2021-10-26"></a>

_服务器 1.47.0、Web 2.27.0，桌面端 1.32.0，CLI 1.22.0，目录连接器 2.9.11_

此最新版本侧重于对单个应用程序的改进，以便您可以完全按照自己的需要使用 Bitwarden。移动应用程序和浏览器扩展的更新将在后续版本中发布：

* **来自 CLI 的密码库管理 API**：使用全新的 CLI 命令 `serve`，您可以对一整套密码库管理端点进行 API 调用（参阅[这里](password-manager/getting-started/bitwarden-cli.md#serve)）。
* **CLI 导出命令的更改**：`export` 不再要求主密码，您现在可以使用 `--password` 参数为加密导出设置自定义加密/解密密码（参阅[这里](password-manager/getting-started/bitwarden-cli.md#export)）。
* **新的导入器**：我们为 Dashlane `.csv` 文件和 1Password .`1pux` 文件（要求 1Password v8.5+）增加了自定义导入器。
* **Myki 导入器的改进**：参阅[这里](https://github.com/bitwarden/jslib/pull/707)。
* **弃用工件绑定**：出于安全考虑，已删除 SAML SSO 配置的工件绑定（参阅[这里](https://github.com/bitwarden/server/pull/1885)）。
* **支持 Docker Compose v2**

## 2022-02-08 <a href="#2021-10-26" id="2021-10-26"></a>

_服务器 1.46.0、Web 2.26.0，桌面端 1.31.0，浏览器扩展 1.56.0，移动端 2.16.0，CLI 1.21.0，目录连接器 2.9.9_

2022 年初始，Bitwarden 很高兴地发布以下内容：

* **桌面端帐户切换**：在 Bitwarden 桌面应用程序中一次性登录最多 5 个帐户。此功能在 Bitwarden 应用程序中分阶段推出，很快将适用于更多其他应用程序（参阅[这里](my-account/log-in-and-unlock/account-switching.md)）。
* **iOS 上的 Send**：现在可以直接从 iOS 的共享菜单分享 Bitwarden Send（参阅[这里](password-manager/bitwarden-send/create-a-send.md)）。
* **从移动端删除帐户**：您现在可以从移动应用程序中删除您的 Bitwarden 帐户，但您为什么要这样做（参阅[这里](my-account/plans-and-pricing/delete-an-account-or-organization.md)）？
* **新的图标**：我们使用全新的图标更新了所有 Bitwarden 应用程序的外观。尽情欣赏！
* **目录连接器 - Azure AD 同步性能**：针对 Azure Active Directory 的目录连接器同步，性能已得到提升。与 Azure AD 同步的组织_将不再_需要更改其同步配置。
* **后端改进**：我们一直在努力改进 Bitwarden 平台的总体性能和稳定性，这将在未来推出一些很棒的新功能。

## 2012-12-07 <a href="#2021-10-26" id="2021-10-26"></a>

_服务器 1.45.0、Web 2.25.0，桌面端 1.30.0，浏览器扩展 1.55.0，移动端 2.15.0，CLI 1.20.0_

Bitwarden 很自豪地宣布在 12 月的版本中增加了新的企业功能，为企业计划增加了灵活性和价值。

* &#x20;[**Key Connector**](admin-console/login-with-sso/key-connector/about-key-connector.md)：(_仅适用于自托管组织_）当使用带有客户管理加密的 SSO 登录时，作为使用主密码解密密码库的一个替代方案，自托管 Key Connector 应用程序向 Bitwarden 客户端提供加密密钥（参阅[这里](admin-console/login-with-sso/key-connector/about-key-connector.md)）。
* **用于企业的家庭**：(_目前仅适用于云托管组织，未来版本的自托管_）从这个版本开始，企业组织的成员可以兑换一个与最多 5 个朋友或家庭成员共享的免费 [Bitwarden 家庭组织](my-account/plans-and-pricing/about-bitwarden-plans.md#families-organizations)。家庭组织包括所有 6 个用户的所有高级功能和无限制的安全数据共享（参阅[这里](my-account/plans-and-pricing/redeem-families-sponsorship.md)）。
* **MacOS 和 Safari 导入器**：我们为从 Safari 和 macOS 导出的密码增加了一个自定义导入器（详情见[这里](password-manager/import-and-export/import-guides/import-data-from-macos-safari.md)）。
* **新的自定义字段类型**：链接型自定义字段可用于解决您的浏览器扩展在自动填写特定网站的用户名和密码时遇到的问题，方法是将用户名和密码链接到定制的表单元素（参阅[此处](<password-manager/auto-fill/Auto-fill Custom Fields.md#using-linked-custom-fields>)）。
* **浏览器扩展 - 自动填充时解锁密码库**：当您尝试在密码库被锁定时使用上下文菜单或键盘快捷键进行自动填充，现在将提示您解锁密码库，并在解锁后自动填写您的凭证。

## 2021-10-26 <a href="#2021-10-26" id="2021-10-26"></a>

_服务器 1.44.0，Web 2.24.0，桌面 端1.29.0，浏览器扩展 1.54.0，移动端 2.14.0，CLI 1.19.0_

很高兴 Bitwarden 团队发布了一系列新功能和更新，以继续我们让个人和企业的密码管理变得简单易用的使命：

{% hint style="info" %}
**弃用公告**：业务门户已弃用。企业组织可以通过组织**管理**选项卡配置[策略](admin-console/organization-basics/enterprise-policies.md)和 [SSO 登录](admin-console/login-with-sso/about-login-with-sso.md)。
{% endhint %}

* **密码库超时策略**：密码库超时策略将为您组织的所有成员应用最长的密码库超时持续时间（参阅[这里](admin-console/organization-basics/enterprise-policies.md#vault-timeout)）。
* **禁用个人密码库导出策略**：禁用个人密码库导出策略将禁止您组织的非所有者/非管理员成员导出私人密码库数据（参阅[这里](admin-console/organization-basics/enterprise-policies.md#disable-personal-vault-export)）。
* **自动扩展组织席位**：团队和企业组织将在邀请新用户时自动扩展用户席位。组织可以设置扩展限制，以防止席位数量超过指定的数量（参阅[这里](admin-console/user-management/user-management.md)）。
* **自定义密码库超时**：您现在可以为密码库超时指定自定义时间范围（小时和分钟）（参阅[这里](my-account/log-in-and-unlock/vault-timeout-options.md#vault-timeout)）。
* **自定义角色 - 改进的集合权限**：自定义角色的集合管理权限已扩展为包括对用户是否可以创建、编辑或删除已分配的集合或所有集合的精细控制（参阅[这里](my-account/log-in-and-unlock/vault-timeout-options.md#vault-timeout)）。
* **管理员密码重置 - 重置后更新密码**：管理员重置的密码现在必须由他们所属的用户在登录 Bitwarden 时立即更新（参阅[这里](admin-console/user-management/admin-password-reset.md#after-a-password-reset)）。
* **浏览器扩展 - 自动填充 Span 元素**：浏览器扩展现在可以在 HTML `<span>` 元素的 innerText 中自动填充[自定义字段](password-manager/vault-basics/custom-fields.md)（参阅[这里](<password-manager/auto-fill/Auto-fill Custom Fields.md#html-span-elements>)）。
* &#x20;**浏览器扩展 - 自动生物识别提示**：浏览器扩展现在可以在打开时自动提示您生物识别输入。您可以从 **⚙️设置**菜单切换此行为（参阅[这里](my-account/log-in-and-unlock/unlocking-with-biometrics.md)）。
* **网页密码库 - 黑暗模式**：网页密码库现在拥有黑暗模式（参阅[这里](password-manager/more/change-app-theme.md)）。
* **CLI - `generate` 密码短语选项**： `bw generate --passphrase` 命令现在包含 `--capitalize` 和 `--includeNumber` 选项（参阅[这里](password-manager/getting-started/bitwarden-cli.md#generate)）。

## 2021-09-21

_服务器 1.43.0，Web 2.23.0，桌面端 1.28.3，浏览器扩展 1.53.0，移动端 2.13.0，CLI 1.18.1_

Bitwarden 的最新版本侧重于对现有功能进行经常性的改进：

* **移动设备上的 FIDO2 WebAuthn**：iOS 和 Android 现在支持通过 FIDO2 WebAuthn 进行两步登录（参阅[这里](my-account/two-step-login/setup-guides/two-step-login-via-fido2-webauthn.md)）。
* **管理员密码重置 - 自动注册改进**：自动注册策略选项现在会阻止用户撤销管理员密码重置（参阅[这里](admin-console/user-management/admin-password-reset.md#automatic-enrollment)）。
* **浏览器扩展 - 从保存栏中选择文件夹**：您现在可以直接从浏览器扩展的保存提示中选择要将项目保存到哪个[文件夹](password-manager/vault-administration/folders.md)（参阅[这里](password-manager/getting-started/getting-started-browserext.md#add-a-login)）。
* **浏览器扩展 - 上下文菜单项目自定义字段**：您现在可以直接从浏览器扩展的上下文菜单中复制 HTML 元素名称，以便轻松创建自定义字段（参阅[这里](password-manager/vault-basics/custom-fields.md#custom-field-names)）。
* **网页密码库 - 策略位置更改**：现在只能从组织的**管理 → 策略**界面配置[企业策略](admin-console/organization-basics/enterprise-policies.md)，而不能从业务门户配置。
* **CAPTCHA 验证**：从这个版本开始，我们将开启 [hCaptcha](https://www.hcaptcha.com/about) 验证以防止诸如撞库之类的机器人攻击。请注意，CLI 中的挑战与其他客户端应用程序中的挑战不同（有关 CLI 的详细信息，请参阅[此处](miscellaneous/cli-authentication-challenges.md)）。

## 2021-08-18 <a href="#2021-06-29" id="2021-06-29"></a>

{% hint style="success" %}
有兴趣成为提供商吗？首先，我们要求：

* 您的企业有一个活跃的企业组织。&#x20;
* 您的企业有一个客户准备在您的提供商下入职。

如果您还没有准备好开始成为提供商，Bitwarden 团队希望支持你作为一个经销商或客户的 Bitwarden 之旅。

[联系我们](https://bitwarden.com/contact)
{% endhint %}

Bitwarden 的最新版本专注于使托管服务提供商（MSP）能够支持其客户的密码管理需求：

* **提供商门户**：提供商门户网站允许托管服务提供商（MSP）和经销商代表客户创建和管理组织。使用该门户，提供商可以无缝地支持多个客户的凭证管理（参阅[这里](provider-portal/get-started-with-provider-portal.md)）。
* **共享用词的变化**：我们将**共享**按钮更新为**移动到组织**，以明确共享项目是由组织所拥有的。此外，我们还将「已共享项目」的指示符号（）更改为与集合的指示符号（）保持一致。
* **CLI `move` 命令**：为了与上述条目保持一致，CLI 的 `share` 命令已被更改为 `move`（参阅[这里](password-manager/getting-started/bitwarden-cli.md#move)）。

## 2021-06-29 <a href="#2021-06-29" id="2021-06-29"></a>

Bitwarden 团队很高兴地宣布推出管理员密码重置功能，这是一项最新功能，旨在帮助需要大规模地确保密码安全的企业。此次发布包括：

* **管理员密码重置**：企业组织可以注册管理员密码重置功能，以允许指定的管理员重置组织用户的主密码（参阅[这里](admin-console/user-management/admin-password-reset.md)）。
* **主密码重新提示**：使用新的主密码重新提示选项，要求验证您的主密码才能查看被用户指定的敏感密码库项目。（参阅[这里](password-manager/vault-basics/vault-items.md#protect-individual-items)）。
* **批量用户管理**：组织所有者和管理员现在可以从组织中批量重新发送邀请、确认已接受的用户以及移除用户（参阅[这里](admin-console/user-management/user-management.md#onboard-users)）。
* **事件日志导出**：直接从网页密码库导出事件日志（参阅[这里](admin-console/organization-basics/event-logs.md#export-events)）。
* **目录连接器 API 密钥认证**：从此版本开始，目录连接器的用户将需要使用[组织 API 密钥](admin-console/bitwarden-public-api.md#authentication)才能登录。
* **目录连接器同步限制增加**：目录连接器现在可以同步无限数量的用户或群组，之前的限制被设置为 2000。要同步 2000 以上的用户或群组，请切换到新的同步选项（参阅[这里](admin-console/user-management/directory-connector/sync-options-and-filters.md#large-syncs)）。
* **页面加载时自动填充功能的增强**：浏览器扩展的页面加载时自动填充功能已升级，可以更灵活地满足用户的独特需求（参阅[这里](password-manager/auto-fill/auto-fill-logins-in-browser-extensions.md#on-page-load)）。
* **更多 CLI 选项**：我们添加了一些新的 CLI 选项，包括轻松检索密码库项目的备注（`bw get notes <id>`）和设置 Send 的最大访问计数的功能（`bw send create --maxAccessCount <#>`）。
* **Web 开发人员自动填充排除**：Web 开发贡献者现在可以通过向 `<input>` 元素添加 `data-bwignore` 属性（例如 `data-bwignore="true"`）来阻止浏览器扩展自动填充给定的表单元素。

## 2021-05-11 <a href="#2021-05-11" id="2021-05-11"></a>

很高兴 Bitwarden 团队发布了一系列新功能和更新，以继续我们让个人和企业的密码管理变得简单易用的使命：

* **Send 隐私 & 安全选项**：使用新的 Send 隐私选项以对接收者隐藏您的电子邮件地址（参阅[这里](password-manager/bitwarden-send/send-privacy.md#hide-email)）。为了防止滥用，文件 Send 现在将需要一个经过验证的电子邮件地址。此外，企业组织可以实施一条新的策略来设置隐藏电子邮件选项的可用性（参阅[这里](admin-console/organization-basics/enterprise-policies.md#send-options)）。
* **FIDO 更新 & 扩展支持**：我们的 FIDO 实施已经从 FIDO U2F 升级为 FIDO2 WebAuthn，但现有的 FIDO U2F 密钥将保留其完整性。对 FIDO 的支持已经扩展到更多的浏览器扩展和 Windows 桌面应用程序（参阅[这里](my-account/two-step-login/setup-guides/two-step-login-via-fido2-webauthn.md)）。
* **用于密钥的自定义字段**：自定义字段的值已经升级到支持多达 5000 个字符，允许存储像 RSA 4096 位 SSH 密钥这样的密钥（参阅[这里](password-manager/vault-basics/custom-fields.md#custom-fields-for-keys)）。
* **文件大小增加**：现在可以创建最大 500 MB 的文件附件或文件 Send。由于设备限制，移动应用程序仍采用旧的 100 MB 限制。
* **禁用浏览器扩展计数器**：使用 **⚙️设置 → 选项**菜单中的新开关来禁用浏览器扩展的角标计数器（参阅[这里](password-manager/auto-fill/auto-fill-logins-in-browser-extensions.md)）。
* **Safari 的生物识别**：Safari 网页扩展现在包含对 Safari 14+ 生物识别解锁的支持（参阅[这里](my-account/log-in-and-unlock/unlocking-with-biometrics.md)）。
* **搜索国际化**：现在可以使用 1 个字符搜索密码库，改善了使用 1 个字符单词的语言（如简体中文和繁体中文）的使用体验。
* **弱密码报告排序**：弱密码报告现在按照密码弱性的严重程度来排序（参阅[这里](password-manager/vault-administration/vault-health-reports.md#weak-passwords-report)）。

{% hint style="warning" %}
由于附件升级，通过最新的客户端上传的附件无法在旧版本的客户端上打开。如果你发现你无法访问最近创建的附件，请将你的客户端升级到最新版本。（**提示**：云网页密码库总是为最新版本。）

**冻结的或旧版的客户端**，包括 Safari 13（或更早）macOS 桌面应用程序和应用程序扩展，将不支持访问这些附件。
{% endhint %}

{% hint style="info" %}
自从 2020 年实施软删除以来，我们一直在耐心地对待回收站。**从 2021 年 5 月 15 日开始**，我们将激活夜间作业，该作业将永久删除你的回收站中已存在 30 天或更长时间的项目。

在 2021 年 5 月 15 日之前，我们建议您在回收站中进行挖掘，以寻找你可能想要恢复的任何内容！
{% endhint %}

## 2021-03-11 <a href="#2021-03-11" id="2021-03-11"></a>

Bitwarden 自豪地宣布我们发布了 Bitwarden Send，一个用于短暂共享的端到端加密解决方案。此次发布包括：

* **Bitwarden Send**：Bitwarden Send 是一个用于短暂共享的端到端加密解决方案。在我们的网站和帮助中心有很多关于 Send 的资料，但你可以从[这里](password-manager/bitwarden-send/about-send.md)开始。
* **FIDO U2F 支持 Edge**：FIDO U2F 方式的两步登录现在可以用于微软 Edge 中的网页密码库和浏览器扩展（参阅[这里](my-account/two-step-login/setup-guides/two-step-login-via-fido2-webauthn.md)）。
* **浏览器扩展中的域名排除**：Bitwarden 浏览器扩展现在可以对其明确不提供记住密码的域名进行配置（参阅[这里](password-manager/more/exclude-domains.md)）。
* **改进的导入错误消息**：最近有很多人迁移到 Bitwarden，所以我们清理了一个导入错误的消息，以帮助你更快地解决问题（参阅[这里](password-manager/import-and-export/import-data-to-your-vault.md#length-related-import-errors)）。
* **Safari 网页扩展移植**：我们的 Safari 应用程序扩展已经正式移植到 Safari 14 以上版本的网页扩展中使用。由于 Safari 的变化，网页扩展的使用现在仅限于那些通过 Mac App Store 下载获取的应用（参阅[这里](password-manager/more/safari-web-extension.md)）。

## 2021-01-19 发行后的更新 <a href="#2021-01-19-post-release-update" id="2021-01-19-post-release-update"></a>

{% hint style="info" %}
如果您拥有最新版（2021-01-19）的桌面应用程序，则浏览器扩展的生物识别解锁**仅适用于基于 Chromium 的浏览器**（比如 Chrome、Edge）上安装的 v1.48.0 版本的浏览器扩展。

当您的浏览器扩展更新到这个版本时，您可能会被要求接受一个新的权限，以便 Bitwarden `Communicate with cooperating native applications（与本机应用程序通信）`。这个权限是安全的，也是**可选的**，它允许浏览器扩展与 Bitwarden 桌面应用程序进行通信，而这是启用生物识别解锁所必需的（参阅[这里](my-account/log-in-and-unlock/unlocking-with-biometrics.md#browser-extensions)）。拒绝此权限也将允许您使用 v1.48.0 扩展，只是不带生物识别解锁功能。

**生物识别解锁当前不适用于：**

* 版本低于 87 的 Firefox 浏览器扩展
* Microsoft App Store 桌面应用程序（从 [bitwarden.com/download](https://bitwarden.com/download) 获取的侧面加载的 Windows 桌面应用程序可以正常工作）
* 侧面加载的 macOS 桌面应用程序（App Store 桌面应用程序可以正常工作）

Bitwarden 团队正在调查这些问题，并将随着情况的进展提供更新。
{% endhint %}

## 2021-01-19

自 2021 年的第一个主要版本以来，Bitwarden 团队合并了多项重大改进，以满足所有用户的关键需求，其中包括：

* **紧急访问**：Bitwarden 新增的紧急访问功能使用户可以指定和管理受信任的紧急联系人，紧急联系人可以在零知识/零信任环境中请求访问其密码库（参阅[这里](my-account/more/emergency-access.md)）。
* **加密导出**：个人用户和组织现在可以将密码库数据导出到加密的 `.json` 文件中（参阅[这里](password-manager/import-and-export/encrypted-exports.md)）。
* **新的角色**：现在可以使用自定义角色来对用户权限进行粒度控制（参阅[这里](admin-console/user-management/user-types-and-access-control.md#custom-role)）。
* **新的企业策略**：现在，企业组织可以使用个人所有权策略（参阅[这里](admin-console/organization-basics/enterprise-policies.md#personal-ownership)）。
* **浏览器扩展的生物识别解锁**：通过与本机桌面应用程序的集成，您现在可以使用生物识别输入来解锁基于 Chromium 的浏览器扩展（参阅[这里](my-account/log-in-and-unlock/unlocking-with-biometrics.md#browser-extensions)）。

## 2020-11-12

最新版本的 Bitwarden 为所有客户端应用程序添加了与 SSO 相关的增强功能，包括：

* **新的企业策略**：单一组织和单点登录（SSO）认证策略现在可供企业组织使用（参阅[这里](admin-console/organization-basics/enterprise-policies.md)）。
* **用于 CLI 的 API 密钥**：使用从你的网页密码库中新获得的 API 密钥来验证进入 Bitwarden CLI（参阅[这里](miscellaneous/personal-api-key-for-cli-authentication.md)）。
* **SSO 入职改进**：我们对用户通过 SSO 入职的方式进行了一些改进，以预防潜在的安全风险（参阅[这里](https://github.com/bitwarden/server/pull/945)）。
* **GDPR 确认**：从现在开始，Bitwarden 的新用户在注册时将被要求确认隐私政策。
* **Android 11 内嵌自动填充**：对于使用 Android 11+ 的设备，启用自动填充服务将为也支持[此功能](https://developer.android.com/guide/topics/text/ime-autofill#workflow)的 IME 显示内嵌建议（参阅[这里](https://github.com/bitwarden/mobile/pull/1145)）。

## 2020-9-30

最新版本的 Bitwarden 为所有客户端应用程序以及网页密码库业务门户增加了备受期待的 **SSO 登录**功能。阅读这篇[博客文章](https://bitwarden.com/blog/post/bitwarden-launches-sso-authentication/)了解关于 SSO 登录的更多信息，同时也可参考我们的[文档](admin-console/login-with-sso/)。

## 2020 早期 <a href="#early-2020-releases" id="early-2020-releases"></a>

在 2020 年 3 月至 9 月之间发布了以下项目：

* [企业策略](admin-console/organization-basics/enterprise-policies.md)
* [密码库超时选项](my-account/log-in-and-unlock/vault-timeout-options.md)
* [回收站功能](password-manager/vault-basics/vault-items.md#delete-a-vault-item)
* [密码查看权限 - ](admin-console/user-management/user-types-and-access-control.md#granular-access-control)[隐藏密码](admin-console/user-management/user-types-and-access-control.md#granular-access-control)
* [桌面版应用程序的触控 ID/Windows Hello](my-account/log-in-and-unlock/unlocking-with-biometrics.md#desktop-applications)

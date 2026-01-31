# 客户端 App 设置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/app-settings/)
{% endhint %}

以下章节列出了 Bitwarden Password Manager App 可用的设置：

## 浏览器扩展 <a href="#browser-extension" id="browser-extension"></a>

<details>

<summary><strong>账户安全</strong></summary>

* **解锁选项**：
  * **使用生物识别解锁**：设置[生物识别解锁](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
    * **启动时提示生物识别**：允许在首次启动时使用生物识别解锁 Bitwarden。
  * **使用 PIN 码解锁**：设置 [PIN 码解锁](../../account/log-in-and-unlock/more-unlock-options/unlock-with-pin.md)。
    * **浏览器重启时要求主密码**：在首次启动时要求使用主密码解锁 Bitwarden。
* **密码库超时**：
  * **超时时间**：设置 Bitwarden 在[超时前](../../account/log-in-and-unlock/vault-timeout-options.md#session-timeout)保持活动的时长。
  * **超时动作**：设置 Bitwarden 在[超时时](../../account/log-in-and-unlock/vault-timeout-options.md#session-timeout-action)将执行的动作。
* **管理设备**：使用[另一台设备](../../account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)或[受信任的设备](../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)批准登录请求。
* **其他选项**：
  * **指纹短语**：查看您账户的[指纹短语](../../security/encryption/account-fingerprint-phrase.md)。
  * **两步登录**：打开网页 App 以设置[两步登录](../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)。
  * **更改主密码**：打开网页 App 以[更改您的主密码](../../account/log-in-and-unlock/your-master-password.md#change-your-master-password)。

</details>

<details>

<summary><strong>自动填充</strong></summary>

* **自动填充建议**：
  * **在表单字段显示自动填充建议**：激活[内嵌自动填充菜单](../autofill/autofill-from/autofill-from-browser-extensions.md#inline-menu)。
    * **将身份显示为建议**：在内嵌自动填充菜单中包含[身份](../autofill/more-autofill-options/auto-fill-cards-and-identities.md)。
    * **将支付卡显示为建议**：在内嵌自动填充菜单中包含[支付卡](../autofill/more-autofill-options/auto-fill-cards-and-identities.md)。
    * **选择图标时显示建议**：点击内嵌图标以激活自动填充菜单，而不仅仅是聚焦于填充字段。
* **将 Bitwarden 设为默认密码管理器**：（仅限 Chrome）[禁用浏览器的内置密码管理器](../autofill/troubleshoot-autofill/disable-a-browsers-built-in-password-manager.md)，并将 Bitwarden 设为默认。
* **在密码库视图中始终将支付卡显示为自动填充建议**：在密码库视图的自动填充建议区域显示所有支付卡。
* **在密码库视图中始终将身份显示为自动填充建议**：在密码库视图的自动填充建议区域显示所有身份。
* **自动填充快捷键**：
  * **管理快捷键**：为 Bitwarden 设置自定义键盘快捷键。
* **页面加载时自动填充**：
  * **页面加载时自动填充**：激活[页面加载时自动填充](../autofill/autofill-from/autofill-from-browser-extensions.md#on-page-load)。
  * **登录项目的默认自动填充设置**：设置项目在[页面加载时自动填充](../autofill/autofill-from/autofill-from-browser-extensions.md#on-page-load)的默认值。此默认值可以被单个项目覆盖。
* **附加选项**：
  * **显示上下文菜单选项**：允许[通过上下文菜单](../autofill/autofill-from/autofill-from-browser-extensions.md#context-menu)访问 Bitwarden 选项（通常使用右键点击）。
  * **自动复制 TOTP**：凭据被用于自动填充后，[自动将 TOTP 复制到剪贴板](../autofill/autofill-from/autofill-from-browser-extensions.md#totp-autofill)。
  * **清除剪贴板**：设置何时清除从 Bitwarden 复制到您剪贴板的内容。
  * **默认 URL 匹配检测**：设置 [Bitwarden 识别自动填充建议](../autofill/troubleshoot-autofill/forming-uris-for-autofill.md)的默认方式。
  * **屏蔽域名**：设置一个域名列表，[阻止 Bitwarden 为其使用自动填充](../autofill/more-autofill-options/blocking-autofill.md)。

</details>

<details>

<summary><strong>通知</strong></summary>

* **保存到密码库选项**：
  * **询问保存和使用通行密钥**：网站或服务支持通行密钥时，[允许 Bitwarden 创建和自动填充通行密钥](../autofill/more-autofill-options/autofill-passkeys.md)。
  * **询问添加登录**：当您使用未存储在 Bitwarden 中的凭据登录时，允许 Bitwarden [提示您新增项目](../autofill/autofill-from/autosave-from-browser-extensions.md#ask-to-add-login)。
  * **询问更新现有登录**：当使用的凭据与 Bitwarden 中存储的凭据不匹配时，允许 Bitwarden [提示您更新项目](../autofill/autofill-from/autosave-from-browser-extensions.md#ask-to-update-existing-login)。
* **排除域名**：设置一个域名列表，阻止提示添加或更新。

</details>

<details>

<summary><strong>密码库选项</strong></summary>

* **文件夹**：添加或编辑[文件夹](vault-navigation/folders.md)。
* **导入项目**：将数据[导入您的密码库](../import-and-export/import-data.md)或[导入组织](../../admin-console/manage-shared-items/import-organization-items/import-to-organization.md)。
* **导出密码库**：[从您的密码库导出](../import-and-export/export-vault-data.md)或[从您的组织中导出](../../admin-console/manage-shared-items/export-organization-items/export-organization-items.md)数据。
* **回收站**：查看[最近删除](vault-items/vault-items.md#delete)的项目。
* **立即同步**：手动触发[密码库同步](syncing-your-vault.md)。

</details>

<details>

<summary><strong>外观</strong></summary>

* **主题**：切换 Bitwarden 的颜色模式（浅色模式、深色模式或跟随系统）。
* **扩展宽度**：切换扩展窗口的宽度（默认、宽或超宽）。
* **紧凑模式（beta 版）**：压缩扩展中元素之间的空白空间。
* **在扩展图标上显示自动填充建议的登录数量**：在扩展图标上显示可用于此页面的自动填充建议的数量。
* **显示动画**：在您使用浏览器扩展时，显示动画，例如在切换视图时的滑动效果。
* **密码库自定义**
  * **显示网站图标并获取更改密码的 URL**：允许 Bitwarden 获取存储在您密码库中的凭据的[网站图标](../../security/data/website-icons.md)和[更改密码的 URL](security-tools/change-at-risk-passwords.md)。
  * **在密码库上显示快速复制操作**：在密码库视图中的每个项目上显示[用于复制用户名或密码的按钮](../autofill/autofill-from/autofill-from-browser-extensions.md#copy-credentials)。
  * **点击自动填充建议中的项目以填充**：[点击密码库视图中的项目](../autofill/autofill-from/autofill-from-browser-extensions.md#click-items)以自动填充其凭据，而不是点击「填充」按钮。

</details>

## 移动 App <a href="#mobile" id="mobile"></a>

<details>

<summary><strong>账户安全</strong></summary>

* **批准登录请求**：
  * **待处理的登录请求**：使用[另一台设备](../../account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)或[受信任的设备](../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)批准登录请求。
* **解锁选项**：
  * **使用生物识别/面容 ID/触控 ID 解锁**：设置[生物识别解锁](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
  * **使用 PIN 码解锁**：设置 [PIN 码解锁](../../account/log-in-and-unlock/more-unlock-options/unlock-with-pin.md)。
    * **App 重启时要求主密码**：首次启动时要求使用主密码解锁 Bitwarden。
* **验证器同步**：
  * **允许验证器同步**：允许 Bitwarden Password Manager 将[验证码同步到 Bitwarden Authenticator](../../bitwarden-authenticator/totp-sync.md)。
* **会话超时**：
  * **超时时间**：设置 Bitwarden 在[超时前](../../account/log-in-and-unlock/vault-timeout-options.md#session-timeout)保持活动的时长。
  * **超时动作**：设置 Bitwarden 在[超时时](../../account/log-in-and-unlock/vault-timeout-options.md#session-timeout-action)将执行的动作。
* **其他**：
  * **指纹短语**：查看您账户的[指纹短语](../../security/encryption/account-fingerprint-phrase.md)。
  * **两步登录**：打开网页 App 以设置[两步登录](../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)。
  * **更改主密码**：打开网页 App 以[更改您的主密码](../../account/log-in-and-unlock/your-master-password.md#change-your-master-password)。

</details>

<details>

<summary><strong>自动填充 (Android)</strong></summary>

* **自动填充服务**：允许 Bitwarden [使用您保存的登录信息登录](../autofill/autofill-from/autofill-from-android.md)您的设备上的 App 和网站。这将要求您在后续窗口中选择 Bitwarden 作为您首选的服务。
  * **显示自动填充建议**：选择是否在键盘（[内嵌](../autofill/autofill-from/autofill-from-android.md#inline)）或输入字段上方（[弹窗](../autofill/autofill-from/autofill-from-android.md#popup)）显示自动填充建议。
* **通行密钥管理**：打开 Android App 设置，[将 Bitwarden 设为您的首选的通行密钥提供程序](../autofill/autofill-from/autofill-from-android.md#using-passkeys)。
  * **特权 App**：了解更多有关 Bitwarden 在您使用通行密钥时如何保护您免受网络钓鱼的信息。
* **使用无障碍功能**：允许在无障碍菜单中将自动填充作为[快速操作磁贴](../autofill/autofill-from/autofill-from-android.md#quick-action-tiles)使用。这将要求您在后续窗口中为 Bitwarden 开启无障碍功能。
* **自动复制 TOTP**：凭据被用于自动填充后，自动将 [TOTP](security-tools/totp.md) 复制到剪贴板。
* **询问添加项目**：在您使用未保存在您的密码库中的凭据登录时，允许 Bitwarden 提示您保存项目。
* **默认 URI 匹配检测**：设置 [Bitwarden 识别自动填充建议](../autofill/troubleshoot-autofill/forming-uris-for-autofill.md)的默认方式。
* **阻止自动填充**：设置一个域名列表，[阻止 Bitwarden 为其使用自动填充](../autofill/more-autofill-options/blocking-autofill.md)。

</details>

<details>

<summary><strong>自动填充 (iOS)</strong></summary>

* **自动填充**：
  * **密码自动填充**：了解如何设置[自动填充](../autofill/autofill-from/autofill-from-ios.md)，然后点击**继续**进入 iOS 菜单，您将在那里进行设置。
  * **App 扩展**：了解 Safari App 扩展，然后点击**激活 App 扩展**来启用它。
* **附加选项**：
  * **自动复制 TOTP**：凭据被用于自动填充后，自动将 [TOTP](security-tools/totp.md) 复制到剪贴板。
  * **默认 URI 匹配检测**：设置 [Bitwarden 识别自动填充建议](../autofill/troubleshoot-autofill/forming-uris-for-autofill.md)的默认方式。

</details>

<details>

<summary><strong>密码库</strong></summary>

* **文件夹**：添加或编辑[文件夹](vault-navigation/folders.md)。
* **导出密码库**：[从您的密码库导出](../import-and-export/export-vault-data.md)或[从您的组织中导出](../../admin-console/manage-shared-items/export-organization-items/export-organization-items.md)数据。
* **导入项目**：打开网页 App 将数据[导入您的密码库](../import-and-export/import-data.md)或[导入组织](../../admin-console/manage-shared-items/import-organization-items/import-to-organization.md)。

</details>

<details>

<summary><strong>外观</strong></summary>

* **语言**：选择 Bitwarden App 使用的语言。
* **主题**：切换 Bitwarden 的颜色模式（浅色模式、深色模式或跟随系统）。
* **使用动态颜色**：(仅限 Android) 根据您的壁纸为 Bitwarden 应用配色方案。
* **显示网站图标**：允许 Bitwarden 获取存储在您的密码库中的凭据的[网站图标](../../security/data/website-icons.md)。

</details>

<details>

<summary><strong>其他</strong></summary>

* **允许刷新时同步**：允许使用下拉手势来[同步您的密码库](syncing-your-vault.md)。
* **清除剪贴板**：设置何时清除从 Bitwarden 复制到您剪贴板的内容。
* **允许通用剪贴板**：(仅限 iOS) 允许从 Bitwarden 移动 App 复制的数据粘贴到使用相同 Apple ID 登录的其他设备上。
* **允许屏幕截图**：(仅限 Android) 允许 Bitwarden 移动 App 出现在截图和屏幕共享中。
* **连接到 Watch**：(仅限 iOS) [将 Bitwarden 连接到您的 Apple Watch](../more/more-platforms/apple-watch-totp.md)，以便轻松访问 TOTP。
* **Siri & 快捷指令访问权限**：(仅限 iOS) 允许 Bitwarden 使用 App Intents 响应 Siri 和快捷指令。

</details>

## 桌面 App <a href="#desktop" id="desktop"></a>

<details>

<summary><strong>账户安全</strong></summary>

* **密钥库超时**：
  * **超时时间**：设置 Bitwarden 在[超时前](../../account/log-in-and-unlock/vault-timeout-options.md#session-timeout)保持活动的时长。
  * **超时动作**：设置 Bitwarden 在[超时时](../../account/log-in-and-unlock/vault-timeout-options.md#session-timeout-action)将执行的动作。
* **使用 PIN 码解锁**：设置 [PIN 码解锁](../../account/log-in-and-unlock/more-unlock-options/unlock-with-pin.md)。
* **重启时使用主密码锁定**：要求 Bitwarden 桌面 App 在首次启动时使用主密码解锁。
* **使用系统身份验证解锁**：(仅限 Linux) 设置[生物识别解锁](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
* **使用触控 ID 解锁**：(仅限 macOS) 设置[生物识别解锁](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
  * **App 重启时要求触控 ID**：(仅限 macOS) 在首次启动时自动提示使用生物识别。
* **使用 Windows Hello 解锁**：(仅限 Windows) 设置[生物识别解锁](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
  * **App 重启时要求主密码或 PIN 码**：(仅限 Windows) 要求 Bitwarden 桌面 App 在首次启动时使用主密码或 PIN 码解锁。

</details>

<details>

<summary><strong>偏好设置</strong></summary>

* **清除剪贴板**：设置何时清除从 Bitwarden 复制到您剪贴板的内容。
* **复制到剪贴板时最小化**：当您将项目数据复制到剪贴板时，自动最小化 Bitwarden。
* **显示网站图标并获取更改密码的 URL**：允许 Bitwarden 获取存储在您密码库中的凭据的[网站图标](../../security/data/website-icons.md)和[更改密码的 URL](security-tools/change-at-risk-passwords.md)。

</details>

<details>

<summary><strong>App 设置 (Linux)</strong></summary>

与**安全**和**偏好设置**不同，这些设置适用于使用桌面 App 的所有账户：

{% hint style="info" %}
在 Linux 上，**系统托盘**是位于屏幕右下角的一排快捷方式。**Dash** 是一排常用的和正在运行的 App，通常位于屏幕左侧。
{% endhint %}

* **显示托盘图标**：始终在系统托盘中显示 Bitwarden 桌面 App 图标。
* **关闭到托盘图标**：关闭窗口时，在系统托盘显示图标而不是无任何显示。
* **启动到托盘图标**：Bitwarden 桌面 App 首次启动时，在系统托盘显示图标而不是打开窗口。
* **登录时自动启动**：登录到您的计算机时，自动启动 Bitwarden 桌面 App。
* **允许浏览器集成**：(非 Safari) 允许 Bitwarden 浏览器扩展与[桌面 App 集成](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#set-up-biometrics-for-browser-extension)以进行生物识别解锁。在 Safari 中，无需激活此选项即可使用集成功能。
  * **要求浏览器集成验证**：在 Bitwarden 桌面 App 和浏览器扩展之间建立集成时，要求确认[指纹短语](../../security/encryption/account-fingerprint-phrase.md)。
* **使用硬件加速**：如果您遇到图形或性能问题，请关闭此选项。
* **启用 SSH 代理**：允许 Bitwarden 桌面 App 充当 [SSH 代理](../developer-tools/ssh/ssh-agent.md)。
* **主题**：切换 Bitwarden 的颜色模式（浅色模式、深色模式或跟随系统）。
* **语言**：选择 Bitwarden 桌面 App 使用的语言。

</details>

<details>

<summary><strong>App 设置 (macOS)</strong></summary>

与**安全**和**偏好设置**不同，这些设置适用于使用桌面 App 的所有账户：

{% hint style="info" %}
在 macOS 上，**菜单栏**是位于屏幕顶部的一排菜单。**Dock** 是一排常用的和正在运行的 App，可通过将光标移动到屏幕边缘来显示。
{% endhint %}

* **显示菜单栏图标**：始终在菜单栏中显示 Bitwarden 桌面 App 图标。
* **最小化到菜单栏**：当最小化窗口时，在菜单栏显示一个图标，而不是在 Dock 中。
* **关闭到菜单栏**：当关闭窗口时，在菜单栏显示一个图标，而不是在 Dock 的任何地方都不显示。
* **启动到菜单栏**：当 Bitwarden 桌面 App 首次启动时，在菜单栏显示一个图标，而不是打开窗口。
* **登录时自动启动**：当你登录到计算机时，自动启动 Bitwarden 桌面 App。
* **始终在 Dock 中显示**：始终在 Dock 中显示 Bitwarden 桌面 App 无论活动菜单栏选项如何。
* **允许浏览器集成**：(非 Safari) 允许 Bitwarden 浏览器扩展与[桌面 App 集成](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#set-up-biometrics-for-browser-extension)以进行生物识别解锁。在 Safari 中，无需激活此选项即可使用集成功能。
  * **要求浏览器集成验证**：在 Bitwarden 桌面 App 和浏览器扩展之间建立集成时，要求确认[指纹短语](../../security/encryption/account-fingerprint-phrase.md)。
* **使用硬件加速**：如果您遇到图形或性能问题，请关闭此选项。
* **启用 SSH 代理**：允许 Bitwarden 桌面 App 充当 [SSH 代理](../developer-tools/ssh/ssh-agent.md)。
* **允许屏幕截图**：允许 Bitwarden 桌面 App 出现在截图和屏幕共享中。关闭时，桌面 App 在大多数截图和屏幕共享中将不可见。
* **允许 DuckDuckGo 浏览器集成**：(仅限 macOS) 允许[ Bitwarden 桌面 App 与 DuckDuckGo macOS 浏览器之间](../more/more-platforms/duckduckgo-macos-browser-integration.md)的集成。
* **主题**：切换 Bitwarden 的颜色模式（浅色模式、深色模式或跟随系统）。
* **语言**：选择 Bitwarden 桌面 App 使用的语言。

</details>

<details>

<summary><strong>App 设置 (Windows)</strong></summary>

与**安全**和**偏好设置**不同，这些设置适用于使用桌面 App 的所有账户：

{% hint style="info" %}
在 Windows 上，**系统托盘**是位于屏幕右下角的一排快捷方式。**任务栏**是一排常用的和正在运行的 App，通常位于屏幕底部中间。
{% endhint %}

* **显示托盘图标**：始终在系统托盘中显示 Bitwarden 桌面 App 图标。
* **最小化到托盘图标**：当最小化窗口时，在系统托盘显示图标而不是任务栏。
* **关闭到托盘图标**：当关闭窗口时，在系统托盘显示图标而不是无任何显示。
* **启动到托盘图标**：当 Bitwarden 桌面 App 首次启动时，在系统托盘显示图标而不是打开窗口。
* **登录时自动启动**：当你登录到计算机时，自动启动 Bitwarden 桌面 App。
* **允许浏览器集成**：(非 Safari) 允许 Bitwarden 浏览器扩展与[桌面 App 集成](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#set-up-biometrics-for-browser-extension)以进行生物识别解锁。在 Safari 中，无需激活此选项即可使用集成功能。
  * **要求浏览器集成验证**：在 Bitwarden 桌面 App 和浏览器扩展之间建立集成时，要求确认[指纹短语](../../security/encryption/account-fingerprint-phrase.md)。
* **使用硬件加速**：如果遇到图形或性能问题，请关闭此选项。
* **启用 SSH 代理**：允许 Bitwarden 桌面 App 充当 [SSH 代理](../developer-tools/ssh/ssh-agent.md)。
* **允许屏幕截图**：允许 Bitwarden 桌面 App 出现在截图和屏幕共享中。关闭时，桌面 App 在大多数截图和屏幕共享中将不可见。
* **主题**：切换 Bitwarden 的颜色模式（浅色模式、深色模式或跟随系统）。
* **语言**：选择 Bitwarden 桌面 App 使用的语言。

</details>

# 浏览器扩展中的自动填充登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-browser/)
{% endhint %}

{% hint style="success" %}
如果您的浏览器扩展在自动填充特定站点的用户名和密码时遇到问题，使用[已链接的自定义字段](<Auto-fill Custom Fields.md#using-linked-custom-fields>)可以强制自动填充。

此外，基本验证提示的工作方式与常规自动填充略有不同。有关更多信息，请参阅另一篇[基本验证提示](../../../auto-fill/basic-auth-prompts.md)的文章。
{% endhint %}

Bitwarden 浏览器扩展有一个独特的**标签页**视图，它可以自动检测打开的标签页中显示的网页的 URI（例如 `google.com`），并找到所有具有相应 URI 的密码库项目。如果您不熟悉 URI 的使用，我们建议您阅读[此文](../../../auto-fill/using-uris.md)。

当一个密码库项目有对应的 URI 时，Bitwarden 图标将覆盖一个角标计数器，报告该网页所对应的密码库项目的数量（_如下图_）。

{% embed url="https://bitwarden.com/_gatsby/image/f6a740c2ca09135be71d4a61008439e6/b4b305513c1909542532d5c62739b41f/Screen%20Shot%202022-05-18%20at%203.23.12%20PM.webp?eu=d6df03b3b09aa8810b6ea4803972683be43602acaf0263d86b32e5a91ea9978e23f51f50229228b37e3b088dd0b414ec6ec279371dbfd78c95ed4ba0eb60f90a568552ef61b62656547dc2ffb8f2021069ce1259a8869a0ca4397186e6b5be2310591b2daf29bbd3ebfc606db4862667b8e2a52e3397f879e21a540c8f5c31bf6ea48f876e4fb99bf301bca2b8f84a8ec9a36e191e8eb72a2535124c1eb72cedadef43762628423e76b8ea29c522dee4596f135e270c498d2472964aff6e39c5e7afa109d1287eb4aece632283c7a788bc1caf2f20ee9e2fabd43a2e116eff51f8e92598b13c594aee28fa974eaf030028418a73d8604fda265d8f1985e328f355e22e7861&a=w%3D850%26h%3D616%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A36%3A00.883Z" %}
浏览器扩展自动填充
{% endembed %}

{% hint style="success" %}
如果需要，您可以使用 ⚙️**设置** → **选项**菜单中的显示**角标计数器**来金禁用角标计数器。
{% endhint %}

选择**标签页**视图中的密码库项目，即可将登录信息自动填入检测到的输入字段中。如果一个网页或服务具有多个关联 URI 的登录项目，Bitwarden 将始终自动填充上次使用的登录项目。

## 使用上下文菜单 <a href="#using-the-context-menu" id="using-the-context-menu"></a>

{% hint style="info" %}
此功能目前在 Safari 浏览器扩展程序中不可用。
{% endhint %}

在不打开浏览器扩展程序的情况下，您可以在用户名或密码输入栏上点击右键，然后使用 **Bitwarden** → **自动填充**选项。当您尝试此操作时，如果您的密码库已锁定，则会打开一个新的标签页，提示您解锁。解锁后，浏览器扩展将自动继续填充您的凭据。

{% embed url="https://bitwarden.com/_gatsby/image/c51dd4594b09d2e34ca4dab6bea03db5/8c4cb6cbf15a5dc6af5be4ee0a22d95b/browserext-context.webp?eu=dd8a51e3e7c8fed1593ca3856070356ab33754faf9043fd83435e2af19abc88e24fb1b5620c32cb8293f5e8c86b247ef6095706411bd84d393bd1ef6ec32ac0b55d25ebf65b57156522dc6ffb0f201413dc11d5aa186cc5ef7642386b6b1b3784c51492fac7fbdd3b9f83237b8d62d63ecb5a72e6f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32bdd2c97f37407c472c7289d02a83219fe1614469255c4003f4633fd601fb6c37c3e3adf55dda2f7de5fa9d3426d295a8d3eb4ea42a27e7d075ebdd7c395b4ff95be9a128a88c205346c534bacb1b&a=w%3D850%26h%3D560%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A36%3A19.771Z" %}
浏览器扩展上下文菜单
{% endembed %}

在使用此方法自动填充不受信任的 iframe 或 HTTP 站点（当基于该项目的已保存 URI 使用 HTTPS ）时，浏览器扩展将警告用户。

## 使用键盘快捷键 <a href="#using-keyboard-shortcuts" id="using-keyboard-shortcuts"></a>

Bitwarden 浏览器扩展提供了一组键盘快捷键（又称为_热键_）来自动填充登录信息。当您尝试此操作时，如果您的密码库已锁定，则会打开一个新的标签页，提示您解锁。解锁后，浏览器扩展将自动继续填充您的凭据。

要自动填充登录信息，请使用以下**默认**快捷键。如果检测到的 URI 匹配多个项目，最后使用的登录项目将用于自动填充操作。您可以通过反复使用键盘快捷键来循环浏览多个登录项目：

* Windows：`Ctrl + Shift + L`
* macOS：`Cmd + Shift + L`
* Linux：`Ctrl + Shift + L`

{% hint style="success" %}
如果登录使用 [Bitwarden 验证器 TOTP](../../../your-vault/totp.md)，使用 `Cmd/Ctrl+Shift+L` 在自动填充后会自动将你的 TOTP 复制到剪贴板。你要做的就是使用 `Cmd/Ctrl+V` 来粘贴！
{% endhint %}

如果任何已指定的快捷键不能使用，很可能是因为你的设备上的另一个应用程序已经占用了它。例如，Windows 上的自动填充快捷键通常被 AMD Radeon Adrenaline 软件（AMD图形驱动程序）使用，因此不能被 Bitwarden 使用。在这种情况下，您应该释放该快捷键，或者配置 Bitwarden 使用其他快捷键。

### 配置键盘快捷键 <a href="#configuring-keyboard-shortcuts" id="configuring-keyboard-shortcuts"></a>

根据你使用的浏览器不同，配置 Bitwarden 浏览器扩展程序使用的键盘快捷键也不同。要访问配置菜单：

* **在 Chrome 中**，在地址栏输入 `chrome://extensions/shortcuts`。在基于 Chromium 的浏览器（如 Brave）中，用 `chrome` 代替相应的浏览器名称（如 `brave://extensions/shortcuts`）。
* **在 Firefox 中**，在地址栏中输入 `about:addons`，选择**管理您的扩展程序**旁边的 **⚙️齿轮**图标，并从下拉菜单中选择**管理扩展程序快捷键**。

某些浏览器包括 **Safari** 和旧版 **Edge**，目前不支持更改扩展程序的默认键盘快捷键。

## 页面加载时自动填充 <a href="#on-page-load" id="on-page-load"></a>

{% hint style="warning" %}
此功能默认情况下被禁用，因为虽然它通常比较安全，但受损或不受信任的网站可能会利用此功能窃取凭据。

浏览器扩展不允许在页面加载时自动填充[不受信任的 iframe](auto-fill-logins-in-browser-extensions.md#auto-fill-in-inframes)，并且当根据[该项目的已保存 URI](../../../auto-fill/using-uris.md) 预期使用 HTTPS 时，浏览器扩展将在 HTTP 站点上自动填充之前向用户发出警告。
{% endhint %}

页面加载时自动填充是 Bitwarden 浏览器扩展提供的一个**实验性的和可选的**功能。页面加载时自动填充功能将在加载与登录项目的 URI 值对应的网页时自动填充登录信息。启用后，您可以设置其默认的行为（即对所有密码库项目开启或对密码库项目关闭）。

要启用此功能，请导航到浏览器扩展中的**设置** → **选项**，勾选**页面加载时自动填充**选项，然后选择默认行为。启用并设置默认行为后，您还可以为每一个单独的密码库项目指定页面加载时的自动填充行为：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5PxR0j79XtzMCrF4R6xUtu/c530d1df7e7b34aac88336213740b62a/onpageloadfull.png?fm=webp&h=822&q=50&w=1398" %}
页面加载选项
{% endembed %}

使用此约定，您可以将浏览器扩展设置为，例如：

* 仅针对选定的少数几个项目执行页面加载时自动填充（即对所有密码库项目**默认关闭**，并对选定的项目**手动打开**）。
* 针对除选定的少数几个项目之外的所有项目执行页面加载时自动填充（即对所有密码库项目**默认打开**，并对选定的项目**手动关闭**）。

## 手动自动填充 <a href="#manually-auto-fill" id="manually-auto-fill"></a>

您可以手动自动填充没有保存 URI 的项目，方法是在 **🔒我的密码库**视图中打开它，然后选择**自动填充**按钮。

浏览器扩展在使用此方法自动填充不受信任的 iframe 或 HTTP 站点（当基于该项目的已保存 URI 使用 HTTPS ）时，将警告用户。

## TOTP 自动填充 <a href="#totp-auto-fill" id="totp-auto-fill"></a>

如果您使用 [Bitwarden 验证器](../../../your-vault/totp.md)，浏览器扩展将自动填充您的 TOTP 代码（前提是您使用上下文菜单、键盘快捷键或手动自动填充）。**如果您使用页面加载时自动填充功能，浏览器扩展将不会自动填充您的 TOTP 代码**。

默认情况下，自动填充登录信息时，您的 TOTP 也会被复制到剪贴板。如果您使用页面加载时自动填充功能，这是推荐的工作流程。

{% hint style="success" %}
可以使用**设置** → **选项** → **自动复制 TOTP** 关闭自动 TOTP 复制，默认情况下它是打开的。此外，使用旁边的**清除剪贴板**选项设置清除复制值的时间间隔。
{% endhint %}

## 自动填充框架 <a href="#auto-fill-in-inframes" id="auto-fill-in-inframes"></a>

浏览器扩展会悄悄地禁用不受信任的 iframe 的[页面加载自动填充](auto-fill-logins-in-browser-extensions.md#on-page-load)，如果用户使用键盘快捷键、上下文菜单或直接从浏览器扩展手动触发自动填充，则会警告用户有关 iframe 的信息。

「不受信任」的 iframe 被定义为 `src=""` 值与登录项目的 URI 不匹配的 iframe，如全局设置或特定于项目的[匹配检测行为](../../../auto-fill/using-uris.md#match-detection-options)所指示的那样。

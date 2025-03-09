# 浏览器扩展中的自动填充登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-browser/)
{% endhint %}

{% hint style="success" %}
如果您的浏览器扩展在自动填充特定站点的用户名和密码时遇到问题，使用[已链接的自定义字段](<Auto-fill Custom Fields.md#using-linked-custom-fields>)可以强制自动填充。

此外，基本验证提示的工作方式与常规自动填充略有不同。有关更多信息，请参阅另一篇[基本验证提示](../../../auto-fill/basic-auth-prompts.md)的文章。
{% endhint %}

使用 Bitwarden 浏览器扩展有很多自动填写凭据的方法！最基本的方法是在网站登录页面打开 Bitwarden 浏览器扩展，在**密码库**选项卡中选择建议项目的**填充**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1pamjhdWn7obh8UBxXcIPF/cb72c2921ce5f717cfd81bf157e50f4d/2024-12-02_13-59-23.png?_a=DAJCwlWIZAAB" %}
浏览器扩展自动填充
{% endembed %}

请注意，当您在试图登录的网站上保存有登录信息时，Bitwarden 浏览器扩展会覆盖一个通知气泡，报告您在该网站上的登录信息的数量。这些项目将显示在**自动填充建议**的顶部。您可以使用过筛选器下拉菜单筛选建议中的内容和所有项目列表中的显示内容，这些下拉菜单可以通过 **☷**&#x6309;钮显示或隐藏：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/12UsFuA2sxbUCBMIczJsxv/22c20404137193420d3b2d1f5fa8611f/2024-12-02_14-07-09.png?_a=DAJCwlWIZAAB" %}
浏览器扩展筛选器和建议
{% endembed %}

{% hint style="success" %}
如果需要，您可以在 ⚙️**设置** → **外观**菜单中的**在扩展图标上显示自动填充建议的登录数量**切换按钮来隐藏角标计数器。
{% endhint %}

选择**填充**按钮将在检测到的输入字段中自动填充信息。如果一个网页或服务有多个带有关联 URI 的项目，Bitwarden 将始终自动填充上次使用的登录项目。

## 自定义自动填充行为

### 单击项目以自动填充 <a href="#customizing-autofill-behaviorclick-items-to-autofill" id="customizing-autofill-behaviorclick-items-to-autofill"></a>

您可以将浏览器扩展设置为在选择密码库项目时自动填充，而不是使用**填充**按钮。要激活此选项，请导航至**设置** → **外观**，然后切换**在自动填充建议中单击项目以自动填充**选项。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3tnagVMjtTufvRCrih3ctQ/b3698262ce7c19baeda6afc87c485167/2025-01-02_11-14-19.png?_a=DAJCwlWIZAAB" %}
单击项目以自动填充
{% endembed %}

激活后，从密码库视图中选择项目时（而不是使用**填充**按钮）将自动填充此项目。可以使用 **≡**&#x9009;项菜单来**查看**此项目。

### 快速复制操作 <a href="#quick-copy-actions" id="quick-copy-actions"></a>

除**填充**按钮外，您还可以使用**密码库**选项卡上的三个快速复制操作按钮，以专门将用户名、密码或验证码复制到剪贴板：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5w7lobEk81aOGfLKFjRp2e/07041024e69f8fae1892b7b56c7ff898/2024-12-17_09-32-41.png?_a=DAJCwlWIZAAB" %}
快速复制操作
{% endembed %}

默认情况下，显示这些按钮的选项是关闭的，可以通过导航到**设置** → **外观**，然后将**在密码库上显示快速复制操作**选项切换为打开来激活。

## 内嵌自动填充菜单 <a href="#inline-auto-fill-menu" id="inline-auto-fill-menu"></a>

使用内嵌自动填充菜单可以快速输入来自您 Bitwarden 密码库中的登录凭据、通行密钥以及 TOTP 代码。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/H7DjdJNvQH00yGNLf5gsC/1ec6f0ce9a94862b0cae1d8b8d679fc8/2024-10-29_14-41-02.png?_a=DAJCwlWIZAAB" %}
内嵌自动填充菜单
{% endembed %}

### 启用内嵌自动填充菜单 <a href="#enable-the-inline-auto-fill-menu" id="enable-the-inline-auto-fill-menu"></a>

要启用内嵌自动填充菜单：

1、登录并解锁 Bitwarden [浏览器扩展](../../../getting-started/getting-started-browserext.md)。

2、选择 **⚙️设置** → **自动填充**，然后定位到**在表单字段显示自动填充建议**下拉菜单。选择您首选的自动填充菜单行为。

3、如果您希望内嵌自动填充菜单建议这些项目类型，还可以切换**将身份显示为建议**和**将支付卡显示为建议**选项。在[这里](auto-fill-cards-and-identities.md#using-the-inline-menu)了解更多信息。

4、下一步，我们建议您禁用浏览器的自动填充选项。如果您的浏览器的自动填充功能已启用，它可能会与 Bitwarden 的自动填充菜单产生冲突。在[这里](../../../auto-fill/disable-a-browsers-built-in-password-manager.md)了解更多信息。

Chrome 和 Brave 用户可以勾选**覆盖浏览器的自动填充设置**选项来禁用浏览器自带的自动填充。

### 使用内嵌自动填充菜单 <a href="#use-the-inline-auto-fill-menu" id="use-the-inline-auto-fill-menu"></a>

{% tabs %}
{% tab title="使用内嵌自动填充登录" %}
使用内嵌自动填充菜单登录账户：

1、选择登录表单的用户名字段。如果您尝试登录时密码库已锁定，菜单会提示您解锁密码库。

2、将显示内嵌自动填充菜单。此时，请选择您希望在网站上使用的登录名或密码。

{% hint style="info" %}
没有看到您想使用的登录凭据吗？编辑密码库项目并选择**自动填充和保存**，或在 URI 字段中手动输入网站。
{% endhint %}

3、如果没有为该网站保存凭据，请选择✚**新建项目**，浏览器扩展将打开一个新的项目，您可以在其中保存新的登录凭据。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1nVpqyl5FuzMPIaKezwZ8c/8a715cb0b1e1423815f0b66b0e8b1b42/web-browser-extension-autofill-newitem.png?_a=DAJCwlWIZAAB" %}

当基于该项目的[已保存 URI](../../../auto-fill/using-uris.md) 预期使用 HTTPS 时，浏览器扩展将在用户使用此方法自动填充[不受信任的 iframe](auto-fill-logins-in-browser-extensions.md#auto-fill-in-inframes) 或 HTTP 站点之前发出警告。

{% hint style="info" %}
如果内嵌自动填充菜单对浏览器造成意外干扰，可按 Esc 键关闭。
{% endhint %}
{% endtab %}

{% tab title="使用内嵌自动填充 TOTP" %}
要使用内嵌自动填充功能自动填充 TOTP 代码：

1、在登录表单中选择 TOTP 字段。

2、将显示内联自动填写菜单，选择 TOTP 代码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3RaBZBRgkfwVF0mQPRZYBJ/840a46c911d09ead87ac09fdb0955493/2025-01-03_09-22-34.png?_a=DAJCwlWIZAAB" %}
TOTP 内嵌自动填充单次登录
{% endembed %}

3、如果此网站有多个登录，内嵌自动填充菜单将显示每一个登录的 TOTP 代码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1rc2rXC3daH5mcEZNRgbv1/db47ffbb4a3b987ff2e3e7842900ceb6/2025-01-02_17-23-28.png?_a=DAJCwlWIZAAB" %}
内嵌 TOTP 自动填充
{% endembed %}
{% endtab %}

{% tab title="使用内嵌自动填充创建账户" %}
要使用内嵌自动填充菜单创建一个新的账户：

1、在登录表单的用户名字段中输入用户名。然后，选择密码字段。

2、将显示内嵌自动填充菜单。如果对生成的密码满意，请选择**填充生成的密码**。您也可以使用 **⟳**&#x751F;成按钮生成新的密码，直到满意为止：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2JcceqWgFbk4ViLCMe6qm5/ce116e8ff337f90fbbd57b52aa15fdcd/2024-11-05_10-07-08.png?_a=DAJCwlWIZAAB" %}

{% hint style="success" %}
该选项将使用您在浏览器扩展的**生成器**选项卡中配置的设置。了解[如何更改这些设置](../../vault-basics/generator.md#password-types)。
{% endhint %}

3、**在点击「注册」或「创建账户」提交表单之前**，内嵌自动填充菜单将提供在 ✚**新增登录**中保存此信息的选项。使用该选项可在弹出窗口中打开 Bitwarden，然后选择**保存**按钮保存生成的凭证：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7cMSUQLfvxHNwHS8xMX1j7/296b7fdfcb384808284aa3f5e67d769a/2024-11-05_10-12-29.png?_a=DAJCwlWIZAAB" %}
保存登录到 Bitwarden
{% endembed %}

4、选择注册、创建账户或网站或应用程序提供的其他按钮来完成账户的创建。
{% endtab %}
{% endtabs %}

## 上下文菜单 <a href="#context-menu" id="context-menu"></a>

{% hint style="info" %}
此功能目前在 Safari 浏览器扩展程序中不可用。
{% endhint %}

在不打开浏览器扩展程序的情况下，您可以在用户名或密码输入栏上点击右键，然后使用 **Bitwarden** → **自动填充**选项。当您尝试此操作时，如果您的密码库已锁定，则会打开一个新的标签页，提示您解锁。解锁后，浏览器扩展将自动继续填充您的用户名、密码、支付卡或身份信息。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6GKKvIe7GwwOBtp9gmh862/4d39f59a8a862bb83d53e50f9f68d107/2024-12-03_09-12-06.png?_a=DAJCwlWIZAAB" %}
浏览器扩展上下文菜单
{% endembed %}

当基于该项目的[已保存 URI](../../../auto-fill/using-uris.md) 使用 HTTPS 时，浏览器扩展将在用户使用此方法自动填充[不受信任的 iframe](auto-fill-logins-in-browser-extensions.md#auto-fill-in-inframes) 或 HTTP 站点时发出警告。

## 键盘快捷键 <a href="#keyboard-shortcuts" id="keyboard-shortcuts"></a>

Bitwarden 浏览器扩展提供了一组键盘快捷键（又称为热键）来自动填充登录信息。当您尝试此操作时，如果您的密码库已锁定，则会打开一个弹出窗口，提示您解锁。解锁后，浏览器扩展将自动继续填充您的凭据。

当基于该项目的[已保存 URI](../../../auto-fill/using-uris.md) 预期使用 HTTPS 时，浏览器扩展将在用户使用此方法自动填充[不受信任的 iframe](auto-fill-logins-in-browser-extensions.md#auto-fill-in-inframes) 或 HTTP 站点之前发出警告。

要自动填充登录信息，请使用以下**默认**快捷键。如果检测到的 URI 匹配多个项目，最后使用的登录项目将用于自动填充操作。您可以通过反复使用键盘快捷键来循环浏览多个登录项目：

* Windows：`Ctrl + Shift + L`
* macOS：`Cmd + Shift + L`
* Linux：`Ctrl + Shift + L`

{% hint style="success" %}
如果登录使用 [Bitwarden 验证器](../../../your-vault/totp.md) TOTP，使用 `Cmd/Ctrl+Shift+L` 在自动填充后会自动将你的 TOTP 复制到剪贴板。您要做的就是使用 `Cmd/Ctrl+V` 来粘贴！
{% endhint %}

如果任何已指定的快捷键不能使用，很可能是因为你的设备上的另一个应用程序已经占用了它。例如，Windows 上的自动填充快捷键通常被 AMD Radeon Adrenaline 软件（AMD 图形驱动程序）使用，因此不能被 Bitwarden 使用。在这种情况下，您应该释放该快捷键，或者配置 Bitwarden 使用其他快捷键。

### 配置键盘快捷键 <a href="#configuring-keyboard-shortcuts" id="configuring-keyboard-shortcuts"></a>

根据您使用的浏览器不同，配置 Bitwarden 浏览器扩展程序使用的键盘快捷键也不同。要访问配置菜单：

* **在 Chrome 中**，在地址栏输入 `chrome://extensions/shortcuts`。在基于 Chromium 的浏览器（如 Brave）中，用 `chrome` 代替相应的浏览器名称（如 `brave://extensions/shortcuts`）。
* **在 Firefox 中**，在地址栏中输入 `about:addons`，选择**管理您的扩展程序**旁边的 **⚙️齿轮**图标，并从下拉菜单中选择**管理扩展程序快捷键**。

某些浏览器包括 **Safari** 和旧版 **Edge**，目前不支持更改扩展程序的默认键盘快捷键。

## 页面加载时 <a href="#on-page-load" id="on-page-load"></a>

{% hint style="warning" %}
此功能默认情况下被禁用，因为虽然它通常比较安全，但受损或不受信任的网站可能会利用此功能窃取凭据。

浏览器扩展不允许在页面加载时自动填充[不受信任的 iframe](auto-fill-logins-in-browser-extensions.md#auto-fill-in-inframes)，并且当根据[该项目的已保存 URI](../../../auto-fill/using-uris.md) 预期使用 HTTPS 时，浏览器扩展将在 HTTP 站点上自动填充之前向用户发出警告。
{% endhint %}

页面加载时自动填充是 Bitwarden 浏览器扩展提供的一个选择性功能（参见上面的**警告**）。页面加载时自动填充功能将在加载与登录项目的 URI 值对应的网页时自动填充登录信息。启用后，您可以设置其默认的行为（即对所有密码库项目开启或对密码库项目关闭）。

要启用此功能，请导航到浏览器扩展中的**设置** → **自动填充**，勾选**页面加载时自动填充**复选框，然后选择默认行为。启用并设置默认行为后，您还可以为每一个单独的密码库项目指定页面加载时的自动填充行为：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5PxR0j79XtzMCrF4R6xUtu/49fca8557bb393247d750e3b3030c0e8/2024-12-03_09-14-59.png?_a=DAJCwlWIZAAB" %}
页面加载选项
{% endembed %}

使用此约定，您可以将浏览器扩展设置为，例如：

* 仅针对选定的少数几个项目执行页面加载时自动填充（即对所有密码库项目**默认关闭**，并对选定的项目**手动打开**）。
* 针对除选定的少数几个项目之外的所有项目执行页面加载时自动填充（即对所有密码库项目**默认打开**，并对选定的项目**手动关闭**）。

## 手动自动填充 <a href="#manually-auto-fill" id="manually-auto-fill"></a>

您可以在**🔒密码库**视图中打开没有保存 URI 的项目，然后选择**填充**按钮，从而手动自动填充这些项目。

当基于该项目的[已保存 URI](../../../auto-fill/using-uris.md) 预期使用 HTTPS 时，浏览器扩展将在用户使用此方法自动填充[不受信任的 iframe](auto-fill-logins-in-browser-extensions.md#auto-fill-in-inframes) 或 HTTP 站点之前发出警告。

## TOTP 自动填充 <a href="#totp-auto-fill" id="totp-auto-fill"></a>

如果您使用 [Bitwarden 验证器](../../../your-vault/totp.md)，浏览器扩展将自动填充您的 TOTP 代码，前提是您使用上下文菜单、键盘快捷键或手动自动填充。您也可以使用内嵌自动填充菜单来填写 TOTP 代码。**如果您在页面加载时使用自动填充功能，浏览器扩展程序将不会自动填写您的 TOTP 代码**。

默认情况下，自动填充登录信息时，您的 TOTP 也会被复制到剪贴板。如果您使用页面加载时自动填充功能，这是推荐的工作流程。

{% hint style="success" %}
可以使用**设置** → **选项** → **自动复制 TOTP** 关闭自动 TOTP 复制，默认情况下它是打开的。此外，使用旁边的**清除剪贴板**选项设置清除复制值的时间间隔。
{% endhint %}

## 自动填充框架 <a href="#auto-fill-in-inframes" id="auto-fill-in-inframes"></a>

浏览器扩展会悄悄地禁用不受信任的 iframe 的[页面加载自动填充](auto-fill-logins-in-browser-extensions.md#on-page-load)，如果用户使用键盘快捷键、上下文菜单或直接从浏览器扩展手动触发自动填充，则会警告用户有关 iframe 的信息。

「不受信任」的 iframe 被定义为 `src=""` 值与登录项目的 URI 不匹配的 iframe，如全局设置或特定于项目的[匹配检测行为](../../../auto-fill/using-uris.md#match-detection-options)所指示的那样。

## 使用 Bitwarden 中存储的通行密钥登录 <a href="#log-in-with-passkeys-stored-in-bitwarden" id="log-in-with-passkeys-stored-in-bitwarden"></a>

{% hint style="info" %}
如果某个域名位于[排除域名](../../../miscellaneous/exclude-domains.md)列表中，Bitwarden 浏览器扩展就不会发出通行密钥提示。
{% endhint %}

存储新的通行密钥时，网站 URI 将保存在新的登录项目中。访问您希望使用通行密钥登录的网站，然后开始通行密钥登录工作流程。相关通行密钥将显示在 Bitwarden 浏览器扩展对话框中。选择要使用的通行密钥，然后按**确认**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5KeuUZox5shd0zDMxPHKXn/1aab35dfceed0ed9cdb17b143be9a890/2024-10-29_11-39-33.png?_a=DAJCwlWIZAAB" %}
使用通行密钥登录
{% endembed %}



{% hint style="success" %}
[内嵌自动填充菜单](auto-fill-logins-in-browser-extensions.md#inline-auto-fill-menu)还可用于轻松使用通行密钥进行身份验证。
{% endhint %}

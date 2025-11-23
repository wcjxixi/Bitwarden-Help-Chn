# 从浏览器扩展自动填充

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/auto-fill-browser/)
{% endhint %}

Bitwarden 的自动填充功能让登录变得快捷安全。当您访问网站时，浏览器扩展程序会自动识别该网站，并将您密码库中匹配的凭据填充到登录字段中。您可以根据自己的喜好配置自动填充方式。

{% hint style="info" %}
[基本验证提示](../more-autofill-options/basic-auth-prompts.md)的工作方式与本文描述的自动填充方式不同。
{% endhint %}

## 设置自动填充 <a href="#setup-auto-fill" id="setup-auto-fill"></a>

首先，所有浏览器扩展的自动填充方式都要求您的登录项目[已分配网站 URI](../troubleshoot-autofill/forming-uris-for-autofill.md)。这样才能将您保存的凭据关联到正确的网站。

接下来，不同自动填充方式的配置和使用步骤各不相同，具体说明请参见下文。

在**设置** → **自动填充**菜单中，某些选项适用于所有或大多数自动填充方式：

* 为获得最佳性能，请勾选**将 Bitwarden 设为默认的密码管理器**并[停用浏览器的密码管理器](../troubleshoot-autofill/disable-a-browsers-built-in-password-manager.md)。这样可以防止浏览器的密码管理工具干扰 Bitwarden 的自动填充功能。
* 如果您不希望在启用自动填充时自动复制 TOTP，请取消选中[**自动复制 TOTP**](autofill-from-browser-extensions.md#totp-autofill)。
* 从**清除剪贴板**下拉菜单中，选择您偏好的时间间隔，以控制从您的密码库复制的值保留多长时间。
* 选择您的**默认 URI 匹配检测**，即 Bitwarden 用于将网站与您保存的凭据配对的逻辑。除非[您的组织另有指定](../../../admin-console/oversight-visibility/enterprise-policies.md#default-uri-match-detection)，否则默认值为**基础域名**。
* 选择并添加[**屏蔽域名**](../more-autofill-options/blocking-autofill.md)，以阻止在特定网站上自动填充。

## 浏览器扩展中的自动填充方式 <a href="#autofill-methods-in-the-browser-extension" id="autofill-methods-in-the-browser-extension"></a>

自动填充登录信息的最基本方式是与 Bitwarden 浏览器扩展交互。当您访问某个网站并且与至少一个项目的已保存的 URI 匹配时，该网站的匹配项目数量将显示在 Bitwarden 扩展图标的顶部。

{% hint style="success" %}
要隐藏匹配项目的总数，请转至 **⚙️设置** → **外观**，然后取消选中**在扩展图标上显示登录自动填充建议的数量**。
{% endhint %}

选择 **Bitwarden 扩展徽章**以打开您的密码库，匹配的项目将显示在顶部的自动填充建议部分。如果您想要包含支付卡或身份，请转至**设置** → **自动填充**，然后选中**在密码库视图中始终将支付卡显示为自动填充建议**或**在密码库视图中始终将身份显示为自动填充建议**。

要查找项目，请选择 **☷筛选器图标**以打开并应用筛选器到**自动填充建议**和**所有项目**结果中：

{% embed url="https://bitwarden.com/assets/12UsFuA2sxbUCBMIczJsxv/689221013fac56ddb555ed9dabddbdc9/screenshot_6.png?w=584&fm=avif" %}
浏览器扩展筛选和建议
{% endembed %}

### 填充按钮 <a href="#fill-button" id="fill-button"></a>

要自动填充登录：

1. 在网站的登录页面上，打开 Bitwarden 浏览器扩展。
2. 转到**密码库**选项卡。
3. 选择登录旁边的**填充**以输入。它可能位于**自动填充建议**部分的顶部：

{% embed url="https://bitwarden.com/assets/1pamjhdWn7obh8UBxXcIPF/1841242fa5299a780d53f3ae70e546b3/screenshot_5.png?w=395&fm=avif" %}
通过浏览器扩展自动填充
{% endembed %}

选择**填充**按钮会将凭据输入到已检测到的输入字段中。如果网页或服务包含多个具有相关 URI 的项目，Bitwarden 将始终自动填充上次使用的登录信息。

{% hint style="info" %}
如果目标字段位于[不受信任的 iframe](autofill-from-browser-extensions.md#autofill-in-iframes) 中，或者当前站点使用 HTTP（[项目已保存 URI](../troubleshoot-autofill/forming-uris-for-autofill.md) 要求使用 HTTPS）您可能会在自动填充之前收到警告。
{% endhint %}

### 复制凭据 <a href="#copy-credentials" id="copy-credentials"></a>

您也可以选择项目旁边的 **❐复制图标**。将出现一个菜单，您可以在其中选择**复制用户名**或**复制密码**：

{% embed url="https://bitwarden.com/assets/7y8WE9sWACC2KLASo9yASw/5c5fa1150e5e4f4ded19baf0afecfa6e/Standard_Copy_icon.png?w=400&fm=avif" %}
标准复制图标
{% endembed %}

或者，您可以在项目旁边添加三个快速复制操作按钮，专门将您的用户名、密码或验证码复制到剪贴板：

{% embed url="https://bitwarden.com/assets/5w7lobEk81aOGfLKFjRp2e/d37711426641f91deb9ea28715901fb0/Quick_copy_icons.png?w=400&fm=avif" %}
快速复制操作
{% endembed %}

该选项默认停用。要启用它，请转到**设置** → **外观**，然后打开**在密码库上显示快速复制操作**。

### 单击项目 <a href="#click-items" id="click-items"></a>

或者，您可以设置浏览器扩展，当该项目出现在**自动填充建议**部分时，您只需单击项目上的任意位置即可自动填充。使用此选项时，不会显示**填充**按钮：

{% embed url="https://bitwarden.com/assets/3tnagVMjtTufvRCrih3ctQ/b3698262ce7c19baeda6afc87c485167/2025-01-02_11-14-19.png?w=862&fm=avif" %}
单击项目以自动填充
{% endembed %}

要激活此选项，请导航至**设置** → **外观**，然后切换**在自动填充建议中单击项目以自动填充**选项。

启用此选项时，如果您想在浏览器扩展中打开项目，请选择 **≡菜单图标** → **查看**。

### 拖放登录 <a href="#drag-and-drop-logins" id="drag-and-drop-logins"></a>

浏览器扩展和桌面 App 包含将用户名和密码字段拖放到网站的登录表单中以填充凭据的功能：

{% embed url="https://bitwarden.com/assets/7m5Ghz2w281MDQXtvWVdAZ/ded43247a3295552fed4690a3431b095/browser_gif.gif?w=750&fm=avif" %}
浏览器扩展的拖放功能
{% endembed %}

要拖放凭据：

1、将光标悬停在 Bitwarden 浏览器扩展或桌面 App 的用户名或密码字段上。

<figure><img src="https://bitwarden.com/assets/38KJr7zvVSKmYri1WaRXGg/5bab3513a7300ef20f9f55a33ba80c82/2025-02-20_11-07-33.png?w=250&#x26;fm=avif" alt=""><figcaption></figcaption></figure>

2、图标出现后，将字段拖到所需的登录表单中。

## 其他填充方式 <a href="#drag-and-drop-logins" id="drag-and-drop-logins"></a>

当您的密码库在浏览器扩展中已锁解时，还有多种方式可以自动填充您的凭据。这些选项可能会更快，因为您不需要与浏览器扩展进行交互。

对于下面描述的所有自动填充选项，在两种情况下您可能会在自动填充之前收到警告：

* 如果目标字段位于[不受信任的 iframe](autofill-from-browser-extensions.md#autofill-in-iframes) 中。
* 当前站点使用 HTTP，但[项目保存的 URI](../troubleshoot-autofill/forming-uris-for-autofill.md) 要求 HTTPS。

### 内嵌菜单 <a href="#inline-menu" id="inline-menu"></a>

使用内嵌自动填充菜单可以快速输入来自您 Bitwarden 密码库中的登录凭据、[通行密钥](../more-autofill-options/autofill-passkeys.md)以及 [TOTP](../../your-vault/security-tools/totp.md) 代码。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/H7DjdJNvQH00yGNLf5gsC/1ec6f0ce9a94862b0cae1d8b8d679fc8/2024-10-29_14-41-02.png?_a=DAJCwlWIZAAB" %}
内嵌自动填充菜单
{% endembed %}

#### 激活内嵌自动填充菜单 <a href="#activate-the-inline-autofill-menu" id="activate-the-inline-autofill-menu"></a>

要启用内嵌自动填充菜单：

1、登录并解锁 Bitwarden [浏览器扩展](../../getting-started/getting-started-browserext.md)。

2、选择 **⚙️设置** → **自动填充**。

3、勾选**在表单字段显示自动填充建议**，这将打开更多选项。

* （可选）如果您希望内嵌自动填充菜单建议[这些项目类型](../more-autofill-options/auto-fill-cards-and-identities.md#using-the-inline-menu)，请选中**将身份显示为建议**和**将支付卡显示为建议**。
* （可选）要仅当选择 Bitwarden 图标时显示可用于自动填充的匹配项目，请选中**选择图标时显示建议**。如果此设置未勾选，则匹配的项目会立即出现在表单字段下方。

我们建议您[停用浏览器的自动填充](../troubleshoot-autofill/disable-a-browsers-built-in-password-manager.md)选项。如果您的浏览器的自动填充功能已启用，它可能会与 Bitwarden 的自动填充菜单产生冲突。

#### 使用内嵌自动填充菜单 <a href="#use-the-inline-auto-fill-menu" id="use-the-inline-auto-fill-menu"></a>

{% tabs %}
{% tab title="使用内嵌自动填充登录" %}
要使用内嵌自动填充菜单登录账户：

1、选择登录表单的用户名字段。如果您尝试登录时密码库已锁定，菜单会提示您解锁密码库。

2、将显示内嵌自动填充菜单。此时，请选择您希望在网站上使用的登录名或密码。

{% hint style="info" %}
没有看到您想使用的登录凭据吗？编辑密码库项目并选择**自动填充和保存**，或在 URI 字段中手动输入网站。
{% endhint %}

3、如果没有为该网站保存凭据，请选择✚**新建项目**，浏览器扩展将打开一个新的项目，您可以在其中保存新的登录凭据。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1nVpqyl5FuzMPIaKezwZ8c/8a715cb0b1e1423815f0b66b0e8b1b42/web-browser-extension-autofill-newitem.png?_a=DAJCwlWIZAAB" %}

{% hint style="info" %}
如果内嵌自动填充菜单对浏览器造成意外干扰，可按 `Esc` 键关闭。
{% endhint %}
{% endtab %}

{% tab title="使用内嵌自动填充输入 TOTP" %}
要使用内嵌自动填充功能自动填充 TOTP 代码，将光标置于登录表单上的 TOTP 字段中。当显示内嵌自动填充菜单时，选择 TOTP 代码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3RaBZBRgkfwVF0mQPRZYBJ/840a46c911d09ead87ac09fdb0955493/2025-01-03_09-22-34.png?_a=DAJCwlWIZAAB" %}
TOTP 内嵌自动填充单次登录
{% endembed %}

如果此网站有多个登录，内嵌自动填充菜单将显示每一个登录的 TOTP 代码：

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
该选项将使用您在浏览器扩展的**生成器**选项卡中配置的设置。[了解如何更改这些设置](../../your-vault/security-tools/generator.md#password-types)。
{% endhint %}

3、**在点击「注册」或「创建账户」提交表单之前**，内嵌自动填充菜单将提供一个**保存到 Bitwarden** 选项。使用该选项可在弹出窗口中打开 Bitwarden，然后选择**保存**按钮保存生成的凭据：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7cMSUQLfvxHNwHS8xMX1j7/296b7fdfcb384808284aa3f5e67d769a/2024-11-05_10-12-29.png?_a=DAJCwlWIZAAB" %}
保存登录到 Bitwarden
{% endembed %}

4、选择注册、创建账户或网站或应用程序提供的其他按钮来完成账户的创建。
{% endtab %}
{% endtabs %}

### 上下文菜单 <a href="#context-menu" id="context-menu"></a>

在不打开浏览器扩展程序的情况下，您可以在用户名或密码输入栏上点击右键，然后使用 **Bitwarden** → **自动填充**选项。当您尝试此操作时，如果您的密码库已锁定，则会打开一个新的标签页，提示您解锁。解锁后，浏览器扩展将自动继续填充您的用户名、密码、支付卡或身份信息。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6GKKvIe7GwwOBtp9gmh862/4d39f59a8a862bb83d53e50f9f68d107/2024-12-03_09-12-06.png?_a=DAJCwlWIZAAB" %}
浏览器扩展上下文菜单
{% endembed %}

{% hint style="info" %}
目前，Safari 浏览器扩展中不支持使用上下文菜单自动填充。
{% endhint %}

### 键盘快捷键 <a href="#keyboard-shortcuts" id="keyboard-shortcuts"></a>

最快捷的方法之一是使用自动填充键盘快捷键。此方法适用于用户名和密码字段在同一页面上并列出现的情况，以及在分步登录流程中分别出现的场景。

#### 设置键盘快捷键 <a href="#set-up-keyboard-shortcuts" id="set-up-keyboard-shortcuts"></a>

用于登录项目的默认快捷键是：`Ctrl/Cmd` + `Shift` + `L`。如果您想更改快捷键或默认快捷键不起作用，请[更新浏览器的快捷键设置](../../your-vault/keyboard-shortcuts.md#browser-extension-shortcuts)。您还可以为[支付卡和身份信息创建快捷键](../more-autofill-options/auto-fill-cards-and-identities.md#using-keyboard-shortcuts)。

如果您使用的是 Microsoft Edge 浏览器，请确保升级到最新的基于 Chromium 内核的版本。

#### 使用键盘快捷键 <a href="#use-keyboard-shortcuts" id="use-keyboard-shortcuts"></a>

要使用快捷键：

1. 将光标放在第一个登录字段（例如用户名）中。
2. 按下 `Ctrl/Cmd` + `Shift` + `L`。
3. （可选）如果检测到的 URI 具有多个登录信息，则将使用最后一次使用的登录信息进行自动填充。再次按下相同的快捷键可在多个登录信息之间切换。

如果您在尝试使用自动填充快捷键时密码库处于锁定状态，则会弹出一个窗口提示您解锁。解锁后，浏览器扩展将自动继续填充您的凭据。

{% hint style="success" %}
如果登录使用 [Bitwarden 验证器](../../your-vault/security-tools/totp.md) TOTP，并且您使用自动填充快捷键，自动填充后会自动将 TOTP 复制到剪贴板。您要做的就是使用 `Cmd/Ctrl+V` 来粘贴！
{% endhint %}

### 页面加载时 <a href="#on-page-load" id="on-page-load"></a>

{% hint style="danger" %}
此功能默认情况下被禁用，因为虽然它通常比较安全，但受损或不受信任的网站可能会利用此功能窃取凭据。

浏览器扩展不允许在页面加载时自动填充[不受信任的 iframe](autofill-from-browser-extensions.md#auto-fill-in-inframes)，并且当根据[该项目的已保存 URI](../troubleshoot-autofill/forming-uris-for-autofill.md) 预期使用 HTTPS 时，浏览器扩展将在 HTTP 站点上自动填充之前向用户发出警告。
{% endhint %}

页面加载时自动填充功能将在加载与登录项目的 URI 值对应的网页时自动填充登录信息。**页面加载时自动填充**功能默认未启用。启用后，您可以为所有项目设置默认行为（开启或关闭）。

要启用此功能，请导航到浏览器扩展中的**设置** → **自动填充**，勾选**页面加载时自动填充**复选框，然后选择默认行为。启用并设置默认行为后，您还可以为每一个密码库项目单独指定页面加载时的自动填充行为：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5PxR0j79XtzMCrF4R6xUtu/49fca8557bb393247d750e3b3030c0e8/2024-12-03_09-14-59.png?_a=DAJCwlWIZAAB" %}
页面加载选项
{% endembed %}

使用此约定，您可以将浏览器扩展设置为，例如：

* 仅针对指定的少数几个项目执行页面加载时自动填充（即对所有密码库项目**默认关闭**，并对指定的项目**手动打开**）。
* 针对除指定的少数几个项目之外的所有项目执行页面加载时自动填充（即对所有密码库项目**默认打开**，并对指定的项目**手动关闭**）。

## 浏览器扩展中的自动填充故障排除 <a href="#troubleshoot-autofill-from-the-browser-extension" id="troubleshoot-autofill-from-the-browser-extension"></a>

如果您的浏览器扩展在自动填充特定网站的用户名和密码时出现问题，您可以使用[链接型自定义字段](../more-autofill-options/auto-fill-custom-fields.md#using-linked-custom-fields)来强制自动填充。

### iframe 中的自动填充 <a href="#autofill-in-iframes" id="autofill-in-iframes"></a>

浏览器扩展会悄悄地禁用不受信任的 iframe 的[页面加载自动填充](autofill-from-browser-extensions.md#on-page-load)，并在您使用键盘快捷键、上下文菜单或直接从浏览器扩展手动触发自动填充时发出警告。

「不受信任」的 iframe 被定义为 `src=""` 值与登录项目的 URI 不匹配的 iframe，如全局设置或特定于项目的[匹配检测行为](../troubleshoot-autofill/forming-uris-for-autofill.md#match-detection-options)所指示的那样。

## 自动填充不太常见的凭据 <a href="#autofill-less-common-credentials" id="autofill-less-common-credentials"></a>

### TOTP 自动填充 <a href="#totp-autofill" id="totp-autofill"></a>

如果您使用 [Bitwarden 验证器](../../your-vault/security-tools/totp.md)，浏览器扩展将自动填充您的 TOTP 代码，前提是您使用上下文菜单、键盘快捷键或手动自动填充（对没有保存 URI 的项目使用**填充**按钮）。您也可以使用内嵌自动填充菜单来填写 TOTP 代码。**如果您使用页面加载时自动填充功能，浏览器扩展程序将不会自动填写您的 TOTP 代码**。

默认情况下，自动填充登录信息后，您的 TOTP 也会被复制到剪贴板。如果您使用页面加载时自动填充功能，这是推荐的工作流程。

{% hint style="success" %}
可以使用**设置** → **选项** → **自动复制 TOTP** 关闭自动 TOTP 复制，默认情况下它是打开的。此外，使用旁边的**清除剪贴板**选项设置清除复制值的时间间隔。
{% endhint %}

### 使用 Bitwarden 中存储的通行密钥登录 <a href="#log-in-with-passkeys-stored-in-bitwarden" id="log-in-with-passkeys-stored-in-bitwarden"></a>

{% hint style="info" %}
如果某个域名位于[排除域名](../more-autofill-options/exclude-domains.md)列表中，Bitwarden 浏览器扩展就不会发出通行密钥提示。
{% endhint %}

您可以使用通行密钥登录网站。保存新通行密钥时，网站 URI 会保存在登录项目中。要使用通行密钥，请打开网站如何开始通行密钥登录流程。相关的通行密钥将显示在 Bitwarden 浏览器扩展对话框中。选择您要使用的通行密钥，然后按**确认**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5KeuUZox5shd0zDMxPHKXn/1aab35dfceed0ed9cdb17b143be9a890/2024-10-29_11-39-33.png?_a=DAJCwlWIZAAB" %}
使用通行密钥登录
{% endembed %}

[内嵌自动填充菜单](autofill-from-browser-extensions.md#inline-auto-fill-menu)还可用于轻松使用通行密钥进行身份验证。

{% hint style="info" %}
当域名位于[**排除域名**](../more-autofill-options/exclude-domains.md)列表中时，Bitwarden 浏览器扩展不会发出通行密钥提示。
{% endhint %}

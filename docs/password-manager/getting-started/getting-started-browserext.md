# Password Manager 浏览器扩展

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/getting-started-browserext/)
{% endhint %}

Bitwarden 浏览器扩展将密码管理直接集成到您最喜爱的浏览器中。从您的浏览器市场或应用商店，或从 [Bitwarden 下载](https://bitwarden.com/download)页面下载 Bitwarden 浏览器扩展。

{% hint style="success" %}
Safari 浏览器扩展与桌面 App 打包在一起，其可从 App Store 下载。[了解更多](../more/more-platforms/safari-web-extension.md)。
{% endhint %}

## 第一步 <a href="#first-steps" id="first-steps"></a>

让我们通过将一个新的登录项目添加到您的密码库来开始您的 Bitwarden 浏览器扩展之旅：

### 添加一个登录 <a href="#add-a-login" id="add-a-login"></a>

现在，让我们添加一个登录到您的新文件夹中。要创建新的登录：

1、导航到 **🔒密码库**选项卡，然后选择 ✚**添加**图标。

2、选择要创建的项目的类型（这里我们选择**登录**）。

3、输入这个新项目的基本信息：

* 帮助您轻松识别它的项目**名称**（例如 `Instagram Account`）
* 您的**用户名**。
* 您的当前**密码**（我们待会会用一个强大的密码来替换它）。

4、从[文件夹](../your-vault/vault-navigation/folders.md)下拉列表中选择一个文件夹。

{% hint style="success" %}
如果您在工作场所使用 Bitwarden，则可以使用**所有者**下拉列表在您的组织内而不是在个人密码库中创建此项目。
{% endhint %}

5、在**网站 (URI)** 字段中，输入您登录账户的 URL（例如 `https://instaagram.com/login`）。

6、很好！选择**保存**以继续。

### 生成一个强密码 <a href="#generate-a-strong-password" id="generate-a-strong-password"></a>

现在，您已经保存了一个新的登录，让我们使用一个强密码替换您的密码来提高它的安全性：

1、在您的网页浏览器中，使用您现有的用户名和密码登录到此账户。我们将用一个更强的密码替换现有密码，但这也是练习自动填充的好机会！

要进行自动填充，请在网站登录页面打开 Bitwarden 浏览器扩展，在 **🔒密码库**选项卡中选择建议的项目的**填充**按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1pamjhdWn7obh8UBxXcIPF/1841242fa5299a780d53f3ae70e546b3/screenshot_5.png?w=395&#x26;fm=avif" alt=""><figcaption><p>通过浏览器扩展自动填充</p></figcaption></figure></div>

2、登录后，找到可以更改密码的地方。

3、在网站的更改密码表单中，输入您的**当前密码**，您可以从 Bitwarden 使用 **❐复制**图标来复制并粘贴该密码：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/40l7cU1a0jzaTNUJXd5jPD/97b9ed67c0b255384ce84fa53fad2015/screenshot_2.png?w=625&#x26;fm=avif" alt=""><figcaption><p>复制密码</p></figcaption></figure></div>

4、填入旧密码后，在 Bitwarden 中打开登录项目并选择**编辑**。

5、在**密码框**中，选择 **⟳生成**然后根据自己的喜好调整密码设置。您可以使用 **⟳**&#x56FE;标，直到找到您喜欢的密码，然后选择**使用此密码**。从 `Fido1234` 更改为 `X@Ln@x9J@&u@5n##B` 可以阻止潜在的黑客攻击。

6、选择**保存**。

7、复制您的新密码并将其粘贴到网站上的**新密码**和**确认密码**字段中。

恭喜！您的登录现已安全且易于使用地保存在 Bitwarden 中了！

### 固定扩展 <a href="#pin-an-extension" id="pin-an-extension"></a>

固定浏览器扩展程序可确保每次打开浏览器时都可以轻松访问它。根据您使用的浏览器，此过程有所不同：

{% tabs %}
{% tab title="Chrome" %}
选择地址栏右侧的**扩展程序**图标，然后在扩展程序列表中选择 Bitwarden 旁边的**固定**图标：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4cwP0QDHWh01v1K8nMV0ma/88b4b36c5b3e9d1fccffe7552880c485/chrome_pin.png?w=340&#x26;fm=avif" alt=""><figcaption><p>Chrome 中的 Pin</p></figcaption></figure></div>
{% endtab %}

{% tab title="Firefox" %}
选择地址栏旁边的**扩展**图标，右键单击 Bitwarden 浏览器扩展，然后选择**固定到工具栏**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2O0RQxs4fr6tTKBAMOQcGy/a54ea16b59f933a209db9458c92358e6/firefox_pin.png?w=403&#x26;fm=avif" alt=""><figcaption><p>Firefox 中的 Pin</p></figcaption></figure></div>

您还可以从 Firefox 菜单中选择**查看** → **侧边栏** → **Bitwarden** 来激活永久 Bitwarden 侧边栏。

{% hint style="info" %}
如果您不想在浏览器启动时打开 Bitwarden 侧边栏，请从 Firefox 侧边栏的 Bitwarden 选项卡中选择**关闭侧边栏**。用户可能需要在每个活动的 Firefox 标签页上选择**关闭侧边栏**并重新启动 Firefox。
{% endhint %}
{% endtab %}

{% tab title="Safari" %}
右键单击工具栏中的任意位置，然后选择**自定义工具栏**打开一个拖放界面，以让您可以移动或移除工具栏中的图标：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3mD3G3rNMEUu24XBh6a3Kt/5217730380fe6ee6cd49f7c3820574ee/safari_pin.png?w=680&#x26;fm=avif" alt=""><figcaption><p>Safari 中的 Pin</p></figcaption></figure></div>
{% endtab %}
{% endtabs %}

## 添加第二个账户 <a href="#add-a-second-account" id="add-a-second-account"></a>

您是否拥有多个 Bitwarden 账户，一个用于个人使用，一个用于工作？浏览器扩展可以同时登录五个账户！

要登录其他账户，请在浏览器扩展右上角选择当前已登录的账户：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7xbbMZ89zcTHz6ee0cA1MK/8d8972a6b995b3fd7367f248c9c60d69/screenshot_3.png?w=440&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展账户切换</p></figcaption></figure></div>

打开账户切换菜单后，选择 **🞤添加账户**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/343trVk3zLCF7Z12uA5wjO/ac2f56fc907372335f30d1dbf68116a1/screenshot_4.png?w=438&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展添加账户</p></figcaption></figure></div>

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除。

{% hint style="info" %}
账户切换功能目前还不适用于 Safari 浏览器扩展。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经掌握了基础知识，让我们深入了解您将经常使用的更多操作，**自动填充**和**自动保存**，以及三个推荐的设置步骤，更轻松地**解锁**密码库，将扩展**固定**到浏览器，以及**禁用浏览器内置**的密码管理器：

### 禁用内置的密码管理器 <a href="#disable-a-built-in-password-manager" id="disable-a-built-in-password-manager"></a>

大多数网络浏览器默认会自动保存您的密码，但专业人士普遍认为，相比 Bitwarden 等专用解决方案，[内置的密码管理器更容易受到攻击](https://www.wired.com/2016/08/browser-password-manager-probably-isnt-enough/)。了解更多有关[手动禁用浏览器内置密码管理器](../autofill/troubleshoot-autofill/disable-a-browsers-built-in-password-manager.md)的信息。

### 自动填充登录 <a href="#auto-fill-a-login" id="auto-fill-a-login"></a>

使用 Bitwarden 浏览器扩展有很多自动填充凭据的方法！最基本的方法是在网站登录页面打开 Bitwarden 浏览器扩展，在 **🔒密码库**选项卡中选择建议的项目的**填充**按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1pamjhdWn7obh8UBxXcIPF/1841242fa5299a780d53f3ae70e546b3/screenshot_5.png?w=395&#x26;fm=avif" alt=""><figcaption><p>通过浏览器扩展自动填充</p></figcaption></figure></div>

请注意，当您在试图登录的网站上以保存了登录信息时，Bitwarden 浏览器扩展会覆盖一个通知气泡，报告您在该网站上的登录项目的数量。这些项目将显示在**自动填充建议**的顶部。您可以使用筛选器下拉菜单过滤建议中的内容和**所有项目**列表中的显示内容，这些下拉菜单可以通过 **☷**&#x6309;钮显示或隐藏：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/12UsFuA2sxbUCBMIczJsxv/689221013fac56ddb555ed9dabddbdc9/screenshot_6.png?w=584&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展筛选器和建议</p></figcaption></figure></div>

浏览器扩展项有好几种可供选择的自动填充选项，包括上下文菜单和键盘快捷键。[了解更多](../autofill/autofill-from/autofill-from-browser-extensions.md)。

### 自动保存登录 <a href="#auto-save-a-login" id="auto-save-a-login"></a>

Bitwarden 浏览器扩展提供一系列[浏览器内通知](../autofill/autofill-from/autosave-from-browser-extensions.md)，可将已解密的数据与您在登录、注册和类似网页表单中输入的数据进行比较。

当您看到此横幅时，选择**保存**以使用用户名、密码和 URI 添加新的登录项目，或更新现有登录项目。如果是新项目，还可以选择**选择文件夹...**，或在保存前**编辑**此项目：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4vsurEuH5deik26BWn4n1p/82757186b081890fbe92b4d73baeae53/screenshot_7.png?w=426&#x26;fm=avif" alt=""><figcaption><p>询问添加登录</p></figcaption></figure></div>

了解更多有关[使用浏览器扩展自动保存](../autofill/autofill-from/autosave-from-browser-extensions.md)的信息。

{% hint style="success" %}
您知道使用 Bitwarden 浏览器扩展可以保存和自动填充通行密钥吗？[了解更多](../autofill/more-autofill-options/autofill-passkeys.md)关于通行密钥的信息。
{% endhint %}

### 使用 PIN 码或生物识别解锁 <a href="#unlock-with-pin-or-biometrics" id="unlock-with-pin-or-biometrics"></a>

要快速访问您的凭据，请设置 [PIN 码](../../account/log-in-and-unlock/more-log-in-unlock-options/unlock-with-pin.md)或[生物识别](../../account/log-in-and-unlock/more-log-in-unlock-options/unlocking-with-biometrics.md)来解锁您的密码库。要设置一个 PIN 码：

1. 在浏览器扩展中，打开 ⚙️**设置**标签。
2. 在**账户安全**部分，选中**使用 PIN 码解锁**复选框。
3. 在输入框中输入所需的 PIN 码。PIN 码可以是任意字符（a-z、0-9、$、＃ 等）的组合。

{% hint style="success" %}
**可选**：预先选中的**启动时要求生物识别**选项将要求您在浏览器重新启动时输入主密码而不是 PIN 码。如果您希望能够在浏览器重新启动时使用 PIN 码解锁，请取消选中此选项。
{% endhint %}

### 浏览器弹出窗口 <a href="#browser-pop-out" id="browser-pop-out"></a>

Bitwarden 浏览器扩展具有弹出窗口功能，允许您在使用网络浏览器时重新定位客户端。要弹出浏览器扩展，请选择下面截图中所示的图标：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1cbJy0jLBmSQmRumvYzVwp/a9e43f4c154686249056924eb3e56323/pop_out_screenshot.png?w=407&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展弹出窗口</p></figcaption></figure></div>

弹出时，浏览器扩展不会遵守您选择的[密码库超时](../../account/log-in-and-unlock/vault-timeout-options.md)设置。

### 将 Bitwarden 设为默认密码管理器 <a href="#make-bitwarden-your-default-password-manager" id="make-bitwarden-your-default-password-manager"></a>

Bitwarden 浏览器扩展有一个内置设置，可以禁用浏览器的默认密码管理器。要使用此设置：

1、导航至 Bitwarden 浏览器扩展中的 ⚙️**设置**选项卡，然后选择**自动填充**。

2、点击启用**将 Bitwarden 设为默认密码管理器**。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5fyBdu5X6JCLu2UsaqYUO0/abfb44cb460314112805bfd0312c1f8f/2025-10-14_12-44-35.png?w=459&#x26;fm=avif" alt=""><figcaption><p>将 Bitwarden 设为默认密码管理器</p></figcaption></figure></div>

3、屏幕上会出现一个对话框，选择**允许**以授予 Bitwarden 更改您的浏览器设置的权限。

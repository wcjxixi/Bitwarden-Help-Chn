# Password Manager 浏览器扩展

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/getting-started-browserext/)
{% endhint %}

Bitwarden 浏览器扩展将密码管理直接集成到您最喜爱的浏览器中。从您的浏览器市场或应用商店，或从 [Bitwarden 下载](https://bitwarden.com/download)页面下载 Bitwarden 浏览器扩展。

浏览器扩展支持 **Google Chrome**、**Mozilla Firefox**、**Opera**、**Microsoft Edge** 和 **Safari** 的最近两个版本。对于 **Vivaldi**、**Brave** 和 **Tor**，只支持最新的版本。

{% hint style="success" %}
Safari 浏览器扩展与桌面 App 打包在一起，其可从 App Store 下载。[了解更多](../miscellaneous/safari-web-extension.md)。
{% endhint %}

## 第一步 <a href="#first-steps" id="first-steps"></a>

让我们通过将一个新的登录项目添加到您的密码库并确保其安全且易于查找来开始您的 Bitwarden 浏览器扩展之旅：

### 创建一个文件夹 <a href="#create-a-folder" id="create-a-folder"></a>

[文件夹](../password-manager/your-vault/vault-items/folders.md)是确保您在需要使用时始终可以找到密码库项目的好方法。要创建一个文件夹：

1. 导航到 **🔒密码库**选项卡，然后选择 ✚**添加**图标。
2. 选择要创建的项目类型（本例中选择**文件夹**）。
3. 给您的新文件夹起个名字（例如 `Social Media`），然后选择**保存**。

### 添加一个登录 <a href="#add-a-login" id="add-a-login"></a>

现在，让我们添加一个登录到您的新文件夹中。要创建新的登录：

1、导航到 **🔒密码库**选项卡，然后选择 ✚**添加**图标。

2、选择要创建的项目的类型（这里我们选择**登录**）。

3、输入这个新项目的基本信息：

* 帮助您轻松识别它的项目**名称**（例如 `Instagram Account`）
* 您的**用户名**。
* 您的当前**密码**（我们待会会用一个强大的密码来替换它）。

4、从文件夹下拉列表中选择一个**文件夹**，如果您按照我们的示例进行操作，请选择我们刚刚创建的 **Social Media** 文件夹！

5、在**网站 (URI)** 字段中，输入您登录账户的 URL（例如 `https://instaagram.com/login`）。

6、很好！选择**保存**以继续。

### 生成一个强密码 <a href="#generate-a-strong-password" id="generate-a-strong-password"></a>

现在，您已经保存了一个新的登录，让我们使用一个强密码替换您的密码来提高它的安全性：

1、在您的网页浏览器中，使用您现有的用户名和密码登录到此账户。我们将用一个更强的密码替换现有密码，但这也是练习自动填充的好机会！

要进行自动填充，请在网站登录页面打开 Bitwarden 浏览器扩展，在 **🔒密码库**选项卡中选择建议的项目的**填充**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1pamjhdWn7obh8UBxXcIPF/cb72c2921ce5f717cfd81bf157e50f4d/2024-12-02_13-59-23.png?_a=DAJCwlWIZAAB" %}
通过浏览器扩展自动填充
{% endembed %}

2、登录后，找到可以更改密码的地方。

3、在网站的更改密码表单中，输入您的**当前密码**，您可以从 Bitwarden 使用 **❐复制**图标来复制并粘贴该密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/40l7cU1a0jzaTNUJXd5jPD/79406c7da76e692a92d06f5aeb0501c0/2024-12-02_14-01-44.png?_a=DAJCwlWIZAAB" %}
复制密码
{% endembed %}

4、填入旧密码后，在 Bitwarden 中打开登录项目并选择**编辑**。

5、在**密码框**中，选择 **⟳生成**然后根据自己的喜好调整密码设置。您可以使用 **⟳**&#x56FE;标，直到找到您喜欢的密码，然后选择**使用此密码**。从 `Fido1234` 更改为 `X@Ln@x9J@&u@5n##B` 可以阻止潜在的黑客攻击。

6、选择**保存**。

7、复制您的新密码并将其粘贴到网站上的**新密码**和**确认密码**字段中。

恭喜！您的登录现已安全且易于使用地保存在 Bitwarden 中了！

## 添加第二个账户 <a href="#add-a-second-account" id="add-a-second-account"></a>

您是否拥有多个 Bitwarden 账户，一个用于个人使用，一个用于工作？浏览器扩展可以同时登录五个账户！

要登录其他账户，请在浏览器扩展右上角选择当前已登录的账户：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7xbbMZ89zcTHz6ee0cA1MK/4cb688e3d593e379ddd8192c6545d5b6/2024-12-02_10-49-10.png?_a=DAJCwlWIZAAB" %}
浏览器扩展账户切换
{% endembed %}

打开账户切换菜单后，选择 **🞤添加账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/343trVk3zLCF7Z12uA5wjO/332a681bf34d66dee8b032812f0f85ad/2024-12-02_10-50-07.png?_a=DAJCwlWIZAAB" %}
浏览器扩展添加账户
{% endembed %}

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除。

{% hint style="info" %}
账户切换功能目前还不适用于 Safari 浏览器扩展。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经掌握了基础知识，让我们深入了解您将经常使用的更多操作，**自动填充**和三个推荐的设置步骤，更轻松地**解锁**密码库，将扩展**固定**到浏览器，以及**禁用浏览器内置**的密码管理器：

### 自动填充登录 <a href="#auto-fill-a-login" id="auto-fill-a-login"></a>

使用 Bitwarden 浏览器扩展有很多自动填充凭据的方法！最基本的方法是在网站登录页面打开 Bitwarden 浏览器扩展，在 **🔒密码库**选项卡中选择建议的项目的**填充**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1pamjhdWn7obh8UBxXcIPF/cb72c2921ce5f717cfd81bf157e50f4d/2024-12-02_13-59-23.png?_a=DAJCwlWIZAAB" %}
通过浏览器扩展自动填充
{% endembed %}

请注意，当您在试图登录的网站上以保存了登录信息时，Bitwarden 浏览器扩展会覆盖一个通知气泡，报告您在该网站上的登录项目的数量。这些项目将显示在**自动填充建议**的顶部。您可以使用筛选器下拉菜单过滤建议中的内容和**所有项目**列表中的显示内容，这些下拉菜单可以通过 **☷**&#x6309;钮显示或隐藏：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/12UsFuA2sxbUCBMIczJsxv/22c20404137193420d3b2d1f5fa8611f/2024-12-02_14-07-09.png?_a=DAJCwlWIZAAB" %}
浏览器扩展筛选器和建议
{% endembed %}

浏览器扩展项有好几种可供选择的自动填充选项，包括上下文菜单和键盘快捷键。[了解更多](../password-manager/autofill/autofill-from/autofill-from-browser-extensions.md)。

### 自动保存登录 <a href="#auto-save-a-login" id="auto-save-a-login"></a>

Bitwarden 浏览器扩展提供一系列[浏览器内通知](../password-manager/autofill/autofill-from/autosave-from-browser-extensions.md)，可将已解密的数据与您在登录、注册和类似网页表单中输入的数据进行比较。这些通知包括：

* 保存或使用通行密钥的通知。
* 添加未检测到的登录的通知。
* 更新现有登录的通知。

当您看到此横幅时，选择**保存**以使用用户名、密码和 URI 添加新的登录项目，或更新现有登录项目。如果是新项目，还可以选择**选择文件夹...**，或在保存前**编辑**此项目：

{% embed url="https://bitwarden.com/assets/4vsurEuH5deik26BWn4n1p/b14619e64cd8cd9c1cd4aa2d9f2fe88a/2025-05-20_16-17-25.png?w=1007&fm=avif&q=80" %}
询问添加登录
{% endembed %}

如果您是使用[禁用个人密码库策略](../admin-console/oversight-visibility/enterprise-policies.md#remove-individual-vault)的组织的成员，选择**保存**将带您进入一个屏幕，您可以在其中选择要将其添加到的[集合](../admin-console/manage-shared-items/collections/about-collections.md)。

如果不想看到这些横幅，请打开浏览器扩展的 **⚙️设置**选项卡，选择**通知**，然后取消选中**询问添加登录**和**询问更新现有登录**复选框。

{% hint style="success" %}
您知道使用 Bitwarden 浏览器扩展可以保存和自动填充通行密钥吗？[了解更多](../password-manager/autofill/more-autofill-options/autofill-passkeys.md)关于通行密钥的信息。
{% endhint %}

### 使用 PIN 码或生物识别解锁 <a href="#unlock-with-pin-or-biometrics" id="unlock-with-pin-or-biometrics"></a>

要快速访问您的凭据，请设置 [PIN 码](../account/log-in-and-unlock/more-unlock-options/unlock-with-pin.md)或[生物识别](../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)来解锁您的密码库。要设置一个 PIN 码：

1. 在浏览器扩展中，打开 ⚙️**设置**标签。
2. 在**账户安全**部分，选中**使用 PIN 码解锁**复选框。
3. 在输入框中输入所需的 PIN 码。PIN 码可以是任意字符（a-z、0-9、$、＃ 等）的组合。

{% hint style="success" %}
**可选**：预先选中的**启动时要求生物识别**选项将要求您在浏览器重新启动时输入主密码而不是 PIN 码。如果您希望能够在浏览器重新启动时使用 PIN 码解锁，请取消选中此选项。
{% endhint %}

### 固定扩展 <a href="#pin-an-extension" id="pin-an-extension"></a>

固定浏览器扩展程序可确保每次打开浏览器时都可以轻松访问它。根据您使用的浏览器，此过程有所不同：

{% tabs %}
{% tab title="Chrome" %}
选择地址栏右侧的**扩展程序**图标，然后在扩展程序列表中选择 Bitwarden 旁边的**固定**图标：

{% embed url="https://bitwarden.com/assets/4cwP0QDHWh01v1K8nMV0ma/4b6107a373a39ce70ced34e585460982/2025-04-23_11-32-35.png?w=450&fm=avif&q=80" %}
Chrome 中的 Pin
{% endembed %}
{% endtab %}

{% tab title="Firefox" %}
右键单击 Bitwarden 浏览器扩展，选择**固定到工具栏。** 您还可以从 Firefox 菜单中选择**查看** → **侧边栏** → **Bitwarden** 来激活持久的 Bitwarden 侧边栏。

{% hint style="info" %}
如果不想在浏览器启动时打开 Bitwarden 侧边栏，请从 Firefox 侧边栏的 Bitwarden 选项卡中选择**关闭侧边栏**。用户可能需要在每个活动的 Firefox 标签页上选择**关闭侧边栏**并重新启动 Firefox。
{% endhint %}
{% endtab %}

{% tab title="Safari" %}
右键单击工具栏中的任意位置，然后选择**自定义工具栏**打开一个拖放界面，以让您可以移动或移除工具栏中的图标：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3mD3G3rNMEUu24XBh6a3Kt/9d4bd3492b6194355611aa5b321733aa/safari-pin.png?fm=webp&h=278&q=50&w=570" %}
Safari 中的 Pin
{% endembed %}
{% endtab %}
{% endtabs %}

### 浏览器弹出窗口 <a href="#browser-pop-out" id="browser-pop-out"></a>

Bitwarden 浏览器扩展具有弹出窗口功能，允许您在使用网络浏览器时重新定位客户端。要弹出浏览器扩展，请选择下面截图中所示的图标：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1cbJy0jLBmSQmRumvYzVwp/be8132e558dd91c6d282f08a02e2d5fa/2024-12-02_14-10-52.png?_a=DAJCwlWIZAAB" %}
浏览器扩展弹出窗口
{% endembed %}

弹出时，浏览器扩展不会遵守您选择的[密码库超时](../account/log-in-and-unlock/vault-timeout-options.md)设置。

### 禁用内置的密码管理器 <a href="#disable-a-built-in-password-manager" id="disable-a-built-in-password-manager"></a>

大多数网络浏览器默认会自动保存您的密码，但专业人士普遍认为，相比 Bitwarden 等专用解决方案，[内置的密码管理器更容易受到攻击](https://www.wired.com/2016/08/browser-password-manager-probably-isnt-enough/)。

#### 将 Bitwarden 设为默认密码管理器 <a href="#make-bitwarden-your-default-password-manager" id="make-bitwarden-your-default-password-manager"></a>

Bitwarden 浏览器扩展有一个内置设置，可以禁用浏览器的默认密码管理器。要使用此设置：

1、导航至 Bitwarden 浏览器扩展中的 **设置**选项卡，然后选择**自动填充**。

2、点击启用**将 Bitwarden 设为默认密码管理器**。

{% embed url="https://bitwarden.com/assets/5fyBdu5X6JCLu2UsaqYUO0/d3ba86c0fc27f1bfa0accccba41e9730/2025-04-15_16-41-28.png?w=380&fm=avif&q=80" %}

3、屏幕上会出现一个对话框，选择**允许**以授予 Bitwarden 更改您的浏览器设置的权限。

#### 手动禁用浏览器内置的密码管理器 <a href="#manually-disable-a-browsers-built-in-password-manager" id="manually-disable-a-browsers-built-in-password-manager"></a>

了解如何禁用常见浏览器的内置密码管理器：

{% tabs %}
{% tab title="Chrome/Chromium" %}
在 Chrome 或任何基于 Chromium 的浏览器（Edge、Opera 和 Brave）中，通过在地址栏中输入 `chrome://password-manager/settings` 以导航到**密码**页面，将 `chrome` 替换为您的浏览器的名称（例如，`brave://password-manager/settings`）。对于 Edge 用户，请导航至 `edge://wallet/settings`。

在此页面上，同时关闭**主动提出保存密码**选项和**自动登录**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6bpi4fkyZhnkhW5RBtugDW/d8e2de4536d6a34f092fd9d5975fd04a/chrome-disable-autofill.png?_a=DAJCwlWIZAAB" %}
Chrome 浏览器选项
{% endembed %}

此页面还将列出浏览器存储的所有**已保存的密码**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4P5alfndwwNgCpTYrSCg61/b3545839a8429f28ee7b6ac66559c3ce/chrome-delete-passwords.png?_a=DAJCwlWIZAAB" %}
Chrome 已保存的密码
{% endembed %}

如果您尚未在 Bitwarden 中保存这些密码，请[将它们导出](../password-manager/import-and-export/import-guides/import-data-from-chrome.md#export-from-chrome)以准备将来导入到 Bitwarden。导出后，您应该从浏览器的存储中删除这些密码。
{% endtab %}

{% tab title="Firefox" %}
在 Firefox 中，导航到**首选项** → **隐私与安全**，然后向下滚动到**登录信息与密码**部分。在这部分中，取消选中所有预先选中的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/72yK5CCMKa9pcfCcdvUZqL/43842f5ab8ed69f16b05513ed16fe864/firefox-disable.png?_a=DAJCwlWIZAAB" %}
Firefox 密码选项
{% endembed %}

{% hint style="success" %}
Bitwarden Password Manager 为高级用户提供各种[报告](../password-manager/your-vault/security-tools/vault-health-reports.md)，如**暴露的密码**和**重复使用的密码**报告，并为所有用户提供免费的**数据泄露**报告。
{% endhint %}

您还可以通过选择**已保存的登录信息...** 按钮找出 Firefox 已经保存了哪些登录信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5UrQ6bGCjV0VdHvy6rzece/576d7d25e03348dee8f06a9af5badb25/firefox-delete.png?_a=DAJCwlWIZAAB" %}
Firefox 已经保存的登录信息
{% endembed %}

如果您尚未在 Bitwarden 中保存这些密码，请[将它们导出](../password-manager/import-and-export/import-guides/import-data-from-chrome.md#export-from-chrome)以准备将来导入到 Bitwarden。导出后，您应该从 Firefox 中**移除**这些密码。
{% endtab %}

{% tab title="Safari" %}
在 Safari 中，从菜单栏中打开**首选项**然后导航到**自动填充**选项卡。在此选项卡上，取消选中所有预先选中的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4nuEz911vsIAUegHVL0Zec/7d663935c4f9e65297c14598f1037b72/safari-disable.png?_a=DAJCwlWIZAAB" %}
Safari 密码选项
{% endembed %}

您还可以通过导航到**密码**选项卡找出 Safari 已经保存了哪些密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6eZMZC98Grc7sbdHbBfXtK/4c72d19c26e56ad7dfb3267f466bd119/safari-delete.png?_a=DAJCwlWIZAAB" %}
Safari 已保存的密码
{% endembed %}

如果您尚未在 Bitwarden 中保存这些密码，请在 Bitwarden 中为这些密码创建登录项目。所有已保存的密码都保存到 Bitwarden 中后，请从 Safari 中**移除**这些密码。
{% endtab %}

{% tab title="Vivaldi" %}
在 Vivaldi 中，打开 **⚙️Vivaldi 设置**窗口，然后从左侧导航中选择 **👁‍🗨隐私**。向下滚动到密码部分并取消选中**保存网页密码**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6nk9FVDeg8XaUz22Xahr8T/ee0f597cc264da5a30853588d541f074/vivaldi-disable.png?_a=DAJCwlWIZAAB" %}
Vivaldi 密码选项
{% endembed %}

您还可以通过选择**显示已保存的密码**按钮找出 Vivaldi 已经保存了哪些密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1j5qvcTAVsXficByKFewec/fd6f86731a9e15d38e0cbc39f4f64197/vivaldi-delete.png?_a=DAJCwlWIZAAB" %}
Vivaldi 已保存的密码
{% endembed %}

如果您尚未在 Bitwarden 中保存这些密码，请在 Bitwarden 中为这些密码创建登录项目。所有已保存的密码都保存到 Bitwarden 中后，请从 Vivaldi 中移除这些密码。[了解更多](https://help.vivaldi.com/desktop/privacy/password-management/#Deleting_passwords)。
{% endtab %}

{% tab title="Tor" %}
虽然 Tor 与 Firefox 共享根目录，但 Tor 的独特之处在于默认情况下它不会保存您的登录信息。如果您还没有手动配置 Tor 来保存和自动填充登录信息，那么您已经准备好了。

如果您配置过了，请通过在地址栏中输入 `about:preferences#privacy` 导航到**密码**页面，然后向下滚动到登录和密码部分。关闭您勾选过的所有选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4FcJnbhCUhDNITJjiy9ciD/d0f83af69188afaf619788c7e60c9a1b/tor-disable.png?_a=DAJCwlWIZAAB" %}
Tor 密码选项
{% endembed %}

您还可以通过选择**已保存的登录信息...** 按钮找出 Tor 已经保存了哪些登录信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3NHOIo5RIwTjVecqRPeT5Y/6c1e26dc5385006a498b77c48e1048c2/tor-delete.png?_a=DAJCwlWIZAAB" %}
Tor 已保存的密码
{% endembed %}

如果您尚未在 Bitwarden 中保存这些密码，请在 Bitwarden 中为这些密码创建登录项目。所有密码都保存到 Bitwarden 中后，从 Tor 中 **🗑️移除**这些密码。
{% endtab %}

{% tab title="DuckDuckGo" %}
在 DuckDuckGo 中，导航至**设置** → **自动填充**。 在此页面中，取消选中**用户名和密码**复选框。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6kAbV4w8EiJX20O9VZOQyl/c6df545c4bc464122b250527b80494d3/Screenshot_2023-11-03_at_11.06.54_AM.png?_a=DAJCwlWIZAAB" %}
禁用 DuckDuckGo 密码管理器
{% endembed %}

您可以通过选择**导出密码**来创建现有数据的备份。创建备份文件后，选择**查看自动填写内容...**，然后删除存储的自动填充数据，以移除之前保存的建议。

在密码管理器部分，macOS 用户可以选择使用 Bitwarden。[了解更多](../miscellaneous/duckduckgo-macos-browser-integration.md)有关 Bitwarden DuckDuckGo macOS 浏览器集成的信息。
{% endtab %}
{% endtabs %}

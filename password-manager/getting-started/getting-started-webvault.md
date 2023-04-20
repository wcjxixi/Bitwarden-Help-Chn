# 网页密码库入门

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/getting-started-webvault/)
{% endhint %}

Bitwarden 网页密码库为个人用户和组织提供了最丰富的 Bitwarden 体验。许多重要功能，例如设置[两步登录](../../my-account/two-step-login/two-step-login-methods.md)或管理[组织](../../admin-console/organization-basics/organizations.md)，只能从网页密码库完成。

{% hint style="success" %}
可以从任何流行的网页浏览器访问网页密码库，网址为 [vault.bitwarden.com](https://vault.bitwarden.com)。或者，如果**您是自托管** Bitwarden，则网址为您[已配置的域名](../../on-premises-hosting/install-deploy-guides/install-and-deploy-linux.md)，例如 `https://my.bitwarden.server.com`。
{% endhint %}

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2xTpSA11EOCzx8VIuVffcF/7b076851ff275c641b6343cd1f311cd3/Screen_Shot_2022-05-13_at_10.29.39_AM.png?fm=webp&h=440&q=50&w=773" %}
Bitwarden 网页密码库
{% endembed %}

当您首次登录网页密码库时，您将进入**密码库**视图。此空间将列出您的所有密码库项目，包括[登录信息、支付卡、身份和安全笔记](../vault-basics/vault-items.md)。

## 第一步 <a href="#first-steps" id="first-steps"></a>

在上面的屏幕截图中，**密码库**视图显示**我的密码库**视图中的 **☷所有项目**。[组织](../../admin-console/organization-basics/organizations.md)的用户将在此处列出其他密码库。使用**筛选器**列可以帮助您使用**收藏**和**文件夹**来组织您的密码库。

让我们设置一个新的文件夹并向其添加一个新的登录项目来作为开始：

### 创建一个文件夹 <a href="#create-a-folder" id="create-a-folder"></a>

要创建文件夹：

1、在筛选器列中，选择文件夹部分旁边的 ✚**添加**图标。

2、为您的文件夹输入一个名称（例如 `Social Media Logins`），然后选择**保存**。

{% hint style="success" %}
为了使密码库更清爽，您可以[将文件夹嵌套在其他文件夹中](../vault-administration/folders.md#nested-folders)。
{% endhint %}

### 添加一个登录 <a href="#add-a-login" id="add-a-login"></a>

要添加一个新的登录项目：

1、选择密码库右上角附近的 ✚**添加项目**按钮。

2、确保从类型下拉列表中选择了**登录**（如果您要添加支付卡、身份或安全笔记，请选择相应的类型）。

3、输入项目的**名称**。名称用于帮助您轻松识别密码库中的项目，因此请为其指定一个可识别的名称（例如`我的 Twitter 登录`）。

4、为登录项目输入您的**用户名**和**密码**。现在，请输入您**现有的**密码，我们稍后会帮助您[用更强的密码替换它](getting-started-webvault.md#generate-a-strong-password)。

5、在 **URI 1** 字段中，输入网站的 URL（例如 `https://twitter.com/login`）。如果您不知道要使用哪个 URL，请导航到网站的登录界面并从地址栏中复制它。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6WQaVgVC3thQYd07vIPsn6/027862bedaee138c1386c3e342dc882e/gs-uri.png?fm=webp&h=946&q=50&w=2260" %}
查找 URI
{% endembed %}

6、从**文件夹**下拉菜单中，选择要将此项目添加到的文件夹的名称（例如，我们之前创建的`社交媒体登录`文件夹）。

如果要将此项目添加到收藏夹，请选择此面板右下角的 **⭐️收藏夹**图标。标记为收藏时，图标将被填充（**★** → **✰**）。

7、干得好！选择**保存**按钮完成添加此项目。

### 生成一个强密码 <a href="#generate-a-strong-password" id="generate-a-strong-password"></a>

现在新的登录项目已保存在您的密码库中，您可以使用用更强的密码替换现有的密码来增强其安全性：

1、在您的 Bitwarden 密码库中，单击要保护的项目以查看其信息。

2、在新的标签页或窗口中，打开相应的网站并登录您的帐户。

{% hint style="success" %}
如果您在 **URI 1** 字段中输入了某些内容，请单击 **⮫启动**图标以直接从您的密码库中打开它！
{% endhint %}

3、在该网站上，导航到可以**更改您的密码**的区域。

通常，您可以在**您的帐户**、**安全**或**登录设置**部分中找到它。

4、大多数网站会要求您先输入**当前密码**。返回到您的 Bitwarden 密码库并单击**密码**字段旁边的 **❐复制**图标。然后，返回到该网站并将其粘贴到**当前密码**字段中。

您可能已经记住了旧的密码，但养成复制和粘贴密码是一个好的习惯，因为一旦你的密码被替换成更强的密码，你将主要以这种方式登录网站。

5、返回到您的 Bitwarden 密码库并单击**密码**字段旁边的 **⟳生成**图标。系统会询问您是否要覆盖当前密码，单击**是**以继续。

这将用随机生成的强密码替换您的**密码**值。从 `Fido1234` 这样的密码迁移到 `X@Ln@x9J@&u@5n##B` 可以阻止潜在的黑客入侵。

6、使用您之前使用的相同的 **❐复制**图标复制您的新密码，然后点击**保存**按钮。

{% hint style="info" %}
不用担心会覆盖您现有的密码！如果出现问题，Bitwarden 会为每个登录项目维护最近五个密码的**密码历史记录**：
{% endhint %}

{% embed url="https://bitwarden.com/help/images/getting-started/pwhistory.png" %}
查看密码历史
{% endembed %}

7、返回到刚才的网站，然后将您的强密码粘贴到**新的密码**和**确认新的密码**字段中。

8、**保存**密码更改后，您就完成了！

### 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

好消息！如果您将用户名和密码保存在网络浏览器或其他密码管理器中，则无需为每次登录重复以上过程。使用我们的专业导入指南之一来帮助您将数据直接传输到 Bitwarden：

* [LastPass](../import-and-export/import-guides/import-your-data-from-lastpass.md)
* [1Password](../import-and-export/import-guides/import-your-data-from-1password.md)
* [Dashlane](../import-and-export/import-guides/Import-data-from-dashlane.md)
* [macOS & Safari](../import-and-export/import-guides/import-data-from-macos-safari.md)
* [Google Chrome](../import-and-export/import-guides/import-your-data-from-google-chrome.md)
* [Firefox](../import-and-export/import-guides/import-your-data-from-firefox.md)

## 保护您的密码库 <a href="#secure-your-vault" id="secure-your-vault"></a>

现在您的密码库中已充满了数据，让我们通过设置两步登录来采取一些措施来保护它。两步登录要求您在登录帐户时使用额外的「令牌」验证您的身份，「令牌」通常是从不同的设备中获取。

两步登录有很多[可用的方式](../../my-account/two-step-login/two-step-login-methods.md)，但对于免费 Bitwarden 帐户，推荐的方式是使用像 [Authy](https://authy.com/) 这样的移动设备身份验证器应用程序：

1、在您的移动设备上下载 Authy。

2、在您的 Bitwarden网页密码库中，选择配置文件图标并从下拉列表中选择**帐户设置**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/74BqYDU6qE9evz6wEz8K7Y/773eec1c0b00e00db4dedd3456e9a3f9/Screen_Shot_2022-05-13_at_10.34.10_AM.png?fm=webp&h=226&q=50&w=773" %}
账户设置
{% endembed %}

3、从帐户设置菜单中，选择**安全**页面然后选择**两步登录**选项卡。

4、定位到**验证器应用**选项然后选择**管理**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1InFT255RrriK85CfBkaoA/deb7e64cf51642e1ea444af43c4f49d2/Screen_Shot_2022-05-13_at_10.40.55_AM.png?fm=webp&h=616&q=50&w=773" %}
管理验证器应用
{% endembed %}

将提示您输入您的主密码以继续。

5、在您的移动设备上，打开 Authy 并点击 ✚**添加帐户**按钮。

6、使用 Authy 扫描您的网页密码库中的二维码。扫描完成后，Authy 将显示一个 6 位数的验证码。

7、在网页密码库的对话框中输入 6 位验证码，然后选择**启用**按钮。

8、选择**关闭**按钮返回两步登录界面，然后选择**查看恢复代码**按钮。

如果您丢失了移动设备，可以使用您的两步登录恢复代码。**这是确保您永远不会被锁定在密码库之外的关键步骤**，所以请不要跳过这一步！

9、输入您的主密码并选择**继续**按钮以获取您的恢复代码。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/y0iYBDQrnWIYSmMtsZF3s/048ebcda08abb8500e38912933adf639/recoverycode.png?fm=webp&h=200&q=50&w=462" %}
恢复代码示例
{% endembed %}

以最适合您的方式保存您的恢复代码。信不信由你，将您的恢复代码打印出来并将其保存在安全的地方，是使代码不易被盗或无意被删除的最佳方法之一。

## 下一步 <a href="#next-steps" id="next-steps"></a>

### 注册高级版 <a href="#signup-for-premium" id="signup-for-premium"></a>

恭喜您掌握了 Bitwarden 的基础知识！我们希望每个人都能安全上网，因此我们很自豪能够免费提供您在这里学到的一切。

对于个人用户，我们提供 **10 美元/年**的高级订阅，可解锁高级密码库功能，包括：

* 高级两步登录选项，例如 [Duo](../../my-account/two-step-login/setup-guides/two-step-login-via-duo.md) 和 [YubiKey 安全钥匙](../../my-account/two-step-login/setup-guides/two-step-login-via-yubikey.md)
* [加密文件附件](../vault-basics/file-attachments.md)的存储空间
* 内置[临时一次性密码（TOTP）身份验证器](../vault-basics/totp.md)
* 通过受信任的紧急联系人[紧急访问](../../my-account/more/emergency-access.md)您的密码库
* 报告密码和安全卫生的[密码库健康报告](../vault-administration/vault-health-reports.md)

要开始高级订阅：

1、在您的 Bitwarden 网页密码库中，从顶部导航栏中导航到**设置**选项卡。

2、从左侧的设置菜单中，选择**高级会员**。

### 开始一个组织 <a href="#start-an-organization" id="start-an-organization"></a>

您是否需要与朋友、家人、团队或整个企业共享密码或其他密码库项目？

Bitwarden 组织可让您做到这一点。我们建议[通过创建一个免费的 2 人组织](../../admin-console/getting-started-organizations.md)来尝试从组织中共享密码的功能。要了解如何操作，请参阅[组织入门](../../admin-console/getting-started-organizations.md)。

您测试了组织后，请查看我们的 [Bitwarden 计划和定价](https://bitwarden.com/pricing/business/)页面，了解您可能感兴趣的不同付费组织类型。

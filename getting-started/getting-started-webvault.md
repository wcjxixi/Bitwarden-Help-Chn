# Password Manager 网页 App

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/getting-started-webvault/)
{% endhint %}

Bitwarden 网页 App 为个人用户和组织提供了最丰富的 Bitwarden 体验。许多重要功能，例如设置[两步登录](../account/two-step-login/setup-guides/two-step-login-methods.md)或管理[组织](../admin-console/organizations-overview.md)，只能从网页 App 完成。

{% hint style="success" %}
可以从任何流行的网页浏览器访问网页 App，网址为 [vault.bitwarden.com](https://vault.bitwarden.com) 和 [vault.bitwarden.eu](https://vault.bitwarden.eu/)。如果您是**自托管** Bitwarden，则网址为您[已配置的域名](../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md)，例如 `https://my.bitwarden.server.com`。
{% endhint %}

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2xTpSA11EOCzx8VIuVffcF/d3bc18e7fc3c3cb0bf1779fad9262cd3/2024-12-02_13-42-14.png?_a=DAJCwlWIZAAB" %}
Bitwarden 网页 App
{% endembed %}

当您首次登录网页 App 时，您将进入**密码库**视图。此空间将列出您的所有密码库项目，包括[登录信息、支付卡、身份和安全笔记](../password-manager/your-vault/vault-items/vault-items.md)。

## 第一步 <a href="#first-steps" id="first-steps"></a>

在上面的屏幕截图中，**密码库**视图显示**我的密码库**视图中的 **☷所有项目**。[组织](../admin-console/organizations-overview.md)的用户将在此处列出其他密码库。使用**筛选器**列可以帮助您使用**收藏**和**文件夹**来组织您的密码库。

让我们设置一个新的文件夹并向其添加一个新的登录项目来作为开始：

### 创建文件夹 <a href="#create-a-folder" id="create-a-folder"></a>

要创建文件夹：

1、从下拉菜单中选择 ✚**新增**图标然后选择**文件夹**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BvTWidqL4xWQvFqBSiJIR/d68bc851d44df1b571eed16366159e0c/2024-12-02_13-50-55.png?_a=DAJCwlWIZAAB" %}
新增文件夹
{% endembed %}

2、为您的文件夹输入一个名称（例如 `Important Logins`），然后选择**保存**。

{% hint style="success" %}
为了使密码库更清爽，您可以[将文件夹嵌套在其他文件夹中](../password-manager/your-vault/vault-items/folders.md#nested-folders)。
{% endhint %}

### 添加登录 <a href="#add-a-login" id="add-a-login"></a>

要添加一个新的登录项目：

1、从下拉菜单中选择 ✚**新增**图标然后选择**登录。**

2、输入**项目名称**。名称用于帮助您轻松识别密码库中的项目，因此请为其指定一个可识别的名称（例如`My Gmail Account`）。

3、从**文件夹**下拉菜单中，选择要添加此项目的文件夹名称（例如，我们之前创建的 `Important Logins` 文件夹）。

4、为登录项目输入您的**用户名**和**密码**。现在，请输入您**现有的**密码，我们稍后会帮助您[用更强的密码替换它](getting-started-webvault.md#generate-a-strong-password)。

5、在**网站 (URI)** 字段中，输入网站的 URL（例如 `https://accounts.google.com`）。如果您不知道要使用哪个 URL，请导航到网站的登录界面并从地址栏中复制它。

{% embed url="https://bitwarden.com/assets/62IycEwbVrumSyPjB9n5XS/0df14e819c0881be3d813e235271acaf/2025-06-02_14-31-28.png?w=956&fm=avif&q=80" %}
定位 URI
{% endembed %}

6、选择 **⭐️收藏**图标以将此项目添加到您的收藏夹。标记为收藏时，图标将被填充（**★** → **✰**）。

7、干得好！选择**保存**按钮完成添加此项目。

### 生成强密码 <a href="#generate-a-strong-password" id="generate-a-strong-password"></a>

现在新的登录项目已保存在您的密码库中，您可以使用用更强的密码替换现有的密码来增强其安全性：

1、在您的密码库中，选择要保护的项目，打开并选择**编辑**按钮。

2、在新的标签页或窗口中，打开相应的网站并登录您的账户。

{% hint style="success" %}
如果您在 **URI 1** 字段中输入了某些内容，请单击 **⮫启动**图标以直接从您的密码库中打开它！
{% endhint %}

3、在该网站上，导航到可以**更改您的密码**的区域。

通常，您可以在**您的账户**、**安全**或**登录设置**部分中找到它。

4、大多数网站会要求您先输入**当前密码**。返回到您的 Bitwarden 密码库并单击**密码**字段旁边的 **❐复制**图标。然后，返回到该网站并将其粘贴到**当前密码**字段中。

您可能已经记住了旧的密码，但养成复制和粘贴密码是一个好的习惯，因为一旦你的密码被替换成更强的密码，你将主要以这种方式登录网站。

5、返回到您的 Bitwarden 密码库并单击**密码**字段旁边的 **⟳生成**图标。系统会询问您是否要覆盖当前密码，单击**是**以继续。

这将用随机生成的强密码替换您的**密码**值。从 `Fido1234` 这样的密码迁移到 `X@Ln@x9J@&u@5n##B` 可以阻止潜在的黑客入侵。

6、使用您之前使用的相同的 **❐复制**图标复制您的新密码，然后点击**保存**按钮。

{% hint style="info" %}
不用担心会覆盖您现有的密码！如果出现问题，Bitwarden 会为每个登录项目保存最近五个密码的[**密码历史记录**](../password-manager/your-vault/security-tools/password-and-generator-history.md#password-history)。
{% endhint %}

7、返回到刚才的网站，然后将您的强密码粘贴到**新密码**和**确认新密码**字段中。

8、**保存**密码更改后，您就完成了！

### 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

好消息！如果您将用户名和密码保存在网络浏览器或其他密码管理器中，则无需为每次登录重复以上过程。使用我们的专业导入指南之一来帮助您将数据直接传输到 Bitwarden：

* [LastPass](../password-manager/import-and-export/import-guides/import-data-from-lastpass.md)
* [1Password](../password-manager/import-and-export/import-guides/import-data-from-1password.md)
* [Dashlane](../import-export/import-guides/Import-data-from-dashlane.md)
* [macOS & Safari](../password-manager/import-and-export/import-guides/import-data-from-macos-and-safari.md)
* [Google Chrome](../password-manager/import-and-export/import-guides/import-data-from-chrome.md)
* [Firefox](../password-manager/import-and-export/import-guides/import-data-from-firefox.md)

## 保护您的密码库 <a href="#secure-your-vault" id="secure-your-vault"></a>

现在您的密码库中已充满了数据，让我们通过设置两步登录来采取一些措施来保护它。两步登录要求您在登录账户时使用额外的「令牌」验证您的身份，「令牌」通常是从不同的设备中获取。

两步登录有很多[可用的方式](../account/two-step-login/setup-guides/two-step-login-methods.md)，但对于免费 Bitwarden 账户，推荐的方式是使用像 [Bitwarden Authenticator](../bitwarden-authenticator/bitwarden-authenticator.md) 这样的移动设备身份验证器 App：

1、在您的移动设备上下载 Bitwarden Authenticator。

2、在您的 Bitwarden 网页 App 中，从导航中选择**设置** → **安全** → **两步登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2BsKs83g4cmiCUwxf2ad83/b2a90e85355f3d937aeb46139203737e/2024-12-02_10-54-31.png?_a=DAJCwlWIZAAB" %}
两步登录
{% endembed %}

3、定位到**验证器 App** 选项然后选择**管理**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5GqQynIX94PhzJQ0tVW1aE/5dcea8d04c8a543daa7f96989f220756/2024-12-02_10-55-22.png?_a=DAJCwlWIZAAB" %}
两步登录提供程序
{% endembed %}

将提示您输入您的主密码以继续。

4、在您的移动设备上，打开 Bitwarden Authenticator 并点击 ✚按钮。

5、使用 Bitwarden Authenticator 扫描您的网页 App 中的二维码。扫描完成后，Bitwarden Authenticator 将显示一个 6 位数的验证码。

6、在网页 App 的对话框中输入 6 位验证码，然后选择**启用**按钮。

7、选择**关闭**按钮返回两步登录界面，然后选择**查看恢复代码**按钮。

如果您丢失了移动设备，可以使用您的两步登录恢复代码。**这是确保您永远不会被锁定在密码库之外的关键步骤**，所以请不要跳过这一步！

8、输入您的主密码并选择**继续**按钮以获取您的恢复代码。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/64piqJsX7vN25To16iRFIp/09e977fae9485c0764f832c6bb4b4b04/2024-12-02_11-24-35.png?_a=DAJCwlWIZAAB" %}
示例恢复代码
{% endembed %}

以最适合您的方式保存您的恢复代码。信不信由你，将您的恢复代码打印出来并将其保存在安全的地方，是使代码不易被盗或无意被删除的最佳方法之一。

## 下一步 <a href="#next-steps" id="next-steps"></a>

### 注册高级版 <a href="#signup-for-premium" id="signup-for-premium"></a>

恭喜您掌握了 Bitwarden 的基础知识！我们希望每个人都能安全上网，因此我们很自豪能够免费提供您在这里学到的一切。

对于个人用户，我们提供 **10 美元/年**的高级订阅，可解锁高级密码库功能，包括：

* 高级两步登录选项，例如 [Duo](../account/two-step-login/setup-guides/two-step-login-via-duo.md) 和 [YubiKey 安全钥匙](../account/two-step-login/setup-guides/two-step-login-via-yubikey.md)
* [加密文件附件](../password-manager/your-vault/vault-items/file-attachments.md)的存储空间
* 集成的[临时一次性密码（TOTP）身份验证器](../password-manager/your-vault/security-tools/totp.md)
* 通过受信任的紧急联系人[紧急访问](../account/log-in-and-unlock/more-log-in-options/emergency-access.md)您的密码库
* 报告密码和安全卫生的[密码库健康报告](../password-manager/your-vault/security-tools/vault-health-reports.md)

要开始高级订阅，请从**密码库**视图中选择**成为高级会员**按钮！

### 开始一个组织 <a href="#start-an-organization" id="start-an-organization"></a>

您是否需要与朋友、家人、团队或整个企业共享密码或其他密码库项目？

Bitwarden 组织可让您做到这一点。我们建议[通过创建一个免费的 2 人组织](../admin-console/organizations-quick-start.md)来尝试从组织中共享密码的功能。要了解如何操作，请参阅[组织入门](../admin-console/organizations-quick-start.md)。

您测试了组织后，请查看我们的 [Bitwarden 定价](https://bitwarden.com/pricing/business/)页面，了解您可能感兴趣的不同付费组织类型。

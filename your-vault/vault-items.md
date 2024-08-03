# 密码库项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-items/)
{% endhint %}

有效地管理密码库中的项目，是确保安全且无缝访问您的信息，并与朋友、家人、团队和同事安全地共享信息的关键。在密码库中可以存储 4 种类型的项目：登录、支付卡、身份和安全笔记：

{% tabs %}
{% tab title="登录" %}
登录项目常用于存储用户名和密码的组合，并支持针对高级用户的 [TOTP 种子](totp.md)。无论您使用的是何种计划，我们都建议为每个登录提供[一个用于方便自动填充的 URI](../auto-fill/using-uris.md)：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5VGRnEvX53BOXa9CCgrhRx/2b27a7adf52a265247be62ebb884223d/Screenshot_2024-02-27_at_10.01.05_AM.png?_a=DAJAUVWIZAAB" %}
登录项目
{% endembed %}
{% endtab %}

{% tab title="支付卡" %}
支付卡项目可用于存储信用卡或借记卡信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/UW8udnRVCQlJyIaCtmG2a/88533f233d9b41185cf306066feb1a73/Screenshot_2024-02-27_at_10.01.52_AM.png?_a=DAJAUVWIZAAB" %}
支付卡项目
{% endembed %}
{% endtab %}

{% tab title="身份" %}
身份信息可用于存储账单信息、邮寄信息或其他任何你在填写在线表格时可能需要访问的信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6R14M0PBJL8RaAP4ye3P4O/d650579a8d381c85237251f6d57836af/Screenshot_2024-02-27_at_10.02.51_AM.png?_a=DAJAUVWIZAAB" %}
身份项目
{% endembed %}
{% endtab %}

{% tab title="安全笔记" %}
安全笔记可用于存储被加密的你想要保护的任何自由格式的文本信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7dkefRm7YAdn1e3FmxgCeN/df8c8f2c5f278bd2620618f2120b2bec/Screenshot_2024-02-27_at_10.03.25_AM.png?_a=DAJAUVWIZAAB" %}
安全笔记项目
{% endembed %}
{% endtab %}
{% endtabs %}

{% hint style="success" %}
您可以从大多数密码管理器或 Web 浏览器将项目直接导入到您的密码库。[了解更多](../import-export/import-data-to-your-vault.md)。
{% endhint %}

## 按密码库筛选 <a href="#filter-by-vault" id="filter-by-vault"></a>

您可以根据项目是在您的个人密码库（**我的密码库**）还是在组织密码库中来筛选要列出的项目。按密码库筛选：

{% tabs %}
{% tab title="网页 App" %}
任选一个：

* 从筛选器列中选择一个密码库名称（在下面的屏幕截图中为 **My Vault** 或 **My Organization**）。
* 选择项目旁边的彩色卡片之一（在下面的屏幕截图中为 **Me** 或 **My Organization**）。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1UhfLlwmahJgbi0bcBtPLT/6f5ec9345231c7d0f0d9b62c25c5ce38/Screenshot_2024-02-27_at_10.07.50_AM.png?_a=DAJAUVWIZAAB" %}
网页 App 筛选器
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
在**密码库**选项卡上的**所有密码库**下拉列表中选择一个密码库：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7sZ4ZAcAGqPWwqCXMky2Ji/ec44e17cb78c485c2c9e1d7912179b75/extension-filtering.png?_a=DAJAUVWIZAAB" %}
浏览器扩展筛选器
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
通过在**我的密码库**选项卡上的**密码库**菜单按钮 (**⋯**) 来选择一个密码库：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/44WqYfqzP9JOJPSZ4Yrzjb/a0a1913ec7b2ec9607d1f4902e639817/mobile-filtering.png?_a=DAJAUVWIZAAB" %}
移动端筛选器
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
从最左边的列中选择一个密码库（在下面的屏幕截图中为 **My Vault** 或 **My Organization**）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2Lng0L2TRQ177CaU8EUQ1m/394ca15fe8df8ce02b9b7ecfa33bb0db/desktop-filtering.png?_a=DAJAUVWIZAAB" %}
桌面端啊筛选器
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用带有 `--organizationid` 选项（组织标识符或 `null`）的 `bw list` 命令，按密码库列出项目。[了解更多](../bitwarden-send/send-from-cli.md#list)。
{% endtab %}
{% endtabs %}

## 管理密码库项目 <a href="#manage-vault-items" id="manage-vault-items"></a>

您可以通过任何 Bitwarden 客户端应用程序添加、编辑和删除密码库项目：

{% tabs %}
{% tab title="网页 App" %}
{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3DW8eh1BQbXObEReorFMW4/50150422da1825766eedffe3a5cf4224/Screenshot_2024-02-27_at_10.10.57_AM.png?_a=DAJAUVWIZAAB" %}
管理项目
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1OddsCwTDlM6yeTNM9GABo/33ef81976203ac284c720af8e3c54651/manage-be.png?_a=DAJAUVWIZAAB" %}
管理项目
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6l8JWKYvh6tVEAY98V5z91/a35b3912e22575b6098425e0be5694ba/bitwarden-mobile-trio-june22.png?_a=DAJAUVWIZAAB" %}
添加或打开项目
{% endembed %}

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/34vxnR6U71CYrcacVkvOve/3471871cc30f7e45ca123ad072e5552a/manage-mobile-2.png?_a=DAJAUVWIZAAB" %}
管理项目
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/25mBh7DRc8X3eZGWFPFZVf/5467a6f940d11b3a3a984f41dc456e53/Screen_Shot_2022-05-18_at_3.49.17_PM.png?_a=DAJAUVWIZAAB" %}
管理项目
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
更多信息，请参阅 [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

除了添加、编辑和删除密码库项目之外，您还可以[克隆](vault-items.md#clone)项目以创建副本、[移动项目](vault-items.md#move-to-organization)到组织以及[保护个人项目](vault-items.md#protect-individual-items)。

### 克隆 <a href="#clone" id="clone"></a>

如果您想创建一个项目的副本，您可以克隆对其具有**所有权**的任何密码库项目：

{% tabs %}
{% tab title="网页 App" %}
在悬停 **⚙️齿轮**下拉菜单中选择**克隆**。
{% endtab %}

{% tab title="浏览器扩展" %}
打开项目然后选择 :dividers:**克隆项目**选项。
{% endtab %}

{% tab title="移动端" %}
打开项目然后在 **≡菜单**中选择**克隆**。
{% endtab %}

{% tab title="桌面端" %}
打开项目然后选择 :dividers:**克隆项目**选项。
{% endtab %}
{% endtabs %}

要克隆组织拥有的项目，必须从[组织密码库视图](../admin-console/organizations-quick-start.md#get-to-know-your-organization)中克隆它。

### 分配到集合 <a href="#assign-to-collections" id="assign-to-collections"></a>

如果您是[组织](../organizations/organizations.md)的成员，您可以将密码库项目分配到组织的集合中，从而将密码库项目的所有权转移给该组织。要与其他组织成员共享，请使用 **≡** 菜单：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/stm9byteqzZn9dvqonHrc/ae2cd1e4af385676f6d19c1b53349dc5/2024-07-15_14-16-27_copy.png?_a=DAJAUVWIZAAB" %}
分配到集合
{% endembed %}

了解更多关于[组织](../organizations/organizations.md)、[集合](../organizations/collections.md)和[共享](../organizations/sharing.md)的信息。

### 保护个人项目 <a href="#protect-individual-items" id="protect-individual-items"></a>

对于任何项目，您可以从添加/编辑界面激活**主密码重新提示**选项，以要求验证您的主密码以访问或自动填充敏感的密码库项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/sgKb0RX5hGdrdKLmXcR0R/96283084869bd9b7a66a2bfb3dd4325e/Screenshot_2024-02-27_at_10.14.21_AM.png?_a=DAJAUVWIZAAB" %}
主密码重新提示
{% endembed %}

主密码重新提示的行为会略有不同，具体取决于您使用的应用程序，例如：

* 在网页 App 中，访问或编辑有关启用此功能的密码库项目的任何内容都将要求您重新输入主密码。
* 在浏览器扩展、桌面 App 和移动 App 上，仅查看隐藏字段（例如密码、隐藏的自定义字段、信用卡号）将需要您重新输入主密码。编辑有关该项目的任何内容也需要您重新输入主密码。

没有主密码的用户（例如，使用[受信任设备 SSO](../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 或 [Key Connector](../login-with-sso/about-key-connector.md) 的组织中的用户）将禁用主密码重新提示。此外，使用[紧急访问](../security/emergency-access.md#use-emergency-access)的受信任联系人无需重新输入主密码即可查看受保护的密码库项目。

{% hint style="warning" %}
主密码重新提示**并非**一种加密机制。此功能是一个仅限于界面的防护栏，老练的用户可能会找到解决方法。我们建议您在无人看守或在共享工作站上，不要让您的密码库处于解锁状态。
{% endhint %}

## 密码库回收站 <a href="#vault-trash" id="vault-trash"></a>

已删除的项目将被发送到回收站，删除后它们会保留 30 天。30 天过后，该项目将被永久删除且不可恢复。

在回收站中，您可以在 30 天等待期之前将项目**恢复**到您的密码库或**永久删除**它：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/36mo5LyroRq1BhOcjSsBb7/c4471d58aa44104d23dea48a48d29394/Screenshot_2024-02-27_at_10.17.42_AM.png?_a=DAJAUVWIZAAB" %}
回收站
{% endembed %}

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

现在，您已了解密码库项目使用的基础知识，我们建议：

* 使用[收藏](favorites.md)和[文件夹](folders.md)组织您的密码库项目
* 将[自定义字段](custom-fields.md)、[TOTP 种子](totp.md)和[文件附件](file-attachments.md)添加到密码库项目

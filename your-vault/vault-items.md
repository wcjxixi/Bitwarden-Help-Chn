# 密码库项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-items/)
{% endhint %}

您知道 Bitwarden 能安全存储的不仅仅是用户名和密码吗？您可以在密码库中存储四种类型的项目：登录、支付卡、身份、安全笔记和 SSH 密钥：

{% tabs %}
{% tab title="登录" %}
登录常用于存储用户名和密码的组合，并支持针对高级用户的 [TOTP 种子](totp.md)。无论您使用的是何种计划，我们都建议为每个登录提供一个[用于方便自动填充的 URI](../auto-fill/using-uris.md)：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5VGRnEvX53BOXa9CCgrhRx/9cdf22fc63819a8f24fc80f0effb5ad3/2024-12-02_14-17-14.png?_a=DAJCwlWIZAAB" %}
登录项目
{% endembed %}
{% endtab %}

{% tab title="支付卡" %}
支付卡项目可用于安全地存储信用卡或借记卡信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/UW8udnRVCQlJyIaCtmG2a/3b9c6078375f2c3aad1249f2e24c6368/2024-12-02_14-17-57.png?_a=DAJCwlWIZAAB" %}
支付卡项目
{% endembed %}
{% endtab %}

{% tab title="身份" %}
身份可用于存储计费、邮寄或其他任何您在填写在线表格时可能需要填写的信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6R14M0PBJL8RaAP4ye3P4O/4ce75723fa117798cbe9db67b8fa7c9b/2024-12-02_14-18-25.png?_a=DAJCwlWIZAAB" %}
身份项目
{% endembed %}
{% endtab %}

{% tab title="安全笔记" %}
安全笔记可用于存储被加密的您想要保护的任何自由格式的文本信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7dkefRm7YAdn1e3FmxgCeN/9c975630d8d64bcec33435370a427076/2024-12-02_14-17-35.png?_a=DAJCwlWIZAAB" %}
安全笔记项目
{% endembed %}
{% endtab %}
{% endtabs %}

{% hint style="success" %}
您可以从大多数密码管理器或网页浏览器将项目直接导入到您的密码库。[了解更多](../import-export/import-data-to-your-vault.md)。
{% endhint %}

## 个人和组织密码库 <a href="#individual-and-organizational-vaults" id="individual-and-organizational-vaults"></a>

许多 Bitwarden 用户都可以访问个人密码库和组织密码库。了解如何有效使用和管理每种密码库：

{% embed url="https://vimeo.com/823390347" %}

## 筛选密码库项目 <a href="#filter-vault-items" id="filter-vault-items"></a>

您可以根据几个不同的特征来筛选要列出的项目。要筛选密码库项目：

{% tabs %}
{% tab title="网页 App" %}
任选一个：

* 从**筛选器**栏中选择一个特征（在下面的屏幕截图中为 **Login**）。
* 选择项目旁边的彩色卡片之一（在下面的屏幕截图中为 **Me** 或 **My Organization**）。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1UhfLlwmahJgbi0bcBtPLT/b4b1875602b0ea555626c98a388779b8/2024-12-02_14-23-39.png?_a=DAJCwlWIZAAB" %}
网页 App 筛选
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
使用 **🔒密码库**选项卡顶部的**密码库**、**集合**、**文件夹**或**类型**选择器。您可以使用 **☷**&#x6309;钮显示或隐藏筛选器下拉菜单：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/12UsFuA2sxbUCBMIczJsxv/22c20404137193420d3b2d1f5fa8611f/2024-12-02_14-07-09.png?_a=DAJCwlWIZAAB" %}
浏览器扩展筛选和建议
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
通过在**密码库**选项卡上的**密码库**菜单按钮 (**⋯**) 来选择一个密码库：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/44WqYfqzP9JOJPSZ4Yrzjb/9167f19bc2e27a158be5ed3fc29a5689/2025-01-21_15-38-59.png?_a=DAJCwlWIZAAB" %}
移动端筛选密码库
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
从最左边的列中选择一个密码库（在下面的屏幕截图中为 **My Vault** 或 **My Organization**）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2Lng0L2TRQ177CaU8EUQ1m/394ca15fe8df8ce02b9b7ecfa33bb0db/desktop-filtering.png?_a=DAJCwlWIZAAB" %}
桌面端筛选
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用带有 `--organizationid` 选项（组织标识符或 `null`）的 `bw list` 命令，按密码库列出项目。[了解更多](../bitwarden-send/send-from-cli.md#list)。
{% endtab %}
{% endtabs %}

## 管理密码库项目 <a href="#manage-vault-items" id="manage-vault-items"></a>

您可以通过任何 Bitwarden App 添加、编辑和[删除](vault-items.md#vault-trash)密码库项目：

{% tabs %}
{% tab title="网页 App" %}
{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3DW8eh1BQbXObEReorFMW4/efdc8af89bd39e2a5657ffa9c264c0c7/2024-12-02_14-30-14.png?_a=DAJCwlWIZAAB" %}
管理项目
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1OddsCwTDlM6yeTNM9GABo/850ce0337579d58f3d5a6f0ea5017638/2024-12-04_15-44-36.png?_a=DAJCwlWIZAAB" %}
管理项目
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
轻点一个项目打开它，或轻点 ✚图标添加新的项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6l8JWKYvh6tVEAY98V5z91/b57d0427062c8902088447206cfaa1d2/2025-01-21_15-41-30.png?_a=DAJCwlWIZAAB" %}

查看项目时，轻按 **✏️**图标进行编辑，或轻按 **≡**&#x9009;项菜单进行编辑：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/34vxnR6U71CYrcacVkvOve/079268a716fc07938e1c065476ccab4f/2025-01-21_15-44-31.png?_a=DAJCwlWIZAAB" %}
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

如果您想复制您拥有所有权的任何项目，您可以克隆该项目。克隆组织所拥有的项目只能由所有者、管理员和具有[**可以管理**](../admin-console/organization-basics/collection-management.md#collection-management-settings)权限的用户从网页 App 的[管理控制台](../admin-console/organizations-quick-start.md)或从密码库视图进行：

{% tabs %}
{% tab title="网页 App" %}
从 **≡选项**菜单选择**克隆**。
{% endtab %}

{% tab title="浏览器扩展" %}
在 **🔒密码库**标签中，选择该项目的 **≡**&#x9009;项菜单，然后从下拉菜单中选择**克隆**。
{% endtab %}

{% tab title="移动端" %}
打开项目然后在 **≡菜单**中点击**克隆**。
{% endtab %}

{% tab title="桌面端" %}
打开项目然后选择 :dividers:**克隆项目**选项。
{% endtab %}
{% endtabs %}

### 分配到集合 <a href="#assign-to-collections" id="assign-to-collections"></a>

如果您是[组织](../organizations/organizations.md)的成员，您可以将密码库项目分配到组织的集合中，从而将密码库项目的所有权转移给该组织。要与其他组织成员共享，请使用 **≡** 菜单：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/stm9byteqzZn9dvqonHrc/0da481b0cf1f54457d08ae02fd917377/2024-12-02_14-33-34.png?_a=DAJCwlWIZAAB" %}
分配到集合
{% endembed %}

了解更多关于[组织](../organizations/organizations.md)、[集合](../organizations/collections.md)和[共享](../organizations/sharing.md)的信息。

### 保护个人项目 <a href="#protect-individual-items" id="protect-individual-items"></a>

对于任何项目，您可以从添加/编辑界面激活**主密码重新提示**选项，以要求验证您的[主密码](your-master-password.md)以访问或自动填充敏感的密码库项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/sgKb0RX5hGdrdKLmXcR0R/f78654839e18b3f474dd3e95ed0d203c/2024-12-02_14-38-06.png?_a=DAJCwlWIZAAB" %}
主密码重新提示
{% endembed %}

主密码重新提示的行为会略有不同，具体取决于您使用的 App，例如：

* 在网页 App 中，访问或编辑启用了此功能的密码库项目的任何内容都将要求您重新输入主密码。
* 在浏览器扩展、桌面 App 和移动 App 上，仅查看隐藏字段（例如密码、隐藏的自定义字段、信用卡号）将需要您重新输入主密码。编辑有关该项目的任何内容也需要您重新输入主密码。

没有主密码的用户（例如，使用[受信任设备 SSO](../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 或 [Key Connector](../login-with-sso/about-key-connector.md) 的组织中的用户）将禁用主密码重新提示。此外，使用[紧急访问](../security/emergency-access.md#use-emergency-access)的受信任联系人无需重新输入主密码即可查看受保护的密码库项目。

{% hint style="warning" %}
主密码重新提示**并非**一种加密机制。此功能是一个仅限于界面的防护栏，老练的用户可能会找到解决方法。我们建议您在无人看守或在共享工作站上，不要让您的密码库处于解锁状态。
{% endhint %}

## 密码库回收站 <a href="#vault-trash" id="vault-trash"></a>

已删除的项目将被发送到回收站，删除后它们会保留 30 天。30 天过后，该项目将被永久删除且不可恢复。

在回收站中，您可以在 30 天等待期之前使用 **≡**&#x83DC;单将项目**恢复**到您的密码库或**永久删除**它：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/36mo5LyroRq1BhOcjSsBb7/a05100ab172376caf15b4c454beee321/2024-12-02_14-39-40.png?_a=DAJCwlWIZAAB" %}
回收站
{% endembed %}

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

现在，您已了解密码库项目使用的基础知识，我们建议：

* 使用[收藏](favorites.md)和[文件夹](folders.md)组织您的密码库项目
* 将[自定义字段](custom-fields.md)、[TOTP 种子](totp.md)和[文件附件](file-attachments.md)添加到密码库项目

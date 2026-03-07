# 密码库项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-items/)
{% endhint %}

## 项目类型 <a href="#item-types" id="item-types"></a>

Bitwarden 能安全存储的不仅仅是用户名和密码。您可以在密码库中存储五种类型的项目：

* **登录**：用于存储用户名和密码的组合，以便在[浏览器扩展](../../autofill/autofill-from/autofill-from-browser-extensions.md)、[iOS App](../../autofill/autofill-from/autofill-from-ios.md) 和 [Android App](../../autofill/autofill-from/autofill-from-android.md) 上轻松自动填充。登录项目还可以存储[通行密钥](../../autofill/more-autofill-options/autofill-passkeys.md)，对于高级用户，还可以存储[验证码](../security-tools/totp.md)。
* **支付卡**：用于存储信用卡或借记卡信息，以便在线结账时[在浏览器扩展和 Android App 上轻松自动填充](../../autofill/more-autofill-options/auto-fill-cards-and-identities.md)。
* **身份**：用于存储身份信息（例如邮寄地址），以便在各种在线表单提交期间[在浏览器扩展和 Android App 上轻松自动填充](../../autofill/more-autofill-options/auto-fill-cards-and-identities.md)。
* **安全备注**：用于存储您想要保护的任何类型的信息的自由格式文本。
* **SSH 密钥**：使用 Bitwarden [作为 SSH 代理](../../developer-tools/ssh/ssh-agent.md)。

## 添加项目 <a href="#add-items" id="add-items"></a>

{% hint style="success" %}
本章节介绍如何手动添加密码库项目，但对于许多用户来说，Bitwarden 建议从大多数密码管理器或网页浏览器直接[导入项目](../../../secrets-manager/import-export/import-data.md)到您的密码库中。
{% endhint %}

您可以从任何 Bitwarden App 添加密码库项目：

{% tabs %}
{% tab title="网页 App" %}
选择 **✚新增**按钮然后选择要创建的项目类型：

{% embed url="https://bitwarden.com/assets/5kGYpHHu4197INxX5kOetu/c1aa36b3847c9824b81466837229ec7d/webappnewtest.png?w=1200&fm=avif" %}
添加项目
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择 **✚新增**按钮然后选择要创建的项目类型：

{% embed url="https://bitwarden.com/assets/3CGG1jYRfgQqi5UlWuwliO/c95b2da5c9e64564c1aa7842207a3a6f/extnew1.png?w=1118&fm=avif" %}
添加项目
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
选择 **✚新增**按钮然后选择要创建的项目类型：

{% embed url="https://bitwarden.com/assets/cMVnILAl9uoih1iTqIHx9/19168711ae327ea490fa51c8d9c27ff3/mobilenew1.png?w=961&fm=avif" %}
添加项目
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
{% embed url="https://bitwarden.com/assets/7xia34eJyx1K8Gy8IXajQ7/36bac46c997498ba821b5cc347eeb65a/desktopnew1.png?w=1054&fm=avif" %}
添加项目
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用 `create` 命令添加新的项目。请参阅 [CLI 文档](../../developer-tools/cli/password-manager-cli.md)以获取更多信息。
{% endtab %}
{% endtabs %}

## 管理项目 <a href="#manage-items" id="manage-items"></a>

您可以从任何 Bitwarden App 管理您的密码库项目：

### 编辑 <a href="#edit" id="edit"></a>

要编辑项目：

{% tabs %}
{% tab title="网页 App" %}
选择您要编辑的项目的 **≡**&#x9009;项菜单：

{% hint style="success" %}
您也可以右键单击该项目来调出相同的菜单。
{% endhint %}

{% embed url="https://bitwarden.com/assets/5FmC9ha8GQ4IKU8UM1ra4x/d470974c62468ba565e58ca1917db0b1/webnew1.png?w=1150&fm=avif" %}
编辑或删除项目
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择一个项目将其打开，然后选择**编辑**：

{% embed url="https://bitwarden.com/assets/2q1EZnISzEG3i8iU4vTKj6/b13c46c27a7fb896f31f81485859459f/extnew4.png?w=1118&fm=avif" %}
编辑或删除项目
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
选择要编辑的项目的 **≡**&#x9009;项菜单，然后选择**编辑**：

{% embed url="https://bitwarden.com/assets/357lJe8JKMXNKEhYKUDn4u/31d5f1f811eb35b8b142f9a6f751dae2/2025-11-10_12-05-53.png?w=961&fm=avif" %}
编辑项目
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
选择一个项目将其打开，然后选择 **✏️**编辑图标：

{% embed url="https://bitwarden.com/assets/6Y4kK7J9aLmo9SDY7Ne8VE/0c422e65f5af509b368ec59928fcd308/desktopnew2.png?w=1054&fm=avif" %}
编辑项目
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用 `edit` 命令编辑项目。请参阅 [CLI 文档](../../developer-tools/cli/password-manager-cli.md)以获取更多信息。
{% endtab %}
{% endtabs %}

### 归档 <a href="#archive" id="archive"></a>

归档是一个整理密码库的有用工具。归档的项目不会出现在搜索结果和自动填充建议中，但会包含在导出中。归档：

* 适用于所有付费方案，包括高级用户和付费组织的成员。如果订阅曾经中断，用户**不会**失去对已归档项目的访问权限。
* 适用于组织项目和个人项目。与[收藏](../vault-navigation/favorites.md)类似，某个用户选择归档项目，并不会为其他有访问权限的用户归档该项目。
* **不会**从报告或导出中移除项目。

要归档项目：

{% tabs %}
{% tab title="网页 App" %}
选择您想要归档的项目，然后使用 **≡**&#x9009;项菜单选择**归档**：

{% embed url="https://bitwarden.com/assets/1aRyGxLdpcvGF3fM2Bbd17/24408086dd8835286d079cb48cd6069a/2026-01-27_10-28-36.png?w=800&fm=avif" %}
使用网页 App 归档
{% endembed %}

在网页 App 中，从您的密码库筛选器中选择**归档**，以查看已归档的项目，然后使用 **≡**&#x9009;项菜单选择**取消归档**，即可将项目恢复到正常的密码库状态。
{% endtab %}

{% tab title="浏览器扩展" %}
使用您想要归档的项目的 **≡**&#x9009;项菜单，然后选择**归档**：

{% embed url="https://bitwarden.com/assets/40gA9zgbeBjx2gw77H61kM/08e93903af859aa75bbdd277b4098a90/2026-01-27_10-40-25.png?w=800&fm=avif" %}
使用浏览器扩展归档
{% endembed %}

在浏览器扩展中，导航至**设置** → **密码库选项** → **归档**，以查看已归档的项目，然后使用 **≡**&#x9009;项菜单选择**取消归档**，即可将项目恢复到正常的密码库状态。
{% endtab %}

{% tab title="移动 App" %}
使用您想要归档的项目的 **⋯**&#x9009;项菜单，然后选择**归档**：

{% embed url="https://bitwarden.com/assets/rrxmgUU3pLqQrYa5wDDb9/fd90c478bacd1c366e59b4be3d07b185/2026-02-23_11-48-54.png?w=800&fm=avif" %}
使用移动 App 归档
{% endembed %}

在移动 App 中，从您的密码库筛选器中选择**归档**，以查看已归档的项目，然后使用 **≡**&#x9009;项菜单选择**取消归档**，即可将项目恢复到正常的密码库状态。
{% endtab %}

{% tab title="桌面 App" %}
打开您想要归档的项目，然后选择**归档**按钮：

{% embed url="https://bitwarden.com/assets/kOYhUPQwYRL9Rm0SKwxsf/1bb7a48646276475df915a73b5ece014/2026-01-27_10-52-53.png?w=800&fm=avif" %}
使用桌面 App 归档
{% endembed %}

在桌面 App 中，从您的密码库筛选器中选择**归档**，以查看已归档的项目，然后使用 **≡**&#x9009;项菜单选择**取消归档**，即可将项目恢复到正常的密码库状态。
{% endtab %}

{% tab title="CLI" %}
要归档一个项目，请使用命令 `bw archive item <item-id>`，其中 `<item-id>` 代表您想要归档的项目的唯一标识符。

要查看归档中的项目，请使用命令 `bw list --archive`。
{% endtab %}
{% endtabs %}

### 删除 <a href="#delete" id="delete"></a>

要删除项目：

{% tabs %}
{% tab title="网页 App" %}
选择该项目的 **≡**&#x9009;项菜单，然后选择 **🗑️删除**：

{% embed url="https://bitwarden.com/assets/3OYHvfRCDy3OphkbEHIJEA/fa47beb671d6efc34a18d05daf630aff/webappnewtest3.png?w=1200&fm=avif" %}
项目选项
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择一个项目将其打开，然后选择 **🗑️**删除图标：

{% embed url="https://bitwarden.com/assets/2q1EZnISzEG3i8iU4vTKj6/b13c46c27a7fb896f31f81485859459f/extnew4.png?w=1118&fm=avif" %}
编辑或删除项目
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
点击某个项目将其打开，然后选择该项目的 **≡**&#x9009;项菜单：

{% embed url="https://bitwarden.com/assets/6XFamLqIYX26cUY5LWQbPE/1a6000050526e7f4f9e8bfcad93619fe/2025-11-10_12-06-19.png?w=961&fm=avif" %}
项目选项
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
选择一个项目将其打开，然后选择 **🗑️**删除图标：

{% embed url="https://bitwarden.com/assets/1E8ieEw6639tLYAxe2HYir/f12ba224477f2338beae164c21f660eb/desktopnew3.png?w=1054&fm=avif" %}
删除项目
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用 `delete` 命令删除项目。请参阅 [CLI 文档](../../developer-tools/cli/password-manager-cli.md)以获取更多信息。
{% endtab %}
{% endtabs %}

#### 密码库回收站 <a href="#vault-trash" id="vault-trash"></a>

已删除的项目将被发送到回收站，删除后它们会保留 30 天。30 天过后，该项目将被永久删除且不可恢复。

在回收站中，您可以在 30 天等待期之前使用 **≡**&#x83DC;单将项目**恢复**到您的密码库或**永久删除**它：

{% tabs %}
{% tab title="网页 App" %}
从筛选菜单选择**回收站**：

{% embed url="https://bitwarden.com/assets/36mo5LyroRq1BhOcjSsBb7/a05100ab172376caf15b4c454beee321/2024-12-02_14-39-40.png?w=1038&fm=avif&q=80" %}
网页 App 中的回收站
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
导航到**设置** → **密码库** → **回收站**：

{% embed url="https://bitwarden.com/assets/5Q0mgKjaDiIKy5ymlVaUnS/fa72b454697bedd7319da17ba671a9e5/2025-04-15_09-33-59.png?w=818&fm=avif&q=80" %}
浏览器扩展中的回收站
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
在**密码库**选项卡上，向下滚动到**回收站**，然后选择项目：

{% embed url="https://bitwarden.com/assets/7HwDVQp0ma6RxU95ILNVtI/52275cc54ff5d789f8825d225edb0ecf/2025-04-15_10-22-16.png?w=680&fm=avif&q=80" %}
移动 App 中的回收站
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
从导航栏选择**回收站**：

{% embed url="https://bitwarden.com/assets/viaKopya1CJ9N6mWKyLV6/e6fb6c21ef79f87f8d701ea7e8e2d2c3/2025-08-13_14-36-35.png?w=900&fm=avif&q=80" %}
桌面 App 中的回收站
{% endembed %}
{% endtab %}
{% endtabs %}

### 克隆 <a href="#clone" id="clone"></a>

您可以克隆您拥有所有权的任何项目来创建重复项目。如果项目归组织所有，则只能由对项目的集合具有[**可以管理**](../../../admin-console/manage-shared-items/collections/collection-settings.md#list-of-settings)访问权限的成员进行克隆，并且只能通过网页 App 完成：

{% tabs %}
{% tab title="网页 App" %}
选择要复制的项目的 **≡**&#x9009;项菜单，然后选择 **❐**&#x514B;隆：

{% embed url="https://bitwarden.com/assets/3OYHvfRCDy3OphkbEHIJEA/fa47beb671d6efc34a18d05daf630aff/webappnewtest3.png?w=1200&fm=avif" %}
项目选项
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择要复制的项目的 **≡**&#x9009;项菜单，然后选择 **❐**&#x514B;隆：

{% embed url="https://bitwarden.com/assets/10bowrbDmxxf8SxrMhplmJ/01597fd4926492def941caf556cd9d12/extnew5.png?w=1118&fm=avif" %}
项目选项
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
击某个项目将其打开，然后选择该项目的 **≡**&#x9009;项菜单：

{% embed url="https://bitwarden.com/assets/6XFamLqIYX26cUY5LWQbPE/1a6000050526e7f4f9e8bfcad93619fe/2025-11-10_12-06-19.png?w=961&fm=avif" %}
项目选项
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
选择一个项目将其打开，然后选择 **❐**&#x514B;隆图标：

{% embed url="https://bitwarden.com/assets/5KRdegIaIbOHxGkMj64Fs9/705d1dfe97b326f75502b9971df4a0aa/desktopnew4.png?w=1054&fm=avif" %}
克隆项目
{% endembed %}
{% endtab %}
{% endtabs %}

## 共享项目 <a href="#share-items" id="share-items"></a>

如果您是[组织](../../../admin-console/organizations-overview.md)的成员，您可以[将密码库项目分配到组织的集合中](../../organization-members/sharing.md)，从而将密码库项目的所有权转移给该组织。要与其他组织成员共享，请使用 **≡**&#x83DC;单：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/stm9byteqzZn9dvqonHrc/0da481b0cf1f54457d08ae02fd917377/2024-12-02_14-33-34.png?_a=DAJCwlWIZAAB" %}
分配到集合
{% endembed %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在，您已了解密码库项目使用的基础知识，我们建议：

* 了解如何使用[检索](../vault-navigation/search-vault.md)、[筛选](../vault-navigation/filter-vault.md)以及在[收藏夹](../vault-navigation/favorites.md)和[文件夹](../vault-navigation/folders.md)中组织密码库来导航您的密码库。
* 了解您还可以向项目添加哪些内容，包括[自定义字段](custom-fields.md)、[TOTP 种子](../security-tools/totp.md)和[文件附件](file-attachments.md)。

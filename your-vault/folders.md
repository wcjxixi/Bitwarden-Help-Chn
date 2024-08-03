# 文件夹

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/folders/)
{% endhint %}

文件夹是用于通过收集登录、支付卡、身份和安全笔记来组织您的个人密码库的结构。使用文件夹是使所有密码库项目易于查找的比较好的方法。可以将任何密码库项目（包括[组织已与您共享的项目](../organizations/sharing.md)）添加到文件夹中。

{% hint style="success" %}
当从筛选器菜单中选择 **☷所有项目**时，添加到文件夹的项目仍会出现在您的密码库中，删除文件夹并**不会**删除该文件夹中的项目。
{% endhint %}

## 创建文件夹 <a href="#create-a-folder" id="create-a-folder"></a>

可以从任何 Bitwarden 客户端应用程序来创建、重命名和删除文件夹：

{% tabs %}
{% tab title="网页密码库" %}
要创建文件夹，请从文件夹列表中选择 ✚**添加**图标：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7zBHis0lDxSnn2ZrB3u7Ra/c9aa79df51aa5e1821fb52bff02ff707/folder-add-web.png?fm=webp&h=496&q=50&w=757" %}
添加文件夹
{% endembed %}

创建文件夹后，您可以随时通过选择此文件夹然后悬停在 :pencil2:**铅笔**图标上来**重命名或删除**文件夹。

{% embed url="https://bitwarden.com/help/images/manage-items/folder-delete-wv.png" %}
编辑或删除文件夹
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
要创建文件夹，请选择 **⚙️设置**菜单，选择**文件夹**选项，然后点击或选择 ✚**添加**图标：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4yq0Dhjt7R1ZjXhM3ACxoH/818870fa0875d0cd7e000d73b0f0e1d3/folder-add-extension.gif?fm=gif&h=730&q=50&w=958" %}
添加文件夹
{% endembed %}

创建文件夹后，您可以随时从同一菜单中选择现有的文件夹来**重命名或删除**文件夹：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7lSQX5GAIQxN0BjPGPqvYo/46cdc82ba0043e9e30586e4171cfe1a1/folder-delete-extension.gif?fm=gif&h=578&q=50&w=942" %}
删除文件夹
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
要创建文件夹，请从文件夹列表中选择 ✚**添加**图标：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5aN4a0qkKkJDJSVAzTy3Ix/8789f8ce5e1c3766f6ae9d6b44e06882/folder-add-desk.png?fm=webp&h=517&q=50&w=741" %}
添加文件夹
{% endembed %}

创建文件夹后，您可以随时通过悬停在 :pencil2:**铅笔**图标上来**重命名或删除**文件夹：

{% embed url="https://bitwarden.com/help/images/manage-items/folder-delete-desktop.png" %}
编辑或删除文件夹
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
要创建文件夹，请点击 **⚙️设置**菜单，点击**文件夹**选项，然后点击/选择 ✚**添加**图标。创建后，您可以从同一菜单中通过点击文件夹来**重命名**文件夹，或使用 **≡**菜单来**删除**文件夹：

{% embed url="https://bitwarden.com/help/images/manage-items/folders-mobile.png" %}
移动端上的文件夹
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
要创建文件夹，请使用命令：

```
bw create folder <foldername>
```

您可以使用 `bw edit <folderId>` 编辑现有文件夹，使用 `bw delete folder <folderId>` 删除文件夹。更多信息，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

{% hint style="info" %}
如果您是组织的成员，**集合**将在筛选器菜单中的文件夹的下方显示。

文件夹和集合之间有相似之处。**文件夹用于组织个人密码库的项目**（可以包含[已共享的项目](../organizations/sharing.md)），并且对您来说是独一无二的，而集合则用于在组织成员之间共享项目。
{% endhint %}

### 嵌套文件夹 <a href="#nested-folders" id="nested-folders"></a>

文件夹可以「嵌套」，以便在密码库中合理地组织它们。嵌套文件夹的深度没有限制，但创建太多层次可能会破坏密码库的界面。

{% hint style="info" %}
在「父」文件夹中进行检索不会将嵌套在其中的文件夹中的项目作为潜在检索结果包括在内。有关更多信息，请参阅[检索密码库](search-your-vault.md)。
{% endhint %}

要创建一个嵌套文件夹，给新的文件夹起一个名字，这个名字需包括「父」文件夹，后面使用一个正斜线 (`/`) 分隔符，例如 `Personal/Email`。

如果没有相应的「父」文件夹名，则该文件夹不会被嵌套，其标题将完整显示。

## 移动项目到文件夹 <a href="#move-items-to-a-folder" id="move-items-to-a-folder"></a>

在密码库中创建文件夹后，可以通过以下几种方式将项目移动到其中：

{% tabs %}
{% tab title="网页密码库" %}
对于网页密码库，可以任选其一：

* 导航到**添加项目**或**编辑项目**界面，从**文件夹**下拉列表中选择您的新文件夹并**保存**您的项目：

{% embed url="https://bitwarden.com/help/images/manage-items/add-to-folder.png" %}
移动项目到文件夹
{% endembed %}

* 导航到**我的密码库**视图，选择要移动的密码库项目，然后使用最上面的 **⚙️**齿轮下拉列表选择 **⮫添加到文件夹**按钮。在移动所选按对话框中，选择要将项目移动到的文件夹：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7zQPzdrcVIbPeX5E8LqTq/781900835d36ecf71db0b47893c41346/2024-07-15_14-16-27.png?_a=DAJAUVWIZAAB" %}
移动项目到文件夹
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
打开要移动的密码库项目，选择**文件夹**下拉列表，然后选择要将项目移动到的文件夹：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6b8EOCtuuHmulnNQNJmWWk/5cf0c1ba3608c5aec3bb26121e0cbab6/folder-move-be.png?fm=webp&h=734&q=50&w=966" %}
移动项目到文件夹
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
打开要移动的密码库项目，选择**文件夹**下拉列表，然后选择要将项目移动到的文件夹：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/63jzyM75IRzhAbw5nNzMHx/29b8ed60015ebf272ce62cb0034ac68e/Screen_Shot_2022-05-18_at_4.00.25_PM.png?_a=DAJAUVWIZAAB" %}
移动项目到文件夹
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
打开要移动的密码库项目，点击**文件夹**下拉菜单，然后选择要将项目移动到的文件夹：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/169hAtd0PhW3BcYlSPy6vn/3fbd101ece93cc272dec77c80bd2d4c1/folder-move-mob.jpeg?fm=webp&h=672&q=50&w=311" %}
移动项目到文件夹
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用 `bw edit` 命令来操作密码库项目 JSON 对象的 `folderId` 属性，如下例所示：

```batch
bw get item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328 | jq '.folderId="3d9cecac-71a2-4637-9341-acf000eedf04"' | bw encode | bw edit item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328
```

{% hint style="success" %}
`edit` 的使用要求：

* 使用带有您要编辑的项目的确切 ID 的 `get` 命令。
* 知道要将其移动到的文件夹的确切 `folderId`。
* 使用 [jq 之类的命令行 JSON 处理器](https://stedolan.github.io/jq/)操作 JSON 对象（特别是 `folderId` 属性）。
* 使用 `encode` 命令对 JSON 对象的更改进行 `encode`。

如果您不熟悉对这些部分的使用，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="success" %}
[组织已与您共享](../organizations/sharing.md)的项目可以添加到您的个人文件夹中，这样做只会影响项目在您的个人密码库中的显示方式（即，将项目添加到文件夹不会授予任何人对该文件夹的访问权限，也不会更改变它是否在他们的密码库中的某个文件夹中）。
{% endhint %}

# 文件夹

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/folders/)
{% endhint %}

文件夹是组织您的个人密码库的结构，可以将登录、支付卡、身份和安全笔记集中在一起。使用文件夹可以方便您查找密码库项目，并且在 Bitwarden App 中，文件夹会按字母顺序排列。可以将任何密码库项目（包括[组织已与您共享的项目](../../organization-members/sharing.md)）添加到文件夹中。

{% hint style="success" %}
当从筛选器菜单中选择**所有密码库**时，添加到某个文件夹的项目仍会出现在您的密码库中，删除文件夹并**不会**删除该文件夹中的项目。删除文件夹是永久性的，删除后，文件夹将无法恢复。
{% endhint %}

## 创建文件夹 <a href="#create-a-folder" id="create-a-folder"></a>

可以从任何 Bitwarden 客户端 App 来创建、重命名和删除文件夹：

{% tabs %}
{% tab title="网页密码库" %}
要创建文件夹，请选择 **➕新增**按钮然后从下拉菜单选择**文件夹**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3BvTWidqL4xWQvFqBSiJIR/d68bc851d44df1b571eed16366159e0c/2024-12-02_13-50-55.png?w=1038&#x26;fm=avif" alt=""><figcaption><p>新增文件夹</p></figcaption></figure></div>

创建后，您可以随时通过选择此文件夹然后单击 :pencil2:**铅笔**图标来重命名或删除文件夹：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1aG4313JkmkBvot45gZvEr/a7dc45d314407131948216acc2b2444d/2024-12-02_16-15-07.png?w=993&#x26;fm=avif" alt=""><figcaption><p>编辑或删除文件夹</p></figcaption></figure></div>
{% endtab %}

{% tab title="浏览器扩展" %}
要创建文件夹，请选择 **➕新增**按钮然后从下拉菜单选择**文件夹**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1aPQBd9bT7uUf20Y1fZwSB/506e7010284c1e0d83b75204bac22eaa/2024-12-02_16-13-10.png?w=1187&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展新增文件夹</p></figcaption></figure></div>

创建后，可以随时从**设置** → **密码库** → **文件夹**菜单中重命名或删除文件夹。
{% endtab %}

{% tab title="桌面端" %}
要创建文件夹，请选择**新增** → **文件夹**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7xia34eJyx1K8Gy8IXajQ7/af2b2ef342350a68b000c405ee698ab4/2026-04-23_09-58-10.png?w=800&#x26;fm=avif" alt=""><figcaption><p>桌面端添加文件夹</p></figcaption></figure></div>

创建文件夹后，您可以随时通过悬停在 :pencil2:**铅笔**图标上来重命名或删除文件夹：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6t2aoywIMdBPMuJktnhEqA/53742fbe25b11095406c40ff6178d6c4/2026-04-23_10-46-29.png?w=800&#x26;fm=avif" alt=""><figcaption><p>桌面端编辑文件夹</p></figcaption></figure></div>
{% endtab %}

{% tab title="移动端" %}
要创建文件夹，请点击 **⚙️设置**菜单，点击**密码库**选项，然后点击**文件夹**选项。点击 **➕添加**图标以添加文件夹。创建后，您可以从同一菜单中通过点击文件夹来重命名文件夹，或使用 **≡**&#x83DC;单来删除文件夹：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6IwzXSJHGmSeU7oIy4z8kZ/95620b58758e50fa0e8e22a65f2bfa15/2025-01-21_15-26-07.png?w=713&#x26;fm=avif" alt=""><figcaption><p>移动端上的文件夹</p></figcaption></figure></div>
{% endtab %}

{% tab title="CLI" %}
要创建文件夹，请使用命令：

```bash
bw create folder <foldername>
```

您可以使用 `bw edit <folderId>` 编辑现有文件夹，使用 `bw delete folder <folderId>` 删除文件夹。更多信息，请参阅 Bitwarden [CLI 文档](../../developer-tools/cli/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

删除文件夹不会删除其中包含的任何密码库项目，也不会删除嵌套在其中的其他文件夹或其内容。

{% hint style="info" %}
如果您是某个组织的成员，在**筛选器**菜单中，集合将显示在文件夹的下方。

文件夹和集合之间有相似之处。**文件夹用于组织个人密码库的项目**（但可以包含[共享的项目](../../organization-members/sharing.md)），仅供您个人使用，而集合则用于在组织成员之间共享。
{% endhint %}

### 嵌套文件夹 <a href="#nested-folders" id="nested-folders"></a>

文件夹可以「嵌套」，以便在密码库中合理地组织它们。嵌套文件夹的层数没有限制，但创建太多层次可能会破坏密码库的界面。

{% hint style="info" %}
在「父」文件夹中进行检索不会将嵌套在其中的文件夹中的项目作为潜在检索结果包括在内。更多信息，请参阅[检索密码库](search-vault.md)。
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5blNMg0hJ9XW3Ts2qPRzF5/7a2bdfb7672c04a1a1fbae1068b8b422/2024-12-02_16-18-48.png?w=932&#x26;fm=avif" alt=""><figcaption><p>嵌套文件夹</p></figcaption></figure></div>

要创建一个嵌套文件夹，给新的文件夹起一个名称，这个名称需包括「父」文件夹，后面使用一个正斜线 (`/`) 分隔符，例如 `Personal/Email`。

如果没有相应的「父」文件夹名称，则该文件夹不会被嵌套，其标题将完整显示。

## 移动项目到文件夹 <a href="#move-items-to-a-folder" id="move-items-to-a-folder"></a>

在密码库中创建文件夹后，可以通过以下几种方式将项目移动到其中：

{% tabs %}
{% tab title="网页密码库" %}
对于网页密码库，可以任选其一：

* 导航到**添加**项目或**编辑**项目界面，从**文件夹**下拉菜单中选择您的新文件夹，然后**保存**您的项目：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4VfciDIbEZZFAG1AXbRf3S/275100f866612da15b4714adea8f1944/2024-12-02_16-20-15.png?w=1205&#x26;fm=avif" alt=""><figcaption><p>移动项目到文件夹</p></figcaption></figure></div>

* 导航到**密码库**视图，选择要移动的项目，然后使用最上面的 **≡**&#x9009;项菜单选择 **💾添加到文件夹**按钮。在移动所选对话框中，选择要将项目移动到的文件夹：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7zQPzdrcVIbPeX5E8LqTq/ce8e8bf7188626093a675eb844d5002a/2024-12-02_16-22-24.png?w=1205&#x26;fm=avif" alt=""><figcaption><p>移动项目到文件夹</p></figcaption></figure></div>
{% endtab %}

{% tab title="浏览器扩展" %}
打开要移动的密码库项目，选择**编辑**按钮，使用**文件夹**下拉菜单选择文件夹，完成后选择**保存**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6b8EOCtuuHmulnNQNJmWWk/f24c97777972b15ee5000e575f2b242c/2024-10-29_11-48-18.png?w=961&#x26;fm=avif" alt=""><figcaption><p>移动项目到文件夹</p></figcaption></figure></div>
{% endtab %}

{% tab title="桌面端" %}
打开要移动的密码库项目，选择**文件夹**下拉菜单，然后选择要将项目移动到的文件夹：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/63jzyM75IRzhAbw5nNzMHx/85db2d1104337e5ebc6e4dd0e8b57f8a/2026-04-23_10-48-31.png?w=800&#x26;fm=avif" alt=""><figcaption><p>移动项目到文件夹</p></figcaption></figure></div>
{% endtab %}

{% tab title="移动端" %}
打开要移动的密码库项目，点击**文件夹**下拉菜单，然后选择要将项目移动到的文件夹：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/169hAtd0PhW3BcYlSPy6vn/2618596e36941b06dabcb766327b664b/2025-01-22_09-44-03.png?w=712&#x26;fm=avif" alt=""><figcaption><p>移动项目到文件夹</p></figcaption></figure></div>
{% endtab %}

{% tab title="CLI" %}
使用 `bw edit` 命令来操作密码库项目 JSON 对象的 `folderId` 属性，如下例所示：

```bash
bw get item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328 | jq '.folderId="3d9cecac-71a2-4637-9341-acf000eedf04"' | bw encode | bw edit item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328
```

{% hint style="success" %}
使用 `edit` 功能需要：

* 使用 `get` 命令并传入要编辑的项目的确切 `id` 。
* 知道要将其移动到的文件夹的确切 `folderId`。
* 使用 [jq 之类的命令行 JSON 处理器](https://stedolan.github.io/jq/)操作 JSON 对象（特别是 `folderId` 属性）。
* 使用 `encode` 命令对 JSON 对象的更改进行编码。

如果您不熟悉对这些部件的使用，请参阅 Bitwarden [CLI 文档](../../developer-tools/cli/password-manager-cli.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="success" %}
[组织已与您共享](../../organization-members/sharing.md)的项目可以添加到您的文件夹中，这样做只会影响该项目在您的个人密码库中的显示方式（即，将项目添加到文件夹不会授予任何人对该文件夹的访问权限，也不会改变它是否在他们的密码库中的某个文件夹中）。
{% endhint %}

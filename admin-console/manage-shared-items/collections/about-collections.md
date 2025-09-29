# 关于集合

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-collections/)
{% endhint %}

集合汇集了从组织内[安全共享](../../../organizations/sharing.md)的登录、笔记、支付卡和身份信息。集合可以由任何组织类型创建和管理。集合是[文件夹](../../../your-vault/folders.md)的组织等效物，但有几个关键的区别：

* 组织可以定义对集合的访问权限，允许用户或[群组](../../manage-members/groups.md)仅能访问他们所需的项目。
* 存储在组织集合中的项目不属于任何个人用户，而是属于组织。
* 组织所拥有的项目**必须**至少被包括在一个集合中。

组织成员可以在**密码库**视图中找到共享项目和个人项目，还可以使用多种方法筛选项目列表，以仅显示组织项目或特定集合中的项目，例如在网页 App 中：

{% embed url="https://bitwarden.com/assets/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?w=1197&fm=avif&q=80" %}
组织密码库
{% endembed %}

## 创建集合 <a href="#create-a-collection" id="create-a-collection"></a>

{% hint style="success" %}
与许多组织管理任务一样，创建集合**只能从网页 App 完成**。
{% endhint %}

具有集合管理[权限](../../manage-members/member-roles.md#permissions)的组织用户可以创建集合。要创建集合：

1、登录到 Bitwarden 网页密码库，选择 ✚**新增**按钮，然后从下拉菜单选择**集合**：

{% embed url="https://bitwarden.com/assets/3rq5lVSQlvNT9gu2M2bCbk/8741dc155e8f2fa83d2caeb69218ce64/2024-12-02_15-35-48.png?w=1038&fm=avif&q=80" %}
创建新的集合
{% endembed %}

2、在**新增集合**选项卡中，为您的集合指定一个**名称**，选择它应属于的**组织**，也可以选择一个集合来[嵌套该集合](about-collections.md#nested-collections)。

{% hint style="success" %}
仅当您使用目录连接器时，**外部 ID** 字段才相关。并且当已配置为使用 [SCIM](../../manage-members/scim/about-scim.md)、目录连接器或 API 时，该字段将在对话框中显示。
{% endhint %}

3、在**访问权限**选项卡中，为现有的成员或[群组](../../manage-members/groups.md)分配访问权限。对于每个选择，分配适当的[权限](../../manage-members/member-roles.md#permissions)级别。作为集合的创建者，您将拥有「可以管理」的权限。

4、选择**保存**以完成集合的创建。

具有管理控制台访问权限的组织成员也可以从那里创建集合。您能否在其中一个或两个位置创建集合、或在两个位置不能创建集合，由组织决定。

### 嵌套集合 <a href="#nested-collections" id="nested-collections"></a>

集合可以被「嵌套」，以方便在您的密码库中逻辑地组织它们：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7EXnVptHEKQkSfKY1FsOmI/d012cd9d0d414528bfbd267d25f04a6f/Screenshot_2024-02-27_at_10.56.41_AM.png?_a=BAJFJtWIB" %}
嵌套的集合
{% endembed %}

嵌套集合**仅用于显示目的**。嵌套的集合不会从他们的「父集合」中继承项目、访问或权限。

要创建嵌套的集合，遵循[上面的步骤](about-collections.md#create-a-collection)，然后从**嵌套在集合下**下拉列表中选择一个父集合。

{% hint style="info" %}
在「父」集合中进行搜索不会将嵌套在其中的集合中的项目包含在潜在的搜索结果当中。有关详细信息，请参阅[检索您的密码库](../../../your-vault/search-your-vault.md)。
{% endhint %}

## 管理集合 <a href="#manage-a-collection" id="manage-a-collection"></a>

您可能需要从一个集合中添加或移除用户/群组，或者完全删除一个集合。这都可以在密码库视图中通过勾选集合，然后使用 **⮟**&#x6309;钮来完成：

{% embed url="https://bitwarden.com/assets/m7O6TwNqNzsOCJNp1caor/914bfbf2192a2cccbe6c3fb58c11a73d/2024-12-02_15-40-10.png?w=1040&fm=avif&q=80" %}
管理集合
{% endembed %}

具有管理控制台访问权限的用户还可以从集合视图使用选项 **≡**&#x83DC;单批量管理集合的访问权限：

{% embed url="https://bitwarden.com/assets/42edJRnvap8xiBpURskIVI/7ff8006517e9bce50dffa4372fcc2911/2024-12-02_15-41-46.png?w=1039&fm=avif&q=80" %}
批量管理集合
{% endembed %}

{% hint style="info" %}
删除一个集合**不会**删除该集合中的密码库项目。删除集合是永久性的，无法恢复。集合中的密码库项目将被移动到**未分配**筛选器中，其可以通过管理控制台访问。
{% endhint %}

### 在集合间移动项目 <a href="#move-an-item-between-collections" id="move-an-item-between-collections"></a>

有权访问组织内多个集合的用户可以将密码库项目从一个集合移动到另一个集合，或将密码库项目添加到多个集合。与[创建集合](about-collections.md#create-a-collection)不同，这可以在任何 Bitwarden App 中完成：

{% tabs %}
{% tab title="网页密码库" %}
要在集合之间移动项目：

1. 选择要移动的项目的 **≡选项**菜单。
2. 从下拉列表中选择**分配到集合**。
3. 勾选将要添加或移动项目到其中的集合，然后选择**保存**。
{% endtab %}

{% tab title="浏览器扩展" %}
要在集合之间移动项目：

1. 选择要移动的项目的 **≡选项**菜单。
2. 从下拉列表中选择**分配到集合**。
3. 勾选将要添加或移动项目到其中的集合，然后选择**保存**。

您还可以直接从项目的**编辑**视图更改项目所属的集合。
{% endtab %}

{% tab title="移动端" %}
要在集合之间移动项目：

1. 打开项目然后点击**编辑**。
2. 点击 **≡选项** 菜单然后点击**集合**。
3. 点击要添加或移动项目到其中的集合，然后点击**保存**。
4. 返回编辑项目界面，再次点击**保存**。
{% endtab %}

{% tab title="桌面端" %}
要在集合之间移动项目：

1. 打开项目然后选择 **✏️编辑**图标。
2. 在编辑项目界面，选择**集合**。
3. 勾选将要添加或移动项目到其中的集合，然后选择**保存**图标。
{% endtab %}

{% tab title="CLI" %}
要从 CLI 更改项目的集合，请使用 `edit` 命令。[了解更多](../../../password-manager/developer-tools/cli/password-manager-cli.md#edit)。
{% endtab %}
{% endtabs %}

### 批量将项目分配到集合 <a href="#collections-ji-he-storing-passkeys-cun-chu-mi-ma-vault-administration-import-export-autofill-bitward" id="collections-ji-he-storing-passkeys-cun-chu-mi-ma-vault-administration-import-export-autofill-bitward"></a>

组织密码库项目可以批量分配给集合：

1、从管理控制台中选择一个或多个密码库项目，然后使用 **≡**&#x83DC;单选择**分配到集合**。

{% embed url="https://bitwarden.com/assets/1u6EPNgAlCnvC9DcmUIosQ/327c0c24e09dce687540499a8eaa5aac/2024-12-02_15-47-21.png?w=1200&fm=avif&q=80" %}
批量分配到集合
{% endembed %}

2、从对话窗口中，使用下拉菜单选择您希望将密码库项目分配到的集合。完成分配方案后，选择**分配**。

### 从所有集合移除某个项目 <a href="#remove-an-item-from-all-collections" id="remove-an-item-from-all-collections"></a>

要从所有集合移除一个项目，必须将该项目从组织中「取消共享」，并将其归还到个人密码库中。属于某个组织的项目不能从某个集合中保留未分配的位置。要从组织中移除某个项目：

1. 通过选择指定项目的 **≡选项**然后选择**克隆**，以将该项目克隆到个人密码库。可以从管理控制台执行此操作，或者所有者、管理员和有「可以管理」权限的用户也可以从密码库视图中执行此操作。
2. 将项目克隆到个人密码库后，返回组织密码库然后从项目的 **≡选项**菜单中选择**删除**。

或者，也可以将项目移到具有更高访问控制限制的不同集合中，从而取消共享。

### 对非管理集合添加访问权限 <a href="#add-access-to-un-managed-collections" id="add-access-to-un-managed-collections"></a>

如果**所有者和管理员可以管理所有集合和项目**选项关闭（[了解更多](collection-management.md#collection-management-settings)），则在集合视图中，没有为其分配具有「[可以管理](../../manage-members/member-roles.md)」权限的成员的任何集合都将显示一个**添加访问权限**徽章：

{% embed url="https://bitwarden.com/assets/1Nqn29nNIkKtb5HfWkfcWK/64c3875f60d3d292837d0655ad3b146c/2024-12-05_09-56-43.png?w=1031&fm=avif&q=80" %}
对非管理集合添加访问权限
{% endembed %}

在为这些集合分配具有「可以管理」权限的成员之前，所有者和管理员可以临时获得这些集合的访问权限。

## 集合设置 <a href="#collections-settings" id="collections-settings"></a>

组织的所有者可以在**设置** → **组织信息**界面上配置集合行为，以适应组织需求。[了解更多](collection-management.md)。

{% hint style="info" %}
企业组织可使用[成员访问权限报告](../../../your-vault/vault-health-reports.md#member-access)查看单个组织成员对集合、群组、项目的访问权限，以及相关权限的概览。
{% endhint %}

## 集合权限 <a href="#collections-permissions" id="collections-permissions"></a>

权限决定了用户可以对特定集合中的项目执行哪些操作。[角色](https://help.ppgg.in/admin-console/user-management/member-roles-and-permissions#member-roles)只能在单个成员的级别上设置，而权限既可以为单个成员设置，也可以为整个群组设置：

{% embed url="https://bitwarden.com/assets/7xXXzsMeryCUtvwwjvqjYr/9a6c7a2916b751acad313f8ddc4ad43e/2025-02-13_10-51-04.png?w=1114&fm=avif&q=80" %}
权限选项
{% endembed %}

{% hint style="info" %}
企业组织可使用[成员访问权限报告](../../../your-vault/vault-health-reports.md#member-access)查看单个组织成员对集合、群组、项目的访问权限，以及相关权限的概览。
{% endhint %}

| 权限        | 描述                                                                                                                              |
| --------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 可以查看      | 用户或群组可以查看集合中的所有项目，包括密码等隐藏字段。                                                                                                    |
| 可以查看，除了密码 | <p>用户或群组可以查看集合中的所有项目，但密码等隐藏字段除外。</p><p>用户仍可通过自动填充使用密码。</p><p>隐藏密码可防被轻易复制​​和粘贴，但不会完全阻止用户访问此信息。请像对待任何共享凭据一样对待隐藏密码。</p>            |
| 可以编辑      | 用户或群组可以添加新项目、将项目分配到集合、从集合中取消项目分配、更改集合分配以及编辑集合中的现有项目，包括密码等隐藏字段。                                                                  |
| 可以编辑，除了密码 | <p>用户或群组可以将新项目添加到集合，以及编辑集合中的现有项目，但密码等隐藏字段除外。</p><p>用户仍可通过自动填充使用密码。</p><p>隐藏密码可防止轻松复制​​和粘贴，但不会完全阻止用户访问此信息。像对待任何共享凭据一样对待隐藏密码。</p> |
| 可以管理      | 用户或群组可以为新的成员或群组分配对集合的访问权限，包括添加具有「可以管理」权限的其他成员，可以删除集合项目，可以删除组织密码库项目，还可以根据需要删除集合。                                                 |

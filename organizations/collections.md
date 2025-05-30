# =集合

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-collections/)
{% endhint %}

集合汇集了从组织内[安全共享](sharing.md)的登录、笔记、支付卡和身份信息。把集合看作是组织 - 等价于用于组织个人密码库的[文件夹](../your-vault/folders.md)，但有几个关键的区别：

* 组织通过将用户或[群组](groups.md)分配给集合来控制对组织所拥有的项目的访问。
* 组织所拥有的项目**必须**至少被包括在一个集合中。

## 创建集合 <a href="#create-a-collection" id="create-a-collection"></a>

{% hint style="success" %}
与许多组织管理任务一样，创建集合**只能从网页密码库完成**。
{% endhint %}

具有集合管理[权限](../admin-console/user-management/member-roles-and-permissions.md#permissions)的组织用户可以创建集合。要创建集合：

1、登录到 Bitwarden 网页密码库，选择 ✚**新增**按钮，然后从下拉菜单选择**集合**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3rq5lVSQlvNT9gu2M2bCbk/9a2bc86276a56c3b215def54187d7e54/Screenshot_2024-02-27_at_10.51.22_AM.png?_a=BAJFJtWIB" %}
创建新的集合
{% endembed %}

2、在**集合信息**选项卡中，为您的集合指定一个**名称**，选择它应属于的组织，也可以选择一个集合来[嵌套该集合](collections.md#nested-collections)。

{% hint style="success" %}
仅当您使用目录连接器时，**外部 ID** 字段才相关。
{% endhint %}

3、在**访问权限**选项卡中，为现有的成员或[群组](groups.md)分配访问权限。对于每个选择，分配适当的[权限](../admin-console/user-management/member-roles-and-permissions.md#permissions)级别。作为集合的创建者，您将拥有「可以管理」的权限。

4、选择**保存**以完成集合的创建。

具有管理控制台访问权限的组织成员也可以从那里创建集合。您能否在其中一个或两个位置创建集合、或在两个位置不能创建集合，由组织决定。

### 嵌套集合 <a href="#nested-collections" id="nested-collections"></a>

集合可以被「嵌套」，以方便在您的密码库中逻辑地组织它们：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7EXnVptHEKQkSfKY1FsOmI/d012cd9d0d414528bfbd267d25f04a6f/Screenshot_2024-02-27_at_10.56.41_AM.png?_a=BAJFJtWIB" %}
嵌套的集合
{% endembed %}

嵌套集合**仅用于显示目的**。嵌套的集合不会从他们的「父集合」中继承项目、访问或权限。

要创建嵌套的集合，遵循[上面的步骤](collections.md#create-a-collection)，然后从**嵌套在集合下**下拉列表中选择一个父集合。

{% hint style="info" %}
在「父」集合中进行搜索不会将嵌套在其中的集合中的项目包含在潜在的搜索结果当中。有关详细信息，请参阅[检索您的密码库](../your-vault/search-your-vault.md)。
{% endhint %}

## 管理集合 <a href="#manage-a-collection" id="manage-a-collection"></a>

你可能需要从一个集合中添加或移除用户/群组，或者完全删除一个集合。这都可以在密码库视图中通过勾选集合，然后使用 **⮟**&#x6309;钮来完成：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/m7O6TwNqNzsOCJNp1caor/522079b1a54e7b3d2db6a6949c7e47a2/Screenshot_2024-02-27_at_11.00.14_AM.png?_a=BAJFJtWIB" %}
管理集合
{% endembed %}

具有管理控制台访问权限的组织成员也可以从那里打开集合来执行此操作。

{% hint style="info" %}
删除一个集合**不会**删除该集合中的密码库项目。当一个集合被删除后，密码库项目将被移动到组织密码库视图中的**未分配**筛选器中。
{% endhint %}

### 在集合间移动项目 <a href="#move-an-item-between-collections" id="move-an-item-between-collections"></a>

有权访问组织内多个集合的用户可以将密码库项目从一个集合移动到另一个集合，或将密码库项目添加到多个集合。与[创建集合](collections.md#create-a-collection)不同，这可以在任何 Bitwarden 应用程序中完成：

{% tabs %}
{% tab title="网页密码库" %}
要在集合之间移动项目：

1. 选择要移动的项目的 **≡选项**菜单。
2. 从下拉列表中选择**集合**。
3. 勾选将要添加或移动项目到其中的集合，然后选择**保存**。
{% endtab %}

{% tab title="浏览器扩展" %}
要在集合之间移动项目：

1. 打开项目然后选择**编辑**。
2. 在编辑项目界面，选择**集合**。
3. 勾选要添加或移动项目的集合，然后选择**保存**。
4. 返回编辑项目界面，再次选择**保存**。
{% endtab %}

{% tab title="移动端" %}
要在集合之间移动项目：

1. 打开项目然后选择**编辑**。
2. 点击 **≡选项** 菜单然后点击**集合**。
3. 点击要添加或移动项目的集合，然后点击**保存**。
4. 返回编辑项目界面，再次点击**保存**。
{% endtab %}

{% tab title="桌面端" %}
要在集合之间移动项目：

1. 打开项目然后选择 **✏️编辑**图标。
2. 在编辑项目界面，选择**集合**。
3. 勾选将要添加或移动项目到其中的集合，然后选择**保存**图标。
{% endtab %}

{% tab title="CLI" %}
要从 CLI 更改项目的集合，请使用 `edit` 命令。[了解更多](../password-manager/developer-tools/password-manager-cli.md#edit)。
{% endtab %}
{% endtabs %}

### 批量将项目分配到集合 <a href="#collections-ji-he-storing-passkeys-cun-chu-mi-ma-vault-administration-import-export-autofill-bitward" id="collections-ji-he-storing-passkeys-cun-chu-mi-ma-vault-administration-import-export-autofill-bitward"></a>

可以批量将组织密码库项目分配给集合：

1、从管理控制台中选择一个或多个密码库项目，然后使用 **≡**&#x83DC;单选择**添加到集合**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1u6EPNgAlCnvC9DcmUIosQ/fa0dc2a311d763d982cd2b448851cbbd/assign_multiple_items_to_colleciton.png?_a=BAJFJtWIB" %}
批量分配到集合
{% endembed %}

2、从对话窗口中，使用下拉菜单选择您希望将密码库项目分配到的集合。完成分配方案后，选择**分配**。

### 从所有集合移除某个项目 <a href="#remove-an-item-from-all-collections" id="remove-an-item-from-all-collections"></a>

### 对非管理集合添加访问权限 <a href="#add-access-to-un-managed-collections" id="add-access-to-un-managed-collections"></a>

## 集合设置 <a href="#collections-settings" id="collections-settings"></a>

组织的所有者可以在**设置** → **组织信息**界面上配置集合行为，以适应组织需求。[了解更多](../admin-console/organization-basics/collection-management.md)。

## 集合权限 <a href="#collections-permissions" id="collections-permissions"></a>

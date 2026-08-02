# 创建集合

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/create-collections/)
{% endhint %}

从 Password Manager 网页 App 或 Admin Console 创建集合。您是否可以创建集合取决于您的角色以及组织的[集合管理设置](collection-settings.md)。

要创建集合：

1、登录到 Bitwarden 网页 App，选择 <i class="fa-plus">:plus:</i>**新增**按钮，然后从下拉菜单选择**集合**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3rq5lVSQlvNT9gu2M2bCbk/8741dc155e8f2fa83d2caeb69218ce64/2024-12-02_15-35-48.png?w=1038&#x26;fm=avif" alt=""><figcaption><p>创建新的集合</p></figcaption></figure></div>

2、在**新增集合**面板中：

* 为您的集合指定一个**名称**
* 选择它应属于的**组织**
* （可选）选择一个集合来嵌套该集合。集合可以被嵌套，以逻辑地组织它们，仅用于显示目的：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7EXnVptHEKQkSfKY1FsOmI/7ffee8ed6f5712cc9fa4419c4eb88b11/Nested_collections_in_filter_column.png?w=250&#x26;fm=avif" alt=""><figcaption><p>筛选器列中的嵌套集合</p></figcaption></figure></div>

3、在**访问权限**选项卡中，[为现有的成员或群组分配访问权限](assign-users-to-collections.md)。对于每个选择，分配适当的[权限](collection-permissions.md)级别。作为集合的创建者，您将拥有「**管理集合**」权限。

4、选择**保存**以完成集合的创建。

{% hint style="success" icon="lightbulb" %}
**外部 ID** (External Id) 字段只有在使用 [Directory Connector](../../manage-members/directory-connector/about-directory-connector.md) 时才相关，使用 [SCIM](../../manage-members/scim/about-scim.md)、Directory Connector 或 API 进行配置时，该字段将在对话框中显示。
{% endhint %}

创建后，您可以通过从**筛选器**中选择该集合来编辑、更改访问权限或删除该集合：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3CBN5Em0nHhMdzbzPWoLJe/0fd30301f94670098de41dd4e0ea5d77/2026-07-07_08-50-35.png?w=847&#x26;fm=avif" alt=""><figcaption><p>删除集合</p></figcaption></figure></div>

删除集合不会删除其中包含的任何密码库项目。但集合本身将被永久删除。<br>

## 下一步 <a href="#next-steps" id="next-steps"></a>

* [进一步了解集合](about-collections.md)。
* [与组织成员共享项目](../../../password-manager/organization-members/sharing.md)。
* [将群组和成员分配到集合](assign-users-to-collections.md)。
* [配置集合权限](collection-permissions.md)。
* [配置集合管理设置](collection-settings.md)。

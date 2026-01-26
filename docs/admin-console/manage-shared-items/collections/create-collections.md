# 创建集合

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/create-collections/)
{% endhint %}

{% hint style="info" %}
只有组织的[集合管理设置](collection-settings.md)允许的用户才能通过 Password Manager 网页 App 创建集合。
{% endhint %}

要创建集合：

1、登录到 Bitwarden 网页 App，选择 ✚**新增**按钮，然后从下拉菜单选择**集合**：

{% embed url="https://bitwarden.com/assets/3rq5lVSQlvNT9gu2M2bCbk/8741dc155e8f2fa83d2caeb69218ce64/2024-12-02_15-35-48.png?w=1038&fm=avif&q=80" %}
创建新的集合
{% endembed %}

{% hint style="success" %}
组织的[所有者、管理员和某些自定义用户](../../manage-members/member-roles.md)也可以直接从**管理控制台**执行此步骤，以跳过此过程中的某些步骤。
{% endhint %}

2、在**新增集合**面板中，为您的集合指定一个**名称**，选择它应属于的**组织**，也可以选择一个集合来嵌套该集合。

{% hint style="info" %}
集合可以被嵌套，以将其逻辑地组织在您的密码库中：

<img src="https://bitwarden.com/assets/7EXnVptHEKQkSfKY1FsOmI/7ffee8ed6f5712cc9fa4419c4eb88b11/Nested_collections_in_filter_column.png?w=250&#x26;fm=avif" alt="" data-size="original">

嵌套集合**仅用于显示目的**。它们不会从其「父」集合中继承项目、访问权限或权限。
{% endhint %}

3、在**访问权限**选项卡中，[为现有的成员或群组分配访问权限](assign-users-to-collections.md)。对于每个选择，分配适当的[权限](collection-permissions.md)级别。作为集合的创建者，您将拥有「**管理集合**」权限。

4、选择**保存**以完成集合的创建。

{% hint style="success" %}
**外部标识** (External Id) 字段只有在使用[目录连接器](../../manage-members/directory-connector/about-directory-connector.md) (Directory Connector) 时才相关，使用 [SCIM](../../manage-members/scim/about-scim.md)、目录连接器或 API 进行配置时，该字段将在对话框中显示。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 从概念层面[了解集合](about-collections.md)。
* 通过新的集合[与组织成员共享项目](../../../password-manager/organization-members/sharing.md)。
* 为新集合[分配群组和成员访问权限](assign-users-to-collections.md)。
* 为集合[配置群组和成员权限](collection-permissions.md)。
* 为组织[配置集合管理设置](collection-settings.md)。

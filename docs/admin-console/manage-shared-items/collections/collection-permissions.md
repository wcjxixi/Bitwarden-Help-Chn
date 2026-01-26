# 集合权限

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/collection-permissions/)
{% endhint %}

集合权限决定了[群组](../../manage-members/groups.md)或成员可以对特定集合中的项目进行哪些操作，比如修改项目，或更改有权访问该集合的人员。

{% hint style="info" %}
这些成员权限共同决定了集合访问权限：

* [成员角色](../../manage-members/member-roles.md)定义了哪些成员可以执行组织级别的操作。
* [集合设置](collection-settings.md)指定哪些成员角色可以**在整个组织中**创建、管理或删除集合。
* [集合权限](collection-permissions.md)控制特定用户或群组可以**在单个集合中**执行哪些操作。
{% endhint %}

## 分配集合权限 <a href="#assign-collection-permissions" id="assign-collection-permissions"></a>

集合权限是在首次将成员或群组[分配给集合](assign-users-to-collections.md)时设置的。基于[成员角色](../../manage-members/member-roles.md)和[集合设置](collection-settings.md)，三种类型的用户可以更新集合权限：

* 集合中具有**管理集合**集合权限的任何成员都可以更改分配给同一集合的群组和成员的权限。
* 被授予**编辑任何集合**权限的[自定义角色](../../manage-members/member-roles.md#custom-role)成员可以更改分配给任何集合的群组和成员的集合权限。
* 如果**所有者和管理员可以管理所有集合和项目**设置为开启，则所有所有者和管理员都可以更改任何集合的集合权限。

要查看或更新集合权限：

1、在您密码库中打开集合。

2、选择集合名称旁边的 **⮟箭头图标**。

3、选择**访问权限**：

{% embed url="https://bitwarden.com/assets/6tRILg5xNTKEkrEKBmYrGZ/7bf2c7425a0ee905821e34e5c42fab7e/Edit_collection_permissions.png?w=1200&fm=avif" %}
编辑集合权限
{% endembed %}

4、从**权限**下拉菜单中，为群组或成员选择一个权限级别。

5、选择**保存**。

{% hint style="success" %}
企业组织可以查看[成员访问报告](../../../password-manager/your-vault/security-tools/vault-health-reports.md#member-access)，以了解成员有权访问哪些集合、他们在每个已分配的集合中的权限级别等。
{% endhint %}

## 权限 <a href="#permissions" id="permissions"></a>

下面的表格列出了每项集合权限允许的操作，以及集合设置或成员角色何时会影响这些权限。默认情况下，用户和群组都拥有**查看项目**权限。

{% hint style="info" %}
[成员角色](../../manage-members/member-roles.md#member-roles)只能在单个成员级别设置，而权限既可以为单个成员设置，也可以为整个群组设置。**在成员级别设置的权限将覆盖在群组级别设置的权限。**
{% endhint %}

| 操作                                                                                                                                         | 查看项目   | 查看项目，隐藏密码 | 编辑项目                                                                                                                                        | 编辑项目，隐藏密码                                                                                                                                   | 管理集合                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------ | --------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| 查看分配的集合中的共享项目                                                                                                                              | **✔︎** | **✔︎**    | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                             |
| 查看分配的集合中的共享项目的[隐藏字段](../../../password-manager/your-vault/vault-items/custom-fields.md)                                                    | **✔︎** | **✘**     | **✔︎**                                                                                                                                      | **✘**                                                                                                                                       | **✔︎**                                                                                                                             |
| <p>可以自动填充共享项目，包括<a href="../../../password-manager/your-vault/vault-items/custom-fields.md">隐藏字段</a><br><br>*隐藏字段受限但不阻止访问。将隐藏密码视为共享凭据。</p> | **✔︎** | **✔︎**    | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                             |
| 将项目添加到分配的集合                                                                                                                                | **✘**  | **✘**     | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                             |
| 将分配的集合中的项目添加到不同的集合                                                                                                                         | **✘**  | **✘**     | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                             |
| 编辑分配的集合中的项目                                                                                                                                | **✘**  | **✘**     | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                                      | **✔︎**                                                                                                                             |
| 编辑分配的集合中的隐藏字段                                                                                                                              | **✘**  | **✘**     | **✔︎**                                                                                                                                      | **✘**                                                                                                                                       | **✔︎**                                                                                                                             |
| 从分配的集合中移除项目                                                                                                                                | **✘**  | **✘**     | **✔︎**                                                                                                                                      | **✘**                                                                                                                                       | **✔︎**                                                                                                                             |
| 从分配的集合中删除项目                                                                                                                                | **✘**  | **✘**     | **✔︎** 如果**限制为具有「管理集合」权限的成员可以删除项目**[设置](collection-settings.md#restrict-item-deletion-to-members-with-the-manage-collection-permissions)已关闭 | **✔︎** 如果**限制为具有「管理集合」权限的成员可以删除项目**[设置](collection-settings.md#restrict-item-deletion-to-members-with-the-manage-collection-permissions)已关闭 | **✔︎**                                                                                                                             |
| 删除分配的集合                                                                                                                                    | **✘**  | **✘**     | **✘**                                                                                                                                       | **✘**                                                                                                                                       | **✔︎** 当**限制为所有者和管理员可以删除集合**[设置](collection-settings.md#restrict-collection-deletion-to-owners-and-admins)打开时，**用户**成员角色无法删除分配的集合。 |
| 管理成员和群组对分配的集合的​​访问权限                                                                                                                       | **✘**  | **✘**     | **✘**                                                                                                                                       | **✘**                                                                                                                                       | **✔︎**                                                                                                                             |
| 从分配的集合导出数据                                                                                                                                 | **✘**  | **✘**     | **✘**                                                                                                                                       | **✘**                                                                                                                                       | **✔︎**                                                                                                                             |

{% hint style="info" %}
以下[成员角色](../../manage-members/member-roles.md)即使没有**管理集合**权限，也可以[导出组织库数据](../../../password-manager/import-and-export/export-vault-data.md)：

* 所有者
* 管理员
* 具有**访问导入/导出**权限的自定义角色
{% endhint %}

{% hint style="danger" %}
**隐藏密码权限**：用户仍然可以通过自动填充来使用密码。虽然隐藏密码可以防止简单的复制和粘贴，但并不能完全阻止用户访问这些信息。请像对待任何共享凭据一样对待隐藏密码。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 从概念层面[了解集合](about-collections.md)。
* 通过新的集合[与组织成员共享项目](../../../password-manager/organization-members/sharing.md)。
* 为新集合[分配群组和成员访问权限](assign-users-to-collections.md)。
* 为集合[配置群组和成员权限](collection-permissions.md)。
* 为组织[配置集合管理设置](collection-settings.md)。

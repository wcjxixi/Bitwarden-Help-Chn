# 将用户分配到集合

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/assign-users-to-collections/)
{% endhint %}

[创建集合](about-collections.md)时，您可以分配现有[群组](../../manage-members/groups.md)或成员的访问权限。您可以随时通过 Password Manager 网页 App 修改谁可以访问某个集合：

1、在网页 App 中，打开集合然后选择 按钮以查看您的选项：

{% embed url="https://bitwarden.com/assets/m7O6TwNqNzsOCJNp1caor/914bfbf2192a2cccbe6c3fb58c11a73d/2024-12-02_15-40-10.png?w=1040&fm=avif&q=80" %}
管理集合
{% endembed %}

2、选择**访问权限**。

3、在集合**访问**视图中，您可以：

* 授与其他[群组](../../manage-members/groups.md)或成员访问权限，包括他们拥有的[权限级别](collection-permissions.md)。
* 更改已可以访问集合的[群组](../../manage-members/groups.md)或成员的[权限级别](collection-permissions.md)。

4、选择保存。

{% hint style="success" %}
**批量管理**：具有管理控制台访问权限的用户可以通过集合视图中的 **≡**&#x83DC;单选项批量管理集合的访问权限：

<img src="https://bitwarden.com/assets/42edJRnvap8xiBpURskIVI/7ff8006517e9bce50dffa4372fcc2911/2024-12-02_15-41-46.png?w=1039&#x26;fm=avif&#x26;q=80" alt="" data-size="original">
{% endhint %}

## 为未管理的集合分配访问权限 <a href="#assign-access-to-un-managed-collections" id="assign-access-to-un-managed-collections"></a>

集合应始终至少有一位被分配的成员拥有[管理集合权限](collection-permissions.md)。在某些情况下，例如管理成员离开您的组织时，集合可能会没有具有该权限级别的成员。

{% hint style="info" %}
以下仅适用于所有者和管理员可以管理所有集合和项目，且集合管理设置关闭的情况。如果您的组织中此设置开启：

* 所有者和管理员可以始终（而非暂时）从**集合**视图修改集合的访问权限。
* 下面描述的**添加访问权限**徽标和选项卡将不会出现。
{% endhint %}

当发生这种情况时，所有者和管理员将通过**集合**视图的**添加访问权限**选项卡暂时获得这些集合的管理能力：

{% embed url="https://bitwarden.com/assets/1Nqn29nNIkKtb5HfWkfcWK/64c3875f60d3d292837d0655ad3b146c/2024-12-05_09-56-43.png?w=1031&fm=avif&q=80" %}
为未管理的集合添加访问权限
{% endembed %}

按照本文前面描述的步骤，所有者和管理员应将新成员分配为具有[管理集合权限](collection-permissions.md)。完成后，所有者和管理员将失去对该集合的管理能力，并且**添加访问权限**标签将被移除。

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 从概念层面[了解集合](about-collections.md)。
* 通过新的集合[与组织成员共享项目](../../../password-manager/vault-basics/organization-members/sharing.md)。
* 为新集合[分配群组和成员访问权限](assign-users-to-collections.md)。
* 为集合[配置群组和成员权限](collection-permissions.md)。
* 为组织[配置集合管理设置](collection-settings.md)。

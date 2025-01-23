# 集合管理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/collection-management/)
{% endhint %}

[集合](../../organizations/collections.md)是一个收集登录、笔记、支付卡和身份信息，以用于在组织内进行安全共享的工具。可以将集合视为等效于组织的文件夹，但有一些关键的区别：

* 组织用户通过将用户或群组分配给集合来控制对组织所拥有的项目的访问权限。
* 组织拥有的项目**必须**至少包含在一个集合中。

## 集合管理设置 <a href="#collection-management-settings" id="collection-management-settings"></a>

{% hint style="success" %}
如果您是自托管，请[在云组织中设置集合管理设置](collection-management.md)，然后[更新自托管服务器的许可证](../../self-hosting/licensing-for-paid-features.md#update-organization-license)以将这些设置转移到您的自托管组织。
{% endhint %}

可以自定义集合管理设置以适应您组织的需求。具体来说，管理控制台的**设置** →  **组织信息**视图中提供了一些选项  ，您可以使用它们来：

{% hint style="info" %}
从 2024 年 03 月 03 日开始，尚未开启[集合管理](collection-management.md)的组织将开始批量迁移到更新的权限结构。如果尚未迁移，您的组织将在接下来的几周内迁移，或者如果您手动启用集合管理。

在迁移期间，所有管理员都会被迁移到具有用户角色的成员，并自动提供新的**可以管理**已分配的集合的权限。他们将保留完全管理这些集合的能力，包括分配新成员或群组访问权限的能力。这也将：

* 将具有包含**编辑已分配的集合**的自定义角色的成员迁移到具有**可以管理**这些集合的权限的用户角色。
* 将具有仅**删除已分配的集合**的自定义角色的成员迁移到对这些集合没有权限的用户角色。
* 弃用**访问所有现有和未来的集合**权限，并授予具有此权限的所有用户**可以管理**所有现有集合的权限。
{% endhint %}

### 所有者和管理员可以管理所有集合和项目 <a href="#owners-and-admins-can-manage-all-collections-and-items" id="owners-and-admins-can-manage-all-collections-and-items"></a>

此选项将决定具有[所有者或管理员角色](../user-management/member-roles-and-permissions.md)的成员是否具有对组织中所有集合以及所属项目的管理权限。

关闭此选项后，所有者或管理员无法自动获取访问或更改权限。所有者和管理员只能具有对他们已直接分配权限的集合的访问权限。

启用此选项后，所有者和管理员将能够从任何集合中添加、编辑、查看或删除密码库项目，从任何集合中添加或删除成员和群组，以及从管理控制台直接删除集合。

{% hint style="success" %}
例如，如果您的 IT 团队需要访问与您的组织关联的所有密码库项目以进行定期审核，则此选项适合您。
{% endhint %}

### 限制为仅所有者和管理员可以创建和删除集合 <a href="#limit-collection-creation-and-deletion-to-owners-and-admins" id="limit-collection-creation-and-deletion-to-owners-and-admins"></a>

此选项将决定具有[用户角色](../user-management/member-roles-and-permissions.md)的组织成员是否具有管理集合的能力。

**关闭**此选项后，用户将可以自由地为自己及其团队创建、管理和删除集合。创建集合的成员将自动获取对该集合的可以管理的权限。因此，他们可以分配新成员或群组访问权限，包括添加具有「[可以管理](../user-management/member-roles-and-permissions.md)」权限的其他成员。

**启用**此选项后，您的所有者和管理员将需要代表您的用户创建组织的集合基础架构，但也可以分配单个用户来管理创建后的集合中的项目和人员。

{% hint style="success" %}
此选项即使**启用，**&#x4EFB;何用户仍然可以被授予「可以管理」集合的权限，以便他们可以管理其创建后的成员和内容。
{% endhint %}

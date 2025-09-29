# =集合设置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/collection-management/)
{% endhint %}

[集合](about-collections.md)是一个收集登录、笔记、支付卡和身份信息，以用于在组织内进行安全共享的工具。可以将集合视为等效于组织的文件夹，但有一些关键的区别：

* 通过将用户或群组分配给集合来控制组织用户对组织所拥有的项目的访问权限。
* 组织拥有的项目**必须**至少包含在一个集合中。

[集合](about-collections.md)管理设置是一套组织范围内的规则，可直接与[成员角色](../../manage-members/member-roles.md)和[集合权限](collection-permissions.md)交互，允许或限制某些用户群的某些操作。这些设置只能由组织所有者在管理控制台的**设置** → **组织信息**视图中设置：

## 设置列表 <a href="#list-of-settings" id="list-of-settings"></a>

### 所有者和管理员可以管理所有集合和项目 <a href="#owners-and-admins-can-manage-all-collections-and-items" id="owners-and-admins-can-manage-all-collections-and-items"></a>

该选项与[所有者和管理员成员角色](../../manage-members/member-roles.md)交互，以确定该用户群是否可以自动访问组织中的所有集合以及所有项目。

| **打开** | <p>开启后，所有者和管理员可获得对组织中所有集合的管理集合权限。</p><p><br>在功能上，这意味着所有者和管理员可以更改或移除任何集合、更改或删除任何集合中的项目、更改或删除分配给任何集合的群组和成员，以及更改分配给任何群组或成员的集合权限。</p> |
| ------ | --------------------------------------------------------------------------------------------------------------------------------- |
| **关闭** |                                                                                                                                   |

**关闭**此选项后，所有者或管理员无法自动获取访问或更改权限。所有者和管理员只能具有对他们已直接分配权限的集合的访问权限。

**关闭**此选项后，对于没有分配具有「[管理集合](../../manage-members/member-roles.md)」权限的成员的任何集合，集合视图中将显示添加访问权限徽章。所有者和管理员将暂时获得对这些集合的访问权限，直到他们为这些集合分配了具有「可以管理」权限的成员。&#x20;

**打开**此选项后，所有者和管理员将可以从管理控制台添加、编辑、查看或删除任何集合中的密码库项目，从任何集合中添加或删除成员和群组，编辑集合信息，以及直接删除集合。

{% hint style="success" %}
例如，如果您的 IT 团队需要访问与您的组织关联的所有密码库项目以进行定期审核，则此选项适合您。
{% endhint %}

### 限制为所有者和管理员可以创建集合 <a href="#limit-collection-creation-to-owners-and-admins" id="limit-collection-creation-to-owners-and-admins"></a>

此选项将决定具有[用户角色](../../manage-members/member-roles.md)的组织成员是否具有管理集合的能力。

**关闭**此选项后，用户将可以自由地为自己及其团队创建集合。创建集合的成员将自动获取对该集合的可以管理的权限。因此，他们可以为新成员或群组分配访问权限，包括添加具有「[管理集合](../../manage-members/member-roles.md)」权限的其他成员。

**打开**此选项后，则需要所有者和管理员来代表您的用户创建组织的集合基础架构，但也可以分配单个用户来管理创建后的集合中的项目和人员。

{% hint style="success" %}
此选项即使**启用，**&#x4EFB;何用户仍然可以被授予「可以管理」集合的权限，以便他们可以管理其创建后的成员和内容。
{% endhint %}

### 限制为所有者和管理员可以删除集合 <a href="#limit-collection-deletion-to-owners-and-admins" id="limit-collection-deletion-to-owners-and-admins"></a>

该选项将决定具有[用户角色](../../manage-members/member-roles.md)的组织成员是否具有删除集合的能力。

**关闭**此选项后，用户可以自由删除集合。

**打开**此选项后，组织所有者和管理员可以删除组织的集合。

### 限制为具有「管理集合」权限的成员可以删除项目 <a href="#limit-item-deletion-to-member-with-the-manage-collection-permissions" id="limit-item-deletion-to-member-with-the-manage-collection-permissions"></a>

此选项将决定拥有**可以编辑**和**可以编辑，隐藏密码**的组织成员是否可以删除集合项目。

**打开**此选项后，只有具有**管理集合**权限的用户才能删除集合项目。

**关闭**该选项后，拥有**可以编辑**和**可以编辑，隐藏密码**权限的用户将可以删除集合项目。

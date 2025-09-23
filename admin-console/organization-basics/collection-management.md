# 集合管理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/collection-management/)
{% endhint %}

[集合](about-collections.md)是一个收集登录、笔记、支付卡和身份信息，以用于在组织内进行安全共享的工具。可以将集合视为等效于组织的文件夹，但有一些关键的区别：

* 通过将用户或群组分配给集合来控制组织用户对组织所拥有的项目的访问权限。
* 组织拥有的项目**必须**至少包含在一个集合中。

## 集合管理设置 <a href="#collection-management-settings" id="collection-management-settings"></a>

集合管理设置可进行自定义，以最大限度地满足您的组织需求。组织所有者可以访问位于管理控制台的**设置** →  **组织信息**视图选项，您可以使用以下这些选项：

{% hint style="info" %}
~~从 2024 年 03 月 03 日开始，尚未开启~~[~~集合管理~~](collection-management.md)~~的组织将开始批量迁移到更新的权限结构。如果尚未迁移，您的组织将在接下来的几周内迁移，或者如果您手动启用集合管理。~~

~~在迁移期间，所有管理员都会被迁移到具有用户角色的成员，并自动提供对已分配的集合的新的**可以管理**权限。他们将保留完全管理这些集合的能力，包括分配新成员或群组访问权限的能力。这也将：~~

* ~~将具有包含**编辑已分配的集合**的自定义角色的成员迁移到对这些集合具有**可以管理**权限的用户角色。~~
* ~~将具有仅**删除已分配的集合**的自定义角色的成员迁移到对这些集合没有权限的用户角色。~~
* ~~弃用**访问所有现有和未来的集合**权限，并授予具有此权限的所有用户对所有现有集合具有**可以管理**权限。~~
{% endhint %}

### 所有者和管理员可以管理所有集合和项目 <a href="#owners-and-admins-can-manage-all-collections-and-items" id="owners-and-admins-can-manage-all-collections-and-items"></a>

此选项将决定具有所有者或管理员角色的成员是否具有对组织中**所有**集合以及所属项目的管理权限。

**关闭**此选项后，所有者或管理员无法自动获取访问或更改权限。所有者和管理员只能具有对他们已直接分配权限的集合的访问权限。

**关闭**此选项后，对于没有分配具有「[管理集合](../user-management/member-roles-and-permissions.md)」权限的成员的任何集合，集合视图中将显示添加访问权限徽章。所有者和管理员将暂时获得对这些集合的访问权限，直到他们为这些集合分配了具有「可以管理」权限的成员。&#x20;

**打开**此选项后，所有者和管理员将可以从管理控制台添加、编辑、查看或删除任何集合中的密码库项目，从任何集合中添加或删除成员和群组，编辑集合信息，以及直接删除集合。

{% hint style="success" %}
例如，如果您的 IT 团队需要访问与您的组织关联的所有密码库项目以进行定期审核，则此选项适合您。
{% endhint %}

### 限制为所有者和管理员可以创建集合 <a href="#limit-collection-creation-to-owners-and-admins" id="limit-collection-creation-to-owners-and-admins"></a>

此选项将决定具有[用户角色](../user-management/member-roles-and-permissions.md)的组织成员是否具有管理集合的能力。

**关闭**此选项后，用户将可以自由地为自己及其团队创建集合。创建集合的成员将自动获取对该集合的可以管理的权限。因此，他们可以为新成员或群组分配访问权限，包括添加具有「[管理集合](../user-management/member-roles-and-permissions.md)」权限的其他成员。

**打开**此选项后，则需要所有者和管理员来代表您的用户创建组织的集合基础架构，但也可以分配单个用户来管理创建后的集合中的项目和人员。

{% hint style="success" %}
此选项即使**启用，**&#x4EFB;何用户仍然可以被授予「可以管理」集合的权限，以便他们可以管理其创建后的成员和内容。
{% endhint %}

### 限制为所有者和管理员可以删除集合 <a href="#limit-collection-deletion-to-owners-and-admins" id="limit-collection-deletion-to-owners-and-admins"></a>

该选项将决定具有[用户角色](../user-management/member-roles-and-permissions.md)的组织成员是否具有删除集合的能力。

**关闭**此选项后，用户可以自由删除集合。

**打开**此选项后，组织所有者和管理员可以删除组织的集合。

### 限制为具有「管理集合」权限的成员可以删除项目 <a href="#limit-item-deletion-to-member-with-the-manage-collection-permissions" id="limit-item-deletion-to-member-with-the-manage-collection-permissions"></a>

此选项将决定拥有**可以编辑**和**可以编辑，隐藏密码**的组织成员是否可以删除集合项目。

**打开**此选项后，只有具有**管理集合**权限的用户才能删除集合项目。

**关闭**该选项后，拥有**可以编辑**和**可以编辑，隐藏密码**权限的用户将可以删除集合项目。

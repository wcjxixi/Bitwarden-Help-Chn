# 集合设置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/collection-management/)
{% endhint %}

[集合](about-collections.md)管理设置是一套组织范围内的规则，可直接与[成员角色](../../manage-members/member-roles.md)和[集合权限](collection-permissions.md)交互，允许或限制某些用户群体执行某些操作。这些设置只能由组织所有者在管理控制台的**设置** → **组织信息**视图中进行设置：

## 设置列表 <a href="#list-of-settings" id="list-of-settings"></a>

### 允许所有者和管理员从管理控制台管理所有集合和项目 <a href="#allow-owners-and-admins-to-manage-all-collections-and-items-from-the-admin-console" id="allow-owners-and-admins-to-manage-all-collections-and-items-from-the-admin-console"></a>

此选项与[所有者和管理员成员角色](../../manage-members/member-roles.md)交互，以确定该用户群体是否可以自动访问组织中的所有集合以及所有项目。

<table data-header-hidden><thead><tr><th width="79.5999755859375"></th><th></th></tr></thead><tbody><tr><td><strong>打开</strong></td><td><p>打开后，所有者和管理员将获得对组织中所有集合的<a href="collection-permissions.md">管理集合</a>权限。</p><p><br>在功能上，这意味着所有者和管理员可以更改或移除任何集合、更改或删除任何集合中的项目、更改或删除分配给任何集合的群组和成员，以及更改分配给任何群组或成员的集合权限。</p></td></tr><tr><td><strong>关闭</strong></td><td><p>关闭后，只有被特别分配了<a href="collection-permissions.md">管理集合</a>权限的成员才能以上述方式管理集合。所有者和管理员只能访问直接分配了权限的集合。这不会阻止所有者和管理员导出所有组织拥有的数据。</p><p></p><p>为防止出现孤立的集合，对于没有成员对其具有<a href="collection-permissions.md">管理集合</a>权限的任何集合，集合视图将显示一个<strong>添加访问权限</strong>徽标。所有者和管理员将<strong>临时</strong>获得对这些集合的访问权限，直到他们分配给某个成员该权限。</p></td></tr></tbody></table>

{% hint style="success" %}
例如，如果您的 IT 团队需要访问与您的组织关联的所有密码库项目以进行定期审核，则此选项适合您。
{% endhint %}

### 限制为所有者和管理员可以创建集合 <a href="#restrict-collection-creation-to-owners-and-admins" id="restrict-collection-creation-to-owners-and-admins"></a>

此选项与[所有者和管理员成员角色](../../manage-members/member-roles.md)交互，以确定是否仅该用户群体具有创建集合的能力。

<table data-header-hidden><thead><tr><th width="79.5999755859375"></th><th></th></tr></thead><tbody><tr><td><strong>打开</strong></td><td>打开后，只有所有者和管理员可以创建集合。这些用户群体将代表您的用户创建您的组织集合结构，但在创建后，他们可以分配个人用户以对为这些集合中的项目和人员进行管理。</td></tr><tr><td><strong>关闭</strong></td><td>关闭后，任何角色的成员都可以为自己和团队创建集合。创建集合的成员将自动获得对该集合的<a href="collection-permissions.md">集合管理</a>权限。</td></tr></tbody></table>

{% hint style="success" %}
此选项即使**打开，**&#x4EFB;何用户仍然可以被授予对集合的**可以管理**权限，以便他们可以管理其创建后的成员和内容。
{% endhint %}

### 限制为所有者和管理员可以删除集合 <a href="#restrict-collection-deletion-to-owners-and-admins" id="restrict-collection-deletion-to-owners-and-admins"></a>

此选项与[所有者和管理员成员角色](../../manage-members/member-roles.md)交互，以确定是否**只有**该用户群体具有删除集合的能力。开启时，此选项还对[管理集合](collection-permissions.md)权限产生下游影响。

<table data-header-hidden><thead><tr><th width="79.5999755859375"></th><th></th></tr></thead><tbody><tr><td><strong>打开</strong></td><td><p>打开后，只有所有者和管理员可以删除集合。</p><p></p><p>功能上，此选项取代了具有<a href="collection-permissions.md">管理集合</a>权限成员原本拥有的删除集合的能力。</p></td></tr><tr><td><strong>关闭</strong></td><td>关闭后，任何角色的成员都可以删除集合，前提是他们拥有对要删除的集合的<a href="collection-permissions.md">管理集合</a>权限。</td></tr></tbody></table>

### 限制为具有「管理集合」权限的成员可以删除项目 <a href="#restrict-item-deletion-to-members-with-the-manage-collection-permissions" id="restrict-item-deletion-to-members-with-the-manage-collection-permissions"></a>

此选项与[管理集合权限](collection-permissions.md)交互，以确定是否仅该用户群体具有删除项目的权限。当关闭时，此选项对[可以编辑权限](collection-permissions.md)也有下游影响。

<table data-header-hidden><thead><tr><th width="79.5999755859375"></th><th></th></tr></thead><tbody><tr><td><strong>打开</strong></td><td>打开后，只有具有管理集合权限的用户才能删除集合项目。</td></tr><tr><td><strong>关闭</strong></td><td>关闭后，拥有<a href="collection-permissions.md">可以编辑</a>和<a href="collection-permissions.md">可以编辑，隐藏密码</a>权限的用户才能删除集合项目。</td></tr></tbody></table>

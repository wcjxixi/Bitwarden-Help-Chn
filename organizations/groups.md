# 群组

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-groups/)
{% endhint %}

## 什么是群组？ <a href="#what-are-groups" id="what-are-groups"></a>

群组用于将个人用户联系在一起，并提供一种可扩展的方式来分配权限，包括对[集合](../admin-console/organization-basics/about-collections.md)的访问和其他[访问控制](../admin-console/user-management/member-roles-and-permissions.md#access-control)。当[入职新用户](user-management.md)时，将他们添加到群组中，他们将自动继承该群组的配置权限。

{% hint style="info" %}
群组适用于[团队和企业组织](organizations.md#types-of-organizations)。
{% endhint %}

### 使用群组 <a href="#using-groups" id="using-groups"></a>

团队和企业组织可以基本用户群组而不是个人用户来指定对[集合](../admin-console/organization-basics/about-collections.md)的访问权限。群组-集合关联为共享资源提供了深层次的访问控制和可扩展性。一种常见的群组-集合方法是创建**按部门的群组**、**按功能的集合**，例如：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1WzkMkukq1i1mueOQP81JC/e6ba38466c2612b64b15344040fea1dd/collections-graphic-2.png?fm=webp&h=304&q=50&w=449" %}
群组-集合的使用
{% endembed %}

其他常见方法包括按**供应商或系统的集合**（即 **Engineering** 群组中的用户被分配到 **AWS Credentials** 集合）和**按地区的群组**（即用户被分配到 **US Employees** 群组或 **UK Employees** 群组）。

## 创建群组 <a href="#create-a-group" id="create-a-group"></a>

组织的[管理员（或更高级别）](../admin-console/user-management/member-roles-and-permissions.md)和[提供商用户](../provider-portal/provider-users.md#provider-user-types)可以创建和管理群组。要创建群组：

1、登录到[网页密码库](https://vault.bitwarden.com/)并打开您的组织。

2、打开**管理**选项卡，然后从左侧菜单中选择**群组**。

3、在群组界面，选择 ✚**新建群组**按钮。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/FefJG4qBRiWkTzsxBKfm6/5562cfa02b046bca4622184938df1340/groups-newgroup.png?fm=webp&h=371&q=50&w=819" %}
新建群组
{% endembed %}

4、为您的群组起个**名称**，并分配所需的[访问控制](../admin-console/user-management/member-roles-and-permissions.md#access-control)。

访问控制用于指定用户可以访问所有项目（即所有集合）或仅限指定的集合，以及是否[隐藏密码或登录为只读](../admin-console/user-management/member-roles-and-permissions.md#granular-access-control)。

{% hint style="success" %}
**外部 ID** 字段仅在您使用[目录连接器](../directory-connector/about-directory-connector.md)时相关。
{% endhint %}

5、选择**保存**以完成群组的创建。

### 分配用户到群组 <a href="#assign-users-to-group-s" id="assign-users-to-group-s"></a>

创建和配置群组后，向其中添加用户：

1、在您的组织密码库中打开**管理**选项卡，并从左侧菜单中选择**人员**。

2、将鼠标悬停在您要添加的用户上，然后使用 **⚙️**齿轮下拉菜单选择**群组**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5gzOInUiL13g0L8z1HbTBk/629e4be8d12aa3e92909ae5252fbd192/org-people-options-updated-overlay.png?fm=webp&h=371&q=50&w=819" %}
人员选项
{% endembed %}

3、勾选要将此用户添加到的群组并**保存**您的选择。

{% hint style="success" %}
您可以从**管理** → **群组**界面，通过使用 ⚙️齿轮下拉菜单选择**用户**，来检查哪些用户属于这一个群组。
{% endhint %}

### 编辑集合分配 <a href="#edit-collections-assignments" id="edit-collections-assignments"></a>

如果您要更改已分配给群组的[集合](../admin-console/organization-basics/about-collections.md)或[访问控制](../admin-console/user-management/member-roles-and-permissions.md#access-control)：

1. 在您的组织密码库中，打开**管理**选项卡并从左侧菜单中选择**群组**。
2. 选择要编辑的群组。
3. 像[最初创建](groups.md#create-a-group)群组时一样配置访问控制设置。

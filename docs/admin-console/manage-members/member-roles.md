# =成员角色

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/user-types-access-control/)
{% endhint %}

成员角色控制着用户的权限，例如配置单点登录 (SSO) 或管理设备审批。您可以在邀请用户时或在之后随时分配[默认角色](member-roles.md#default-roles)或[自定义角色](member-roles.md#custom-roles)。企业组织中的管理员和所有者可以管理角色，并可以创建自定义角色。

## 分配成员角色 <a href="#assign-member-roles" id="assign-member-roles"></a>

在管理控制台中，您可以通过两种方式分配成员角色：

* [邀请新成员](user-management.md#invite)时，选择一个**成员角色**。
* 要更改现有成员的角色，请转到**成员**然后选择该成员的名称。从出现的选项中选择一个**成员角色**：

{% embed url="https://bitwarden.com/assets/73zJ6ZvMNNLU8TyH0Xdhow/a96f23b972fc9e954ac4860d3fb044d6/Edit_member_role.png?w=1200&fm=avif" %}
编辑成员角色
{% endembed %}

## 默认角色 <a href="#default-roles" id="default-roles"></a>

有三种默认的成员角色：所有者、管理员和用户。每种角色被授予不同的权限，用于管理您的组织和访问共享项目。

| 角色  | 概述                                                                                                                                                                                                          |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 所有者 | <p>只有所有者才能访问组织的计费和账单详情。只有当前所有者才能邀请新的所有者或将所有者角色分配给现有成员。</p><p></p><p>为防止<a href="../more/managing-access-when-the-organization-owner-leaves.md">所有者离职时</a>组织订阅中断，我们强烈建议至少指定一位额外的所有者。IT 团队经理或项目经理都是不错的人选。</p> |
| 管理员 | <p>管理员负责管理组织特有的配置，例如 SSO 和企业策略。他们还拥有管理成员的权限，例如邀请新用户和创建用户群组。</p><p></p><p>在为团队选择管理员时，请考虑哪些人将协助在整个组织内配置 Bitwarden，或哪些人需要访问组织报告（例如事件日志或 Access Intelligence）。</p>                                              |
| 用户  | <p>用户可以访问其分配的集合中的共享项目并管理个人密码库项目。基于他们的集合权限，他们可以添加、编辑或删除集合项目。</p><p></p><p>将用户角色分配给需要访问共享密码但不需要管理组织设置、成员或策略的团队成员。这是大多数成员的标准角色。</p>                                                                            |

{% hint style="success" %}
至少要指定一名额外的所有者，以便在当前所有者不可用时保持对计费和订阅详细信息的访问权限。
{% endhint %}

## 默认角色权限 <a href="#default-role-permissions" id="default-role-permissions"></a>



### 项目和集合 <a href="#items-and-collections" id="items-and-collections"></a>



### 成员和活动 <a href="#members-and-activity" id="members-and-activity"></a>



### 组织计费和设置 <a href="#organization-billing-and-settings" id="organization-billing-and-settings"></a>



## 自定义角色 <a href="#custom-roles" id="custom-roles"></a>



默认情况下，自定义角色包含与**用户**成员角色相同的权限。将自定义角色分配给新成员或现有成员时，请检查您想要授予的其他权限：

* 访问事件日志
* 访问导入/导出
* 访问报告
* 管理所有集合
  * 这包括创建、编辑和删除任何集合的能力。
* 创建新的集合
* 删除任何集合
* 编辑任何集合
* 管理群组
* 管理 SSO
* 管理策略
* 管理用户
  * 具有**管理用户**权限的自定义用户只能授予他们已有的权限。例如，仅具有**管理用户**和**访问报告**的自定义用户无法将**管理 SSO** 授予其他人。
* 管理账户恢复（也可管理设备批准请求）
  * 自定义用户可以为已注册账户恢复功能的成员[重置主密码](account-recovery/recover-a-member-account.md)。如果没有额外的**管理用户**权限，**成员**页面只会列出已注册的成员并显示**恢复账户**操作。
  * 此权限还允许自定义用户管理[受信任的设备请求](../login-with-sso/trusted-devices/approve-a-trusted-device.md)。



## 成员角色 <a href="#member-roles" id="member-roles"></a>

角色决定了成员在组织可用工具范围内可以采取的操作，但无法决定[他们可以访问哪些集合](member-roles.md#permissions)。

{% hint style="info" %}
~~从 2024 年 03 月 07 日开始，尚未开启~~[~~集合管理~~](../manage-shared-items/collections/collection-settings.md)~~的组织将开始批量迁移到一个更新了的权限结构。如果尚未迁移，您的组织将在接下来的几周内迁移，或者如果您手动打开集合管理。~~

~~在迁移期间，所有**经理**都会被迁移到具有**用户**角色的成员，并自动提供新的「**可以管理**」已分配的集合的权限。他们将保留完全管理这些馆集合的能力，包括分配新成员或群组访问权限的能力。这也将：~~

* ~~将具有「**编辑已分配的集合**」的自定义角色的成员迁移到具有「**可以管理**」这些集合的权限的用户角色。~~
* ~~将具有仅「**删除已分配的集合**」的自定义角色的成员迁移到对这些集合没有权限的用户角色。~~
* ~~弃用「**访问所有现有和未来集合**」权限，并授予具有此权限的所有用户「**可以管理**」所有现有集合的权限。~~
{% endhint %}


# 成员角色

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/user-types-access-control/)
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

<table><thead><tr><th width="79.60003662109375">角色</th><th>概述</th></tr></thead><tbody><tr><td>所有者</td><td><p>只有所有者才能访问组织的计费和账单详情。只有当前所有者才能邀请新的所有者或将所有者角色分配给现有成员。</p><p></p><p>为防止<a href="../more/managing-access-when-the-organization-owner-leaves.md">所有者离职时</a>组织订阅中断，我们强烈建议至少指定一位额外的所有者。IT 团队经理或项目经理都是不错的人选。</p></td></tr><tr><td>管理员</td><td><p>管理员负责管理组织特有的配置，例如 SSO 和企业策略。他们还拥有管理成员的权限，例如邀请新用户和创建用户群组。</p><p></p><p>在为团队选择管理员时，请考虑哪些人将协助在整个组织内配置 Bitwarden，或哪些人需要访问组织报告（例如事件日志或 Access Intelligence）。</p></td></tr><tr><td>用户</td><td><p>用户可以访问已分配的集合中的共享项目并管理个人密码库项目。基于他们的集合权限，他们可以添加、编辑或删除集合项目。</p><p></p><p>将用户角色分配给需要访问共享密码但不需要管理组织设置、成员或策略的团队成员。这是大多数成员的标准角色。</p></td></tr></tbody></table>

{% hint style="success" %}
至少指定一名额外的所有者，以便在当前所有者不可用时保持对计费和订阅详细信息的访问权限。
{% endhint %}

## 默认角色权限 <a href="#default-role-permissions" id="default-role-permissions"></a>

下面的表格列出了每个成员角色的权限。

### 项目和集合 <a href="#items-and-collections" id="items-and-collections"></a>

虽然每个成员角色都可以将新项目保存到「**我的密码库**」或「[我的项目](../../password-manager/organization-members/my-items.md)」中，但对[集合](../manage-shared-items/collections/about-collections.md)的访问权限由三种相互作用的权限类型决定。

{% hint style="info" %}
这些成员权限共同决定了集合访问权限：

* [成员角色](member-roles.md)定义了哪些成员可以执行组织级别的操作。
* [集合设置](../manage-shared-items/collections/collection-settings.md)指定了哪些成员角色可以**在整个组织中**创建、管理或删除集合。
* [集合权限](../manage-shared-items/collections/collection-permissions.md)控制了特定用户或群组可以**在单个集合中**执行哪些操作。
{% endhint %}

下面的表格列出了每个成员角色默认可以执行的操作，以及集合设置或集合权限何时会影响这些权限。首次设置组织时，所有集合设置均处于关闭状态，受邀请的用户或群组将获得**查看项目**集合权限。

| 可执行的操作                                                                                                                                    | 所有者                                                                                                                                                                                       | 管理员                                                                                                                                                                                       | 用户                                                                                                                                                                                                                                |
| ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 在**我的密码库**或**我的项目**中添加、编辑或移除项目                                                                                                            | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                                                            |
| 创建集合                                                                                                                                      | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                    | **✔︎** 如果关闭了**限制为所有者和管理员可以创建集合**[设置](../manage-shared-items/collections/collection-settings.md#restrict-collection-creation-to-owners-and-admins)                                                                                 |
| 访问已分配的集合中的共享项目                                                                                                                            | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                                                            |
| <p>从已分配的集合中添加、编辑、删除和导出项目<br><br>*成员的<a href="../manage-shared-items/collections/collection-permissions.md">集合权限</a>决定了他们可以在该集合中执行哪些操作</p> | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                                                            |
| 删除已分配的集合                                                                                                                                  | **✔︎** 如果分配了**管理集合**[权限](../manage-shared-items/collections/collection-permissions.md)                                                                                                    | **✔︎** 如果分配了**管理集合**[权限](../manage-shared-items/collections/collection-permissions.md)                                                                                                    | **✔︎** 如果关闭了**限制为所有者和管理员可以删除集合**[设置](../manage-shared-items/collections/collection-settings.md#restrict-collection-deletion-to-owners-and-admins)，并且分配了**管理集合**[权限](../manage-shared-items/collections/collection-permissions.md) |
| 访问和管理组织内的所有集合                                                                                                                             | **✘** 如果关闭了**允许所有者和管理员从管理控制台管理所有集合和项目**[设置](../manage-shared-items/collections/collection-settings.md#allow-owners-and-admins-to-manage-all-collections-and-items-from-the-admin-console) | **✘** 如果关闭了**允许所有者和管理员从管理控制台管理所有集合和项目**[设置](../manage-shared-items/collections/collection-settings.md#allow-owners-and-admins-to-manage-all-collections-and-items-from-the-admin-console) | **✘**                                                                                                                                                                                                                             |
| [导出组织密码库数据](../manage-shared-items/export-organization-items/export-organization-items.md)                                                | **✔︎**                                                                                                                                                                                    | **✔︎**                                                                                                                                                                                    | **✘**                                                                                                                                                                                                                             |
| 管理[集合设置](../manage-shared-items/collections/collection-settings.md)                                                                       | **✔︎**                                                                                                                                                                                    | **✘**                                                                                                                                                                                     | **✘**                                                                                                                                                                                                                             |

### 成员和活动 <a href="#members-and-activity" id="members-and-activity"></a>

所有者和管理员拥有更强的用户管理能力和访问组织级报告的能力。

<table><thead><tr><th width="221.20001220703125">可执行的操作</th><th width="105.39990234375">所有者</th><th width="103.199951171875">管理员</th><th>用户</th></tr></thead><tbody><tr><td><a href="user-management.md#onboard-users">邀请并确认新用户</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td><a href="revoke-remove/temporarily-revoke-access.md">撤销</a>和<a href="revoke-remove/permanently-remove-access.md">移除</a>用户</td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>分配和管理成员角色</td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>创建和删除<a href="groups.md">群组</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>将用户添加到群组</td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>管理<a href="account-recovery/about-account-recovery.md">账户恢复</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>管理<a href="../login-with-sso/trusted-devices/about-trusted-devices.md">受信任设备</a>审批</td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>查看<a href="../../password-manager/your-vault/security-tools/vault-health-reports.md">密码库健康报告</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong> *所有用户均可访问<a href="../../password-manager/your-vault/security-tools/vault-health-reports.md#data-breach-report-individual-vaults-only">数据泄露报告</a></td></tr><tr><td>查看<a href="../oversight-visibility/event-logging/event-logs.md">事件日志</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>查看 <a href="../oversight-visibility/access-intelligence.md">Access Intelligence</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr></tbody></table>

### 组织计费和设置 <a href="#organization-billing-and-settings" id="organization-billing-and-settings"></a>

只有所有者可以访问大多数组织配置设置。

<table><thead><tr><th width="367.5999755859375">可执行的操作</th><th width="123.4000244140625">所有者</th><th width="123.0001220703125">管理员</th><th>用户</th></tr></thead><tbody><tr><td><a href="../../plans-and-pricing/update-your-billing-information.md">管理计费</a>，包括订阅、付款方式和计费历史记录</td><td><strong>✔︎</strong></td><td><strong>✘</strong></td><td><strong>✘</strong></td></tr><tr><td>更改组织名称</td><td><strong>✔︎</strong></td><td><strong>✘</strong></td><td><strong>✘</strong></td></tr><tr><td>管理<a href="../oversight-visibility/enterprise-policies.md">企业策略</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>管理<a href="../oversight-visibility/claimed-domains/claimed-domains.md">声明的域名</a></td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>管理 SSO 配置</td><td><strong>✔︎</strong></td><td><strong>✔︎</strong></td><td><strong>✘</strong></td></tr><tr><td>管理组织两步登录</td><td><strong>✔︎</strong></td><td><strong>✘</strong></td><td><strong>✘</strong> </td></tr><tr><td>管理 <a href="../../password-manager/developer-tools/api/password-manager-apis.md">API</a> 密钥</td><td><strong>✔︎</strong></td><td><strong>✘</strong></td><td><strong>✘</strong></td></tr><tr><td>管理 <a href="scim/about-scim.md">SCIM</a> 配置</td><td><strong>✔︎</strong></td><td><strong>✘</strong></td><td><strong>✘</strong></td></tr></tbody></table>

## 自定义角色 <a href="#custom-roles" id="custom-roles"></a>

企业团队可以根据自身需求构建自定义角色，这非常适合最小权限安全模型。使用自定义角色可以委派组织管理任务或授予用户对特定功能的访问权限。常见的自定义角色包括：

<table><thead><tr><th width="505.99993896484375">用例</th><th>自定义角色权限</th></tr></thead><tbody><tr><td>负责处理登录问题和受信任设备请求<strong>的 IT 服务台</strong></td><td>管理账户恢复</td></tr><tr><td>负责审查安全事件和合规性的<strong>审计员</strong></td><td>访问事件日志和访问报告</td></tr><tr><td>负责跟踪密码健康状况和管理<a href="../manage-shared-items/collections/assign-users-to-collections.md">基于群组的集合访问权限</a>的<strong>团队经理</strong></td><td>访问报告和管理群组</td></tr></tbody></table>

{% hint style="info" %}
如果需要管理订阅信息或更新付款详细信息，请分配**所有者**角色。无法通过自定义角色授予组织计费访问权限。
{% endhint %}

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

{% hint style="info" %}
~~从 2024 年 03 月 07 日开始，尚未开启~~[~~集合管理~~](../manage-shared-items/collections/collection-settings.md)~~的组织将开始批量迁移到一个更新了的权限结构。如果尚未迁移，您的组织将在接下来的几周内迁移，或者如果您手动打开集合管理。~~

~~在迁移期间，所有**经理**都会被迁移到具有**用户**角色的成员，并自动提供新的「**可以管理**」已分配的集合的权限。他们将保留完全管理这些馆集合的能力，包括分配新成员或群组访问权限的能力。这也将：~~

* ~~将具有「**编辑已分配的集合**」的自定义角色的成员迁移到具有「**可以管理**」这些集合的权限的用户角色。~~
* ~~将具有仅「**删除已分配的集合**」的自定义角色的成员迁移到对这些集合没有权限的用户角色。~~
* ~~弃用「**访问所有现有和未来集合**」权限，并授予具有此权限的所有用户「**可以管理**」所有现有集合的权限。~~
{% endhint %}


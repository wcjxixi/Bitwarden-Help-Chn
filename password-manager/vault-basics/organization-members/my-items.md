# 我的项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/my-items/)
{% endhint %}

「**我的项目**」是组织成员存储不需要与其他用户共享但仍然属于组织所有权的项目的位置。要启用「我的项目」功能，组织必须打开[强制数据所有权策略](../../../admin-console/oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)。在用户离职后，项目的控制权将作为继承过程的一部分转移给管理员。

{% hint style="danger" %}
Bitwarden目前仅建议对尚未开始推广的组织启用[强制组织数据所有权策略](../../../admin-console/oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)。对于已建立的组织，Bitwarden 将在未来更新中启用功能，使所有员工凭证统一归入组织密码库，确保所有权与控制权的一致性。
{% endhint %}

管理员激活强制组织数据所有权策略后，「**我的项目**」将被添加到所有组织成员的密码库中。

* 「我的项目」是组织成员存储密码库项目的首选位置。
* 保存在「我的项目」中的项目将始终属于该组织所有。
* 用户无法将「我的项目」分配给其他组织成员，组织内共享的项目也无法移动到用户的「我的项目」中。
* 当组织成员账户被移除或删除后，「我的项目」的管理权将转移给管理员。在[此处](../../../admin-console/manage-members/revoke-remove/permanently-remove-access.md)了解有关继承后「我的项目」的更多信息。
* 保存在「我的项目」中的项目将包含在事件日志报告中。

## 使用「我的项目」 <a href="#use-my-items" id="use-my-items"></a>

「我的项目」与集合一起位于用户的密码库中。「我的项目」存储用户为其个人工作职责而创建的密码库项目，例如不打算与其他组织成员共享的工作必要登录凭据。

{% embed url="https://bitwarden.com/assets/7f20Jamu35GDGYF4sOmsgn/ea93b8e238fc3345cd6db96e4c824779/2025-10-08_11-18-36.png?w=589&fm=avif" %}
「我的项目」位置
{% endembed %}

用户无法创建、重命名或删除「我的项目」。

## 导入到「我的项目」 <a href="#import-to-my-items" id="import-to-my-items"></a>

组织成员可以在任何 Bitwarden 客户端上通过从集合下拉菜单中选择「我的项目」将项目导入到「我的项目」：

{% embed url="https://bitwarden.com/assets/3PO3iAbypeTCIXsWCu2jQ2/846cb1ceb1c696ae549b2df413ff0801/2025-10-08_15-43-37.png?w=1200&fm=avif" %}
导入到「我的项目」
{% endembed %}

在[此处](../../import-and-export/import-data.md)了解有关将项目导入 Bitwarden 的更多信息。

## 保存到「我的项目」 <a href="#save-to-my-items" id="save-to-my-items"></a>

当强制组织所有权策略处于激活状态时，创建新密码库项目的用户将能够将项目保存到「我的项目」。

在创建项目时，「我的项目」将默认出现在「集合」字段中。

{% embed url="https://bitwarden.com/assets/5Z9lis0vkv5MNSWWIy8XHW/476245dcbeec31c62d6c8881f4eb4586/2025-10-08_11-15-05.png?w=1200&fm=avif" %}
为「我的项目」创建新项目
{% endembed %}

## 传输项目 <a href="#transfer-items" id="transfer-items"></a>

启用强制组织所有权策略允许组织管理员在成员继任期间安全地转移成员凭据。来自已移除已删除用户的凭据可以转移到其他集合。在[此处](../../../admin-console/manage-members/revoke-remove/permanently-remove-access.md)了解关于员工离职和继任后转移项目的更多信息。

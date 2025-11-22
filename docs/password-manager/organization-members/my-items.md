# 我的项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/my-items/)
{% endhint %}

**我的项目**是组织成员存储不需要与其他用户共享但仍然属于组织所有权的项目的位置。要启用「我的项目」功能，组织必须启用[强制数据所有权策略](../../admin-console/oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)。在用户离职后，项目的控制权将作为继承过程的一部分转移给管理员。启用策略后，将在每个组织成员的密码库中创建「我的项目」，可以在其中存储和维护组织拥有的项目。

{% hint style="danger" %}
Bitwarden目前仅建议对尚未开始推广的组织启用[强制组织数据所有权策略](../../admin-console/oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)。

如果您的组织在 2025.11.0 版本之前激活了该策略，将为自该版本以后确认的成员创建**我的项目**。现有成员将不会拥有**我的项目**，并且可以继续使用他们的**我的密码库**。未来版本将允许已开始成员入职并使用个人密码库的组织，将所有凭据迁移至组织所有权。
{% endhint %}

管理员激活强制组织数据所有权策略后，**我的项目**将被添加到所有组织成员的密码库中。

* 「我的项目」是组织成员存储密码库项目的首选位置。
* 保存在「我的项目」中的项目将始终属于该组织所有。
* 用户无法将「我的项目」分配给其他组织成员，组织内共享的项目也无法移动到用户的「我的项目」中。
* 当组织成员账户被移除或删除后，「我的项目」的管理权将转移给管理员。在[此处](../../admin-console/manage-members/revoke-remove/permanently-remove-access.md)了解有关继承后「我的项目」的更多信息。
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

{% hint style="info" %}
将文件导入到**我的项目**时，该文件中的任何文件夹引用都不会保留。导入完成后，您可以将导入的数据组织到[文件夹](../your-vault/vault-navigation/folders.md)中。
{% endhint %}

## 保存到「我的项目」 <a href="#save-to-my-items" id="save-to-my-items"></a>

当强制组织所有权策略处于激活状态时，创建新密码库项目的用户将能够将项目保存到「我的项目」。

在创建项目时，「我的项目」将默认出现在**集合**字段中。

{% embed url="https://bitwarden.com/assets/5Z9lis0vkv5MNSWWIy8XHW/476245dcbeec31c62d6c8881f4eb4586/2025-10-08_11-15-05.png?w=1200&fm=avif" %}
为「我的项目」创建新项目
{% endembed %}

## 传输项目 <a href="#transfer-items" id="transfer-items"></a>

启用强制组织所有权策略以允许组织管理员在成员继任期间安全地转移成员凭据。来自已移除或已删除用户的凭据可以转移到其他集合。了解更多有关[员工离职和继任后转移项目](../../admin-console/manage-members/revoke-remove/permanently-remove-access.md)的信息。

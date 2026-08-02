# 我的项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/my-items/)
{% endhint %}

「**我的项目**」是组织成员存储不需要与其他用户共享但仍然属于组织所有权的项目的位置。当组织正在使用[集中化组织所有权](../../admin-console/oversight-visibility/enterprise-policies.md#centralize-organization-ownership)策略，「我的项目」将可供成员使用。

所有者或管理员启用该策略后，「**我的项目**」将被添加到每一位组织成员的密码库中，并且根据组织策略的设置，用户可能会被提示[将项目从「我的密码库」转移到「我的项目」](transfer-ownership.md)。

{% hint style="warning" %}
目前，Bitwarden 仅建议对尚未开始推广的组织启用[强制组织数据所有权策略](../../admin-console/oversight-visibility/enterprise-policies.md#centralize-organization-ownership)。如果您的组织在 [2025.11.0](../../release-notes.md#id-2025.11.0) 版本之前激活了该策略，将为自该版本以后确认的成员创建「**我的项目**」。现有成员将不会拥有「**我的项目**」，并且可以继续使用他们的「**我的密码库**」。
{% endhint %}

「**我的项目**」是每个组织成员存储项目的主要位置，特别是那些不需要与其他成员共享的项目：

* 「**我的项目**」中的项目归组织拥有。这些项目除该成员外，任何人无法直接访问，但会记录[事件日志](../../admin-console/oversight-visibility/event-logging/event-logs.md)和组织[健康报告](../your-vault/security-tools/vault-health-reports.md)。
* 成员不能在[将项目分配到集合](sharing.md)之前，与其它成员共享「**我的项目**」中的项目。
* 通过[集合](../../admin-console/manage-shared-items/collections/about-collections.md)共享给成员的项目无法移动或添加到「**我的项目**」。
* 当成员账户从组织中被[移除](../../admin-console/manage-members/revoke-remove/permanently-remove-access.md)或[删除](../../admin-console/manage-members/revoke-remove/delete-member-accounts.md)后，「**我的项目**」中的项目将转移给组织管理员。

## 定位「我的项目」 <a href="#locating-my-items" id="locating-my-items"></a>

「**我的项目**」可作为密码库筛选器在任何 Bitwarden App 中使用，例如在网页 App 中：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7f20Jamu35GDGYF4sOmsgn/5e525f384e09aef4b22c0c7f7cf993cb/2026-01-27_09-27-31.png?w=1016&#x26;fm=avif" alt=""><figcaption><p>网页 App 中的「我的项目」</p></figcaption></figure></div>

注意在这个截图中，**所有者**列指示了该项目归企业组织拥有。

## 使用「我的项目」 <a href="#use-my-items" id="use-my-items"></a>

### 保存到「我的项目」 <a href="#save-to-my-items" id="save-to-my-items"></a>

对于拥有访问权限的组织成员，「**我的项目**」将是保存新项目的默认集合：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5Z9lis0vkv5MNSWWIy8XHW/f66a9a878e33a1dc4fc038c3d5bfd3ba/2026-01-27_09-30-50.png?w=1017&#x26;fm=avif" alt=""><figcaption><p>保存到「我的项目」</p></figcaption></figure></div>

### 导入到「我的项目」 <a href="#import-to-my-items" id="import-to-my-items"></a>

对于拥有访问权限的组织成员，「**我的项目**」可以被选择作为集合来[导入数据](../import-and-export/import-data.md)到其中：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3PO3iAbypeTCIXsWCu2jQ2/a75eff626ca0bf19a12fca8b5cd50a1c/2026-01-27_09-38-30.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>导入到「我的项目」</p></figcaption></figure></div>

在任何 Bitwarden 客户端上，组织成员可以通过从**集合**下拉菜单中选择「**我的项目**」来[导入项目](../import-and-export/import-data.md)到其中。

{% hint style="info" %}
将文件导入到「**我的项目**」后，该文件中的任何文件夹引用都不会保留。导入完成后，您可以将导入的数据组织到[文件夹](../your-vault/vault-navigation/folders.md)中。
{% endhint %}

## 离职后 <a href="#after-offboarding" id="after-offboarding"></a>

当成员从组织中被[移除](../../admin-console/manage-members/revoke-remove/permanently-remove-access.md)或[删除](../../admin-console/manage-members/revoke-remove/delete-member-accounts.md)后，「**我的项目**」中的项目将自动转移给组织管理员。此后，管理员可以决定如何处理这些项目，例如将它们转移到其他成员使用的集合中，或从组织中清除。了解更多有关[员工离职和继任后转移项目](../../admin-console/manage-members/revoke-remove/permanently-remove-access.md)的信息。

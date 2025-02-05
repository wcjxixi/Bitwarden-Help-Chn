# =组织所有者离职时的访问权限管理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/managing-access-when-the-organization-owner-leaves/)
{% endhint %}

本文针对组织所有者离开公司后的常见问题。如果组织所有权在所有者离开之前没有转移，则以下场景之一可能适用于您的组织。

{% hint style="info" %}
Bitwarden 支持部门无法透露组织当前所有者的身份。这些信息只能直接与组织所有者核实。为方便过程顺畅，我们建议使用所有者注册的电子邮箱地址联系支持部门。
{% endhint %}

## 组织所有者已离职，我可以访问他们的账户凭据 <a href="#the-organization-owner-has-left-and-i-have-access-to-their-account-credentials" id="the-organization-owner-has-left-and-i-have-access-to-their-account-credentials"></a>

如果您可以访问所有者的账户凭据：

1. **访问管理控制台邀请新的所有者或转让所有权**：如果您拥有所有者账户的凭据，则可以直接访问组织的[管理控制台](../organizations-quick-start.md)。这允许您执行许多任务，包括邀请新的所有者、转让所有权和进行必要的更改。
2. **备份组织数据**：确保备份所有重要的组织数据，以防将来数据丢失。[此处](../../import-export/export-vault-data.md#export-an-organization-vault)了解更多信息。
3. **为冗余访问设置管理员或备用的所有者**：确保设置多个管理员或备用的所有者，以保证未来访问的连续性和账户的管理。

## The organization owner has left and I

组织中有任何现任管理员吗？

{% tabs %}
{% tab title="是" %}
* **使用前任所有者的电子邮箱联系支持部门**：使用所有者的电子邮箱联系支持部门。如果设置了管理员，您可以请求支持人员将其中一人提升为所有者角色。如果所有者电子邮箱已不存在，请重新创建收件箱。

{% hint style="danger" %}
只有当请求是来自所有者的电子邮箱地址时，支持部门才会执行管理员晋升。此政策没有例外。
{% endhint %}
{% endtab %}

{% tab title="否" %}
* **尝试恢复账户**：如果没有管理员，则需要手动备份组织数据，并尽快重新开始。要备份组织信息：
  * 使用 Bitwarden 导出功能导出组织密码库数据。这需要用户拥有导入/导出权限的[自定义角色](../user-management/member-roles-and-permissions.md)。
  * 如果没有用户拥有 Bitwarden 导出权限的自定义角色，用户可以手动复制和粘贴数据，以导出组织密码库数据。

{% hint style="danger" %}
如果在您执行备份之前，组织的订阅已失效，请联系支持部门申请临时服务激活，以便导出组织数据。
{% endhint %}
{% endtab %}
{% endtabs %}

## 我必须取消已激活的订阅 <a href="#i-have-to-cancel-an-active-subscription" id="i-have-to-cancel-an-active-subscription"></a>

您是否可以访问所有者或账单联系人的电子邮箱？

{% tabs %}
{% tab title="是" %}
如果您可以访问所有者或计费联系人的电子邮箱地址：

* **使用所有者或计费联系人的电子邮箱地址联系支持部门**：如果订阅仍然有效，您可以使用计费账户关联的电子邮箱联系 Bitwarde 支持部门取消订阅。
  * 您可以使用与组织所有者或计费联系人相关联的电子邮箱联系 Bitwarden 支持部门，取消已激活订阅的续订。授权的计费联系人是接收账单、付款提醒和收据的电子邮箱地址。
{% endtab %}

{% tab title="否" %}
如果您无法访问所有者或计费联系人的电子邮箱地址：

* **联系支持部门并提供默认付款方式的详细信息**：您可以联系支持部门并提供以下付款方式的详细信息，授权删除付款方式：
  * 最后一次付款所用支付卡的有效期。
  * 上次付款所用支付卡的最后 4 位数字。
  * 最后一次付款的日期。
  * 最后一次付款的金额。
{% endtab %}
{% endtabs %}

{% hint style="info" %}
这些信息将帮助 Bitwarden 支持部门确认您的身份并处理取消申请，更多信息请参阅[此处](../../plans-and-pricing/billing-faqs.md#wen-wo-de-zu-zhi-de-ji-fei-dian-zi-you-jian-de-chi-you-zhe-ke-yi-zhi-xing-na-xie-cao-zuo)。
{% endhint %}

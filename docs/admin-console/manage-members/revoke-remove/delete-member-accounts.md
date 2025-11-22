# 删除组织成员账户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/delete-member-accounts/)
{% endhint %}

{% hint style="danger" %}
删除账户是永久性的，无法撤消或恢复。要创建密码库数据的备份以将其存储在安全位置，请[导出密码库数据](../../../password-manager/import-and-export/export-vault-data.md)。
{% endhint %}

根据您组织的设置，您可以删除成员账户。删除账户与移除用户不同。

## 删除账户 <a href="#delete-an-account" id="delete-an-account"></a>

1、如果您有一个[已声明的域名](../../oversight-visibility/claimed-domains/claimed-domains.md)，那么任何账户电子邮箱地址与域名相匹配（例如：`jdoe@mycompany.com`）的用户都可以被组织管理员直接删除，而不是只能[从组织中移除](permanently-remove-access.md)：

{% embed url="https://bitwarden.com/assets/6HUnGTfMstF4IasZcKBfdi/0d2dbd328ba4a006611576e7d91c70df/2025-01-14_10-45-56.png?w=1117&fm=avif&q=80" %}
删除已声明的账户
{% endembed %}

2、如果您是自托管 Bitwarden，已授权的管理员可以从[系统管理员门户](../../../self-hosting/system-administrator-portal.md)中删除该账户。

3、如果该账户拥有一个您公司控制的 `@yourcompany.com` 电子邮箱地址，您可以使用[此流程](../../../plans-and-pricing/delete-an-account-or-organization.md#wu-xu-deng-lu)在 `@yourcompany.com` 收件箱中发起和确认删除。

如果这些方法都不适合您组织的 Bitwarden 配置，请从您的组织中[移除该成员](permanently-remove-access.md)。然后他们可以[删除他们的个人账户](../../../plans-and-pricing/delete-an-account-or-organization.md)。

## 移除账户 <a href="#remove-an-account" id="remove-an-account"></a>

如果您不想永久删除账户数据，请考虑从组织中[移除成员](permanently-remove-access.md)。**移除用户并不会删除他们的 Bitwarden 账户**。他们将失去了对组织及其数据的所有访问权限。如果他们知道主密码，他们仍然可以登录自己的账户并访问任何个人拥有的项目。

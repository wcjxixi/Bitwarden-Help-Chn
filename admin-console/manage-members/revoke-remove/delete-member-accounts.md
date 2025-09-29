# 删除成员账户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/delete-member-accounts/)
{% endhint %}

**从您的组织中移除用户不会删除他们的 Bitwarden 账户**。用户被移除后，对组织及其数据的所有访问权限都将被切断，但如果用户有主密码，他们仍然可以登录自己的账户并访问任何个人拥有的项目。

根据您组织实施的具体情况，您可以使用以下方法之一来删除属于被移除成员的 Bitwarden 账户：

1、如果您有一个[已声明的域名](../../login-with-sso/claimed-domains.md)，那么任何账户电子邮箱地址与域名相匹配（例如：`jdoe@mycompany.com`）的用户都可以被组织管理员直接删除，而不是只能[从组织中移除](permanently-remove-access.md)：

{% embed url="https://bitwarden.com/assets/6HUnGTfMstF4IasZcKBfdi/0d2dbd328ba4a006611576e7d91c70df/2025-01-14_10-45-56.png?w=1117&fm=avif&q=80" %}
删除已声明的账户
{% endembed %}

2、如果您是自托管 Bitwarden，已授权的管理员可以从[系统管理员门户](../../../self-hosting/system-administrator-portal.md)中删除该账户。

3、如果该账户拥有一个您公司控制的 `@yourcompany.com` 电子邮箱地址，您可以使用[此流程](../../../plans-and-pricing/delete-an-account-or-organization.md#wu-xu-deng-lu)在 `@yourcompany.com` 收件箱中发起和确认删除。

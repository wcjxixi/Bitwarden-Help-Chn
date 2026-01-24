# 声明账户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/claimed-accounts/)
{% endhint %}

当企业组织[声明域名](claimed-domains.md)后，具有与该域名匹配的电子邮箱地址（例如 `jdoe@mycompany.com`）的成员账户入职组织时，将被该组织声明。被声明的账户实际上**归组织所有**，因此账户的工作方式会发生一些关键变化。

{% hint style="info" %}
用户必须拥有匹配的域名，**并且**是 Bitwarden 组织的[已确认的成员](../../manage-members/user-management.md#confirm)，才能被视为已声明的账户。声明域名**不会**自动邀请任何用户，因此本身不会增加您的订阅的席位数量。
{% endhint %}

## 删除已声明的账户 <a href="#deletion-of-claimed-accounts" id="deletion-of-claimed-accounts"></a>

组织管理员可以彻底删除已声明的成员账户，而不仅仅是将其从组织中移除。这包括删除该用户的个人密码库（如果该用户拥有个人保密码库的话）。如果您是已声明账户的组织的成员，请务必不要在该账户中存储任何个人凭据。

{% hint style="info" %}
可以从管理控制台的**成员**页面使用 **≡**&#x9009;项菜单删除已声明的账户：

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6HUnGTfMstF4IasZcKBfdi/0d2dbd328ba4a006611576e7d91c70df/2025-01-14_10-45-56.png?_a=DAJCwlWIZAAB" alt="删除已声明的账户" data-size="original">

没有声明账户的组织成员只能从组织中**被移除**。
{% endhint %}

## 限制账户操作权限 <a href="#restricted-access-to-account-actions" id="restricted-access-to-account-actions"></a>

如果您是已声明账户的组织的成员，您将不能：

* 将您的账户电子邮箱地址更改为您的组织未声明的域名（但您仍然可以更改电子邮箱地址的用户名部分）。
* 退出组织。
* 清空您的密码库。
* 删除您的账户。

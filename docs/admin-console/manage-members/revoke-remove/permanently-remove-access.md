# 永久移除访问权限

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/remove-users/)
{% endhint %}

组织管理员、所有者和某些自定义角色成员可以从组织中移除成员。删除成员意味着：

* **会**切断对组织及其数据的所有访问权限。被移除的成员需要重新加入组织才能重新获得访问权限。
* 大多数情况下**不会**删除其 Bitwarden 账户。除非您采取措施删除他们的账户，否则被移除的成员仍能访问他们个人拥有的保险库项目。
* 如果同步过程中删除禁用用户选项被打开，则使用目录同步的组织会自动执行此操作。

要从您的组织移除成员：

1. 在管理控制台中，导航到**成员**视图。
2. 勾选要从组织中移除的成员，然后使用 ≡选项菜单来 **✘移除**：

{% embed url="https://bitwarden.com/assets/5hTYQXah4C90KJcZnWwnqs/83372c5f7e37a9ea27cb14cc78b3b93e/2024-12-03_15-06-01.png?w=1197&fm=avif&q=80" %}
移除成员
{% endembed %}

{% hint style="success" %}
如果您的组织有一个[已声明的域名](../../oversight-visibility/claimed-domains/claimed-domains.md)，如果用户的账户电子邮箱地址与您已声明的域名相匹配，**移除**选项将改为**删除**，并将[直接删除账户](delete-member-accounts.md)，而不是只移除对组织的访问权限：

<img src="https://bitwarden.com/assets/6HUnGTfMstF4IasZcKBfdi/0d2dbd328ba4a006611576e7d91c70df/2025-01-14_10-45-56.png?w=1117&#x26;fm=avif&#x26;q=80" alt="" data-size="original">
{% endhint %}

脱机设备会缓存数据的只读副本，包括组织项目。移除成员后，某些客户端可能会在短时间内保留对只读数据的访问权限。如果预计会有人恶意利用这一点，那么在您将成员从组织中移除时，就应该更新该成员拥有访问权限的凭据。

{% hint style="danger" %}
对于那些使用[受信任设备 SSO](../../login-with-sso/trusted-devices/) 而没有主密码的成员账户：

* [从您的组织中移除它们](permanently-remove-access.md)将切断它们对 Bitwarden 账户的所有访问权限，除非：(i) 您事先使用[账户恢复](../account-recovery/about-account-recovery.md)为他们分配一个主密码；(ii) 他们在被移除前至少使用主密码登录过一次。

除非在用户被从组织中移除**之前**采取了上述步骤，否则用户将无法重新加入您的组织。如果没有采取上述步骤，每个被移除的用户都必须[删除自己的账户](../../../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，然后重新获得邀请才能创建账户和加入组织。

* [撤销对组织的访问权限](temporarily-revoke-access.md)，但不会从组织中移除他们，他们仍然可以登录 Bitwarden 并**仅可以**访问他们的个人密码库。
{% endhint %}

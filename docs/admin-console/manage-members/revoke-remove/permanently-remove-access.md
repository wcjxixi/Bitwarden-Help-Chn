# 永久移除访问权限

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/remove-users/)
{% endhint %}

组织[管理员、所有者和某些自定义角色成员](../member-roles.md)可以从组织中移除成员。移除成员意味着：

* **会切断**对组织及其数据的所有访问权限。被移除的成员需要[重新加入组织](../user-management.md#onboard-users)才能重新获得访问权限。
* 大多数情况下**不会删除**其 Bitwarden 账户。除非您[删除他们的账户](delete-member-accounts.md)，否则被移除的成员仍可以访问他们个人拥有的密码库项目。
* 如果组织使用[目录同步](../directory-connector/about-directory-connector.md)并且**同步过程移除已禁用的用户**选项被打开，则会**自动**执行此操作。

## 从组织移除成员 <a href="#remove-members-from-an-organization" id="remove-members-from-an-organization"></a>

要从您的组织移除成员：

1、在管理控制台中，转到**成员**。

2、选择要移除的用户，然后选择 ≡**选项**图标。

3、选择 **✘移除**：

{% embed url="https://bitwarden.com/assets/5hTYQXah4C90KJcZnWwnqs/83372c5f7e37a9ea27cb14cc78b3b93e/2024-12-03_15-06-01.png?w=1197&fm=avif&q=80" %}
移除成员
{% endembed %}

4、选择**移除成员**进行确认。

{% hint style="success" %}
如果您的组织有一个[已声明的域名](../../oversight-visibility/claimed-domains/claimed-domains.md)，如果用户的账户电子邮箱地址与您已声明的域名相匹配，**移除**选项将改为**删除**，并将[直接删除账户](delete-member-accounts.md)，而不是只移除对组织的访问权限：

<img src="https://bitwarden.com/assets/6HUnGTfMstF4IasZcKBfdi/0d2dbd328ba4a006611576e7d91c70df/2025-01-14_10-45-56.png?w=1117&#x26;fm=avif&#x26;q=80" alt="" data-size="original">
{% endhint %}

脱机设备会缓存数据的只读副本，包括组织项目。移除成员后，某些客户端可能会在短时间内保留对只读数据的访问权限。如果预计会有人恶意利用这一点，那么在您将成员从组织中移除时，就应该更新该成员拥有访问权限的凭据。

{% hint style="danger" %}
对于那些使用[受信任设备 SSO](../../login-with-sso/trusted-devices/) 而没有主密码的成员账户：

* [从您的组织中移除它们](permanently-remove-access.md)将切断它们对 Bitwarden 账户的所有访问权限，除非该账户此前通过[账户恢复](../account-recovery/about-account-recovery.md)功能设置过主密码，且在移除前至少使用该主密码登录过一次。

除非在用户被从组织中移除**之前**采取了上述步骤，否则用户将无法重新加入您的组织。如果没有采取上述步骤，每个被移除的用户都必须[删除自己的账户](../../../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，然后重新获得邀请才能创建账户和加入组织。

* [撤销对组织的访问权限](temporarily-revoke-access.md)，但不会从组织中移除他们，他们仍然可以登录 Bitwarden 并**仅可以**访问他们的个人密码库。
{% endhint %}

## 已移除成员的数据会怎样 <a href="#what-happens-to-removed-members-data" id="what-happens-to-removed-members-data"></a>

所有[集合](../../manage-shared-items/collections/about-collections.md)均归组织所有。当您移除对集合中唯一拥有完整的[管理集合权限](../../manage-shared-items/collections/collection-permissions.md)的成员时，所有者和管理员可以授予现有成员对[该集合的访问权限](../../manage-shared-items/collections/assign-users-to-collections.md#assign-access-to-un-managed-collections)。

「我的密码库」中保存的项目归个人用户所有。当成员从组织中移除时，该用户仍保留其「我的密码库」中的所有项目。

相比之下，使用[强制组织所有权策略](../../oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)的组织在成员移除后仍可访问数据。此策略会将个人拥有的「我的密码库」替换为组织拥有的「[我的项目](../../../password-manager/organization-members/my-items.md)」。当「我的项目」中包含数据的成员被移除时，其「我的项目」会自动转换为以该用户电子邮件地址命名的集合。然后，所有者和管理员可以[分配对该集合的访问权限](../../manage-shared-items/collections/assign-users-to-collections.md#assign-access-to-un-managed-collections)。现有成员获得[管理集合权限](../../manage-shared-items/collections/collection-permissions.md)后，即可像访问标准 Bitwarden 集合一样访问、编辑和重新分配项目。

{% hint style="danger" %}
Bitwarden 目前仅建议对尚未开始推广的组织启用[强制组织数据所有权策略](../../oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)。

如果您的组织在 2025.11.0 版本之前激活了该策略，将为自该版本以后确认的成员创建**我的项目**。现有成员将不会拥有**我的项目**，并且可以继续使用他们的**我的密码库**。未来版本将允许已开始成员入职并使用个人密码库的组织，将所有凭据迁移至组织所有权。
{% endhint %}

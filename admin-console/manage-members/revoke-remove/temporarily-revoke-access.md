# 临时撤销访问权限

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/revoke-users/)
{% endhint %}

组织[管理员和某些自定义角色成员](../member-roles.md)可以通过撤销和恢复来临时管理成员对组织的访问权限。撤销访问权限

* 当某个成员在一段时间内不应该拥有访问权限，但将来需要恢复他们的访问权限时，通常很有用。
* 当用户违反某些[企业策略](../../oversight-visibility/enterprise-policies.md)时，会**自动**执行此操作。
* 对于[使用 SCIM](../scim/about-scim.md) 的企业，当成员在 IdP 中被挂起或停用时，会**自动**执行此操作。

被撤销成员恢复对访问权限不需要他们采取任何步骤重新加入组织，这意味着他们不需要[被重新邀请、接受邀请或被确认](../user-management.md#onboard-users)。

## 撤销访问权限 <a href="#revoke-access" id="revoke-access"></a>

{% hint style="info" %}
只有**所有者**可以撤销和恢复其他**所有者**的访问权限。
{% endhint %}

要撤销成员对组织的访问权限：

1、在管理控制台中，导航到**成员**视图。

2、选择您想要撤销访问权限的成员，然后使用 ≡选项菜单**撤销访问权限**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6hBUggWWvdttF0RUqU8IZ9/389eb47b90742bb3e3844f5105bc643a/2024-12-03_15-06-01.png?_a=DAJCwlWIZAAB" %}
撤销访问权限
{% endembed %}

### 已被撤销的成员的限制 <a href="#restrictions-on-revoked-members" id="restrictions-on-revoked-members"></a>

已撤销访问权限的用户被列在**已撤销**选项卡中，并将：

* 无权限访问任何组织密码库项目、集合等。
* 无法使用 [SSO 登录](../../../login-with-sso/)，或使用[组织 Duo](../../../account/two-step-login/setup-guides/two-step-login-via-duo.md) 进行两步登录。
  * 如果成员[没有主密码](../../login-with-sso/trusted-devices/about-trusted-devices.md)，他们仍然可以使用受信任的设备登录，但**只能访问自己的个人密码库**。
* 不受您的组织[策略](../../oversight-visibility/enterprise-policies.md)的约束。
* 不占用许可证席位。

## 恢复访问权限 <a href="#restore-access" id="restore-access"></a>

{% hint style="info" %}
未遵守某些[策略](../../oversight-visibility/enterprise-policies.md)的成员将无法恢复其访问权限，直到他们采取措施来遵守这些策略。
{% endhint %}

要恢复某个用户的访问权限：

1、在管理控制台中，导航到**成员**视图。

2、打开**已撤销**选项卡。

3、选择您想要恢复访问权限的成员，然后使用 ≡选项菜单**恢复访问权限**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2xe3Vt7l9CCO85RhhmoVJU/47321af7571e298c697a412c650403d6/2024-12-03_15-11-35.png?_a=DAJCwlWIZAAB" %}
恢复访问权限
{% endembed %}

当您恢复某个用户的访问权限时，他们无需再次执行[邀请](../user-management.md#invite) → [接受](../user-management.md#accept) → [确认](../user-management.md#confirm)流程。

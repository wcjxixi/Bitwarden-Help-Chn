# 临时撤销访问权限

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/revoke-users/)
{% endhint %}

撤销成员是指将某人从您的组织中临时移除。之后您可以[恢复其访问权限](temporarily-revoke-access.md#restore-access)或将其[永久移除](permanently-remove-access.md)出您的组织。成员被撤销后，该成员将：

* 无法访问任何组织密码库项目或集合。
* 无法使用您的组织 [SSO](../../login-with-sso/about-sso.md) 登录。

{% hint style="danger" %}
**没有主密码的**成员（例如，在使用[受信任设备](../../login-with-sso/trusted-devices/about-trusted-devices.md)或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md) 的组织中的成员）如果被撤销，其将被完全锁定在他们的账户之外。
{% endhint %}

* 不受您的组织[策略](../../oversight-visibility/enterprise-policies.md)的约束。
* 不占用[订阅席位](../../../plans-and-pricing/manage-subscription-seats-in-your-organization.md)。

## 撤销访问权限 <a href="#revoke-access" id="revoke-access"></a>

撤销成员有好几种方法。当成员违反某些[企业策略](../../oversight-visibility/enterprise-policies.md)，或者成员在用于其组织 [SCIM](../scim/about-scim.md) 的 IdP 中被暂停或停用时，成员将被**自动**撤销。

或者，拥有**管理用户**权限的[所有者、管理员或自定义角色成员](../member-roles.md)可以**手动**撤销用户：

1、在Admin Console 中，选择**成员**。

2、勾选您想要撤销的成员。

3、选择 **≡**&#x9009;项菜单。

4、选择**撤销访问权限**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6hBUggWWvdttF0RUqU8IZ9/389eb47b90742bb3e3844f5105bc643a/2024-12-03_15-06-01.png?w=1197&#x26;fm=avif" alt=""><figcaption><p>撤销访问权限</p></figcaption></figure></div>

5、选择**撤销成员**以确认。

{% hint style="success" %}
要查看哪些成员被撤销，请转至**成员** → **已撤销**。将鼠标悬停在特定用户旁边的 **ⓘ已撤销**图标上，即可了解他们被撤销的原因：

<img src="https://bitwarden.com/assets/4K6UcJtGBxlmEyY0ASKBBs/f4ed8fec1ad67da90dd0f980ef2744a6/Revoke_reason_tooltip.png?w=800&#x26;fm=avif" alt="" data-size="original">

如果显示「Unknown reason」，则说明该成员在[版本 2026.5.0](../../../release-notes.md#id-2026.5.0) 发布之前已被撤销。
{% endhint %}

## 恢复访问权限 <a href="#restore-access" id="restore-access"></a>

{% hint style="info" %}
不符合某些[企业策略](../../oversight-visibility/enterprise-policies.md)的成员，在他们采取措施遵守这些策略之前，将无法恢复到您的组织中。
{% endhint %}

要恢复成员的访问权限：

1、在 Admin Console 中，选择**成员**。

2、选择**已撤销**。

3、勾选您想要将其返回您组织的成员。

4、选择 **≡**&#x9009;项菜单。

5、选择**恢复访问权限**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2xe3Vt7l9CCO85RhhmoVJU/47321af7571e298c697a412c650403d6/2024-12-03_15-11-35.png?w=1197&#x26;fm=avif" alt=""><figcaption><p>恢复访问权限</p></figcaption></figure></div>

6、选择**撤销成员**以确认。

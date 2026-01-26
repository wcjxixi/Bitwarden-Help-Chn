# 声明域名

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/domain-verification/)
{% endhint %}

> **\[译者注]**：从版本 2025.3.0 开始，之前的「域名验证」(Domain verification) 已改名为「声明域名」(Claimed domains)

企业客户可通过有效的 Bitwarden 专属 DNS TXT 记录为其组织声明域名（如 `mycompany.com`）的所有权。声明域名后，您的组织将获得对具有匹配的电子邮箱地址的账户的额外控制权限：

* **阻止未经授权创建账户的策略**：[启用此策略](../enterprise-policies.md#block-account-creation-for-claimed-domains)可阻止具有与域名匹配的电子邮箱账户（例如 `jdoe@mycompany.com`）在组织外部创建 Bitwarden 账户。此策略启用后，具有与域名匹配的电子邮箱账户只能通过受邀加入组织的方式创建 Bitwarden 账户。
* **声明成员账户**：使用与域名匹配的电子邮箱地址（如 `jdoe@mycompany.com`）入职的组织成员账户将自动[被组织声明](claimed-accounts.md)，会限制用户进行某些账户操作，并允许管理员直接[删除账户](../../manage-members/revoke-remove/delete-member-accounts.md)，而不是仅将其从组织中移除。

使用具有与域名匹配的电子邮箱地址（如 `jdoe@mycompany.com`）入职的组织成员账户（称为[已声明账户](claimed-accounts.md)）还将获得以下好处：

* **更便捷的 SSO 流程**：在 SSO 身份验证期间，这些成员将自动跳过要求他们输入 [SSO 标识符](../../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md#get-your-organization-identifier)的步骤。
* **自动验证电子邮箱**：入职时，这些成员的[电子邮箱将自动验证](../../../password-manager/more/password-manager-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)。

## 声明域名 <a href="#claim-a-domain" id="claim-a-domain"></a>

要声明某个域名，Bitwarden 必须确认以下信息：

* 没有其他组织验证该域名。
* 您的组织拥有此域名的所有权。

Bitwarden 将使用 DNS TXT 记录来验证域名声明。该 DNS TXT 记录必须始终保持激活状态并可用，因为 Bitwarden 将不断对其进行检查。

要声明域名，请以[管理员或所有者](../../manage-members/member-roles.md#member-roles)身份完成以下步骤：：

1、登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**设置** → **声明域名**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6WJAs5AXufz8zSiVjEp5aA/8d9f4576f877ce74d6553430801070a9/2025-01-14_09-56-53.png?_a=DAJCwlWIZAAB" %}
声明域名
{% endembed %}

3、在**声明域名**界面，您将看到一个活动域名的列表，以及状态检查和选项。如果您没有活动域名，请选择**新增域名**。

{% hint style="success" %}
如果是首次声明域名，[单一组织策略](../enterprise-policies.md#single-organization)将在声明过程中自动激活。如果您在 2025.3.0 版本发布之前已经声明了一个域名，则无需遵守此要求。
{% endhint %}

4、在弹出窗口中，输入**域名名称**。

{% hint style="info" %}
域名条目的格式中**不要**包含 `https://` 或 `www.`。
{% endhint %}

5、复制 **DNS TXT 记录**然后将其添加到您的域名中。

6、选择**声明域名**。

## 管理您的域名 <a href="#managing-domains" id="managing-domains"></a>

您可以从**声明域名**页面管理和查看您的域名的状态。所有域名均拥有**已声明**或**未声明**状态：

{% embed url="https://bitwarden.com/assets/1sgIhVJzsRce0VyNIvH1ze/9ebaf423a88815e476bf2d81231fbf8e/2025-04-15_09-52-34.png?w=1200&fm=avif" %}
声明域名
{% endembed %}

{% hint style="success" %}
在 Bitwarden 中更新您已声明的域名之前，请使用 `dig` 命令验证您的 TXT 记录是否公开可见：

```bash
dig your.domain.com TXT
```

**如果发现错误的 TXT 记录**，您的 DNS 更改可能需要更长时间才能生效。**如果发现正确的 TXT 记录但声明仍然失败**，则可能是您的 Bitwarden 服务器配置为使用内部 DNS 服务器，而不是进行更新的公共 DNS 服务器。
{% endhint %}

使用域名右侧的 **≡** 菜单以：

* 编辑或删除域名。
* **复制 DNS TXT 记录**以将其提供给您的 DNS 提程序。
* 如果自动声明不成功，可以手动**验证域名**。

{% hint style="danger" %}
Bitwarden 将在前 72 小时内尝试声明域名 3 次。如果该域名在第 3 次尝试后的 7 天内仍未通过验证，该域名将从您的组织中被移除。
{% endhint %}

域名声明活动将记录在组织事件日志中。要查看事件，请在管理控制台中导航到**报告** → **事件日志**。

## 域名被声明后 <a href="#once-your-domain-is-claimed" id="once-your-domain-is-claimed"></a>

您的域名被声明和验证后，您的组织就可以获得以下访问权限：

### 为已声明的域名阻止账户创建 <a href="#block-account-creation-for-claimed-domains" id="block-account-creation-for-claimed-domains"></a>

启用[此策略](../enterprise-policies.md#block-account-creation-for-claimed-domains)可阻止域名匹配的电子邮箱账户（例如 `jdoe@mycompany.com`）在组织外部创建 Bitwarden 账户。启用此策略后，域名匹配的电子邮箱账只能通过受邀加入组织的方式创建 Bitwarden 账户。

### 声明成员账户 <a href="#claimed-member-accounts" id="claimed-member-accounts"></a>

使用与域名匹配的电子邮箱地址（如 `jdoe@mycompany.com`）入职的组织成员账户将自动[被组织声明](claimed-accounts.md)，这会导致账户的工作方式发生一些关键性的变化：

{% hint style="info" %}
用户必须拥有一个匹配的域名**并且**是您的 Bitwarden 组织的[已确认的成员](../../manage-members/user-management.md#confirm)才能被视为已声明的账户。声明域名**不会**自动邀请任何用户，因此本身不会增加您的订阅席位数量。
{% endhint %}

#### 删除组织管理的账户 <a href="#org-managed-account-deletion" id="org-managed-account-deletion"></a>

组织管理员可以直接删除已声明的成员账户，而不是只将他们从组织中移除。所有者和管理员可以在管理控制台的**成员**页面上使用 **≡**&#x83DC;单删除已声明的账户：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6HUnGTfMstF4IasZcKBfdi/0d2dbd328ba4a006611576e7d91c70df/2025-01-14_10-45-56.png?_a=DAJCwlWIZAAB" %}
删除已声明的账户
{% endembed %}

如果组织成员没有已声明的账户，则可将其从组织中**移除**。

{% hint style="info" %}
Directory Connector 和 SCIM 无法删除已声明账户，只有管理员和所有者可以通过网页 App 管理控制台执行此操作。
{% endhint %}

#### 限制账户操作权限 <a href="#restricted-access-to-account-actions" id="restricted-access-to-account-actions"></a>

成员账户用户将受到以下限制：

* 将他们的账户电子邮箱地址更改为其他域名（成员仍可更改电子邮箱地址中的用户名部分）。
* 离开组织。
* 清空他们的密码库。
* 删除他们的账户。


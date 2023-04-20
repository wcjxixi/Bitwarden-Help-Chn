# 用户管理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-users/)
{% endhint %}

## 用户席位 <a href="#user-seats" id="user-seats"></a>

当您[邀请](user-management.md#invite)新用户时，Bitwarden [团队和企业组织](../organization-basics/organizations.md#types-of-organizations)将**自动扩展**用户席位。您可以在扩展时设置[席位限制](user-management.md#set-a-seat-limit)以防止您的席位数超过指定的数量，或根据需要[手动添加席位](user-management.md#manually-add-or-remove-seats)。无论您选择如何添加席位，您都需要[手动移除](user-management.md#manually-add-or-remove-seats)不再使用的席位。

添加和删​移除用户席位将调整您未来的账单总金额。添加席位将立即以调整后的比例向您存档的付款方式扣款，这样**您只需为计费周期的剩余时间（月/年）付费**。移除席位会导致您的下一次收费被调整，已付费席位**未使用的时间将计入您的信用额度**。

{% hint style="info" %}
只有[组织的所有者](user-types-and-access-control.md#user-types)或[提供商服务用户](../../provider-portal/provider-users.md#provider-user-types)可以添加或移除席位，因为这会直接影响计费。
{% endhint %}

### 设置席位限制 <a href="#set-a-seat-limit" id="set-a-seat-limit"></a>

要对您的组织可以扩展到的席位数量设置限制：

1、登录到您的[网页密码库](../../password-manager/getting-started/getting-started-webvault.md)并打开您的组织。

2、打开**设置**选项卡，然后从左侧菜单中选择**订阅**。

3、选中**限制订阅（可选）**复选框：

{% embed url="https://bitwarden.com/help/images/organizations/user-seats.png" %}
设置席位限制
{% endembed %}

4、在**最大席位限制（可选）**输入栏中，指定一个席位限制。

5、选择保存。

{% hint style="info" %}
一旦达到指定的限制后，您将无法邀请新的用户，除非您提高限制。
{% endhint %}

### 手动添加或移除席位 <a href="#manually-add-or-remove-seats" id="manually-add-or-remove-seats"></a>

要对您的组织手动添加或移除席位：

1、登录到您的[网页密码库](../../password-manager/getting-started/getting-started-webvault.md)并打开您的组织。

2、打开**设置**选项卡，然后从左侧菜单中选择**订阅**。

3、在**订阅席位**输入栏中，使用悬停箭头添加或删除席位：

{% embed url="https://bitwarden.com/help/images/organizations/user-seats-add-remove.png" %}
添加或移除用户席位
{% endembed %}

4、选择**保存**。

{% hint style="info" %}
如果您将**订阅席位**增加到超过指定的**最大席位限制**，您还必须增加席位限制，使其等于或大于所需的订阅席位数。
{% endhint %}

## 入职用户 <a href="#onboard-users" id="onboard-users"></a>

为了确保组织的安全，Bitwarden 应用了一个 3 步流程来入职新成员，[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)。

{% hint style="success" %}
使用 [**Bitwarden 目录连接器**](directory-connector/about-directory-connector.md)，团队和企业组织可以同步 Bitwarden 到现有的用户目录，以自动添加或移除新用户。
{% endhint %}

### 邀请 <a href="#invite" id="invite"></a>

{% hint style="success" %}
**对于企业组织**，我们建议在邀请用户之前配置企业策略，以确保加入您的组织时的合规性。
{% endhint %}

要邀请用户到您的组织：

1、登录到您的[网页密码库](https://vault.bitwarden.com/)并打开您的组织。

2、打开**管理**选项卡，然后从左侧菜单中选择**人员**。

3、选择 ✚**邀请用户**按钮。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3RF78KrWI0bdVigd2AZhKN/99a428a8136b310dbce9255b1333786f/org-people-invite.png?fm=webp&h=369&q=50&w=824" %}
邀请用户
{% endembed %}

4、在邀请用户面板上：

* 输入新用户用于接收邀请的**电子邮件**地址。您可以使用逗号分隔电子邮件地址，一次最多添加 20 个用户。
* 选择要应用于新用户的**用户类型**。[用户类型](user-types-and-access-control.md#user-types)将决定这些用户在组织层面拥有哪些权限。
* 选择要应用于新用户的**访问控制**。[访问控制](user-types-and-access-control.md#access-control)将决定这些用户可以访问哪些集合，以及在这些集合中的访问级别。

5、单击**保存**以邀请指定的用户加入您的组织。

{% hint style="info" %}
**邀请将在 5 天后过期**，届时需要重新邀请用户。通过勾选每个用户并使用 **⚙️**齿轮下拉菜单**重新发送邀请**来批量重新邀请用户。

如果您是自托管 Bitwarden，您可以使用[环境变量](../../on-premises-hosting/configure-environment-variables.md)来配置邀请的有效期。
{% endhint %}

### 接受 <a href="#accept" id="accept"></a>

受邀用户将收到一封来自 Bitwarden 的电子邮件，邀请他们加入组织。单击电子邮件中的链接将打开 Bitwarden 客户端邀请窗口。使用现有的 Bitwarden 账号**登录**或**创建账户**来接受邀请：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/4d34e1f7476d2bc27dc4f13c527dec1a/user-accept-updated.png?fm=webp&h=374&q=50&w=439" %}
邀请窗口
{% endembed %}

当您接受邀请时，系统会通知您一旦[确认](user-management.md#confirm)即可访问该组织：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/42WmguoHbM1F15YVUTHCRZ/3208851291aab7fa35ed644424e603fc/96a14f9b-aa0e-460b-95f7-d60535f4de81.png?fm=webp&h=644&q=50&w=1609" %}
已接受邀请
{% endembed %}

### 确认 <a href="#confirm" id="confirm"></a>

要确认已接受加入您组织的邀请：

1、登录到您的[网页密码库](https://vault.bitwarden.com/)并打开您的组织。

2、打开**管理**选项卡，然后从左侧菜单中选择**人员**。

3、选择任何`已接受`的用户，然后使用 **⚙️**齿轮下拉菜单 **✔︎确认所选**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4K01wesgLdxx7TjJVLysOn/a44426fe9afd4df4af7b2312e490fd31/org-people-options-overlay.png?fm=webp&h=458&q=50&w=824" %}
确认已接受的用户
{% endembed %}

4、验证您屏幕上显示的[指纹短语](../../security/account-fingerprint-phrase.md)是否与您的新成员的匹配，指纹短语可以在**设置 → 我的帐户**中找到。

每一个指纹短语对于其帐户都是唯一的，它是确保安全添加用户的最后一层监督。如果它们匹配，请选择**提交**。

## 离职用户 <a href="#offboard-users" id="offboard-users"></a>

要从您的组织移除用户：

1、登录到您的[网页密码库](https://vault.bitwarden.com/)并打开您的组织。

2、打开**管理**选项卡，然后从左侧菜单中选择**人员**。

3、勾选要从组织中移除的用户，然后使用 **⚙️**齿轮下拉列来 **✘移除**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5hTYQXah4C90KJcZnWwnqs/16ea7a088c47990bfe2b43d0085558c4/org-people-bulkremove.png?fm=webp&h=378&q=50&w=819" %}
移除用户
{% endembed %}

{% hint style="success" %}
离线设备会缓存密码库数据的只读副本，包括组织密码库数据。如果您预计有人会对此进行恶意利用，则当您将成员从组织中移除时，应更新该成员拥有访问权限的凭据。
{% endhint %}

### 删除用户账户 <a href="#deleting-user-accounts" id="deleting-user-accounts"></a>

**从您的组织中移除用户不会删除他们的 Bitwarden 帐**户。当用户被移除时，他们将无法再访问组织或任何已共享的项目和集合，但是他们仍然可以使用他们现有的主密码登录 Bitwarden 并访问任何个人密码库项目。

根据实施的具体情况，您可以使用以下方法之一删除已离职用户的 Bitwarden 用户帐户：

1. 如果您是自托管 Bitwarden，已授权的管理员可以从[系统管理员门户](../../on-premises-hosting/system-administrator-portal.md)中删除该帐户。
2. 如果该帐户拥有一个您公司控制的 `@yourcompany.com` 电子邮件地址，您可以使用[无需登录而删除](https://vault.bitwarden.com/#/recover-delete)工具并在 `@yourcompany.com` 收件箱中确认删除。有关更多信息，请参阅[不登录而删除帐户](../../my-account/plans-and-pricing/delete-an-account-or-organization.md#without-logging-in)。

## 撤销访问权限 <a href="#revoke-access" id="revoke-access"></a>

您可以暂时撤销用户对您的组织及其密码库项目的访问权限，而无需完全删移除用户。要撤销访问权限：

1、登录到您的[网页密码库](https://vault.bitwarden.com/)并打开您的组织。

2、在您的组织中，打开**管理**选项卡，然后从左侧菜单中选择**人员**。

3、选择您要为其撤消访问权限的用户，然后使用 **⚙️**齿轮下拉菜单以**撤消访问权限**：

{% embed url="https://bitwarden.com/_gatsby/image/f4ba890f4370f592e01b1beb4e3bc981/c7323bddeacd7502e26856611bf80d62/Screen%20Shot%202022-07-22%20at%209.06.53%20AM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6hBUggWWvdttF0RUqU8IZ9%2Ff43652c728340fcefe8f7667f7d2c2a0%2FScreen_Shot_2022-07-22_at_9.06.53_AM.png&a=w%3D846%26h%3D440%26fm%3Dwebp%26q%3D75&cd=2022-08-04T12%3A55%3A20.353Z" %}
撤消访问权限
{% endembed %}

{% hint style="success" %}
只有**所有者**可以撤销和恢复其他所有者的访问权限。
{% endhint %}

已撤销访问权限的用户位于**已撤销**选项卡中，并将：

* 无权限访问任何组织密码库项目、集合等
* 无法使用 [SSO 登录](../login-with-sso/)，或使用[组织 Duo](../../my-account/two-step-login/setup-guides/two-step-login-via-duo.md) 进行两步登录
* 不受您的组织[策略](../organization-basics/enterprise-policies.md)的约束

{% hint style="info" %}
被撤销的用户仍将占据许可席位，我们正在考虑在未来版本中更改此行为。
{% endhint %}

### 恢复访问权限 <a href="#restore-access" id="restore-access"></a>

要恢复某个用户的访问权限：

1、登录到您的[网页密码库](https://vault.bitwarden.com/)并打开您的组织。

2、在您的组织中，打开**管理**选项卡，然后从左侧菜单中选择**人员**。

3、打开**已撤销**选项卡。

4、选择您要为其恢复访问权限的用户，然后使用 **⚙️**齿轮下拉菜单以**恢复访问权限**：

{% embed url="https://bitwarden.com/_gatsby/image/4cb82a2002af08a027898b4fe217f05e/ed04732ac1f5ce45b7059bb5a0e36778/Screen%20Shot%202022-07-22%20at%209.19.19%20AM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F2xe3Vt7l9CCO85RhhmoVJU%2F181624144f4c42bd0dfd4fa5c34d5f1b%2FScreen_Shot_2022-07-22_at_9.19.19_AM.png&a=w%3D846%26h%3D435%26fm%3Dwebp%26q%3D75&cd=2022-08-04T12%3A55%3A20.345Z" %}
恢复访问权限
{% endembed %}

当您恢复某个用户的访问权限时，他们无需再次执行[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)流程。

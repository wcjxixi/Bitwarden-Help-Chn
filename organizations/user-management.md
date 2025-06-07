# 用户管理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-users/)
{% endhint %}

## 用户席位 <a href="#user-seats" id="user-seats"></a>

「用户席位」指的是一个组织内单个用户的许可证。当您的组织成员占用一个用户席位时，该成员将根据您的特定计划获得访问 Bitwarden 服务的权限。用户席位并非永久绑定给该成员；当成员离开组织时，该用户席位将可供新成员使用。

当您[邀请](user-management.md#invite)新用户时，Bitwarden 云端 [团队和企业组织](organizations.md#types-of-organizations)将**自动扩展**用户席位。您可以在扩展时设置[席位限制](user-management.md#set-a-seat-limit)以防止您的席位数超过指定的数量，或根据需要[手动添加席位](user-management.md#manually-add-or-remove-seats)。无论您选择如何添加席位，您都需要[手动移除](user-management.md#manually-add-or-remove-seats)不再使用的席位。

添加和删​移除用户席位将调整您未来的账单总金额。添加席位将立即以调整后的比例向您存档的付款方式扣款，这样**您只需为计费周期的剩余时间（月/年）付费**。移除席位会导致您的下一次收费被调整，已付费席位**未使用的时间将计入您的信用额度**。

{% hint style="info" %}
只有[组织的所有者](../admin-console/user-management/member-roles-and-permissions.md#user-types)或[提供商服务用户](../provider-portal/provider-users.md#provider-user-types)可以添加或移除席位，因为这会直接影响计费。
{% endhint %}

### 设置席位限制 <a href="#set-a-seat-limit" id="set-a-seat-limit"></a>

{% hint style="info" %}
自托管组织拥有的席位数量将始终与其[对应的云端组织](../self-hosting/plan-for-deployment/self-host-an-organization.md#step-3-start-your-organization)保持一致。您将需要通过云端管理控制台管理您的席位数量，但可以通过设置[计费同步](../self-hosting/licensing.md#zi-dong-tong-bu)，使更改对您的自托管组织生效，而无需重新上传许可证。
{% endhint %}

要对您的组织可以扩展到的席位数量设置限制：

1、登录 Bitwarden 网页 App 然后使用产品切换器打开管理员控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**计费** → **订阅**，然后勾选**限制订阅**复选框：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5DBnJW1y9welOF6hrDKrrh/a700ae21b6f3dd20b702aa9d172ed707/2024-12-03_14-48-25.png?_a=DAJCwlWIZAAB" %}
设置席位限制
{% endembed %}

3、在**席位限制**输入字段中，指定一个席位限制。

4、选择**保存**。

{% hint style="info" %}
一旦达到指定的限制后，您将无法邀请新的用户，除非您提高限制。
{% endhint %}

### 手动添加或移除席位 <a href="#manually-add-or-remove-seats" id="manually-add-or-remove-seats"></a>

{% hint style="info" %}
自托管组织拥有的席位数量将始终与其[对应的云端组织](../self-hosting/plan-for-deployment/self-host-an-organization.md#step-3-start-your-organization)保持一致。您将需要通过云端管理控制台管理您的席位数量，但可以通过设置[计费同步](../self-hosting/licensing.md#zi-dong-tong-bu)，使更改对您的自托管组织生效，而无需重新上传许可证。
{% endhint %}

要对您的组织手动添加或移除席位：

1、登录到 Bitwarden [网页 App](../getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**计费** → **订阅**。

3、在**订阅席位**输入字段中，使用悬停箭头添加或移除席位：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6vCLfjhJz8FOGEeAuQmYQN/f6d0bfe07c1f4db8633e735f42f121fe/2024-12-03_14-49-45.png?_a=DAJCwlWIZAAB" %}
添加或移除席位
{% endembed %}

4、选择**保存**。

{% hint style="info" %}
如果您将**订阅席位**增加到超过指定的**席位限制**，您还必须增加席位限制，使其等于或大于所需的订阅席位数。
{% endhint %}

## 入职用户 <a href="#onboard-users" id="onboard-users"></a>

为了确保组织的安全，Bitwarden 应用了一个 3 步流程来入职新成员，[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)。

{% hint style="success" %}
本文件涵盖了将用户添加到 Bitwarden 组织的手动入职流程，然而 Bitwarden 也提供两种自动配置用户和群组的方法：

* 团队和企业组织可以使用 [Azure AD](../scim/azure-ad-scim-integration.md)、[Okta](../scim/okta-scim-integration.md)、[OneLogin](../scim/onelogin-scim-integration.md) 和 [JumpCloud](../scim/jumpcloud-scim-integration.md) 的 SCIM 集成。
* 团队和企业组织可以使用目录连接器连接到 [Active Directory/LDAP](../directory-connector/sync-with-active-directory-or-ldap.md)、[Azure AD](../admin-console/user-management/directory-connector/sync-with-microsoft-entra-id.md)、[Google Workspace](../directory-connector/sync-with-google-workspace.md)、[Okta](../directory-connector/sync-with-okta.md) 和 [OneLogin](../directory-connector/sync-with-onelogin.md)。
{% endhint %}

### 邀请 <a href="#invite" id="invite"></a>

{% hint style="success" %}
**对于企业组织**，我们建议在邀请用户之前配置企业策略，以确保加入您的组织时的合规性。
{% endhint %}

要邀请用户加入您的组织：

1、登录到 Bitwarden [网页 App](../getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**成员**，然后选择 ✚**邀请用户**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7AJjR4oqEnCH3A89YYoWpH/0d8004ac55a7ce2dfb3525be56885e66/2024-12-03_14-02-20.png?_a=DAJCwlWIZAAB" %}
邀请成员加入组织
{% endembed %}

3、在邀请用户面板上：

* 输入新用户用于接收邀请的**电子邮箱**地址。您可以使用逗号分隔电子邮件地址，一次最多添加 20 个用户。
* 选择要应用于新用户的**成员角色**。[成员角色](../admin-console/user-management/member-roles-and-permissions.md#member-roles)决定了这些用户在组织层面拥有哪些权限。
* 在群组标签页中，选择要将此用户添加到哪些[群组](groups.md)中。
* 在集合标签页中，选择要为此用户授予访问权限的集合以及他们应拥有的每个集合的[权限](../admin-console/user-management/member-roles-and-permissions.md#permissions)。

4、点击**保存**以邀请指定的用户加入您的组织。

{% hint style="info" %}
**邀请将在 5 天后过期**，届时需要重新邀请用户。通过勾选每个用户并使用 ≡选项菜单**重新发送邀请**来批量重新邀请用户。

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1yj3MLJDTr7zOn5TwP0FGJ/3f09a294f42a4bc8772369648afd450d/2024-12-03_15-03-31.png?_a=DAJCwlWIZAAB" alt="" data-size="original">

如果您是自托管 Bitwarden，您可以使用[环境变量](../self-hosting/deploy-and-configure/configuration-options/environment-variables.md)来配置邀请的有效期。
{% endhint %}

### 接受 <a href="#accept" id="accept"></a>

受邀用户将收到一封来自 Bitwarden 的电子邮件，邀请他们加入组织。单击电子邮件中的链接将打开 Bitwarden 网页 App，用户可以在其中登录或创建账户以接受邀请：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/58e2ece3acfe37eaffa4bc55611eb414/Screen_Shot_2023-04-28_at_10.40.35_AM.png?_a=DAJCwlWIZAAB" %}
邀请加入
{% endembed %}

您必须**完全登录到 Bitwarden 网页 App** 以接受邀请。接受邀请后，您将收到通知，[确认](user-management.md#confirm)后即可访问组织。此外，组织成员在接受邀请时，其[电子邮件将自动验证](../your-vault/general-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)。

### 确认 <a href="#confirm" id="confirm"></a>

{% hint style="success" %}
[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)，这 3 步流程旨在通过保持端到端加密来简化组织与用户之间的安全共享。[了解更多](../security/bitwarden-security-whitepaper.md#sharing-data-between-users)。
{% endhint %}

要确认已接受加入您组织的邀请：

1、登录到 Bitwarden [网页 App](../getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**成员**。

3、选择任何`已接受`的用户，然后使用 ≡选项菜单 **✔︎确认所选**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5eRDRAooRSGqRWJYZB5fgz/95422412e2a27069ca903f4a6ec1a8a7/2024-12-03_14-04-59.png?_a=DAJCwlWIZAAB" %}
确认成员加入组织
{% endembed %}

4、验证您屏幕上显示的[指纹短语](../security/encryption/account-fingerprint-phrase.md)是否与您的新成员的匹配，指纹短语可以在**设置 → 我的帐户**中找到。



<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sWPBv5GFAyMcULNxfCCJG/b3115a77e0d8d8d48fcc1f9e24e42d70/fingerprint-phrase.png?_a=DAJCwlWIZAAB" alt=""><figcaption><p>示例指纹短语</p></figcaption></figure>

每一个指纹短语对于其账户都是唯一的，它是确保安全添加用户的最后一层监督。如果它们匹配，请选择**提交**。

## 离职用户 <a href="#offboard-users" id="offboard-users"></a>

{% hint style="danger" %}
对于那些使用[受信任设备 SSO](../admin-console/login-with-sso/trusted-devices/) 而没有主密码的账户，[从您的组织中移除它们](user-management.md#offboard-users)将切它们断对的 Bitwarden 账户的所有访问权限，除非：

1. 您事先使用[账户恢复](admin-password-reset.md)为他们分配一个主密码。
2. 用户在账户恢复后至少登录一次，以完全完成账户恢复流程。

此外，除非在用户被从组织中移除之前采取上述步骤，否则用户将无法重新加入您的组织。在这种情况下，用户将需要[删除他们的账户](../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，并收到一份新的邀请以创建账户并加入您的组织。

撤销对组织的访问权限，但不会从组织中移除他们，他们仍然可以登录 Bitwarden 并**仅可以**访问他们个人密码库。
{% endhint %}

要从您的组织移除用户：

1、登录到 Bitwarden [网页 App](../getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**成员**。

2、打开**管理**选项卡，然后从左侧菜单中选择**人员**。

3、勾选要从组织中移除的用户，然后使用 ≡选项菜单来 **✘移除**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5hTYQXah4C90KJcZnWwnqs/83372c5f7e37a9ea27cb14cc78b3b93e/2024-12-03_15-06-01.png?_a=DAJCwlWIZAAB" %}
移除成员
{% endembed %}

{% hint style="success" %}
离线设备会缓存密码库数据的只读副本，包括组织密码库数据。如果您预计有人会对此进行恶意利用，则当您将成员从组织中移除时，应更新该成员拥有访问权限的凭据。
{% endhint %}

### 删除用户账户 <a href="#deleting-user-accounts" id="deleting-user-accounts"></a>

**从您的组织中移除用户不会删除他们的 Bitwarden 帐**户。当用户被移除时，他们将无法再访问组织或任何已共享的项目和集合，但是他们仍然可以使用他们现有的主密码登录 Bitwarden 并访问任何个人密码库项目。

根据实施的具体情况，您可以使用以下方法之一删除已离职用户的 Bitwarden 用户帐户：

1. 如果您是自托管 Bitwarden，已授权的管理员可以从[系统管理员门户](../self-hosting/system-administrator-portal.md)中删除该帐户。
2. 如果该账户拥有一个您公司控制的 `@yourcompany.com` 电子邮箱地址，您可以使用[无需登录而删除](https://vault.bitwarden.com/#/recover-delete)工具并在 `@yourcompany.com` 收件箱中确认删除。有关更多信息，请参阅[删除账户或组织](../plans-and-pricing/delete-an-account-or-organization.md)。

## 撤销访问权限 <a href="#revoke-access" id="revoke-access"></a>

{% hint style="success" %}
如果您的组织已启用 [SCIM 集成](../scim/about-scim.md)，当用户在源目录中被挂起或停用时，用户对组织的访问权限将自动撤销。
{% endhint %}

{% hint style="danger" %}
对于那些使用[受信任设备 SSO](../admin-console/login-with-sso/trusted-devices/) 而没有主密码的账户，[从您的组织中移除它们](user-management.md#offboard-users)将切它们断对的 Bitwarden 账户的所有访问权限，除非：

1. 您事先使用[账户恢复](admin-password-reset.md)为他们分配一个主密码。
2. 用户在账户恢复后至少登录一次，以完全完成账户恢复流程。

此外，除非在用户被从组织中移除之前采取上述步骤，否则用户将无法重新加入您的组织。在这种情况下，用户将需要[删除他们的账户](../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，并收到一份新的邀请以创建账户并加入您的组织。

撤销对组织的访问权限，但不会从组织中移除他们，他们仍然可以登录 Bitwarden 并**仅可以**访问他们个人密码库。
{% endhint %}

您可以暂时撤销用户对您的组织及组织密码库项目的访问权限，而无需完全删移除用户。要撤销访问权限：

1、在管理控制台中，导航到**成员**。

2、选择您想要撤销访问权限的成员，然后使用 ≡选项菜单**撤销访问权限**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6hBUggWWvdttF0RUqU8IZ9/389eb47b90742bb3e3844f5105bc643a/2024-12-03_15-06-01.png?_a=DAJCwlWIZAAB" %}
撤销访问权限
{% endembed %}

{% hint style="success" %}
只有**所有者**可以撤销和恢复其他所有者的访问权限。
{% endhint %}

已撤销访问权限的用户位于**已撤销**选项卡中，并将：

* 无权限访问任何组织密码库项目、集合等。
* 无法使用 [SSO 登录](../login-with-sso/)，或使用[组织 Duo](../account/two-step-login/setup-guides/two-step-login-via-duo.md) 进行两步登录。
* 不受您的组织[策略](enterprise-policies.md)的约束。
* 不占用许可证座位。

### 恢复访问权限 <a href="#restore-access" id="restore-access"></a>

要恢复某个用户的访问权限：

1、在管理控制台中，导航到**成员**。

2、选择您想要恢复访问权限的成员，然后使用 ≡选项菜单**恢复访问权限**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2xe3Vt7l9CCO85RhhmoVJU/47321af7571e298c697a412c650403d6/2024-12-03_15-11-35.png?_a=DAJCwlWIZAAB" %}
恢复访问权限
{% endembed %}

当您恢复某个用户的访问权限时，他们无需再次执行[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)流程。

## 审查用户 2FA 状态 <a href="#review-user-2fa-status" id="review-user-2fa-status"></a>

用户的 2FA 状态可在**成员**页面查看。如果用户拥有一个 **🔒**图标，说明其 Bitwarden 账户已启用两步登录。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/HNlJNX9VJVURxGqrrBdRb/55b9ee7cc268e3400eb3d1f136e161fd/2024-12-03_15-14-09.png?_a=DAJCwlWIZAAB" %}
2FA 指示器
{% endembed %}

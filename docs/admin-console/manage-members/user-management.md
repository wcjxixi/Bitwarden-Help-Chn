# 用户管理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-users/)
{% endhint %}

## 用户席位 <a href="#user-seats" id="user-seats"></a>

「用户席位」指的是一个组织内单个用户的许可证。当您的组织成员占用一个用户席位时，该成员将根据您的特定方案获得访问 Bitwarden 服务的权限。用户席位并非永久绑定给该成员；当成员离开组织时，该用户席位将可供新成员使用。

当您[邀请](user-management.md#invite)新用户时，Bitwarden 云端 [团队和企业组织](../organizations-overview.md#types-of-organizations)将**自动扩展**用户席位。您可以在扩展时设置[席位限制](user-management.md#set-a-seat-limit)以防止您的席位数超过指定的数量，或根据需要[手动添加席位](user-management.md#manually-add-or-remove-seats)。无论您选择如何添加席位，您都需要[手动移除](user-management.md#manually-add-or-remove-seats)不再使用的席位。

添加和删​移除用户席位将调整您未来的账单总金额。添加席位将立即以调整后的比例向您存档的付款方式扣款，这样**您只需为计费周期的剩余时间（月/年）付费**。移除席位会导致您的下一次收费被调整，已付费席位**未使用的时间将计入您的信用额度**。

{% hint style="info" %}
只有[组织的所有者](member-roles.md#user-types)或[提供商服务用户](../../provider-portal/provider-users.md#provider-user-types)可以添加或移除席位，因为这会直接影响计费。
{% endhint %}

### 设置席位限制 <a href="#set-a-seat-limit" id="set-a-seat-limit"></a>

{% hint style="info" %}
自托管组织拥有的席位数量将始终与其[对应的云端组织](../../self-hosting/plan-for-deployment/self-host-an-organization.md#step-3-start-your-organization)保持一致。您将需要通过云端管理控制台管理您的席位数量，但可以通过设置[计费同步](../../self-hosting/licensing-on-premise.md#zi-dong-tong-bu)，使更改对您的自托管组织生效，而无需重新上传许可证。
{% endhint %}

要对您的组织可以扩展到的席位数量设置限制：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

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
自托管组织拥有的席位数量将始终与其[对应的云端组织](../../self-hosting/plan-for-deployment/self-host-an-organization.md#step-3-start-your-organization)保持一致。您将需要通过云端管理控制台管理您的席位数量，但可以通过设置[计费同步](../../self-hosting/licensing-on-premise.md#zi-dong-tong-bu)，使更改对您的自托管组织生效，而无需重新上传许可证。
{% endhint %}

要对您的组织手动添加或移除席位：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

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

为了确保组织的安全，Bitwarden 采用了一个 3 步流程来入职新成员：[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)。此流程旨在通过端到端加密，促进组织和用户之间的安全共享。

{% hint style="info" %}
本页面涵盖了手动将用户添加到组织的流程，此外，也提供了其他自动配置用户和群组的方法：

* 团队和企业组织可以[使用 SCIM](scim/about-scim.md)。
* 团队和企业组织可以[使用目录同步](directory-connector/about-directory-connector.md)。
* 企业组织可以[使用 JIT](../login-with-sso/jit-provisioning.md)。
{% endhint %}

### 邀请 <a href="#invite" id="invite"></a>

{% hint style="success" %}
**对于企业组织**，我们建议在邀请用户之前配置[企业策略](../oversight-visibility/enterprise-policies.md)，以确保加入您的组织时的合规性。
{% endhint %}

要邀请用户加入您的组织：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**成员**，然后选择 ✚**邀请用户**按钮：

{% embed url="https://bitwarden.com/assets/7AJjR4oqEnCH3A89YYoWpH/498d594fa9703bee9c5f49e2af9f83d0/Invite_member_to_an_organization.png?w=1200&fm=avif" %}
邀请成员加入组织
{% endembed %}

3、在邀请用户面板上：

* 输入新用户用于接收邀请的**电子邮箱**地址。您可以使用逗号分隔电子邮件地址，一次最多添加 20 个用户。
* 选择要应用于新用户的**成员角色**。[成员角色](member-roles.md#member-roles)决定了这些用户在组织层面拥有哪些权限。
* 在**群组**标签页中，选择要将此用户添加到哪些[群组](groups.md)中。
* 在**集合**标签页中，选择要为此用户授予访问权限的集合以及他们应拥有的每个集合的[权限](member-roles.md#permissions)。

4、点击**保存**以邀请指定的用户加入您的组织。

{% hint style="info" %}
**邀请将在 5 天后过期**，届时需要重新邀请用户。通过勾选每个用户并使用 **≡选项图标**选择**重新发送邀请**来批量重新邀请用户。

<img src="https://bitwarden.com/assets/1yj3MLJDTr7zOn5TwP0FGJ/67a16c6ee6ee14a92aa350986244e164/Resend_invitations.png?w=1200&#x26;fm=avif" alt="" data-size="original">

如果您是自托管 Bitwarden，您可以使用[环境变量](../../self-hosting/deploy-and-configure/configuration-options/environment-variables.md)来配置邀请的有效期。
{% endhint %}

### 接受 <a href="#accept" id="accept"></a>

受邀用户将收到一封来自 Bitwarden 的电子邮件，邀请他们加入组织。单击电子邮件中的链接将打开 Bitwarden 网页 App，用户可以在其中登录或创建账户以接受邀请：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/58e2ece3acfe37eaffa4bc55611eb414/Screen_Shot_2023-04-28_at_10.40.35_AM.png?_a=DAJCwlWIZAAB" %}
邀请加入
{% endembed %}

您必须**完全登录到 Bitwarden 网页 App** 以接受邀请。接受邀请后，您将收到通知，[确认](user-management.md#confirm)后即可访问组织。此外，组织成员在接受邀请时，其[电子邮件将自动验证](../../password-manager/more/password-manager-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)。

### 确认 <a href="#confirm" id="confirm"></a>

要确认已接受加入您组织的邀请：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md) 然后使用产品切换器打开管理员控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**成员**。

3、选择任何`已接受`的用户，然后使用 ≡选项菜单 **✔︎确认所选**：

{% embed url="https://bitwarden.com/assets/5eRDRAooRSGqRWJYZB5fgz/f3eac670d95664be963d2b38eddf68b5/Confirm_member_to_an_organization.png?w=1200&fm=avif" %}
确认成员加入组织
{% endembed %}

4、验证您屏幕上显示的[指纹短语](../../security/encryption/account-fingerprint-phrase.md)是否与您的新成员的匹配，指纹短语可以在**设置 → 我的帐户**中找到。

<div align="left"><figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sWPBv5GFAyMcULNxfCCJG/b3115a77e0d8d8d48fcc1f9e24e42d70/fingerprint-phrase.png?_a=DAJCwlWIZAAB" alt=""><figcaption><p>示例指纹短语</p></figcaption></figure></div>

每一个指纹短语对于其账户都是唯一的，它是确保安全添加用户的最后一层监督。如果它们匹配，请选择**提交**。

{% hint style="info" %}
如果已打开**不再提示验证指纹短语**，则可通过清除浏览器缓存和 cookie 来重新激活指纹短语验证。
{% endhint %}

## 管理现有成员 <a href="#manage-existing-members" id="manage-existing-members"></a>

在**成员**页面，您还可以查看和更新​​个人成员的账户，例如将其添加到群组、集合或 Secrets Manager。选择 **≡菜单图标**查看每个用户的可用选项：

{% embed url="https://bitwarden.com/assets/5tspjHKPHunTlRhylIJo5O/c707a3e1780364f8820832c216b5ca64/Update_member.png?w=1200&fm=avif" %}
更新用户
{% endembed %}

### 审查 2FA 状态 <a href="#review-2fa-status" id="review-2fa-status"></a>

用户的 2FA 状态可在**成员**页面查看。如果用户拥有一个 **🔒锁定图标**，说明其 Bitwarden 账户已启用两步登录。

{% embed url="https://bitwarden.com/assets/HNlJNX9VJVURxGqrrBdRb/1592f5c29694cf36e973ddac553e95e1/2FA_status.png?w=1200&fm=avif" %}
2FA 状态
{% endembed %}

### 下载成员列表 <a href="#download-list-of-members" id="download-list-of-members"></a>

如果您想在管理控制台之外查看或分享所有组织成员的列表，拥有**管理用户**权限的所有者、管理员和[自定义角色](member-roles.md#custom-role)用户可以导出 `.csv` 文件。所有组织均可使用此功能。

要导出成员列表，请转到**成员然后**选择 **⬇️下载图标**：

{% embed url="https://bitwarden.com/assets/6FCI1z0EtjbNAgeK5DZVx6/0e9b448678e95f10249a009d5d7f5aba/Export_member_list.png?w=1200&fm=avif" %}
导出成员列表
{% endembed %}

{% hint style="info" %}
拥有**管理账户恢复权限**但没有**管理用户**权限的自定义角色用户也可以下载 `.csv` 文件，但该文件仅显示已注册[账户恢复](account-recovery/about-account-recovery.md)的成员。所有其他成员均不包含在该文件中。
{% endhint %}

#### 包含的数据 <a href="#included-data" id="included-data"></a>

成员列表导出文件包含每个账户的以下信息：

| 列               | 描述                                                                                                                                |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| 电子邮箱            | 账户的电子邮箱地址                                                                                                                         |
| 名称              | 用户的名称，可在**设置** → **我的账户**中查看                                                                                                      |
| 状态              | 显示账户的[入职](user-management.md#onboard-users)状态（**已邀请**、**已接受**或**已确认**），或账户是否已从组织中[撤销](revoke-remove/temporarily-revoke-access.md) |
| 角色              | 用户在组织中的[成员角色](member-roles.md)                                                                                                    |
| 两步登录            | 显示用户是否使用[两步登录方式](../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)登录                                   |
| 账户恢复            | 显示用户是否已注册[账户恢复](account-recovery/about-account-recovery.md)                                                                       |
| Secrets Manager | 显示是否已为该成员启用 [Secrets Manager](../../secrets-manager/secrets-manager-overview.md)                                                  |
| 群组              | 列出包含该成员的所有群组                                                                                                                      |

{% hint style="success" %}
企业组织可以查看[成员访问权限报告](../../password-manager/your-vault/security-tools/vault-health-reports.md#member-access)，了解成员可以访问哪些集合、他们在每个已分配的集合中的权限级别等等。
{% endhint %}

### 移除用户 <a href="#remove-users" id="remove-users"></a>

您也可以在**成员**页面将成员从组织中移除。有三种方式：

* [临时撤销访问权限](revoke-remove/temporarily-revoke-access.md)
* [永久移除访问权限](revoke-remove/permanently-remove-access.md)
* [删除组织成员账户](revoke-remove/delete-member-accounts.md)

{% hint style="danger" %}
删除账户是永久性的，无法撤销或恢复。要创建密码库数据的备份并将其存储在安全位置，请[导出您的密码库数据](../../password-manager/import-and-export/export-vault-data.md)。
{% endhint %}

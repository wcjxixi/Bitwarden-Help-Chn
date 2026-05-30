# 邀请 & 管理成员

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-users/)
{% endhint %}

添加和管理您的组织成员，以确保合适的人员可以访问 Bitwarden。

{% hint style="info" %}
本文仅讨论邀请用户和管理您的订阅席位数量的可用方法之一：

* 所有组织都可以[手动邀请用户](user-management.md)和更新[席位数量](../../plans-and-pricing/manage-subscription-seats-in-your-organization.md)。
* 团队版和企业版组织可以使用 [SCIM](scim/about-scim.md)。
* 团队版和企业版组织可以使用 [Directory Connector](directory-connector/about-directory-connector.md)。
* 企业版组织可以[使用 JIT](../login-with-sso/jit-provisioning.md)。
{% endhint %}

## 添加新成员 <a href="#add-new-members" id="add-new-members"></a>

为了确保组织的安全，Bitwarden 采用了一个 三步流程来添加和入职新成员：[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)。此流程旨在通过保持端到端加密，促进组织和用户之间的安全共享。

### 邀请 <a href="#invite" id="invite"></a>

{% hint style="success" %}
对于企业版组织，我们建议在邀请用户之前配置[企业策略](../oversight-visibility/enterprise-policies.md)，以确保新成员加入组织时符合合规要求。
{% endhint %}

要邀请某人加入您的组织：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

2、导航到**成员**，然后选择 ✚**邀请用户**按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7AJjR4oqEnCH3A89YYoWpH/498d594fa9703bee9c5f49e2af9f83d0/Invite_member_to_an_organization.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>邀请成员加入组织</p></figcaption></figure></div>

3、在邀请用户面板上：

* 输入新用户用于接收邀请的**电子邮箱**地址。您可以使用逗号分隔电子邮箱地址一次性添加多个用户。
* 选择要应用于新用户的**成员角色**。[成员角色](member-roles.md#member-roles)决定了这些用户在组织层面拥有哪些权限。
* 在**群组**选项卡中，选择要将此用户添加到哪些[群组](groups.md)中。
* 在**集合**选项卡中，选择要为此用户授予访问权限的集合，以及他们应拥有的每个集合的[权限](member-roles.md#permissions)。

4、点击**保存**以邀请指定的用户加入您的组织。

{% hint style="info" %}
**邀请将在 5 天后过期**，届时需要重新邀请该成员。通过勾选每个用户并使用 **≡选项图标**选择**重新发送邀请**来批量重新邀请成员：

<img src="https://bitwarden.com/assets/1yj3MLJDTr7zOn5TwP0FGJ/67a16c6ee6ee14a92aa350986244e164/Resend_invitations.png?w=1200&#x26;fm=avif" alt="" data-size="original">

如果您是自托管 Bitwarden，您可以使用[环境变量](../../self-hosting/deploy-and-configure/configuration-options/environment-variables.md)来配置邀请的有效期。
{% endhint %}

### 接受 <a href="#accept" id="accept"></a>

受邀用户将收到一封来自 Bitwarden 的电子邮件，邀请他们加入组织。点击电子邮件中的链接将打开 Bitwarden 网页 App，用户可以在其中登录或创建账户以接受邀请：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4Fe96NuWb7yRe6muKf7UbZ/bcb1a8df0bc2ffdecbcd86b82d16c9a3/2025-09-03_10-41-25.png?w=711&#x26;fm=avif" alt=""><figcaption><p>组织邀请</p></figcaption></figure></div>

您必须**完全登录到 Bitwarden 网页 App** 才能接受邀请。接受邀请后，管理员需要[确认](user-management.md#confirm)访问权限。确认后，您将收到可以访问组织的通知。此外，组织成员在接受邀请时，其[电子邮箱将自动验证](../../password-manager/more/password-manager-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)。

### 确认 <a href="#confirm" id="confirm"></a>

要确认已接受加入您组织的邀请：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

2、导航到**成员**。

3、选择任何`已接受`的用户，然后使用 ≡选项菜单 **✔︎确认所选**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5eRDRAooRSGqRWJYZB5fgz/f3eac670d95664be963d2b38eddf68b5/Confirm_member_to_an_organization.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>确认成员加入组织</p></figcaption></figure></div>

4、验证您屏幕上显示的[指纹短语](../../security/encryption/account-fingerprint-phrase.md)是否与您的新成员的匹配，指纹短语可以在**设置 → 我的账户**中找到。

<div align="left" data-with-frame="true"><figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sWPBv5GFAyMcULNxfCCJG/b3115a77e0d8d8d48fcc1f9e24e42d70/fingerprint-phrase.png?_a=DAJCwlWIZAAB" alt=""><figcaption><p>示例指纹短语</p></figcaption></figure></div>

每一个指纹短语对于其账户都是唯一的，它是确保安全添加用户的最后一层监督。如果它们匹配，请选择**提交**。

{% hint style="info" %}
如果已打开**不再提示验证指纹短语**，则可通过清除浏览器缓存和 cookie 来重新激活指纹短语验证。
{% endhint %}

## 管理现有成员 <a href="#manage-existing-members" id="manage-existing-members"></a>

在**成员**页面，您还可以查看和更新​​个人成员的账户，例如将其添加到群组、集合或 Secrets Manager。选择 **≡菜单图标**查看每个用户的可用选项：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5tspjHKPHunTlRhylIJo5O/c707a3e1780364f8820832c216b5ca64/Update_member.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>更新成员</p></figcaption></figure></div>

### 审查 2FA 状态 <a href="#review-2fa-status" id="review-2fa-status"></a>

用户的 2FA 状态可在**成员**页面查看。如果用户拥有一个 **🔒锁定图标**，说明其 Bitwarden 账户已启用两步登录：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/HNlJNX9VJVURxGqrrBdRb/1592f5c29694cf36e973ddac553e95e1/2FA_status.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>2FA 状态</p></figcaption></figure></div>

### 下载成员列表 <a href="#download-list-of-members" id="download-list-of-members"></a>

如果您想在 Admin Console 之外查看或分享所有组织成员的列表，拥有**管理用户**权限的所有者、管理员和[自定义角色](member-roles.md#custom-role)用户可以导出 `.csv` 文件。此功能适用于所有组织。

要导出成员列表，请前往**成员**然后选择 **⬇️下载图标**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6FCI1z0EtjbNAgeK5DZVx6/0e9b448678e95f10249a009d5d7f5aba/Export_member_list.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>导出成员列表</p></figcaption></figure></div>

{% hint style="info" %}
拥有**管理账户恢复**权限但没有**管理用户**权限的自定义角色用户也可以下载 `.csv` 文件，但该文件仅显示注册了[账户恢复](account-recovery/about-account-recovery.md)的成员。所有其他成员均不包含在该文件中。
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
企业版组织可以查看[成员访问权限报告](../../password-manager/your-vault/security-tools/vault-health-reports.md#member-access)，了解成员可以访问哪些集合、他们在每个已分配的集合中的权限级别等等。
{% endhint %}

### 移除用户 <a href="#remove-users" id="remove-users"></a>

您也可以在**成员**页面将成员从组织中移除。有三种方式：

* [临时撤销访问权限](revoke-remove/temporarily-revoke-access.md)
* [永久移除访问权限](revoke-remove/permanently-remove-access.md)
* [删除组织成员账户](revoke-remove/delete-member-accounts.md)

{% hint style="danger" %}
删除账户是永久性的，无法撤销或恢复。要创建密码库数据的备份并将其存储在安全位置，请[导出您的密码库数据](../../password-manager/import-and-export/export-vault-data.md)。
{% endhint %}

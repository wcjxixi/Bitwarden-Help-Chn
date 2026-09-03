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
* 企业版组织可以通过可共享的邀请链接邀请成员。
* 企业版组织可以[使用 JIT](../login-with-sso/jit-provisioning.md)。
{% endhint %}

## 添加新成员 <a href="#add-new-members" id="add-new-members"></a>

为了确保组织的安全，Bitwarden 采用了一个 三步流程来添加和入职新成员：[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)。此流程旨在通过保持端到端加密，促进组织和用户之间的安全共享。

### 邀请 <a href="#invite" id="invite"></a>

{% hint style="success" icon="lightbulb" %}
对于企业版组织，我们建议在邀请用户之前配置[企业策略](../oversight-visibility/enterprise-policies.md)，以确保新成员加入组织时符合合规要求。用户进入[接受](user-management.md#accept)状态后，他们将受组织策略的约束。
{% endhint %}

选择一种邀请用户加入您的组织的方式：

{% tabs %}
{% tab title="电子邮件邀请" %}
1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

2、导航到**成员**，然后选择 <i class="fa-plus">:plus:</i>**邀请成员**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7AJjR4oqEnCH3A89YYoWpH/498d594fa9703bee9c5f49e2af9f83d0/Invite_member_to_an_organization.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>邀请成员加入组织</p></figcaption></figure></div>

3、选择**通过电子邮件**选项卡：

* 输入新用户用于接收邀请的**电子邮箱**地址。您可以使用逗号分隔电子邮箱地址一次性添加多个用户。
* 选择要应用于新用户的**成员角色**。[成员角色](member-roles.md#member-roles)决定了这些用户在组织层面拥有哪些权限。
* 在**群组**选项卡中，选择要将此用户添加到哪些[群组](groups.md)中。
* 在**集合**选项卡中，选择要为此用户授予访问权限的集合，以及他们应拥有的每个集合的[权限](member-roles.md#permissions)。

4、点击**保存**以邀请指定的用户加入您的组织。
{% endtab %}

{% tab title="链接邀请" %}
企业版组织可以生成一个可分享的邀请链接，任何拥有该链接的人，只要其电子邮箱域名在链接的允许列表中，即可使用该链接请求加入组织。这让管理员可以通过他们首选的通信渠道（如 Slack 或 Teams 消息）分发邀请，而无需依赖从 Bitwarden 发送的个人电子邮件。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/TFK2JVOdL4WqjCk4xtQEi/c57df92f2d832569b9d63dcbb084aaec/edited_copy_link.png?w=700&#x26;fm=avif" alt=""><figcaption><p>复制链接</p></figcaption></figure></div>

有效的邀请链接将包含以下结构：

```
https://vault.bitwarden.com/#/join/{inviteLinkCode}?key={inviteKey}
```

要生成邀请链接：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

2、导航到**成员**，然后选择 <i class="fa-plus">:plus:</i>**邀请成员**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7AJjR4oqEnCH3A89YYoWpH/498d594fa9703bee9c5f49e2af9f83d0/Invite_member_to_an_organization.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>邀请成员加入组织</p></figcaption></figure></div>

3、选择**通过链接**选项卡：

4、输入一个或多个**允许的域名**。使用邀请链接时：

* 只有这些域名上的电子邮箱地址才能使用该链接加入。
* 必须始终至少存在一个域名，您无法生成不受限制的链接。
  * 允许的域名为链接提供了额外的安全性。您应仅允许信任的域名。不建议使用诸如 gmail.com 之类的泛域名。
* 移除允许的域名或生成新链接将使之前生成的链接失效。
* 如果组织拥有[声明域名](../oversight-visibility/claimed-domains/claimed-domains.md)，该字段将自动预填入此域名。

{% hint style="warning" %}
**允许的**域名可让您更精细地控制哪些用户可以尝试加入您的组织。此外，请注意，允许的域名与已声明的域名是两种不同的机制。如果您的组织拥有**声明域名**，则在生成第一个链接时，该域名会自动填入允许的域名列表中。
{% endhint %}

5、选择**复制链接**，然后通过您首选的渠道分享。

{% hint style="info" %}
为了接受邀请链接，成员的电子邮箱地址必须经过验证。云端账户通常在注册时即完成验证。如果电子邮箱未经验证，未验证的用户可以登录网页 App 然后选择**验证电子邮箱**。
{% endhint %}

#### 刷新或限制链接 <a href="#refresh-or-restrict-a-link" id="refresh-or-restrict-a-link"></a>

邀请链接不会自行过期。若要使其失效，请选择**刷新**以生成新链接，旧链接将立即停用。从允许列表中移除所有域名也会使链接失效。

{% hint style="info" %}
邀请链接适用于企业版组织。如果您的组织已从企业版降级，现有链接将不再有效，且**通过链接**选项卡将不可用。
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**电子邀请将在 5 天后过期**，届时需要重新邀请该成员。可通过勾选每个用户并使用 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i>**选项图标**选择**重新发送邀请**来批量重新邀请成员：

<img src="https://bitwarden.com/assets/1yj3MLJDTr7zOn5TwP0FGJ/67a16c6ee6ee14a92aa350986244e164/Resend_invitations.png?w=1200&#x26;fm=avif" alt="" data-size="original">

如果您是自托管 Bitwarden，您可以使用[环境变量](../../self-hosting/deploy-and-configure/configuration-options/environment-variables.md)来配置邀请的有效期。

**链接邀请**不会过期，除非允许的域名已被移除、链接已被轮换或链接已被停用。
{% endhint %}

### 接受 <a href="#accept" id="accept"></a>

用户要接受组织邀请：

{% tabs %}
{% tab title="电子邮件邀请" %}
受邀用户将收到一封来自 Bitwarden 的电子邮件，邀请他们加入组织。点击电子邮件中的链接将打开 Bitwarden 网页 App，用户可以在其中登录或创建账户以接受邀请：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4Fe96NuWb7yRe6muKf7UbZ/bcb1a8df0bc2ffdecbcd86b82d16c9a3/2025-09-03_10-41-25.png?w=711&#x26;fm=avif" alt=""><figcaption><p>组织邀请</p></figcaption></figure></div>

您必须**完全登录到 Bitwarden 网页 App** 才能接受邀请。接受邀请后，管理员需要[确认](user-management.md#confirm)访问权限。确认后，您将收到可以访问组织的通知。此外，组织成员在接受邀请时，其[电子邮箱将自动验证](../../password-manager/more/password-manager-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)。
{% endtab %}

{% tab title="链接邀请" %}
受邀用户将通过组织管理员首选的方式收到链接，例如电子邮件、Slack、Teams 等。用户确认该链接是来自可靠来源后，点击链接将把他们重定向到组织邀请页面：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3L7jnjSHjQpjVkhCwbkC5j/b309ddcd2bc75cac1d6a64a4d423da66/join_invite_link.png?w=400&#x26;fm=avif" alt=""><figcaption><p>打开组织邀请链接</p></figcaption></figure></div>

要加入该组织：

* **新用户**：填写对话框中显示的字段，以创建新的 Bitwarden 账户。
* **现有用户**：选择创建账户对话框下方的**登录**。现有用户必须拥有[已验证电子邮箱](../../password-manager/more/password-manager-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)的账户，才能接受组织邀请。

您接受邀请后，管理员将需要[确认](user-management.md#confirm)访问权限。确认后，您将收到通知，即可访问该组织。

{% hint style="info" %}
接受邀请链接时，用于登录或创建新账户的电子邮箱地址，将与组织的允许域名列表进行核对。如果使用链接未能成功，请检查：

* 地址域名是否与组织的允许域名列表匹配。
* 管理员是否尚未删除、轮换或停用该链接。
* 您现有的 Bitwarden 账户是否符合组织策略，例如[单一组织](../oversight-visibility/enterprise-policies.md#single-organization)策略。
* 您之前尚未接受加入此组织的邀请。
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
在用户被[确认](user-management.md#confirm)之前，需要先遵守以下策略。这些策略包括：

* [单一组织](../oversight-visibility/enterprise-policies.md#single-organization)
* [要求两步登录](../oversight-visibility/enterprise-policies.md#require-two-step-login)
{% endhint %}

### 确认 <a href="#confirm" id="confirm"></a>

要确认已接受加入您组织的邀请：

1、登录到 Bitwarden [网页 App](../../password-manager/getting-started/getting-started-webvault.md)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

2、导航到**成员**。

3、选择任何`已接受`的用户，然后使用 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i> 选项菜单 <i class="fa-check">:check:</i>**确认所选**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5eRDRAooRSGqRWJYZB5fgz/f3eac670d95664be963d2b38eddf68b5/Confirm_member_to_an_organization.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>确认成员加入组织</p></figcaption></figure></div>

4、验证您屏幕上显示的[指纹短语](../../security/encryption/account-fingerprint-phrase.md)是否与您的新成员的匹配，指纹短语可以在**设置 → 我的账户**中找到。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6sWPBv5GFAyMcULNxfCCJG/b3115a77e0d8d8d48fcc1f9e24e42d70/fingerprint-phrase.png?w=285&#x26;fm=avif" alt=""><figcaption><p>指纹短语</p></figcaption></figure></div>

每一个指纹短语对于其账户都是唯一的，它是确保安全添加用户的最后一层监督。如果它们匹配，请选择**提交**。

{% hint style="info" %}
如果已打开**不再提示验证指纹短语**，则可通过清除浏览器缓存和 cookie 来重新激活指纹短语验证。
{% endhint %}

## 管理现有成员 <a href="#manage-existing-members" id="manage-existing-members"></a>

在**成员**页面，您还可以查看和更新​​个人成员的账户，例如将其添加到群组、集合或 Secrets Manager。选择 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i>**菜单图标**查看每个用户的可用选项：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5tspjHKPHunTlRhylIJo5O/c707a3e1780364f8820832c216b5ca64/Update_member.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>更新成员</p></figcaption></figure></div>

### 审查 2FA 和账户恢复状态 <a href="#review-2fa-and-account-recovery-status" id="review-2fa-and-account-recovery-status"></a>

**成员**页面还会在**策略**列中标注哪些用户已启用特定功能。<i class="fa-key">:key:</i>**钥匙图标**表示该成员已注册[账户恢复](account-recovery/about-account-recovery.md)。<i class="fa-lock-keyhole">:lock-keyhole:</i>**锁图标**表示启用了[两步登录](../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/HNlJNX9VJVURxGqrrBdRb/1592f5c29694cf36e973ddac553e95e1/2FA_status.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>2FA 状态</p></figcaption></figure></div>

### 下载成员列表 <a href="#download-list-of-members" id="download-list-of-members"></a>

如果您想在 Admin Console 之外查看或分享所有组织成员的列表，拥有**管理用户**权限的所有者、管理员和[自定义角色](member-roles.md#custom-role)用户可以导出 `.csv` 文件。此功能适用于所有组织。

要导出成员列表，请前往**成员**然后选择 <i class="fa-arrow-down-to-bracket">:arrow-down-to-bracket:</i>**下载图标**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6FCI1z0EtjbNAgeK5DZVx6/0e9b448678e95f10249a009d5d7f5aba/Export_member_list.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>导出成员列表</p></figcaption></figure></div>

{% hint style="info" %}
拥有**管理账户恢复**权限但没有**管理用户**权限的自定义角色用户也可以下载 `.csv` 文件，但该文件仅显示注册了[账户恢复](account-recovery/about-account-recovery.md)的成员。所有其他成员均不包含在该文件中。
{% endhint %}

#### 包含的数据 <a href="#included-data" id="included-data"></a>

成员列表导出文件包含每个账户的以下信息：

<table data-search="false"><thead><tr><th>列</th><th>描述</th></tr></thead><tbody><tr><td>电子邮箱</td><td>账户的电子邮箱地址</td></tr><tr><td>名称</td><td>用户的名称，可在<strong>设置</strong> → <strong>我的账户</strong>中查看</td></tr><tr><td>状态</td><td>显示账户的<a href="user-management.md#onboard-users">入职</a>状态（<strong>已邀请</strong>、<strong>已接受</strong>或<strong>已确认</strong>），或账户是否已从组织中<a href="revoke-remove/temporarily-revoke-access.md">撤销</a></td></tr><tr><td>角色</td><td>用户在组织中的<a href="member-roles.md">成员角色</a></td></tr><tr><td>两步登录</td><td>显示用户是否使用<a href="../../account/two-step-login/setup-two-step-login/two-step-login-methods.md">两步登录方式</a>登录</td></tr><tr><td>账户恢复</td><td>显示用户是否已注册<a href="account-recovery/about-account-recovery.md">账户恢复</a></td></tr><tr><td>Secrets Manager</td><td>显示是否已为该成员启用 <a href="../../secrets-manager/secrets-manager-overview.md">Secrets Manager</a></td></tr><tr><td>群组</td><td>列出包含该成员的所有群组</td></tr></tbody></table>

{% hint style="success" icon="lightbulb" %}
企业版组织可以查看[成员访问权限报告](../../password-manager/your-vault/security-tools/vault-health-reports.md#member-access)，了解成员可以访问哪些集合、他们在每个已分配的集合中的权限级别等等。
{% endhint %}

### 更新成员的账户电子邮箱和名称 <a href="#update-members-account-email-and-name" id="update-members-account-email-and-name"></a>

如果您的组织使用已声明的域名，并且某个成员没有主密码，管理员可以[更改该成员的电子邮箱地址和名称](change-members-account-email-and-name.md)。

### 移除用户 <a href="#remove-users" id="remove-users"></a>

您也可以在**成员**页面将成员从组织中移除。有三种方式：

* [临时撤销访问权限](revoke-remove/temporarily-revoke-access.md)
* [永久移除访问权限](revoke-remove/permanently-remove-access.md)
* [删除组织成员账户](revoke-remove/delete-member-accounts.md)

{% hint style="warning" %}
删除账户或组织是**永久性的，无法撤销或恢复，并将删除所有相关的密码库数据**。在执行账户或组织删除之前，您可能需要先导出数据：

* [导出个人密码库数据](../../password-manager/import-and-export/export-vault-data.md)
* [导出组织密码库数据](../manage-shared-items/export-organization-items/export-organization-items.md)
{% endhint %}

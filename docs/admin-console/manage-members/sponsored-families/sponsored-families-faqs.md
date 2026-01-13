# 赞助家庭 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/sponsored-families-faqs/)
{% endhint %}

## 雇主 FAQ <a href="#employer-faqs" id="employer-faqs"></a>

### 问：自托管企业组织可以发出赞助吗？ <a href="#q-can-self-hosted-enterprise-organizations-issue-sponsorships" id="q-can-self-hosted-enterprise-organizations-issue-sponsorships"></a>

**答：**&#x53EF;以。您可以在[这里](../../../self-hosting/deploy-and-configure/optional-features/self-hosting-families-sponsorships.md)找到简短设置过程的说明。请提醒您的用户，他们的赞助家庭组织将通过我们的公共云 (`https://vault.bitwarden.com`) 提供，而不是通过您的自托管服务器提供。

## 员工 FAQ <a href="#employee-faqs" id="employee-faqs"></a>

### 问：我可以使用属于赞助企业成员的账户进行兑换吗？ <a href="#can-i-redeem-with-the-account-thats-a-member-of-the-sponsoring-enterprise" id="can-i-redeem-with-the-account-thats-a-member-of-the-sponsoring-enterprise"></a>

**答：**&#x4E0D;可以。兑换时，系统会要求您输入您拥有的**个人电子邮箱地址**。如果您已有个人 Bitwarden 账户，请输入该账户的电子邮箱地址。如果没有，请输入您要为其创建个人 Bitwarden 账户的个人电子邮箱地址。

### 问：我可以为我现有的家庭组织兑换吗？ <a href="#can-i-redeem-for-my-existing-families-organization" id="can-i-redeem-for-my-existing-families-organization"></a>

**答：**&#x53EF;以！为活跃的家庭组织兑换赞助将立即将您切换到赞助订阅，并在您已支付的订阅剩余时间上按比例添加账户信用额度。

### 问：我可以添加额外的存储空间吗？ <a href="#can-i-add-additional-storage" id="can-i-add-additional-storage"></a>

**答：**&#x53EF;以。您的赞助中只包含 1 GB。可以随时添加更多存储空间，这样做会通过您已存档的付款方式收取费用。

### 问：如果我离开赞助我的组织会怎样？ <a href="#what-happens-if-i-leave-the-organization-sponsoring-me" id="what-happens-if-i-leave-the-organization-sponsoring-me"></a>

**答：**&#x5982;果您离开或从赞助组织中被移除，或手动结束您的赞助，在下一个计费周期将通过您已存档的付款方式收取费用。

### 问：如果我的电子邮件中收到了续订提醒，我应该做什么？ <a href="#q-what-do-i-do-if-i-received-a-renewal-reminder-in-my-email" id="q-what-do-i-do-if-i-received-a-renewal-reminder-in-my-email"></a>

答：如果您仍然是赞助您的免费家庭组织的企业组织（通常是雇主）的成员，您可以放心地忽略这封邮件。如果您不再是该企业组织的成员，请打开您的家庭组织管理控制台，导航至**计费** → **付款方式**，检查付款方式是否有效，以确保您的组织能够顺利续订。

### 问：`Awaiting Sync` 是什么意思？ <a href="#q-what-does-awaiting-sync-mean" id="q-what-does-awaiting-sync-mean"></a>

**答：**`Awaiting Sync`（等待同步）表示您的自托管 Bitwarden 服务器正在等待与 Bitwarden 云同步，然后您的赞助才能完全兑换或更改。同步每天发生一次。

如果您尝试在同步完成之前兑换您的赞助，您将在云网络密码库中收到一条错误消息，内容为 `Cannot find an outstanding sponsorship offer for this organization`（找不到此组织的赞助邀请）。

### 问：受赞助的家庭组织可以放在自托管服务器上吗？ <a href="#q-can-a-sponsored-families-organization-be-on-a-self-hosted-server" id="q-can-a-sponsored-families-organization-be-on-a-self-hosted-server"></a>

**答：**&#x53EF;以。但是有几个步骤需要完成：

1. [如上所述](sponsored-families-faqs.md#redeem-your-sponsorship)，在 `https://vault.bitwarden.com` 兑换您的赞助。
2. 还是在 `https://vault.bitwarden.com`，[按照此处所述](../../../self-hosting/licensing-on-premise.md#retrieve-your-license-1)获取您的家庭组织的许可证文件。
3. [如此处所述](../../../self-hosting/licensing-on-premise.md#apply-your-license-1)，登录到您的自托管服务器并将许可证文件应用到组织。

请注意，您的自托管服务器需要连接到 SMTP 邮件服务器，以便将您的家庭组织的邀请发送给其他成员。

### 问：如果我的组织在美国服务器上，我能否在欧盟服务器上兑换家庭组织？ <a href="#q-if-my-organization-is-on-a-us-server-can-i-redeem-a-families-organization-on-the-eu-server" id="q-if-my-organization-is-on-a-us-server-can-i-redeem-a-families-organization-on-the-eu-server"></a>

**答：**&#x4E0D;能。家庭方案赞助只能在与赞助企业组织相同的云服务器上兑换。如果您的企业组织已从一个云服务器迁移到另一个云服务器，则必须在正确的云服务器上赞助新的家庭组织。有关迁移组织的更多信息，请参阅 [Bitwarden 迁移指南](../../more/teams-and-enterprise-migration-guide.md)。

### 问：如何移除家庭组织？ <a href="#q-how-do-i-remove-a-families-organization" id="q-how-do-i-remove-a-families-organization"></a>

**答：**&#x8981;移除家庭组织，请登录到属于企业组织成员的账户中，然后导航到**设置** → **免费 Bitwarden 家庭**。选择与赞助的家庭组织相关的 **⚙️**齿轮图标，然后选择**移除**。

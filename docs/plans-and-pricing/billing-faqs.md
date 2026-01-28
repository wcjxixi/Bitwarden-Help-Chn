# 计费 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/billing-faqs/)
{% endhint %}

本文包含有关方案和定价的常见问题 (FAQ)。

如需帮助选择适合您的 Bitwarden 方案，请参阅[哪种方案适合我？](what-plan-is-right-for-me.md)以及[关于 Bitwarden 方案](password-manager/about-bitwarden-plans.md)。

## 账户管理 <a href="#account-management" id="account-management"></a>

### 问：如何知道我在使用哪一种订阅方案？ <a href="#q-how-do-i-find-out-what-subscription-plan-im-on" id="q-how-do-i-find-out-what-subscription-plan-im-on"></a>

**答：**&#x767B;录您的网页 App：

* 对于个人订阅：请导航至**设置** → **订阅**。如果看不到此界面，则表示此账户是免费方案。如果存在此界面，则表示此账户是高级方案。
* 对于组织订阅：打开管理控制台。在组织的**计费** → **订阅**视图中，在**方案**部分记录了此组织的方案。

### 问：如何查看我的计费信息？ <a href="#q-how-do-i-view-my-billing-information" id="q-how-do-i-view-my-billing-information"></a>

**答：**&#x67E5;看计费信息取决于您是查看个人订阅还是组织订阅的计费信息。使用[更新您的计费信息](update-your-billing-information.md)来指导您完成这两个过程。

### 问：如何删除我的账户？ <a href="#q-how-do-i-delete-my-account" id="q-how-do-i-delete-my-account"></a>

**答：**&#x6211;们很遗憾看到您离开。使用[删除您的账户](delete-an-account-or-organization.md)来指导您完成这个过程。

### 问：如何从个人订阅升级到组织订阅？ <a href="#q-how-do-i-upgrade-from-an-individual-subscription-to-an-organization" id="q-how-do-i-upgrade-from-an-individual-subscription-to-an-organization"></a>

**答：**&#x4F7F;用[从个人升级到组织](password-manager/upgrade-from-individual-to-organization.md)来指导您完成这个过程。

### 问：如何从我的组织中添加或移除用户席位？ <a href="#q-how-do-i-add-or-remove-a-user-seat-from-my-organization" id="q-how-do-i-add-or-remove-a-user-seat-from-my-organization"></a>

**答：**&#x5BF9;于团队和企业组织，当您邀请新用户时，将自动添加用户席位。您可以[指定限制](../admin-console/manage-members/user-management.md#set-a-seat-limit)以防止您的席位数超过指定的数量。

要移除用户席位，请导航到您组织的**计费** → **订阅**界面，然后使用**订阅席位**输入框来移除席位（[了解更多](../admin-console/manage-members/user-management.md#manually-add-or-remove-seats)）。

添加和删​移除用户席位将调整您未来的账单总额。添加席位将立即以调整后的比例向您存档的付款方式扣款，这样**您只需为计费周期（月/年）的剩余时间付费**。移除席位会导致您的下一次收费被调整，已付费席位**未使用的时间将计入您的信用额度**。

### 问：如何将订阅用于自托管？ <a href="#q-how-do-subscriptions-work-for-self-hosting" id="q-how-do-subscriptions-work-for-self-hosting"></a>

**答：**&#x8981;在自托管服务器上使用订阅，请首先通过[网页 App](../password-manager/getting-started/getting-started-webvault.md) 在 Bitwarden 云端创建账户和订阅。从那里下载[订阅许可证](../self-hosting/licensing-on-premise.md#organization-license)，该许可证将标记对高级或组织功能的访问权限，以应用于您的自托管服务器。

根据 Bitwarden 服务条款，每个订阅仅允许一个组织部署。

### 问：如果我有一个家庭组织，还需要高级会员吗？ <a href="#q-if-i-have-a-families-organization-do-i-need-premium" id="q-if-i-have-a-families-organization-do-i-need-premium"></a>

**答：**&#x5F53;前的家庭方案（2020 年 09 月推出）自动为组织的所有 6 名成员提供高级功能，所以不需要！

传统的家庭方案不会自动提供高级功能，因此用户需要单独升级到高级版，或者由家庭组织的所有者升级组织。

### 问：为什么我的云端和自托管许可证到期日期不匹配？

**答：**&#x4E3A;了确保您不会无意中失去组织功能，我们在云上许可证到期和自托管服务器上许可证到期之间提供 2 个月的宽限期。[了解更多](organization-renewal.md)。

### 问：我的组织的计费电子邮箱的持有者可以执行哪些操作？

**答：**&#x60A8;组织的[计费电子邮箱](../admin-console/organizations-overview.md#create-an-organization)的持有人可以通过联系我们：

* 在订阅中添加或移除信用卡。
* 更改组织的计费电子邮件地址。
* 查询存档的账单和计费信息。
* 在每月和每年计费周期之间切换（如果适用于您的组织）。
* 请求方案升级、降级、取消或席位调整。

他们**不能**以任何理由请求删除组织、获取当前组织所有者的身份或请求将任何用户提升为所有者。

## 付款选项 <a href="#payment-options" id="payment-options"></a>

### 问：你们接受美国国内的客户的哪些付款方式？ <a href="#q-what-payment-options-do-you-accept-for-customers-based-in-the-united-states" id="q-what-payment-options-do-you-accept-for-customers-based-in-the-united-states"></a>

**答：**&#x6211;们接受信用卡/借记卡、PayPal、银行账户 (ACH)，以及比特币。对于企业订阅，我们还接受电汇和企业支票，最低付款额为 500 美元。有关付款方式的更多信息，请联系我们的[售后支持](https://bitwarden.com/contact/)。

### 问：你们接受美国国外的客户的哪些付款方式？ <a href="#q-what-payment-options-do-you-accept-for-customers-outside-the-united-states" id="q-what-payment-options-do-you-accept-for-customers-outside-the-united-states"></a>

**答：**&#x6211;们接受信用卡/借记卡、PayPal，以及比特币。对于企业订阅，我们还接受电汇和企业支票，最低付款额为 500 美元。有关付款方式的更多信息，请联系我们的[售后支持](https://bitwarden.com/contact/)。

### 问：可以使用比特币付款吗？ <a href="#q-can-i-pay-with-bitcoin" id="q-can-i-pay-with-bitcoin"></a>

**答：**&#x53EF;以。请注意，在购买订阅之前，您需要在**设置** → **计费**界面使用比特币添加信用额度。

### 问：我可以将 Bitwarden 免费方案用于商业用途吗？ <a href="#q-can-i-use-a-bitwarden-free-plan-for-commercial-use" id="q-can-i-use-a-bitwarden-free-plan-for-commercial-use"></a>

**答：**&#x53EA;要遵守我们的[服务条款](https://bitwarden.com/terms/)，用户可以出于个人或商业目的使用 Bitwarden 客户端（无论是付费账户还是免费账户）。

Bitwarden 的许可证授予有限的、非独占的、不可转让的、免版税许可，可将商业模块仅用于非生产环境中的内部开发和测试。更多信息，请参阅[许可证](https://github.com/bitwarden/server/blob/main/LICENSE.txt)和[许可证 FAQ](https://github.com/bitwarden/server/blob/main/LICENSE_FAQ.md)。

如果用户不打算修改、转售、出租、租赁、分发、再许可、出借或以其他方式将商业模块转让给任何第三方，或创建竞争性产品或服务，则可以在遵守我们的服务条款的前提下，将任何可用客户端用于商业或个人用途。

## 已知问题 <a href="#known-issues" id="known-issues"></a>

### 问：当我尝试在 Firefox 上升级高级版时发生了一个错误。我该如何解决这个问题？ <a href="#q-an-error-occurs-when-i-try-to-go-premium-on-firefox-how-do-i-fix-this" id="q-an-error-occurs-when-i-try-to-go-premium-on-firefox-how-do-i-fix-this"></a>

**答：**&#x6211;们观察到一些 Firefox 用户在提交高级订阅的付款信息时会收到如下错误信息：

`You passed an empty string for 'payment_method_data[referrer]'. We assume empty values are an attempt to unset a parameter; however 'payment_method_data[referrer]' cannot be unset. You should remove 'payment_method_data[referrer]' from your request or supply a non-empty value.`

当提交您的付款方式受到已安装的浏览器扩展或配置的浏览器选项的阻碍时，通常会发生这种情况。

**在隐私窗口中打开 Firefox 浏览器，然后尝试重新提交。**

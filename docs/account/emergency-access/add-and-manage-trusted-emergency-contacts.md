# 添加 & 管理受信任的紧急联系人

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/add-and-manage-trusted-emergency-contacts/)
{% endhint %}

受信任的紧急联系人是指您允许通过[紧急访问](about-emergency-access.md)登录您的 Bitwarden 账户的人员。您可以随时添加或更新受信任的紧急联系人。

## 添加受信任的紧急联系人 <a href="#add-trusted-emergency-contacts" id="add-trusted-emergency-contacts"></a>

为紧急访问[添加受信任的紧急联系人](add-and-manage-trusted-emergency-contacts.md)适用于高级版用户，包括付费版组织（家庭版、团队版和企业版）的成员。如果您的组织开启了[自动确认策略](../../admin-console/oversight-visibility/enterprise-policies.md#automatic-user-confirmation)，则您的账户将**无法**使用紧急访问。

要为紧急访问指定受信任的紧急联系人：

### 1. 您邀请其他用户成为您受信任的紧急联系人 <a href="#id-1-you-invite-another-user-to-become-your-trusted-emergency-contact" id="id-1-you-invite-another-user-to-become-your-trusted-emergency-contact"></a>

作为想要对您的密码库授予紧急访问的人，请邀请受信任的紧急联系人：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、选择 **➕添加紧急联系人**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3gb0Zm4K935RUmzjd62eJq/a3930a8381fe1205b655e7a7bb0eca47/2025-12-31_09-50-39.png?w=966&#x26;fm=avif" alt=""><figcaption><p>紧急访问页面</p></figcaption></figure></div>

3、输入您信任的紧急联系人的**电子邮箱**。受信任的紧急联系人必须拥有 Bitwarden 账户（免费版或高级版），以及必须位于同一[服务器地理位置](../../security/server-geographies.md)：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2IEldGj87MY2IMDQpty6Vr/f0e9750c278663903be46f4a5d5a4f8c/2025-12-31_09-52-02.png?w=964&#x26;fm=avif" alt=""><figcaption><p>邀请紧急联系人</p></figcaption></figure></div>

4、为受信任的紧急联系人设置**用户访问权限**级别：**查看**或**接管**。

5、设置**等待时间**。这是您的受信任的紧急联系人请求账户访问权限后，必须等待多长时间才能获得此访问权限，除非您提前[手动批准请求](add-and-manage-trusted-emergency-contacts.md#use-emergency-access)。最短等待时间为一天。

6、选择**保存**以发送邀请。

您的受信任的紧急联系人**必须现在接受此邀请**。

{% hint style="info" %}
成为受信任的紧急联系人的邀请的有效期只有 5 天。
{% endhint %}

### &#xD;2\. 他们接受邀请 <a href="#id-2-they-accept-the-invitation" id="id-2-they-accept-the-invitation"></a>

作为想要接收他人密码库的紧急访问权限的人，请接受邀请：

1、打开电子邮件邀请，然后选择**成为紧急联系人**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1S7YBbeECgEdl1v9r4E5BU/37c6c4207cb8c6df7f69a63ea12751fd/Screenshot_2024-02-27_at_9.23.46_AM.png?w=590&#x26;fm=avif" alt=""><figcaption><p>紧急访问邀请</p></figcaption></figure></div>

2、将在浏览器中打开登录页面。根据您是否拥有账户，选择**登录**或**创建账户**以接受邀请。

接受邀请后，邀请的用户**必须确认您作为其受信任的联系人**，然后他们才能[发起访问请求](add-and-manage-trusted-emergency-contacts.md#use-emergency-access)。

### 3. 您确认他们为您受信任的紧急联系人 <a href="#id-3-you-confirm-them-as-your-trusted-emergency-contact" id="id-3-you-confirm-them-as-your-trusted-emergency-contact"></a>

作为想要对您的密码库授予紧急访问的人，请在受信任的联系人接受邀请后确认该联系人：：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、当受邀请的用户显示 `需要确认` 状态时，选择 **≡**&#x83DC;单图标。

3、从下拉菜单中选择**确认**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/jEvLxG2nmFJRnlTbcpwRO/891f14df501abae6c1e93ce57a527ec4/2025-12-31_09-53-35.png?w=966&#x26;fm=avif" alt=""><figcaption><p>确认紧急联系人</p></figcaption></figure></div>

4、为验证受邀请的用户，请与受邀请的用户确认显示的[指纹短语](../../security/encryption/account-fingerprint-phrase.md)，然后选择**确认**。

受信任的紧急联系人设置&#x20;<a href="#trusted-emergency-contact-settings" id="trusted-emergency-contact-settings"></a>
------------------------------------------------------------------------------------------------

为每位受信任的紧急联系人，选择自动授予访问权限前的等待时间，以及他们获得的访问级别。

### 用户访问权限 <a href="#user-access" id="user-access"></a>

* **查看**：当紧急访问请求被批准后，此用户将获得对您个人密码库中所有项目，包括登录项目的密码和附件的查看/读取权限。
* **接管**：当紧急访问请求被批准后，此用户必须创建一个主密码，以获得对您密码库的永久读取/写入权限。这将**替换**您之前的主密码，并移除之前设置的任何[两步登录方式](../two-step-login/setup-two-step-login/two-step-login-methods.md)。

### 等待时间 <a href="#wait-time" id="wait-time"></a>

当受信任的紧急联系人[请求访问权限](request-and-grant-emergency-access.md#id-1-the-trusted-emergency-contact-requests-access-to-the-account)时，您可以手动批准或拒绝。如果您未回应，访问权限将在您添加该特定受信任的紧急联系人时指定的等待时间后自动批准。最短等待时间为一天。

## 更改受信任的紧急联系人设置 <a href="#change-trusted-emergency-contact-settings" id="change-trusted-emergency-contact-settings"></a>

要更改紧急联系人的用户访问权限或等待时间：

1、前往**设置** → **紧急访问**。

2、选择用户的电子邮箱，这将打开其详细信息。

3、根据需要更新**用户访问权限**或**等待时间**。

4、选择**保存**。

{% hint style="success" %}
您也可以从**设置** → **紧急访问**中管理[待处理或已授权的紧急访问请求](request-and-grant-emergency-access.md#approve-or-deny-an-emergency-access-request)。
{% endhint %}

## 移除受信任的紧急联系人 <a href="#remove-a-trusted-emergency-contact" id="remove-a-trusted-emergency-contact"></a>

要从您的账户中移除受信任的紧急联系人：

1、前往**设置** → **紧急访问**。

2、选择 **≡**&#x83DC;单图标。

3、选择**移除**。

4、选择**是**以确认。

## 常见问题 <a href="#frequently-asked-questions" id="frequently-asked-questions"></a>

<details>

<summary>如果我的高级版功能被取消或由于支付失败而失效，紧急访问还能正常使用吗？</summary>

如果您的高级版功能被取消，您受信任的紧急联系人仍然可以请求并获取对您密码库的访问权限。但是，您将无法添加新的或编辑现有的受信任的紧急联系人。

</details>

<details>

<summary>当我的受信任的紧急联系人更改他们的账户电子邮箱地址时会发生什么？</summary>

作为受信任的紧急联系人的用户状态与一个唯一的 Bitwarden 账户 ID 相关联，这意味着如果受信任的紧急联系人[更改了他们的电子邮箱地址](../../password-manager/more/password-manager-faqs.md#q-how-do-i-change-my-email-address)，无需重新配置即可保持其紧急访问权限。同样地，如果紧急访问授予人更改了他们的电子邮箱地址，也无需重新配置。

</details>

<details>

<summary>当我的受信任的紧急联系人删除他们的账户时会发生什么？</summary>

如果一个受信任的紧急联系人创建了新的 Bitwarden 账户并[删除](../../plans-and-pricing/delete-an-account-or-organization.md)了旧账户，他们将被自动从受信任的紧急联系人中移除，并且必须重新[被邀请](add-and-manage-trusted-emergency-contacts.md#add-trusted-emergency-contacts)。

</details>

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 与您受信任的联系人分享[如何请求访问权限](request-and-grant-emergency-access.md#id-1-the-trusted-emergency-contact-requests-access-to-the-account)，以备不时之需。
* 了解如何[处理针对您账户的紧急访问请求](request-and-grant-emergency-access.md#approve-or-deny-an-emergency-access-request)。

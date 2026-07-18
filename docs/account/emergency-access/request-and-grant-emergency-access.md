# 请求 & 授予紧急访问权限

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/request-and-grant-emergency-access/)
{% endhint %}

作为受信任的紧急联系人，当账户持有人无法联系或[忘记主密码](../i-forgot-my-master-password.md)时，您可以请求[紧急访问](about-emergency-access.md)其 Bitwarden 密码库。请求发出后，账户持有人可[批准或拒绝访问权限](request-and-grant-emergency-access.md#approve-or-deny-an-emergency-access-request)，或在您配置的等待时间后自动获得访问权限。

## 获取账户的紧急访问权限 <a href="#get-emergency-access-to-an-account" id="get-emergency-access-to-an-account"></a>

受信任的紧急联系人获取紧急访问权限需经过三个步骤：

### 1. 受信任的紧急联系人请求访问账户 <a href="#id-1-the-trusted-emergency-contact-requests-access-to-the-account" id="id-1-the-trusted-emergency-contact-requests-access-to-the-account"></a>

首先，请求对此账户的访问权限：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、在**被指定为紧急联系人**部分，选择 **≡菜单图标**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6x38VldDaEOAqpuCQ4htRJ/7946735436fd16b660aad5d7969dba8d/2025-12-31_09-54-39.png?w=966&#x26;fm=avif" alt=""><figcaption><p>请求紧急访问</p></figcaption></figure></div>

3、从出现的确认信息中，选择**请求访问**。系统将向账户持有人发送一封电子邮件，告知他们有人请求访问其账户。

### 2. 受信任的紧急联系人的请求被批准或拒绝 <a href="#id-2-the-trusted-emergency-contacts-request-is-approved-or-denied" id="id-2-the-trusted-emergency-contacts-request-is-approved-or-denied"></a>

如果账户持有人无法登录，您的请求将在[等待时间](add-and-manage-trusted-emergency-contacts.md#wait-time)到期后自动获得批准。

但是，如果账户持有人在此之前能够登录，他们可以手动[批准或拒绝您的请求](request-and-grant-emergency-access.md#approve-or-deny-an-emergency-access-request)。

### 3. 若请求被批准，受信任的紧急联系人可通过查看密码库或更新主密码以登录账户来获得访问权限 <a href="#id-3-the-trusted-emergency-contact-gets-access" id="id-3-the-trusted-emergency-contact-gets-access"></a>

您的请求获得批准后，您可以访问该账户：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、在**被指定为紧急联系人**部分，选择 **≡菜单图标**，然后从下拉列表中选择为您分配的访问权限相对应的选项：

* **查看**：选择此选项将显示账户持有人的密码库项目。
* **接管**：选择此选项将允许您输入并确认账户持有人的新的主密码。选择**保存**，然后使用账户持有人的电子邮箱地址和新的主密码登录。

## 管理受信任的紧急联系人的访问权限 <a href="#manage-a-trusted-emergency-contacts-access" id="manage-a-trusted-emergency-contacts-access"></a>

作为账户持有人，您可以在三个环节控制受信任紧急联系人对您账户的访问权限：

* 将其从受信任紧急联系人列表中移除。
* 批准或拒绝其待处理的紧急访问请求。
* 撤销已授予的紧急访问权限。具体操作步骤取决于授予的是查看权限还是接管权限。

### 批准或拒绝紧急访问请求 <a href="#approve-or-deny-an-emergency-access-request" id="approve-or-deny-an-emergency-access-request"></a>

如果您在受信任的紧急联系人请求访问权限时仍能登录账户，您可以在等待时间到期之前批准或拒绝该请求。要批准或拒绝紧急访问请求：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、在**已信任的紧急联系人**部分，使用 **≡菜单图标**。

3、选择**批准**或**拒绝**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7iPFwb2NfsjeVywrwlZxSx/8ff35e1f5d8e2febf34089528ecea5ff/2025-12-31_09-55-14.png?w=966&#x26;fm=avif" alt=""><figcaption><p>批准或拒绝紧急访问</p></figcaption></figure></div>

您的请求获得批准后，您可以访问该账户：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、在**被指定为紧急联系人**部分，选择 **≡菜单图标**，然后从下拉列表中选择为您分配的访问权限相对应的选项：

* **查看**：选择此选项将显示账户持有人的密码库项目。
* **接管**：选择此选项将允许您输入并确认账户持有人的新的主密码。选择**保存**，然后使用账户持有人的电子邮箱地址和新的主密码登录。

{% hint style="info" %}
当您使用紧急访问**接管组织账户**时，有几点重要的注意事项：

* 如果组织已启用[主密码要求](../../admin-console/oversight-visibility/enterprise-policies.md#master-password-requirements)策略，在接管时更改主密码将强制执行此策略。
* 如果该账户不是组织[所有者](../../admin-console/manage-members/member-roles.md)，他们将自动从任何组织中移除。
* 如果该账户是组织所有者，他们不会被移除也不会失去其组织中的权限。因此，未对所有者执行的策略在接管后仍然不会被执行。
{% endhint %}

您可能需要撤销已信任的联系人对您的密码库的访问权限。移除某人先前被授予的对您帐户的紧急访问权限的步骤取决于此用户是被授予查看访问权限还是接管访问权限。

### 撤销查看访问权限 <a href="#revoke-view-access" id="revoke-view-access"></a>

当有人通过紧急访问被授予**查看**访问权限时，他们可以查看您的密码库项目，直到您撤销该权限。

要撤销通过紧急访问授予的某人的查看访问权限：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、在**已信任的紧急联系人**部分，选择具有有效紧急访问权限的账户旁的 **≡菜单图标**。

3、选择 **✘拒绝**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7dhQEDLZNKCwwspstJnhj0/543dd12da8a8d64952763027678cf15a/2025-12-31_09-55-33.png?w=966&#x26;fm=avif" alt=""><figcaption><p>拒绝紧急访问</p></figcaption></figure></div>

### 撤销接管访问权限 <a href="#revoke-takeover-access" id="revoke-takeover-access"></a>

当受信任的紧急联系人被授予并使用接管访问权限时，他们将会更改您账户的主密码。因此，移除他们的访问权限的唯一方法是：

1. 获取他们为您的账户创建的新主密码
2. 并使用新主密码登录[网页 App](../../password-manager/getting-started/getting-started-webvault.md)。
3. [更改您的主密码](../master-password.md#change-your-master-password)为一个他们不知道的密码。

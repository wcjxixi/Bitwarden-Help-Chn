# =添加 & 管理已信任的紧急联系人

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/add-and-manage-trusted-emergency-contacts/)
{% endhint %}

## 添加可信任的紧急联系人 <a href="#add-trusted-emergency-contacts" id="add-trusted-emergency-contacts"></a>

只有高级版用户，包括付费组织（家庭版、团队版或企业版）的成员才能指定可信任的紧急联系人。在同一 [Bitwarden 服务器](../../security/server-geographies.md)上的任何免费或高级 Bitwarden 账户都可以被指定为可信任的紧急联系人。您拥有的可信任的紧急联系人的数量没有限制。

设置紧急访问分为 3 个步骤：

1. 您**邀请**其他用户成为您的可信任的紧急联系人。
2. 他们**接受**邀请。
3. 您**确认**他们作为您的可信任的紧急联系人。

{% tabs %}
{% tab title="邀请" %}
作为想要对您的密码库授予紧急访问的人，请邀请信任的紧急联系人：

1、在 Bitwarden 网页 App 中，转到**设置** → **紧急访问**。

2、选择 **➕添加紧急联系人**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3gb0Zm4K935RUmzjd62eJq/a3930a8381fe1205b655e7a7bb0eca47/2025-12-31_09-50-39.png?w=966&#x26;fm=avif" alt=""><figcaption><p>紧急访问页面</p></figcaption></figure></div>

3、输入您信任的紧急联系人的**电子邮箱**。可信任的紧急联系人必须拥有 Bitwarden 账户（免费版或高级版），以及必须位于同一[服务器地理位置](../../security/server-geographies.md)：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2IEldGj87MY2IMDQpty6Vr/f0e9750c278663903be46f4a5d5a4f8c/2025-12-31_09-52-02.png?w=964&#x26;fm=avif" alt=""><figcaption><p>邀请紧急联系人</p></figcaption></figure></div>

4、为可信任的紧急联系人设置**用户访问权限**级别：**查看**或**接管**。

5、设置**等待时间**。这是您的可信任的紧急联系人请求账户访问权限后，必须等待多长时间才能获得此访问权限，除非您提前[手动批准请求](add-and-manage-trusted-emergency-contacts.md#use-emergency-access)。最短等待时间为一天。

6、选择**保存**以发送邀请。

您的可信任的紧急联系人**必须现在接受此邀请**。

{% hint style="info" %}
成为可信任的紧急联系人的邀请的有效期只有 5 天。
{% endhint %}
{% endtab %}

{% tab title="接受" %}
作为想要接收他人密码库的紧急访问权限的人，请接受发出的电子邮件邀请：

1、在收到的电子邮件邀请中，选择电子邮件中的**成为紧急联系人**按钮，以在浏览器中打开紧急访问页面：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1S7YBbeECgEdl1v9r4E5BU/37c6c4207cb8c6df7f69a63ea12751fd/Screenshot_2024-02-27_at_9.23.46_AM.png?w=590&#x26;fm=avif" alt=""><figcaption><p>紧急访问邀请</p></figcaption></figure></div>

2、登录您的 Bitwarden 账户以接受邀请。如果您还没有 Bitwarden 账户，则需要创建一个。

接受邀请后，邀请的用户**必须确认您的接受**，然后您才能[发起访问请求](add-and-manage-trusted-emergency-contacts.md#use-emergency-access)。
{% endtab %}

{% tab title="确认" %}
作为想要对您的密码库授予紧急访问权限的人，请确认您新的信任紧急联系人：

1、在 Bitwarden 网页 App 中，导航至**设置** → **紧急访问**。

2、在**信任的紧急联系人**部分，已邀请的用户应该显示了一个 `需要确认` 状态卡。使用 **≡**&#x83DC;单，从下拉菜单中选择**确认**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/jEvLxG2nmFJRnlTbcpwRO/891f14df501abae6c1e93ce57a527ec4/2025-12-31_09-53-35.png?w=966&#x26;fm=avif" alt=""><figcaption><p>确认紧急联系人</p></figcaption></figure></div>

为确保加密密钥的完整性，在完成确认前，请与受让人核实显示的指纹短语。
{% endtab %}
{% endtabs %}

## 使用紧急访问 <a href="#use-emergency-access" id="use-emergency-access"></a>

[设置](add-and-manage-trusted-emergency-contacts.md#add-trusted-emergency-contacts)完成后，信任的紧急联系人可以对您的账户**请求访问权限**。如果您仍然可以登录到您的账户，您可以在指定的等待时间内**批准或拒绝请求**。当您不再希望可信任的联系人能够**访问您的账户**时，您可以**撤销他们的紧急访问权限**。

{% tabs %}
{% tab title="请求访问权限" %}
要对某个账户请求访问权限：

1、在 Bitwarden 网页 App 中，导航至**设置** → **紧急访问**。

2、在**被指定为紧急联系人**部分，选择 **≡菜单图标**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6x38VldDaEOAqpuCQ4htRJ/7946735436fd16b660aad5d7969dba8d/2025-12-31_09-54-39.png?w=966&#x26;fm=avif" alt=""><figcaption><p>请求紧急访问</p></figcaption></figure></div>

3、从出现的确认信息中，选择**请求访问**。系统将向账户持有人发送一封电子邮件，告知他们有人请求访问其账户。

在指定的等待时间之后，**或者**当授予人手动批准您的紧急访问请求时，您将获得对授予人密码库的访问权限。
{% endtab %}

{% tab title="批准或拒绝请求" %}
您可以在配置的等待时间到期之前手动批准或拒绝紧急访问请求。要批准或拒绝紧急访问请求：

1、在 Bitwarden 网页 App 中，前往**设置** → **紧急访问**。

2、在**已信任的紧急联系人**部分，使用 **≡菜单图标**。

3、选择**批准**或**拒绝**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7iPFwb2NfsjeVywrwlZxSx/8ff35e1f5d8e2febf34089528ecea5ff/2025-12-31_09-55-14.png?w=966&#x26;fm=avif" alt=""><figcaption><p>批准或拒绝紧急访问</p></figcaption></figure></div>
{% endtab %}

{% tab title="访问账户" %}
在您的请求获得批准或等待时间结束后，要访问授予人的密码库：

1、在 Bitwarden 网页 App 中，前往**设置** → **紧急访问**。

2、在**被指定为紧急联系人**部分，选择 **≡菜单图标**，然后从下拉列表中选择为您分配的访问权限相对应的选项：

* **查看**：选择此选项将显示授予人的密码库项目。
* **接管**：选择此选项将允许您输入并确认授予人账户新的主密码。选择**保存**，然后使用授予人的电子邮箱地址和新的主密码登录。

{% hint style="info" %}
当您使用紧急访问**接管组织账户**时，有几点重要的注意事项：

* 如果组织已启用[主密码要求](../../admin-console/oversight-visibility/enterprise-policies.md#master-password-requirements)策略，在接管时更改主密码将强制执行此策略。
* 如果该账户不是组织[所有者](../../admin-console/manage-members/member-roles.md)，他们将自动从任何组织中移除。
* 如果该账户是组织所有者，他们不会被移除也不会失去其组织中的权限。因此，未对所有者执行的策略在接管后仍然不会被执行。
{% endhint %}
{% endtab %}

{% tab title="撤销访问权限" %}
您可能需要撤销已信任的联系人对您的密码库的访问权限。移除某人先前被授予的对您帐户的紧急访问权限的步骤取决于此用户是被授予查看访问权限还是接管访问权限。

### 查看访问权限 <a href="#view-access" id="view-access"></a>

当有人通过紧急访问被授予**查看**访问权限时，他们可以查看您的密码库项目，直到他们的访问权限被手动撤销。

要撤销通过紧急访问授予的某人的查看访问权限：

1、转到**设置** → **紧急访问**。

2、选择与他们的电子邮箱位于同一行的 **≡菜单图标**。

3、选择 **✘拒绝**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7dhQEDLZNKCwwspstJnhj0/543dd12da8a8d64952763027678cf15a/2025-12-31_09-55-33.png?w=966&#x26;fm=avif" alt=""><figcaption><p>拒绝紧急访问</p></figcaption></figure></div>

### 接管访问权限 <a href="#takeover-access" id="takeover-access"></a>

当信任的紧急联系人被授予并使用**接管**访问权限时，他们会更改您账户的主密码。因此，移除他们的访问权限的唯一方法是：

1. 获取他们为您的账户创建的新主密码并使用它登录[网页密码库](../../password-manager/getting-started/getting-started-webvault.md)。
2. [更改您的主密码](../master-password.md#change-your-master-password)为一个他们不知道的密码。
{% endtab %}
{% endtabs %}

## 管理信任的紧急联系人 <a href="#manage-trusted-emergency-contacts" id="manage-trusted-emergency-contacts"></a>

您可以随时更新您的信任的紧急访问联系人。要更改紧急访问联系人的用户访问权限或等待时间：

1. 转到**设置** → **紧急访问**。
2. 点击用户的电子邮箱，这将打开他们的详细信息。
3. 根据需要，更新**用户访问权限**或**等待时间**。
4. 选择**保存**。

要移除某位已信任的紧急联系人：

1. 转到**设置** → **紧急访问**。
2. 选择 **≡菜单图标**。
3. 选择**移除**。
4. 选择**是**以确认。

将您账户的访问权限授予给某一位信任的联系人后，，您可以[撤销他们的访问权限](add-and-manage-trusted-emergency-contacts.md#use-emergency-access)。



## 常见问题 <a href="#frequently-asked-questions" id="frequently-asked-questions"></a>

<details>

<summary>当我的已信任的紧急联系人更改他们的账户电子邮箱地址时会发生什么？</summary>

作为已信任的紧急联系人的用户状态与一个唯一的 Bitwarden 账户 ID 相关联，这意味着如果已信任的紧急联系人[更改了他们的电子邮箱地址](../../password-manager/more/password-manager-faqs.md#q-how-do-i-change-my-email-address)，无需重新配置即可保持其紧急访问权限。同样地，如果紧急访问授予人更改了他们的电子邮箱地址，也无需重新配置。

</details>

<details>

<summary>当我的已信任的紧急联系人删除他们的账户时会发生什么？</summary>

如果一个已信任的紧急联系人创建了新的 Bitwarden 账户并[删除](../../plans-and-pricing/delete-an-account-or-organization.md)了旧账户，他们将被自动从已信任的紧急联系人中移除，并且必须重新[被邀请](add-and-manage-trusted-emergency-contacts.md#add-trusted-emergency-contacts)。

</details>

<details>

<summary>如果我的高级版功能被取消或由于支付失败而失效，紧急访问还能正常使用吗？</summary>

如果您的高级版功能被取消，您已信任的紧急联系人仍然可以请求并获取对您密码库的访问权限。但是，您将无法添加新的或编辑现有的信任的紧急联系人。

</details>

2

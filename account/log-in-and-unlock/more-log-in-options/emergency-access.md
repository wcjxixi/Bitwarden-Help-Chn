# 使用紧急访问登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/emergency-access/)
{% endhint %}

紧急访问使用户能够指定和管理[可信任的紧急联系人](emergency-access.md#trusted-emergency-contacts)，这些联系人可以通过可配置的权限级别请求访问其密码库。

{% hint style="info" %}
只有高级用户，包括付费组织（家庭、团队或企业）的成员才能指定可信任的紧急联系人，但任何拥有 Bitwarden 账户的人都可以被指定为可信任的紧急联系人。

**如果您的高级功能因付款方式失败而被取消或失效，**&#x60A8;的可信紧急联系人仍然可以请求并获得对您的密码库的访问。但是，您将无法添加新的可信紧急联系人或编辑现有的可信紧急联系人。
{% endhint %}

## 设置紧急访问 <a href="#setup-emergency-access" id="setup-emergency-access"></a>

设置紧急访问分为 3 个步骤：您必须首先**邀请**用户成为受信任的紧急联系人，然后他们必须**接受**邀请，最后您必须**确认**他们的接受：

{% tabs %}
{% tab title="邀请" %}
作为想要对您的密码库授予紧急访问权限的人，请邀请值得信赖的紧急联系人：

1、在 Bitwarden 网页 App 中，导航至**设置** → **紧急访问**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gb0Zm4K935RUmzjd62eJq/d5ba9e65a6f5905fa39c8a601f207a0a/2024-12-02_11-29-43.png?_a=DAJCwlWIZAAB" %}
紧急访问页面
{% endembed %}

2、选择 **🞤添加紧急联系人**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7vRyx6gsjm4H9ej6mw4mTv/6750adcecb6c00d740b61b85e7b20baf/2024-12-02_11-35-11.png?_a=DAJCwlWIZAAB" %}
添加紧急联系人
{% endembed %}

3、输入您的可信紧急联系人的**电子邮箱**地址。可信紧急联系人必须拥有他们自己的 Bitwarden 账户，但不需要是高级会员。

{% embed url="https://bitwarden.com/assets/2IEldGj87MY2IMDQpty6Vr/1a8841c005dfc0a6baddcde9bf9e0476/Emergency_access.png?w=750&fm=avif&q=80" %}
紧急访问对话框
{% endembed %}

4、为可信紧急联系人设置**用户访问权限**级别（[仅查看或接管](emergency-access.md#user-access)）。

5、为密码库访问设置**等待时间**。等待时间决定了在发起紧急访问请求后，可信紧急联系人必须等待多长时间才能访问您的密码库。

6、选择**保存**按钮以发送邀请。

您的可信紧急联系人**必须马上接受邀请**。

{% hint style="info" %}
紧急联系人邀请的有效期只有 5 天。
{% endhint %}
{% endtab %}

{% tab title="接受" %}
作为想要接收他人密码库的紧急访问权限的人，请接受发出的电子邮件邀请：

1、在收到的电子邮件邀请中，选择电子邮件中的**成为紧急联系人**按钮，以在浏览器中打开紧急访问页面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1S7YBbeECgEdl1v9r4E5BU/37c6c4207cb8c6df7f69a63ea12751fd/Screenshot_2024-02-27_at_9.23.46_AM.png?_a=DAJAUVWIZAAB" %}
紧急访问邀请
{% endembed %}

2、登录您的 Bitwarden 账户以接受邀请。如果您还没有 Bitwarden 账户，则需要创建一个。

接受邀请后，邀请的用户**必须确认您的接受**，然后您才能[发起访问请求](emergency-access.md#use-emergency-access)。
{% endtab %}

{% tab title="确认" %}
作为想要对您的密码库授予紧急访问权限的人，请确认您新的可信任紧急联系人：

1、在 Bitwarden 网页 App 中，导航至**设置** → **紧急访问**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gb0Zm4K935RUmzjd62eJq/d5ba9e65a6f5905fa39c8a601f207a0a/2024-12-02_11-29-43.png?_a=DAJCwlWIZAAB" %}
紧急访问页面
{% endembed %}

2、在**可信紧急联系人**部分，受邀请的用户应该显示一个 `需要确认` 状态卡。使用 **≡**&#x83DC;单，从下拉菜单中选择**确认**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/jEvLxG2nmFJRnlTbcpwRO/8b564a834758b744b5a2f86114393302/2024-12-02_11-38-53.png?_a=DAJCwlWIZAAB" %}
确认紧急联系人
{% endembed %}

为确保加密密钥的完整性，在完成确认前，请与受让人核实显示的指纹短语。
{% endtab %}
{% endtabs %}

## 使用紧急访问 <a href="#use-emergency-access" id="use-emergency-access"></a>

设置完成后，以下部分将帮助您以受信任的紧急联系人的身份**发起访问**或以被指定的受信任紧急联系人的身份**管理访问**：

{% tabs %}
{% tab title="发起访问" %}
## 发起紧急访问 <a href="#initiate-emergency-access" id="initiate-emergency-access"></a>

完成以下步骤以发起紧急访问请求：

1、在 Bitwarden 网页 App 中，导航至**设置** → **紧急访问**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gb0Zm4K935RUmzjd62eJq/d5ba9e65a6f5905fa39c8a601f207a0a/2024-12-02_11-29-43.png?_a=DAJCwlWIZAAB" %}
紧急访问页面
{% endembed %}

2、在**指定为紧急联系人**部分，选择 ≡菜单图标然后选择**请求访问**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6x38VldDaEOAqpuCQ4htRJ/25f126a7ae7cc932562fe62e7aac7bc2/2024-12-02_11-40-35.png?_a=DAJCwlWIZAAB" %}
请求紧急访问
{% endembed %}

3、在确认窗口中，选择**请求访问**按钮。

在配置的等待时间之后，或当授予人手动批准（请参阅**管理访问**选项卡）紧急访问请求时，您将获得对授予人密码库的访问权限。

### 访问授予人的密码库 <a href="#access-grantees-vault" id="access-grantees-vault"></a>

您的请求获得批准后，完成以下步骤以访问授予人的密码库：

1、在 Bitwarden 网页 App 中，导航至**设置** → **紧急访问**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gb0Zm4K935RUmzjd62eJq/d5ba9e65a6f5905fa39c8a601f207a0a/2024-12-02_11-29-43.png?_a=DAJCwlWIZAAB" %}
紧急访问页面
{% endembed %}

2、在**指定为紧急联系人**部分，选择 **≡**&#x83DC;单图标，然后从下拉列表中选择与[分配给您的访问权限](emergency-access.md#user-access)相对应的选项：

* **查看** - 选择此选项将在此屏幕上显示授予人的密码库项目。
* **接管** - 选择此选项将打开接管对话框。输入并确认授予者账户的新主密码。保存后，输入授予人的电子邮箱地址和新的主密码，和往常一样登录 Bitwarden。
{% endtab %}

{% tab title="管理访问" %}
## 批准或拒绝紧急访问 <a href="#manually-approve-emergency-access" id="manually-approve-emergency-access"></a>

您可以在配置的等待时间到期之前手动批准或拒绝紧急访问请求。完成以下步骤以批准或拒绝紧急访问：

1、在 Bitwarden 网页 App 中，导航至**设置** → **紧急访问**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gb0Zm4K935RUmzjd62eJq/d5ba9e65a6f5905fa39c8a601f207a0a/2024-12-02_11-29-43.png?_a=DAJCwlWIZAAB" %}
紧急访问页面
{% endembed %}

2、在**可信紧急联系人**部分，使用 **≡**&#x83DC;单图标然后选择**批准**或**拒绝**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7iPFwb2NfsjeVywrwlZxSx/e7986fffd8b304d4bf8ae6734caba206/2024-12-02_11-42-09.png?_a=DAJCwlWIZAAB" %}
批准或拒绝紧急访问
{% endembed %}

## 撤销访问 <a href="#revoking-access" id="revoking-access"></a>

使用紧急访问后重新获得对您的密码库的独占访问权限的步骤取决于授予的[访问级别](emergency-access.md#user-access)：

### 撤销查看权限 <a href="#revoke-view-access" id="revoke-view-access"></a>

他们获得批准后，直到他们的访问权限被手动撤销，获得**查看**访问权限的可信紧急联系人在获得批准后，将能够查看您的密码库项目，直到他们的访问权限被手动撤销。要手动撤销访问，请使用 **≡**&#x83DC;单选择 **✘拒绝**访问：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7dhQEDLZNKCwwspstJnhj0/148c5963b9b0e81c0e5e1e0803c45812/2024-12-02_11-44-01.png?_a=DAJCwlWIZAAB" %}
撤销紧急访问
{% endembed %}

### 撤销接管 <a href="#revoke-a-takeover" id="revoke-a-takeover"></a>

获得**接管**访问权限的可信紧急联系人使用后，将为您的账户创建一个新的主密码。因此，撤销访问权限的唯一方法包括：

1. 获取他们为您的账户创建的新主密码并使用它登录[网页密码库](../../../getting-started/getting-started-webvault.md)。
2. [更改您的主密码](../your-master-password.md#change-your-master-password)为一个他们不知道的密码。
{% endtab %}
{% endtabs %}

## 更多信息 <a href="#more-information" id="more-information"></a>

### 可信紧急联系人 <a href="#trusted-emergency-contacts" id="trusted-emergency-contacts"></a>

紧急访问依赖于 Bitwarden 内的公钥交换，因此可信紧急联系人必须是现有的 Bitwarden 用户，或者在接受邀请前会被提示创建一个 Bitwarden 账户。可信紧急联系人不需要必须是高级用户。

作为受信任的紧急联系人的用户状态，其与唯一的 Bitwarden 账户 ID 相关联，这意味着，如果受让人[更改了他的电子邮箱地址](../../../your-vault/general-faqs.md)，则无需重新配置即可维持其紧急访问权限。

如果受让人创建了一个**新的 Bitwarden 账户**，并[删除](../../../plans-and-pricing/delete-an-account-or-organization.md)了已被指定为受信任的紧急联系人的旧账户，他们将自动从授予人的名单中移除，必须[重新邀请](emergency-access.md#setup-emergency-access)。

一个用户可以拥有的可信紧急联系人的数量没有限制。

{% hint style="success" %}
作为授予人，您可以在配置的等待时间到期之前的任何时间[拒绝](emergency-access.md#use-emergency-access)紧急访问请求。
{% endhint %}

### 用户访问控制 <a href="#user-access" id="user-access"></a>

可以向可信紧急联系人授予以下用户访问级别之一：

* **查看**：授予紧急访问请求后，将授予该用户对您的个人密码库中所有项目的查看/读取访问权限。
* **接管**：授予紧急访问请求后，该用户可以创建一个主密码，用于对您的密码库进行永久读/写访问（这将**取代**您之前的主密码）。接管将禁用该账户已启用的任何[两步登录方式](../../two-step-login/setup-guides/two-step-login-methods.md)。

{% hint style="success" %}
作为授予人，您可以随时撤消受让人的**查看**访问权限。
{% endhint %}

**当您是一个组织的成员时**，您将自动从其不是[所有者](../../../admin-console/manage-members/member-roles.md)的任何组织中被移除。所有者不会从他们的组织中被移除或失去权限，但是，如果启用，将在接管时执行[主密码策略](../../../admin-console/oversight-visibility/enterprise-policies.md#master-password)。通常，不对所有者执行的策略（例如，[两步登录](../../../admin-console/oversight-visibility/enterprise-policies.md#two-step-login)）将不会在接管时执行。

### 工作原理 <a href="#how-it-works" id="how-it-works"></a>

{% hint style="info" %}
以下信息引用了加密密钥名称和过程，这些内容在[散列、密钥派生和加密](../../../security/bitwarden-security-whitepaper.md#hashing-key-derivation-and-encryption)章节中有介绍。请先阅读该章节。
{% endhint %}

紧急访问使用公共密钥交换和加密/解密来允许用户授予[可信紧急联系人](emergency-access.md#trusted-emergency-contacts)在零知识环境下[访问密码库数据](emergency-access.md#user-access)的权限：

1. 一个 Bitwarden 用户（授予人）邀请另一个 Bitwarden 用户成为其可信紧急联系人（受让人）。邀请（有效期仅 5 天）指定了用户访问级别，并包含对受让人 **RSA 公钥**的请求。
2. 受让人将通过电子邮件收到邀请通知，并接受邀请成为可信紧急联系人。接受邀请后，受让人的 **RSA 公钥**将与用户记录一起存储。
3. 授予人将通过电子邮件收到接受通知，并确认受让人成为其可信紧急联系人。确认后，授予人的**用户对称密钥**将使用受让人的 **RSA 公钥**进行加密，并与邀请一起存储。受让人将收到确认通知。
4. 发生紧急情况时，受让人可以提交紧急访问请求以要求进入授予人的密码库。
5. 授予人将通过电子邮件收到请求通知。授予人可以随时手动批准请求，否则请求将受到授予人指定的等待时间的约束。当请求被批准或等待时间结束后，经**公钥加密的用户对称密钥**将交付给受让人，并使用受让人的 **RSA 私钥**进行解密。\
   或者，授予人可以拒绝请求，这将阻止受让人获得下一步所述的访问权限。拒绝请求不会使受让人不再是受信任的紧急联系人，也不会阻止他们在未来提出访问请求。
6. 根据指定的用户访问级别，受让人可以：
   * 获得对授予人密码库中的项目的查看/读取权限（**查看**）。
   * 被要求为授予人的密码库创建一个新的主密码（**接管**）。

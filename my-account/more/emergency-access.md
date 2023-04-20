# 紧急访问

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/emergency-access/)
{% endhint %}

紧急访问使用户能够指定和管理可信任的紧急联系人，这些联系人可以通过可配置的权限级别请求访问其密码库。

{% hint style="info" %}
只有高级用户，包括付费组织（家庭、团队或企业）的成员才能指定可信任的紧急联系人，但任何拥有 Bitwarden 账户的人都可以被指定为可信任的紧急联系人。

**如果您的高级功能因付款方式失败而被取消或失效，**您的可信紧急联系人仍然可以请求并获得对您的密码库的访问。但是，您将无法添加新的或编辑现有的可信紧急联系人。
{% endhint %}

## 它是如何工作的 <a href="#how-it-works" id="how-it-works"></a>

紧急访问使用公共密钥交换和加密/解密来允许用户授予[可信紧急联系人](emergency-access.md#trusted-emergency-contacts)在零知识环境下[访问密码库数据](emergency-access.md#user-access)的权限：

1. 一个 Bitwarden 用户（_授予人_）[邀请另一个 Bitwarden 用户](emergency-access.md#setup-emergency-access)成为其可信紧急联系人（_受让人_）。邀请（有效期仅 5 天）指定了[用户访问级别](emergency-access.md#user-access)，并包含对受让人的公共密钥的请求。
2. 受让人将通过电子邮件收到邀请通知，并[接受邀请](emergency-access.md#setup-emergency-access)成为可信紧急联系人。接受邀请后，受让人的公钥将与邀请一起存储。
3. 授予人将通过电子邮件收到接受通知，并[确认受让人](emergency-access.md#setup-emergency-access)成为其可信紧急联系人。确认后，授予人的主密钥将使用受让人的公钥进行加密，并在加密后存储。受让人将收到确认通知。
4. 发生紧急情况时，受让人可以[提交紧急访问请求](emergency-access.md#use-emergency-access)以要求进入授予人的密码库。
5. 授予人将通过电子邮件收到请求通知。授予人可以随时[手动批准请求](emergency-access.md#use-emergency-access)，否则请求将受到授予人指定的等待时间的约束。当请求被批准或等待时间结束后，经公钥加密的主密钥将交付给受让人，并使用受让人的私钥进行解密。
6. 根据指定的[用户访问级别](emergency-access.md#user-access)，受让人可以：
   * 获得对授予人密码库中的项目的查看/读取权限（**查看**）。
   * 提示为授予人的密码库创建新的主密码（**接管**）。

### 可信紧急联系人 <a href="#trusted-emergency-contacts" id="trusted-emergency-contacts"></a>

紧急访问依赖于 Bitwarden 内的公钥交换，因此可信紧急联系人必须是现有的 Bitwarden 用户，或者在接受邀请前会被提示创建一个 Bitwarden 账户。可信紧急联系人不需要必须是高级用户。

作为受信任的紧急联系人的用户状态，其与唯一的 Bitwarden 账户 ID 相关联，这意味着，如果受让人[更改了他的电子邮件地址](../../password-manager/more/password-manager-faqs.md)，则无需重新配置即可维持其紧急访问权限。如果受让人创建了一个**新的 Bitwarden 账户**，并[删除](../plans-and-pricing/delete-an-account-or-organization.md)了已被指定为受信任的紧急联系人的旧账户，他们将自动从授予人的名单中移除，必须[重新邀请](emergency-access.md#setup-emergency-access)。

一个用户可以拥有的可信紧急联系人的数量没有限制。

{% hint style="success" %}
作为授予人，您可以在配置的等待时间到期之前的任何时间[拒绝](emergency-access.md#use-emergency-access)紧急访问请求。
{% endhint %}

### 用户访问控制 <a href="#user-access" id="user-access"></a>

可以为可信紧急联系人授予以下用户访问级别之一：

* **查看**：授予紧急访问请求后，将授予该用户对您的个人密码库中所有项目的查看/读取访问权限。
* **接管**：授予紧急访问请求后，该用户可以创建一个主密码，用于对您的密码库进行永久读/写访问（这将**取代**您之前的主密码）。接管将禁用该帐户已启用的任何[两步登录方式](../two-step-login/two-step-login-methods.md)。

{% hint style="success" %}
作为授予人，您可以随时撤消受让人的**查看**访问权限。
{% endhint %}

**当您是一个组织的成员时**，您将自动从其不是[所有者](../../admin-console/user-management/user-types-and-access-control.md)的任何组织中被移除。所有者不会从他们的组织中被移除或失去权限，但是，如果启用，将在接管时执行[主密码策略](../../admin-console/organization-basics/enterprise-policies.md#master-password)。通常，不对所有者执行的策略（例如，[两步登录](../../admin-console/organization-basics/enterprise-policies.md#two-step-login)）将不会在接管时执行。

## 设置紧急访问 <a href="#setup-emergency-access" id="setup-emergency-access"></a>

以下内容将引导您设置紧急访问，分开为您是要**授予访问**您的密码库还是**接收访问**其他用户的密码库：

{% tabs %}
{% tab title="授予访问" %}
### 邀请可信紧急联系人 <a href="#invite-a-trusted-emergency-contact" id="invite-a-trusted-emergency-contact"></a>

请完成以下步骤为您的密码库邀请可信紧急联系人：

1、登录到网[页密码库](../../password-manager/getting-started/getting-started-webvault.md)。

2、从顶部导航栏中选择**设置**。

3、从左侧设置菜单中选择**紧急访问**。

4、选择 **🞤添加紧急联系人**按钮。在邀请紧急联系人窗口中：

{% embed url="https://bitwarden.com/help/images/features/emergency-access/ea-invite.png" %}
添加紧急联系人
{% endembed %}

* 输入您的可信紧急联系人的**电子邮件**地址。可信紧急联系人必须拥有他们自己的 Bitwarden 账户，但不需要是高级会员。
* 为可信紧急联系人设置**用户访问权限**级别（[仅查看或接管](emergency-access.md#user-access)）。
* 为密码库访问设置**等待时间**。等待时间决定了在启动紧急访问请求后，可信紧急联系人必须等待多长时间才能访问密码库。

5、选择**保存**按钮以发送邀请。您的可信紧急联系人现在必须接受邀请（请参阅**接受访问**选项卡）。

{% hint style="info" %}
紧急联系人邀请的有效期只有 5 天。
{% endhint %}

### 确认已接受的邀请 <a href="#confirm-an-accepted-invitation" id="confirm-an-accepted-invitation"></a>

在您信任的紧急联系人接受邀请后，请完成以下步骤进行确认：

1、登录到[网页密码库](../../password-manager/getting-started/getting-started-webvault.md)。

2、从顶部导航栏中选择**设置**。

3、从左侧设置菜单中选择**紧急访问**。

在**可信紧急联系人**部分，被邀请的用户应该显示一个`已接受`状态卡。

4、将鼠标悬停在用户上方，选择齿轮图标，然后从下拉菜单中选择**确认**。

{% embed url="https://bitwarden.com/help/images/features/emergency-access/ea-confirm.png" %}

为确保加密密钥的完整性，在完成确认前，请与受让人核实显示的指纹短语。
{% endtab %}

{% tab title="接受访问" %}
### 接受邀请 <a href="#accept-an-invitation" id="accept-an-invitation"></a>

完成以下步骤来接受邀请成为可信紧急联系人：

1、在收到的电子邮件邀请中，选择电子邮件中的**成为紧急联系人**按钮，以在浏览器中打开紧急访问接受页面：

{% embed url="https://bitwarden.com/help/images/features/emergency-access/ea-invitation.png" %}
紧急访问邀请：
{% endembed %}

2、登录您的 Bitwarden 帐户以接受邀请。如果您还没有 Bitwarden 帐户，则需要创建一个。

接受邀请后，邀请用户必须确认您的接受，然后您才能[发起访问请求](emergency-access.md#use-emergency-access)（请参阅**授予访问**选项卡）。
{% endtab %}
{% endtabs %}

## 使用紧急访问 <a href="#use-emergency-access" id="use-emergency-access"></a>

{% tabs %}
{% tab title="发起访问" %}
### 发起紧急访问 <a href="#initiate-emergency-access" id="initiate-emergency-access"></a>

完成以下步骤以发起紧急访问请求：

1、登录到[网页密码](../../password-manager/getting-started/getting-started-webvault.md)。

2、从顶部导航栏中选择**设置**。

3、从左侧设置菜单中选择**紧急访问**。

4、在**指定为紧急联系人**部分，选择您要访问其密码库的授予人。

5、在请求访问窗口中，选择**请求访问**按钮。

{% embed url="https://bitwarden.com/help/images/features/emergency-access/ea-request.png" %}
申请访问
{% endembed %}

在配置的等待时间之后，或当授予人手动批准（请参阅**管理访问**选项卡）紧急访问请求时，您将获得对授予人密码库的访问权限。

### 访问授予人的密码库 <a href="#access-grantees-vault" id="access-grantees-vault"></a>

您的请求获得批准后，完成以下步骤以访问授予人的密码库：

1. 登录到[网页密码库](../../password-manager/getting-started/getting-started-webvault.md)
2. 从顶部导航栏中选择**设置**
3. 从左侧设置菜单中选择**紧急访问**
4. 在**指定为紧急联系人**部分，悬停在您希望访问其密码库的授予人上，然后选择齿轮图标。
5. 从下拉列表中选择与[分配给您的访问权限](emergency-access.md#user-access)相对应的选项：
   * **查看**：选择此选项将在此屏幕上显示授予人的密码库项目。
   * **接管**：选择此选项将打开接管对话框。输入并确认授予者帐户的新主密码。保存后，输入授予人的电子邮件地址和创建的主密码，和往常一样登录 Bitwarden。
{% endtab %}

{% tab title="管理访问" %}
### 批准或拒绝紧急访问 <a href="#manually-approve-emergency-access" id="manually-approve-emergency-access"></a>

您可以在配置的等待时间到期之前手动批准或拒绝紧急访问请求。完成以下步骤以批准或拒绝紧急访问：

1. 登录到[网页密码库](../../password-manager/getting-started/getting-started-webvault.md)。
2. 从顶部导航栏中选择**设置**。
3. 从左侧设置菜单中选择**紧急访问**。
4. 悬停在具有`紧急访问已发起`状态卡的用户上方，选择齿轮图标。
5. 从齿轮下拉列表中，选择**批准**或**拒绝**。

### 撤销访问 <a href="#revoking-access" id="revoking-access"></a>

使用紧急访问后重新获得对您的密码库的独占访问权限的步骤取决于授予的[访问级别](emergency-access.md#user-access)：

#### 撤销查看权限 <a href="#revoke-view-access" id="revoke-view-access"></a>

他们获得批准后，直到他们的访问权限被手动撤销，获得**查看**访问权限的可信紧急联系人将能够查看您的密码库项目。要手动撤销访问，请使用 **⚙️齿轮**下拉菜单 **✘拒绝**访问：

{% embed url="https://bitwarden.com/help/images/features/emergency-access/ea-revoke.png" %}
撤销紧急访问
{% endembed %}

#### 撤销接管 <a href="#revoke-a-takeover" id="revoke-a-takeover"></a>

获得接管访问权限的可信紧急联系人使用后，将为您的帐户创建一个新的主密码。因此，撤销访问权限的唯一方法包括：

1. 获取他们为您的帐户创建的新主密码并使用它登录[网页密码库](../../password-manager/getting-started/getting-started-webvault.md)。
2. [更改您的主密码](../log-in-and-unlock/your-master-password.md#change-your-master-password)为一个他们不知道的密码。
{% endtab %}
{% endtabs %}

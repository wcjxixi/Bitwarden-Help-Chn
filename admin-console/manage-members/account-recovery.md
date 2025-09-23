# 账户恢复

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery/)
{% endhint %}

{% hint style="info" %}
账户恢复适用于**企业组织**。与 SSO 登录一样，账户恢复不适用于[经典 2019 企业组织](../../plans-and-pricing/updates-to-bitwarden-plans-2019-2020.md)计划。
{% endhint %}

## 什么是账户恢复？ <a href="#what-is-account-recovery" id="what-is-account-recovery"></a>

账户恢复（以前叫「管理员密码重置」）允许[指定的管理员](account-recovery.md#permissions)恢复企业组织用户账户以及在员工忘记[主密码](../../account/log-in-and-unlock/your-master-password.md)时恢复访问权限。通过[启用账户恢复策略](account-recovery.md#activate-account-recovery)为组织激活账户恢复。

个人用户必须被注册（通过[自行注册](account-recovery.md#self-enroll-in-password-reset)或使用[自动注册策略选项](account-recovery.md#automatic-enrollment)）才有资格进行账户恢复，因为注册会触发密钥交换，以确保恢复的安全。

**账户恢复不会绕过两步登录或 SSO 登录。**&#x5982;果为账户启用了[两步登录方式](../../account/two-step-login/setup-guides/two-step-login-methods.md)，或者如果您的组织[要求 SSO 身份验证](../manage-shared-items/enterprise-policies.md#single-sign-on-authentication)，您在密码重置后仍将需要使用该方式访问您的密码库。

### 加密 <a href="#encryption" id="encryption"></a>

当组织的成员[注册](account-recovery.md#automatic-enrollment)账户恢复时，该用户的[加密密钥](../../security/encryption/encryption-key-rotation.md)将使用组织的公钥进行加密。其结果将作为**账户恢复密钥**存储。

当执行恢复操作时：

1. 使用组织对称密钥解密组织私钥。
2. 使用已解密的组织私钥解密用户的**账户恢复密钥**，从而得到用户的[加密密钥](../../security/encryption/encryption-key-rotation.md)。
3. 用户的加密密钥和主密码散列被替换为新的加密密钥和新的主密码散列，这些散列源自新的主密码。
4. 使用组织的公钥加密用户新的加密密钥，使用新的密钥替换之前的**账户恢复密钥**。

任何人，包括执行重置的管理员，都**无法**看到旧的主密码。

### 权限 <a href="#permissions" id="permissions"></a>

账户恢复可由[所有者、管理员和允许的自定义用户](member-roles-and-permissions.md)执行。账户恢复使用分级权限结构来确定谁可以重置谁的主密码：

* 任何所有者、管理员或允许的自定义用户都可以重置用户、经理或自定义用户的主密码。
* 只有管​​理员或所有者可以重置管理员的主密码。
* 只有所有者可以重置其他所有者的主密码。

### 事件日志 <a href="#event-logging" id="event-logging"></a>

以下情况会记录[事件](../reporting/event-logs.md)：

* 使用账户恢复重置了主密码。
* 用户更新了通过账户恢复颁发的密码。
* 用户注册了账户恢复。
* 用户撤销了账户恢复。

## 激活账户恢复 <a href="#activate-account-recovery" id="activate-account-recovery"></a>

要为您的企业组织激活账户恢复，请使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

在管理控制台中，导航至**设置** → **策略**并开启**账户恢复管理**策略。您必须至少是组织管理员才能激活此策略：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2flohk6BsRKvazjztwvzsJ/4258307d845b33cd9f765388ca6bfea6/2024-12-03_14-24-58.png?_a=DAJCwlWIZAAB" %}
设置策略
{% endembed %}

用户需要[自行注册](account-recovery.md#self-enroll-in-password-reset)或[自动注册](account-recovery.md#automatic-enrollment)账户恢复，然后才能重置其主密码。

### 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

启用自动注册策略选项将在新用户[加入组织的邀请被接受后](user-management.md#accept)自动注册新用户的账户恢复功能。并且会阻止他们[撤销](account-recovery.md#withdraw-enrollment)账户恢复。

已经在组织中的用户不会被注册账户恢复，需要他们[自行注册](account-recovery.md#self-enroll-in-password-reset)。

{% hint style="success" %}
如果您为组织成员使用自动注册账户恢复，我们**强烈建议您通知他们这一功能**。很多 Bitwarden 组织用户在他们的个人密码库中存储私人凭据，应该让他们知道账户恢复将允许管理员访问他们的个人密码库。
{% endhint %}

### 自行注册账户恢复 <a href="#self-enroll-in-account-recovery" id="self-enroll-in-account-recovery"></a>

要注册账户恢复，在密码库视图种选择您的组织旁边的 **≡选项**菜单，然后选择**注册账户恢复**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4ape19S5L7lf0tAAEyInGR/87fadad707f8c7acb5894e94e758c6c3/2024-12-03_15-33-13.png?_a=DAJCwlWIZAAB" %}
注册账户恢复
{% endembed %}

如果您愿意，您可以在多个组织中注册账户恢复。

### 撤销注册 <a href="#withdraw-enrollment" id="withdraw-enrollment"></a>

注册后，您可以从用于注册的同一下拉菜单中**撤销**账户恢复：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4GR176lad9pre4sZN3rA35/642bdef55248fb84ddb24fc316875b11/2024-12-03_15-34-30.png?_a=DAJCwlWIZAAB" %}
撤销账户恢复
{% endembed %}

已启用[自动注册](account-recovery.md#automatic-enrollment)策略选项的组织中的用户将**不允许撤销**账户恢复。此外，手动更改您的主密码或[轮换您的加密密钥](../../security/encryption/encryption-key-rotation.md)**不会**使您撤销账户恢复。

## 恢复账户 <a href="#recover-an-account" id="recover-an-account"></a>

{% hint style="info" %}
您必须是[所有者、管理员或允许的自定义用户](account-recovery.md#permissions)才能重置主密码。检查本文的[权限](account-recovery.md#permissions)章节以了解您可以重置谁的主密码。
{% endhint %}

要重置企业组织成员的主密码：

1、在管理控制台中，导航至**成员**。

2、对于要重置其主密码的成员，请使用 **≡选项**菜单选择 **🔑恢复账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/26oD8iqDY15SNJXCJlQE71/22e66b7e11a56d99c13ac41a1236c4e7/2024-12-03_15-35-51.png?_a=DAJCwlWIZAAB" %}
恢复账户
{% endembed %}

3、在恢复账户窗口中，为用户创建一个**新密码**。如果您的组织启用了[主密码策略](../manage-shared-items/enterprise-policies.md#master-password)，您将需要创建一个满足实施要求的密码（例如，最少 8 个字符，包含数字）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/28qKke9XJLj6nTZJjg4mK4/7b1c2c5cb2c139bf08ea4c5f65c9a02a/2024-12-03_15-38-52.png?_a=DAJCwlWIZAAB" %}
创建一个新的密码
{% endembed %}

复制新的主密码并使用安全的通讯方式联系用户，例如使用 [Bitwarden Send](../../bitwarden-send/create-a-send.md)。

4、选择**保存**以执行账户恢复。这样做会将用户从当前会话中注销。某些客户端应用程序（比如移动 App）上的活动会话可能会保持活动长达一小时。

### 恢复后 <a href="#after-a-recovery" id="after-a-recovery"></a>

当您的主密码被重置时，您将收到一封来自 Bitwarden 的电子邮件，通知您这一点。收到此电子邮件后，请联系您的组织管理员，通过诸如 [Bitwarden Send](../../bitwarden-send/create-a-send.md) 等安全渠道获取您的新主密码。

当您使用新的主密码重新获得对密码库的访问权限后，系统将提示您再次更新主密码：

{% embed url="https://bitwarden.com/help/images/organizations/pwreset-temporary.png" %}
更新您的主密码
{% endembed %}

因为主密码应该是**强大**且**易记**的，并且**只有您自己**知道，所以重置后您会被要求更新您的主密码。

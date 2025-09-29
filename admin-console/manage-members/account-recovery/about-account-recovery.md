# 关于账户恢复

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery/)
{% endhint %}

{% hint style="info" %}
账户恢复适用于**企业组织**。与 SSO 登录一样，账户恢复不适用于[经典 2019 企业组织](../../../plans-and-pricing/updates-to-bitwarden-plans-2019-2020.md)计划。
{% endhint %}

## 什么是账户恢复？ <a href="#what-is-account-recovery" id="what-is-account-recovery"></a>

账户恢复（以前叫「管理员密码重置」）允许[指定的管理员](about-account-recovery.md#permissions)恢复企业组织用户账户以及在员工忘记[主密码](../../../account/log-in-and-unlock/your-master-password.md)时恢复访问权限。通过[启用账户恢复策略](about-account-recovery.md#activate-account-recovery)为组织激活账户恢复。

个人用户必须被注册（通过[自行注册](about-account-recovery.md#self-enroll-in-password-reset)或使用[自动注册策略选项](about-account-recovery.md#automatic-enrollment)）才有资格进行账户恢复，因为注册会触发密钥交换，以确保恢复的安全。

**账户恢复不会绕过两步登录或 SSO 登录。**&#x5982;果为账户启用了[两步登录方式](../../../account/two-step-login/setup-guides/two-step-login-methods.md)，或者如果您的组织[要求 SSO 身份验证](../../oversight-visibility/enterprise-policies.md#single-sign-on-authentication)，您在密码重置后仍将需要使用该方式访问您的密码库。

### 加密 <a href="#encryption" id="encryption"></a>

当组织的成员[注册](about-account-recovery.md#automatic-enrollment)账户恢复时，该用户的[加密密钥](../../../security/encryption/encryption-key-rotation.md)将使用组织的公钥进行加密。其结果将作为**账户恢复密钥**存储。

当执行恢复操作时：

1. 使用组织对称密钥解密组织私钥。
2. 使用已解密的组织私钥解密用户的**账户恢复密钥**，从而得到用户的[加密密钥](../../../security/encryption/encryption-key-rotation.md)。
3. 用户的加密密钥和主密码散列被替换为新的加密密钥和新的主密码散列，这些散列源自新的主密码。
4. 使用组织的公钥加密用户新的加密密钥，使用新的密钥替换之前的**账户恢复密钥**。

任何人，包括执行重置的管理员，都**无法**看到旧的主密码。

### 权限 <a href="#permissions" id="permissions"></a>

账户恢复可由[所有者、管理员和允许的自定义用户](../member-roles.md)执行。账户恢复使用分级权限结构来确定谁可以重置谁的主密码：

* 任何所有者、管理员或允许的自定义用户都可以重置用户、经理或自定义用户的主密码。
* 只有管​​理员或所有者可以重置管理员的主密码。
* 只有所有者可以重置其他所有者的主密码。

### 事件日志 <a href="#event-logging" id="event-logging"></a>

以下情况会记录[事件](../../oversight-visibility/event-logging/event-logs.md)：

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

用户需要[自行注册](about-account-recovery.md#self-enroll-in-password-reset)或[自动注册](about-account-recovery.md#automatic-enrollment)账户恢复，然后才能重置其主密码。

### &#x20;<a href="#automatic-enrollment" id="automatic-enrollment"></a>

## &#x20;<a href="#recover-an-account" id="recover-an-account"></a>

### 恢复后 <a href="#after-a-recovery" id="after-a-recovery"></a>

当您的主密码被重置时，您将收到一封来自 Bitwarden 的电子邮件，通知您这一点。收到此电子邮件后，请联系您的组织管理员，通过诸如 [Bitwarden Send](../../../bitwarden-send/create-a-send.md) 等安全渠道获取您的新主密码。

当您使用新的主密码重新获得对密码库的访问权限后，系统将提示您再次更新主密码：

{% embed url="https://bitwarden.com/help/images/organizations/pwreset-temporary.png" %}
更新您的主密码
{% endembed %}

因为主密码应该是**强大**且**易记**的，并且**只有您自己**知道，所以重置后您会被要求更新您的主密码。

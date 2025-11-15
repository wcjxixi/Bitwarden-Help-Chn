# 关于账户恢复

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery/)
{% endhint %}

{% hint style="info" %}
账户恢复适用于**企业组织**。
{% endhint %}

账户恢复功能允许所有者、管理员和某些自定义角色成员在成员忘记主密码或丢失可信设备时恢复成员账户。账户恢复：

* 可通过开启账户恢复管理策略为组织激活账户恢复。
* 要求成员通过自动注册或自助注册的方式注册，以获得账户恢复资格。注册会触发密钥交换，从而确保账户恢复的安全性。
* **不会绕过成员的两步登录或 SSO**。如果为账户启用了[两步登录方式](../../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)，或者如果组织[要求 SSO 身份验证](../../oversight-visibility/enterprise-policies.md#single-sign-on-authentication)，则成员在恢复后仍需使用这些方法访问他们的账户。

## 更多信息 <a href="#more-information" id="more-information"></a>

### 谁可以恢复账户 <a href="#who-can-recover-accounts" id="who-can-recover-accounts"></a>

账户恢复可由[所有者、管理员和允许的自定义用户](../member-roles.md)执行。账户恢复使用分级权限结构来确定谁可以重置谁的主密码，这意味着：

* 任何所有者、管理员或包含**管理账户恢复**的自定义角色都可以重置用户或自定义角色成员的主密码。
* 只有管​​理员或所有者可以重置管理员的主密码。
* 只有所有者可以重置其他所有者的主密码。

### 事件日志 <a href="#event-logging" id="event-logging"></a>

以下情况会记录[事件](../../oversight-visibility/event-logging/event-logs.md)：

* 使用账户恢复重置了主密码。
* 用户更新了通过账户恢复颁发的密码。
* 用户注册了账户恢复。
* 用户撤销了账户恢复。

### 工作原理 <a href="#how-it-works" id="how-it-works"></a>

当组织的成员注册账户恢复时，该用户的[加密密钥](../../../security/encryption/encryption-key-rotation.md)将使用组织的公钥进行加密。其结果将作为**账户恢复密钥**存储。

当执行恢复操作时：

1. 使用组织对称密钥解密组织私钥。
2. 使用已解密的组织私钥解密用户的**账户恢复密钥**，从而得到用户的[加密密钥](../../../security/encryption/encryption-key-rotation.md)。
3. 用户的加密密钥和主密码散列被替换为新的加密密钥和新的主密码散列，这些散列源自新的主密码。
4. 使用组织的公钥加密用户新的加密密钥，使用新的密钥替换之前的**账户恢复密钥**。

任何人，包括执行重置的管理员，都**无法**看到旧的主密码。

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 通过开启[账户恢复管理策略](../../oversight-visibility/enterprise-policies.md#account-recovery-administration)来设置账户恢复。
* 如果用户在策略开启前加入或您没有开启自动注册，请指导用户[注册账户恢复](account-recovery-enrollment.md)。
* 了解如何[恢复已注册成员的账户](recover-a-member-account.md)。
* 向成员提供[账户恢复后的操作说明](my-account-was-recovered.md)。

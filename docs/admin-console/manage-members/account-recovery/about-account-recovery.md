# 关于账户恢复

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery/)
{% endhint %}

{% hint style="info" %}
账户恢复适用于**企业版组织**。是比个人管理的两步登录[恢复代码](../../../account/two-step-login/recovery-codes.md)更为强大的替代方案。
{% endhint %}

丢失[主密码](../../../account/master-password.md)、[两步登录方式](../../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)或[受信任信设备](../../login-with-sso/trusted-devices/about-trusted-devices.md)，会导致成员无法访问其密码库。账户恢复使管理员能够重置成员凭据并恢复其访问权限。[设置好账户恢复](account-recovery-enrollment.md)且成员注册后，重新获得账户访问权限需要两个步骤：

* 管理员重置该成员的主密码、两步登录方式，或两者同时重置。Bitwarden 随后会向该成员的账户邮箱发送一个恢复链接。
* 成员收到邮件中的恢复链接后，即可重置其主密码和/或设置新的两步登录方式。

账户恢复仅影响在 Bitwarden 内配置的凭据。它**不会绕过 SSO** 或您在 IdP 处配置的任何双重身份验证。如果您的组织[要求 SSO 身份验证](../../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)，成员在恢复后仍需通过这些方式访问其账户。

{% hint style="info" %}
账户恢复不会恢复已删除的账户。[删除账户](../revoke-remove/delete-member-accounts.md)是永久性的，无法撤消。
{% endhint %}

## 谁可以恢复账户 <a href="#who-can-recover-accounts" id="who-can-recover-accounts"></a>

[所有者、管理员以及具有**管理账户恢复**权限的自定义角色成员](../member-roles.md)可以发起账户恢复。谁可以重置谁的主密码或两步登录方式取决于他们的角色：

* 任何所有者、管理员或包含**管理账户恢复**的自定义角色都可以重置用户或自定义角色成员的账户。
* 只有管​​理员或所有者可以重置管理员的账户。
* 只有所有者可以重置其他所有者的账户。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

当组织的成员注册账户恢复时，该用户的[加密密钥](../../../security/encryption/encryption-key-rotation.md)将使用组织的公钥进行加密。其结果将作为**账户恢复密钥**存储。

当执行恢复操作时：

1. 使用组织对称密钥解密组织私钥。
2. 使用已解密的组织私钥解密用户的**账户恢复密钥**，从而得到用户的[加密密钥](../../../security/encryption/encryption-key-rotation.md)。
3. 用户的加密密钥和主密码散列被替换为新的加密密钥和新的主密码散列，这些散列源自新的主密码。
4. 使用组织的公钥加密用户新的加密密钥，使用新的密钥替换之前的**账户恢复密钥**。

任何人，包括执行重置的管理员，都**无法**看到旧的主密码。

## 事件日志 <a href="#event-logging" id="event-logging"></a>

以下情况会记录[事件](../../oversight-visibility/event-logging/event-logs.md)：

* 用户使用账户恢复重置了主密码。
* 用户更新了通过账户恢复颁发的密码。
* 用户注册了账户恢复。
* 用户撤销了账户恢复。

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 通过启用[账户恢复管理策略](../../oversight-visibility/enterprise-policies.md#account-recovery-administration)来设置账户恢复。
* 如果用户在策略开启前加入，或您没有启用自动注册，请指导用户[注册账户恢复](account-recovery-enrollment.md)。
* 了解如何[恢复已注册成员的账户](recover-a-member-account.md)。
* 向成员提供[账户恢复后的操作说明](my-account-was-recovered.md)。

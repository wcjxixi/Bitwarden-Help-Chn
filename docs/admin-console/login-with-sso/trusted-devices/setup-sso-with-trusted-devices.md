# 设置受信任设备 SSO

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/setup-sso-with-trusted-devices/)
{% endhint %}

本文档将引导您将[受信任设备 SSO](./) 添加到您的组织。要完成以下步骤，您必须是组织所有者或管理员：

1、登录到 Bitwarden 网页 App，然后使用产品切换器打开管理控制台：

{% embed url="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&fm=avif" %}
产品切换器
{% endembed %}

2、从导航中选择**设置** → **策略**。

3、在策略页面上，激活受信任设备所需的以下策略：

* **单一组织**策略。
* **要求单点登录身份验证**策略。
* **账户恢复管理**策略。
* 账户恢复管理策略的**为新用户启用自动注册**选项。

{% hint style="info" %}
如果您没有事先激活这些策略，它们将在您激活**受信任设备**成员解密选项时自动激活。但是，如果任何账户未启用账户恢复，则他们需要[自行注册](../../manage-members/account-recovery/about-account-recovery.md#self-enroll-in-password-reset)，然后使用受信任设备[管理员批准](approve-a-trusted-device.md)。启用[账户恢复](../../manage-members/account-recovery/about-account-recovery.md)的用户必须在账户恢复后至少登录一次才能完全完成账户恢复流程。
{% endhint %}

4、从导航中选择**设置** → **单点登录**。如果您尚未设置 SSO，请按照我们的[ SAML 2.0](../sso-guides/generic-saml.md) 或 [OIDC 实施](../sso-guides/generic-oidc.md)指南之一获取帮助。

5、在「成员解密选项」部分中选择**受信任设备**选项。

激活后，用户即可开始使用受信任设备解密其密码库。

加入使用受信任设备 SSO 的组织时，管理员和所有者将被提示创建主密码以实现冗余和故障转移，但普通用户角色的成员无法设置主密码。

{% hint style="danger" %}
从受信任设备 SSO 迁移到其他成员解密选项之前，请注意以下几点：：

* 从受信任设备 SSO 迁移到主密码解密时，任何没有主密码的组织成员在下次登录时都会被提示创建一个主密码。
* **不支持**从受信任设备 SSO 迁移到 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

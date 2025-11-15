# 设置受信任设备 SSO

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/setup-sso-with-trusted-devices/)
{% endhint %}

本文档将引导您将[受信任设备 SSO](./) 添加到您的组织。要完成以下步骤，您必须是组织所有者或管理员：

1、登录到 Bitwarden 网页 App，然后使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/919a2c332ed6a53707f80ac3f734e0a8/2024-06-04_10-13-18.png?_a=DAJAUVWIZAAB" %}
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

4、从导航中选择**设置** → **单点登录**。如果您尚未设置 SSO，请按照我们的[ SAML 2.0](../saml-2.0-configuration.md) 或 [OIDC 实施](../oidc-configuration.md)指南之一获取帮助。

5、在「成员解密选项」部分中选择**受信任设备**选项。

激活后，用户可以开始使用受信任设备解密其密码库。

如果您期望让没有主密码的成员**只能**使用受信任设备，请指导用户从组织邀请中选择**登录** → **企业 SSO** 以启动 JIT 配置。管理员/所有者仍应使用**创建账户**选项，以便他们拥有主密码，以用于冗余和故障转移目的。

{% hint style="danger" %}
从受信任设备 SSO 迁移到其他成员解密选项之前，请注意以下几点：：

* 从受信任设备 SSO 迁移到主密码解密时，任何没有主密码的组织成员在下次登录时都会被提示创建一个主密码。
* **不支持**从受信任设备 SSO 迁移到 Key Connector。
{% endhint %}

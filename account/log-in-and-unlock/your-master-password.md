# 主密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/master-password/)
{% endhint %}

主密码是访问密码库的主要方式。您的主密码非常重要：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记密码的强度。

[2023.3.0 版本](../../release-notes.md)发布后，主密码要求必须至少包含 12 个字符。

{% hint style="success" %}
担心忘记您的主密码吗？这里有一些建议：

* **设置主密码提示**。如果您需要提醒，可以在登录屏界面请求主密码提示电子邮件。确保使用只有您自己能理解的提示。
* **指定一个**[**可信紧急联系人**](more-log-in-options/emergency-access.md)。具有高级访问权限的用户可以在紧急情况下将密码库的访问权限授予朋友或家庭成员。
{% endhint %}

## 更改主密码 <a href="#change-your-master-password" id="change-your-master-password"></a>

如果您知道当前的主密码，您可以通过[网页密码库](../../getting-started/getting-started-webvault.md)更改它：

{% hint style="info" %}
如果您不知道主密码，请参阅[我忘记了主密码](i-forgot-my-master-password.md)**。**
{% endhint %}

1、在网页 App 中，从导航栏选择**设置** → **安全**。

2、选择**主密码**选项卡：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2Svv0PwlH9i7SSK73dlv9A/5ff2708bb08164626baf1f03d3854b24/2024-12-02_10-24-14.png?_a=DAJCwlWIZAAB" %}
主密码设置
{% endembed %}

3、输入您的**当前主密码**。

4、输入并确认您的**新主密码**。

5、如果您想在提交主密码之前通过 HIBP 检查您的主密码，请选中**检查密码的已知数据泄露**（[了解更多](../../your-vault/vault-health-reports.md#data-breach-report-individual-vaults-only)）复选框。要运行此报告，您的主密码的哈希值将发送到 HIBP，并与存储的公开哈希值进行比较。 Bitwarden 永远不会暴露您的主密码本身。

{% hint style="warning" %}
除非您完全了解其后果和所需的后续步骤，否则请不要选中**同时轮换账户加密密钥**复选框。[了解更多](../../security/account-encryption-key.md)。
{% endhint %}

6、选择**更改主密码**按钮。

更改主密码将会自动注销网页密码库会话，并要求您使用新的主密码重新登录。当前已登录的 App 可能保持活动状态长达一小时，但最终也会要求您使用新的主密码重新登录。

## 我忘记了主密码 <a href="#i-forgot-my-master-password" id="i-forgot-my-master-password"></a>

了解如果您[忘记了主密码](i-forgot-my-master-password.md)该怎么做。

## 附加登录选项 <a href="#additional-login-options" id="additional-login-options"></a>

您的主密码是设置 Bitwarden 账户的必要条件。根据您或您的组织与 Bitwarden 交互的方式，可以使用其他选项来访问您的 Bitwarden 账户。

| 方式              | 描述                                                                                                                                                                                            |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 使用设备登录          | 设备登录是一种利用受信任的辅助设备向 Bitwarden 发送身份验证请求。在[此处](more-log-in-options/log-in-with-device.md)了解有关设备登录的更多信息。                                                                                          |
| 使用 SSO 登录       | Bitwarden 用户如果属于一个使用单点登录 (SSO) 的组织，可以利用现有的身份提供程序进行登录，提供程序将对用户进行身份验证。在[此处](../../login-with-sso/about-login-with-sso.md)了解有关 SSO 登录的更多信息。                                                      |
| 使用通行密钥登录        | 通行密钥可用作使用主密码和电子邮件登录 Bitwarden 的替代方案，并且某些通行密钥还可用于密码库加密和解密。在[此处](more-log-in-options/log-in-with-passkeys.md)了解更多信息。                                                                            |
| 使用生物识别和 PIN 码解锁 | 使用生物识别或 PIN 解锁并不是一种替代登录方法，但是，此功能可以允许您使用系统生物识别或 PIN（而不是主密码）访问已锁定的帐户。了解有关[使用生物识别解锁](more-unlock-options/unlocking-with-biometrics.md)和[使用 PIN 解锁](more-unlock-options/unlock-with-pin.md)的更多信息。 |

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

现在您已经创建了**好记**且**强大**的主密码，我们建议：

* [通过两步登录进一步保护您的密码库](../two-step-login/setup-guides/two-step-login-methods.md)
* [启用紧急访问](more-log-in-options/emergency-access.md)（需要高级会员）

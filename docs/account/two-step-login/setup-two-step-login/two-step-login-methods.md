# 两步登录方式

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login/)
{% endhint %}

{% hint style="success" %}
**2025 年 03 月 04 日**：为提高账户安全性，Bitwarden 将开始要求**未使用两步登录的用户**在[从新设备登录账户或清除浏览器 cookie 后](../../log-in-and-unlock/new-device-protection.md)进行额外的验证。您可能已收到了相关电子邮件和产品通知。

输入 Bitwarden 主密码后，系统会提示您输入发送到您账户电子邮箱的一次性验证码。您也可以：

* 按照本页面上的任何指南设置两步登录。
* 从**设置** → **我的账户**页面的**危险区域**部分选择退出该功能（**停用新设备登录保护**）。
{% endhint %}

使用两步登录（也称为双因素验证或 2FA）来保护您的 Bitwarden 密码库，通过在您登录时要求使用辅助设备进行身份验证，防止恶意行为者访问您的数据（即使他们发现了您的主密码）。如果您不熟悉 2FA 的基础知识，请查看我们的[现场指南](../field-guide-for-two-step-login.md)。

{% embed url="https://vimeo.com/1060246387" %}

有许多不同的方式可用于两步登录。您可以根据自己的喜好使用多种方式。重要的是，任何形式的两步登录都需要激活，才能确保您的账户受到保护。

## 适用于个人的两步登录 <a href="#two-step-login-for-individuals" id="two-step-login-for-individuals"></a>

任何人都可以通过访问网页 App，然后选择**设置** → **安全** → **两步登录**，以在他们的个人账户上设置两步登录。请至少设置以下一种两步登录方式。每一种方式都有设置说明：

| 方式                                                                                                | 设置说明                                        | 订阅要求  |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------- | ----- |
| FIDO2 WebAuthn 凭据（如 YubiKey 和 Google Titan 等硬件钥匙）                                                 | [设置说明](two-step-login-via-fido.md)          | 全部免费  |
| 验证器 App（如 [Bitwarden Authenticator](../../../bitwarden-authenticator/bitwarden-authenticator.md)） | [设置说明](two-step-login-via-authenticator.md) | 全部免费  |
| 电子邮箱                                                                                              | [设置说明](two-step-login-via-email.md)         | 全部免费  |
| Duo Security 的 Duo Push、短信、电话和安全钥匙                                                                | [设置说明](two-step-login-via-duo.md)           | 要求高级版 |
| YubiKey OTP（任何 4/5 系列设备或 YubiKey NEO/NFC）                                                         | [设置说明](two-step-login-via-yubikey.md)       | 要求高级版 |

## 适用于团队和企业的两步登录 <a href="#two-step-login-for-teams-and-enterprise" id="two-step-login-for-teams-and-enterprise"></a>

尽管每个用户可以使用上面图示中的方式在其账户上激活两步登录，但团队和企业组织还有其他选项：

| 方式                                 | 设置说明                              | 订阅要求      |
| ---------------------------------- | --------------------------------- | --------- |
| Duo Security 的 Duo Push、短信、电话和安全钥匙 | [设置说明](two-step-login-via-duo.md) | 要求团队版或企业版 |

此外，企业组织可以通过[策略](../../../admin-console/oversight-visibility/enterprise-policies.md#require-two-step-login)要求两步登录，并且当使用单点登录 (SSO) 时，可以使用您的身份提供程序在 Bitwarden 之外实现相同的保护。

## 使用多个方式 <a href="#using-multiple-methods" id="using-multiple-methods"></a>

您可以选择启用多个两步登录方式。当您使用多个已启用的方式登录 Bitwarden 时，将按照以下优先顺序提示您使用最高优先级的两步登录方式：

1. Duo（组织）
2. FIDO2 WebAuthn
3. YubiKey
4. Duo（个人）
5. 验证器 App
6. 电子邮箱

{% hint style="warning" %}
如果您[使用 SSO 登录](../../log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)，则不建议使用电子邮箱方式的两步登录，因为使用多个方式会导致错误。可以考虑改为设置[免费的验证器方式的两步登录](two-step-login-via-authenticator.md)。
{% endhint %}

不过，任何方式都可以使用。通过选择**使用其他两步登录方式**按钮，以使用低优先级方式进行验证：

{% tabs %}
{% tab title="网页 App" %}
{% embed url="https://bitwarden.com/assets/6pZaDONKwdhsCVDxz4fEoP/16a2053bf3a08a0449a0db1410fa752d/2025-02-28_08-56-53.png?w=654&fm=avif" %}
使用其他两步登录方式
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
{% embed url="https://bitwarden.com/assets/X0JAzFLcwRr4smlsMYCf7/0aa1f3c0cf56dd8e062e1e89fd99e43d/2025-03-17_10-55-29.png?w=999&fm=avif" %}
使用其他两步登录方式
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
{% embed url="https://bitwarden.com/assets/2iyAQzp5BrmXPbIqKp9aB5/6b7bc9726ade6a5ef79cf4877e5c30ec/2025-03-18_09-30-31.png?w=710&fm=avif" %}
使用其他两步登录方式
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
{% embed url="https://bitwarden.com/assets/36novNT7xJ8ZJSoG66MQXg/774092e3a3361e3a92d3bd84786b260e/setup-two-step-login-1.png?w=850&fm=avif" %}
使用其他两步登录方式
{% endembed %}
{% endtab %}
{% endtabs %}

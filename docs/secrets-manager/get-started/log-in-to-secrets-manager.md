# 登录 Secrets Manager

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/log-in-to-secrets-manager/)
{% endhint %}

您用于登录 Password Manager 的端到端零知识加密的 Bitwarden 账户与您用于登录 Secrets Manager 的账户相同。

{% hint style="success" %}
本文与登录 Secrets Manager 网页密码库相关。[Secrets Manager CLI](../developer-tools/secrets-manager-cli.md) 主要用于编写机密注入到您的应用程序和基础设施中的脚本，需要使用[访问令牌](../your-secrets/access-tokens.md)登录。
{% endhint %}

## 主密码 <a href="#master-password" id="master-password"></a>

主密码是访问您的 Bitwarden 账户的主要方法。您的主密码非常重要：

* **好记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记你的主密码！**
* **强大**：使用一个更长、更复杂且不太常见的主密码是保护您账户的最佳方式。Bitwarden 提供了一个免费的密码强度测试工具来测试您正在考虑使用的密码的强度。

{% hint style="success" %}
担心忘记您的主密码吗？这里有一些建议：

* **设置主密码提示**。如果您需要提醒，可以在登录屏界面请求主密码提示电子邮件。确保使用只有您自己能理解的提示。
* **指定一个**[**可信紧急联系人**](../../account/log-in-and-unlock/more-log-in-options/emergency-access.md)。具有高级访问权限的用户可以在紧急情况下将密码库的访问权限授予朋友或家人。
{% endhint %}

了解[如何更改您的主密码](../../account/log-in-and-unlock/your-master-password.md#change-your-master-password)，或者如果您[忘记了主密码](../../account/log-in-and-unlock/i-forgot-my-master-password.md)该怎么做。

## 两步登录 <a href="#two-step-login" id="two-step-login"></a>

使用两步登录（也称为双因素验证或 2FA）来保护您的 Bitwarden 账户，通过在您登录时要求使用辅助设备进行身份验证，防止恶意行为者访问您的数据（即使他们发现了您的主密码）。

两步登录有很多不同的方式，从专用的身份验证器应用程序到硬件安全钥匙。无论您选择什么，Bitwarden 都强烈建议您使用两步登录来保护您的密码库。

### 免费方式 <a href="#free-methods" id="free-methods"></a>

Bitwarden 提供多种免费的两步登录方式，包括：

| 方式                                                                                                                                | 设置说明                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| 通过验证器 App（例如 [Authy](https://authy.com/) 或 [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=zh-Hans)） | 点[这里](../../account/two-step-login/setup-two-step-login/two-step-login-via-authenticator.md) |
| 通过电子邮件                                                                                                                            | 点[这里](../../account/two-step-login/setup-two-step-login/two-step-login-via-email.md)         |
| 通过 FIDO2 WebAuthn 验证器                                                                                                             | 点[这里](../../account/two-step-login/setup-two-step-login/two-step-login-via-fido.md)          |

### 高级方式 <a href="#premium-methods" id="premium-methods"></a>

对于高级用户（包括付费组织的成员），Bitwarden 提供了几种高级的两步登录方式：

| 方式                                        | 设置说明                                                                                   |
| ----------------------------------------- | -------------------------------------------------------------------------------------- |
| 通过具有 Duo Push、短信、电话和安全密钥的 Duo Security    | 点[这里](../../account/two-step-login/setup-two-step-login/two-step-login-via-duo.md)     |
| 通过 YubiKey（任何 4/5 系列或 YubiKey NEO/NFC 设备） | 点[这里](../../account/two-step-login/setup-two-step-login/two-step-login-via-yubikey.md) |

## 设备登录 <a href="#log-in-with-device" id="log-in-with-device"></a>

您知道吗？您可以使用辅助设备而不是您的主密码登录 Bitwarden 网页 App。设备登录是一种无密码的身份验证方法，通过向您当前登录的任何特定设备发送身份验证请求以供批准，而无需输入您的主密码。[了解更多](../../account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)。

## 单点登录 <a href="#single-sign-on" id="single-sign-on"></a>

如果您的组织使用 [SSO 登录](../../admin-console/login-with-sso/about-sso.md)，您还可以[使用联合 SSO 凭据](../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)访问您的 Bitwarden 网页 App。

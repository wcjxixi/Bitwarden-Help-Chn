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

| 方式                                                                                                | 设置说明                                        | 订阅要求   |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------- | ------ |
| FIDO2 WebAuthn 凭据（如 YubiKey 和 Google Titan 等硬件钥匙）                                                 | [设置说明](two-step-login-via-fido.md)          | 全部免费   |
| 验证器 App（如 [Bitwarden Authenticator](../../../bitwarden-authenticator/bitwarden-authenticator.md)） | [设置说明](two-step-login-via-authenticator.md) | 全部免费   |
| 电子邮箱                                                                                              | [设置说明](two-step-login-via-email.md)         | 全部免费   |
| Duo Security 的 Duo Push、短信、电话和安全钥匙                                                                | [设置说明](two-step-login-via-duo.md)           | 要求高级会员 |
| YubiKey OTP（任何 4/5 系列设备或 YubiKey NEO/NFC）                                                         | [设置说明](two-step-login-via-yubikey.md)       | 要求高级会员 |

## 适用于团队和企业的两步登录 <a href="#two-step-login-for-teams-and-enterprise" id="two-step-login-for-teams-and-enterprise"></a>

尽管每个用户可以使用上面图示中的方式在其账户上激活两步登录，但团队和企业组织还有其他选项：

| 方式                                 | 设置说明                              | 订阅要求    |
| ---------------------------------- | --------------------------------- | ------- |
| Duo Security 的 Duo Push、短信、电话和安全钥匙 | [设置说明](two-step-login-via-duo.md) | 要求团队或企业 |

此外，企业组织可以通过[策略](../../../admin-console/manage-shared-items/enterprise-policies.md#require-two-step-login)要求两步登录，并且当使用单点登录 (SSO) 时，可以使用您的身份提供程序在 Bitwarden 之外实现相同的保护。

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

{% embed url="https://bitwarden.com/_gatsby/image/ffa607d1f0a31f518a607ea92e53034c/21be4ea96e73c75751773d1e39571e10/twostep-diffmethod.webp?eu=8d8e54e0b5c1fed25e3aa7d56d706261e73d53acfb5767d56e60b0a74ea899d52da51f00229c7eb77f6b0b8f85e942b333c42c664debd48891b44ea7eb30ad5d52800fea61b47507052e90abb6f50f436e951f5ea287c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bbdd0b4626a91b0cb58bbbeadda6fb9d4ad29513584932a70751a1a0ae529bdf1e106253f7a130937cfae0dc16296e33a4d64755d5e51f4787e970ab8286483f9aff80b8f272ea5f096656ec69df9&a=w%3D453%26h%3D334%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A14%3A58.081Z" %}
使用其他两步登录方式
{% endembed %}

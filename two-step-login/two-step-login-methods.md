# 两步登录方式

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login/)
{% endhint %}

使用两步登录（也称为双因素验证或 2FA）来保护您的 Bitwarden 密码库，通过在您登录时要求使用辅助设备进行身份验证，防止恶意行为者访问您的数据（即使他们发现了您的主密码）。如果您不熟悉 2FA 的基础知识，请查看我们的[现场指南](field-guide-for-two-step-login.md)。

两步登录有许多不同的方式，从专用的验证器应用程序到硬件安全钥匙。无论你选择什么，Bitwarden 强烈建议你使用两步登录来保护你的密码库。事实上，我们认为这是非常重要的，所以我们很乐意为您[免费](two-step-login-methods.md#free-methods)提供一些方式。

## 用于个人的两步登录 <a href="#two-step-login-for-individuals" id="two-step-login-for-individuals"></a>

您可以通过[网页密码库](../getting-started/getting-started-webvault.md)的**账户设置**菜单逐个启用以下的两步登录方式。

### 免费方式 <a href="#free-methods" id="free-methods"></a>

Bitwarden 提供多种免费的两步登录方式，包括：

| 方式                                                                                                       | 设置说明                                                     |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| 通过 FIDO2 WebAuthn 验凭据                                                                                    | 点[这里](setup-guides/two-step-login-via-fido2-webauthn.md) |
| 通过验证器应用程序（例如 [2FAS](https://2fas.com/)、[Ravio](https://raivo-otp.com/) 或 [Aegis](https://getaegis.app/)） | 点[这里](setup-guides/two-step-login-via-authenticator.md)  |
| 通过电子邮件                                                                                                   | 点[这里](setup-guides/two-step-login-via-email.md)          |

### 高级方式 <a href="#premium-methods" id="premium-methods"></a>

对于高级用户（包括付费组织的成员），Bitwarden 提供了几种高级的两步登录方式：

| 方式                                       | 设置说明                                              |
| ---------------------------------------- | ------------------------------------------------- |
| 通过 Duo Security 的 Duo Push、短信、电话和安全钥匙    | 点[这里](setup-guides/two-step-login-via-duo.md)     |
| 通过 YubiKey（任何 4/5 系列设备或 YubiKey NEO/NFC） | 点[这里](setup-guides/two-step-login-via-yubikey.md) |

## 用于团队和企业的两步登录 <a href="#two-step-login-for-teams-and-enterprise" id="two-step-login-for-teams-and-enterprise"></a>

虽然上述所有用于个人的方式都可以启用，但只有团队和企业组织可以从组织的**设置**菜单启用以下组织层面的方式。

| 方式                                    | 设置说明                                          |
| ------------------------------------- | --------------------------------------------- |
| 通过 Duo Security 的 Duo Push、短信、电话和安全钥匙 | 点[这里](setup-guides/two-step-login-via-duo.md) |

## 使用多个方式 <a href="#using-multiple-methods" id="using-multiple-methods"></a>

您可以选择启用多个两步登录方式。当你使用多个已启用的方式登录到 Bitwarden 时，将按照以下优先顺序提示您使用最高优先级的两步登录方式：

1. Duo（组织）
2. FIDO2 WebAuthn
3. YubiKey
4. Duo（个人）
5. 验证器应用程序
6. 电子邮件

{% hint style="warning" %}
如果您使用 SSO 登录，则不建议使用电子邮件方式的两步登录，因为使用多个方式会导致错误。可以考虑改为设置[免费的验证器应用程序方式的两步登录](setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}

不过，任何方式都可以使用。通过选择**使用其他两步登录方式**按钮，以使用低优先级方式进行验证：

{% embed url="https://bitwarden.com/_gatsby/image/ffa607d1f0a31f518a607ea92e53034c/21be4ea96e73c75751773d1e39571e10/twostep-diffmethod.webp?eu=8d8e54e0b5c1fed25e3aa7d56d706261e73d53acfb5767d56e60b0a74ea899d52da51f00229c7eb77f6b0b8f85e942b333c42c664debd48891b44ea7eb30ad5d52800fea61b47507052e90abb6f50f436e951f5ea287c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bbdd0b4626a91b0cb58bbbeadda6fb9d4ad29513584932a70751a1a0ae529bdf1e106253f7a130937cfae0dc16296e33a4d64755d5e51f4787e970ab8286483f9aff80b8f272ea5f096656ec69df9&a=w%3D453%26h%3D334%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A14%3A58.081Z" %}
使用其他两步登录方式
{% endembed %}

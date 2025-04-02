# 两步登录方式

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login/)
{% endhint %}

{% hint style="success" %}
**2024 年 12 月**：为了提高账户安全性，当从新设备登录您的账户或清除浏览器 cookie 后登录您的账户，Bitwarden 很快将要求进行额外验证。您可能已收到一封表明这一点的电子邮件。

输入 Bitwarden 主密码后，系统将提示您输入发送到您账户电子邮箱的一次性验证码。或者，您可以按照本页上的任何指南预先设置两步登录。
{% endhint %}

使用两步登录（也称为双因素验证或 2FA）来保护您的 Bitwarden 密码库，通过在您登录时要求使用辅助设备进行身份验证，防止恶意行为者访问您的数据（即使他们发现了您的主密码）。如果您不熟悉 2FA 的基础知识，请查看我们的[现场指南](field-guide-for-two-step-login.md)。

两步登录有许多不同的方式，从专用的验证器 App 到硬件安全钥匙。无论您选择什么，Bitwarden 都强烈建议您使用两步登录来保护你的密码库。事实上，我们认为这是非常重要的，所以我们很乐意为您提供一些[免费](two-step-login-methods.md#free-methods)的方式。

## 用于个人的两步登录 <a href="#two-step-login-for-individuals" id="two-step-login-for-individuals"></a>

您可以通过[网页密码库](../getting-started/getting-started-webvault.md)的**设置** → **安全** → **两步登录**菜单逐个启用以下的两步登录方式。

### 免费方式 <a href="#free-methods" id="free-methods"></a>

Bitwarden 提供多种免费的两步登录方式，包括：

| 方式                                                                                            | 设置说明                                                                         |
| --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| 通过 FIDO2 WebAuthn 凭据（如 YubiKey 和 Google Titan 等硬件钥匙）                                          | 点击[这里](../my-account/two-step-login/setup-guides/two-step-login-via-fido.md) |
| 通过验证器 App（如 [Bitwarden Authenticator](../bitwarden-authenticator/bitwarden-authenticator.md)） | 点击[这里](setup-guides/two-step-login-via-authenticator.md)                     |
| 通过电子邮箱                                                                                        | 点击[这里](setup-guides/two-step-login-via-email.md)                             |

### 高级方式 <a href="#premium-methods" id="premium-methods"></a>

对于高级用户（包括付费组织的成员），Bitwarden 提供了几种额外的高级两步登录方式：

| 方式                                       | 设置说明                                               |
| ---------------------------------------- | -------------------------------------------------- |
| 通过 Duo Security 的 Duo Push、短信、电话和安全钥匙    | 点击[这里](setup-guides/two-step-login-via-duo.md)     |
| 通过 YubiKey（任何 4/5 系列设备或 YubiKey NEO/NFC） | 点击[这里](setup-guides/two-step-login-via-yubikey.md) |

## 用于团队和企业的两步登录 <a href="#two-step-login-for-teams-and-enterprise" id="two-step-login-for-teams-and-enterprise"></a>

虽然上述所有用于个人的方式都可以启用，但只有团队和企业组织可以从组织的**设置**菜单启用以下组织层面的方式。

| 方式                                    | 设置说明                                           |
| ------------------------------------- | ---------------------------------------------- |
| 通过 Duo Security 的 Duo Push、短信、电话和安全钥匙 | 点击[这里](setup-guides/two-step-login-via-duo.md) |

## 使用多个方式 <a href="#using-multiple-methods" id="using-multiple-methods"></a>

您可以选择启用多个两步登录方式。当您使用多个已启用的方式登录 Bitwarden 时，将按照以下优先顺序提示您使用最高优先级的两步登录方式：

1. Duo（组织）
2. FIDO2 WebAuthn
3. YubiKey
4. Duo（个人）
5. 验证器 App
6. 电子邮箱

{% hint style="warning" %}
如果您[使用 SSO 登录](../login-with-sso/using-login-with-sso.md)，则不建议使用电子邮箱方式的两步登录，因为使用多个方式会导致错误。可以考虑改为设置[免费的验证器方式的两步登录](setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}

不过，任何方式都可以使用。通过选择**使用其他两步登录方式**按钮，以使用低优先级方式进行验证：

{% embed url="https://bitwarden.com/_gatsby/image/ffa607d1f0a31f518a607ea92e53034c/21be4ea96e73c75751773d1e39571e10/twostep-diffmethod.webp?eu=8d8e54e0b5c1fed25e3aa7d56d706261e73d53acfb5767d56e60b0a74ea899d52da51f00229c7eb77f6b0b8f85e942b333c42c664debd48891b44ea7eb30ad5d52800fea61b47507052e90abb6f50f436e951f5ea287c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bbdd0b4626a91b0cb58bbbeadda6fb9d4ad29513584932a70751a1a0ae529bdf1e106253f7a130937cfae0dc16296e33a4d64755d5e51f4787e970ab8286483f9aff80b8f272ea5f096656ec69df9&a=w%3D453%26h%3D334%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A14%3A58.081Z" %}
使用其他两步登录方式
{% endembed %}

## 启用两步登录 <a href="#enabling-two-step-login" id="enabling-two-step-login"></a>

要为您的 Bitwarden 账户设置两步登录：

{% embed url="https://vimeo.com/795652047" %}

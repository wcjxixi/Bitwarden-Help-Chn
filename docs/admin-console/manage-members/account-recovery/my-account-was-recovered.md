# 我的账户已被恢复

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/my-account-was-recovered/)
{% endhint %}

如果您的组织管理员[重置了您的主密码或两步登录方式](recover-a-member-account.md)，Bitwarden 将向您发送一封电子邮件。此消息旨在让您了解情况，并帮助您重新获得对账户的访问权限。

{% hint style="info" %}
账户恢复仅影响在 Bitwarden 内配置的凭据。它**不会绕过 SSO** 或由您的 IdP 配置的任何双重身份验证。如果您的组织[要求 SSO 身份验证](../../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)，成员在恢复后仍需通过这些方式访问其账户
{% endhint %}

## 重置主密码 <a href="#reset-master-password" id="reset-master-password"></a>

收到账户恢复电子邮件后，请向管理员索取临时主密码。请通过安全渠道接收，例如 [Bitwarden Send](../../../password-manager/bitwarden-send/create-a-send.md)。然后重置您的主密码：

1. 在电子邮件中，选择恢复您的账户以打开恢复网页。
2. 输入您的电子邮箱然后选择**继续**。
3. 输入您的临时主密码，然后选择**使用主密码登录**。
4. 创建新的主密码，然后选择**更改主密码**。
5. 使用您的电子邮箱和新主密码登录您的 Bitwarden 账户。
6. （可选）前往**设置** → **安全**以设置新的[两步登录方式](../../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)。

重置后，将要求您更新主密码，因为主密码应当**强大**、**易记**，并且**只有您**自己知道。

## 重置两步登录 <a href="#reset-two-step-login" id="reset-two-step-login"></a>

您的管理员可能选择保留您的主密码不变，仅移除您 Bitwarden 账户上配置的两步登录。在这种情况下，要添加新的两步登录方式：

1. 在电子邮件中，选择恢复您的账户以打开恢复网页。
2. 输入您的电子邮箱然后选择**继续**。
3. 输入您的临时主密码，然后选择**使用主密码登录**。
4. 设置[两步登录方式](../../../account/two-step-login/setup-two-step-login/two-step-login-methods.md)的页面将打开。请设置您选择的方式。

{% hint style="info" %}
如果在连接新的两步登录方式后无法访问组织数据，请联系您的管理员。他们可能需要[恢复](../revoke-remove/temporarily-revoke-access.md#restore-access)您的账户。
{% endhint %}

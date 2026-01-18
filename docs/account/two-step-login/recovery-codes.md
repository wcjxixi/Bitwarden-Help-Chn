# 两步登录恢复代码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/two-step-recovery-code/)
{% endhint %}

当您激活任何[两步登录方式](setup-two-step-login/two-step-login-methods.md)时，Bitwarden 会提供一个唯一的恢复代码。如果您[丢失了身份验证设备](lost-two-step-device.md)，请使用此代码断开所有两步登录方式并重新获得对您账户的访问权限。如果您同时丢失了恢复代码和两步设备（例如带有验证器 App 的手机或已链接的电子邮箱收件箱），您可能会被锁定在您的密码库之外。

## 保存您的恢复代码 <a href="#save-your-recovery-code" id="save-your-recovery-code"></a>

启用任何两步登录方式后，应立即保存您的恢复代码，并将其存储在您选择的安全位置。将打印副本保存在安全的地方是一个不错的选择，因为它可以防止数字盗窃和意外删除。

{% hint style="info" %}
[使用恢复代码](recovery-codes.md#use-your-recovery-code)后，会生成一个新的恢复代码。确保保存更新后的代码。添加新的两步登录方式或更改主密码不会影响恢复代码。
{% endhint %}

要在 Bitwarden 网页 App 中查找您的恢复代码：

1、设置至少一种两步登录方式后，转到**设置** → **安全**。

2、选择**两步登录**。

3、选择**查看恢复代码**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2BsKs83g4cmiCUwxf2ad83/b2a90e85355f3d937aeb46139203737e/2024-12-02_10-54-31.png?_a=DAJCwlWIZAAB" %}
两步登录
{% endembed %}

3、输入您的主密码然后选择**继续**。您的恢复代码将出现：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/64piqJsX7vN25To16iRFIp/09e977fae9485c0764f832c6bb4b4b04/2024-12-02_11-24-35.png?_a=DAJCwlWIZAAB" %}
示例恢复代码
{% endembed %}

## 使用您的恢复代码 <a href="#use-your-recovery-code" id="use-your-recovery-code"></a>

要使用恢复代码重新获取对您的账户的访问权限：

1. 转到您账户服务器位置的恢复页面：
   * **美国**：[https://vault.bitwarden.com/#/recover-2fa/](https://vault.bitwarden.com/#/recover-2fa/)
   * **欧盟**：[https://vault.bitwarden.eu/#/recover-2fa/](https://vault.bitwarden.eu/#/recover-2fa)
   * **自托管**：`https://your.domain.com/#/recover-2fa/`
2. 输入您的电子邮箱地址、主密码和恢复代码。
3. 选择**提交**。

您的账户详细信息和恢复代码通过身份验证后，您将登录到您的密码库，并且之前设置的所有两步登录方式都将被禁用。

{% hint style="info" %}
恢复代码不会禁用用于组织的 Duo。如果您被组织 Duo 提示锁定在密码库之外，请联系您公司的 Duo 管理员，以获得绕过此提示的帮助。

如果您不确定 Duo 提示是个人设置的还是组织设置的，请尝试选择**使用其他两步登录方式**。
{% endhint %}

为了以后保持对您账户安全可靠的访问：

* 设置或重新激活至少一种[两步登录方式](setup-two-step-login/two-step-login-methods.md)。如果您不这样做，当您从无法识别的设备登录时，Bitwarden 将向您的账户电子邮箱发送[验证码](../log-in-and-unlock/new-device-protection.md)。
* [保存您的新恢复代码](recovery-codes.md#save-your-recovery-code)，因为它在使用后会发生变化。

### 企业成员 <a href="#enterprise-members" id="enterprise-members"></a>

当您是企业组织的成员时，提交有效的恢复代码后发生的情况可能会有所不同。

如果您的组织[要求单点登录身份验证](../../admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)，但不[要求两步登录](../../admin-console/oversight-visibility/enterprise-policies.md#require-two-step-login)，您将被定向到 SSO 登录页面。使用您的 SSO 凭据登录并访问您的 Bitwarden 密码库。

如果您的组织[要求两步登录](../../admin-console/oversight-visibility/enterprise-policies.md#require-two-step-login)，成功使用恢复代码后会将您从组织中移除。登录后要重新加入组织：

1. 设置一个新的[两步登录方式](setup-two-step-login/two-step-login-methods.md)。
2. 如果您的组织还[要求单点登录身份验证](../../admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)，请将您的 SSO 凭据重新连接到您的 Bitwarden 账户。
3. 请求管理员或所有者在组织内[恢复您的账户](../../admin-console/manage-members/revoke-remove/temporarily-revoke-access.md#restore-access)。

# 丢失了辅助设备

{% hint style="success" %}
对应的[官方文档地址](https://help.bitwarden.com/article/lost-two-step-device/)
{% endhint %}

失去对辅助设备（例如，安装了验证器的移动设备、安全钥匙或已链接的电子邮箱收件箱）的访问权限有可能将您锁定在 Bitwarden 密码库之外。

当您失去对辅助设备的访问权限时，该怎么办取决于您是否保存了您的[两步登录恢复代码](recovery-codes.md)。如果您不确定，请记住，恢复代码需要主动保存（即 Bitwarden 不会为您保存在任何地方），它看起来像这样：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/64piqJsX7vN25To16iRFIp/09e977fae9485c0764f832c6bb4b4b04/2024-12-02_11-24-35.png?_a=DAJCwlWIZAAB" %}
示例恢复代码
{% endembed %}

## 有恢复代码？ <a href="#i-dont-have-a-recovery-code" id="i-dont-have-a-recovery-code"></a>

很好！如果您在某处保存了恢复代码，您可以用它从密码库外部禁用所有两步登录方式。

要使用您的恢复代码，请导航到 [https://vault.bitwarden.com/#/recover-2fa](https://vault.bitwarden.com/#/recover-2fa) 或 [https://vault.bitwarden.eu/#/recover-2fa/](https://vault.bitwarden.eu/#/recover-2fa/)，或者，如果是自托管，请导航到 `https://your.domain.com/#/recover-2fa`。

{% hint style="info" %}
恢复代码不会禁用用于组织的 Duo。如果您被组织 Duo 提示锁定在密码库之外，请联系您公司的 Duo 管理员，以获得绕过提示的帮助。如果您不确定 Duo 提示是个人设置的还是组织设置的，请尝试使用**使用其他两步登录方式**按钮。
{% endhint %}

## 没有恢复代码？ <a href="#i-dont-have-a-recovery-code" id="i-dont-have-a-recovery-code"></a>

如果您没有将您的恢复代码保存在密码库之外的某个地方，那么很遗憾，团队无法恢复您的账户或其中的数据。您需要删除自己的账户，然后重新创建一个新的账户。

{% hint style="success" %}
在操作删除您的账户之前，请尝试以下操作：

* 过在登录界面上选择**使用其他两步登录方式**，检查您是否启用了备用的两步登录方式。
* **如果您使用 Duo**，请[生成绕行代码](https://duo.com/docs/administration-users#generating-a-bypass-code)。对于组织 Duo，公司的 Duo 管理员可以为您生成绕行代码。
* **如果您在使用紧急访问**：具有**接管**访问权限的受信任的紧急联系人可以禁用两步登录方式。[了解如何使用紧急访问访问密码库](../security/emergency-access.md#use-emergency-access)。
* **请检查您当前是否登录了任何 Bitwarden 客户端应用程序**（移动 App、浏览器扩展等）。如果是，请[导出您的密码库数据](../import-export/export-vault-data.md)以保存您的数据。

[账户恢复](../organizations/admin-password-reset.md)不会绕过两步登录。
{% endhint %}

要删除您的账户：

1. 导航至 [https://vault.bitwarden.com/#/recover-delete](https://vault.bitwarden.com/#/recover-delete) 或 [https://vault.bitwarden.eu/#/recover-delete](https://vault.bitwarden.eu/#/recover-delete)。
2. 输入您账户关联的**电子邮箱地址**
3. 在您的电子邮箱收件箱中，打开邮件并确认您要删除此 Bitwarden 账户

如果您删除了一个与高级订阅相关联的 Bitwarden 账户，请[联系我们](https://bitwarden.com/contact/)，我们将把您现有的订阅重新应用到您的新账户中。如果在删除之前已成功导出了密码库数据，则可以轻松地将其[导入到新的账户](../import-export/import-data-to-your-vault.md)。

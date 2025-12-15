# 无法访问两步登录

{% hint style="success" %}
对应的[官方文档地址](https://help.bitwarden.com/article/lost-two-step-device/)
{% endhint %}

[两步登录方式](setup-two-step-login/two-step-login-methods.md)可以保护您的账户，但丢失身份验证设备（例如带有验证器 App 的手机或已链接的电子邮箱收件箱）可能会将您锁定在 Bitwarden 密码库之外。如果您丢失了两步身份验证方式，恢复选项将受到限制。重新获得访问权限很大程度上取决于您或您的公司管理员之前是否为这种潜在情况做好了准备。

## 可能的恢复方法 <a href="#possible-recovery-methods" id="possible-recovery-methods"></a>

尝试以下选项，看看您是否可以重置两步登录方式或在创建新账户之前[导出您的密码库](../../password-manager/import-and-export/export-vault-data.md)。

{% hint style="info" %}
[账户恢复](../../admin-console/manage-members/account-recovery/about-account-recovery.md)不会绕过或停用两步身份验证。
{% endhint %}

### 备用两步登录方法 <a href="#alternate-two-step-login-method" id="alternate-two-step-login-method"></a>

如果您设置了多种两步登录方式，请尝试另一种。在登录界面上时，选择使用**其他两步登录方式**。

### 恢复代码 <a href="#recovery-code" id="recovery-code"></a>

如果您在被锁定之前保存了恢复代码，则可以[使用恢复代码](recovery-codes.md#use-your-recovery-code)访问您的账户。当您设置任何两步登录方式时，都会生成恢复代码，并且您必须主动将代码保存在密码库外部可以找到的位置。Bitwarden 无法代表您获取恢复代码。

当您从账户的安全设置中获取恢复代码时，恢复代码如下所示：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/64piqJsX7vN25To16iRFIp/09e977fae9485c0764f832c6bb4b4b04/2024-12-02_11-24-35.png?_a=DAJCwlWIZAAB" %}
示例恢复代码
{% endembed %}

{% hint style="info" %}
恢复代码不会禁用用于组织的 Duo。如果您被组织 Duo 提示锁定在密码库之外，请联系您公司的 Duo 管理员，以获得绕过此提示的帮助。

如果您不确定 Duo 提示是个人设置的还是组织设置的，请尝试选择**使用其他两步登录方式**。
{% endhint %}

### 受信任的紧急联系人 <a href="#trusted-emergency-contact" id="trusted-emergency-contact"></a>

如果您指定了具有接管访问权限的[受信任的紧急联系人](../log-in-and-unlock/more-log-in-options/emergency-access.md)，请请求他们[发起紧急访问](../log-in-and-unlock/more-log-in-options/emergency-access.md#use-emergency-access)。在为该紧急联系人设置的**等待时间**过后，所有两步登录方式将被关闭，紧急联系人可以更改主密码。

### Duo 绕行代码 <a href="#duo-bypass-code" id="duo-bypass-code"></a>

如果您的 Bitwarden 账户已连接到 Duo，请请求您公司的 Duo 管理员生成[绕行代码](https://duo.com/docs/administration-users#generating-a-bypass-code)。此临时代码将验证您的 Duo 凭据，以便您登录 Bitwarden。

### 其他设备或 Bitwarden App <a href="#other-device-or-bitwarden-app" id="other-device-or-bitwarden-app"></a>

检查您的所有设备，看看您是否已登录到任何 Bitwarden 客户端，例如移动 App、浏览器扩展或桌面 App。

* 如果您已登录网页 App，请获取并[使用您的恢复代码](recovery-codes.md#use-your-recovery-code)来断开所有两步登录方式。
* 如果您已登录到任何其他 Bitwarden App，请[导出您的密码库](../../password-manager/import-and-export/export-vault-data.md)，创建一个新账户，然后在其中[导入您的数据](../../password-manager/import-and-export/import-data.md)。确认您的数据已正确导入后，请注销旧账户并考虑将其[删除](../../plans-and-pricing/delete-an-account-or-organization.md)。

## 当恢复方法不起作用时 <a href="#when-recovery-methods-dont-work" id="when-recovery-methods-dont-work"></a>

我们建议仔细检查您的所有设备和浏览器中是否有任何已登录的 Bitwarden 会话。如果您找到了，这就是您[导出密码库数据](../../password-manager/import-and-export/export-vault-data.md)的最后机会。

如果这些选项均无法让你获取对您的账户的访问权限，那么 Bitwarden 也无法恢复该账户或其数据。您需要[删除您的账户](../../plans-and-pricing/delete-an-account-or-organization.md#wu-xu-deng-lu)并然后创建一个新账户。如果您删除了具有高级版订阅的 Bitwarden 账户，请[联系我们](https://bitwarden.com/contact/)，我们将把您现有的订阅应用到您的新账户中。

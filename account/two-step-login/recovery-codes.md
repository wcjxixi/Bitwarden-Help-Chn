# 获取恢复代码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/two-step-recovery-code/)
{% endhint %}

如果您启用了任何[两步登录方式](setup-guides/two-step-login-methods.md)，重要的是要明白，失去对您的辅助设备（如安装了验证器的移动设备、安全钥匙、或已链接的电子邮箱收件箱）的访问，有可能将您锁定在您的 Bitwarden 密码库之外。

为了防止这种情况的发生，Bitwarden 生成了一个**恢复代码**，它可以和您的主密码一起使用，以从您的密码库外部禁用任何已启用的两步登录方式。

{% hint style="success" %}
启用任何两步登录方式之后，应立即[获取您的恢复代码](recovery-codes.md#get-your-recovery-code)。此外，每次[使用](recovery-codes.md#use-your-recovery-code)后都要重新获取一个新的恢复代码，因为每次被使用后它都会更改。
{% endhint %}

除了确保恢复代码的安全，用户可能还希望在启用双重身份验证之前创建[导出](../../import-export/encrypted-exports.md)以备份密码库数据。

## 获取您的恢复代码 <a href="#get-your-recovery-code" id="get-your-recovery-code"></a>

要获取您的恢复代码：

1、登录您的网页 App。

2、从导航选择**设置** → **安全** → **两步登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2BsKs83g4cmiCUwxf2ad83/b2a90e85355f3d937aeb46139203737e/2024-12-02_10-54-31.png?_a=DAJCwlWIZAAB" %}
两步登录
{% endembed %}

3、选择屏幕上方的**查看恢复代码**。将提示您输入您的主密码，然后将打开恢复代码面板：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/64piqJsX7vN25To16iRFIp/09e977fae9485c0764f832c6bb4b4b04/2024-12-02_11-24-35.png?_a=DAJCwlWIZAAB" %}
示例恢复代码
{% endembed %}

以最适合您的方式保存您的恢复代码。不管是否相信，打印代码并将其保存在安全的地方是确保代码不易被盗窃或无意删除的最佳方式之一。

{% hint style="info" %}
**恢复代码什么时候会更改？**

禁用和重新启用两步登录或更改您的主密码都不会更改您的恢复代码。恢复代码只会[在它被您使用后](recovery-codes.md#use-your-recovery-code)更改。使用恢复代码后，请立即获取一个新的代码，并使用对您最有意义的方式进行保存。
{% endhint %}

## 使用您的恢复代码 <a href="#use-your-recovery-code" id="use-your-recovery-code"></a>

要使用您的恢复代码，请导航到 [https://vault.bitwarden.com/#/recover-2fa](https://vault.bitwarden.com/#/recover-2fa) 或 [https://vault.bitwarden.eu/#/recover-2fa/](https://vault.bitwarden.eu/#/recover-2fa/)，或者，如果是自托管，请导航到 `https://your.domain.com/#/recover-2fa`。

使用恢复代码与正常的登录过程相同，需要提供您的电子邮箱地址和主密码，但也需要提供您的恢复代码。三者都验证成功后，您将登录进您的密码库同时**所有的两步登录方式将被禁用**。

**使用后需重新获取新的恢复代码，因为每次使用后它都会更改**。此时，您还应该重新启用你想在未来使用的任何两步登录方式。

{% hint style="info" %}
恢复代码不会禁用用于组织的 Duo。如果您被组织 Duo 提示锁定在密码库之外，请联系您公司的 Duo 管理员，以获得绕过提示的帮助。

如果您不确定 Duo 提示是个人设置的还是组织设置的，请尝试使用**使用其他两步登录方式**按钮。
{% endhint %}

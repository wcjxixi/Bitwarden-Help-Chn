# 恢复代码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/two-step-recovery-code/)
{% endhint %}

如果您启用了任何[两步登录方式](two-step-login-methods.md)，重要的是要明白，失去对您的辅助设备（如安装了验证器的移动设备、安全钥匙、或已链接的电子邮件收件箱）的访问，有可能将您锁定在您的 Bitwarden 密码库之外。

为了防止这种情况的发生，Bitwarden 生成了一个**恢复代码**，它可以和您的主密码一起使用，以从您的密码库外部禁用任何已启用的两步登录方式。

{% hint style="success" %}
启用任何两步登录方式之后，应**立即**[获取您的恢复代码](recovery-codes.md#get-your-recovery-code)。此外，每次[使用](recovery-codes.md#use-your-recovery-code)后都要重新获取一个新的恢复代码，因为每次被使用后它都会更改。
{% endhint %}

## 获取您的恢复代码 <a href="#get-your-recovery-code" id="get-your-recovery-code"></a>

要获取您的恢复代码：

1、登录您的[网页密码库](https://vault.bitwarden.com/)。

2、选择个人资料图标并然后下拉列表中选择**账户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?eu=8adb56b0eaccf885076fa2d66f746161e56956aaac0032d43465b6f94bfe9b8e71fa1151289528b0796d528bd7e816bc31c67d691befd18991bc4af4be3da80d07835fb836b07807052ec4fde4a1574d60c11b5fa8d1c90ca76a21ddb4b4e47711571b23ae7ebbd7e8fa3064badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec3226050d762c882bfad0bb5137732f072e7fc6d45fae7e91b13f4934705f0c03a5673a8555fb3863c7b0aef509da7e7ee7fdc06073d0cab1e3be58f97f2888ac7ff6c654780e0fae0eadb966f6d10b574aee2bfa8b4fb61d04352ff36197647e8e&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A24%3A03.707Z" %}
账户设置
{% endembed %}

3、选择**安全**页面然后选择**两步登录**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/825426d227e1afce2f4b644e6a3e9e84/3cbf2a88c5de2a53993ef05ef68dd09e/Screen%20Shot%202022-05-16%20at%2011.13.53%20AM.webp?eu=da8a56b3b0c9ff8e0a6ef2806a713261e96b52aca85232853c31e0ad4ffa99d220a51f01249279b5246b0c8dd0b344ee66937e3348eb82dac0b81cf3ef36a85c008650b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af815d7191f5ae2d32c6f825b9613b13834e73ad30b393c1301beb98b84ee9e1ecfb5bccceb32c0e40d9a73277774b1909ea28bda2e60c75264a1319609bf137a439c9f2531e61215c4203f27a3bd63aaa285ec2e5e5a05ec77f788ed9b42f30d894&a=w%3D779%26h%3D301%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.371Z" %}
两步登录
{% endembed %}

4、选择屏幕上方的**查看恢复代码**。将提示您输入您的主密码，然后将打开恢复代码面板：

{% embed url="https://bitwarden.com/_gatsby/image/3f64f4e767e6e380c21e9b5903e99a01/bf8c24649842f132ed4afbe94198c70b/recoverycode.webp?eu=898d57e6b6ccf88f5a3df2d56073363be53f02a2fe5665d83f66e2fa4dfc96d42da51a0775c678b97e60528fd3e84ab933cf7d651ab8d6dfc4e94ef3e264f80955845eec61bb210e537e91fce4fc0f4161cf1e50a180c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bbd949e6a5f948dd818a998ecac6d929de1746536a2b32a24261f4d5fe42fbda1b051226d29430961cbaf0dc43795e36a48672b0b0905a678788506a42a6481ada8fe098c643bbfff&a=w%3D690%26h%3D294%26fm%3Dwebp%26q%3D75&cd=2022-12-09T17%3A14%3A34.027Z" %}
示例恢复代码
{% endembed %}

以最适合您的方式保存您的恢复代码。不管是否相信，打印代码并将其保存在安全的地方是确保代码不易被盗窃或无意删除的最佳方式之一。

{% hint style="info" %}
**恢复代码什么时候会更改？**

禁用和重新启用两步登陆或更改您的主密码都不会更改您的恢复代码。恢复代码只会[在它被您使用后](recovery-codes.md#use-your-recovery-code)更改。使用恢复代码后，请立即获取一个新的代码，并使用对您最有意义的方式进行保存。
{% endhint %}

## 使用您的恢复代码 <a href="#use-your-recovery-code" id="use-your-recovery-code"></a>

要使用您的恢复代码，请导航到 [`https://vault.bitwarden.com/#/recover-2fa`](https://vault.bitwarden.com/#/recover-2fa)（或者，如果是自托管安装，请导航到 `https://your.vault.domain.com/#/recover-2fa`）。

使用恢复代码与正常的登录过程相同，需要提供您的电子邮件地址和主密码，但也需要提供您的恢复代码。三者都验证成功后，您将登录进您的密码库同时**所有的两步登录方式将被禁用**。

**使用后需重新获取新的恢复代码，因为每次使用后它都会更改**。此时，您还应该重新启用你想在未来使用的任何两步登陆方式。

{% hint style="success" %}
恢复代码**不会禁用用于组织的 Duo**。您可以通过**（组织）**头部来判断 Duo 提示是否是组织层面的，如下截图所示：

![](<../.gitbook/assets/image (3).png>)

如果 **Duo (Organization)** 提示窗口提示您被锁定在您的密码库之外了，请与您公司的 Duo 管理员联系，以帮助绕过此提示。
{% endhint %}

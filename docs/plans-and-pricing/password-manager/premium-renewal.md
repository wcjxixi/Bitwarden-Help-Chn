# 高级会员续费

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/premium-renewal/)
{% endhint %}

个人高级版订阅按年自动续费。您可以在您的网页版 App 中导航到**设置** → **订阅**，来查看您的续费日期：

{% embed url="https://bitwarden.com/assets/3Ru9TSLguhRNYtLe2TLwXk/525da31347b13dfcce28efa49531fadc/Subscription_page.png?w=1200&fm=avif" %}
订阅页面
{% endembed %}

当您的续费日期临近时，Bitwarden 建议您导航到**设置** → **订阅** → **付款方式**来验证付款方式。有关更新您的付款方式的帮助，请参阅[更新您的计费信息](../update-your-billing-information.md)。

{% hint style="danger" %}
如果我们无法处理您的付款方式，或者您取消了订阅，您的账户将恢复为[免费个人版](about-bitwarden-plans.md#free-individual)。在您重新启动您的高级订阅之前，将导致以下情况：

**两步登录**

您**不会**被锁定在您的密码库之外，但您将无法使用高级两步登录选项，如 YubiKey、FIDO2 或 Duo。

* 如果您启用了核心的两步登录选项（验证器 App 或电子邮件），您将被提示使用这些可用的选项。&#x20;
* 如果您没有启用其他两步登录选项，您将在没有两步登录的情况下进行身份验证进入密码库。

**Bitwarden 验证器 (TOTP)**

您的密匙将继续存储在密码库项目的**验证器密钥 (TOTP)** 字段中，但是 Bitwarden 不会生成 TOTP 代码。

**加密文件附件**

文件**不会**从您的密码库中删除，但您无法上传或下载。

**紧急访问**

已信任的紧急联系人仍然可以请求并获得对您的密码库的访问权限。但是，作为授予人，您将无法添加新的或编辑现有的可信任的紧急联系人。
{% endhint %}

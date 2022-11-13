# 来自 Bitwarden 的电子邮件

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/emails-from-bitwarden/)
{% endhint %}

与使用强密码一样，避免可疑电子邮件是您在线安全工具包中的一个重要工具。我们建议您熟悉这些 [FTC 指南](https://www.consumer.ftc.gov/articles/how-recognize-and-avoid-phishing-scams)，以发现和避免网络钓鱼。

以下指南可帮助您确定看似来自 Bitwarden 的电子邮件是否合法：

## 自动电子邮件 <a href="#automated-emails" id="automated-emails"></a>

### 产品交互电子邮件 <a href="#product-interaction-emails" id="product-interaction-emails"></a>

诸如新设备警报、加入组织的邀请和两步登录代码之类的电子邮件将来自 `no-reply@bitwarden.com`，或者，如果您是自托管，则来自已配置的域名，例如 `no-reply@my.domain.com`。

这些电子邮件**永远不会包含附件**。如果系统提示您下载文件，请向我们报告该电子邮件。

其中一些电子邮件（例如组织邀请）将包含按钮。在**单击超链接之前**，请务必总是检查此超链接的合法性，确认它指向 `https://vault.bitwarden.com`、您或您组织的自托管域名。如果您不知道您组织的域名，请询问您的 IT 团队成员或管理员。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/4d34e1f7476d2bc27dc4f13c527dec1a/user-accept-updated.png?fm=webp&h=374&q=50&w=439" %}
邀请窗口
{% endembed %}

### 付款电子邮件 <a href="#payments-emails" id="payments-emails"></a>

个人高级订阅和付费组织订阅的自动付款电子邮件将来自一个地址，例如 `@stripe.com`、`invoice+statements+acct_xxxxxxxxxxx@stripe.com`。

这些电子邮件**将包含**附件，具体是 PDF 发票和收据。

## 交互式电子邮件 <a href="#opt-in-emails" id="opt-in-emails"></a>

虽然您会在日常使用 Bitwarden 过程中收到[自动电子邮件](emails-from-bitwarden.md#automated-emails)，但如果您与 Bitwarden 生态系统的各个部分进行了交互，您也可能会收到来自以下地址的电子邮件：

* 支持请求：`support@bitwarden.com`
* 产品公告：`productupdates@bitwarden.com`
* 试用信息：`trial@bitwarden.com`
* 营销活动：`marketing@bitwarden.com`
* 来自 Bitwarden 团队成员的电子邮件：`@bitwarden.com`

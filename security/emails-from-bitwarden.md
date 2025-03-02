# 来自 Bitwarden 的电子邮件

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/emails-from-bitwarden/)
{% endhint %}

与使用强密码一样，避免可疑电子邮件也是您在线安全工具包中的一个重要工具。我们建议您熟悉 [FTC 指南](https://www.consumer.ftc.gov/articles/how-recognize-and-avoid-phishing-scams)，以识别和避免网络钓鱼。

以下是一些指导原则，可帮助您确定一封看似来自 Bitwarden 的电子邮件是否合法：

## 自动电子邮件 <a href="#automated-emails" id="automated-emails"></a>

### 产品交互电子邮件 <a href="#product-interaction-emails" id="product-interaction-emails"></a>

诸如新设备警报、加入组织的邀请、请求访问机密管理器，以及两步登录代码之类的电子邮件将来自 `no-reply@bitwarden.com`，或者，如果您是自托管，则来自已配置的域名，例如 `no-reply@my.domain.com`。

{% hint style="info" %}
自 2024.9.2 起，电子邮件验证请求在创建账户时发送给云用户，也是从 `no-reply@bitwarden.com` 发出的：

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2QR4MYirRuYyMJnkx5ce6e/858d2d1fc23440e31ce87a8ff6efa4f5/2024-09-26_10-01-00.png?_a=DAJCwlWIZAAB" alt="" data-size="original">
{% endhint %}

这些电子邮件**永远不会包含附件**。如果系统提示您下载文件，请向我们报告该电子邮件。

其中一些电子邮件（例如组织邀请）将包含按钮。在**单击超链接之前**，请务必总是检查此超链接的合法性，确认它指向 `https://vault.bitwarden.com`、您或您组织的自托管域名。如果您不知道您组织的域名，请询问您的 IT 团队成员或管理员。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/58e2ece3acfe37eaffa4bc55611eb414/Screen_Shot_2023-04-28_at_10.40.35_AM.png?_a=DAJCwlWIZAAB" %}
邀请加入
{% endembed %}

### 付款电子邮件 <a href="#payments-emails" id="payments-emails"></a>

个人高级订阅和付费组织订阅的自动付款电子邮件将来自 `invoice+statements@bitwarden.com` 地址。

这些电子邮件**将包含**附件，具体是 PDF 发票和收据。

### 续费电子邮件 <a href="#renewals-emails" id="renewals-emails"></a>

对于即将到期的 Bitwarden 订阅，付费用户将收到电子邮件提醒即将续费。这些电子邮件将来自 `no-reply@bitwarden.com` 和 `upcoming-invoice@bitwarden.com` 两个地址。

## 交互式电子邮件 <a href="#opt-in-emails" id="opt-in-emails"></a>

虽然您会在日常使用 Bitwarden 过程中收到[自动电子邮件](emails-from-bitwarden.md#automated-emails)，但如果您与 Bitwarden 生态系统的各个部分进行了交互，您也可能会收到来自以下地址的电子邮件：

* 支持请求：`support@bitwarden.com`
* 产品公告：`productupdates@bitwarden.com`
* 试用信息：`trial@bitwarden.com`
* 营销活动：`marketing@bitwarden.com`
* 来自 Bitwarden 团队成员的电子邮件：`@bitwarden.com`&#x20;

## 警告电子邮件 <a href="#alert-emails" id="alert-emails"></a>

Bitwarden 会对可疑活动（如从未知设备登录和从未知设备尝试登录失败）发送电子邮件提醒。

这些电子邮件**永远不会包含附件**。如果提示您下载文件或点击未知链接，请联系我们。

### 新设备登录 <a href="#new-device-logged-in" id="new-device-logged-in"></a>

如果您的账户从未知设备成功登录，您将收到一封包含登录信息的电子邮件。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BPGGp6Wvm3NzDopPbkkj2/b8ff436931e2791d366dda3ea8ed078e/Screenshot_2023-03-29_at_4.05.28_PM.png?_a=DAJCwlWIZAAB" %}

电子邮件内容包括：

* 日期
* IP 地址
* 设备类型

如果您无法识别该登录，请参阅[此处](security-faqs.md#q-what-do-i-do-if-i-dont-recognize-a-new-device-logging-into-bitwarden)并立即采取措施保护您的账户。

### 受信任设备请求被批准 <a href="#trusted-device-request-approved" id="trusted-device-request-approved"></a>

向组织管理员提出的[添加受信任设备](../admin-console/login-with-sso/trusted-devices/add-a-trusted-device.md)的请求获得批准后，会向提出请求的用户发送一封电子邮件，通知他们可以继续在该设备上登录。**用户必须在 12 小时内登录新设备，否则批准将失效。**

电子邮件内容包括：

* 日期
* IP 地址
* 设备类型

## 公告电子邮件 <a href="#announcement-emails" id="announcement-emails"></a>

### 主题：即将到来的登录变更（2024 年 12 月） <a href="#subject-upcoming-login-changes-dec.-2024" id="subject-upcoming-login-changes-dec.-2024"></a>

这封电子邮件于 2024 年 12 月从 `no-reply@bitwarden.com` 发送，旨在通知用户即将对新设备验证做出的更改。

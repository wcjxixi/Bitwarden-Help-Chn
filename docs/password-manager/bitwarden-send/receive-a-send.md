# 接收 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/receive-send/)
{% endhint %}

与传统的 Bitwarden 密码库项目不同，任何拥有 Send 链接的人（包括没有 Bitwarden 账户的人）都可以接收并打开 Send。Send 链接是随机生成的，看起来像这样：

* `https://send.bitwarden.com/#...`，这会自动解析为 `https://vault.bitwarden/com/#/send/...`
* `https://your.selfhosted.domain.com/#/send/...`，如果是自托管

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/LLnrgZwyr6IAJ0GImXLnj/da3e363db0474f4cd6a57a44a6f1bd8f/Receive_a_send.png?w=564&#x26;fm=avif" alt=""><figcaption><p>收到的 Send</p></figcaption></figure></div>

根据发送者[所配置的选项](create-a-send.md)，Send 的接收者可能需要：

* 输入密码来访问 Send 的内容。
* 输入[电子邮件验证码](receive-a-send.md#email-verified-sends)
* 手动切换隐藏文本 Send 的可见性。

## 电子邮箱验证的 Send <a href="#email-verified-sends" id="email-verified-sends"></a>

高级版 Bitwarden 用户可以创建要求电子邮箱验证才能查看的 Send。如果您收到要求电子邮箱验证的 Send 链接，则在打开 Send 链接后会提示您输入验证码。要打开电子邮箱验证的 Send：

1、打开您从发送者处收到的 Send 链接然后输入您的电子邮箱地址：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6guff4hS04wXAcGp7DUMDo/5ba4409fd5fcf3171f665896fa17ca9f/2026-02-24_16-06-03.png?w=450&#x26;fm=avif" alt=""><figcaption><p>输入电子邮箱 Send</p></figcaption></figure></div>

2、如果输入的电子邮箱与发送者指定的电子邮箱地址匹配，您将在电子邮箱收件箱中收到一个授权码：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3f6f5IfMdXDqrR3cMwgoWN/65f8d6ffe2b3239049e7f76dfca33253/2026-02-24_16-06-56.png?w=450&#x26;fm=avif" alt=""><figcaption><p>Send 验证码</p></figcaption></figure></div>

3、输入授权码即可查看此 Send。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7qM22jPeoKCnGE6GS03wz7/4f959a8b1b7b9f13674bdda975af9a5d/2026-02-24_17-04-46.png?w=493&#x26;fm=avif" alt=""><figcaption><p>输入 Send 验证码</p></figcaption></figure></div>

## 隐藏电子邮箱的 Send <a href="#hidden-email-sends" id="hidden-email-sends"></a>

默认情况下，Send 对象将对接收者显示发送者的电子邮箱地址，如上面的屏幕截图所示。发送者可以为 Send 对象选择隐藏其电子邮箱地址，该电子邮箱地址将替换为警告消息：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/47RPmr6xOowzjJbG6JxVG3/42ba660b4316b57c4857ed7f7fcd58e3/Hidden_email_send.png?w=516&#x26;fm=avif" alt=""><figcaption><p>隐藏电子邮箱的文件 Send</p></figcaption></figure></div>

如果您收到一个带有这种警告信息的 Send，以下是您应该做的：

* **此 Send 是预期的吗？**\
  如果此 Send 是预期的，请与预期的发送者取得联系。与此人确认收到的此 Send 的链接（`https://vault.bitwarden.com/#/send/xxx/yyy`）与他们创建的一致。
* **此 Send 是非预期的吗？**\
  如果此 Send 是非预期的，您应该在与之互动之前确定发送者的身份。询问您的同事、经理或拥有 Bitwarden 账户的朋友，他们是否可能给你发送了什么。如果您确定了发送者，请与此人确认收到的 Send 链接（`https://vault.bitwarden.com/#/send/xxx/yyy`）与他们创建的一致。**如果您不能识别发送者**，不要与此 Send 互动。

{% hint style="danger" %}
使用上述措施以确保隐藏了电子邮箱的 Send 的可信度，对于文件 Send 来说尤其重要。**千万不要下载未知的文件**。
{% endhint %}

## 已删除、已过期和已禁用的 Send <a href="#deleted-expired-and-disabled-sends" id="deleted-expired-and-disabled-sends"></a>

当一个 Send [被删除、已过期或被禁用](send-lifespan.md)时，将为试图使用已生成的 Send 链接的接收者显示一个界面指示该 Send 不存在或不再可用：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6sveEP7CK57cGvSa9zpdwe/8da52464833e2dbfab7ef228f38f77e6/A_deleted__expired__or_disabled_Send.png?w=488&#x26;fm=avif" alt=""><figcaption><p>已删除、已过期或已禁用的 Send</p></figcaption></figure></div>

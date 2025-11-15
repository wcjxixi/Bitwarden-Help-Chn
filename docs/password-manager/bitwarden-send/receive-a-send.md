# 接收 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/receive-send/)
{% endhint %}

与传统的 Bitwarden 密码库项目不同，任何拥有 Send 链接的人（包括没有 Bitwarden 账户的人）都可以接收并打开 Send。Send 链接是随机生成的，看起来像这样：

* `https://send.bitwarden.com/#...`，这会自动解析为 `https://vault.bitwarden/com/#/send/...`
* `https://your.selfhosted.domain.com/#/send/...`，如果是自托管

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/LLnrgZwyr6IAJ0GImXLnj/578559931915e04aeb6f037e2f03490e/2024-12-03_10-21-38.png?_a=DAJCwlWIZAAB" %}
收到的 Send
{% endembed %}

根据发送者[所配置的选项](create-a-send.md)，Send 的接收者可能需要：

* 输入密码来访问 Send 的内容。
* 手动切换隐藏文本 Send 的可见性。

## 隐藏电子邮箱的 Send <a href="#hidden-email-sends" id="hidden-email-sends"></a>

默认情况下，Send 对象将对接收者显示发送者的电子邮箱地址，如上面的屏幕截图所示。发送者可以为 Send 对象选择隐藏其电子邮箱地址，该电子邮箱地址将替换为警告消息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/47RPmr6xOowzjJbG6JxVG3/98c803df88adcde39c96331cf34ab106/2024-12-03_10-23-03.png?_a=DAJCwlWIZAAB" %}
隐藏了电子邮箱的文件 Send
{% endembed %}

如果您收到一个带有这种警告信息的 Send，您应该这样做：

* **这条 Send 是预期的吗？**\
  如果这条 Send 是预期的，请与预期的发送者取得联系。与此人确认收到的此 Send 的链接（`https://vault.bitwarden.com/#/send/xxx/yyy`）与他们创建的一致。
* **这条 Send 是非预期的吗？**\
  如果这条 Send 是非预期的，您应该在与之互动之前确定发送者的身份。问问您的同事、经理或拥有 Bitwarden 账户的朋友，他们是否可能给你发送了什么。如果您确定了发送者，请与此人确认收到的 Send 链接（`https://vault.bitwarden.com/#/send/xxx/yyy`）与他们创建的一致。**如果您不能识别发送者**，不要与此 Send 互动。

{% hint style="warning" %}
使用上述措施以确保隐藏了电子邮箱的 Send 的可信度，对于文件 Send 来说尤其重要。**千万不要下载未知的文件**。
{% endhint %}

## 已删除、已过期和已禁用的 Send <a href="#deleted-expired-and-disabled-sends" id="deleted-expired-and-disabled-sends"></a>

当一个 Send 已[被删除、过期或禁用](send-lifespan.md)时，将为试图使用已生成的 Send 链接的接收者显示一个界面指示该 Send 不存在或不再可用：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sveEP7CK57cGvSa9zpdwe/896f888bbbc782b8eef633afbd112d68/2024-12-03_10-24-14.png?_a=DAJCwlWIZAAB" %}
已删除、已过期或已禁用的 Send
{% endembed %}

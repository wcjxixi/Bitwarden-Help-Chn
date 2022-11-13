# 自托管 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/send-hosting/)
{% endhint %}

[更新实例](../on-premises-hosting/update-your-instance.md)后，大多数的实现都已经被设置为开始[使用 Send](create-a-send.md)。一个例外的情况是如果你使用了一个非默认的**用于附件存储的映射卷**。

附加到文件 Send 的文件被存储在现有附件卷的 `send` 子目录中（即 `./bwdata/core/attachments/send`）。这是由 `globalSettings__send__baseDirectory=` 环境变量决定的，此变量在 `global.override.env` 中的默认配置如下：

```systemd
globalSettings__send__baseDirectory=/etc/bitwarden/core/attachments/send
```

如果您想将附加到文件 Send 的文件存储在非默认附件卷中，您需要将 `globalSettings__send__baseDirectory=` 指向新卷。更多信息，请参阅[配置环境变量](../on-premises-hosting/configure-environment-variables.md)。

# 异常流量错误

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/unusual-traffic-error/)
{% endhint %}

如果您收到一条错误消息，内容为 `Traffic from your network looks unusual. Connect to a different network or try again.`（来自您的网络的流量看起来异常。请连接到不同的网络或重试。）。说明您的 IP 地址或请求已被标记为恶意 Internet 流量的潜在来源。此标记是临时性的，但是您可以采取一些措施来快速重新获得对 Bitwarden 的访问权限：

* **如果您使用的是 VPN 或代理服务器**，则路由您的流量的服务器也可能是恶意参与者的路由请求。断开与服务器的连接或尝试不同的服务器。
* **如果您使用的是 Tor**，则路由您的流量的 Tor 中继也可能是恶意参与者的路由请求。尝试使用不同的退出节点。

如果这些解决方案都不适合您，您可以[联系我们](https://bitwarden.com/contact/)寻求进一步帮助。同时请提供：

* 您使用的 IP 地址，以及您使用的是 VPN、代理服务器还是 Tor。
* 您使用的 Bitwarden 客户端（例如，网页密码库或桌面应用程序）。
* 发生错误时的 UTC 时间戳。
* 消息中的错误代码（通常为 `2`、`6` 或 `7`）。

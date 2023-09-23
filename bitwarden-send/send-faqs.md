# Send 常见问题

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/send-faqs/)
{% endhint %}

### 问：为什么我无法创建文件 Send？ <a href="#q-why-cant-i-create-a-file-send" id="q-why-cant-i-create-a-file-send"></a>

**答：**文本 Send 适用于所有 Bitwarden 用户，但文件 Send 的创建仅适用于高级用户，包括付费组织的成员（家庭、团队或企业）。

此外，要创建文件 Send，要求您的电子邮件地址已经过验证。

### 问：为什么我无法从 Firefox 或 Safari 浏览器扩展中创建文件 Send？ <a href="#q-why-cant-i-create-a-file-send-from-firefox-or-safari-browser-extension" id="q-why-cant-i-create-a-file-send-from-firefox-or-safari-browser-extension"></a>

**答：**可以的！但是，要在 Firefox 浏览器扩展的创建 Send 视图中浏览文件，您需要在边栏中打开扩展或使用弹出按钮弹出到新窗口：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/lTtqybY88TyGYQgPpRzLX/509b194c9d2e737aa3b287a80180af99/send-ff-popout.png?fm=webp&h=153&q=50&w=584" %}
弹出图标
{% endembed %}

### 问：为什么 Send 从我的 Send 视图中消失了？ <a href="#q-why-are-sends-missing-from-my-send-view" id="q-why-are-sends-missing-from-my-send-view"></a>

**答：**根据设计，Send 是短暂的。每个已创建的 Send 都有**最大 31 天的生命周期**，可以在[创建 Send](create-a-send.md) 时或在任何时候通过编辑 Send 来配置。当达到 Send 的[删除日期](send-lifespan.md#deletion-date)时，它将从 Bitwarden 系统中清除，发送者和任何接收者都无法访问。

### 问：Send 旁边的图标代表什么？ <a href="#q-what-do-the-icons-next-to-my-sends-indicate" id="q-what-do-the-icons-next-to-my-sends-indicate"></a>

**答：**Send 视图中的图标旨在帮助您了解已配置的[生命周期](send-lifespan.md)和[隐私](send-privacy.md)选项：

| 图标‎     | ‎含义                                                                        |
| ------- | -------------------------------------------------------------------------- |
| **🔑**  | ‎此 Send ‎‎[受密码保护‎‎](send-privacy.md#send-passwords)。‎                      |
| **⚠️**  | ‎此 Send 已‎‎[手动禁用](send-lifespan.md#manually-disable-or-delete)‎‎。‎         |
| **🕘**  | ‎此 Send 已到达指定的‎‎[到期日期‎‎](send-lifespan.md#expiration-date)。‎               |
| **🚫**  | ‎此 Send 已到达指定‎‎的[最大访问次数](send-lifespan.md#maximum-access-count)‎‎。‎        |
| **🗑️** | ‎此 Send 已到达指定的‎‎[删除日期](send-lifespan.md#deletion-date)‎‎，并‎**‎正在等待删除‎‎**。‎ |

### 问：我可以为组织禁用 Send 吗？ <a href="#q-can-i-disable-send-for-my-organization" id="q-can-i-disable-send-for-my-organization"></a>

**答：**企业组织可以使用[禁用 Send 策略](../organizations/enterprise-policies.md#disable-send)随时禁用 Send 。管理员和所有者可以从组织的**管理** → **策略**页面实施此策略。启用该策略将阻止组织成员创建或编辑任何 Send 。

### 问：可以在内部网络上使用 Send 以在网络外部共享吗？ <a href="#q-can-send-be-used-on-an-internal-network-to-share-outside-of-the-network" id="q-can-send-be-used-on-an-internal-network-to-share-outside-of-the-network"></a>

**答：**Send 被设计成一个可以通过网络共享的端到端加密的 URL。在内部网络之外使用 Send 需要打开 80 和 443 端口。如果您使用反向代理，则必须将以下变量添加到 `./bwdata/env/global-override.env`：

```systemd
globalSettings__attachment__baseDirectory=/etc/bitwarden/core/attachments
globalSettings__attachment__baseUrl=https://YOURDOMAINHERE/attachments
globalSettings__send__baseDirectory=/etc/bitwarden/core/attachments/send
globalSettings__send__baseUrl=https://YOURDOMAINHERE/attachments/send
```

{% hint style="info" %}
或者，也可以通过您的云端组织在线使用 Send。拥有自托管的组织不会被限制云端组织的使用，两个平台将以相同的订阅运行！
{% endhint %}

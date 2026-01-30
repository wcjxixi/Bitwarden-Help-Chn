# 关于 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-send/)
{% endhint %}

Bitwarden Send 是一种加密的文件和文本共享工具，可通过安全的临时链接将敏感信息直接传输给任何人。Send 可用于传输多达 1000 个加密字符的文本或多达 500 MB（或移动设备上为 100 MB）的文件，并可以通过文本、电子邮件或任何您喜欢的通信渠道[与任何人分享](receive-a-send.md)。

## 访问 Send <a href="#accessing-send" id="accessing-send"></a>

可以从任何 Bitwarden App 的 Send 视图创建、编辑、管理和删除 Send。从主导航访问 Send 视图：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7umXxS0YG58NdB3vb4kwKo/28d9a7f361875597d0d4739e46d80762/2024-12-03_10-06-39.png?_a=DAJCwlWIZAAB" %}
网页 App 中的 Send
{% endembed %}

## 使用 Send <a href="#using-send" id="using-send"></a>

使用 Bitwarden Send 是一个简单的两步过程：[创建您的 Send](create-a-send.md) 然后与[目标接收者](receive-a-send.md)分享。要创建 Send：

1、选择**新增 Send**：

{% embed url="https://bitwarden.com/assets/5ixV8tBpmNQsujpAfan69u/af68ada565dceeec687e6e8a61e2b386/New_Send.png?w=1200&fm=avif" %}
新增 Send
{% endembed %}

2、择所需的[生命周期选项](send-lifespan.md)和[隐私选项](send-privacy.md)以满足您的分享需求。

{% embed url="https://bitwarden.com/assets/5vAk27se4vF8LYczDueYex/53eda1c891e04157814f0ada56042b3d/2026-01-07_12-30-53.png?w=923&fm=avif" %}
Send 选项
{% endembed %}

3、使用您喜欢的任何通信渠道分享 Send 链接。

每个 Send 都有一个[已配置生命周期](send-lifespan.md)，以允许您跟踪 Send。每当发生一个生命周期事件（例如，到期）时，Send 将显示[一组状态图标](send-faqs.md#q-what-do-the-icons-next-to-my-sends-indicate)。图标如下：

| 图标      | 含义                                                             |
| ------- | -------------------------------------------------------------- |
| **🔑**  | 此 Send [受密码保护](send-privacy.md#send-passwords)。                |
| **⚠️**  | 此 Send 已[被手动禁用](send-lifespan.md#manually-disable-or-delete)。  |
| **🕘**  | 此 Send 已达到指定的[有效期](send-lifespan.md#expiration-date)。          |
| **🚫**  | 此 Send 已达到指定的[最大访问次数](send-lifespan.md#maximum-access-count)。  |
| **🗑️** | 此 Send 已达到指定的[删除日期](send-lifespan.md#deletion-date)，**正等待删除**。 |

## Send 安全性 <a href="#send-security" id="send-security"></a>

* **端到端加密**：Send 数据在创建时会[被加密](send-encryption.md)，只有当接收者打开 Send 链接时才会解密。与传统的密码库项目一样，Send 的内容**被加密**存储在 Bitwarden 系统中。生成的每一个 Send 链接不包含任何与 Send 内容相关的数据，因此可以安全地通过中间通信服务进行分享，而不会泄露信息。
* **动态的短暂**：Send 是为短暂分享而设计的，所以您[创建的每一个 Send](create-a-send.md) 都有一个可指定的[生命周期](send-lifespan.md)（最长 31 天），生命周期可以使用预先设置的选项或自定义的时间戳来进行选择。当达到删除日期时，该 Send 及其内容将被完全清除。使用额外的选项，如[到期日期](send-lifespan.md#expiration-date)和[最大访问次数](send-lifespan.md#maximum-access-count)，依据您的需要确保终止接收者的访问。
* **灵活的隐私**：通过[配置密码](send-privacy.md#send-passwords)设置访问权限或[对收件人隐藏您的电子邮箱地址](send-privacy.md#hide-email)来保护您的 Send 内容。对于文本 Send，您还可以选择性地要求用户[切换可见性](send-privacy.md#hide-text)，以防止暴露给无意的旁人。

{% hint style="info" %}
个人密码库项目的附件和所有 Send 使用高级订阅或组织授予的个人存储空间。组织拥有的项目上的附件使用共享的组织存储空间。了解如何[添加存储空间](../your-vault/vault-items/file-attachments.md#add-storage-space)。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经了解了 Bitwarden Send 的基础知识，我们建议：

* [创建您的第一个 Send](create-a-send.md)
* [高级会员的文件 Send](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#premium-individual)
* 更多有关 Send 的更深入概述，请参阅 [Bitwarden Send - How it works](https://bitwarden.com/blog/bitwarden-send-how-it-works/)。

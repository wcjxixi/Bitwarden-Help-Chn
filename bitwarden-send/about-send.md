# 关于 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-send/)
{% endhint %}

## 什么是 Send？ <a href="#what-is-send" id="what-is-send"></a>

Bitwarden Send 是一种安全和短暂的方案，用于传输敏感信息给**任何人**。Send 可以包含纯文本或者最大 100MB 的文件附件。每一个 Send 都会分配一个随机生成的安全链接，它可以通过文本、电子邮件或任何您喜欢的通信渠道[与任何人分享](receive-a-send.md)（包括那些没有 Bitwarden 账户的人）。每一个 Send 都是：

* **端到端加密**：Send 中的数据在创建时[被加密](send-encryption.md)，只有当接收者打开 Send 链接时才会解密。与传统的密码库项目一样，Send 的内容**被加密**存储在 Bitwarden 系统中。生成的每一个 Send 链接不包含任何与 Send 内容相关的数据，所以通过中间通信服务分享是安全的，不会将信息暴露给 Bitwarden 或任何使用的中间服务。
* **动态的短暂**：Send 是为短暂分享而设计的，所以您[创建的每一个 Send](create-a-send.md) 都有一个可指定的[生命周期](send-lifespan.md)（最长 31 天），生命周期可以使用预先设置的选项或自定义的时间戳来进行精确到分钟的配置。当达到删除日期时，该 Send 及其内容将从 Bitwarden 系统中完全清除。使用额外的选项，如[到期日期](send-lifespan.md#expiration-date)和[最大访问次数](send-lifespan.md#maximum-access-count)，依据您的需要确保终止接收者的访问。
* **可定制的隐私**：通过选择性[配置密码](send-privacy.md#send-passwords)来保护您的 Send 内容，这样无意的接收者就无法看到其包含的信息。对于文本 Send，您还可以选择性地要求接收者[切换可见性](send-privacy.md#hide-text)，以防止暴露给无意的旁人。

{% hint style="info" %}
个人密码库项目和所有 Send 的附件使用高级订阅或组织授予的个人存储空间。组织拥有的项目上的附件使用共享的组织存储空间。了解如何[添加存储空间](../your-vault/file-attachments.md#add-storage-space)。
{% endhint %}

## Send 视图 <a href="#the-send-view" id="the-send-view"></a>

通过任何 Bitwarden 应用程序的 **Send** 视图创建、编辑、管理和删除 Send。可以从全局应用程序导航访问 **Send** 视图，例如，在网页密码库中：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7umXxS0YG58NdB3vb4kwKo/7694316a119567d1ae0451f514fa4cb5/send-webvault.png?fm=webp&h=379&q=50&w=911" %}
网页密码库中的 Send
{% endembed %}

## Send 的使用 <a href="#using-send" id="using-send"></a>

Bitwarden Send 的使用是一个简单的两步过程：

1. [创建你的 Send](create-a-send.md) ，根据你的分享需求，设置[生命周期选项](send-lifespan.md)以及[隐私选项](send-privacy.md)。
2. 使用您喜欢的任何通信渠道，与[预定的接收者](receive-a-send.md)分享 Send 链接。

作为发送者，我们建议您对[已配置生命周期](send-lifespan.md)的 Send 保持跟踪。为了使这一点尽可能简单，每当发生一个生命周期事件（例如，到期）时，您的 Send 视图中的 Send 将显示[一组状态图标](send-faqs.md#q-what-do-the-icons-next-to-my-sends-indicate)。

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

现在您已经了解了 Bitwarden Send 的基础知识，我们建议：

* [创建您的第一个 Send](create-a-send.md)
* [高级会员的文件 Send](../plans-and-pricing/password-manager/about-bitwarden-plans.md#premium-individual)

# 关于 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-send/)
{% endhint %}

Bitwarden Send 是一种加密的文件和文本共享工具，可通过安全、临时的链接将敏感的文本或文件直接传输给任何人。Send 可用于传输多达 1000 个加密字符的文本或多达 500 MB（或移动设备上为 100 MB）的文件，并可以通过文本、电子邮件或任何您喜欢的通信渠道[与任何人分享](receive-a-send.md)。

{% hint style="info" %}
如果您所在的组织已在[管理 Send 策略](../../admin-console/oversight-visibility/enterprise-policies.md#manage-send)下关闭了 Send 功能，您对 Send 的访问将受到限制：

* 您无法创建新的 Send，也无法编辑现有的 Send。
* 您可以在所有 Bitwarden 客户端（网页 App 除外）的 **Send** 页面查看和删除 Send。
* 您无法通过 Bitwarden 网页 App 访问 Send 页面。

使用管理 Send 策略，组织所有者和管理员还可以控制创建新 Send 时哪些字段不可用。
{% endhint %}

## 访问 Send <a href="#accessing-send" id="accessing-send"></a>

可以从任何 Bitwarden App 的 **Send** 视图创建、编辑、管理和删除 Send。从主导航访问 Send 视图：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7umXxS0YG58NdB3vb4kwKo/c2a5f8ae8fa0bae6becb2e20e7f59390/2026-02-24_12-52-46.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>网页 App 中的 Send</p></figcaption></figure></div>

每个 Send 都有一个[配置的生命周期](send-lifespan.md)，以允许您跟踪 Send。每当发生一个生命周期事件（例如，到期）时，您创建的 Send 将显示状态图标：

<table><thead><tr><th width="100">图标</th><th>含义</th></tr></thead><tbody><tr><td><strong>🔒</strong></td><td>此 Send <a href="send-privacy.md#send-passwords">受密码保护</a>。</td></tr><tr><td><strong>⚠</strong></td><td>此 Send 已<a href="send-lifespan.md#manually-disable-or-delete">被手动禁用</a>。</td></tr><tr><td><strong>🕘</strong></td><td>此 Send 已达到指定的<a href="send-lifespan.md#expiration-date">有效期</a>。</td></tr><tr><td><strong>⚠</strong></td><td>此 Send 已达到指定的<a href="send-lifespan.md#maximum-access-count">最大访问次数</a>。</td></tr><tr><td><strong>🗑️</strong></td><td>此 Send 已达到指定的<a href="send-lifespan.md#deletion-date">删除日期</a>，<strong>正等待删除</strong>。</td></tr></tbody></table>

## 使用 Send <a href="#using-send" id="using-send"></a>

使用 Bitwarden Send 是一个三步过程：

1、[创建 Send](create-a-send.md) 并选择所需的[生命周期选项](send-lifespan.md)和[隐私选项](send-privacy.md)以满足您的分享需求。

2、通过您喜欢的任何通信渠道分享 Send 链接。

3、[接收者打开 Send 链接](receive-a-send.md)以访问其内容。

## Send 安全性 <a href="#send-security" id="send-security"></a>

<details>

<summary><strong>端到端加密</strong></summary>

数据在创建时会被[加密](send-encryption.md)，只有当接收者打开 Send 链接时才会[解密](send-encryption.md#send-decryption)。与传统的密码库项目一样，Send 的内容**被加密**存储在 Bitwarden 系统中。生成的每一个 Send 链接不包含任何与 Send 内容相关的数据，因此可以安全地通过中间通信服务进行分享，而不会泄露信息。

</details>

<details>

<summary><strong>动态的短暂</strong></summary>

Send 是为短暂分享而设计的，所以您[创建的每一个 Send](create-a-send.md) 都有一个可指定的[生命周期](send-lifespan.md)（最长 31 天），生命周期可以使用预先设置的选项或自定义的时间戳来进行选择。当达到删除日期时，该 Send 及其内容将被完全清除。使用额外的选项，如[到期日期](send-lifespan.md#expiration-date)和[最大访问次数](send-lifespan.md#maximum-access-count)，依据您的意愿确保终止接收者的访问。

</details>

<details>

<summary><strong>灵活的隐私</strong></summary>

您可以使用多种灵活的隐私选项来保护您的 Send 的内容：

* 通过[配置密码](send-privacy.md#send-passwords)设置访问权限
* 对指定的接收者[电子邮箱验证](send-privacy.md#email-verified-recipients)访问权限
* [对接收者隐藏您的电子邮箱地址](send-privacy.md#hide-email)

对于文本 Send，您还可以选择要求用户[切换可见性](send-privacy.md#hide-text)，以防止暴露给无意的旁人。

</details>

{% hint style="info" %}
个人密码库项目的附件和所有 Send 均使用高级版订阅或组织授予的个人存储空间。组织拥有的项目的附件使用共享的组织存储空间。了解如何[添加存储空间](../your-vault/vault-items/file-attachments.md#add-storage-space)。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经了解了 Bitwarden Send 的基础知识，我们建议：

* [创建您的第一个 Send](create-a-send.md)
* [升级到高级版以使用文件 Send](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#premium-individual)
* 更多有关 Send 的更深入概述，请参阅 [Bitwarden Send - How it works](https://bitwarden.com/blog/bitwarden-send-how-it-works/)。

# Send 加密

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/send-encryption/)
{% endhint %}

## Send 加密 <a href="#send-encryption" id="send-encryption"></a>

Send 是一种安全和短暂的机制，用于向任何人传输敏感信息，包括纯文本和文件。正如[关于 Send](about-send.md) 一文所指出的，Send 是**端到端加密**的，这意味着加密（如下所述）和解密发生在客户端内。当您创建一个 Send 时：

1、生成一个用于 Send 的新的 128 位秘钥。

2、使用 HKDF-SHA256，从秘钥中派生出一个 512 位的加密密钥。

3、派生的加密密钥用于 AES-256 加密 Send，包括其文件/文本数据和元数据（名称、文件名、备注等）。

{% hint style="success" %}
任何用于保护 Send 的[密码](send-privacy.md#send-passwords)都**不涉及 Send 的加密**和解密。密码纯粹是一种验证方式，但是在密码验证成功之前，将[阻止解密](send-encryption.md#send-decryption)受密码保护的 Send。
{% endhint %}

4、加密后的 Send 被上传到 Bitwarden 服务器，包括一个唯一的 Send ID，Bitwarden 会使用该 ID 来[识别要解密的 Send](send-encryption.md#send-decryption)，但**不包括**加密密钥。

## Send 解密 <a href="#send-decryption" id="send-decryption"></a>

Send 是通过打开 [Send 链接](receive-a-send.md)来解密的，Send 链接由唯一的 Send ID 和派生的加密密钥构成：

`https://vault.bitwarden.com/#/send/send_id/encryption_key`

当你访问一个 Send 链接时：

1. 网页浏览器向 Bitwarden 服务器请求 Send 访问页面。
2. Bitwarden 服务器将 Send 访问页面作为网页密码库客户端返回。
3. 网页密码库客户端在本地解析包含 Send ID 和加密密钥的 URL 片段。
4. 网页密码库客户端根据解析后的 Send ID 向服务器请求数据。加密密钥**永远不会**包含在网络请求中。
5. Bitwarden服务器将加密后的 Send 返回给网页密码库客户端。
6. 网页密码库客户端使用加密密钥在本地对 Send 进行解密。

{% hint style="success" %}
如果 Send 是有[密码保护](send-privacy.md#send-passwords)的，那么 Send 的解密将**被验证阻止**。服务器验证密码，并且仅在密码正确的情况下才返回 Send。请勿将其与用于解密的密码相混淆。
{% endhint %}

## Send 安全性 <a href="#send-security" id="send-security"></a>

传输 Bitwarden Send 链接时，您可以使用一些可选的步骤来提高其安全性：

1. 为 Send 添加密码并通过单独的通道分享密码。
2. 发送不包含密钥的链接（最后一个正斜杠之前的所有内容）并通过单独的通道发送密钥。
3. 同时使用上述两个选项。

{% hint style="success" %}
重新组装 Send URL 时，请确保同时包含 Send ID 和加密密钥。

比如：`https://vault.bitwarden.com/#/send/send_id/encryption_key`
{% endhint %}

# 加密协议

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/what-encryption-is-used/)
{% endhint %}

在将任何内容发送到云服务器进行存储之前，Bitwarden **始终**会在本地设备上加密和/或哈希数据。 **Bitwarden 服务器仅用于存储已加密的数据。**&#x66F4;多信息，请参阅[存储](../data/data-storage.md)。

所有密码库数据在存储到任何地方之前均由 Bitwarden 加密。要了解具体操作方法，请参阅 [Bitwarden 安全白皮书](../bitwarden-security-whitepaper.md)。Bitwarden 是一种零知识的解决方案，这意味着您是唯一能够获得您的密钥并能够解密您的密码库数据的一方。

{% hint style="success" %}
如果您想了解更多关于这些加密密钥是如何用来保护你的密码库的，你可以查看我们的[安全白皮书](https://bitwarden.com/images/resources/security-white-paper-download.pdf)。
{% endhint %}

## 认证的对称加密 <a href="#authenticated-symmetric-encryption" id="authenticated-symmetric-encryption"></a>

Bitwarden 采用高级加密标准的密码块链模式 (AES-CBC)，并使用 256 位密钥。AES 是一种密码学标准，被美国政府和全球其他领先的安全机构用于保护最高机密数据。正确的实施（使用 CSPRNG 生成，或由强主密码通过 KDF 派生）加上足够强的加密密钥，AES 被认为是不可破解的。

为确保 AES 加密的完整性与可验证，Bitwarden 同时采用基于哈希的消息认证码 (HMAC) 配合 SHA-256 算法。HMAC 是 Bitwarden 为验证加密数据来源可信且传输无损而采取的额外措施。该组合方案称为 AES256-CBC-HMAC-SHA256。

## 公钥密码学 <a href="#public-key-cryptography" id="public-key-cryptography"></a>

公钥密码学，也称为非对称密码学，为 Bitwarden 的组织管理和紧急访问等功能提供安全数据共享支持。Bitwarden 采用 RSA 加密系统，并结合最优非对称加密填充 (OAEP )方案。

{% hint style="info" %}
Bitwarden 目前正在研究后量子密码学选项。
{% endhint %}

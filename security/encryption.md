# =加密方式

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/what-encryption-is-used/)
{% endhint %}

Bitwarden 为您的密码库使用 [AES-CBC](encryption.md#aes-cbc) 256 位加密方式，并使用 [PBKDF2](encryption.md#pbkdf2) SHA-256 来派生加密密钥。

在将任何内容发送到云服务器进行存储之前，Bitwarden **始终**会在本地设备上加密和/或哈希数据。 **Bitwarden 服务器仅用于存储已加密的数据。**有关更多信息，请参阅[存储](storage.md)。

密码库数据只能使用从您的主密码派生的密钥来解密。Bitwarden 是一种零知识的解决方案，这意味着您是唯一能够获得您的密钥并能够解密您的密码库数据的一方。

{% hint style="success" %}
我们鼓励您访问我们的[交互式加密页面](https://bitwarden.com/help/crypto.html)，亲自了解 Bitwarden 是如何对您的数据进行加密的。

如果你想了解更多关于这些加密密钥是如何用来保护你的密码库的，你可以查看我们的[安全白皮书](https://bitwarden.com/images/resources/security-white-paper-download.pdf)。
{% endhint %}

## AES-CBC

[AES](https://en.wikipedia.org/wiki/Advanced\_Encryption\_Standard)-CBC（[Cipher Block Chaining](https://en.wikipedia.org/wiki/Block\_cipher\_mode\_of\_operation#Cipher\_block\_chaining\_\(CBC\))）是一种加密技术的标准，被美国政府和世界各地的其他政府机构用于保护顶级机密数据。正确的实施加上复杂的加密密钥（您的主密码），AES 被认为是坚不可摧的。

## PBKDF2

[PBKDF2](https://en.wikipedia.org/wiki/PBKDF2) SHA-256 用于从您的主密码派生出加密密钥。Bitwarden 使用您的电子邮件地址将您的主密码在**本地**进行[盐化和哈希](https://www.okta.com/blog/2019/03/what-are-salted-passwords-and-password-hashing/)处理，然后再传输到我们的服务器。Bitwarden 服务器收到哈希的密码后，会使用一个加密安全的随机值再次对其进行盐化，并再次对其哈希，然后存储在我们的数据库中。

PBKDF2 使用的默认迭代数是客户端上的 100,001 次迭代（可从您的帐户设置中配置客户端迭代数），当存储到我们的服务器上时会再进行 100,000 次迭代（默认情况下总计为 200,001 次迭代）。组织密钥使用 [RSA-2048](https://en.wikipedia.org/wiki/RSA\_numbers#RSA-2048) 共享。

所使用的哈希函数是单向哈希，这意味着 Bitwarden 的任何人都**无法对其逆向工程**，从而泄露您的主密码。即使 Bitwarden 被黑客攻击，也无任何办法获取您的主密码。

## 更改 KDF 迭代 <a href="#changing-kdf-iterations" id="changing-kdf-iterations"></a>

## Argon2id

## 调用的加密库 <a href="#invoked-crypto-libraries" id="invoked-crypto-libraries"></a>

**Bitwarden 不编写任何加密代码**。Bitwarden 仅从流行且信誉良好的加密库中调用加密，这些库由加密专家编写和维护。我们使用以下加密库：

* JavaScript（网页端、浏览器扩展、桌面和 CLI 密码库）
  * [Web Crypto](https://w3c.github.io/webcrypto/Overview.html)
  * [Node.js Crypto](https://nodejs.org/api/crypto.html)
  * [Forge](https://github.com/digitalbazaar/forge)
* C＃（移动端）
  * CommonCrypto（iOS，Apple）
  * Javax.Crypto（Android，Oracle）
  * [BouncyCastle](http://www.bouncycastle.org/csharp/)（Android）

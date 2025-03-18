# 加密方式

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/what-encryption-is-used/)
{% endhint %}

Bitwarden 为您的密码库使用 [AES-CBC](encryption.md#aes-cbc) 256 位加密方式，并使用 [PBKDF2](encryption.md#pbkdf2) SHA-256 来派生加密密钥。

在将任何内容发送到云服务器进行存储之前，Bitwarden **始终**会在本地设备上加密和/或哈希数据。 **Bitwarden 服务器仅用于存储已加密的数据。**&#x6709;关更多信息，请参阅[存储](storage.md)。

密码库数据只能使用从您的主密码派生的密钥来解密。Bitwarden 是一种零知识的解决方案，这意味着您是唯一能够获得您的密钥并能够解密您的密码库数据的一方。

{% hint style="success" %}
我们鼓励您访问我们的[交互式加密页面](https://bitwarden.com/help/crypto.html)，亲自了解 Bitwarden 是如何对您的数据进行加密的。

如果你想了解更多关于这些加密密钥是如何用来保护你的密码库的，你可以查看我们的[安全白皮书](https://bitwarden.com/images/resources/security-white-paper-download.pdf)。
{% endhint %}

## AES-CBC

[AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)-CBC（[Cipher Block Chaining](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation#Cipher_block_chaining_\(CBC\))）是一种加密技术的标准，被美国政府和世界各地的其他政府机构用于保护顶级机密数据。正确的实施加上复杂的加密密钥（您的主密码），AES 被认为是坚不可摧的。

## PBKDF2

[PBKDF2](https://en.wikipedia.org/wiki/PBKDF2) SHA-256 用于从您的主密码派生出加密密钥，您也可以选择 [Argon2](encryption.md#argon2id) 作为替代方案。Bitwarden 使用您的电子邮件地址将您的主密码在**本地**进行[盐化和哈希](https://www.okta.com/blog/2019/03/what-are-salted-passwords-and-password-hashing/)处理，然后再传输到我们的服务器。Bitwarden 服务器收到哈希的密码后，会使用一个加密安全的随机值再次对其进行盐化，并再次对其哈希，然后存储在我们的数据库中。

PBKDF2 使用的默认迭代数是客户端上的 600,001 次迭代（可从您的账户设置中配置客户端迭代数），当存储到我们的服务器上时会再进行 100,000 次迭代（默认情况下总计为 700,001 次迭代）。组织密钥使用 [RSA-2048](https://en.wikipedia.org/wiki/RSA_numbers#RSA-2048) 共享。

{% hint style="success" %}
Bitwarden 使用的默认迭代数在 2023 年 2 月增加。在此之后创建的账户将使用 600,00，但是如果您在此之前创建了账户，则应增加迭代次数。可以在以下部分中找到这样做的说明。
{% endhint %}

所使用的哈希函数是单向哈希，这意味着 Bitwarden 的任何人都**无法对其逆向工程**，从而泄露您的主密码。即使 Bitwarden 被黑客攻击，也无任何办法获取您的主密码。

### 更改 KDF 迭代 <a href="#changing-kdf-iterations" id="changing-kdf-iterations"></a>

如上所述，Bitwarden 使用一个更安全的默认数值，但是您可以从网页密码库的**账户设置** → **安全** → **密钥**菜单更改迭代数。

更改迭代数有助于保护您的主密码免遭攻击者的暴力破解，但不应将其视为一开始就使用强主密码的替代方法。更改迭代数将重新加密受保护的对称密钥并更新身份验证哈希，就像正常的主密码更改一样，但不会轮换对称加密密钥，因此密码库数据不会被重新加密。有关重新加密数据的信息，请参阅[此处](account-encryption-key.md)。

在 CPU 较慢的设备上登录（以及解锁）Bitwarden 时，将 KDF 迭代设置得太高可能会导致性能不佳。我们建议您以 50,000 为增量增加该值，然后测试您的所有设备。

当您更改迭代数时，您将从所有客户端注销。尽管在更改 KDF 迭代数时不存在轮换加密密钥所涉及的风险，但我们仍然建议事先导出您的密码库数据。

## Argon2id

Argon2 是 2015 年[密码哈希竞赛](https://www.password-hashing.net/)的获胜者，可作为 PBKDF2 的替代品（[了解更多](kdf-algorithms.md)）。该算法共有三个版本，Bitwarden 已经实现了 [OWASP 推荐](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)的 Argon2id。Argon2id 是其他版本的混合体，结合了数据相关和数据无关的内存访问，这使其具有 Argon2i 对侧通道缓存定时攻击的一些抵抗力以及 Argon2d 对 GPU 破解攻击的大部分抵抗力（[来源](https://github.com/p-h-c/phc-winner-argon2)）。

默认情况下，Bitwarden 设置为分配 64 MB 内存，迭代 3 次，并跨 4 个线程执行此操作。这些默认值高于[当前的 OWASP 建议](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html#introduction)，但如果您要更改您的设置，这里有一些提示：

* 增加 **KDF 迭代**将线性增加运行时间。
* 您可以使用的 **KDF 并行**数量取决于您机器的 CPU。一般来说，最大并行数 = 核心数量 x 2。

{% hint style="info" %}
KDF 内存值大于 48 MB 的 Argon2id 用户每次启动 iOS 自动填充或通过共享表创建新 Send 时，都会收到一个警告对话框。若要避免此消息，请调整 Argon2id 设置或启用[生物识别解锁](../your-vault/unlocking-with-biometrics.md)。
{% endhint %}

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

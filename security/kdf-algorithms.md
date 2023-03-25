# KDF 算法

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/kdf-algorithms/)
{% endhint %}

Bitwarden 首先在创建帐户时使用密钥派生函数 (KDF) 从输入的主密码中派生出帐户的主密钥，作为帐户主密码哈希的输入（[了解更多](../business-resources/bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。每当用户通过身份验证时，例如解锁密码库或满足[主密码重新提示](../your-vault/vault-items.md#protect-individual-items)时，都会重复该过程，以便可以将新派生的哈希值与最初派生的哈希值进行比较。如果它们匹配，则用户通过身份验证。

KDF 被用来阻止针对主密码的暴力或字典攻击。KDF 迫使攻击者的机器为每次密码猜测计算大量的哈希值，从而增加攻击者的成本。

目前有两种 KDF 算法可用于 Bitwarden：**PBKDF2** 和 **Argon2**。每种算法都有一系列可用选项，可用于增加攻击者的时间和费用，或「工作因素」。

## PBKDF2

基于密码的密钥派生函数 2 (PBKDF2) [由 NIST 推荐](https://pages.nist.gov/800-63-3/sp800-63b.html#memsecretver)，已被 Bitwarden 实现，只要未改变其默认值，它就能满足 FIPS-140 的要求。

PBKDF2 已被 Bitwarden 实现，其工作原理是将您的主密码与您的用户名混合，并通过单向哈希算法 (HMAC-SHA-256) 运行结果值以创建固定长度的哈希值。该值再次用您的用户名加盐，并散列可配置的次数（**KDF 迭代**）。所有迭代后的结果值就是您的主密钥，它充当主密码散列的输入，用于在用户登录时验证该用户（了解更多）。

默认情况下，Bitwarden 设置为迭代 600,000 次，这是 OWASP 为 HMAC-SHA-256 实现推荐的。只要用户不将此值设置得更低，实现就符合 FIPS-140，但如果您选择更改设置，这里有一些提示：

* 更多的 KDF 迭代将**同时**增加攻击者破解密码所需的时间，**以及**合法用户登录所需的时间。
* 我们建议您以 50,000 为增量增加该值并测试您的所有设备。

## Argon2id

Argon2 是 2015 年[密码哈希竞赛](https://www.password-hashing.net/)的获胜者。该算法共有三个版本，Bitwarden 已经实现了 [OWASP 推荐](https://cheatsheetseries.owasp.org/cheatsheets/Password\_Storage\_Cheat\_Sheet.html)的 Argon2id。Argon2id 是其他版本的混合体，结合了数据相关和数据无关的内存访问，这使其具有 Argon2i 对侧通道缓存定时攻击的一些抵抗力以及 Argon2d 对 GPU 破解攻击的大部分抵抗力（[来源](https://github.com/p-h-c/phc-winner-argon2)）。

Argon2 已被 Bitwarden 实现，其工作原理是将您的主密码与您的用户名混合，并通过单向哈希算法 (BLAKE2b) 运行结果值以创建固定长度的哈希值。

Argon2 分配一部分内存（**KDF 内存**）然后用已计算的哈希值填充它直到填满。这是重复的，从它在第一个停止的内存的后续部分开始，在多个线程（**KDF 并行**）上迭代多次（**KDF 迭代**）。所有迭代后的结果值是您的主密钥，它充当主密码哈希的输入，用于在用户登录时验证该用户（[了解更多](../business-resources/bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。

默认情况下，Bitwarden 设置为分配 64 MiB 内存，迭代 3 次，并跨 4 个线程执行此操作。这些默认值高于[当前的 OWASP 建议](https://cheatsheetseries.owasp.org/cheatsheets/Password\_Storage\_Cheat\_Sheet.html#introduction)，但如果您要更改您的设置，这里有一些提示：

* 增加 **KDF 迭代**将线性增加运行时间。
* 您可以使用的 **KDF 并行**数量取决于您机器的 CPU。一般来说，最大。并行数 = 核心数量 x 2。

## 更改 KDF 算法 <a href="#changing-kdf-algorithm" id="changing-kdf-algorithm"></a>

{% hint style="info" %}
**2023-02-14**：2023.2.0 及以后版本的 Bitwarden 客户端支持 Argon2，通过网页密码库切换到 Argon2 可能意味着其他客户端在更新之前无法加载您的密码库。通常在发布后一周内更新这些客户端。
{% endhint %}

要更改您的 KDF 算法，请导航至网页密码库的**帐户设置** → **安全** → **密钥**页面。更改算法将重新加密受保护的对称密钥并更新身份验证哈希，就像正常的主密码更改一样，但不会轮换对称加密密钥，因此密码库数据不会被重新加密。有关重新加密数据的信息，请参阅[此处](account-encryption-key.md)。

当您更改了算法后，您将从所有客户端注销。尽管在更改算法时不存在[轮换加密密钥](account-encryption-key.md)所涉及的风险，但我们仍然建议事先[导出您的密码库数据](../import-export/export-vault-data.md)。

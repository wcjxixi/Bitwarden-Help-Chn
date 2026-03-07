# 加密密钥派生

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/kdf-algorithms/)
{% endhint %}

Bitwarden 在创建账户时首先使用密钥派生函数 (KDF)，通过输入的主密码派生出账户的主密钥，该主密码随后作为输入生成账户的主密码哈希值（[了解更多](../bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。每当用户通过身份验证时，例如解锁密码库或满足[主密码重新提示](../../password-manager/your-vault/vault-items/vault-items.md#protect-individual-items)时，都会重复该过程，将新派生的哈希值与最初派生的哈希值进行比较。若两者匹配，则用户通过身份验证。

KDF 被用来阻止针对主密码的暴力或字典攻击。KDF 迫使攻击者的机器为每次密码猜测计算大量的哈希值，从而增加攻击者的成本。

Bitwarden 目前有两种 KDF 算法用于密码派生：[PBKDF2](encryption-key-derivation.md#pbkdf2) 和 [Argon2](encryption-key-derivation.md#argon2id)。每种算法都有一系列可用选项，可用于增加攻击者的时间和费用，或「工作因素」。

## PBKDF2

基于密码的密钥派生函数 2 (PBKDF2) [由 NIST 推荐](https://pages.nist.gov/800-63-3/sp800-63b.html#memsecretver)，已被 Bitwarden 实现，只要未改变其默认值，它就能满足 FIPS-140 的要求。

PBKDF2 已被 Bitwarden 实现，其工作原理是将您的主密码与您的用户名混合，并通过单向哈希算法 (HMAC-SHA-256) 运行结果值以创建固定长度的哈希值。该值再次用您的用户名加盐，并散列可配置的次数（**KDF 迭代**）。所有迭代后的结果值就是您的主密钥，它充当主密码散列的输入，用于在用户登录时验证该用户（[了解更多](../bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。

{% hint style="info" %}
Bitwarden 执行超出客户端和服务器之间配置的额外迭代。主密码哈希的默认总迭代次数为 700,000 次。更多详细信息，请参阅 [Bitwarden 安全白皮书](../bitwarden-security-whitepaper.md)。
{% endhint %}

默认情况下，Bitwarden 设置为迭代 600,000 次，这是 [OWASP 为 HMAC-SHA-256 实现推荐的](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html#pbkdf2)。只要用户不将此值设置得更低，实现就符合 FIPS-140。

## Argon2id

Argon2 是 2015 年[密码哈希竞赛](https://www.password-hashing.net/)的获胜者。该算法共有三个版本，Bitwarden 已经实现了 [OWASP 推荐](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)的 Argon2id。Argon2id 是其他版本的混合体，结合了数据相关和数据无关的内存访问，这使其具有 Argon2i 对侧通道缓存定时攻击的一些抵抗力以及 Argon2d 对 GPU 破解攻击的大部分抵抗力（[来源](https://github.com/p-h-c/phc-winner-argon2)）。

Argon2 已被 Bitwarden 实现，其工作原理是将您的主密码与您的用户名混合，并通过单向哈希算法 (BLAKE2b) 运行结果值以创建固定长度的哈希值。

Argon2 分配一部分内存（**KDF 内存**）然后用已计算的哈希值填充它直到填满。这是重复的，从它在第一个停止的内存的后续部分开始，在多个线程（**KDF 并行**）上迭代多次（**KDF 迭代**）。所有迭代后的结果值是您的主密钥，它充当主密码哈希的输入，用于在用户登录时验证该用户（[了解更多](../bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。

默认情况下，Bitwarden 设置为分配 64 MiB 内存，迭代 3 次，并跨 4 个线程执行此操作。这些默认值高于[当前 OWASP 的推荐](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html#introduction)，但如果您要更改您的设置，这里有一些提示：

* 增加 **KDF 迭代**将线性增加运行时间。
* 您可以使用的 **KDF 并行**数量取决于您机器的 CPU。一般来说，最大并行数 = 核心数量 x 2。

{% hint style="info" %}
KDF 内存值高于 64 MiB 的 Argon2id 用户每次启动 iOS 自动填充或通过共享表创建新的 Send 时都会收到警告对话框。要避免出现此消息，请调整 Argon2id 设置或启用[生物识别解锁](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#use-unlock-with-biometrics)。
{% endhint %}

## 更改 KDF 算法 <a href="#changing-kdf-algorithm" id="changing-kdf-algorithm"></a>

{% hint style="info" %}
**2023-02-14**：2023.2.0 及以后版本的 Bitwarden 客户端支持 Argon2，通过网页密码库切换到 Argon2 可能意味着其他客户端在更新之前无法加载您的密码库。通常在发布后一周内更新这些客户端。
{% endhint %}

更改迭代次数可以帮助保护您的主密码免遭攻击者暴力破解，但首先不应将其视为使用强主密码的替代品。强大的主密码始终是您 Bitwarden 账户的第一道也是最好的防线。

更改 KDF 算法会重新加密受保护的对称密钥并更新身份验证哈希，就像普通的主密码更改一样，但不会轮换[对称加密密钥](../bitwarden-security-whitepaper.md#rotating-the-account-encryption-key)，因此密码库数据不会被重新加密。了解更多有关[重新加密数据](encryption-key-rotation.md#how-to-rotate-your-encryption-key)的信息。

{% hint style="danger" %}
在对加密设置进行**任何**更改之前，建议您先[备份您的个人密码库数据](../../password-manager/import-and-export/export-vault-data.md)。
{% endhint %}

要更改您的 KDF 算法：

1、在网页 App 中，转到**设置** → **安全**。

2、选择**密钥**：

{% embed url="https://bitwarden.com/assets/wdv28A2B5yaUswQcFvT9j/ef47b457ed64f67ee84b4289ad3477a4/2026-03-06_08-57-10.png?w=800&fm=avif" %}
加密密钥设置
{% endembed %}

3、从**算法**下拉菜单中，选择 **PBKDF2 SHA-256** 或 **Argon2id**。

4、（可选）更新显示的其他设置。

5、选择**更新加密设置**。

更高的 KDF 迭代会增加攻击者破解密码所需的时间**以及**合法用户登录所需的时间。将 KDF 迭代设置得太高可能会导致在 CPU 较慢的设备上登录和解锁 Bitwarden 时性能不佳。我们建议以 100,000 为增量增加该值，然后在所有设备上进行测试。

对于 **PBKDF2 SHA-256**，默认 KDF 迭代设置是 600,000。

对于 **Argon2id**，默认设置为：

* KDF 内存：64
* KDF 迭代：3
* KDF 并行度：4

### 低 KDF 迭代 <a href="#low-kdf-iterations" id="low-kdf-iterations"></a>

在 [2026.2.1 版本](../../release-notes.md#id-2026.2.1)中，Bitwarden 将 [PBKDF2](https://bitwarden.atlassian.net/jira/software/projects/DHCTW/issues/DHCTW-956?jql=project%20%3D%20%22DHCTW%22%20AND%20statusCategory%20%3D%20%22Done%22%20AND%20text%20~%20%22kdf%22%20ORDER%20BY%20created%20DESC\&referrer=agility) KDF 迭代的最小次数增加到了 600,000，以符合 OWASP 指南。这加强了密码库加密，以抵御拥有日益强大设备的黑客。

如果您使用 PBKDF2 算法并将 KDF 迭代设置为低于 600,000，您将收到一条**更新 KDF 设置**的消&#x606F;**。**&#x5982;果您看到此消息，请输入您的主密码然后选择**更新设置**以将 PBKDF2 迭代增加到 600,000。您无需重新登录任何客户端即可发生此更改。如果您点击**稍后**，此消息将在 24 小时后再次出现，以鼓励您保护您的账户。或者，为了您的方便，您将不会看到此提示，并且如果您使用主密码解锁或登录，则会自动进行此增加动作。

### HKDF

HKDF 是基于 HMAC 的密钥派生函数 (KDF)，在 [RFC 5869](https://datatracker.ietf.org/doc/html/rfc5869) 中进行了规范，在业界广泛使用，并由 NIST 在 [SP 800-56](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-56Cr2.pdf) 中推荐。 Bitwarden 使用 HKDF 从非密码类材料（例如其他密钥或加密随机生成的材料）中派生加密密钥。

# 加密密钥派生

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/kdf-algorithms/)
{% endhint %}

Bitwarden 在创建账户时首先使用密钥派生函数 (KDF)，通过输入的主密码派生出账户的主密钥，该主密码随后作为输入生成账户的主密码哈希值（[了解更多](../bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。每当用户通过身份验证时，例如解锁密码库或满足[主密码重新提示](../../password-manager/your-vault/vault-items/vault-items.md#protect-individual-items)时，都会重复该过程，将新派生的哈希值与最初派生的哈希值进行比较。若两者匹配，则用户通过身份验证。

KDF 被用来阻止针对主密码的暴力或字典攻击。KDF 迫使攻击者的机器为每次密码猜测计算大量的哈希值，从而增加攻击者的成本。

Bitwarden 目前有两种 KDF 算法用于密码派生：**PBKDF2** 和 **Argon2**。每种算法都有一系列可用选项，可用于增加攻击者的时间和费用，或「工作因素」。

## PBKDF2

基于密码的密钥派生函数 2 (PBKDF2) [由 NIST 推荐](https://pages.nist.gov/800-63-3/sp800-63b.html#memsecretver)，已被 Bitwarden 实现，只要未改变其默认值，它就能满足 FIPS-140 的要求。

PBKDF2 已被 Bitwarden 实现，其工作原理是将您的主密码与您的用户名混合，并通过单向哈希算法 (HMAC-SHA-256) 运行结果值以创建固定长度的哈希值。该值再次用您的用户名加盐，并散列可配置的次数（**KDF 迭代**）。所有迭代后的结果值就是您的主密钥，它充当主密码散列的输入，用于在用户登录时验证该用户（[了解更多](../bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。

{% hint style="info" %}
Bitwarden 执行超出客户端和服务器之间配置的额外迭代。主密码哈希的默认总迭代次数为 700,000 次。更多详细信息，请参阅 [Bitwarden 安全白皮书](../bitwarden-security-whitepaper.md)。
{% endhint %}

默认情况下，Bitwarden 设置为迭代 600,000 次，这是 [OWASP 为 HMAC-SHA-256 实现推荐的](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html#pbkdf2)。只要用户不将此值设置得更低，实现就符合 FIPS-140，但如果您选择更改设置，这里有一些提示：

* 更多的 KDF 迭代将**同时**增加攻击者破解密码所需的时间，**以及**合法用户登录所需的时间。

## Argon2id

Argon2 是 2015 年[密码哈希竞赛](https://www.password-hashing.net/)的获胜者。该算法共有三个版本，Bitwarden 已经实现了 [OWASP 推荐](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)的 Argon2id。Argon2id 是其他版本的混合体，结合了数据相关和数据无关的内存访问，这使其具有 Argon2i 对侧通道缓存定时攻击的一些抵抗力以及 Argon2d 对 GPU 破解攻击的大部分抵抗力（[来源](https://github.com/p-h-c/phc-winner-argon2)）。

Argon2 已被 Bitwarden 实现，其工作原理是将您的主密码与您的用户名混合，并通过单向哈希算法 (BLAKE2b) 运行结果值以创建固定长度的哈希值。

Argon2 分配一部分内存（**KDF 内存**）然后用已计算的哈希值填充它直到填满。这是重复的，从它在第一个停止的内存的后续部分开始，在多个线程（**KDF 并行**）上迭代多次（**KDF 迭代**）。所有迭代后的结果值是您的主密钥，它充当主密码哈希的输入，用于在用户登录时验证该用户（[了解更多](../bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)）。

默认情况下，Bitwarden 设置为分配 64 MB 内存，迭代 3 次，并跨 4 个线程执行此操作。这些默认值高于[当前 OWASP 的推荐](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html#introduction)，但如果您要更改您的设置，这里有一些提示：

* 增加 **KDF 迭代**将线性增加运行时间。
* 您可以使用的 **KDF 并行**数量取决于您机器的 CPU。一般来说，最大并行数 = 核心数量 x 2。

{% hint style="info" %}
KDF 内存值高于 64 MiB 的 Argon2id 用户每次启动 iOS 自动填充或通过共享表创建新的 Send 时都会收到警告对话框。要避免出现此消息，请调整 Argon2id 设置或启用[生物识别解锁](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#use-unlock-with-biometrics)。
{% endhint %}

## 更改 KDF 算法 <a href="#changing-kdf-algorithm" id="changing-kdf-algorithm"></a>

{% hint style="info" %}
**2023-02-14**：2023.2.0 及以后版本的 Bitwarden 客户端支持 Argon2，通过网页密码库切换到 Argon2 可能意味着其他客户端在更新之前无法加载您的密码库。通常在发布后一周内更新这些客户端。
{% endhint %}

要更改您的 KDF 算法，请导航至网页密码库的**账户设置** → **安全** → **密钥**页面。更改算法将重新加密受保护的对称密钥并更新身份验证哈希，就像正常的主密码更改一样，但不会轮换对称加密密钥，因此密码库数据不会被重新加密。有关重新加密数据的信息，请参阅[此处](encryption-key-rotation.md)。

将 KDF 迭代设置得太高可能会导致在 CPU 较慢的设备上登录和解锁 Bitwarden 时性能不佳。我们建议以 100,000 为增量增加该值，然后在所有设备上进行测试。

{% hint style="danger" %}
在对加密设置进行**任何**更改之前，建议您先备份您的个人密码库数据。有关详细信息，请参阅[导出密码库数据](../../password-manager/import-and-export/export-vault-data.md)。
{% endhint %}

### 低 KDF 迭代 <a href="#low-kdf-iterations" id="low-kdf-iterations"></a>

在 [2023.2.0 版本](https://bitwarden.com/help/releasenotes/#202320)中，根据已更新的 OWASP 指南，Bitwarden 将使用 [PBKDF2](https://bitwarden.atlassian.net/jira/software/projects/DHCTW/issues/DHCTW-956?jql=project%20%3D%20%22DHCTW%22%20AND%20statusCategory%20%3D%20%22Done%22%20AND%20text%20~%20%22kdf%22%20ORDER%20BY%20created%20DESC\&referrer=agility) 算法的账户的默认 KDF 迭代次数增加到了 600,000。这加强了密码库加密，以抵御拥有日益强大设备的黑客。如果您使用 PBKDF2 算法并将 KDF 迭代设置为低于 600,000，**您将收到一条鼓励您增加 KDF 设置的警告消息。**

如果您看到此消息，请选择**更新 KDF 设置**按钮并将 PBKDF2 迭代次数增加到至少 600,000，或者将您的 KDF 算法更改为具有默认设置的 [Argon2id](https://bitwarden.atlassian.net/jira/software/projects/DHCTW/issues/DHCTW-956?jql=project%20%3D%20%22DHCTW%22%20AND%20statusCategory%20%3D%20%22Done%22%20AND%20text%20~%20%22kdf%22%20ORDER%20BY%20created%20DESC\&referrer=agility)。当您保存这些更改时，您将从所有客户端被注销，因此请确保您知道您的主密码并且您的两步登录方式可用。

更改迭代次数有助于保护您的主密码免遭攻击者的暴力破解，但不应将其视为一开始就使用强主密码的替代方法。强大的主密码始终是您 Bitwarden 账户的第一道也是最好的防线。

### HKDF

HKDF 是基于 HMAC 的密钥派生函数 (KDF)，在 RFC 5869 中进行了规范，在业界广泛使用，并由 NIST 在 SP 800-56 中推荐。 Bitwarden 使用 HKDF 从非密码材料（例如其他密钥或加密随机生成的材料）中派生加密密钥。

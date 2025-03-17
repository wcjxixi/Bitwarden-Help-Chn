# Bitwarden 安全白皮书

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/bitwarden-security-white-paper/)
{% endhint %}

## 概述 <a href="#overview" id="overview"></a>

### 每个人的联系比以往任何时候都更加紧密 <a href="#everyone-is-more-connected-than-ever" id="everyone-is-more-connected-than-ever"></a>

在当今社会，与互联网连接的设备和服务比以往任何时候都更加重要。随着越来越多的公司提供创新的软件即服务产品来改善用户的家庭和工作生活，凭据和机器机密的数量呈指数级增长。对他们安全的威胁也是如此。

### 网络安全威胁很大，但实践很少 <a href="#cybersecurity-threats-are-high-but-practices-are-low" id="cybersecurity-threats-are-high-but-practices-are-low"></a>

用户和客户数据面临的威胁不断增加。几乎每周都会有数据泄露或勒索软件攻击的新闻出现，而这些仅仅是规模大到足以被公布的事件。2023 年，[IBM 报告](https://www.ibm.com/reports/data-breach)称，考虑到调查成本、法律费用、机会成本和客户信任损失，美国数据泄露的平均成本接近 948 万美元。

[Verizon](https://www.verizon.com/business/resources/reports/2023-data-breach-investigations-report-dbir.pdf) 的研究表明，在数据泄露事件中，被泄露的凭据占 86%。这包括使用在其他外泄事件中被猜测、钓鱼或泄露的密码。

面对这些威胁，人们希望企业为员工尽可能多地提供培训和工具，但 [Bitwarden 的研究](https://bitwarden.com/resources/2023-password-decisions-survey-results/)表明，用户并不总是遵循最佳实践，其中 90% 的受访者表示他们重复使用了密码。

安全专家建议用户为每个账户使用不同的随机生成的密码。但如何管理所有这些密码呢？如何在整个组织中保持良好的密码习惯呢？

### Bitwarden 帮助保护个人、企业和基础设施的安全 <a href="#bitwarden-helps-secure-individuals-businesses-and-infrastructure-secrets" id="bitwarden-helps-secure-individuals-businesses-and-infrastructure-secrets"></a>

Bitwarden 提供了一系列安全产品，旨在保护每个人，防止数据泄露，并确保工作效率。

Bitwarden Password Manager 为用户提供了创建、存储和共享密码的工具，同时保持了最高级别的安全性。它是存储所有登录信息、密码和其他敏感信息的最简单和最安全的方法，同时还能方便地在所有设备之间保持同步。

Bitwarden Secrets Manager 使开发人员、DevOps 和 IT 团队能够存储、共享和自动处理机器机密，例如身份验证密钥、数据库密码和 API 密钥。这种端到端加密的机密管理解决方案支持安全地部署基础设施和应用代码，没有暴露关键机器机密的风险。

Bitwarden Passwordless.dev 提供了开发人员所需的 API 和工具，以实施基于 FIDO2 WebAuthn 通行密钥身份验证（用于网站和应用程序的下一代安全凭据验证）。

### 维护安全性和合规性 <a href="#maintaining-security-and-compliance" id="maintaining-security-and-compliance"></a>

Bitwarden 的解决方案、软件、基础设施和安全流程都是以多层次、深入防御的方式从头设计的。Bitwarden 的安全与合规计划基于 ISO27001 信息安全管理体系 (ISMS)。我们定义了管理我们的安全政策和流程的政策，并不断更新我们的安全计划，以符合适用的法律、行业和监管要求。

Bitwarden 遵守行业标准的应用安全准则，包括一个专门的安全工程团队，并定期审查应用源代码和 IT 基础设施，以检测、验证和修复任何安全漏洞。

本白皮书概述了 Bitwarden 的安全原则，并提供了其他文件的链接，这些文件提供了在特定领域的更多细节。

## Bitwarden 安全原则 <a href="#bitwarden-security-principles" id="bitwarden-security-principles"></a>

使用 Bitwarden 产品保护用户数据是 Bitwarden 系统和员工以及用户本身之间的合作关系。本章节将概括介绍 Bitwarden 使用的关键安全措施以及 Bitwarden 为用户提供的用于保护 Bitwarden 中存储的数据的工具。

### 关键安全措施 <a href="#key-security-measures" id="key-security-measures"></a>

Bitwarden 采用以下关键的安全措施来保护 Bitwarden 中存储的数据：

**端到端加密**：通过端到端 AES-CBC 256 位加密以及 HMAC 身份验证、加盐哈希和密钥导出函数（例如 [PBKDF2 SHA-256](encryption.md#pbkdf2) 或 [Argon2id](encryption.md#argon2id) ）来锁定您的密码和私人信息。所有的加密密钥都由您设备上的客户端生成和管理，并且所有的加密都在本地完成。[这里](bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)查看更多详情。

**零知识加密**：Bitwarden 团队成员无法查看您的密码。您的数据使用您的个人电子邮件和主密码进行端到端加密。Bitwarden 绝不会存储也无法访问您的主密码或加密密钥。

**安全密码共享**：Bitwarden 支持在整个组织中与用户安全地共享和管理敏感数据。非对称和对称加密的组合可以在共享敏感信息时对其进行保护。

**开源和可用源码**：所有 Bitwarden 软件产品的源代码都托管在 [GitHub](https://github.com/bitwarden) 上，我们欢迎大家对 Bitwarden 代码库进行审查、审计和贡献。Bitwarden 源代码由著名的第三方安全审计公司以及独立的安全研究人员进行审计。此外，[Bitwarden 漏洞披露计划](https://hackerone.com/bitwarden?type=team\&view_policy=true)还得到了 HackerOne 黑客社区的帮助，以使 Bitwarden 更加安全。

**隐私设计**：Bitwarden 将你所有的登录信息存储在一个加密的密码库中，并在你所有的设备上同步。由于它在离开你的设备之前就已经完全加密了，因此只有你才能访问你的数据。即使 Bitwarden 团队也无法读取您的数据（即使我们想读取）。

**安全审计**：每年至少对应用程序和/或平台进行一次第三方安全审查和评估。

**合规：**&#x42;itwarden 符合 AICPA SOC2 Type 2 /数据隐私框架、GDPR 和 CCPA 法规。[了解更多](compliance-audits-and-certifications.md)。

### 适用于用户的安全工具 <a href="#security-tools-for-users" id="security-tools-for-users"></a>

以下工具由 Bitwarden 提供，个人用户和企业必须采取行动，以优化账户保护和避免锁定：

#### 主密码 <a href="#master-password" id="master-password"></a>

Bitwarden 的用户数据保护从用户创建账户和主密码的那一刻开始。主密码是用户访问其存储了敏感数据的密码库的令牌。用户应使用强密码创建账户，Bitwarden 提供了一个密码强度计，以帮助用户创建强大的主密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6Nopwp0Wbr6FmfQBfzhAGb/e80b52613f70186f491e629cc7906c91/Screenshot_2024-04-01_at_9.41.44_AM.png?_a=DAJAUVWIZAAB" %}
密码强度计
{% endembed %}

如当用户试图使用弱密码注册时，Bitwarden 会发出警告，并且还提供了通过与 [Have I Been Pwned (HIBP)](https://haveibeenpwned.com/FAQs) 的集成来检查主密码是否已被泄露的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2fc9uAmERxfK7QEkFzeeO0/0fbe2a9b1d207950a2d30358f904c405/Screenshot_2024-04-01_at_9.50.46_AM.png?_a=DAJAUVWIZAAB" %}
主密码弱或暴露
{% endembed %}

**用户永远不要忘记他们的主密码，这一点非常重要**。主密码：

* 使用后会从内存中被清除。
* 不会通过互联网传输到 Bitwarden 服务器。
* Bitwarden 的任何人都无法看到、读取或进行逆向。

基于此，以及由于您的数据在离开本地设备之前已完全加密和/或哈希，忘记主密码将导致用户无法访问其账户，除非他们启用了紧急访问或账户恢复功能，这两者将在本文后面进行详细介绍。

{% hint style="success" %}
用户可以通过 Bitwarden 网页 App 更改他们的主密码。[了解如何操作](../your-vault/your-master-password.md#change-your-master-password)。
{% endhint %}

#### 替代登录方法 <a href="#alternative-log-in-methods" id="alternative-log-in-methods"></a>

Bitwarden 客户端提供以下替代身份验证方法。其中一些方法也可用于登录时解密：

* **设备登录**：从 Bitwarden 客户端发起身份验证请求，并通过在您已登录的设备上批准该请求来完成身份验证。[了解它是如何工作的](../your-vault/log-in-with-device.md)。
* **通行密钥登录**：使用通行密钥登录 Bitwarden 客户端，如果该通行密钥支持 PRF，则使用它来解密您的密码库数据。[了解它是如何工作的](../my-account/log-in-and-unlock/log-in-with-passkeys.md)。
* **受信任设备 SSO** ：受信任设备 SSO 允许用户使用 SSO 进行身份验证并使用设备存储的加密密钥解密其密码库，从而无需输入主密码。[了解它是如何工作的](../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md)。

#### 两步登录 <a href="#two-step-login" id="two-step-login"></a>

两步登录（也称为「二因素认证」或「2FA」）是一种用于保护在线账户的额外的安全层，即使有人掌握了主密码，也能确保账户安全。当启用两步登录时，用户在登录 Bitwarden 时需要完成一个额外的步骤，比如使用 [FIDO2 安全密钥](../two-step-login/setup-guides/two-step-login-via-fido2-webauthn.md)或[验证器 App](../two-step-login/setup-guides/two-step-login-via-authenticator.md) 来确认登录尝试。作为最佳实践，**Bitwarden 推荐所有用户启用并使用两步登录**。

Bitwarden 会提供给用户一个恢复代码，用于在丢失了辅助设备（例如 YubiKey）时关闭两步登录功能。**用户应该在启用此功能后立即获取并保存此恢复代码**，因为 Bitwarden 员工和系统无法代表用户禁用两步登录。

了解更多关于可用的[两步登录方式](../two-step-login/two-step-login-methods.md)、[使用多种方式](../two-step-login/two-step-login-methods.md#using-multiple-methods)以及在[丢失辅助设备](../two-step-login/lost-secondary-device.md)时该怎么做的信息。

#### 紧急访问 <a href="#emergency-access" id="emergency-access"></a>

高级用户，包括付费组织（家庭、团队或企业）的成员，可以指定[可信的紧急联系人](emergency-access.md)，以便在紧急情况下请求访问他们的密码库。可信的紧急联系人可以被分配为仅查看或接管账户的权限。

紧急访问使用非对称加密，使用户能够在零知识环境中授权可信的紧急联系人访问密码库数据。

{% hint style="info" %}
以下信息涉及到加密密钥名称和过程，其包含在[哈希、密钥派生和加密](bitwarden-security-whitepaper.md#hashing-key-derivation-and-encryption)部分中。请考虑先阅读那部分。
{% endhint %}

1. 一个 Bitwarden 用户（授予人）邀请另一个 Bitwarden 用户成为其可信紧急联系人（受让人）。邀请（有效期仅 5 天）指定了用户访问级别，并包含对受让人的 **RSA 公共密钥**的请求。
2. 受让人将通过电子邮件收到邀请通知，并接受邀请成为可信紧急联系人。接受邀请后，受让人的 **RSA 公共密钥**将与邀请一起存储。
3. 授予人将通过电子邮件收到接受通知，并确认受让人成为其可信紧急联系人。确认后，授予人的**用户对称密钥**将使用受让人的 **RSA 公共密钥**进行加密，并在加密后存储。受让人将收到确认通知。
4. 发生紧急情况时，受让人可以提交紧急访问请求以要求进入授予人的密码库。
5. 授予人将通过电子邮件收到请求通知。授予人可以随时手动批准请求，否则请求将受到授予人指定的等待时间的约束。当请求被批准或等待时间结束后，经**公钥加密的主密钥**将交付给受让人，并使用受让人的 **RSA 私钥**进行解密。
6. 根据指定的用户访问级别，受让人可以：
   * 获得对授予人密码库中的项目的查看/读取权限。
   * 提示为授予人的密码库创建新的主密码。

#### 账户恢复 <a href="#account-recovery" id="account-recovery"></a>

[账户恢复](../organizations/admin-password-reset.md)功能允许企业组织的指定管理员在员工忘记主密码的情况下恢复成员账户并恢复访问权限。企业也可能希望当员工离职时使用账户恢复功能来重新获得成员账户的所有权。

{% hint style="info" %}
以下信息涉及到加密密钥名称和过程，其包含在[哈希、密钥派生和加密](bitwarden-security-whitepaper.md#hashing-key-derivation-and-encryption)部分中。请考虑先阅读那部分。
{% endhint %}

当组织成员注册账户恢复时，该用户的账户加密密钥（即**用户对称密钥**）会使用组织的 RSA 公钥进行加密。加密后的结果存储为**账户恢复密钥**。

在进行恢复操作时：

1. 使用**组织对称密钥**解密组织的 **RSA 私钥**。
2. 使用解密后的 **RSA 私钥**解密用户的**账户恢复密钥**，从而得到**用户对称密钥**（在产品中称为「账户加密密钥」）。
3. 使用新的**主密钥**对**用户对称密钥**进行加密，并从新的主密码中生成新的**主密码哈希**。替换服务器端原有的**主密钥加密的用户对称密钥**和**主密码哈希**。
4. 使用组织的 **RSA 公钥**重新加密用**户对称密钥**，将先前的**账户恢复密钥**替换为新的密钥。

## 哈希、密钥派生和加密 <a href="#hashing-key-derivation-and-encryption" id="hashing-key-derivation-and-encryption"></a>

这部分将介绍当用户创建 Bitwarden 账户并随后登录以访问其数据时所实施的加密过程：

### 账户创建 <a href="#account-creation" id="account-creation"></a>

创建账户时，Bitwarden 使用基于密码的密钥派生函数 2 (PBKDF2)，经过 600,000 次迭代，使用具有盐化的用户电子邮件地址来扩展用户主密码。

{% hint style="info" %}
虽然用户账户在初始时使用 PBKDF2，但用户可以选择在账户创建后将其密钥派生函数更改为 [Argon2id](encryption.md#pbkdf2)。了解如何[更改 KDF 算法](kdf-algorithms.md#changing-kdf-algorithm)。
{% endhint %}

盐化值的结果是 256 位**主密钥**。然后，使用基于 HMAC 的提取和扩展密钥派生函数 (HKDF)，将**主密钥**的长度再次扩展为 512 位，从而产生**扩展主密钥**。**主密钥**和**扩展主密钥**永远不会存储到 Bitwarden 服务器或传输到 Bitwarden 服务器。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6nm36M2VAPwxdwlD8HoR2N/0b39079292cb7c80ac5147ffa5ab36eb/whitepaper-1.png?_a=DAJAUVWIZAAB" %}
基于密码的密钥派生
{% endembed %}

接下来，使用加密安全伪随机数生成器 (CSPRNG) 创建 512 位**生成的对称密钥**和**初始化向量**。使用**扩展主密钥**和**初始化向量**，用 AES-256 位加密对**生成的对称密钥**进行加密。得到的密钥称为**受保护的对称密钥**，其是与用户相关联的主密钥，**受保护的对称密钥**在账户创建时被发送到 Bitwarden 服务器，并在同步时发送回 Bitwarden 客户端应用程序。

当用户注册账户时，也会创建一个非对称密钥对。[当用户创建组织时](bitwarden-security-whitepaper.md#when-you-create-an-organization-1)，以及在可用于在用户之间共享数据（比如[紧急访问](emergency-access.md)）等过程中，将使用这个**已生成的 RSA 密钥对**。

最后，使用具有**主密钥**有效载荷和主密码盐化的 PBKDF-SHA256 生成**主密码哈希值**。**主密码哈希值**会在账户创建和登录时被发送到 Bitwarden 服务器，用于验证用户账户。到达服务器后，将使用随机盐化的 PBKDF2-SHA256 和 600,000 次迭代再次对**主密码哈希值**进行哈希：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1rLMJoZFka4Per5lIyuMv9/33bc3f62358591bfe4cb86d3c3375535/whitepaper-acctcreate.png?_a=DAJAUVWIZAAB" %}
Bitwarden 密码散列、密钥派生和加密
{% endembed %}

### 身份验证和解密 <a href="#authentication-and-decryption" id="authentication-and-decryption"></a>

用户需要输入电子邮箱地址，通常还需要输入主密码才能[登录](https://vault.bitwarden.com/#/) Bitwarden 账户。

接下来，Bitwarden 使用具有默认为 600,000 次迭代的基于密码的密钥衍生函数 2 (PBKDF2) 来扩展具有盐化的用户电子邮箱地址的主密码。所得的盐化值就是 256 位的**主密钥**。使用 PBKDF-SHA256 生成的**主密码哈希值**以及**主密钥**的有效载荷和主密码盐化，通过将哈希值与服务器端存储的哈希值进行比较，将其发送到服务器进行身份验证。

{% hint style="info" %}
虽然用户账户在初始时使用 PBKDF2，但用户可以选择在账户创建后将其密钥派生函数更改为 [Argon2id](encryption.md#pbkdf2)。了解如何[更改 KDF 算法](kdf-algorithms.md#changing-kdf-algorithm)。
{% endhint %}

同时，使用基于 HMAC 的提取和扩展密钥派生函数 (HKDF)，将**主密钥**的长度扩展为 512 位，从而产生**扩展主密钥**。**受保护的对称密钥**存储在服务器端并由客户端检索，使用此**扩展主密钥**进行解密。客户端使用生成的**对称密钥**来解密密码库数据。此解密完全在 Bitwarden 客户端上完成。**主密码**和**扩展主密钥**永远不会存储到 Bitwarden 服务器或传输到 Bitwarden 服务器。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/lrLsAOcvBsN1vaYAaZQKt/a73a6f46d55cf705423aa7a6a12b7f8a/whitepaper-login.png?_a=DAJAUVWIZAAB" %}
用户登录概述
{% endembed %}

Bitwarden 不会将主密码本身存储在本地或 Bitwarden 客户端内存中。您的账户加密密钥（**用户对称密钥**）会保存在内存中，以用于密码库解密。

当 Bitwarden 客户端被锁定时，您的加密密钥和密码库数据将从内存中清除。在锁屏一定时间内不活动后，我们会重新加载应用程序进程，以确保任何剩余的管理内存地址也被清除。我们尽最大努力确保任何用于应用程序运作的数据只在您需要的时候保留在内存中，并且每当应用程序被锁定时，内存都会被清理。我们认为 Bitwarden 应用程序在锁定状态下是完全安全的。

### 轮换账户加密密钥 <a href="#rotating-the-account-encryption-key" id="rotating-the-account-encryption-key"></a>

在进行密码更改操作期间，您还可以选择轮换（即更改）其**用户对称密钥**（在产品中称为「账户加密密钥」）。如果用户认为以前的主密码已被盗用，或者他们存储在 Bitwarden 密码库的数据已从其中一台设备上被窃取，则轮换此密钥是一个好主意。

{% hint style="danger" %}
轮换账户加密密钥是一项敏感操作，因此在更改主密码时这不是默认选项。密钥轮换会为您的账户生成一个新的随机加密密钥，并使用此新密钥**重新加密所有密码库数据**。请参阅[本文](account-encryption-key.md)了解更多详情。
{% endhint %}

### 变体 <a href="#variations" id="variations"></a>

这部分将介绍当用户使用设备登录、通行密钥登录或使用受信任设备 SSO 时加密过程的变体。

#### 设备登录 <a href="#log-in-with-device" id="log-in-with-device"></a>

当发起设备登录时：

1. 发起客户端向 Bitwarden 服务器发送请求，其中包括账户电子邮件地址、唯一的**身份验证请求公钥**ª 和访问代码。
2. 已注册设备，即已登录并在 Bitwarden 服务器中存储了[唯一设备 GUID](administrative-data.md) 的移动或桌面 App，将收到请求。
3. 当请求获得批准时，批准客户端使用请求中包含的**身份验证请求公钥**对账户的**主密钥**和**主密码哈希**进行加密。
4. 然后，批准客户端将**加密的主密钥**和**加密的主密码哈希**发送到 Bitwarden 服务器，并将请求标记为已完成。
5. 发起客户端向 Bitwarden 服务器请求**加密的主密钥**和**加密的主密码哈希**。
6. 然后，发起客户端使用**身份验证请求私钥**在**本地**解密**主密钥**和**主密码哈希**。
7. 然后，发起客户端使用访问代码和已完成的身份验证请求，通过 Bitwarden Identity 服务对用户进行身份验证。

ª -**身份验证请求公钥和私钥**是为每个无密码登录请求唯一生成的，并且仅在请求期间存在。如果请求未获批准或拒绝，则请求将过期并每 15 分钟从 Bitwarden 服务器中清除一次。

#### 通行密钥登录 <a href="#log-in-with-passkeys" id="log-in-with-passkeys"></a>

下面将介绍当用户的通行密钥被设置为加密时使用通行密钥登录的机制。用户可以选择不使用通行密钥进行加密。

当一个已注册的通行密钥用于登录 Bitwarden 时：

1. 身份验证器通过 WebAuthn API 生成**通行密钥公钥和私钥对**。根据定义，该密钥对构成了您的通行密钥。鉴权选项包括：使用的加密算法，由 Bitwarden 提供给验证者。
2. 身份验证器通过 WebAuthn API 的 PRF 扩展生成 **PRF 对称密钥**。该密钥源自您的通行密钥特有的**内部机密**和 Bitwarden 提供的**盐化**。
3. Bitwarden 客户端生成 **PRF 公钥和私钥对**。PRF 公钥对您的**用户对称密钥**（在产品中称为“账户加密密钥”）进行加密，您的客户端可以通过登录和解锁来访问该密钥，并将生成的 **PRF 加密的用户对称密钥**发送到服务器。
4. 使用 **PRF 对称密钥**（请参阅步骤 2）加密 **PRF 私钥**，并将生成的 **PRF 加密的私钥**发送到服务器。
5. 您的客户端将数据发送到 Bitwarden 服务器，为您的账户创建新的通行密钥凭据记录。如果您的通行密钥已注册并支持密码库加密和解密，则此记录包括：
   * 通行密钥名称
   * 通行密钥公钥
   * PRF 公钥
   * PRF 加密的用户对称密钥
   * PRF 加密的私钥

完成身份验证所需的**通行密钥公私钥**只会以加密格式保留在客户端。

当使用通行密钥登录，特别是解密您的密码库数据时：

1. 使用 WebAuthn API 公钥加密技术，您的身份验证请求将得到断言和确认。
2. 您的 **PRF 加密的用户对称密钥**（在产品中称为「账户加密密钥」）和 **PRF 加密的私钥**将从服务器发送到您的客户端。
3. 使用 Bitwarden 提供的相同**盐化**和您的通行密钥特有的**内部机密**，在本地重新创建 **PRF 对称密钥**。
4. **PRF 对称密钥**用于解密您的**PRF 加密私钥**，从而生成您的 **PRF 私钥**。
5. **PRF 私钥**用于解密您的 **PRF 加密的用户对称密钥**，从而生成您的**用户对称密钥**。这用于解密您的密码库数据。

#### 受信任设备 SSO <a href="#sso-with-trusted-devices" id="sso-with-trusted-devices"></a>

下面章节介绍不同受信任设备程序中的加密过程和密钥交换：

{% tabs %}
{% tab title="入职" %}
当新用户加入组织时，会使用**组织公钥**对其账户加密密钥进行加密，从而创建**账户恢复密钥**（[了解更多](https://help.ppgg.in/admin-console/user-management/account-recovery)）。账户恢复是启用受信任设备 SSO 的先决条件。

然后询问用户是否想要记住或信任此设备。当他们选择这样做时：

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2o9o8L0JZMvWZYJvfKGMzj/b7cab59682862c8e782331ed6a2ef9d9/td-create.png?_a=DAJAUVWIZAAB" alt=""><figcaption><p>创建受信任设备</p></figcaption></figure>

1. 客户端生成一个新的**设备密钥**。该密钥永远不会离开客户端。
2. 客户端生成一个新的 RSA 密钥对，称为**设备私钥**和**设备公钥**。
3. 用户的账户加密密钥使用未加密的**设备公钥**进行加密，并将结果值作为**公钥加密的用户密钥**发送到服务器。
4. **设备公钥**使用用户的账户加密密钥进行加密，并将结果值作为**用户密钥加密的公钥**发送到服务器。
5. **设备私钥**使用第一个**设备密钥**进行加密，并将所得值作为**设备密钥加密的私钥**发送到服务器。

最重要的是，在启动发起&#x65F6;**，公钥加密的用户密钥**和**设备密钥加密的私钥**将从服务器发送到客户端。

如果用户需要轮换其账户加密密钥，则将使用**用户密钥加密的公钥**。
{% endtab %}

{% tab title="登录" %}
当用户在已受信任的设备上使用 SSO 进行身份验证时：

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/61SSa6ITlRaICIUoCzEiVp/746cf3ba3005b4118d20319e894c47c7/td-use.png?_a=DAJAUVWIZAAB" alt=""><figcaption><p>使用受信任设备</p></figcaption></figure>

1. 用户的**公钥加密的用户密钥**（用于解密密码库数据的账户加密密钥的加密版本）从服务器发送到客户端。
2. 用户的**设备密钥加密的私钥**（用于解密**公钥加密的用户密钥**的未加密版本）从服务器发送到客户端。
3. 客户端使用**设备密钥**解密**设备密钥加密的私钥**，该**设备密钥**永远不会离开客户端。
4. 现在未加密的**设备私钥**用于解密**公钥加密的用户密钥**，从而产生用户的账户加密密钥。
5. 用户的账户加密密钥解密密码库数据。
{% endtab %}

{% tab title="批准" %}
当用户使用 SSO 进行身份验证，并选择使用未受信任的设备（即**设备对称密钥**不存在于该设备上）解密其密码库时，他们需要选择一种方法来批准该设备，并选择信任该设备，以便将来无需进一步批准即可使用。接下来会发生什么取决于所选的选项：

* **从其他设备批准：**
  1. 触发[此处](https://help.ppgg.in/my-account/log-in-and-unlock/log-in-with-device#how-it-works)记录的流程后，客户端就获得并解密了账户加密密钥。
  2. 用户现在可以使用解密后的账户加密密钥解密其密码库数据。如果用户选择信任该设备，则会按照**入职**选项卡中的说明与客户端建立信任。
* **请求管理员批准：**
  1. 发起请求的客户端向 Bitwarden 数据库中的验证请求表 POST 一个请求，其中包括账户电子邮件地址、唯一的**身份验证请求公钥**ª 和访问代码。
  2. 管理员可在设备批准页面上[批准或拒绝此请求](https://help.ppgg.in/admin-console/login-with-sso/trusted-devices/approve-a-trusted-device)。
  3. 请求获得管理员批准后，被批准客户端会使用请求中包含的**身份验证请求公钥**对用户的账户加密密钥进行加密。
  4. 然后，被批准客户端将加密后的账户加密密钥 PUT 到验证请求记录，并标记为请求已完成。
  5. 发起请求的客户端 GET 到加密后的账户加密密钥，然后使用**身份验证请求私钥**ª 对它进行**本地**解密。
  6. 使用解密后的账户加密密钥，与客户端建立信任关系，详见**入职**选项卡。

ª - **身份验证请求公钥**和**私钥**是为每一个无密码登录请求生成的唯一密钥，其存在时间与请求的存在时间相同。未被批准的请求，请求将在 1 周后过期。

* **使用主密码批准：**
  1. 按照安全白皮书中「[身份验证和解密](https://help.ppgg.in/security/bitwarden-security-whitepaper#authentication-and-decryption)」部分的说明，获取并解密用户的账户加密密钥。
  2. 使用解密后的账户加密密钥，按照**入职**选项卡中的说明与客户建立信任。
{% endtab %}

{% tab title="密钥轮换" %}
{% hint style="info" %}
只有拥有主密码的用户才能轮换其[账户加密密钥](https://help.ppgg.in/security/account-encryption-key)。[了解更多](https://help.ppgg.in/admin-console/login-with-sso/trusted-devices/about-trusted-devices#impact-on-master-passwords)。
{% endhint %}

当用户轮换其[账户加密密钥](account-encryption-key.md)时，正常轮换过程如下：

1. **用户密钥-已加密的公钥**从服务器发送到客户端，然后使用旧的账户加密密钥（又称**用户密钥**）对其解密，得到**设备公钥**。
2. 使用未加密的设备公钥对用户的新的账户加密密钥进行加密，然后将结果值作为新的**公钥-已加密的用户密钥**发送到服务器。
3. 使用用户的新的账户加密密钥对设备公钥进行加密，然后将结果值作为新的**用户密钥-已加密的公钥**发送到服务器。
4. 为此用户持久保存在服务器上的所有其他设备的受信任设备加密密钥都会被清除。这样，服务器上就只保留该单个设备所需的三个密钥（**公钥-已加密的用户密钥**、**用户密钥-已加密的公钥**和在此过程中未被更改的**设备密钥-已加密的私钥**）。

任何现在未受信任的客户端都必须通过**批准**选项卡中说明的方法之一重新建立信任。
{% endtab %}
{% endtabs %}

## 在用户之间共享数据 <a href="#sharing-data-between-users" id="sharing-data-between-users"></a>

协作是使用密码管理器的主要好处之一。要实现共享，首先需要创建一个[组织](../organizations/organizations.md)。Bitwarden 组织是一个实体，它将希望共享项目的用户联系在一起。一个组织可以是一个家庭、团队、公司或其他任何希望共享数据的团体。

本节将介绍为确保安全、端到端、零知识共享数据加密方法而实施的加密过程，以及为确保数据控制而实施的其他安全措施：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1f8B41wwuVVuaJP8NjI8jy/c059ab0fa4a645eb14973571c7669128/whitepaper-orgcloseup.png?_a=DAJCwlWIZAAB" %}
组织密钥保护与交换
{% endembed %}

### 当您创建组织时 <a href="#when-you-create-an-organization" id="when-you-create-an-organization"></a>

创建组织时，会使用加密安全的伪随机数生成器 (CSPRNG) 生成**组织对称密钥**。该密钥用于加密组织所拥有的密码库数据，因此与组织成员共享数据需要安全地提供**组织对称密钥**的访问权限。不受保护的**组织对称密钥**绝不会存储在 Bitwarden 服务器上。

**组织对称密钥**一经创建，就会使用 RSA-OAEP 和组织创建者的 **RSA 公钥**对其进行加密。

{% hint style="info" %}
每个用户在创建账户时都会生成一个 **RSA 密钥对**，无论其是否为组织成员，因此该密钥在创建组织之前就已经存在。**RSA 私钥**的用途如下所述，它与用户的用**户对称密钥**一起加密存储，因此用户必须完全登录后才能访问它。
{% endhint %}

此操作的结果值称为**受保护的组织对称密钥**，并被发送到 Bitwarden 服务器。

当组织创建者或任何组织成员登录到他们的账户时，客户端应用程序使用已解密的 **RSA 私钥**来解密**受保护的组织对称密钥**，从而产生**组织对称密钥**。使用组织对称密钥，在本地解密组织拥有的密码库数据。

> **\[译者注]**：
>
> * **CSPRNG**：Cryptographically Secure Pseudorandom Number Generator（加密安全的伪随机数生成器）。是一种用于生成高安全性伪随机数的算法或工具。主要用于需要高安全性的场景，如加密密钥生成、数字签名、随机数种子等。
> * **RSA-OAEP**：RSA Optimal Asymmetric Encryption Padding（RSA 最优非对称加密填充）。是一种基于 RSA 加密算法的填充方案，常用于加密敏感数据，如密钥或消息。

### 当用户加入组织时 <a href="#when-users-join-an-organization" id="when-users-join-an-organization"></a>

后续用户加入组织的过程非常相似，但有些差异值得注意。

首先，组织的既定成员（特别是有权限入职其他用户的成员）向组织确认该用户。该既定成员由于已经登录其账户并完成了上一节中描述的组织数据解密过程，因此可以访问已解密的**组织对称密钥**。

因此，当新用户得到确认时，既定成员的客户端将连接到 Bitwarden 服务器，获取新用户的 **RSA 公钥**（该密钥在创建账户时存储在 Bitwarden 服务器上），并用它来加密已解密的**组织对称密钥**。这会产生一个新的**受保护的组织对称密钥**，该密钥将发送到 Bitwarden 服务器并为新成员存储。

{% hint style="info" %}
每个**受保护的组织对称密钥**对于其用户来说都是唯一的，但是当使用特定用户的 **RSA 私钥**解密时，每个受保护的组织对称密钥都将解密为相同的要求的**组织对称密钥**。
{% endhint %}

新用户登录其账户时，客户端应用程序使用已解密的 **RSA 私钥**来解密**受保护的组织对称密钥**，从而产生**组织对称密钥**。使用组织对称密钥，在本地解密组织拥有的密码库数据。

阅读更多：[什么是组织？](../organizations/organizations.md)

### 其他安全措施 <a href="#additional-security-measures" id="additional-security-measures"></a>

#### 访问控制、权限和角色 <a href="#access-controls-permissions-and-roles" id="access-controls-permissions-and-roles"></a>

Bitwarden 组织使用集合、工程和群组对密码库数据和用户进行逻辑分组：

* **集合和工程**：将密码库数据以逻辑方式组织成离散的单元，以确保成员能访问所有资源，而且只能访问他们需要的资源。
* **群组**：以逻辑方式将成员组织成离散单元，以确保每个人都能访问所有资源，而且只能访问他们需要的资源。
* **成员角色**：为成员分配角色，让他们在组织范围内访问适当级别的工具。
* **权限**：指定成员获准访问的密码库数据的操作权限。

#### 事件日志 <a href="#event-logs" id="event-logs"></a>

事件日志包含带有时间戳的详细信息，说明组织内发生了哪些操作或变更。这些日志有助于研究凭据或配置的更改，对审计跟踪调查和故障排除非常有用。拥有 Password Manager 和 Secrets Manager的团队和企业组织均可使用事件日志。了解更多有关[事件日志](../admin-console/reporting/event-logs.md)的信息。

团队和企业组织也可以使用 [Bitwarden 公共 API ](../organizations/bitwarden-public-api.md)为其事件日志收集更多数据。

#### SIEM 集成 <a href="#siem-integrations" id="siem-integrations"></a>

Bitwarden 提供多种安全信息和事件管理 (SIEM) 集成：

* [Splunk](../admin-console/reporting/splunk-siem.md)
* [Panther](../admin-console/reporting/panther-siem.md)
* [Elastic](../admin-console/reporting/elastic-siem.md)

对于其他 SIEM 系统，可结合使用 API 和 CLI 来收集数据。[此处](../admin-console/reporting/event-logs.md#siem-and-external-systems-integrations)概述了这一过程。

## 数据保护 <a href="#data-protection" id="data-protection"></a>

本节将介绍为确保数据安全而采取的措施：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5hrNLuFuk9laua0zD0zSL/2f9a008c97f9bf98b969e96a85a0a32a/multifactor_encryption__2_.png?_a=DAJCwlWIZAAB" %}
多因素加密
{% endembed %}

### 密码库数据是如何加密的 <a href="#how-vault-data-is-encrypted" id="how-vault-data-is-encrypted"></a>

所有密码库数据（登录、支付卡、身份、笔记和机密）都受到端到端加密保护。您选择存储在 Bitwarden 中的数据首先会被存储为一个称为 Cipher 的对象。在创建、编辑或导入密码库项目时，会使用唯一、随机、64 字节的 **Cipher 密钥**对 Cipher 进行本地加密。每个 **Cipher 密钥**在发送到 Bitwarden 服务器之前，会根据项目是个人所有还是组织所有，使用**用户对称密钥**或**组织对称密钥**进行加密。这些加密操作完全在 Bitwarden 客户端应用程序上执行。

> **\[译者注]**：**Cipher**：Cipher 是一个术语，指的是**加密数据对象**。在 Bitwarden 中它表示包含加密后的敏感信息（如密码、笔记或信用卡）及其元数据（如名称、文件夹、访问权限等）的结构化对象。

当用户登录 Bitwarden 时，客户端通过使用**拉伸后的主密钥**对其**受保护的对称密钥**进行解密，从而获得其**用户对称密钥**。如果用户是某个组织的成员，则通过其 **RSA 私钥**访问**组织对称密钥**。有了这些密钥中的一个，**Cipher 密钥**就可以在本地解密，所得值可用于解密个人或组织的密码库数据。

当用户更换其账户加密密钥（这里称为**用户对称密钥**）时，每个现有的 **Cipher 密钥**都会用新的**用户对称密钥**重新加密。

{% hint style="info" %}
对于附件，**Cipher 密钥**用于加密附件的元数据，特别是文件名和大小。**Cipher 密钥**还用于加密**附件密钥**，而**附件密钥**又用于加密附件数据本身。
{% endhint %}

### 密码库健康报告 <a href="#vault-health-reports" id="vault-health-reports"></a>

密码库健康状况报告可用于评估 Bitwarden Password Manager中存储的数据的安全性。报告，例如重复使用密码和弱密码报告，可在 Bitwarden 客户端应用程序上本地运行。这样就可以在 Bitwarden 无法访问未加密版本数据的情况下识别出违规项目。进一步了解可用的[密码库健康报告](../your-vault/vault-health-reports.md)。

### 中转过程中的数据保护 <a href="#data-protection-in-transit" id="data-protection-in-transit"></a>

Bitwarden 使用 TLS/SSL 来确保 Bitwarden 客户端和用户设备与 Bitwarden 云之间的通信安全。Bitwarden 的 TLS 实现使用 X.509 证书进行服务器身份验证和密钥交换，并使用强大的 Cipher 套件进行批量加密。Bitwarden 服务器可配置为拒绝弱 Cipher 和协议。

Bitwarden 还实施了 HTTP 安全标头，如 HTTP 严格传输安全 (HSTS)，这将强制所有连接使用 TLS。 HSTS 的这一额外保护层可降低降级攻击和错误配置的风险。

### 空闲时的数据保护 <a href="#data-protection-at-rest" id="data-protection-at-rest"></a>

在将您的数据发送到云服务器进行同步之前，Bitwarden 总是在您的本地设备上对数据进行加密和/或散列。Bitwarden 服务器仅用于存储和同步加密后的密码库数据，无法从 Bitwarden 云服务器中获取您的未加密数据。具体来说，Bitwarden 使用 AES 256 位加密以及 [PBKDF-SHA256](encryption.md#pbkdf2) 或 [Argon2id](encryption.md#argon2id) 来保护您的数据安全。存储在密码库中的通行密钥使用 ES256 算法生成。

AES 是密码学的一个标准，被美国政府和世界各地的其他政府机构用于保护绝密数据。只要实施得当，加上强大的加密密钥（即您的主密码），AES 被认为是不可破解的。

[PBKDF-SHA256](encryption.md#pbkdf2) 或 [Argon2id](encryption.md#argon2id) 用于从您的主密码派生加密密钥。然后对该密钥进行盐化和哈希处理，以便与 Bitwarden 服务器进行验证。PBKDF2 在客户端默认使用的迭代次数是 600,001 次（此客户端迭代次数可以从您的账户设置中配置）。

{% hint style="info" %}
虽然用户账户是使用 PBKDF2 初始化的，但用户可以在账户创建后选择将密钥派生函数更改为 [Argon2id](encryption.md#argon2id)。了解[如何更改 KDF 算法](kdf-algorithms.md#changing-kdf-algorithm)。
{% endhint %}

Bitwarden 云数据库存储您的已加密的密码库，并托管在安全的 Microsoft Azure 云基础设施中。它配置了 Azure 提供的一种名为透明数据加密 (TDE) 的静态加密技术。TDE 在整个 Bitwarden 云数据库、相关备份数据和事务日志文件不使用时对其进行实时加密和解密。Azure 处理 TDE 的加密密钥，只有经过授权的 Bitwarden 服务器组件才能访问这些密钥。[此处](https://learn.microsoft.com/zh-cn/azure/azure-sql/database/transparent-data-encryption-tde-overview?view=azuresql\&tabs=azure-portal)了解更多有关 Azure 透明数据加密的信息。

此外，Bitwarden 服务器应用程序还会对与用户账户相关的敏感数据库列进行加密。主密码哈希值和受保护的用户密钥在进出 Bitwarden 云数据库时会被即时加密。这些列级加密操作是使用 Bitwarden 在严格控制的密钥管理服务 (KMS) 中管理的密钥执行的。

了解更多信息： [端到端加密如何为零知识铺平道路](https://bitwarden.com/blog/end-to-end-encryption-and-zero-knowledge/)以及[使用何种加密方式](encryption.md)。

### 数据类型和数据保留 <a href="#data-types-and-data-retention" id="data-types-and-data-retention"></a>

Bitwarden 处理两种用户数据以提供 Bitwarden 服务：(i) 密码库数据和 (II) 管理数据。

(i) 密码库数据

密码库数据包括存储在 Bitwarden 服务账户内的所有信息，其中可能包括个人信息。如果我们为您托管 Bitwarden 服务，我们将托管密码库数据。密码库数据在您的控制下使用安全加密密钥进行加密。Bitwarden 无法访问密码库数据。

保管库数据的保留：您可以随时添加、修改和删除密码库数据。

(ii) 管理数据

Bitwarden 会在您创建账户、使用 Bitwarden 服务和支持以及支付 Bitwarden 服务费用时获取您的个人信息，如 Bitwarden 服务用户的姓名、电子邮箱地址、电话和其他联系信息，以及您 Bitwarden 服务账户中的项目数量（以下称为「管理数据」）。Bitwarden 使用管理数据为您提供 Bitwarden 服务。只要您还是 Bitwarden 的客户，我们就会在法律要求的期限内保留管理数据。如果您终止与 Bitwarden 的关系，我们将根据我们的数据保留政策删除您的个人信息。

当您使用本网站或与我们联系（如通过电子邮件）时，您将提供，而 Bitwarden 也将收集某些个人信息，比如：

* 名称
* 企业名称和地址
* 企业电话号码
* 电子邮箱地址
* IP 地址和其他在线标识符
* 您同意与我们分享的任何客户评价。
* 您在网站互动区提供的信息，如可填写表格或文本框、培训、网络研讨会或活动注册。
* 您使用的设备信息，包括硬件型号、操作系统和版本、唯一设备标识符、网络信息、IP地址和/或与网站互动时的 Bitwarden 服务信息。
* 如果您与 Bitwarden 社区或培训互动，或注册参加考试或活动，我们可能会收集您的履历信息和您分享的内容。
* 通过 cookies、像素标签、日志或其他类似技术收集的信息。

更多信息请参阅 [Bitwarden 隐私政策](https://bitwarden.com/privacy/)。

## 云平台和网页应用程序安全 <a href="#cloud-platform-and-web-application-security" id="cloud-platform-and-web-application-security"></a>

### 架构概述 <a href="#architecture-overview" id="architecture-overview"></a>

Bitwarden 使用 Microsoft 团队管理的服务（包括 Azure Kubernetes 服务 (AKS)）在 Microsoft Azure 云中安全地处理和存储所有数据。

Azure Kubernetes 服务是 Microsoft 提供的 Kubernetes 托管服务，可降低部署和管理 Kubernetes 集群的复杂性。Microsoft 全面管理此控制平台。控制平台包含用于操作和维护 Bitwarden Kubernetes 集群的所有组件和服务。Microsoft 和 AKS 团队部署、运营并负责 AKS 服务的可用性和功能。Bitwarden 团队负责管理：

* AKS 服务的访问管理
* 打补丁和更新，以应用 Node OS 安全补丁、Node 映像版本升级和 Kubernetes 版本（集群升级）
* AKS 中的 docker 映像和运行容器的容器安全性
* 节点的网络安全

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6PDqnG1zfXQLQ54rm0auc0/8b41d77f1451ae0aed8c259fa85ed5a2/Security_White_Paper_Diagrams_August_2023_-GO_BR-.png?_a=DAJCwlWIZAAB" %}
Bitwarden 架构概述
{% endembed %}

### 安全更新和补丁 <a href="#security-updates-and-patching" id="security-updates-and-patching"></a>

#### Azure Kubernetes Services (AKS)

Microsoft 为其 AKS 服务提供补丁、新的节点映像和新的 Kubernetes 版本。Bitwarden 团队负责管理和监控 AKS 环境，并遵循 Microsoft 的升级建议和漏洞报告，以确保应用节点操作系统安全补丁、节点映像版本升级和 Kubernetes 版本（集群升级）。此外，Bitwarden 团队还应用更新和补丁，以维护 AKS 中 docker 映像和运行容器的安全性。

### 生产系统控制 <a href="#control-of-production-systems" id="control-of-production-systems"></a>

Bitwarden 为所有生产系统维护文档化的运行手册，涵盖部署、更新和故障排除流程。在出现问题时，系统会设置大量警报来通知和升级。

#### 基线配置 <a href="#baseline-configurations" id="baseline-configurations"></a>

Bitwarden 使用 Microsoft 团队管理的服务（包括 Azure Kubernetes 服务 (AKS)）在 Microsoft Azure 云中安全地处理和存储所有数据。

#### Azure Kubernetes Services (AKS)

使用云安全态势管理和漏洞管理服务建立和监控安全基准配置。

#### HTTP 安全标头 <a href="#http-security-headers" id="http-security-headers"></a>

Bitwarden 利用 HTTP 安全标头为 Bitwarden 网页应用程序和通信提供额外的保护。例如，HTTP 严格传输安全 (HSTS) 将强制所有连接使用 TLS，从而降低降级攻击和错误配置的风险。内容安全策略标头可进一步防止跨站脚本 (XSS) 等注入式攻击。此外，Bitwarden 还实现了 X-Frame-Options: SAMEORIGIN 来抵御 clickjacking（点击劫持）。

### 密钥管理程序 <a href="#key-management-procedures" id="key-management-procedures"></a>

Bitwarden 平台本身使用的密钥和其他机密，包括 Bitwarden 云服务提供商账户的凭据，都是根据行业标准惯例生成、安全存储和按需轮换的。Bitwarden 使用内部 Bitwarden 密码库对 Bitwarden 平台使用的敏感密钥或其他机密进行安全存储和备份。通过访问控制、权限和角色对这些密码库的访问权限进行严格管理。

### 日志记录、监控和警报通知 <a href="#logging-monitoring-and-alert-notification" id="logging-monitoring-and-alert-notification"></a>

Bitwarden 为所有生产系统维护文档化的运行手册，涵盖部署、更新和故障排除流程。在出现问题时，系统会设置广泛的警报以进行通知和升级。Bitwarden 云基础设施的手动和自动监控相结合，可提供全面、详细的系统健康状况视图，并可对问题领域主动发出警报。问题会迅速浮出水面，这样 Bitwarden 基础设施团队就能有效应对并缓解问题，将中断时间降到最低。

### 威胁预防和响应 <a href="#threat-prevention-and-response" id="threat-prevention-and-response"></a>

Bitwarden 利用各种服务和工具对我们的网络、资产、数据和服务进行持续的安全监控，这些服务和工具包括但不限于安全信息事件管理 (SIEM)、安全运营中心 (SOC)、漏洞管理、数据丢失防护 (DLP) 以及端点检测和响应 (EDR)。Bitwarden 制定了安全事件响应政策和计划，旨在将网络事件的整体影响降至最低，并将以下内容作为事件响应生命周期的一部分：

* 准备和规划
* 检测和分析
* 遏制
* 消除
* 恢复
* 事后活动

Bitwarden 使用内容分发网络 (CDN) 服务，以便在边缘提供网页应用程序防火墙 (WAF)、更好的 DDoS 保护、分布式可用性和缓存。Bitwarden 还在 CDN 提供商内部使用代理，以提高其服务和网站的网络安全性和性能。

#### 代码评估 <a href="#code-assessments" id="code-assessments"></a>

Bitwarden 是一款开源软件。我们所有的源代码都托管在 GitHub 上，任何人都可以免费审查。Bitwarden 源代码由信誉良好的第三方安全审计公司和独立安全研究人员进行审计。此外，Bitwarden 漏洞披露计划还寻求 HackerOne 黑客社区的帮助，以提高 Bitwarden 的安全性。

### 业务连续性和灾难恢复 <a href="#business-continuity-and-disaster-recovery" id="business-continuity-and-disaster-recovery"></a>

Bitwarden 采用了 Microsoft Azure 的全套灾难恢复和业务连续性实践，这些实践已内置到 Bitwarden 云中。这包括为我们的应用程序和数据库层提供高可用性和备份服务。

### 软件生命周期和变更管理 <a href="#software-lifecycle-and-change-management" id="software-lifecycle-and-change-management"></a>

Bitwarden 对平台、应用程序和生产基础设施的变更进行评估，以最大限度地降低风险，并按照 Bitwarden 的标准操作程序实施变更。

变更请求项目根据路线图进行规划，并提交给工程部门。工程部门将对其能力进行审查和评估，并对每个变更请求项目的工作量进行评估。经过审核和评估后，产品和工程团队将制定具体版本的工作内容。当该版本的开发生命周期开始时，首席技术官会通过沟通渠道和管理会议提供该版本的详细信息。

在高层次上，开发、发布、测试和审批流程包括：

* 使用 GitHub 中的拉取请求进行开发、构建和迭代。
* 使功能达到可测试的程度。
* 工程部在开发和构建过程中对功能和/或产品进行功能测试。
* 作为 Bitwarden 持续集成 (CI) 管道的一部分，单元测试构建和静态应用程序安全测试 (SAST) 已实现自动化。
* 客户成功团队也会进行一些测试。
* 工程管理部门协助审查并帮助流程正规化，包括文档更新。
* 首席技术官提供最终批准/否决批准。

**出席会议**：为确保成功审查、批准实施和关闭变更请求，每个核心运营和 IT 服务人员都应派代表参加会议，审查和讨论变更请求。

紧急部署和热修补程序应优先上报，并在进行变更之前由经理或主管对变更进行审查和批准，随后在下一次预定的变更会议上进行审查、沟通和关闭。这通常是在服务中断、系统瘫痪或紧急预防中断的情况下。

### 审计性和合规性 <a href="#auditability-and-compliance" id="auditability-and-compliance"></a>

Bitwarden 安全和合规计划是基于 ISO-27001 信息安全管理系统 (ISMS)。Bitwarden 员工制定了安全和流程管理政策，并不断更新安全计划，以符合适用的法律、行业和监管要求，为您提供符合我们服务协议条款的服务。

Bitwarden 遵守行业标准的应用程序安全准则，其中包括一个专门的安全工程团队，并定期审查应用程序源代码和IT基础设施，以检测、验证和修复任何安全漏洞。

#### 外部安全审查 <a href="#external-security-reviews" id="external-security-reviews"></a>

每年至少对应用程序和/或平台进行一次第三方安全审查和评估。

#### 认证 <a href="#certifications" id="certifications"></a>

Bitwarden 的认证包括:

* SOC2 Type II（每年更新）
* SOC3（每年更新）
* ISO 27001

根据美国注册会计师协会 (AICPA) 的规定，系统和组织控制 (SOC)、SOC 2 Type II 报告的使用受到限制。如需查询 SOC 2 报告，请[联系我们](https://bitwarden.com/contact/)。

了解更多：[Bitwarden 获得 SOC2 认证](https://bitwarden.com/blog/bitwarden-achieves-soc-2-certification/)

SOC 3 报告提供 SOC 2 报告的摘要，并公开发布。根据美国注册会计师协会 (AICPA) 的规定，SOC 3 是服务机构报告一般使用的信托服务标准的 SOC。Bitwarden [在此](https://cdn.bitwarden.com/misc/Bitwarden%202020%20SOC%203%20Report.pdf)提供 SOC 3 报告的副本，报告摘要表明了我们对安全和隐私标准的承诺。

这些 SOC 认证代表了比特梵德致力于保护客户安全和隐私以及遵守严格标准的一个方面。Bitwarden 还定期对我们的网络安全和代码完整性进行审核。

了解更多：[Bitwarden 2020 安全审计完成](https://bitwarden.com/blog/bitwarden-network-security-assessment-2020/)以及[Bitwarden 完成第三方安全审计](https://bitwarden.com/blog/third-party-security-audit/)

### 员工访问控制 <a href="#employee-access-controls" id="employee-access-controls"></a>

Bitwarden 的员工在数据、系统和信息资产的设计、架构、实施、管理、支持和互动方面都接受过大量的培训，拥有丰富的专业知识。

Bitwarden 遵循既定的入职流程，以确保分配和维护适当级别的访问权限。Bitwarden 为每个角色设定了适当的访问级别。所有请求，包括任何访问权限变更请求，都需要经过经理的审核和批准。Bitwarden 遵循最低权限政策，授予员工完成其职责所需的最低访问级别。Bitwarden 遵循通过 Bitwarden 人力资源部建立的离职流程，在员工离职时取消所有访问权限。

## 威胁模型和攻击面分析概述 <a href="#threat-model-and-attack-surface-analysis-overview" id="threat-model-and-attack-surface-analysis-overview"></a>

Bitwarden 采用基于风险的方法设计安全服务和系统，其中包括威胁模型和攻击面分析，以识别威胁并制定缓解措施。风险和威胁模型分析扩展到 Bitwarden 平台的所有领域，包括核心的 Bitwarden 云服务器应用程序和 Bitwarden 客户端，如移动、桌面、网页应用程序、浏览器和/或命令行界面。

### Bitwarden 客户 <a href="#bitwarden-clients" id="bitwarden-clients"></a>

用户主要通过客户端应用程序与 Bitwarden 进行交互，如移动、桌面、网页应用程序、浏览器和/或命令行界面。这些设备、工作站和网页浏览器的安全性至关重要，因为如果其中一个或多个设备受到攻击，攻击者就有可能安装键盘记录器等恶意软件，从而获取在这些设备上输入的所有信息，包括您的任何密码和机密。作为最终用户和/或设备所有者，您有责任确保您的设备安全，防止未经授权的访问。

### HTTPS TLS 和网页浏览器加密端到端加密 <a href="#https-tls-and-web-browser-crypto-end-to-end-encryption" id="https-tls-and-web-browser-crypto-end-to-end-encryption"></a>

Bitwarden 网页客户端在您的网页浏览器中运行。Bitwarden 网页客户端的真实性和完整性取决于 HTTPS TLS 连接的完整性。有能力篡改网页客户端传输流量的攻击者可能会向用户发送恶意客户端。

网页浏览器攻击是攻击者和网络犯罪分子注入恶意软件或造成破坏的最常用方法之一。网页浏览器的攻击载体可能包括：

* **社会工程学因素**：如网络钓鱼，诱骗和说服受害者采取任何行动，从而损害其用户机密和账户的安全。
* **网页浏览器攻击和浏览器扩展/插件漏洞**：恶意扩展设计用于在键盘上输入用户秘密时捕获用户秘密。
* **通过浏览器对网页应用程序的攻击**：点击劫持、跨站脚本攻击 (XSS)、跨站请求伪造 (CSRF)。

Bitwarden 利用 [HTTP 安全标头](bitwarden-security-whitepaper.md#http-security-headers)为 Bitwarden 网页应用程序和通信提供额外的保护。

## 结语 <a href="#conclusion" id="conclusion"></a>

提供此 Bitwarden 安全与合规计划概述，以供您参考。Bitwarden 的解决方案、软件、基础设施和安全流程都是以多层次、深入防御的方式从头设计的。

Bitwarden 的安全与合规计划基于 ISO27001 信息安全管理体系 (ISMS)。Bitwarden 员工制定了安全和流程管理政策，并不断更新我们的安全计划，以符合适用的法律、行业和监管要求，以便为您提供符合我们[服务协议条款](https://bitwarden.com/terms/)的服务。

如果您有任何疑问，请[联系我们](https://github.com/bitwarden/help/blob/master/_articles/security/www.bitwarden.com/contact)。

### 文档变更日志 <a href="#document-changelog" id="document-changelog"></a>

| 2024 年 03 月 11 日 | 新增了 ISO 27001 认证。         |
| ---------------- | ------------------------- |
| 2024 年 12 月 11 日 | 调整了内存管理方面的语言。             |
| 2024 年 08 月 02 日 | 重构了文档以方便导航，改进信息架构，并使风格更一致 |
| 2024 年 07 月 25 日 | 添加了有关密码库项目加密的密钥信息         |
| 2024 年 03 月 23 日 | 新增了**用户间数据共享**部分的描述和图表    |
| 2024 年 01 月 12 日 | 添加了有关使用通行密钥登录的信息          |

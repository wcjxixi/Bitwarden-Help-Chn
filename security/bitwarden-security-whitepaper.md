# =Bitwarden 安全白皮书

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/bitwarden-security-white-paper/)
{% endhint %}

> **\[译者注]**：
>
> * [ISMS](https://en.wikipedia.org/wiki/Information_security_management)：Information Security Management System（信息安全管理体系）
> * [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2)：Password-Based Key Derivation Function 2（基于密码的密钥派生函数 2）
> * [HKDF](https://en.wikipedia.org/wiki/HKDF)：HMAC-based Extract-and-Expand Key Derivation Function（基于 HMAC 的提取和扩展密钥派生函数）
> * [CSPRNG](https://en.wikipedia.org/wiki/CSPRNG)：Cryptographically Secure Pseudorandom Number Generator（加密安全伪随机数生成器）
> * [HSTS](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security)：HTTP Strict Transport Security（HTTP 严格传输安全）
> * [SIEM](https://en.wikipedia.org/wiki/Security_information_and_event_management)：Security Information and Event Management（安全信息和事件管理）
> * [XSS](https://en.wikipedia.org/wiki/Cross-site_scripting)：Cross-Site Scripting（跨站点脚本）
> * [CSRF](https://en.wikipedia.org/wiki/Cross-site_request_forgery)：Cross-Site Request Forgery（跨站点请求伪造）

{% hint style="success" %}
请阅读下面的全文，或[下载 PDF](https://bitwarden.com/images/resources/security-white-paper-2021.pdf)（英文）。
{% endhint %}

## 概述 <a href="#overview" id="overview"></a>

### 每个人的联系比以往任何时候都更加紧密 <a href="#everyone-is-more-connected-than-ever" id="everyone-is-more-connected-than-ever"></a>

在当今社会，与互联网连接的设备和服务比以往任何时候都更加重要。随着越来越多的公司提供创新的软件即服务产品来改善用户的家庭和工作生活，凭证和机器机密的数量呈指数级增长。对他们安全的威胁也是如此。

### 网络安全威胁很大，但实践很少 <a href="#cybersecurity-threats-are-high-but-practices-are-low" id="cybersecurity-threats-are-high-but-practices-are-low"></a>

用户和客户数据面临的威胁不断增加。几乎每周都会有数据泄露或勒索软件攻击的新闻出现，而这些仅仅是规模大到足以被公布的事件。2023 年，[IBM 报告](https://www.ibm.com/reports/data-breach)称，考虑到调查成本、法律费用、机会成本和客户信任损失，美国数据泄露的平均成本接近 948 万美元。

[Verizon](https://www.verizon.com/business/resources/reports/2023-data-breach-investigations-report-dbir.pdf) 的研究表明，在数据泄露事件中，被泄露的凭证占 86%。这包括使用在其他外泄事件中被猜测、钓鱼或泄露的密码。

面对这些威胁，人们希望企业为员工尽可能多地提供培训和工具，但 [Bitwarden 的研究](https://bitwarden.com/resources/2023-password-decisions-survey-results/)表明，用户并不总是遵循最佳实践，其中 90% 的受访者表示他们重复使用了密码。

安全专家建议用户为每个账户使用不同的随机生成的密码。但如何管理所有这些密码呢？如何在整个组织中保持良好的密码习惯呢？

### Bitwarden 帮助保护个人、企业和基础设施的安全 <a href="#bitwarden-helps-secure-individuals-businesses-and-infrastructure-secrets" id="bitwarden-helps-secure-individuals-businesses-and-infrastructure-secrets"></a>

Bitwarden 提供了一系列安全产品，旨在保护每个人，防止数据泄露，并确保工作效率。

Bitwarden Password Manager 为用户提供了创建、存储和共享密码的工具，同时保持了最高级别的安全性。它是存储所有登录信息、密码和其他敏感信息的最简单和最安全的方法，同时还能方便地在所有设备之间保持同步。

Bitwarden Secrets Manager 使开发人员、DevOps 和 IT 团队能够存储、共享和自动处理机器机密，例如身份验证密钥、数据库密码和 API 密钥。这种端到端加密的机密管理解决方案支持安全地部署基础设施和应用代码，没有暴露关键机器机密的风险。

Bitwarden Passwordless.dev 提供了开发人员所需的 API 和工具，以实施基于 FIDO2 WebAuthn 通行密钥身份验证（用于网站和应用程序的下一代安全凭证验证）。

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

{% hint style="info" %}
~~2021 年中期发布的~~[~~账户恢复~~](../organizations/admin-password-reset.md)~~功能为所有组织引入了一个新的 RSA 公钥/私钥对。私钥在存储之前将使用组织中预先存在的对称密钥进一步加密。在创建新组织时将在客户端生成并加密此密钥，或者对于现有的组织：~~

* ~~导航到**管理** → **人员**界面。~~
* ~~更新**设置** → **我的组织**界面上的任何内容。~~
* ~~从一种组织类型升级到另一种组织类型。~~
{% endhint %}

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
5. 您的客户端将数据发送到 Bitwarden 服务器，为您的账户创建新的通行密钥凭证记录。如果您的通行密钥已注册并支持密码库加密和解密，则此记录包括：
   * 通行密钥名称
   * 通行密钥公钥
   * PRF 公钥
   * PRF 加密的用户对称密钥
   * PRF 加密的私钥

完成身份验证所需的**通行密钥公私钥**只会以加密格式保留在客户端。

当使用通行密钥登录，特别是解密您的密码库数据时：

1. 使用 WebAuthn API 公钥加密技术，您的身份验证请求将得到断言和确认。
2. 您的 **PRF 加密的用户对称密钥**（在产品中称为“账户加密密钥”）和 **PRF 加密的私钥**将从服务器发送到您的客户端。
3. 使用 Bitwarden 提供的相同**盐化**和您的通行密钥特有的**内部机密**，在本地重新创建 **PRF 对称密钥**。
4. **PRF 对称密钥**用于解密您的**PRF 加密私钥**，从而生成您的 **PRF 私钥**。
5. **PRF 私钥**用于解密您的 **PRF 加密的用户对称密钥**，从而生成您的**用户对称密钥**。这用于解密您的密码库数据。

#### 受信任设备 SSO <a href="#sso-with-trusted-devices" id="sso-with-trusted-devices"></a>

下面章节介绍不同受信任设备程序中的加密过程和密钥交换：

{% tabs %}
{% tab title="入职" %}
当新用户加入组织时，会通过使用**组织公钥**加密其账户加密密钥来创建**账户恢复密钥**（了解更多）。账户恢复是受信任设备 SSO 的必要条件。

然后会询问用户是否要记住或信任设备。当用户选择这样做时：

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
当用户在已信任的设备上使用 SSO 进行身份验证时：

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
只有拥有主密码的用户才能轮换其[账户加密密钥](https://help.ppgg.in/security/account-encryption-key)。[了解更多](https://help.ppgg.in/admin-console/login-with-sso/trusted-devices/about-trusted-devices#impact-on-master-passwords)。

当某个用户轮换其账户加密密钥时，正常轮换过程如下：

1. **用户密钥-已加密的公钥**从服务器发送到客户端，然后使用旧的账户加密密钥（又称**用户密钥**）对其解密，得到**设备公钥**。
2. 使用未加密的设备公钥对用户的新的账户加密密钥进行加密，然后将结果值作为新的**公钥-已加密的用户密钥**发送到服务器。
3. 使用用户的新的账户加密密钥对设备公钥进行加密，然后将结果值作为新的**用户密钥-已加密的公钥**发送到服务器。
4. 为此用户持久保存在服务器上的所有其他设备的受信任设备加密密钥都会被清除。这样，服务器上就只保留该单个设备所需的三个密钥（**公钥-已加密的用户密钥**、**用户密钥-已加密的公钥**和在此过程中未被更改的**设备密钥-已加密的私钥**）。

任何现在未受信任的客户端都必须通过**批准**选项卡中说明的方法之一重新建立信任。
{% endtab %}
{% endtabs %}

## 在用户之间共享数据 <a href="#sharing-data-between-users" id="sharing-data-between-users"></a>

### 当创建组织时 <a href="#when-you-create-an-organization" id="when-you-create-an-organization"></a>

### 当用户加入组织时 <a href="#when-users-join-an-organization" id="when-users-join-an-organization"></a>

### 额外的安全措施 <a href="#additional-security-measures" id="additional-security-measures"></a>

#### 访问控制、权限和角色 <a href="#access-controls-permissions-and-roles" id="access-controls-permissions-and-roles"></a>

#### 事件日志 <a href="#event-logs" id="event-logs"></a>

#### SIEM 集成 <a href="#siem-integrations" id="siem-integrations"></a>

## 数据保护 <a href="#data-protection" id="data-protection"></a>

### 密码库数据是如何加密的 <a href="#how-vault-data-is-encrypted" id="how-vault-data-is-encrypted"></a>

### 密码库健康报告 <a href="#vault-health-reports" id="vault-health-reports"></a>

### 中转过程中的数据保护 <a href="#data-protection-in-transit" id="data-protection-in-transit"></a>

### 空闲时的数据保护 <a href="#data-protection-at-rest" id="data-protection-at-rest"></a>

### 数据类型和数据保留 <a href="#data-types-and-data-retention" id="data-types-and-data-retention"></a>

## 云平台和网页应用安全 <a href="#cloud-platform-and-web-application-security" id="cloud-platform-and-web-application-security"></a>

### 架构概述 <a href="#architecture-overview" id="architecture-overview"></a>

### 安全更新和补丁 <a href="#security-updates-and-patching" id="security-updates-and-patching"></a>

#### Azure Kubernetes Services (AKS)

### 生产系统控制 <a href="#control-of-production-systems" id="control-of-production-systems"></a>

#### 基线配置 <a href="#baseline-configurations" id="baseline-configurations"></a>

#### Azure Kubernetes Services (AKS)

#### HTTP 安全标头 <a href="#http-security-headers" id="http-security-headers"></a>

### 密钥管理程序 <a href="#key-management-procedures" id="key-management-procedures"></a>

### 日志记录、监控和警报通知 <a href="#logging-monitoring-and-alert-notification" id="logging-monitoring-and-alert-notification"></a>

### 威胁预防和响应 <a href="#threat-prevention-and-response" id="threat-prevention-and-response"></a>

#### 代码评估 <a href="#code-assessments" id="code-assessments"></a>

### 业务连续性和灾难恢复 <a href="#business-continuity-and-disaster-recovery" id="business-continuity-and-disaster-recovery"></a>

### 软件生命周期和变更管理 <a href="#software-lifecycle-and-change-management" id="software-lifecycle-and-change-management"></a>

### 可审计性和合规性 <a href="#auditability-and-compliance" id="auditability-and-compliance"></a>

#### 外部安全审查 <a href="#external-security-reviews" id="external-security-reviews"></a>

#### 认证 <a href="#certifications" id="certifications"></a>

### 员工访问控制 <a href="#employee-access-controls" id="employee-access-controls"></a>

## 威胁模型和攻击面分析概述 <a href="#threat-model-and-attack-surface-analysis-overview" id="threat-model-and-attack-surface-analysis-overview"></a>

### Bitwarden 客户 <a href="#bitwarden-clients" id="bitwarden-clients"></a>

### HTTPS TLS 和网页浏览器加密端到端加密 <a href="#https-tls-and-web-browser-crypto-end-to-end-encryption" id="https-tls-and-web-browser-crypto-end-to-end-encryption"></a>

## 结语 <a href="#conclusion" id="conclusion"></a>

### 文档变更日志 <a href="#document-changelog" id="document-changelog"></a>





#### 启用两步登录后的额外用户数据保护 <a href="#additional-user-data-protection-when-enabling-two-step-login" id="additional-user-data-protection-when-enabling-two-step-login"></a>

两步登录（也称为双因素验证或 2FA）是您账户的额外安全层，旨在确保您是**唯一**可以访问您的账户的人，即使有人得到了您的主密码。

作为最佳实践，我们建议所有用户在其 Bitwarden 账户中激活并使用两步登录。激活两步登录后，您需要在登录 Bitwarden 时完成第二步（除了您的主密码）。默认情况下，每次都会提示您完成第二步，但是会出现一个「记住我」提示，该提示将保存您的 2FA 状态，因此您下次无需使用 2FA 即可在该特定设备上登录最多长达 30 天。

注意：更改你的主密码或取消会话授权都需要重新验证 2FA，无论你之前是否勾选了「记住我」。

Bitwarden 支持如下方式的两步登录：

**免费计划**

* 使用验证器应用程序（如 [2FAS](https://2fas.com/)、[Ravio](https://raivo-otp.com/) 或 [Aegis](https://getaegis.app/)）
* FIDO2 WebAuthn（任何经 FIDO WebAuthn 认证的钥匙）
* 电子邮件&#x20;

**高级功能 - 包含于家庭、团队和企业计划中**

* Duo Security 的 Duo Push、短信、电话和安全钥匙
* YubiKey（任何 4/5 系列设备或 YubiKey NEO/NFC）

您可以启用多种两步登录方式。如果您启用了多种两步登录方式，则登录时显示的默认方式的优先顺序如下：FIDO U2F > YubiKey > Duo > 验证器应用 > Email。不过，您可以在登录时手动切换并使用任何一种方式。

**非常重要的一点是，千万不要丢失两步登录恢复代码。**&#x42;itwarden 提供的账户保护安全模式不支持用户丢失主密码或两步登录恢复代码。如果您在账户上启用了两步登录，并丢失了两步登录恢复代码，您将无法登录您的 Bitwarden 账户。

{% hint style="info" %}
2021 年中期，Bitwarden 为企业计划推出了[账户恢复](../organizations/admin-password-reset.md)功能。使用此选项，用户和组织可以选择实施一个允许管理员和所有者为用户重置密码的新策略。
{% endhint %}

#### 更改用户密码 <a href="#changing-user-password" id="changing-user-password"></a>

您的主密码只能通过[网页密码库](https://vault.bitwarden.com/#/)更改。有关如何更改用户密码的具体步骤，请参阅[此 Bitwarden 帮助文章](../your-vault/your-master-password.md)。

#### 轮换账户的加密密钥 <a href="#rotating-your-accounts-encryption-key" id="rotating-your-accounts-encryption-key"></a>



#### 中转过程中的数据保护 <a href="#data-protection-in-transit" id="data-protection-in-transit"></a>

在处理您的敏感数据时，Bitwarden 非常重视安全问题。您的数据如果没有在您的本地设备上进行加密，是绝对不会被发送到 Bitwarden 云端的。

此外，Bitwarden 使用 TLS/SSL 来确保 Bitwarden 客户端和用户设备与 Bitwarden 云之间的通信安全。Bitwarden 的 TLS 实施使用 2048 位 X.509 证书进行服务器认证和密钥交换，使用强密码套件进行批量加密。我们的服务器被配置为拒绝弱密码和协议。

Bitwarden 还实现了 HTTP 安全头文件，如 HTTP 严格传输安全 (HSTS)，它将强制所有连接使用 TLS。这种具有 HSTS 的额外保护层降低了降级攻击和错误配置的风险。

#### 空闲时的数据保护 <a href="#data-protection-at-rest" id="data-protection-at-rest"></a>

在将您的数据发送到云服务器进行同步之前，Bitwarden 总是在您的本地设备上对数据进行加密和/或散列。Bitwarden 服务器仅用于存储和同步加密后的密码库数据，无法从 Bitwarden 云服务器中获取您的未加密数据。具体来说，Bitwarden 使用 AES 256 位加密以及 PBKDF-SHA256 来保护您的数据安全。

AES 是密码学的一个标准，被美国政府和世界各地的其他政府机构用于保护绝密数据。只要实施得当，加上强大的加密密钥（您的主密码），AES 被认为是不可破解的。

PBKDF-SHA256 用于从您的主密码派生加密密钥。然后，这个密钥会经过盐化和哈希处理，以便与 Bitwarden 服务器进行验证。PBKDF2 默认使用的迭代次数是在客户端的 600,001 次（此迭代次数可以从你的账户设置中配置），然后当存储在我们的服务器上时，会有额外的 100,000 次迭代（默认情况下总共为  700,001 次）。

{% hint style="info" %}
在 2023.2.0 版本中，Bitwarden 添加了 Argon2id 作为 PBKDF2 的备用选项。[了解更多](kdf-algorithms.md)。
{% endhint %}

一些加密数据，包括用户的受保护对称密钥和主密码哈希，也由应用程序以透明方式静态加密，这意味着它们在流入和流出 Bitwarden 数据库时将被再次加密和解密。

Bitwarden 还使用 Azure 透明数据加密 (TDE) 通过对数据库、关联备份和静态事务日志文件执行实时加密和解密来防止恶意离线活动的威胁。

了解更多信息：[端到端加密如何为零知识铺平道路](https://bitwarden.com/blog/post/end-to-end-encryption-and-zero-knowledge/)和[使用哪些加密技术](https://bitwarden.com/help/article/what-encryption-is-used/)。

### 如何确保密码库项目的安全 <a href="#how-vault-items-are-secured" id="how-vault-items-are-secured"></a>

所有与您存储的密码库数据相关的信息（登录、支付卡、身份信息、笔记）都受端到端加密的保护。您选择存储在 Bitwarden 密码库中的项目首先会被存储在一个叫做 Cipher 对象的项目中。Cipher 对象使用您生成的对称密钥加密，只有通过使用扩展主密钥解密受保护的对称密钥，才能知道此对称密钥。这种加密和解密完全是在 Bitwarden 客户端上完成的，因为你的主密码或扩展主密钥永远不会存储到 Bitwarden 服务器，也不会传输到 Bitwarden 服务器。

#### 密码库健康报告 <a href="#vault-health-reports" id="vault-health-reports"></a>

所有 Bitwarden 付费计划都附带针对个人和组织的密码库健康报告。

对于个人密码库，个人用户可以使用以下报告：

* 公开密码报告
* 重复使用密码报告
* 弱密码报告
* 不安全网站报告
* 无效 2FA 报告
* 数据泄露报告

对于商业用户，组织密码库项目存在一组类似的报告。

了解更多：[密码库健康报告](../your-vault/vault-health-reports.md)

有关 Bitwarden 事件日志和外部报告的更多信息，请参阅[事件日志](../admin-console/reporting/event-logs.md)。

### 将密码和其他机密导入 Bitwarden <a href="#importing-passwords-and-other-secrets-into-bitwarden" id="importing-passwords-and-other-secrets-into-bitwarden"></a>

您可以轻松地将数据从 40 多种不同的服务（包括所有流行的密码管理器应用程序）导入 Bitwarden。[Bitwarden 帮助中心](../import-export/import-data-to-your-vault.md)记录了受支持的应用程序的完整列表以及一些其他信息，包括将数据导入 Bitwarden 的疑难解答步骤。

如果要从 LastPass.com 网页密码库导出您的站点信息，请参考此帮助说明中的具体信息：[从 LastPass 导入数据](../password-manager/import-and-export/import-guides/import-data-from-lastpass.md)。

### 用户之间共享数据 <a href="#sharing-data-between-users" id="sharing-data-between-users"></a>

{% embed url="https://bitwarden.com/_gatsby/image/247a0dc16f67c8c202ec1075c4eaa600/df3d74ff52a7f409cfdddc70d8d1be60/whitepaper-orgcloseup.webp?eu=dd8f59e4ea9ea8d1596cf2836c23676de96e54aef60767833935b0ae1cfecdd02df64a5124902be52d6f58de80b213eb6fce7d3748bad8dfc9ba1ff6b93cff0850d10fec64e57354517ec2fdb0f302176e941350f082cb5af1687bd5edb6b07610034d2ffb28ed80e6f17120f0c0252df5effb7f3297e866b3560805885b24b827a5ce8b7701e98cee4ca9bcefff0190dbe0320616d3813123300b5a3e8b68eadfd20c0f635048017cd1fc58c268c7e43c4a30270f5907f23268d151f26b32c6e3faf25adf7c72e0aac12e37de9aead5ad4bec7f34fa9065fed167254d58e953b3fc25a0&a=w%3D850%26h%3D478%26fm%3Dwebp%26q%3D75&cd=2023-09-08T13%3A16%3A28.412Z" %}
图示：组织密钥保护与交换
{% endembed %}

使用密码管理器的优势之一就是协作。为了实现共享，首先需要创建一个组织。Bitwarden 组织是一个实体，它将想要共享项目的用户联系在一起。一个组织可以是一个家庭、团队、公司、或希望共享数据的任何其他类型的团体。

单个用户账户可以创建和/或属于许多不同的组织，允许你从一个账户管理你的项目。

您可以从网页密码库中创建一个新的 Bitwarden 组织，或者请求现有组织的管理员向您发出邀请。

#### 当您创建一个组织时 <a href="#when-you-create-an-organization" id="when-you-create-an-organization"></a>

将使用加密安全伪随机数生成器 (CSPRNG) 生成组织对称密钥。该组织对称密钥用于解密组织拥有的密码库数据，因此与组织成员共享数据需要安全地提供对其的访问权限。原始组织对称密钥永远不会存储在 Bitwarden 服务器上。

生成了组织对称密钥后，就会使用 RSA-OAEP 通过组织创建者的 RSA 公钥加密组织对称密钥。在创建账户时会为每个用户生成一个 RSA 密钥对，无论他们是否是组织成员，因此该密钥在组织创建之前就已经存在。

{% hint style="info" %}
RSA 私钥（其用途如下所述）是使用用户账户加密密钥加密存储的，因此用户必须完全登录才能访问它。
{% endhint %}

此操作的结果值称为受保护的组织对称密钥，并发送到Bitwarden服务器。

当组织创建者或任何组织成员登录到他们的账户时，客户端应用程序使用已解密的 RSA 私钥来解密受保护的组织对称密钥，从而产生组织对称密钥。使用组织对称密钥，在本地解密组织拥有的密码库数据。

#### 当用户加入组织时 <a href="#when-users-join-an-organization" id="when-users-join-an-organization"></a>

后续用户加入组织的过程非常相似，但有些差异值得注意。

首先，组织的既定成员（特别是有权限入职其他用户的成员）向组织确认该用户。该既定成员由于已经登录其账户并完成了上一节中描述的组织数据解密过程，因此可以访问已解密的组织对称密钥。

因此，当新用户得到确认时，既定成员的客户端将连接到 Bitwarden 服务器，检索新用户的 RSA 公钥（该密钥在创建账户时存储在 Bitwarden 服务器上），并用它来加密已解密的组织对称密钥。这会产生一个新的受保护组织对称密钥，该密钥将发送到 Bitwarden 服务器并为新成员存储。

{% hint style="info" %}
每个受保护的组织对称密钥对于其用户来说都是唯一的，但是当使用其特定用户的 RSA 私钥解密时，每个受保护的组织对称密钥都将解密为相同的所需组织对称密钥。
{% endhint %}

新用户登录其账户时，客户端应用程序使用已解密的 RSA 私钥来解密新的受保护组织对称密钥，从而生成组织对称密钥。使用组织对称密钥，在本地解密组织拥有的密码库数据。

阅读更多：[什么是组织？](../organizations/organizations.md)

#### 访问控制和 Bitwarden 集合管理 <a href="#access-controls-and-managing-bitwarden-collections" id="access-controls-and-managing-bitwarden-collections"></a>

随着您的组织对 Bitwarden 的使用越来越多，拥有不需要访问组织密码库中的所有资源而能够独立管理集合的用户是很有帮助的。

管理集合和群组是一种简单的方式，用于在 Bitwarden 中隔离、授予或限制对密码库项目的访问，从而控制用户对资源的可见性。

Bitwarden 帮助中心的[用户类型和访问控制](../admin-console/user-management/member-roles-and-permissions.md)部分记录了完整的角色和访问控制列表。

阅读更多：[关于集合](../organizations/collections.md)

#### 事件日志 <a href="#event-logs" id="event-logs"></a>

事件日志包含了时间标记、在一个组织内发生了哪些动作或更改的详细情况。这些日志对于研究凭证或配置的更改有帮助，以及对于审计跟踪调查和故障排除非常有用。

更多关于[事件日志](../admin-console/reporting/event-logs.md)的信息记录于 Bitwarden 帮助中心。事件日志仅适用于团队和商业计划。

要收集更多的数据，具有 API 访问权限的计划可以使用 Bitwarden API。API 响应将包含事件类型和相关数据。

#### SIEM 集成和外部系统 <a href="#siem-integration-and-external-systems" id="siem-integration-and-external-systems"></a>

对于像 Splunk 这样的安全信息和事件管理 (SIEM) 系统，当从 Bitwarden 导出数据时，可能会使用 API 和 CLI 的数据组合来收集数据。

在帮助中心的 [SIEM 和外部系统集成](../admin-console/reporting/event-logs.md#siem-and-external-systems-integrations)下的**组织事件日志**的说明中概述此过程。

### 账户保护和避免被锁定 <a href="#account-protection-and-avoiding-lockout" id="account-protection-and-avoiding-lockout"></a>

如今，对于基本、高级、家庭和团队计划，Bitwarden 提供的具有安全模式的账户保护不支持用户丢失密码或丢失两步登录恢复代码。

如果你的账户已经启用了两步登录，Bitwarden 不能重置用户密码，也不能禁用两步登录。家庭和团队账户的所有者或管理员无法重置用户密码。有关企业计划的详细信息，请参阅下一章节。

{% hint style="warning" %}
对于丢失了主密码或者丢失了两步登录恢复代码的用户，需要删除他们的账户然后重新开始。
{% endhint %}

为了减轻这些潜在的问题，Bitwarden 建议采取以下措施来保护账户和避免被锁定。

**主密码**

请确定一种保留方式，用于让您能够在您忘记主密码时恢复它。这可能包括将其写下来，并将其存放在一个安全的地方。

**使用主密码提示**

如果有帮助，请使用在注册时由 Bitwarden 提供的主密码提示。或者在任何时候在网页密码库的设置中设置一个提示。

**组织管理**

对于组织，要有多个可以访问和管理组织的管理员。

**两步登录恢复代码**

如果您选择设置两步登录或组织要求您设置两步登录，请务必访问并保留您的恢复代码，并将其存储在与主密码同样安全的地方。

### 企业计划中的账户恢复 <a href="#account-recovery-in-enterprise-plans" id="account-recovery-in-enterprise-plans"></a>

2021 年中期，Bitwarden 为企业计划推出了[账户恢复](../organizations/admin-password-reset.md)功能。使用此选项，用户和组织可以选择实施一个允许管理员和所有者为用户重置密码的新策略。

### Bitwarden 云平台和网页应用程序安全 <a href="#bitwarden-cloud-platform-and-web-application-security" id="bitwarden-cloud-platform-and-web-application-security"></a>

#### Bitwarden 架构概述 <a href="#bitwarden-architecture-overview" id="bitwarden-architecture-overview"></a>

Bitwarden 使用微软团队管理的服务，在微软 Azure 云中安全地处理和存储所有数据。由于 Bitwarden 只使用 Azure 提供的服务产品，因此没有服务器基础设施需要管理和维护。所有的正常运行时间、可扩展性和安全更新、补丁和保证都由微软及其云基础设施提供支持。

#### 安全更新和补丁 <a href="#security-updates-and-patching" id="security-updates-and-patching"></a>

微软的团队在两个层面上管理操作系统补丁，即物理服务器和运行 Azure 应用服务资源的客户虚拟机 (VM)。两者每月都会更新，这与每月的[微软周二补丁计划](https://docs.microsoft.com/zh-cn/security-updates/)保持一致。这些更新会自动应用，以保证 Azure 服务 SLA 的高可用性。

阅读更多内容：[Azure 应用服务中的补丁](https://docs.microsoft.com/zh-cn/azure/app-service/overview-patch-os-runtime)或[应用服务 SLA](https://azure.microsoft.com/zh-cn/support/legal/sla/app-service/v1_0/)。

有关更新如何应用的详细信息，请阅读[这里](https://azure.github.io/AppService/2018/01/18/Demystifying-the-magic-behind-App-Service-OS-updates.html)。

{% embed url="https://bitwarden.com/_gatsby/image/4e05430a00a931e81bbbe914306e5ef8/df3d74ff52a7f409cfdddc70d8d1be60/whitepaper-final.webp?eu=d68853e0e0cdff8f0b3cf4d73c233169b16d51feaf5835d03c66b1ae1cad96d22cf41156279778b52a6808d8d6e546ec33952c681aee828f93ba1bf2eb66a80b55805fea64e6700f507dc3fbe1fd534d6ccf1d51f080cc0ea06474d6e3b5b47410594f23fa72b9d3e4ab3735b08b7a33e2b1af2c3796fe7ee6445c51c14035b824f89ac12c47b39fe74aacf8bded5f9cdfa4784303c5ad6066684b5d06be6be1a4e40c2c7e2e5f5d55baee06b060dce0547d1d425b5b41aa676b9506fb7360cab2fbf454d17f73e9abcd35708fcbfa83ea4fa42876e4c972a1d03a790a5fb354f5e53fa29235465bc337accc12e35f1b751ed5&a=w%3D850%26h%3D478%26fm%3Dwebp%26q%3D75&cd=2023-09-08T13%3A16%3A35.988Z" %}
图示：Bitwarden 架构概述
{% endembed %}

#### Bitwarden 访问控制 <a href="#bitwarden-access-controls" id="bitwarden-access-controls"></a>

Bitwarden 的员工在他们设计、构建、实施、管理、支持并与之交互的数据、系统和信息资产类型方面具有丰富的培训和专业知识。

Bitwarden 遵循既定的入职流程，以确保分配和维护适当的访问级别。Bitwarden 为每个角色制定了适当的访问级别。所有的请求，包括任何访问请求变更，都需要由经理审查和批准。Bitwarden 遵循最低权限策略，给予员工完成其职责所需的最低级别的访问权限。Bitwarden 通过 Bitwarden 人力资源部门遵循既定的离职流程，在员工离职时取消所有访问权限。

#### 软件生命周期和变更管理 <a href="#software-lifecycle-and-change-management" id="software-lifecycle-and-change-management"></a>

Bitwarden 会对平台、应用程序和生产基础设施的变更进行评估，以将风险降到最低，在 Bitwarden，这些变更的实施遵循的标准操作流程。

变更请求项目根据路线图进行规划，并在此时提交给工程部门。工程部门将审核和评估他们的能力，并考核每个变更请求项目的努力程度。经过审核和评估后，他们将制定指定版本的工作内容。CTO 通过沟通渠道和管理会议提供版本的细节，并开始该版本的开发生命周期。

高级开发、发布、测试和批准流程：

* 使用 GitHub 中的拉取请求进行开发、构建和迭代
* 让功能达到可测试的程度
* 工程部门在开发和构建过程中对功能和/或产品进行功能测试
* 作为 Bitwarden 持续集成 (CI) 管道的一部分，单元测试构建是自动化的
* &#x20;一些测试也由客户成功团队执行
* 工程总监协助审核，并帮助正式确定流程，包括文档更新
* CTO 提供最后的执行/不执行批准

出席会议：为确保成功进行审核、批准实施并结束变更请求，每个核心业务和信息技术服务人员都应派代表参加会议，审核和讨论变更请求。

紧急部署/热修补程序将获得更高的优先级，并在变更前从经理或主管那里获得审核和批准，随后在下一次预定的变更会议上进行审核、沟通并关闭。这通常是在服务中断、系统停机或紧急中断预防的情况下。

#### 生产系统的控制 <a href="#control-of-production-systems" id="control-of-production-systems"></a>

Bitwarden 维护所有生产系统的文档化运行手册，涵盖部署、更新和故障排除流程。还设置了大量的警报，以便在出现问题时通知和升级。

**基线配置**：Bitwarden 使用由微软团队管理的服务，在微软 Azure 云中安全地处理和存储所有数据。由于 Bitwarden 只使用 Azure 提供的服务产品，因此没有服务器基础设施需要管理和维护。所有的正常运行时间、可扩展性、安全更新和保证都由微软及其云基础设施提供支持。

Bitwarden 使用 Azure 服务配置来确保以可重复且一致的方式配置和部署应用程序。

#### Bitwarden 平台密钥管理程序 <a href="#bitwarden-platform-key-management-procedures" id="bitwarden-platform-key-management-procedures"></a>

Bitwarden 平台本身使用了密钥和其他机密，包括 Bitwarden 云提供商账户的凭证。所有这些密钥都是按照行业标准的做法生成、安全存储并根据需要进行轮换。Bitwarden 使用一个内部 Bitwarden 密码库，用于安全存储和备份 Bitwarden 平台所使用的敏感密钥或其他机密。Bitwarden 密码库的访问控制使用[用户类型和访问控制](../admin-console/user-management/member-roles-and-permissions.md)。

#### 数据类型和数据保留 <a href="#data-types-and-data-retention" id="data-types-and-data-retention"></a>

Bitwarden 处理两种类型的用户数据来提供 Bitwarden 服务：(i) 密码库数据和(ii) 管理数据。

(i) 密码库数据

密码库数据包括存储在 Bitwarden 服务账户中的所有信息，并且可能包括个人信息。如果我们为您托管 Bitwarden 服务，我们将托管密码库数据。密码库数据使用受您控制的安全加密密钥进行加密。Bitwarden 无法访问密码库数据。

密码库数据的数据保留：您可以随时添加、修改和删除密码库数据。

(ii) 管理数据

Bitwarden 会因您的账户创建、Bitwarden 服务和支持的使用，以及对 Bitwarden 服务的支付而获取个人信息，如 Bitwarden 服务用户的姓名、电子邮件地址、电话和其他联系信息，以及您的 Bitwarden 服务账户（「管理数据」）中的项目数量。Bitwarden 使用管理数据向您提供 Bitwarden 服务。只要您是 Bitwarden 的客户，我们就会按照法律要求保留管理数据。如果您终止与 Bitwarden 的关系，我们将根据我们的数据保留政策删除您的个人信息。

当您使用本网站或与我们沟通（如通过电子邮件）时，您将提供，Bitwarden 也将收集某些个人信息，如：

* 姓名
* 公司名称和地址
* 公司电话号码
* 电子邮件地址
* IP 地址和其他在线标识符
* 您同意我们分享的任何客户评价
* 您提供给网站互动区域的信息，如可填写的表格或文本框、培训、网络研讨会或活动注册
* 您使用的设备信息，包括硬件型号、操作系统和版本、唯一设备标识符、网络信息、IP 地址和/或与网站互动时的 Bitwarden 服务信息
* 如果您与 Bitwarden 社区或培训互动，或注册参加网络研讨会或活动，我们可能会收集您的履历信息以及您分享的内容
* 通过 cookie、像素标签、日志或其他类似技术收集的信息

更多信息请参考 [Bitwarden 隐私政策](https://bitwarden.com/privacy/)。

#### 记录、监控和警报通知 <a href="#logging-monitoring-and-alert-notification" id="logging-monitoring-and-alert-notification"></a>

Bitwarden 维护所有生产系统的文档化运行手册，涵盖部署、更新和故障排除流程。设置了大量的警报，以便在出现问题时通知和升级。Bitwarden 云基础设施的手动和自动监控相结合，提供了一个全面和详细的系统健康状况视图，以及对关注区域的主动警报。问题会迅速浮出水面，以便我们的基础设施团队能够有效地应对和缓解问题，将干扰降到最低。

#### 业务连续性/灾难恢复 <a href="#business-continuity-disaster-recovery" id="business-continuity-disaster-recovery"></a>

Bitwarden 使用了微软 Azure 的全套灾难恢复和业务连续性实践，这些实践都是内置在 Bitwarden 云中的。这包括针对我们的应用程序和数据库层面的高可用性和备份服务。

#### 威胁预防和应对 <a href="#threat-prevention-and-response" id="threat-prevention-and-response"></a>

Bitwarden 定期进行漏洞评估。我们使用第三方工具和外部服务，包括：OWASP ZAP、[Mozilla Observatory](https://observatory.mozilla.org/)、OpenVAS 等用来做内部评估。

Bitwarden 使用 Cloudflare 用于在边缘提供 WAF、更好的 DDoS 防护、分布式可用性和缓存。Bitwarden 还使用 Cloudflare 代理，以为我们的服务和网站获得更好的网络安全及性能。

Bitwarden 是一个开源软件。我们所有的源代码都托管在 GitHub 上，任何人都可以免费审查。Bitwarden 的源代码由著名的第三方安全审计公司以及独立的安全研究人员进行审计。此外，[Bitwarden 漏洞披露计划](https://hackerone.com/bitwarden?type=team\&view_policy=true)还得到了 HackerOne 黑客社区的帮助，以使 Bitwarden 更加安全。

#### 审计性和合规性 <a href="#auditability-and-compliance" id="auditability-and-compliance"></a>

Bitwarden 安全与合规计划基于 ISO27001 信息安全管理系统 (ISMS)。我们已经定义了管理我们的安全政策和流程的政策，并不断更新我们的安全计划，以符合适用的法律、行业和监管要求，以便我们在我们的[服务条款协议](https://bitwarden.com/terms/)下向您提供服务。

Bitwarden 遵守行业标准的应用程序安全准则，包括一个专门的安全工程团队，并定期审查应用程序源代码和 IT 基础设施，以检测、验证和修复任何安全漏洞。

**外部安全审查**：对应用程序和/或平台的第三方安全审查和评估每年至少进行一次。

**认证**：Bitwarden 的认证包括：

* SOC2 Type II（每年更新）
* SOC3（每年更新）&#x20;

根据 AICPA 的规定，SOC 2 第二类报告的使用受到限制。如需查询 SOC 2 报告，请[联系我们](https://bitwarden.com/contact/)。

阅读更多：[Bitwarden 实现 SOC2 认证](https://bitwarden.com/blog/post/bitwarden-achieves-soc-2-certification/)。

SOC 3 报告是对 SOC 2 报告的总结，可以公开发布。根据 AICPA 的规定，SOC 3 是服务机构的 SOC 报告，是关于信托服务标准的通用报告。[在这里](https://cdn.bitwarden.com/misc/Bitwarden%202020%20SOC%203%20Report.pdf) Bitwarden 提供了一份我们的 SOC 3 报告的副本。

这些 SOC 认证代表了我们对保障客户安全和隐私的承诺，以及对严格标准的遵守。Bitwarden 还定期对我们的网络安全和代码完整性进行审计。

阅读更多：[Bitwarden 2020 安全审计完成](https://bitwarden.com/blog/post/bitwarden-network-security-assessment-2020/)和 [Bitwarden 完成第三方安全审计](https://bitwarden.com/blog/post/third-party-security-audit/)。

#### HTTP 安全头文件 <a href="#http-security-headers" id="http-security-headers"></a>

Bitwarden 使用 HTTP 安全头文件作为 Bitwarden 网络应用和通信的额外保护层。例如，HTTP 严格传输安全 (HSTS) 将强制所有连接使用 TLS，从而降低降级攻击和错误配置的风险。内容安全策略头文件提供进一步的保护，防止注入攻击，如跨站点脚本 (XSS)。此外，Bitwarden 还实现了 X-Frame-Options：SAMEORIGIN 用来抵御点击劫持。

### 威胁模型和攻击面分析概述 <a href="#threat-model-and-attack-surface-analysis-overview" id="threat-model-and-attack-surface-analysis-overview"></a>

Bitwarden 遵循基于风险的方法来设计安全服务和系统，包括威胁建模和攻击面分析，以识别威胁并制定缓解措施。风险和威胁建模分析扩展到 Bitwarden 平台的所有领域，包括核心 Bitwarden 云服务器应用程序和 Bitwarden 客户端，如移动端、桌面端、网页 App、浏览器和/或命令行界面。

#### Bitwarden 客户端 <a href="#bitwarden-clients" id="bitwarden-clients"></a>

用户主要通过我们的客户端应用程序与 Bitwarden 进行交互，如移动端、桌面端、网页 App、浏览器和/或命令行界面。这些设备、工作站和网页浏览器的安全是至关重要的，因为如果这些设备中的一个或多个被入侵，攻击者可能会安装恶意软件，如键盘记录器，从而获取在这些设备上输入的所有信息，包括您的任何密码和机密。作为终端用户和/或设备所有者，您有责任确保您的设备安全，并防止非授权访问。

#### HTTPS TLS 和网页浏览器端到端加密 <a href="#https-tls-and-web-browser-crypto-end-to-end-encryption" id="https-tls-and-web-browser-crypto-end-to-end-encryption"></a>

Bitwarden 网页客户端运行在您的网页浏览器中。Bitwarden 网页客户端的真实性和完整性取决于传输客户端的 HTTPS TLS 连接的完整性。攻击者如果能够篡改传递给网页客户端的流量，就可以向用户提供一个恶意客户端。

网页浏览器攻击是攻击者和网络犯罪分子注入恶意软件或造成破坏的最流行方式之一。对网页浏览器的攻击载体可能包括：

* **社会工程元素，如网络钓鱼**：欺骗和说服受害者采用任何危害其用户机密和账户安全的行为
* **浏览器攻击和浏览器扩展/附加组件漏洞**：当用户在键盘上打字时，恶意扩展程序就会捕捉到用户的机密
* **通过浏览器对网页应用程序的攻击**：点击劫持、跨站点脚本 (XSS)、跨站点请求伪造 (CSRF)。

Bitwarden 使用 [HTTP 安全头文件](bitwarden-security-whitepaper.md#http-security-headers)作为 Bitwarden 网络应用和通信的额外保护层。

#### 代码评估 <a href="#code-assessments" id="code-assessments"></a>

Bitwarden 是一个开源的密码管理器。我们所有的源代码都托管在 [GitHub](https://github.com/bitwarden) 上，并提供给大家公开审查。Bitwarden 的源代码每年都由被著名的第三方安全审计公司以及独立的安全研究人员进行审计。此外，Bitwarden 漏洞披露计划还得到了 HackerOne 黑客社区的帮助，以使 Bitwarden 更加安全。

阅读更多：

* [Bitwarden 安全常见问题](security-faqs.md)
* [Bitwarden 威胁预防和应对](bitwarden-security-whitepaper.md#threat-prevention-and-response)
* [Bitwarden 安全和合规性评估、审核、漏洞扫描、PenTesting](bitwarden-security-whitepaper.md#auditability-and-compliance)

## 总结 <a href="#conclusion" id="conclusion"></a>

提供此 Bitwarden 安全与合规计划概述，以供您参考。Bitwarden 的解决方案、软件、基础设施和安全流程都是以多层次、深入防御的方式从头设计的。

Bitwarden 的安全与合规计划基于 ISO27001 信息安全管理体系 (ISMS)。我们定义了管理我们的安全政策和流程的政策，并不断更新我们的安全计划，以符合适用的法律、行业和监管要求，以便我们在我们的[服务条款协议](https://bitwarden.com/terms/)下向您提供服务。

如果您有任何疑问，请[联系我们](https://github.com/bitwarden/help/blob/master/_articles/security/www.bitwarden.com/contact)。

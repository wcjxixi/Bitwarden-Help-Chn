# Bitwarden 安全白皮书

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/bitwarden-security-white-paper/)
{% endhint %}

> **\[译者注]**术语解释：
>
> * [ISMS](https://en.wikipedia.org/wiki/Information\_security\_management)：Information Security Management System（信息安全管理体系）
> * [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2)：Password-Based Key Derivation Function 2（基于密码的密钥派生函数 2）
> * [HKDF](https://en.wikipedia.org/wiki/HKDF)：HMAC-based Extract-and-Expand Key Derivation Function（基于 HMAC 的提取和扩展密钥派生函数）
> * [CSPRNG](https://en.wikipedia.org/wiki/CSPRNG)：Cryptographically Secure Pseudorandom Number Generator（加密安全伪随机数生成器）
> * [HSTS](https://en.wikipedia.org/wiki/HTTP\_Strict\_Transport\_Security)：HTTP Strict Transport Security（HTTP 严格传输安全）
> * [SIEM](https://en.wikipedia.org/wiki/Security\_information\_and\_event\_management)：Security Information and Event Management（安全信息和事件管理）
> * [XSS](https://en.wikipedia.org/wiki/Cross-site\_scripting)：Cross-Site Scripting（跨站点脚本）
> * [CSRF](https://en.wikipedia.org/wiki/Cross-site\_request\_forgery)：Cross-Site Request Forgery（跨站点请求伪造）

{% hint style="success" %}
请阅读下面的全文，或[下载 PDF](https://bitwarden.com/images/resources/security-white-paper-2021.pdf)（英文）。
{% endhint %}

## Bitwarden 安全与合规计划概述 <a href="#overview-of-bitwarden-security-and-compliance-program" id="overview-of-bitwarden-security-and-compliance-program"></a>

随着越来越多地使用远程工作，互联网的使用率比以往任何时候都高，创建和维护几十个（甚至上百个）具有登录和密码的在线账户的需求也是惊人的。

安全专家建议对每一个创建的账户使用不同的、随机生成的密码。但如何管理所有这些密码呢？又如何在整个组织中保持良好的密码健康呢？

有效的密码管理是企业中还未被充分利用的资源。[Rapid7 2020 年连帽衫报告](https://www.rapid7.com/research/reports/under-the-hoodie-2020/)指出，密码管理和二次控制（如双因素验证）「严重缺乏导致 ‘轻松’ 泄露」。以不安全的方式重复使用密码或共享密码，使企业变得脆弱。

要给企业带来改变，安全和 IT 团队必须对员工进行最佳实践的教育。关于密码管理，对密码健康有促进的最简单方法之一就是在整个工作场所部署密码管理解决方案。

要存储所有的登录、密码和其他敏感信息，同时又可以方便地在所有设备之间同步，Bitwarden 是最简单、最安全的方式。

Bitwarden 提供了创建、存储和共享密码的工具，同时又保持最高级别的安全性。

Bitwarden 的解决方案、软件、基础设施和安全流程都是以多层次、深入防御的方式从头设计的。Bitwarden 的安全与合规计划基于 ISO27001 信息安全管理体系（ISMS）。我们定义了管理我们的安全政策和流程的政策，并不断更新我们的安全计划，以符合适用的法律、行业和监管要求，以便我们在我们的[服务条款协议](https://bitwarden.com/terms/)下向您提供服务。

Bitwarden 遵守行业标准的应用安全准则，包括一个专门的安全工程团队，并定期审查应用源代码和 IT 基础设施，以检测、验证和修复任何安全漏洞。

本白皮书概述了 Bitwarden 的安全原则，并提供了其他文件的链接，以在特定领域提供更多细节。

## Bitwarden 安全原则 <a href="#bitwarden-security-principles" id="bitwarden-security-principles"></a>

### 用户数据保护 <a href="#user-data-protection" id="user-data-protection"></a>

Bitwarden 采用以下关键安全措施来保护用户数据。

**端到端加密**：使用端到端的 AES-CBC 256 位加密、盐化的哈希和 PBKDF2 SHA-256 来锁定您的密码以及私人信息。所有的加密密钥都由您设备上的客户端生成和管理，以及所有的加密都在本地完成。更多详情请查看[密码哈希派生](bitwarden-security-whitepaper.md#overview-of-the-master-password-hashing-key-derivation-and-encryption-process)部分。

**零知识加密**：Bitwarden 团队成员无法看到您的密码。您的数据使用您的个人电子邮件和主密码被端到端加密。我们永不存储也无法访问您的主密码或您的加密密钥。

{% hint style="info" %}
2021 年中期发布的管理员密码重置功能为所有组织引入了一个新的 RSA 公钥/私钥对。私钥在存储之前将使用组织中预先存在的对称密钥进一步加密。在创建新组织时将在客户端生成并加密此密钥，或者对于现有的组织：

* 导航到**管理** → **人员**界面。
* 更新**设置** → **我的组织**界面上的任何内容。
* 从一种组织类型升级到另一种组织类型。
{% endhint %}

**安全密码共享**：Bitwarden 可以在整个组织中与用户安全地共享和管理敏感数据。当敏感信息被共享时，受到非对称和对称加密组合的保护。

**开源和可用源码**：所有 Bitwarden 软件产品的源代码都托管在 [GitHub](https://github.com/bitwarden) 上，我们欢迎大家对 Bitwarden 代码库进行审查、审计和贡献。Bitwarden 源代码由著名的第三方安全审计公司以及独立的安全研究人员进行审计。此外，[Bitwarden 漏洞披露计划](https://hackerone.com/bitwarden?type=team\&view\_policy=true)还得到了 HackerOne 黑客社区的帮助，以使 Bitwarden 更加安全。

**通过设计保护隐私**：Bitwarden 将你所有的登录信息存储在一个加密的密码库中，并在你所有的设备上同步。由于它在离开你的设备之前就已经完全加密了，所以只有你才能访问你的数据。即使 Bitwarden 团队也无法读取您的数据（即使我们想读取）。您的数据被 AES-CBC 256 位加密、盐化哈希和 PBKDF2 SHA-256 密封。

**安全审计 & 合规**：Bitwarden 符合 AICPA SOC2 类型 2 /隐私保护，GDPR 和 CCPA 法规，开源并经第三方审计。

#### 主密码 <a href="#master-password" id="master-password"></a>

Bitwarden 的用户数据保护始于用户创建账户和主密码的那一刻。我们强烈建议在入职过程中使用一个强大的主密码。Bitwarden 提供了一个密码强度计，它将评估并显示正在输入的主密码的整体强度，以鼓励使用强大的主密码。

![创建一个 Bitwarden 账户](https://github.com/bitwarden/help/raw/master/images/security-white-paper/create-account.png)

如果你试图使用弱密码注册，Bitwarden 会提醒你选择的主密码是弱密码。

![弱主密码警告](https://github.com/bitwarden/help/raw/master/images/security-white-paper/weak-master-password-warning.png)

使用一个强大的主密码是为您自己的安全利益着想，因为它是您用来访问您的安全密码库的令牌，您的敏感物品就存放在那里。在您使用 Bitwarden 服务时，您有责任保证您的账户安全。我们提供额外的措施，如两步登录，帮助您维护您的账户安全，但您的账户内容及其安全由您决定。

![选择一个强主密码](https://github.com/bitwarden/help/raw/master/images/security-white-paper/choose-a-strong-master-password.png)

阅读更多：[密码管理的五种最佳实践](https://bitwarden.com/blog/post/five-best-practices-for-password-management/)和[来自 NIST 的 3 个小贴士让你的密码安全无忧](https://bitwarden.com/blog/post/3-tips-from-nist-to-keep-passwords-secure/)。

有用的工具：[Bitwarden 密码强度测试工具](https://bitwarden.com/password-strength/)和 [Bitwarden 密码生成器](https://bitwarden.com/password-generator/)。

**非常重要的是，永远不要忘记您的主密码**。主密码在使用后会从内存中清除，不会通过互联网传输到 Bitwarden 服务器，因此，如果您忘记了主密码，无任何办法恢复它。

这也意味着 Bitwarden 团队的任何人都无法看到、阅读或通过逆向工程获得您的真实数据。您的数据在离开您的本地设备之前就已经被完全加密和/或哈希了。这是 Bitwarden 保护您和您的数据的一个关键步骤。

在创建您的账户并指定您的主密码后，Bitwarden 接下来会生成一系列密钥，用于保护您账户的数据。

{% hint style="info" %}
2021 年中期，Bitwarden 为企业计划引入了管理员密码重置功能。使用此选项，用户和组织可以选择实施一个允许管理员和所有者为用户重置密码的新策略。有关此功能的更多详细信息，请访问我们的帮助站点 [https://bitwarden.com/help/article/releasenotes/](https://bitwarden.com/help/article/releasenotes/)
{% endhint %}

### 主密码哈希、密钥派生和加密过程概述 <a href="#overview-of-the-master-password-hashing-key-derivation-and-encryption-process" id="overview-of-the-master-password-hashing-key-derivation-and-encryption-process"></a>

#### 用户账户创建 <a href="#user-account-creation" id="user-account-creation"></a>

提交「创建账户」表单后，Bitwarden 使用具有 100,000 次迭代的基于密码的密钥派生函数 2（PBKDF2）来扩展具有盐化的用户电子邮件地址的用户主密码。最终的盐化值是 256 位主密钥。使用基于 HMAC 的提取和扩展密钥派生函数（HKDF），还可以将主密钥的长度扩展为 512 位长度。主密钥和扩展主密钥永远不会存储到 Bitwarden 服务器或传输到 Bitwarden 服务器。

![基于密码的密钥派生](https://github.com/bitwarden/help/raw/master/images/security-white-paper/password-based-key-deviation.png)

此外，使用加密安全伪随机数生成器（CSPRNG）生成 512 位对称密钥和初始化向量。使用扩展的主密钥和初始化向量，用 AES-256 位加密对对称密钥进行加密。得到的密钥称为受保护的对称密钥。受保护的对称密钥是与用户相关联的主密钥，在账户创建时被发送到服务器，并在同步时返回到 Bitwarden 客户端应用程序。

当用户注册账户时，也会生成一个非对称密钥（RSA 密钥对）。当用户创建组织时，会使用生成的 RSA 密钥对。组织被创建并用于在用户之间共享数据。当您创建一个组织时，将使用加密安全伪随机数生成器（CSPRNG）生成组织对称密钥。使用生成的 RSA 密钥对中的公钥加密组织对称密钥。生成的 RSA 密钥对中的私钥与生成的对称密钥使用 AES-256 加密。

更多细节请参考[在用户之间共享数据](bitwarden-security-whitepaper.md#sharing-data-between-users)。下面的图表显示了创建 Bitwarden 用户账户时生成的各种密钥。

![注册新的 Bitwarden 帐户时创建的各种密钥的概述](https://github.com/bitwarden/help/raw/master/images/security-white-paper/overview-of-keys-generated.png)

主密码哈希值也是使用带主密钥有效载荷和主密码盐化的 PBKDF-SHA256 生成。主密码哈希值在账户创建和登录时被发送到服务器，用于验证用户账户。到达服务器后，将使用随机盐化的 PBKDF2-SHA256 和 100,000 次迭代再次对主密码哈希值进行哈希。密码哈希、密钥派生和加密过程的概述如下图所示：

![Bitwarden 密码散列、密钥派生和加密](https://github.com/bitwarden/help/raw/master/images/security-white-paper/bitwarden-password-hashing-key-derivation-encryption.png)

#### 用户登录 | 用户验证 | 访问用户密码库数据 <a href="#user-login-or-user-authentication-or-access-to-user-vault-data" id="user-login-or-user-authentication-or-access-to-user-vault-data"></a>

您需要先输入您的电子邮件地址和主密码才能登录您的 Bitwarden 账户。

接下来，Bitwarden 使用具有默认为 100,000 次迭代的基于密码的密钥衍生函数 2（PBKDF2）来扩展具有盐化的用户电子邮件地址的主密码。所得的盐化值就是 256 位的主密钥。主密钥的哈希值会在账户创建和登录时发送到服务器，并用于验证用户账户。

主密钥还可以使用基于 HMAC 的提取和扩展密钥派生函数（HKDF）扩展到 512 位长度。受保护的对称密钥使用扩展的主密钥进行解密。对称密钥用于解密密码库项目。解密工作完全在 Bitwarden 客户端上完成，因为您的主密码或扩展主密钥绝不会存储到 Bitwarden 服务器，也不会传输到 Bitwarden 服务器。

![用户登录概述](https://github.com/bitwarden/help/raw/master/images/security-white-paper/user-login-diagram.png)

我们不会将主密码保存在本地或 Bitwarden 客户端内存中。您的加密密钥（对称密钥）会在应用程序解锁时保存在内存中。这是您解密密码库数据所需要的。当密码库被锁定时，这些数据会从内存中清除。在锁屏一定时间内不活动后，我们会重新加载应用程序进程，以确保任何剩余的管理内存地址也被清除。我们尽最大努力确保任何用于应用程序运作的数据只在您需要的时候保留在内存中，并且每当应用程序被锁定时，内存都会被清理。我们认为应用程序在锁定状态下是完全安全的。

#### 启用两步登录后的额外用户数据保护 <a href="#additional-user-data-protection-when-enabling-two-step-login" id="additional-user-data-protection-when-enabling-two-step-login"></a>

两步登录（也称为双因素验证或 2FA）是您账户的额外安全层，旨在确保您是**唯一**可以访问您的账户的人，即使有人得到了您的主密码。

作为最佳实践，我们建议所有用户在其 Bitwarden 帐户中激活并使用两步登录。激活两步登录后，您需要在登录 Bitwarden 时完成第二步（除了您的主密码）。默认情况下，每次都会提示您完成第二步，但是会出现一个「记住我」提示，该提示将保存您的 2FA 状态，因此您下次无需使用 2FA 即可在该特定设备上登录最多长达 30 天。

注意：更改你的主密码或取消会话授权都需要重新验证 2FA，无论你之前是否勾选了「记住我」。

Bitwarden 支持如下方式的两步登录：

**免费计划**

* 使用验证应用程序，如 [Authy](https://authy.com/) 或 [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=zh-Hans)
* 电子邮件&#x20;

**高级功能 - 包含于家庭、团队和企业计划中**

* 具有 Duo 推送、短信、电话和 U2F 安全钥匙的 Duo 安全
* YubiKey（任何 4/5 系列设备或 YubiKey NEO/NFC）
* FIDO U2F（任何经 FIDO U2F 认证的钥匙）&#x20;

您可以启用多种两步登录方式。如果您启用了多种两步登录方式，则登录时显示的默认方式的优先顺序如下：FIDO U2F > YubiKey > Duo > 验证器应用 > Email。不过，您可以在登录时手动切换并使用任何一种方式。

**非常重要的一点是，千万不要丢失两步登录恢复代码。**Bitwarden 提供的账户保护安全模式不支持用户丢失主密码或两步登录恢复代码。如果您在账户上启用了两步登录，并丢失了两步登录恢复代码，您将无法登录您的 Bitwarden 账户。

{% hint style="info" %}
2021 年中期，Bitwarden 为企业计划引入了管理员密码重置功能。使用此选项，用户和组织可以选择实施一个允许管理员和所有者为用户重置密码的新策略。有关此功能的更多详细信息，请访问我们的帮助站点 [https://bitwarden.com/help/article/releasenotes/](https://bitwarden.com/help/article/releasenotes/)
{% endhint %}

#### 更改用户密码 <a href="#changing-user-password" id="changing-user-password"></a>

您的主密码只能通过[网页密码库](https://vault.bitwarden.com/#/)更改。有关如何更改用户密码的具体步骤，请参阅[此 Bitwarden 帮助文章](../your-vault/your-master-password.md)。

#### 轮换账户的加密密钥 <a href="#rotating-your-accounts-encryption-key" id="rotating-your-accounts-encryption-key"></a>

在进行密码更改操作期间，您还可以选择轮换（更改）帐户的加密密钥。如果您认为以前的主密码已被盗用，或者您的 Bitwarden 密码库的数据已从其中一台设备上被窃取，则轮换加密密钥是一个好主意。

{% hint style="danger" %}
轮换帐户的加密密钥是一项敏感操作，因此这不是默认选项。密钥轮换会为您的帐户生成一个新的随机加密密钥，并使用此新密钥**重新加密所有密码库数据**。请参阅[此 Bitwarden 帮助文章](../your-vault/your-master-password.md)了解更多详情。
{% endhint %}

#### 中转过程中的数据保护 <a href="#data-protection-in-transit" id="data-protection-in-transit"></a>

在处理您的敏感数据时，Bitwarden 非常重视安全问题。您的数据如果没有在您的本地设备上进行加密，是绝对不会被发送到 Bitwarden 云端的。

此外，Bitwarden 使用 TLS/SSL 来确保 Bitwarden 客户端和用户设备与 Bitwarden 云之间的通信安全。Bitwarden 的 TLS 实施使用 2048 位 X.509 证书进行服务器认证和密钥交换，使用强密码套件进行批量加密。我们的服务器被配置为拒绝弱密码和协议。

Bitwarden 还实现了 HTTP 安全头文件，如 HTTP 严格传输安全（HSTS），它将强制所有连接使用 TLS。这种具有 HSTS 的额外保护层降低了降级攻击和错误配置的风险。

#### 空闲时的数据保护 <a href="#data-protection-at-rest" id="data-protection-at-rest"></a>

在将您的数据发送到云服务器进行同步之前，Bitwarden 总是在您的本地设备上对数据进行加密和/或散列。Bitwarden 服务器仅用于存储和同步加密后的密码库数据，无法从 Bitwarden 云服务器中获取您的未加密数据。具体来说，Bitwarden 使用 AES 256 位加密以及 PBKDF-SHA256 来保护您的数据安全。

AES 是密码学的一个标准，被美国政府和世界各地的其他政府机构用于保护绝密数据。只要实施得当，加上强大的加密密钥（您的主密码），AES 被认为是不可破解的。

PBKDF-SHA256 用于从您的主密码派生加密密钥。然后，这个密钥会经过盐化和哈希处理，以便与 Bitwarden 服务器进行验证。PBKDF2 默认使用的迭代次数是在客户端的 100,001 次（此迭代次数可以从你的账户设置中配置），然后当存储在我们的服务器上时，会有额外的 100,000 次迭代（默认情况下总共为  200,001 次）。

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

有关 Bitwarden 事件日志和外部报告的更多信息，请参阅[事件日志](../organizations/event-logs.md)。

### 将密码和其他机密导入 Bitwarden <a href="#importing-passwords-and-other-secrets-into-bitwarden" id="importing-passwords-and-other-secrets-into-bitwarden"></a>

您可以轻松地将数据从 40 多种不同的服务（包括所有流行的密码管理器应用程序）导入 Bitwarden。 [Bitwarden 帮助中心](../import-export/import-data-to-your-vault.md)记录了受支持的应用程序的完整列表以及一些其他信息，包括将数据导入 Bitwarden 的疑难解答步骤。

如果要从 LastPass.com 网页密码库导出您的站点信息，请参考此帮助说明中的具体信息：[从 LastPass 导入数据](../import-export/import-guides/import-your-data-from-lastpass.md)。

### 用户之间共享数据 <a href="#sharing-data-between-users" id="sharing-data-between-users"></a>

![RSA 密钥对：组织对称密钥和用户非对称密钥](https://github.com/bitwarden/help/raw/master/images/security-white-paper/overview-organization-symmetric-key-and-rsa-key-pair.png)

使用密码管理器的优势之一就是协作。为了实现共享，首先需要创建一个组织。Bitwarden 组织是一个实体，它将想要共享项目的用户联系在一起。一个组织可以是一个家庭、团队、公司、或希望共享数据的任何其他类型的团体。

一个用户账户可以创建和/或属于许多不同的组织，允许你从一个账户管理你的项目。

您可以从网页密码库中创建一个新的 Bitwarden 组织，或者请求现有组织的管理员向您发出邀请。

当您创建一个组织时，将使用加密安全伪随机数生成器（CSPRNG）生成组织对称密钥。使用您生成的 RSA 密钥对中的公钥加密组织对称密钥。使用 AES-256 与生成的对称密钥加密生成的 RSA 密钥对中的私钥。生成的 RSA 密钥对和生成的对称密钥在你第一次注册账户时创建。

阅读更多：[什么是组织？](../organizations/organizations.md)

#### 访问控制和 Bitwarden 集合管理 <a href="#access-controls-and-managing-bitwarden-collections" id="access-controls-and-managing-bitwarden-collections"></a>

随着您的组织对 Bitwarden 的使用越来越多，拥有不需要访问组织密码库中的所有资源而能够独立管理集合的用户是很有帮助的。

管理集合和群组是一种简单的方式，用于在 Bitwarden 中隔离、授予或限制对密码库项目的访问，从而控制用户对资源的可见性。

Bitwarden 帮助中心的[用户类型和访问控制](../organizations/user-types-and-access-control.md)部分记录了完整的角色和访问控制列表。

阅读更多：[如何管理集合](broken-reference)。

#### 事件日志 <a href="#event-logs" id="event-logs"></a>

事件日志包含了时间标记、在一个组织内发生了哪些动作或更改的详细情况。这些日志对于研究凭证或配置的更改有帮助，以及对于审计跟踪调查和故障排除非常有用。

更多关于[事件日志](../organizations/event-logs.md)的信息记录于 Bitwarden 帮助中心。事件日志仅适用于团队和商业计划。

要收集更多的数据，具有 API 访问权限的计划可以使用 Bitwarden API。API 响应将包含事件类型和相关数据。

#### SIEM 集成和外部系统 <a href="#siem-integration-and-external-systems" id="siem-integration-and-external-systems"></a>

对于像 Splunk 这样的安全信息和事件管理（SIEM）系统，当从 Bitwarden 导出数据时，可能会使用 API 和 CLI 的数据组合来收集数据。

在帮助中心的 [SIEM 和外部系统集成](../organizations/event-logs.md#siem-and-external-systems-integrations)下的**组织事件日志**的说明中概述此过程。

### 账户保护和避免被锁定 <a href="#account-protection-and-avoiding-lockout" id="account-protection-and-avoiding-lockout"></a>

如今，对于基本、高级、家庭和团队计划，Bitwarden 提供的具有安全模式的账户保护不支持用户丢失密码或丢失两步登录恢复代码。

如果你的账户已经启用了两步登录，Bitwarden 不能重置用户密码，也不能禁用两步登录。家庭和团队帐户的所有者或管理员无法重置用户密码。有关企业计划的详细信息，请参阅下一章节。

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

### 企业计划中的管理员密码重置 <a href="#admin-password-reset-in-enterprise-plans" id="admin-password-reset-in-enterprise-plans"></a>

2021 年中期，Bitwarden 为企业计划引入了管理员密码重置功能。使用此选项，用户和组织可以选择实施一个允许管理员和所有者为用户重置密码的新策略。有关此功能的更多详细信息，请访问我们的帮助站点 [https://bitwarden.com/help/article/releasenotes/](https://bitwarden.com/help/article/releasenotes/)。

### Bitwarden 云平台和网页应用程序安全 <a href="#bitwarden-cloud-platform-and-web-application-security" id="bitwarden-cloud-platform-and-web-application-security"></a>

#### Bitwarden 架构概述 <a href="#bitwarden-architecture-overview" id="bitwarden-architecture-overview"></a>

Bitwarden 使用微软团队管理的服务，在微软 Azure 云中安全地处理和存储所有数据。由于 Bitwarden 只使用 Azure 提供的服务产品，因此没有服务器基础设施需要管理和维护。所有的正常运行时间、可扩展性和安全更新、补丁和保证都由微软及其云基础设施提供支持。

#### 安全更新和补丁 <a href="#security-updates-and-patching" id="security-updates-and-patching"></a>

微软的团队在两个层面上管理操作系统补丁，即物理服务器和运行 Azure 应用服务资源的客户虚拟机（VM）。两者每月都会更新，这与每月的[微软周二补丁计划](https://docs.microsoft.com/zh-cn/security-updates/)保持一致。这些更新会自动应用，以保证 Azure 服务 SLA 的高可用性。

阅读更多内容：[Azure 应用服务中的补丁](https://docs.microsoft.com/zh-cn/azure/app-service/overview-patch-os-runtime)或[应用服务 SLA](https://azure.microsoft.com/zh-cn/support/legal/sla/app-service/v1\_0/)。

有关更新如何应用的详细信息，请阅读[这里](https://azure.github.io/AppService/2018/01/18/Demystifying-the-magic-behind-App-Service-OS-updates.html)。

![Bitwarden 架构概述](https://github.com/bitwarden/help/raw/master/images/security-white-paper/bitwarden-architecture-overview.png)

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
* 作为 Bitwarden 持续集成（CI）管道的一部分，单元测试构建是自动化的
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

Bitwarden 平台本身使用了密钥和其他机密，包括 Bitwarden 云提供商账户的凭证。所有这些密钥都是按照行业标准的做法生成、安全存储并根据需要进行轮换。Bitwarden 使用一个内部 Bitwarden 密码库，用于安全存储和备份 Bitwarden 平台所使用的敏感密钥或其他机密。Bitwarden 密码库的访问控制使用[用户类型和访问控制](../organizations/user-types-and-access-control.md)。

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

Bitwarden 是一个开源软件。我们所有的源代码都托管在 GitHub 上，任何人都可以免费审查。Bitwarden 的源代码由著名的第三方安全审计公司以及独立的安全研究人员进行审计。此外，[Bitwarden 漏洞披露计划](https://hackerone.com/bitwarden?type=team\&view\_policy=true)还得到了 HackerOne 黑客社区的帮助，以使 Bitwarden 更加安全。

#### 审计性和合规性 <a href="#auditability-and-compliance" id="auditability-and-compliance"></a>

Bitwarden 安全与合规计划基于 ISO27001 信息安全管理系统（ISMS）。我们已经定义了管理我们的安全政策和流程的政策，并不断更新我们的安全计划，以符合适用的法律、行业和监管要求，以便我们在我们的[服务条款协议](https://bitwarden.com/terms/)下向您提供服务。

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

Bitwarden 使用 HTTP 安全头文件作为 Bitwarden 网络应用和通信的额外保护层。例如，HTTP 严格传输安全（HSTS）将强制所有连接使用 TLS，从而降低降级攻击和错误配置的风险。内容安全策略头文件提供进一步的保护，防止注入攻击，如跨站点脚本（XSS）。此外，Bitwarden 还实现了 X-Frame-Options：SAMEORIGIN 用来抵御点击劫持。

### 威胁模型和攻击面分析概述 <a href="#threat-model-and-attack-surface-analysis-overview" id="threat-model-and-attack-surface-analysis-overview"></a>

Bitwarden 遵循基于风险的方法来设计安全服务和系统，包括威胁建模和攻击面分析，以识别威胁并制定缓解措施。风险和威胁建模分析扩展到 Bitwarden 平台的所有领域，包括核心 Bitwarden 云服务器应用程序和 Bitwarden 客户端，如移动端、桌面端、Web 应用程序、浏览器和/或命令行界面。

#### Bitwarden 客户端 <a href="#bitwarden-clients" id="bitwarden-clients"></a>

用户主要通过我们的客户端应用程序与 Bitwarden 进行交互，如移动端、桌面端、Web 应用程序、浏览器和/或命令行界面。这些设备、工作站和网页浏览器的安全是至关重要的，因为如果这些设备中的一个或多个被入侵，攻击者可能会安装恶意软件，如键盘记录器，从而获取在这些设备上输入的所有信息，包括您的任何密码和机密。作为终端用户和/或设备所有者，您有责任确保您的设备安全，并防止非授权访问。

#### HTTPS TLS 和网页浏览器端到端加密 <a href="#https-tls-and-web-browser-crypto-end-to-end-encryption" id="https-tls-and-web-browser-crypto-end-to-end-encryption"></a>

Bitwarden 网页客户端运行在您的网页浏览器中。Bitwarden 网页客户端的真实性和完整性取决于传输客户端的 HTTPS TLS 连接的完整性。攻击者如果能够篡改传递给网页客户端的流量，就可以向用户提供一个恶意客户端。

网页浏览器攻击是攻击者和网络犯罪分子注入恶意软件或造成破坏的最流行方式之一。对网页浏览器的攻击载体可能包括：

* **社会工程元素，如网络钓鱼**：欺骗和说服受害者采用任何危害其用户机密和账户安全的行为
* **浏览器攻击和浏览器扩展/附加组件漏洞**：当用户在键盘上打字时，恶意扩展程序就会捕捉到用户的机密
* **通过浏览器对网页应用程序的攻击**：点击劫持、跨站点脚本（XSS）、跨站点请求伪造（CSRF）。

Bitwarden 使用 [HTTP 安全头文件](bitwarden-security-whitepaper.md#http-security-headers)作为 Bitwarden 网络应用和通信的额外保护层。

#### 代码评估 <a href="#code-assessments" id="code-assessments"></a>

Bitwarden 是一个开源的密码管理器。我们所有的源代码都托管在 [GitHub](https://github.com/bitwarden) 上，并提供给大家公开审查。Bitwarden 的源代码每年都由被著名的第三方安全审计公司以及独立的安全研究人员进行审计。此外，Bitwarden 漏洞披露计划还得到了 HackerOne 黑客社区的帮助，以使 Bitwarden 更加安全。

阅读更多：

* [Bitwarden 安全常见问题](../security/security-faqs.md)
* [Bitwarden 威胁预防和应对](bitwarden-security-whitepaper.md#threat-prevention-and-response)
* [Bitwarden 安全和合规性评估、审核、漏洞扫描、PenTesting](bitwarden-security-whitepaper.md#auditability-and-compliance)

## 总结 <a href="#conclusion" id="conclusion"></a>

提供此 Bitwarden 安全与合规计划概述，以供您参考。Bitwarden 的解决方案、软件、基础设施和安全流程都是以多层次、深入防御的方式从头设计的。

Bitwarden 的安全与合规计划基于 ISO27001 信息安全管理体系（ISMS）。我们定义了管理我们的安全政策和流程的政策，并不断更新我们的安全计划，以符合适用的法律、行业和监管要求，以便我们在我们的[服务条款协议](https://bitwarden.com/terms/)下向您提供服务。

如果您有任何疑问，请[联系我们](https://github.com/bitwarden/help/blob/master/\_articles/security/www.bitwarden.com/contact)。

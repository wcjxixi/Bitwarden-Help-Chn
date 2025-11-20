# 安全 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/security-faqs/)
{% endhint %}

本文包含有关安全的常见问题 (FAQ)。

### 问：为什么我应该在密码方面信任 Bitwarden？ <a href="#q-why-should-i-trust-bitwarden-with-my-passwords" id="q-why-should-i-trust-bitwarden-with-my-passwords"></a>

**答：**&#x60A8;可以出于以下这些原因信任我们：

1. Bitwarden 是一个**开源**软件。我们所有的源代码都托管在 [GitHub](https://github.com/bitwarden) 上，任何人都可以免费查看。成千上万的软件开发者都在关注 Bitwarden 的源代码项目（你也可以！）。
2. Bitwarden 由独立的安全研究人员以及**信誉良好的第三方安全公司进行**[**审计**](compliance-audits-and-certifications.md)。
3. Bitwarden **不存储您的密码**。Bitwarden 存储的是您的密码的加密版本，只有您才能解锁。您的敏感信息在被发送到我们的云服务器之前，会在您的个人设备上进行本地加密。
4. **Bitwarden 的声誉很好**。Bitwarden 被数百万个人和企业使用。如果我们做任何有问题或有风险的事情，我们就会被淘汰！

还是不相信我们吗？不必这样。开源是美丽的。您可以轻松地自己托管整个 Bitwarden 堆栈，您的数据由您自己掌控。在[这里](../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md)了解更多。

### 问：如果 Bitwarden 被黑会怎么样？ <a href="#q-what-happens-if-bitwarden-gets-hacked" id="q-what-happens-if-bitwarden-gets-hacked"></a>

**答：**&#x42;itwarden 采取极端措施确保其网站、应用程序和云服务器的安全。Bitwarden 使用 Microsoft Azure 托管服务来管理服务器基础设施和安全，而不是直接自己来做。

如果由于某些原因 Bitwarden 被黑客攻击，您的数据因此遭泄露，由于对您的密码库数据和主密码采取了[强大的加密和单向盐化哈希](encryption/encryption-protocols.md)措施，您的信息仍然受到保护。

### 问：Bitwarden 可以看到我的密码吗？ <a href="#q-can-bitwarden-see-my-passwords" id="q-can-bitwarden-see-my-passwords"></a>

**答：**&#x4E0D;能。

您的数据在离开您的本地设备之前就已经被完全加密和/或哈希，因此 Bitwarden 团队的任何人都无法看到、读取或进行逆向工程来获取您的真实数据。Bitwarden 服务器只存储已被加密和哈希的数据。有关您的数据如何被加密的更多信息，请参阅[加密](encryption/encryption-protocols.md)。

### 问：我的 Bitwarden 主密码是否存储在本地？ <a href="#q-is-my-bitwarden-master-password-stored-locally" id="q-is-my-bitwarden-master-password-stored-locally"></a>

**答：**&#x6CA1;有。

我们不会将主密码保存在本地或内存中。仅当 App 解锁后，您的加密密钥（从主密码派生而来）将会保存在内存中，这用于来解密您密码库中的数据。当密码库被锁定时，这些数据会从内存中清除。

我们还会在锁屏 10 秒后重新加载应用程序的渲染进程，以确保任何尚未被垃圾收集的托管内存地址也被清除。我们尽最大努力确保任何可能在内存中为应用程序运作的数据只在您需要的时间内保存在内存中，并且每当应用程序被锁定时，内存都会被清理。当应用程序处于锁定状态时，我们认为应用程序的加密数据是完全安全的。

### 问：如果有无法识别的新设备登录 Bitwarden 该怎么办？ <a href="#q-what-do-i-do-if-i-dont-recognize-a-new-device-logging-into-bitwarden" id="q-what-do-i-do-if-i-dont-recognize-a-new-device-logging-into-bitwarden"></a>

**答：**&#x5982;果新设备的 IP 地址与任何已知的 IP 地址（家庭网络、工作网络、移动网络等）不匹配，请更改您的主密码，并确保您的账户启用了两步登录。您还应该从网络密码库的**账户设置**页面取消会话授权，以强制在所有设备上注销。如果您认为您的密码库项目可能受到威胁，您应该更改您的密码。

### 问：Bitwarden 符合哪些合规？拥有哪些认证？ <a href="#q-what-is-bitwarden-compliant-with-what-certifications-do-you-have" id="q-what-is-bitwarden-compliant-with-what-certifications-do-you-have"></a>

**答：**&#x42;itwarden 符合以下政策：

* **GDPR**，在[这里](https://bitwarden.com/privacy)了解更多。
* **CCPA**，在[这里](https://bitwarden.com/compliance)了解更多。
* **HIPAA**，在[这里](https://bitwarden.com/blog/post/why-use-a-hippa-compliant-password-manager/)了解更多。
* **SOC 2 Type 2**，在[这里](https://bitwarden.com/blog/post/bitwarden-achieves-soc-2-certification/)了解更多。
* **SOC 3**，在[这里](https://bitwarden.com/blog/post/bitwarden-achieves-soc-2-certification/)了解更多。

有关更多信息，请访问我们的[安全与合规](https://bitwarden.com/compliance)页面。

### 问：Bitwarden 如何满足欧洲合规要求？ <a href="#q-how-does-bitwarden-meet-european-compliance-requirements" id="q-how-does-bitwarden-meet-european-compliance-requirements"></a>

**答：**&#x42;itwarden 符合 GDPR 标准，并使用经批准的信息传输机制，包括根据 2021 年 6 月 4 日欧盟委员会实施决定 (EU) 2021/914 批准的欧洲议会和理事会条例 (EU) 2016/679 制定的欧盟标准合同条款 (SCC)。目前载于 [https://eur-lex.europa.eu/eli/dec\_impl/2021/914/oj](https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj)。对于商业和企业客户，Bitwarden 可以执行 Bitwarden 数据保护协议。

Bitwarden 云服务器目前托管在美国和欧盟的 Microsoft Azure 上。如今，Bitwarden 通过这一基础设施为数百万用户提供服务，其中包括欧洲和世界各地的政府和企业客户。

对于需要完全控制数据驻留的客户，也可以将 Bitwarden 私有托管在您自己的基础设施上。

存储在 Bitwarden 中的所有密码库数据，无论是在云端还是自托管，都经过端到端加密，除 Bitwarden 用户外任何人都无法访问。通过这种端到端、零知识加密架构，即使 Bitwarden 也无法访问您的数据。

有关 Bitwarden 安全性和合规性认证的完整列表，请访问 [https://bitwarden.com/compliance/](https://bitwarden.com/compliance/)。

### 问：在我的 Biwatrden 账户中使用了哪些第三方服务、库和标识符？ <a href="#q-what-third-party-services-libraries-or-identifiers-are-used-in-my-bitwarden-account" id="q-what-third-party-services-libraries-or-identifiers-are-used-in-my-bitwarden-account"></a>

**答：**&#x5728;移动应用程序中，Firebase 云消息传递（经常被误认为是跟踪器）仅用于与[同步](../password-manager/your-vault/syncing-your-vault.md)相关的推送通知，并且绝对不执行任何跟踪功能。Microsoft Visual Studio App Center 用于在一系列移动设备上进行崩溃报告。在 Web Vault 中，Stripe 和 PayPal 脚本仅用于支付页面上的支付处理。

对于那些喜欢排除所有第 3 方通信的用户，Firebase 和 Microsoft Visual Studio App Center 已从 [F-Droid 构建](https://bitwarden.com/download/)中完全移除。此外，关闭自托管 Bitwarden 服务器上的推送通知将禁用推送中继服务器。

Bitwarden 非常重视用户的安全和隐私。Bitwarden 维护安全的端到端加密，对您的加密密钥零了解。作为一家专注于开源的公司，我们邀请任何人随时在 [GitHub](https://github.com/bitwarden) 上查看我们的库实现。

### 问：如何对我的 Bitwarden 组织要求两步登录？ <a href="#q-how-do-i-require-two-step-login-for-my-bitwarden-organization" id="q-how-do-i-require-two-step-login-for-my-bitwarden-organization"></a>

**答：**&#x4F7F;用企业组织订阅中的[企业策略](../admin-console/oversight-visibility/enterprise-policies.md)，可以实现强制 2FA 功能。您也可以为您的组织启用 Duo MFA 集成来实现强制 2FA/MFA。有关更多信息，请参阅  [Duo 方式的两步登录](../account/two-step-login/setup-two-step-login/two-step-login-via-duo.md)。

### 问：Bitwarden 的自托管实例的证书选项是什么？ <a href="#q-what-are-the-certificate-options-for-a-self-hosted-instance-of-bitwarden" id="q-what-are-the-certificate-options-for-a-self-hosted-instance-of-bitwarden"></a>

**答：**&#x6709;关完整列表以及说明，请参阅[证书选项](../self-hosting/deploy-and-configure/configuration-options/certificate-options.md)。

### 问：Bitwarden 如何审核代码的更改？ <a href="#q-how-does-bitwarden-vet-code-changes" id="q-how-does-bitwarden-vet-code-changes"></a>

**答：**&#x5BF9;我们系统的安全性有信心，这对 Bitwarden 来说是极度重要的。所有提交的代码更改在被合并到任何代码库之前，都会由团队中的一个或多个非作者成员进行审查。所有的代码在生产前都要经过多个测试和 QA 环境。Bitwarden 已经实施了 SOC2 报告来审计和验证我们的内部程序。正如报告中提到的，我们的团队要经过严格的背景调查和彻底的面试过程。Bitwarden 作为一个开源产品，也欢迎同行在任何时候对我们的代码进行审查。Bitwarden 团队将努力尽一切可能让我们的用户感到舒适，并保证他们的数据安全。

### 问：Bitwarden 缓存会话信息会保持多长时间？ <a href="#q-how-long-does-bitwarden-cache-session-information" id="q-how-long-does-bitwarden-cache-session-information"></a>

**答：**&#x597D;问题！答案取决于特定的信息和客户端应用程序：

*   离线密码库会话将在 30 天后过期。

    * 移动客户端应用程序**除外**，它将在 90 天后过期。


* [两步登录](../account/two-step-login/setup-two-step-login/two-step-login-methods.md)的**记住我**选项将在 30 天后过期。
* 目录连接器[同步缓存](../admin-console/manage-members/directory-connector/clear-sync-cache.md)将在 30 天后被清除。
* 组织邀请将在 5 天后过期。自托管客户可以[使用环境变量](../self-hosting/deploy-and-configure/configuration-options/environment-variables.md#optional-variables)对其进行配置。

### 问：如何验证 Bitwarden App 的校验和？ <a href="#q-how-do-i-validate-the-checksum-of-a-bitwarden-app" id="q-how-do-i-validate-the-checksum-of-a-bitwarden-app"></a>

**答：**&#x76EE;前可对 Password Manager 桌面 App、Android 移动 App 和 CLI 客户端进行校验和验证：

{% tabs %}
{% tab title="桌面端" %}
1、从 [https://github.com/bitwarden/clients/releases/](https://github.com/bitwarden/clients/releases/) 下载最新版本的桌面 App 软件包（例如 `Bitwarden-Installer-2024.8.2.exe`）。

2、从同一页面下载该版本的 `sha256-checksums.txt` 文件，然后用文本编辑器打开它。

3、使用 `CertUtil` 或 `sha256sum` 命令生成已下载的软件包的 SHA-256 哈希值，例如：

```
sha256sum Bitwarden-2024.8.2-universal.dmg
```

该命令将在控制台打印哈希值。

4、将打印的哈希值与已下载的软件包的 `sha256-checksums.txt` 中列出的值进行比较。
{% endtab %}

{% tab title="Android" %}
1、从 [https://github.com/bitwarden/android/releases/](https://github.com/bitwarden/android/releases/) 下载最新版本的 Android App 软件包（例如 `com.x8bit.bitwarden.apk`）。

2、从同一页面下载相应的 `{package}-sha256.txt` 文件，然后用文本编辑器打开它。

3、使用 `CertUtil` 或 `sha256sum` 命令生成已下载的软件包的 SHA-256 哈希值，例如：

```
sha256sum com.x8bit.bitwarden.apk
```

该命令将在控制台打印哈希值。

4、将打印的哈希值与已下载的软件包的 `{package}-sha256.txt` 中列出的值进行比较。
{% endtab %}

{% tab title="CLI" %}
1、从 [https://github.com/bitwarden/clients/releases/](https://github.com/bitwarden/clients/releases/) 下载最新版本的 CLI 软件包（例如 `bw-linux-2024.8.2.zip`）。

2、从同一页面下载相应的 SHA-256 `.txt` 文件，此例中为 `bw-linux-sha256-2024.8.2.txt`，然后用文本编辑器打开它。

3、使用 `CertUtil` 或 `sha256sum` 命令生成已下载的 `.zip` 文件的 SHA-256 哈希值，例如：

```
sha256sum bw-linux-2024.8.2.zip
```

该命令将在控制台打印哈希值。

4、将打印的哈希值与已下载的软件包的 `.txt` 文件中列出的值进行比较。
{% endtab %}
{% endtabs %}

### 问：如何向 Bitwarden 进行安全披露或报告？ <a href="#q-how-do-i-make-a-security-disclosure-or-report-to-bitwarden" id="q-how-do-i-make-a-security-disclosure-or-report-to-bitwarden"></a>

**答：**&#x42;itwarden 认为，与全球安全研究人员合作对于确保用户安全至关重要。如果您认为在我们的产品或服务中发现了安全问题，我们鼓励您通过我们的 [HackerOne 计划](https://hackerone.com/bitwarden/)提交报告。我们欢迎与您合作，尽快解决问题。[详细了解我们的披露政策](https://github.com/bitwarden/server/security/policy)。

### ~~问：为什么我的网络密码库会转到 web-vault.pages.dev？~~ <a href="#q-why-is-my-web-vault-going-to-web-vault.pages.dev" id="q-why-is-my-web-vault-going-to-web-vault.pages.dev"></a>

~~**答：**`web-vault.pages.dev` 是 Bitwarden 独有的子域名，由 Cloudflare Pages 使用。当 Cloudflare 遇到 DNS 问题时，此 URL 可能会向用户显示。在输入用户名和主密码之前，您应该通过检查 URL 来始终警惕网络钓鱼尝试，但 `web-vault.pages.dev` 应被视为可以安全登录。~~

### 问：如何保护我的 Bitwarden 账户免受暴力攻击？ <a href="#q-how-can-i-protect-my-bitwarden-account-from-brute-force-attacks" id="q-how-can-i-protect-my-bitwarden-account-from-brute-force-attacks"></a>

**答：**&#x66B4;力攻击是指恶意行为者循环使用弱密码和短密码的组合来尝试访问您的账户。Bitwarden 提供了几种保护自己免受这些潜在攻击的方法：

* 拥有一个长且唯一的主密码。Bitwarden 要求至少 12 个字符以提高账户安全性。
* 在所有 Bitwarden 账户上设置 [2FA](../account/two-step-login/field-guide-for-two-step-login.md) 以添加额外的安全层。
* 在未知设备尝试登录 9 次失败后，Bitwarden 将要求 CAPTCHA 验证。

## 关于特定客户端 App 的问题 <a href="#questions-regarding-specific-client-apps" id="questions-regarding-specific-client-apps"></a>

### 问：Bitwarden 使用客户端应用程序的哪些数据？

**答：**&#x42;itwarden 使用管理数据为您提供 Bitwarden 服务。如某些**App 隐私**报告所示，用户在创建账户时提供以下信息：

* 您的名称（可选）
* 您的电子邮件地址（用于电子邮箱验证、账户管理以及您与 Bitwarden 之间的交流沟通）

此外，**Bitwarden 生成的**特定于设备的 GUID（有时称为**设备 ID**）将分配给您的设备。当新设备登录到您的密码库时，此 GUID 用于提醒您。

### 问：可以解释一下电子应用程序安全吗？ <a href="#q-can-you-explain-electron-app-security" id="q-can-you-explain-electron-app-security"></a>

**答：**&#x4E00;篇经常被分享的文章表明，电子应用程序存在缺陷，然而所提到的攻击需要用户拥有一台已被入侵的机器，这当然会让恶意攻击者入侵该机器上的数据。只要您没有理由相信您所使用的设备已经被入侵，您的数据就是安全的。

### 问：Bitwarden 如何保护浏览器扩展？ <a href="#q-how-does-bitwarden-secure-browser-extensions" id="q-how-does-bitwarden-secure-browser-extensions"></a>

**答：**&#x5982;果开发得当，扩展程序是可以安全使用的。由于浏览器扩展的工作原理，总是可能会出现错误。我们在开发我们的扩展程序和附加组件时，会非常小心谨慎。我们会密切关注行业内发生的任何事情，并对所有事物进行更多的安全审计。

### 问：浏览器扩展要求哪些权限？ <a href="#q-what-is-the-browser-extension-asking-permission-for" id="q-what-is-the-browser-extension-asking-permission-for"></a>

**答：**&#x5B89;装时，浏览器扩展会请求访问剪贴板，以便使用计划的剪贴板清除功能（在**选项**菜单中访问）。

启用该**可选功能**后，剪贴板清除功能将在可配置的时间间隔内清除任何由 Bitwarden 创建或填充的条目。访问剪贴板，Bitwarden 将能够通过检查最后复制的项目与您密码库中最后复制的项目是否匹配，从而在不移除与 Bitwarden 应用程序无关的剪贴板项目的情况下执行此操作。请注意，该功能**默认是关闭**的。

### 问：移动 App 要求哪些 App 权限？ <a href="#q-what-app-permissions-are-asked-for-by-the-mobile-app" id="q-what-app-permissions-are-asked-for-by-the-mobile-app"></a>

**答：**&#x5F53;您使用这些 App 时，Bitwarden Android 和 iOS App 可能会要求以下权限：

| 权限                          | 理由                                     |
| --------------------------- | -------------------------------------- |
| 允许 Bitwarden 拍照和录制视频吗？      | 用于两步登录或 Bitwarden Authenticator 扫描二维码。 |
| 允许 Bitwarden 访问您设备上的照片和媒体吗？ | 用于从设备上保存的文件创建附件或 Send。                 |

Bitwarden 所需的其他基本权限已[在 Google Play 商店中列出](https://play.google.com/store/apps/details?id=com.x8bit.bitwarden)。

### 问：为何浏览器扩展需要 `nativeMessaging` 权限？ <a href="#q-why-does-the-browser-extension-need-nativemessaging-permission" id="q-why-does-the-browser-extension-need-nativemessaging-permission"></a>

**答：**&#x31;.48.0 版本的浏览器扩展启用了[浏览扩展的生物识别解锁](../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md#browser-extensions)。

此权限，也就是 `nativeMessaging`，可以安全地接受它，它允许浏览器扩展与 Bitwarden 桌面 App 进行通信，这是启用生物识别解锁所必需的。

请注意，当您的浏览器更新到此版本时，您可能会被要求接受一个名为「与本机应用程序通信」（在基于 Chromium 的浏览器中）或 「与 Firefox 以外的程序交换消息」的新权限。如果您不接受此权限，该扩展将保持禁用状态。

### 问：Bitwarden 是否符合 FIPS 标准？ <a href="#q-is-bitwarden-fips-compliant" id="q-is-bitwarden-fips-compliant"></a>

**答：**&#x42;itwarden 使用[符合 FIPS 标准的库和密码学](encryption/encryption-protocols.md#invoked-crypto-libraries)，但是 Bitwarden 平台没有进行任何 FIPS 认证。Bitwarden 的大多数 FIPS 安装利用自托管选项，使评估（即网络安全成熟度模型认证）更容易。

### 问：我可以限制某些设备对 Bitwarden 的访问吗？ <a href="#q-can-i-restrict-access-to-bitwarden-to-certain-devices" id="q-can-i-restrict-access-to-bitwarden-to-certain-devices"></a>

**答：**&#x4F7F;用自助托管，您可以使用自定义防火墙和 NGINX 配置以及 VPN/VLAN 访问控制来确定访问 Bitwarden 实例的设备类型和/或网络层。您也可以使用其他工具，比如设备级证书来控制特定设备对 Bitwarden 实例的访问。

### 问：Bitwarden 有便携版应用程序吗？ <a href="#q-does-bitwarden-have-a-portable-application" id="q-does-bitwarden-have-a-portable-application"></a>

**答：**&#x6709;的！ Bitwarden 桌面 App 在 Windws 中有提供便携版 `.exe`，其可在[此处](https://bitwarden.com/download)下载。便携版 App 非常适合**始终离线**的环境或不需要 App 自动更新的场景。便携版 App **不会自行更新**。

### 问：网站访问选项会干扰 Bitwarden 浏览器扩展吗？ <a href="#q-will-site-access-options-interfere-with-the-bitwarden-browser-extension" id="q-will-site-access-options-interfere-with-the-bitwarden-browser-extension"></a>

**答：**&#x4E3A;了使 Bitwarden 浏览器扩展正常工作，必须将其网站访问权限设置为**在所有网站上**或**在特定网站上**并将 Bitwarden 服务器添加到列表中。将网站访问权限设置为**点击时**会限制 Bitwarden 从 Bitwarden 服务器获取数据的能力，而这正是保存或更新凭据所必需的基本功能。

### 问：Bitwarden 采取哪些措施来维护本地客户端安全？ <a href="#q-what-steps-does-bitwarden-take-to-maintain-local-client-security" id="q-what-steps-does-bitwarden-take-to-maintain-local-client-security"></a>

**答：**&#x6240;有 Bitwarden 客户端（桌面、网页、移动、浏览器扩展）都会在从 Bitwarden 服务器检索敏感数据时对其进行加密。在 Bitwarden 安全白皮书上了解有关 Bitwarden [身份验证和解密](bitwarden-security-whitepaper.md#authentication-and-decryption)的更多信息。

为了防止中间人 (MitM) 攻击和加密数据操纵，Bitwarden 确保客户端和服务器之间的所有通信均通过采用 TLS 加密的 HTTPS 进行。此外，加密的密码库数据（密码库「blob」）是使用字符串加密算法（PBKDF2 和 Argon2）在客户端本地解密的，这意味着对加密 blob 的任何篡改都可能导致解密失败或数据不可用，从而有助于防止未经授权的操作被悄悄接受。

因此，最终用户或设备所有者有责任确保其设备的安全并防止未经授权的访问。Bitwarden 承认某些用户可能在越狱或取得 root 权限的设备上进行操作。此类环境不受支持，Bitwarden 无法保证安全性和内存管理保护。

### 问：Bitwarden 是否可以在模拟环境中运行？ <a href="#q-does-bitwarden-run-in-emulated-environments" id="q-does-bitwarden-run-in-emulated-environments"></a>

**答：**&#x662F;的，用户可以在模拟环境中运行 Bitwarden。Bitwarden 的开发过程本身涉及各种操作系统的仿真器和模拟器的使用。由于 Bitwarden 是开源的，因此开发人员可以完全访问代码库，并能够在模拟环境中构建、运行和调试应用程序。这种透明度和灵活性支持广泛的用例，从受控环境中的测试到为项目本身做出贡献。

### 问：第三方网站可以知道我安装了 Bitwarden 吗？ <a href="#q-can-third-party-sites-know-that-i-have-bitwarden-installed" id="q-can-third-party-sites-know-that-i-have-bitwarden-installed"></a>

**答：**&#x867D;然 Bitwarden 确实采用了多种技术来帮助防止浏览器指纹识别，但不可能完全阻止对浏览器扩展程序使用的检测。对指纹识别敏感的用户可以选择不使用浏览器扩展，而选择桌面 App。

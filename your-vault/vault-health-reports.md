# 密码库健康报告

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/reports/)
{% endhint %}

密码库健康报告可用于评估 Bitwarden 个人或组织密码库的安全性。重复使用密码和弱密码报告等报告可在客户端本地运行。这样就可以在 Bitwarden 无法访问未加密版本数据的情况下识别出违规项目。

{% hint style="info" %}
大部分密码库健康报告功能适用于高级用户，包括付费组织（家庭、团队或企业）的成员。但[数据泄露报告](vault-health-reports.md#data-breach-report-individual-vaults-only)对所有用户都是免费的。
{% endhint %}

## 查看报告 <a href="#view-a-report" id="view-a-report"></a>

完成以下步骤以查看您的**个人密码库**的任何密码库健康报告：

1、登录到网页 App 然后从导航栏选择**报告：**

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/JcoKvP7eLrZHUEKmjTqgc/0213680bf5546cfc7df498d9931c8d2f/2024-12-02_16-29-59.png?_a=DAJCwlWIZAAB" %}
报告页面
{% endembed %}

2、选择要运行的报告。

要查看您的**组织密码库**的任何密码库健康报告：

1、登录到 Bitwarden 网页 App。

2、使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

3、在您的组织中，从导航栏选择**报告** → **报告**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5POQmt3TrEgfFzRNwHancg/9a67882a07d8894747ebb5bc3bbdcaae/2024-12-02_16-31-14.png?_a=DAJCwlWIZAAB" %}
组织报告
{% endembed %}

4、选择要运行的报告。

## 可用的报告 <a href="#available-reports" id="available-reports"></a>

### 泄露密码报告 <a href="#exposed-passwords-report" id="exposed-passwords-report"></a>

泄露密码报告可以识别被黑客公开发布或在暗网上出售的已知数据泄露事件中暴露的密码。

该报告使用受信任的网络服务在已知泄露密码的数据库中检索您所有密码哈希值的前 5 位，然后，将返回的匹配的散列列表与您的密码的完整散列列表进行本地比较。这种比较只在本地进行，以保护你的 [k-匿名性](https://en.wikipedia.org/wiki/K-anonymity)。

被识别后，您应该为违规账户或服务创建一个新的密码。

{% hint style="success" %}
**为什么使用密码哈希值的前 5 位？**

如果此报告使用您的实际密码来执行，那这些密码是否暴露并不重要了，因为您主动将其泄露给此服务了。并且这个报告的结果并不意味着您的个人账户已被泄露，只是您使用的密码已经在这些暴露的密码数据库中被发现，您应该避免使用泄露的密码和非唯一的密码。
{% endhint %}

### 重复使用的密码报告 <a href="#reused-passwords-report" id="reused-passwords-report"></a>

重复使用的密码报告可以识别密码库中的非唯一密码。如果在多个服务中重复使用相同的密码，当一个服务被攻破时，会让黑客轻松获取您的更多在线账户的访问权限。

确定后，您应该为违规账户或服务创建一个唯一的密码。

### 弱密码报告 <a href="#weak-passwords-report" id="weak-passwords-report"></a>

弱密码报告可以识别出容易被黑客和用于破解密码的自动化工具猜中的弱密码，并按弱点的严重性进行排序。Bitwarden 密码生成器可以帮助您创建更强大的密码。该报告使用 [zxcvbn](https://dropbox.tech/security/zxcvbn-realistic-password-strength-estimation) 进行密码强度分析。

被识别后，您应该使用 Bitwarden 密码生成器为违规账户或服务创建一个强密码。

### 不安全网站报告 <a href="#unsecured-websites-report" id="unsecured-websites-report"></a>

不安全网站报告可以识别在 URI 中使用不安全 (`http://`) 方案的登录项目。使用 `https://` 的 TLS/SSL 加密通信要安全得多。要了解更多信息，请参阅 [URI 的使用](../password-manager/autofill/troubleshoot-autofill/forming-uris-for-autofill.md)。

被识别后，您应该将违规的 URI 由 `http://` 更改为 `https://`。

### 未激活 2FA 报告 <a href="#inactive-2-fa-report" id="inactive-2-fa-report"></a>

未激活 2FA 报告可以识别如下的登录项目：

* 该服务提供了通过 TOTP 的双重验证 (2FA)
* 您尚未存储 TOTP 验证证器密钥

双重验证 (2FA) 是保护您帐户安全的一个重要安全设置。如果网站提供，您应该始终启用双重验证。通过将 URI 数据与来自 [https://2fa.directory/](https://2fa.directory/) 的数据进行交叉引用，可以识别出违规项目。

被识别后，使用 `Instructions` （说明） 超链接来为每个违规项目设置 2FA。

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3USpBf7beuGcdJvMhDrwNI/570672e3220f09e0398ced33a154b1ea/inactive-2fa.png?_a=DAJAUVWIZAAB" alt=""><figcaption><p>报告说明</p></figcaption></figure>

### 成员访问权限 <a href="#member-access" id="member-access"></a>

企业组织可以使用成员访问权限报告来查看组织成员有权访问的**群组**、**集合**和**项目**的列表。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4oNfzpIcDwn2XjUgG0lPG3/a51bac815082055fdd6f47a40937b72d/2024-09-10_16-13-31.png?_a=DAJAUVWIZAAB" %}
成员访问权限报告
{% endembed %}

使用成员访问权限报告，您可以：

* 查看每个用户有权访问的群组、集合和项目的总数。
* 使用搜索成员在成员访问页面上搜索单个成员。
* 使用**导出**→ 按钮创建 CSV 导出。CSV 导出包含了每个成员的**群组**和**集合访问权限**的详细列表，以及**集合权限**、**两步登录**和**账户恢复**状态。

### 数据泄露报告（仅个人密码库） <a href="#data-breach-report-individual-vaults-only" id="data-breach-report-individual-vaults-only"></a>

数据泄露报告使用一项名为 Have I Been Pwned (HIBP) 的服务来识别已知事件中的泄露数据（电子邮箱地址、密码、信用卡、DoB 等）。

> **\[译者注]**：DoB：Date of Birth（出生日期）

当您创建一个 Bitwarden 账户时，您可以选择在您决定使用主密码之前运行此报告。要运行此报告，您的主密码的哈希值将发送到 HIBP，并与存储的已暴露哈希值进行比较。Bitwarden 永远不会泄露您的主密码。

HIBP 将「泄漏」定义为「通常是由于访问控制不足或软件的安全弱点造成数据在脆弱的系统中无意中暴露的事件」。更多信息，请参阅 [HIBP 常见问题文档](https://haveibeenpwned.com/FAQs)。

{% hint style="info" %}
如果您是自托管 Bitwarden，想要在您的实例中运行数据泄露报告，您需要购买 HIBP 订阅密钥，该密钥将授权您对 API 进行调用。可以[在此处](https://haveibeenpwned.com/API/Key)购买此密钥。

拥有此密钥后，打开 `./bwdata/env/global.override.env` 并将 `globalSetting__hibpApiKey=` 的占位符值替换为您购买的 API 密钥：

```
globalSettings__hibpApiKey=REPLACE
```

更多信息，请参阅[配置环境变量](../self-hosting/deploy-and-configure/configuration-options/environment-variables.md)。
{% endhint %}

# 加密密钥轮换

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/account-encryption-key/)
{% endhint %}

每个 Bitwarden 账户都有一个用于加密所有密码库数据的加密密钥。

{% hint style="danger" %}
**轮换加密密钥是潜在的危险操作。**&#x8BF7;通读本章节，以了解这样做的全部后果。
{% endhint %}

轮换账户的加密密钥会生成一个新的加密密钥，用于重新加密所有密码库数据。如果您的账户已被盗用，并且有人获得了您的加密密钥，则您应该考虑轮换您的加密密钥。

## 轮换之前 <a href="#before-rotating" id="before-rotating"></a>

在轮换之前，您应该采取以下措施以防止数据丢失或损坏：

### 重新创建账户的加密导出 <a href="#re-create-any-account-backup-exports" id="re-create-any-account-backup-exports"></a>

如果您使用[加密导出](../../password-manager/import-and-export/encrypted-exports.md)来存储长期的安全备份，您应该立即使用新的加密密钥重新创建密码库数据的加密导出。

加密导出使用您的加密密钥来加密**以及解密**您的密码库数据，这意味着，经过轮换的加密密钥将无法解密使用「陈旧」（轮换前）的密钥创建的导出。

### 注销客户端应用程序 <a href="#log-out-of-client-applications" id="log-out-of-client-applications"></a>

轮换加密密钥后，我们建议您注销 Bitwarden 客户端应用程序（桌面 App、浏览器扩展、移动 App 等）上的任何已登录会话。以这种方式注销客户端 App 将关闭使用「陈旧」（轮换前）加密密钥的会话。然后，像往常一样重新登录将使用新的加密密钥。

**在使用「陈旧」加密密钥的会话中进行更改将导致数据损坏，从而使您的数据无法恢复。**

## 如何轮换加密密钥 <a href="#how-to-rotate-your-encryption-key" id="how-to-rotate-your-encryption-key"></a>

{% hint style="danger" %}
Bitwarden 建议在轮换账户加密密钥前备份您的项目。在此场景下，推荐使用密码保护的 `.json` 导出格式，但**除账户限制**的 `.json` 导出格式外，任何格式在密钥轮换后均可重新导入。有关密码库导出以及包含哪些项目的更多信息，请参阅[导出密码库数据](../../password-manager/import-and-export/export-vault-data.md)。
{% endhint %}

要轮换您账户的加密密钥：

1、在网页 App 中，导航到**设置** → **安全** → **主密码**：

{% embed url="https://bitwarden.com/assets/2Svv0PwlH9i7SSK73dlv9A/e451afb190346e492110a7bf1bd3a518/Master_password_settings.png?w=1200&fm=avif" %}
主密码设置
{% endembed %}

2、输入您的**当前主密码**然后创建/确认**新主密码**。

3、勾选**同时轮换账户的加密密钥**复选框并接受弹出的对话框。

4、选择**更改主密码**按钮。

> **\[译者注]**：更改您的主密码或更改加密密钥设置 (KDF) 时，均不会主动轮换账户的加密密钥。仅在更改您的主密码时勾选**同时轮换账户的加密密钥**才会更改您账户的加密密钥。

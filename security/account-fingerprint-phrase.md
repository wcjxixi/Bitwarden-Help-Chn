# 账户指纹短语

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/fingerprint-phrase/)
{% endhint %}

每个 Bitwarden 用户帐户都有一个与之关联的公共「指纹短语」。您帐户的指纹短语永远不会改变，它由五个以特定顺序出现的随机英语单词组成。**指纹短语示例：**

```
alligator-transfer-laziness-macaroni-blue
```

## 我的指纹短语是用来做什么的？ <a href="#what-is-my-fingerprint-phrase-used-for" id="what-is-my-fingerprint-phrase-used-for"></a>

指纹短语是一项重要的安全功能，当执行与加密相关的重要操作（例如共享）时，有助于唯一且安全地标识 Bitwarden 用户帐户。

某些 Bitwarden 过程（例如，将新用户添加到组织，启用浏览器扩展的生物识别解锁）可能会要求您验证指纹短语是否与您自己或其他用户的指纹短语相匹配。

验证指纹短语可确保安全初始端到端加密，并确保与您通信（和连接）的 Bitwarden 服务器未被恶意篡改。

## 在哪里可以找到我的指纹短语？ <a href="#where-can-i-find-my-fingerprint-phrase" id="where-can-i-find-my-fingerprint-phrase"></a>

您可以在 Bitwarden 应用程序的以下位置找到帐户的指纹短语：

* **网页密码库**：设置 → 我的帐户
* **桌面应用程序**：帐户 → 指纹短语
* **浏览器扩展**：设置 → 帐户 → 指纹短语
* **移动应用程序**：设置 → 帐户 → 指纹短语
* **CLI**：`bw get fingerprint me`

## 我需要写下我的指纹短语吗？ <a href="#do-i-need-to-write-down-my-fingerprint-phrase" id="do-i-need-to-write-down-my-fingerprint-phrase"></a>

不知道您的指纹短语永远不会导致您被锁定在您的密码库之外。因此，将指纹短语记下并将其存储在安全的地方并不重要，但有些用户可能会选择这样做。

{% hint style="success" %}
另一方面，[恢复代码](../two-step-login/recovery-codes.md)用于两步登录，应**始终**以对您有意义的方式存储在 Bitwarden 之外。在您[丢失了两步登录辅助设备](../two-step-login/lost-secondary-device.md)时，这将确保您不会被锁定在您的帐户之外。
{% endhint %}

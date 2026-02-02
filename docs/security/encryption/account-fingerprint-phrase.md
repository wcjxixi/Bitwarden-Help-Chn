# 账户指纹短语

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/fingerprint-phrase/)
{% endhint %}

{% hint style="success" %}
您是否希望使用指纹阅读器解锁您的密码库？如果是这样，请参阅[生物识别](../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md)。
{% endhint %}

每个 Bitwarden 用户账户都有一个与之关联的「指纹短语」。您账户的指纹短语永远不会改变，它由五个以特定顺序出现的随机英语单词组成。例如：`alligator-transfer-laziness-macaroni-blue`&#x20;

指纹短语是一个重要的安全功能，用于在加密相关流程（例如共享凭据）期间确认 Bitwarden 用户的身份。验证指纹短语可确保安全初始端到端加密，并确保与您通信的 Bitwarden 服务器未被恶意篡改。

## 我的指纹短语是用来做什么的？ <a href="#what-is-my-fingerprint-phrase-used-for" id="what-is-my-fingerprint-phrase-used-for"></a>

某些 Bitwarden 流程（例如，将新用户添加到组织，或确认[设备登录请求](../../account/log-in-and-unlock/more-log-in-options/log-in-with-device.md)），会要求您验证指纹短语是否与您本人或其他用户的指纹短语相匹配。当操作过程中出现指纹短语时，请使用辅助通信方式（例如电话或短信）与 Bitwarden 用户联系。

## 在哪里可以找到我的指纹短语？ <a href="#where-can-i-find-my-fingerprint-phrase" id="where-can-i-find-my-fingerprint-phrase"></a>

您可以在 Bitwarden 客户端应用程序的以下位置找到您的账户指纹短语：

* **网页 App**：设置 → 我的账户
* **桌面 App**：账户 → 指纹短语
* **浏览器扩展**：设置 → 账户安全 → 指纹短语
* **移动 App**：设置 → 账户安全 → 账户指纹短语
* **CLI**：使用命令 `bw get fingerprint me`

## 我需要写下我的指纹短语吗？ <a href="#do-i-need-to-write-down-my-fingerprint-phrase" id="do-i-need-to-write-down-my-fingerprint-phrase"></a>

不知道您的指纹短语永远不会导致您被锁定在您的密码库之外。因此，将指纹短语记下并将其存储在安全的地方并不重要，但有些用户可能会选择这样做。

{% hint style="success" %}
另一方面，[恢复代码](../../account/two-step-login/recovery-codes.md)用于两步登录，应**始终**以对您有意义的方式存储在 Bitwarden 之外。在您[丢失了两步登录辅助设备](../../account/two-step-login/lost-two-step-device.md)时，这将确保您不会被锁定在您的账户之外。
{% endhint %}

## 我可以更改我的指纹短语吗？ <a href="#can-i-change-my-fingerprint-phrase" id="can-i-change-my-fingerprint-phrase"></a>

虽然您无法更改当前账户的指纹短语，但您可以通过[删除账户](../../plans-and-pricing/delete-an-account-or-organization.md)然后创建一个新账户的方式来生成一个新的短语。

我们的指纹短语源自[电子前哨基金会 (EFF) 的长单词列表](https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases)，该列表已经过「人工检查，并尽可能删除了亵渎、侮辱、敏感或带有煽动色彩的单词」。

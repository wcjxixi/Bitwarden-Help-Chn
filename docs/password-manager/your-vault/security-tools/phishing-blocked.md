# 钓鱼拦截器

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/phishing-blocked/)
{% endhint %}

Bitwarden 钓鱼拦截器检测已知的钓鱼网站，并将用户重定向到安全的通知页面，帮助确保凭据不会被误录或被泄露。钓鱼拦截器使用定期更新的开源的 [Phishing.Database](https://github.com/Phishing-Database/Phishing.Database) 来识别网络钓鱼网站。

钓鱼拦截器适用于 `2026.1.0` 及更新版本的浏览器客户端上的 Bitwarden 个人高级版和家庭版方案。

{% hint style="info" %}
目前，钓鱼拦截器不适用于 Bitwarden Safari 浏览器扩展。
{% endhint %}

## 钓鱼拦截器 <a href="#phishing-blocker" id="phishing-blocker"></a>

钓鱼拦截器通过浏览器扩展程序运行。当钓鱼拦截器识别出已知的钓鱼网站时：

1、Bitwarden 不会加载已知的钓鱼网站，而是会将用户重定向到一个警告页面，提示该网站已被拦截。

<figure><img src="https://bitwarden.com/assets/7IDSIId3ZA7nRT1T8gdX1T/3382ba87ffa5a38d8fa68b03d4ea0dcc/Phiishing-blocker-cropped.png?w=542&#x26;fm=jpg" alt="钓鱼拦截器"><figcaption></figcaption></figure>

2、选择合适的选项：

* **关闭标签页**：选择此选项将关闭 Bitwarden 已拦截的恶意标签页。
* **继续**：选择此选项将允许您继续访问该网站并关闭 Bitwarden 钓鱼拦截器。

{% hint style="info" %}
选择**继续**将访问之前被识别为存在钓鱼活动的网站。此操作可能会导致您的凭据泄露。建议谨慎选择此选项。
{% endhint %}

## 切换钓鱼拦截器 <a href="#toggle-phishing-blocker" id="toggle-phishing-blocker"></a>

默认情况下，个人高级版用户和家庭版用户将启用网络钓鱼拦截器。您可以在浏览器扩展中通过依次点击**设置** → **账户安全**然后选择开关来**打开**或**关闭**此功能：

<figure><img src="https://bitwarden.com/assets/4jeEBHYQeUpsZNOoKKUeW1/d19fe64cfed2edba32983f45c5434490/phishing_setting.png?w=750&#x26;fm=jpg" alt="切换钓鱼拦截器"><figcaption><p>切换钓鱼拦截器</p></figcaption></figure>

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

Bitwarden 钓鱼拦截器使用 Phishing.Database 来引用已知的钓鱼网站。这个开源工具由用户每日更新，用于识别有害的 URL。

{% hint style="info" %}
所有网站检查均由 Bitwarden 浏览器扩展在本地执行。任何数据都不会与 Bitwarden 或第三方共享。
{% endhint %}

1. Bitwarden 浏览器扩展直接从 Phishing.Database 获取列表。
2. Bitwarden API 使用 SHA-256 校验和来识别列表的更改并获取更新后的列表。
3. 使用浏览器扩展，Bitwarden 会在页面加载时将 URL 与钓鱼列表进行比对。
4. 如果网站与钓鱼数据库中的已知威胁匹配，Bitwarden 会将您带到拦截界面，并提供离开网站或继续的选项。

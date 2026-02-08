# 钓鱼拦截器

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/phishing-blocked/)
{% endhint %}

Bitwarden 钓鱼拦截器检测已知钓鱼网站，并将用户重定向到安全的通知页面，帮助确保凭证不会被误录或被泄露。钓鱼拦截器利用定期更新的开源工具识别钓鱼网站 [Phishing.Database](https://github.com/Phishing-Database/Phishing.Database)。

钓鱼拦截工具适用于 Bitwarden 个人高级和家庭套餐，浏览器客户端及更新版本。`2026.1.0`

{% hint style="info" %}
目前，Safari的Bitwarden浏览器扩展中尚无钓鱼拦截工具。
{% endhint %}

## 钓鱼拦截器 <a href="#phishing-blocker" id="phishing-blocker"></a>

钓鱼拦截器是通过浏览器扩展来工作的。当钓鱼拦截器识别出已知的钓鱼网站时：

1、Bitwarden不会加载已知的钓鱼网站，而是将用户重定向到警告页面，提示该网站已被封锁。

<figure><img src="https://bitwarden.com/assets/7IDSIId3ZA7nRT1T8gdX1T/3382ba87ffa5a38d8fa68b03d4ea0dcc/Phiishing-blocker-cropped.png?w=542&#x26;fm=jpg" alt="钓鱼拦截器"><figcaption></figcaption></figure>

2、选择合适的选项：

* **关闭标签**页：选择此选项将关闭 Bitwarden 封锁的恶意标签页。
* **继续**：选择此选项后，您可以继续访问网站并关闭Bitwarden钓鱼拦截器。

{% hint style="info" %}
选&#x62E9;**“继续”**&#x5C06;进入之前被识别为钓鱼活动的网站。此举可能导致您的资质被泄露。选择此选项时请注意。
{% endhint %}

## 切换钓鱼拦截器 <a href="#toggle-phishing-blocker" id="toggle-phishing-blocker"></a>

默认情况下，钓鱼拦截器将对个人高级用户和家庭用户开放。您可以通过浏览器扩展中**打开或关闭**该功能，方法是进入**账户安全**设置→选择以下开关：

<figure><img src="https://bitwarden.com/assets/4jeEBHYQeUpsZNOoKKUeW1/d19fe64cfed2edba32983f45c5434490/phishing_setting.png?w=750&#x26;fm=jpg" alt="切换钓鱼拦截器"><figcaption><p>切换钓鱼拦截器</p></figcaption></figure>

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

Bitwarden 钓鱼拦截器使用 Phishing.Database 来引用已知的钓鱼网站。该开源工具每日由用户更新以识别有害URL。

{% hint style="info" %}
所有网站检查均由 Bitwarden 浏览器扩展进行本地作。任何数据都不会与Bitwarden或第三方共享。
{% endhint %}

1. Bitwarden 浏览器扩展直接从 Phishing.Database 获取该列表。
2. Bitwarden API 使用 SHA-256 校验和来识别列表变更并获取更新后的列表。
3. 使用浏览器扩展后，Bitwarden 会在页面加载时将 URL 与钓鱼列表进行核对。
4. 如果该网站与钓鱼数据库中的已知威胁匹配，Bitwarden会带你进入被屏蔽的界面，提供离开网站或继续的选项。

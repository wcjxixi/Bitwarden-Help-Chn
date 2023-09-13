# 关于

> 20230827：由于官方帮助中心改动频繁，以及个人能力+精力有限，部分细节可能不会随官方保持更新！

***

这里是对 Bitwarden 官方 [Bitwarden Help Center](https://bitwarden.com/help/) 的中文翻译，并参考了 Github 上的 [Bitwarden Help](https://github.com/bitwarden/help) 项目（已停止更新）。

在便于理解的基础上，文字内容尽量将其中文化，同时也包括部分图片内容。

译者：[@wcjxixi](mailto:wcjxixi@gmail.com)

致谢 [Google Translate](https://translate.google.com/) 以及 [DeepL](https://www.deepl.com/) ！

{% hint style="danger" %}
个人能力有限，具体请以 [Bitwarden](https://bitwarden.com/) 官方页面为准。使用本内容所产生的一切后果，与 @wcjxixi 无关。Use at your own risk！！！
{% endhint %}

{% hint style="info" %}
**备注：**标题前有 **\*** 的表示在 Github 上的 [Bitwarden 官方帮助中心项目](https://github.com/bitwarden/help)里有，但在官方 [Bitwarden Help Center](https://bitwarden.com/help/) 里被移除或未显示的页面和/或分类，我将其保留仅作为参考之用。
{% endhint %}

## Bitwarden 介绍 <a href="#about-bitwarden" id="about-bitwarden"></a>

Bitwarden 是一个开源的密码管理系统，你可以使用 Bitwarden 官方提供的云服务，也可以将 Bitwarden 安装和托管在自己的服务器上。

个人账户的免费版不限制使用时间、不限制密码条目数、不限制设备数量、不限制文件夹数量、支持常见的验证器应用程序（如 [Authy](https://authy.com/)、 [Microsoft Authenticator](https://www.microsoft.com/en-us/account/authenticator)、[Google Authenticator](https://github.com/google/google-authenticator)），完全可以满足大部分个人的日常使用。

需要使用更高级功能（TOTP、文件附件等），可以选择个人账户的高级版，或者使用组织账户。

## 个人账户比较 <a href="#compare-individual-plans" id="compare-individual-plans"></a>

<table><thead><tr><th width="211.77867335127684">功能</th><th width="164.19100031205608">免费版</th><th>高级版</th></tr></thead><tbody><tr><td>价格（/年）</td><td>免费</td><td>$10.00</td></tr><tr><td>安装所有平台程序</td><td>支持</td><td>支持</td></tr><tr><td>无限制同步所有设备</td><td>支持</td><td>支持</td></tr><tr><td>项目条数</td><td>无限制</td><td>无限制</td></tr><tr><td>文件夹数量</td><td>无限制</td><td>无限制</td></tr><tr><td>密码生成器</td><td>支持</td><td>支持</td></tr><tr><td>存储空间</td><td>无</td><td>1GB</td></tr><tr><td>附加存储（GB/年）</td><td>不支持</td><td>$4.00</td></tr><tr><td>两步登录类型</td><td>验证器应用+电子邮件</td><td>免费版+YubiKey+Duo+FIDO U2F</td></tr><tr><td>内置 TOTP 功能</td><td>不支持</td><td>支持</td></tr><tr><td>Bitwarden Send</td><td>文本</td><td>文本+文件</td></tr><tr><td>紧急访问</td><td>不支持</td><td>支持</td></tr><tr><td>数据泄漏报告</td><td>支持</td><td>支持</td></tr><tr><td>健康报告</td><td>不支持</td><td>支持</td></tr><tr><td>本地托管</td><td>支持</td><td>支持</td></tr><tr><td>免费试用</td><td>-</td><td>不支持</td></tr><tr><td>付款周期</td><td>-</td><td>年付</td></tr></tbody></table>

## 组织账户比较 <a href="#compare-organization-plans" id="compare-organization-plans"></a>

Bitwarden 还提供组织账户（用于密码共享等），分别为针对个人使用的免费版、家庭版，针对商业使用的团队版和企业版。

{% tabs %}
{% tab title="2020-8-31之前" %}
<table><thead><tr><th width="150">功能</th><th width="150">免费版</th><th width="150">家庭版</th><th width="150">团队版</th><th>企业版</th></tr></thead><tbody><tr><td>初始价格</td><td>免费</td><td>$1.00/月</td><td>$5.00/月</td><td>$3.00/人/月</td></tr><tr><td>初始用户数</td><td>2</td><td>5</td><td>5</td><td>1</td></tr><tr><td>附加用户（/人/月）</td><td>不支持</td><td>不支持</td><td>$2.00</td><td>$3.00</td></tr><tr><td>最大用户数</td><td>2</td><td>5</td><td>无限制</td><td>无限制</td></tr><tr><td>共享条目数</td><td>无限制</td><td>无限制</td><td>无限制</td><td>无限制</td></tr><tr><td>集合数量</td><td>2</td><td>无限制</td><td>无限制</td><td>无限制</td></tr><tr><td>初始存储空间</td><td>无</td><td>1GB</td><td>1GB</td><td>1GB</td></tr><tr><td>附加存储（/GB/月）</td><td>不支持</td><td>$0.33</td><td>$0.33</td><td>$0.33</td></tr><tr><td>群组控制</td><td>不支持</td><td>不支持</td><td>不支持</td><td>支持</td></tr><tr><td>企业策略</td><td>不支持</td><td>不支持</td><td>不支持</td><td>支持</td></tr><tr><td>审核日志</td><td>不支持</td><td>不支持</td><td>不支持</td><td>支持</td></tr><tr><td>目录同步</td><td>不支持</td><td>不支持</td><td>不支持</td><td>支持</td></tr><tr><td>高级功能</td><td>无</td><td>无</td><td>无</td><td>有</td></tr><tr><td>高级功能购买</td><td>不支持</td><td>$3.33/月</td><td>不支持</td><td>-</td></tr><tr><td>本地托管</td><td>不支持</td><td>支持</td><td>不支持</td><td>支持</td></tr><tr><td>7 天免费试用</td><td>-</td><td>支持</td><td>支持</td><td>支持</td></tr><tr><td>付款周期</td><td>-</td><td>年付</td><td>年付/月付</td><td>年付/月付</td></tr></tbody></table>
{% endtab %}

{% tab title="2020-8-31之后" %}
<table><thead><tr><th width="150">功能</th><th width="150">免费版</th><th width="150">家庭版</th><th width="150">团队版</th><th>企业版</th></tr></thead><tbody><tr><td>初始价格</td><td>免费</td><td>$3.33/月</td><td>$3.00/人/月</td><td>$5.00/人/月</td></tr><tr><td>初始用户数</td><td>2</td><td>6</td><td>1</td><td>1</td></tr><tr><td>附加用户（/人/月）</td><td>不支持</td><td>不支持</td><td>$3.00</td><td>$5.00</td></tr><tr><td>最大用户数</td><td>2</td><td>6</td><td>无限制</td><td>无限制</td></tr><tr><td>共享条目数</td><td>无限制</td><td>无限制</td><td>无限制</td><td>无限制</td></tr><tr><td>集合数量</td><td>2</td><td>无限制</td><td>无限制</td><td>无限制</td></tr><tr><td>初始存储空间</td><td>无</td><td>1GB</td><td>1GB</td><td>1GB</td></tr><tr><td>附加存储（/GB/月）</td><td>不支持</td><td>$0.33</td><td>$0.33</td><td>$0.33</td></tr><tr><td>Bitwarden Send</td><td>文本</td><td>文本+文件</td><td>文本+文件</td><td>文本+文件</td></tr><tr><td>群组控制</td><td>不支持</td><td>不支持</td><td>支持</td><td>支持</td></tr><tr><td>企业策略</td><td>不支持</td><td>不支持</td><td>不支持</td><td>支持</td></tr><tr><td>审核日志</td><td>不支持</td><td>不支持</td><td>支持</td><td>支持</td></tr><tr><td>目录同步</td><td>不支持</td><td>不支持</td><td>支持</td><td>支持</td></tr><tr><td>SSO 登录</td><td>不支持</td><td>不支持</td><td>不支持</td><td>支持</td></tr><tr><td>高级功能</td><td>无</td><td>有</td><td>有</td><td>有</td></tr><tr><td>高级功能购买</td><td>不支持</td><td>-</td><td>-</td><td>-</td></tr><tr><td>本地托管</td><td>不支持</td><td>支持</td><td>不支持</td><td>支持</td></tr><tr><td>7 天免费试用</td><td>-</td><td>支持</td><td>支持</td><td>支持</td></tr><tr><td>付款周期</td><td>-</td><td>年付</td><td>年付/月付</td><td>年付/月付</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

部分功能解释：

* **文件夹**：Bitwarden 里面的文件夹可以理解为「分类」，你可以把任何类型（登录、支付卡、身份或安全笔记）的项目放到某个「文件夹」中。
* **内置 TOTP**：相当于内置了一个类似 [Authy](https://authy.com/) 这样的两步验证管理工具，这样就不需要再单独安装和使用一个 Authy 应用程序了。
* **两步登录类型**：这里的两步登录类型是针对登录 Bitwarden 的两步登录，与除 Bitwarden 之外的其他网站或程序的两步登录没关系。

## 价格和账单 <a href="#price-and-billing" id="price-and-billing"></a>

1. 付费组织订阅如何 7 天免费试用：你必须先订阅才能试用（订阅时需要输入付款信息），7 天免费试用期结束的时候，才会从您输入的付款方式中扣款。记得在订阅后的 7 天内主动取消订阅。
2. 支持订阅开始日期 30 天内的无条件退款（需要给 [Bitwarden 支持](https://bitwarden.com/contact/)发邮件）。

### 价格比较 <a href="#compare-price" id="compare-price"></a>

{% tabs %}
{% tab title="2020-8-31之前" %}
<table><thead><tr><th width="150">项目</th><th width="150">家庭版（仅年付）</th><th width="150">团队版年付</th><th width="150">企业版年付</th><th width="150">团队版月付</th><th>企业版月付</th></tr></thead><tbody><tr><td>初始价格</td><td>$1.00/月</td><td>$5.00/月</td><td>$3.00/人/月</td><td>$8.00/月</td><td>$4.00/人/月</td></tr><tr><td>附加用户</td><td>-</td><td>$2.00/人/月</td><td>$3.00/人/月</td><td>$2.50/人/月</td><td>$4.00/人/月</td></tr><tr><td>附加存储</td><td>$0.33/GB/月</td><td>$0.33/GB/月</td><td>$0.33/GB/月</td><td>$0.50/GB/月</td><td>$0.50/GB/月</td></tr><tr><td>高级功能</td><td>$3.33/月</td><td>需个人购买</td><td>需个人购买</td><td>需个人购买</td><td>需个人购买</td></tr></tbody></table>
{% endtab %}

{% tab title="2020-8-31之后" %}
<table><thead><tr><th width="150">项目</th><th width="150">家庭版（仅年付）</th><th width="150">团队版年付</th><th width="150">企业版年付</th><th width="150">团队版月付</th><th>企业版月付</th></tr></thead><tbody><tr><td>初始价格</td><td>$3.33/月</td><td>$3.00/人/月</td><td>$5.00/人/月</td><td>$4.00/人/月</td><td>$6.00/人/月</td></tr><tr><td>附加用户</td><td>-</td><td>$3.00/人/月</td><td>$5.00/人/月</td><td>$4.00/人/月</td><td>$6.00/人/月</td></tr><tr><td>附加存储</td><td>$0.33/GB/月</td><td>$0.33/GB/月</td><td>$0.33/GB/月</td><td>$0.5/GB/月</td><td>0.5/GB/月</td></tr><tr><td>高级功能</td><td>已包含</td><td>已包含</td><td>已包含</td><td>已包含</td><td>已包含</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

### 账单示例 <a href="#example-bill" id="example-bill"></a>

Bitwarden Inc. 与 Stripe 合作，提供安全的账单和支付处理服务。[在线账单示例](https://pay.stripe.com/invoice/acct\_19smIXIGBnsLynRr/invst\_Gxl9wk8thL7uIP8FnEWcpplsD0MsFKd)或本地账单示例。

{% file src=".gitbook/assets/Invoice-3167AF0C-0001.pdf" %}

# 创建 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/create-send/)
{% endhint %}

任何用户都可以创建文本 Send，但文件 Send 的创建仅适用于[高级用户](../../plans-and-pricing/password-manager/about-bitwarden-plans.md)，或付费组织（家庭版、团队版或企业版）的成员。

{% hint style="info" %}
如果您是激活了 [Send 控制策略](../../admin-console/oversight-visibility/enterprise-policies.md#send-controls)中的**禁用 Send** 选项的组织的成员，则您无法创建新的 Send 或编辑现有的 Send。虽然强制执行此策略时无法使用 Bitwarden 网页 App 访问 Send 页面，但您可以从任何其他客户端查看或删除现有的 Send。
{% endhint %}

选择您想要使用 Send 的 Bitwarden App 以开始：

{% tabs %}
{% tab title="网页 App" %}
要从网页 App 创建一个新的 Send：

1、从导航栏选择 **Send**。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**密码库**视图一样，您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择 ✚**新建 Send** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/9KgYcB25tb8NfYnitr0c0/a874be205a9a09ed66ad33a8d4c95ca9/2026-02-25_10-37-01.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>新建 Send</p></figcaption></figure></div>

3、在**新建 Send** 对话框中，指定如下内容：

* **这是什么类型的 Send？**：选择此 Send 是**文本**还是**文件**：

<table><thead><tr><th width="100">类型</th><th>步骤</th></tr></thead><tbody><tr><td><strong>文本</strong></td><td><p>在输入框中输入或粘贴所需的文本。切换<strong>访问 Send 时，默认隐藏文本</strong>选项，将要求接收者在打开 Send 时<a href="send-privacy.md">切换可见性</a>。加密后的 Send 不能超过 1000 个字符。</p><p></p><p>保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会增加到 ~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。</p></td></tr><tr><td><strong>文件</strong></td><td>选择<strong>选择文件</strong>按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 500 MB（移动端是 100 MB）。（<strong>要求高级版</strong> &#x26; 验证电子邮箱）</td></tr></tbody></table>

* **名称**：为此 Send 指定一个可识别的有含义的名称。

默认情况下，Send 将在其创建后的 7 天后删除。您可以更改它以及更改其他选项（请参阅第 4 步），否则，点击**保存**以完成创建 Send。

4、根据需要配置以下选项：

<table><thead><tr><th width="100">选项</th><th>描述</th></tr></thead><tbody><tr><td><strong>默认隐藏文本</strong></td><td>Send 内容将默认隐藏。</td></tr><tr><td><strong>删除日期</strong></td><td>此 Send 将在指定的日期和时间被永久<a href="send-lifespan.md#deletion-behavior">删除</a>。默认为创建后 7 天。<strong>允许的最大值</strong>为自创建后 30 天。</td></tr><tr><td><strong>谁可以查看</strong></td><td><p>选择谁可以查看：</p><p></p><p><strong>拥有链接的任何人</strong>：收到 Send 链接的任何人都可以查看 Send 的内容。</p><p></p><p><strong>指定的人员</strong>：指定可以接收此 Send 的收件人的<a href="send-privacy.md#email-verified-recipients">电子邮箱地址</a>。当访问 Send 时，他们将在电子邮件中收到验证码（<strong>要求高级版</strong>）。</p><p></p><p><strong>拥有您设置的密码的任何人</strong>：要求此 Send 的收件人<a href="send-privacy.md#send-passwords">输入密码</a>才能获得访问权限。</p></td></tr><tr><td><strong>限制查看</strong></td><td>在达到指定的访问次数后，此 Send 将被<a href="send-lifespan.md#maximum-access-count-behavior">禁用</a>。默认为不指定。</td></tr><tr><td><strong>对查看者隐藏您的电子邮箱地址</strong></td><td>对 Send 接收者<a href="send-privacy.md#hide-email">隐藏您的电子邮箱</a>。</td></tr><tr><td><strong>私密备注</strong></td><td>输入此 Send 的私密备注，该备注仅对您可见。</td></tr></tbody></table>

对 Send 满意后，选择**保存**以完成。

Send 创建后，使用 **≡选项**菜单然后选择 **❐复制 Send 链接**按钮以将生成的链接复制到剪贴板：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1PiQrX748LtTFXChfAIbFP/0ff74124a0d215254c532fe79cff9012/2026-02-25_11-08-25.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>Send 选项</p></figcaption></figure></div>

复制后，将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展创建一个新的 Send：

1、选择 ✈️**Send** 标签页。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**密码库**视图一样，您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择 ✚**新增** 按钮然后选择**文本**或**文件**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2qOv6DJYX1is2zurmeVBOd/5d2f0fd435c2534bc3377d651cd4f7f1/2026-02-25_11-11-56.png?w=480&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展 Send 视图</p></figcaption></figure></div>

3、在**新建 Send** 视图中，指定如下内容：

* **名称**：为此 Send 指定一个可识别的有含义的名称。
* 某些选项取决于您选择的是**文本**还是**文件**：

<table><thead><tr><th width="100">类型</th><th>步骤</th></tr></thead><tbody><tr><td><strong>文本</strong></td><td><p>在输入框中输入或粘贴所需的文本。切换<strong>访问 Send 时，默认隐藏文本</strong>选项，将要求接收者在打开 Send 时<a href="send-privacy.md">切换可见性</a>。加密后的 Send 不能超过 1000 个字符。</p><p></p><p>保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会增加到 ~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。</p></td></tr><tr><td><strong>文件</strong></td><td>选择<strong>选择文件</strong>按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 500 MB（移动端是 100 MB）。（<strong>要求高级版</strong> &#x26; 验证电子邮箱）</td></tr></tbody></table>

* **名称**：为此 Send 指定一个可识别的有含义的名称。

默认情况下，Send 将在其创建后的 7 天后删除。您可以更改它以及更改其他选项（请参阅第 4 步），然后，点击**保存**以完成创建 Send。

{% hint style="info" %}
要在使用 Firefox 或 Safari 浏览器扩展时创建 Send，必须在侧边栏打开扩展或选择弹出按钮：

<img src="https://bitwarden.com/assets/1cbJy0jLBmSQmRumvYzVwp/a9e43f4c154686249056924eb3e56323/pop_out_screenshot.png?w=800&#x26;fm=avif" alt="" data-size="original">
{% endhint %}

4、根据需要配置以下选项：

<table><thead><tr><th width="100">选项</th><th>描述</th></tr></thead><tbody><tr><td><strong>默认隐藏文本</strong></td><td>Send 内容将默认隐藏。</td></tr><tr><td><strong>删除日期</strong></td><td>此 Send 将在指定的日期和时间被永久<a href="send-lifespan.md#deletion-behavior">删除</a>。默认为创建后 7 天。<strong>允许的最大值</strong>为自创建后 30 天。</td></tr><tr><td><strong>谁可以查看</strong></td><td><p>选择谁可以查看：</p><p></p><p><strong>拥有链接的任何人</strong>：收到 Send 链接的任何人都可以查看 Send 的内容。</p><p></p><p><strong>指定的人员</strong>：指定可以接收此 Send 的收件人的<a href="send-privacy.md#email-verified-recipients">电子邮箱地址</a>。当访问 Send 时，他们将在电子邮件中收到验证码（<strong>要求高级版</strong>）。</p><p></p><p><strong>拥有您设置的密码的任何人</strong>：要求此 Send 的收件人<a href="send-privacy.md#send-passwords">输入密码</a>才能获得访问权限。</p></td></tr><tr><td><strong>限制查看</strong></td><td>在达到指定的访问次数后，此 Send 将被<a href="send-lifespan.md#maximum-access-count-behavior">禁用</a>。默认为不指定。</td></tr><tr><td><strong>对查看者隐藏您的电子邮箱地址</strong></td><td>对 Send 接收者<a href="send-privacy.md#hide-email">隐藏您的电子邮箱</a>。</td></tr><tr><td><strong>私密备注</strong></td><td>输入此 Send 的私密备注，该备注仅对您可见。</td></tr></tbody></table>

对 Send 满意后，选择**保存**以完成。

Send 创建后，您可以复制链接或选择 **≡**&#x7136;后选择**复制 Send 链接**按钮以将生成的链接复制到剪贴板：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1lLksK7QbomKPRueO41c4d/7af290d439cb39056564454b78e52936/2026-02-25_11-18-05.png?w=481&#x26;fm=avif" alt=""><figcaption><p>复制 Send 链接</p></figcaption></figure></div>

复制后，将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="桌面端" %}
要从桌面 App 创建一个新的 Send：

1、选择 ✈️**Send** 标签页。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**密码库**视图一样，您可以通过点击某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择 **新增 Send** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2O01p5FyMpUhlhi5bAq7mH/0c154046969e8028d95fb4bdbaf12b93/2026-02-26_15-40-37.png?w=1249&#x26;fm=avif" alt=""><figcaption><p>桌面 App Send 视图</p></figcaption></figure></div>

3、在右边栏中，指定如下内容：

* **名称**：为此 Send 指定一个可识别的有含义的名称。
* **类型**：选择此 Send 是**文本**还是**文件**：

<table><thead><tr><th width="100">类型</th><th>步骤</th></tr></thead><tbody><tr><td><strong>文本</strong></td><td><p>在输入框中输入或粘贴所需的文本。切换<strong>访问 Send 时，默认隐藏文本</strong>选项，将要求接收者在打开 Send 时<a href="send-privacy.md">切换可见性</a>。加密后的 Send 不能超过 1000 个字符。</p><p></p><p>保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会增加到 ~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。</p></td></tr><tr><td><strong>文件</strong></td><td>选择<strong>选择文件</strong>按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 500 MB（移动端是 100 MB）。（<strong>要求高级版</strong> &#x26; 验证电子邮箱）</td></tr></tbody></table>

默认情况下，Send 将在其创建后的 7 天后删除。您可以更改它以及更改其他选项（请参阅第 4 步），否则，点击**保存**以完成创建 Send。

4、根据需要配置以下选项：

<table><thead><tr><th width="100">选项</th><th>描述</th></tr></thead><tbody><tr><td><strong>默认隐藏文本</strong></td><td>Send 内容将默认隐藏。</td></tr><tr><td><strong>删除日期</strong></td><td>此 Send 将在指定的日期和时间被永久<a href="send-lifespan.md#deletion-behavior">删除</a>。默认为创建后 7 天。<strong>允许的最大值</strong>为自创建后 30 天。</td></tr><tr><td><strong>谁可以查看</strong></td><td><p>选择谁可以查看：</p><p></p><p><strong>拥有链接的任何人</strong>：收到 Send 链接的任何人都可以查看 Send 的内容。</p><p></p><p><strong>指定的人员</strong>：指定可以接收此 Send 的收件人的<a href="send-privacy.md#email-verified-recipients">电子邮箱地址</a>。当访问 Send 时，他们将在电子邮件中收到验证码（<strong>要求高级版</strong>）。</p><p></p><p><strong>拥有您设置的密码的任何人</strong>：要求此 Send 的收件人<a href="send-privacy.md#send-passwords">输入密码</a>才能获得访问权限。</p></td></tr><tr><td><strong>限制查看</strong></td><td>在达到指定的访问次数后，此 Send 将被<a href="send-lifespan.md#maximum-access-count-behavior">禁用</a>。默认为不指定。</td></tr><tr><td><strong>对查看者隐藏您的电子邮箱地址</strong></td><td>对 Send 接收者<a href="send-privacy.md#hide-email">隐藏您的电子邮箱</a>。</td></tr><tr><td><strong>私密备注</strong></td><td>输入此 Send 的私密备注，该备注仅对您可见。</td></tr></tbody></table>

对 Send 满意后，选择**保存**以完成。

Send 创建后，选择 **≡** 然后选择**复制 Send 链接**按钮以将生成的链接复制到剪贴板：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4IgMnKAEjk16bJdbuUkVeH/aef61f80bb7426874c937d07eaa58b85/2026-02-25_11-40-24.png?w=1315&#x26;fm=avif" alt=""><figcaption><p>桌面 App 复制 Send 链接</p></figcaption></figure></div>

复制后，将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="移动端" %}
要从移动 App 创建一个新的 Send：

1、点击 ✈️**Send** 标签页。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**我的密码库**视图一样，您可以通过点击某一可用的**类型**来筛选 Send。
{% endhint %}

2、点击 ✚**新增 Send** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5vHsSA3o9O735MitlnOPVr/e2eeb5387bf1358f4aa0aaafbfaa3d5c/new_send_mobile.png?w=715&#x26;fm=avif" alt=""><figcaption><p>移动端 Send</p></figcaption></figure></div>

3、在**添加 Send** 视图中，指定如下内容：

* **类型**：选择此 Send 是**文本**还是**文件**：

<table><thead><tr><th width="100">类型</th><th>步骤</th></tr></thead><tbody><tr><td><strong>文本</strong></td><td><p>在输入框中输入或粘贴所需的文本。切换<strong>访问 Send 时，默认隐藏文本</strong>选项，将要求接收者在打开 Send 时<a href="send-privacy.md">切换可见性</a>。加密后的 Send 不能超过 1000 个字符。</p><p></p><p>保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会增加到 ~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。</p></td></tr><tr><td><strong>文件</strong></td><td>选择<strong>选择文件</strong>按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 500 MB（移动端是 100 MB）。（<strong>要求高级版</strong> &#x26; 验证电子邮箱）</td></tr></tbody></table>

* **名称**：为此 Send 指定一个可识别的有含义的名称。

默认情况下，Send 将在其创建后的 7 天后删除。您可以使用 \
&#xNAN;**⋁附加选项**菜单更改它以及更改其他选项（请参阅第 4 步），否则，点击**保存**以完成创建 Send。

4、根据需要配置以下选项：

<table><thead><tr><th width="100">选项</th><th>描述</th></tr></thead><tbody><tr><td><strong>默认隐藏文本</strong></td><td>Send 内容将默认隐藏。</td></tr><tr><td><strong>删除日期</strong></td><td>此 Send 将在指定的日期和时间被永久<a href="send-lifespan.md#deletion-behavior">删除</a>。默认为创建后 7 天。<strong>允许的最大值</strong>为自创建后 30 天。</td></tr><tr><td><strong>谁可以查看</strong></td><td><p>选择谁可以查看：</p><p></p><p><strong>拥有链接的任何人</strong>：收到 Send 链接的任何人都可以查看 Send 的内容。</p><p></p><p><strong>指定的人员</strong>：指定可以接收此 Send 的收件人的<a href="send-privacy.md#email-verified-recipients">电子邮箱地址</a>。当访问 Send 时，他们将在电子邮件中收到验证码（<strong>要求高级版</strong>）。</p><p></p><p><strong>拥有您设置的密码的任何人</strong>：要求此 Send 的收件人<a href="send-privacy.md#send-passwords">输入密码</a>才能获得访问权限。</p></td></tr><tr><td><strong>限制查看</strong></td><td>在达到指定的访问次数后，此 Send 将被<a href="send-lifespan.md#maximum-access-count-behavior">禁用</a>。默认为不指定。</td></tr><tr><td><strong>对查看者隐藏您的电子邮箱地址</strong></td><td>对 Send 接收者<a href="send-privacy.md#hide-email">隐藏您的电子邮箱</a>。</td></tr><tr><td><strong>私密备注</strong></td><td>输入此 Send 的私密备注，该备注仅对您可见。</td></tr></tbody></table>

对 Send 的满意后，选择**保存**以完成。

Send 创建后，选择 **≡**&#x7136;后选择**分享链接**选项：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6WZTQUop3KXnQKoGqgVzgu/8bf9c1b068a97856c5d13b09449a1fdf/shore-mobile-send.png?w=715&#x26;fm=avif" alt=""><figcaption><p>移动端分享 Send</p></figcaption></figure></div>

{% hint style="info" %}
如果您使用的是 iOS，您还可以直接从 iOS [共享菜单](https://developer.apple.com/design/human-interface-guidelines/ios/extensions/sharing-and-actions/)分享您的 Send。
{% endhint %}

将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="CLI" %}
以下的示例命令用于帮助您从 CLI 使用 Send 入门。更多帮助编写您自己的 Send 命令的示例，我们建议阅读 [CLI 上的 Send](send-from-cli.md)。

要创建一个简单的文本 Send，将[删除日期](send-lifespan.md#deletion-date)设置为自创建之日起 14 天：

```batch
bw send -n "My Text Send" -d 14 "My first secret message."
```

要创建一个简单的文件 Send，将[删除日期](send-lifespan.md#deletion-date)设置为自创建之日起 14 天：

```batch
bw send -n "My File Send" - d 14 -f /Users/myaccount/Documents/my_file.pdf
```
{% endtab %}
{% endtabs %}

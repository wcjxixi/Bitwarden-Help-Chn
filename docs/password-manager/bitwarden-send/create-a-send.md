# 创建 & 编辑 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/create-send/)
{% endhint %}

Bitwarden Send 功能让您能够通过安全生成的链接，与任何人分享加密的文本或文件。您可以从任何 Bitwarden App 中创建 Send，并根据您的分享需求配置访问权限和隐私选项。

{% hint style="info" %}
如果您所在的组织已在[管理 Send 策略](../../admin-console/oversight-visibility/enterprise-policies.md#manage-send)下关闭了 Send 功能，您对 Send 的访问将受到限制：

* 您无法创建新的 Send，也无法编辑现有的 Send。
* 您可以在所有 Bitwarden 客户端（网页 App 除外）的 **Send** 页面查看和删除 Send。
* 您无法通过 Bitwarden 网页 App 访问 Send 页面。

使用管理 Send 策略，组织所有者和管理员还可以控制创建新 Send 时哪些字段不可用。
{% endhint %}

## 创建 Send <a href="#create-a-send" id="create-a-send"></a>

有两种类型的 Send：

* **文本 Send** 共享加密的文本内容，例如消息或笔记。所有 Bitwarden 用户都可以创建和编辑文本 Send。
* **文件 Send** 包含加密的文件，例如文档或图片。只有高级版用户或付费版组织（家庭版、团队版或企业版）的成员才能创建文件 Send。要创建文件 Send，您账户的电子邮箱地址也必须已经过验证。

{% hint style="info" %}
如果您的账户较旧，您可能需要主动验证您的电子邮箱。登录[网页 App](https://vault.bitwarden.com/) 然后选择**验证电子邮箱**。如果您的账户电子邮箱未经验证，则无法创建 [Send](about-send.md)。
{% endhint %}

选择您想要使用 Send 的 Bitwarden App 以开始：

{% tabs %}
{% tab title="网页 App" %}
要从网页 App 创建新的 Send：

1、选择 <i class="fa-paper-plane-top">:paper-plane-top:</i>**Send**。

{% hint style="info" %}
该页面将列出所有您创建的尚未达到[删除日期](send-lifespan.md#deletion-date)的 Send。您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择 <i class="fa-plus">:plus:</i>**新增**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/9KgYcB25tb8NfYnitr0c0/a874be205a9a09ed66ad33a8d4c95ca9/2026-02-25_10-37-01.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>新建 Send</p></figcaption></figure></div>

3、选择要创建的 Send 的类型：**文本**或**文件**。

4、输入**名称**。此名称将对打开该 Send 的任何人可见。

5、根据 Send 类型的不同：

* 对于**文本 Send**，输入**要分享的文本**。如果您不希望链接在浏览器中首次打开时显示此文本，请勾选**默认隐藏文本。**&#x8FD9;将要求接收者[切换可见性](send-privacy.md#hide-text)才能阅读您的消息。

{% hint style="info" %}
文本 Send 最多可包含加密的 1,000 个字符。保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会扩展到 \~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。
{% endhint %}

* 对于**文件 Send**，选择**选择文件**然后挑选您的文件。

{% hint style="info" %}
每个文件 Send 的最大文件大小为 500 MB（移动端是 100 MB）。
{% endhint %}

6、从下拉菜单中选择**删除日期**，届时 Send 将被永久[删除](send-lifespan.md#deletion-date)。默认为创建后 7 天，允许的最大值为 30 天。

7、（可选）根据需要调整其余选项：

* 从下拉菜单中选择**谁可以查看**：
  * 选择**拥有链接的任何人**以允许任何人打开 Send 链接并查看其内容。这是默认选项。
  * 选择**指定的人员**并输入他们的电子邮箱地址（最多 2,500 个字符），以在打开 Send 前[要求 Send 电子邮箱验证](send-privacy.md#email-verified-recipients)。
  * 选择**拥有您设置的密码的任何人**，以要求接收者[输入密码才能打开 Send](send-privacy.md#send-passwords)。
* 在**限制查看次数**中输入一个数字，以控制 Send 在被[停用](send-lifespan.md#maximum-access-count-behavior)前可以被打开的次数。默认情况下不设置限制。
* 勾选**对查看者隐藏您的电子邮箱地址**，以从打开的 Send 中移除您账户的电子邮箱。

{% hint style="info" %}
当 Send 被限制为**指定的人员**或**拥有您设置的密码的任何人**时，您的电子邮箱地址将始终隐藏，直到接收者输入通过电子邮件发送的验证码或密码。之后，**对查看者隐藏您的电子邮箱地址**设置才生效。
{% endhint %}

* 输入仅对您（Send 的创建者）可见的**私密备注**。此备注不会显示在打开的 Send 上。

8、选择**保存**。

Send 创建后，使用 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i>**选项**菜单然后选择 <i class="fa-copy">:copy:</i>**复制 Send 链接**按钮以将生成的链接复制到剪贴板：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1PiQrX748LtTFXChfAIbFP/0ff74124a0d215254c532fe79cff9012/2026-02-25_11-08-25.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>Send 选项</p></figcaption></figure></div>

复制后，您可以通过任何喜欢的方式将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="浏览器扩展" %}
{% hint style="info" %}
要使用 Firefox 或 Safari 浏览器扩展创建 Send，您必须在侧边栏中打开扩展，或选择弹出按钮：

<img src="https://bitwarden.com/assets/1cbJy0jLBmSQmRumvYzVwp/a9e43f4c154686249056924eb3e56323/pop_out_screenshot.png?w=407&#x26;fm=avif" alt="" data-size="original">
{% endhint %}

要从浏览器扩展创建新的 Send：

1、选择 <i class="fa-paper-plane-top">:paper-plane-top:</i>**Send**。

{% hint style="info" %}
该页面将列出所有您创建的尚未达到[删除日期](send-lifespan.md#deletion-date)的 Send。您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择  <i class="fa-plus">:plus:</i>**新增**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2qOv6DJYX1is2zurmeVBOd/5d2f0fd435c2534bc3377d651cd4f7f1/2026-02-25_11-11-56.png?w=480&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展中的 Send 视图</p></figcaption></figure></div>

3、选择要创建的 Send 的类型：**文本**或**文件**。

4、输入**名称**。此名称将对打开该 Send 的任何人可见。

5、根据 Send 类型的不同：

* 对于**文本 Send**，输入**要分享的文本**。如果您不希望链接在浏览器中首次打开时显示此文本，请勾选**默认隐藏文本。**&#x8FD9;将要求接收者[切换可见性](send-privacy.md#hide-text)才能阅读您的消息。

{% hint style="info" %}
文本 Send 最多可包含加密的 1,000 个字符。保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会扩展到 \~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。
{% endhint %}

* 对于**文件 Send**，选择**选择文件**然后挑选您的文件。

{% hint style="info" %}
每个文件 Send 的最大文件大小为 500 MB（移动端是 100 MB）。
{% endhint %}

6、从下拉菜单中选择**删除日期**，届时 Send 将被永久[删除](send-lifespan.md#deletion-date)。默认为创建后 7 天，允许的最大值为 30 天。

7、（可选）根据需要调整其余选项：

* 从下拉菜单中选择**谁可以查看**：
  * 选择**拥有链接的任何人**以允许任何人打开 Send 链接并查看其内容。这是默认选项。
  * 选择**指定的人员**并输入他们的电子邮箱地址（最多 2,500 个字符），以在打开 Send 前[要求 Send 电子邮箱验证](send-privacy.md#email-verified-recipients)。
  * 选择**拥有您设置的密码的任何人**，以要求接收者[输入密码才能打开 Send](send-privacy.md#send-passwords)。
* 在**限制查看次数**中输入一个数字，以控制 Send 在被[停用](send-lifespan.md#maximum-access-count-behavior)前可以被打开的次数。默认情况下不设置限制。
* 勾选**对查看者隐藏您的电子邮箱地址**，以从打开的 Send 中移除您账户的电子邮箱。

{% hint style="info" %}
当 Send 被限制为**指定的人员**或**拥有您设置的密码的任何人**时，您的电子邮箱地址将始终隐藏，直到接收者输入通过电子邮件发送的验证码或密码。之后，**对查看者隐藏您的电子邮箱地址**设置才生效。
{% endhint %}

* 输入仅对您（Send 的创建者）可见的**私密备注**。此备注不会显示在打开的 Send 上。

8、选择**保存**。

Send 创建后，您可以复制链接，或选择  <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i> 然后点击**复制 Send 链接**以将生成的链接复制到剪贴板：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1lLksK7QbomKPRueO41c4d/7af290d439cb39056564454b78e52936/2026-02-25_11-18-05.png?w=481&#x26;fm=avif" alt=""><figcaption><p>复制 Send 链接</p></figcaption></figure></div>

复制后，您可以通过任何喜欢的方式将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="桌面端" %}
要从桌面 App 创建新的 Send：

1、选择 <i class="fa-paper-plane-top">:paper-plane-top:</i>**Send**。

{% hint style="info" %}
该页面将列出所有您创建的尚未达到[删除日期](send-lifespan.md#deletion-date)的 Send。您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择  <i class="fa-plus">:plus:</i>**新增**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2O01p5FyMpUhlhi5bAq7mH/3135d39e953c52bb0d843ee6afeb1121/2026-04-23_11-48-19.png?w=979&#x26;fm=avif" alt=""><figcaption><p>桌面 App 中的 Send 视图</p></figcaption></figure></div>

3、选择要创建的 Send 的类型：**文本**或**文件**。

4、输入**名称**。此名称将对打开该 Send 的任何人可见。

5、根据 Send 类型的不同：

* 对于**文本 Send**，输入**要分享的文本**。如果您不希望链接在浏览器中首次打开时显示此文本，请勾选**默认隐藏文本。**&#x8FD9;将要求接收者[切换可见性](send-privacy.md#hide-text)才能阅读您的消息。

{% hint style="info" %}
文本 Send 最多可包含加密的 1,000 个字符。保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会扩展到 \~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。
{% endhint %}

* 对于**文件 Send**，选择**选择文件**然后挑选您的文件。

{% hint style="info" %}
每个文件 Send 的最大文件大小为 500 MB（移动端是 100 MB）。
{% endhint %}

6、从下拉菜单中选择**删除日期**，届时 Send 将被永久[删除](send-lifespan.md#deletion-date)。默认为创建后 7 天，允许的最大值为 30 天。

7、（可选）根据需要调整其余选项：

* 从下拉菜单中选择**谁可以查看**：
  * 选择**拥有链接的任何人**以允许任何人打开 Send 链接并查看其内容。这是默认选项。
  * 选择**指定的人员**并输入他们的电子邮箱地址（最多 2,500 个字符），以在打开 Send 前[要求 Send 电子邮箱验证](send-privacy.md#email-verified-recipients)。
  * 选择**拥有您设置的密码的任何人**，以要求接收者[输入密码才能打开 Send](send-privacy.md#send-passwords)。
* 在**限制查看次数**中输入一个数字，以控制 Send 在被[停用](send-lifespan.md#maximum-access-count-behavior)前可以被打开的次数。默认情况下不设置限制。
* 勾选**对查看者隐藏您的电子邮箱地址**，以从打开的 Send 中移除您账户的电子邮箱。

{% hint style="info" %}
当 Send 被限制为**指定的人员**或**拥有您设置的密码的任何人**时，您的电子邮箱地址将始终隐藏，直到接收者输入通过电子邮件发送的验证码或密码。之后，**对查看者隐藏您的电子邮箱地址**设置才生效。
{% endhint %}

* 输入仅对您（Send 的创建者）可见的**私密备注**。此备注不会显示在打开的 Send 上。

8、选择**保存**。

Send 创建后，选择 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i> 然后选择**复制 Send 链接**以将生成的链接复制到剪贴板：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4IgMnKAEjk16bJdbuUkVeH/fb20d049505d8a69dce6f39e4e4a9c4c/2026-04-23_11-49-34.png?w=979&#x26;fm=avif" alt=""><figcaption><p>桌面端的 Send 选项</p></figcaption></figure></div>

复制后，您可以通过任何喜欢的方式将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="移动端" %}
要从移动 App 创建新的 Send：

1、选择 <i class="fa-paper-plane-top">:paper-plane-top:</i>**Send**。

{% hint style="info" %}
该页面将列出所有您创建的尚未达到[删除日期](send-lifespan.md#deletion-date)的 Send。您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择  <i class="fa-plus">:plus:</i>**新增图标**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5vHsSA3o9O735MitlnOPVr/e2eeb5387bf1358f4aa0aaafbfaa3d5c/new_send_mobile.png?w=715&#x26;fm=avif" alt=""><figcaption><p>移动 App 中的 Send</p></figcaption></figure></div>

3、选择要创建的 Send 的类型：**文本**或**文件**。

4、输入**名称**。此名称将对打开该 Send 的任何人可见。

5、根据 Send 类型的不同：

* 对于**文本 Send**，输入**要分享的文本**。如果您不希望链接在浏览器中首次打开时显示此文本，请勾选**默认隐藏文本。**&#x8FD9;将要求接收者[切换可见性](send-privacy.md#hide-text)才能阅读您的消息。

{% hint style="info" %}
文本 Send 最多可包含加密的 1,000 个字符。保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会扩展到 \~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。
{% endhint %}

* 对于**文件 Send**，选择**选择文件**然后挑选您的文件。

{% hint style="info" %}
每个文件 Send 的最大文件大小为 500 MB（移动端是 100 MB）。
{% endhint %}

6、从下拉菜单中选择**删除日期**，届时 Send 将被永久[删除](send-lifespan.md#deletion-date)。默认为创建后 7 天，允许的最大值为 30 天。

7、（可选）根据需要调整其余选项：

* 从下拉菜单中选择**谁可以查看**：
  * 选择**拥有链接的任何人**以允许任何人打开 Send 链接并查看其内容。这是默认选项。
  * 选择**指定的人员**并输入他们的电子邮箱地址（最多 2,500 个字符），以在打开 Send 前[要求 Send 电子邮箱验证](send-privacy.md#email-verified-recipients)。
  * 选择**拥有您设置的密码的任何人**，以要求接收者[输入密码才能打开 Send](send-privacy.md#send-passwords)。
* 在**限制查看次数**中输入一个数字，以控制 Send 在被[停用](send-lifespan.md#maximum-access-count-behavior)前可以被打开的次数。默认情况下不设置限制。
* 勾选**对查看者隐藏您的电子邮箱地址**，以从打开的 Send 中移除您账户的电子邮箱。

{% hint style="info" %}
当 Send 被限制为**指定的人员**或**拥有您设置的密码的任何人**时，您的电子邮箱地址将始终隐藏，直到接收者输入通过电子邮件发送的验证码或密码。之后，**对查看者隐藏您的电子邮箱地址**设置才生效。
{% endhint %}

* 输入仅对您（Send 的创建者）可见的**私密备注**。此备注不会显示在打开的 Send 上。

8、选择**保存**。

Send 创建后，选择 <i class="fa-ellipsis">:ellipsis:</i> 然后选择**分享链接**选项：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6WZTQUop3KXnQKoGqgVzgu/8bf9c1b068a97856c5d13b09449a1fdf/shore-mobile-send.png?w=715&#x26;fm=avif" alt=""><figcaption><p>在移动端分享 Send</p></figcaption></figure></div>

{% hint style="info" %}
如果您使用 iOS，还可以直接从 iOS [分享菜单](https://developer.apple.com/design/human-interface-guidelines/ios/extensions/sharing-and-actions/)中分享您的 Send。
{% endhint %}

复制后，您可以通过任何喜欢的方式将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="CLI" %}
以下的示例命令用于帮助您从 CLI 使用 Send 入门。更多帮助编写您自己的 Send 命令的示例，我们建议阅读 [CLI 上的 Send](send-from-cli.md)。

要创建一个简单的文本 Send，并将[删除日期](send-lifespan.md#deletion-date)设置为自创建之日后的 14 天：

```batch
bw send -n "My Text Send" -d 14 "My first secret message."
```

要创建一个简单的文件 Send，并将[删除日期](send-lifespan.md#deletion-date)设置为自创建之日后的 14 天：

```batch
bw send -n "My File Send" - d 14 -f /Users/myaccount/Documents/my_file.pdf
```
{% endtab %}
{% endtabs %}

## 编辑 Send <a href="#edit-a-send" id="edit-a-send"></a>

{% tabs %}
{% tab title="网页 App" %}
要编辑 Send：

1. 前往 **Send**。
2. 选择 **Send** 的名称。
3. 选择**编辑**。
4. 进行所需的更改，然后选择**保存**。
{% endtab %}

{% tab title="浏览器扩展" %}
要编辑 Send：

1. 前往 **Send**。
2. 选择 **Send** 的名称。
3. 进行所需的更改，然后选择**保存**。
{% endtab %}

{% tab title="桌面端" %}
要编辑 Send：

1. 前往 **Send**。
2. 选择 **Send** 的名称。
3. 进行所需的更改，然后选择**保存**。
{% endtab %}

{% tab title="移动端" %}
要编辑 Send：

1. 点击 **Send**。
2. 点击 **Send** 的名称。
3. 进行所需的更改，然后点击 <i class="fa-circle-check">:circle-check:</i>**检查**图标。
{% endtab %}

{% tab title="CLI" %}
使用 `edit` 命令[通过 CLI 更新 Send](send-from-cli.md#edit)。
{% endtab %}
{% endtabs %}

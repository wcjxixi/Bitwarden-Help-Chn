# ==创建 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/create-send/)
{% endhint %}

任何用户都可以创建文本 Send，但文件 Send 的创建仅适用于[高级用户](../plans-and-pricing/password-manager/about-bitwarden-plans.md)，或付费组织（家庭、团队或企业）的成员。选择您想要使用的 Bitwarden App 以开始：

{% tabs %}
{% tab title="网页 App" %}
要从网页 App 创建一个新的 Send：

1、从导航栏选择 **Send**。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**密码库**视图一样，您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择 ✚**新建 Send** 按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/63ReMUtu41rk0xNrxr6aHF/76e84697397cad9915a24d0f37f58374/2024-12-03_10-06-39.png?_a=DAJCwlWIZAAB" %}
新建 Send
{% endembed %}

3、在**新建 Send** 对话框中，为 Send 指定如下内容：

* **这是什么类型的 Send？**：选择此 Send 是**文本**还是**文件**：

<table><thead><tr><th width="150">类型</th><th>描述</th></tr></thead><tbody><tr><td><strong>文本</strong></td><td><p>在输入框中输入或粘贴所需的文本。切换<strong>访问 Send 时，默认隐藏文本</strong>选项，将要求接收者在打开 Send 时<a href="send-privacy.md">切换可见性</a>。加密后的发送内容不得超过 1000 个字符。</p><p></p><p>保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会增加到 ~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。</p></td></tr><tr><td><strong>文件</strong></td><td>选择<strong>选择文件</strong>按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 500 MB（移动端是 100 MB）。（<strong>要求高级会员</strong> &#x26; 已验证电子邮箱）</td></tr></tbody></table>

* **名称**：为此 Send 指定一个可识别的有含义的名称。

默认情况下，Send 将在其创建后的 7 天后删除。您可以使用 **⮟选项**菜单配置此选项及其他选项（请参阅第 4 步），否则，点击**保存**以完成创建 Send。

4、选择 **⮟选项**菜单，根据需要配置以下选项：

<table><thead><tr><th width="150">选项</th><th>描述</th></tr></thead><tbody><tr><td><strong>删除日期</strong></td><td>此 Send 将在指定的日期和时间被永久<a href="send-lifespan.md#deletion-behavior">删除</a>。默认为创建后 7 天。<strong>允许的最大值</strong>为自创建后 31 天。</td></tr><tr><td><strong>到期日期</strong></td><td>此 Send 将在指定的日期和时间<a href="send-lifespan.md#expiration-behavior">到期</a>。默认为<strong>永不</strong>。</td></tr><tr><td><strong>最大访问次数</strong></td><td>在达到指定的访问次数后，此 Send 将被<a href="send-lifespan.md#maximum-access-count-behavior">禁用</a>。默认为不指定。</td></tr><tr><td><strong>密码</strong></td><td>要求此 Send 的接收者输入<a href="send-privacy.md#send-passwords">密码</a>才能获得访问权限。</td></tr><tr><td><strong>备注</strong></td><td>输入此 Send 的私密备注，该备注仅对发送者可见。</td></tr><tr><td><strong>对接收者隐藏我的电子邮箱地址</strong></td><td>对 Send 接收者<a href="send-privacy.md#hide-email">隐藏您的电子邮箱</a>。</td></tr><tr><td><strong>禁用此 Send 则任何人无法访问它</strong></td><td>选中此复选框可阻止任何接收者访问此 Send。您仍然可以从 Send 视图中交互此 Send。</td></tr></tbody></table>

{% hint style="success" %}
本文的剩余部分将介绍如何将 Send 链接复制到剪贴板，但是您可以通过在**保存**之前勾选**保存时复制此 Send 的分享链接到剪贴板**以自动执行此操作。
{% endhint %}

对 Send 的配置满意后，请选择**保存**按钮以完成操作。

创建 Send 后，请使用 **≡选项**菜单并选择 **❐复制 Send 链接**按钮将生成的链接复制到剪贴板：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6y6TJ0P7YbMza7p90kxu6X/929e10a4eac5d842b4cf283d46a41824/2024-12-03_10-09-52.png?_a=DAJCwlWIZAAB" %}
Send 选项
{% endembed %}

复制后，与您期望的接收者分享 Send 链接。Send 是端到端加密的，因此您不必担心会将任何 Send 数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展创建一个新的 Send：

1、选择 ✈️**Send** 标签页。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**密码库**视图一样，您可以选择某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择 ✚**新增** 按钮然后选择**文本**或**文件**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2qOv6DJYX1is2zurmeVBOd/b7a99ad66a86a39cec32f4136209e49c/2024-12-03_10-14-26.png?_a=DAJCwlWIZAAB" %}
新建 Send
{% endembed %}

3、在**新建 Send** 对话框中，为 Send 指定如下内容：

* **名称**：为此 Send 指定一个可识别的有含义的名称。
* 某些选项取决于您选择的是**文本**还是**文件**：

<table><thead><tr><th width="150">类型</th><th>步骤</th></tr></thead><tbody><tr><td><strong>文本</strong></td><td><p>在输入框中输入或粘贴所需的文本。切换<strong>访问 Send 时，默认隐藏文本</strong>选项，将要求接收者在打开 Send 时<a href="send-privacy.md">切换可见性</a>。加密后的发送内容不得超过 1000 个字符。</p><p></p><p>保存时，Send 文本的字符数会因加密而增加，这意味着一个 700 个字符的 Send 文本在与 Bitwarden 接触时会增加到 ~1,000 个字符，从而触发错误。根据经验，加密后字符数会增加 30-50%。</p></td></tr><tr><td><strong>文件</strong></td><td>选择<strong>选择文件</strong>按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 500 MB（移动端是 100 MB）。（<strong>要求高级会员</strong> &#x26; 已验证电子邮箱）</td></tr></tbody></table>

默认情况下，Send 将在其创建后的 7 天后删除。您可以使用 **⮟选项**菜单配置此选项及其他选项（请参阅第 4 步），否则，点击**保存**以完成创建 Send。

{% hint style="info" %}
要在使用 Firefox 或 Safari 浏览器扩展时创建 Send，必须在侧边栏打开扩展或选择弹出按钮：

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1cbJy0jLBmSQmRumvYzVwp/be8132e558dd91c6d282f08a02e2d5fa/2024-12-02_14-10-52.png?_a=DAJCwlWIZAAB" alt="" data-size="original">
{% endhint %}

4、选择 **⮟选项**菜单，根据需要配置以下选项：

<table><thead><tr><th width="150">选项</th><th>描述</th></tr></thead><tbody><tr><td><strong>删除日期</strong></td><td>此 Send 将在指定的日期和时间被永久<a href="send-lifespan.md#deletion-behavior">删除</a>。默认为创建后 7 天。<strong>允许的最大值</strong>为自创建后 31 天。</td></tr><tr><td><strong>到期日期</strong></td><td>此 Send 将在指定的日期和时间<a href="send-lifespan.md#expiration-behavior">到期</a>。默认为<strong>永不</strong>。</td></tr><tr><td><strong>最大访问次数</strong></td><td>在达到指定的访问次数后，此 Send 将被<a href="send-lifespan.md#maximum-access-count-behavior">禁用</a>。默认为不指定。</td></tr><tr><td><strong>密码</strong></td><td>要求此 Send 的接收者输入<a href="send-privacy.md#send-passwords">密码</a>才能获得访问权限。</td></tr><tr><td><strong>备注</strong></td><td>输入此 Send 的私密备注，该备注仅对发送者可见。</td></tr><tr><td><strong>对接收者隐藏我的电子邮箱地址</strong></td><td>对 Send 接收者<a href="send-privacy.md#hide-email">隐藏您的电子邮箱</a>。</td></tr></tbody></table>

满意后，选择**保存**完成 Send 的创建。您可以立即从下一个屏幕复制 Send 链接，也可以稍后从 Send 视图中复制：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1lLksK7QbomKPRueO41c4d/a8c2a62a2e918763c89522a9dc35d7bb/send-be-share.png?fm=webp&h=271&q=50&w=392" %}
复制 Send 链接
{% endembed %}

复制后，与您期望的接收者分享 Send 链接。Send 是端到端加密的，因此您不必担心会将任何 Send 数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="桌面端" %}
要从桌面应用程序创建一个新的 Send：

1、选择 ✈️**Send** 标签页。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**我的密码库**视图一样，您可以通过点击某一可用的**类型**来筛选 Send。
{% endhint %}

2、选择位于中间列下方的 ✚**添加** 图标：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2O01p5FyMpUhlhi5bAq7mH/b730e0a73a8d869ae4fbcd9e6aef20fa/send-desktop-add.png?fm=webp&h=681&q=50&w=1136" %}
桌面应用程序中的 Send 视图
{% endembed %}

3、在右边栏中，为 Send 指定如下内容：

* **名称**：为此 Send 指定一个可识别的有含义的名称。
*   **类型**：指定此 Send 是**文本**还是**文件**：

    | **类型** | **描述**                                                                                   |
    | ------ | ---------------------------------------------------------------------------------------- |
    | **文本** | 在输入框中输入或粘贴所需的文本。切换**访问 Send 时，默认隐藏文本**选项，将要求接收者在打开 Send 时[切换可见性](send-privacy.md)。       |
    | **文件** | 点按**选择文件**按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 100 MB（移动端为 100 MB）。（**需要高级会员** & 已验证电子邮件） |

默认，Send 将在其创建后的 7 天后删除。您可以使用 **⮟选项**菜单配置此选项及其他选项（请参阅第 4 步），否则，点击**保存**以完成创建 Send。

4、点击 **⮟选项**菜单，根据需要配置以下选项：

| 选项                     | 描述                                                                                            |
| ---------------------- | --------------------------------------------------------------------------------------------- |
| **删除日期**               | 此 Send 将在指定的日期和时间被永久[删除](send-lifespan.md#deletion-behavior)。默认为创建后 7 天。**允许的最大值**为自创建后 31 天。 |
| **到期日期**               | 此 Send 将在指定的日期和时间[到期](send-lifespan.md#expiration-behavior)。默认为**永不**。                        |
| **最大访问次数**             | 在达到指定的访问次数后，此 Send 将被[禁用](send-lifespan.md#maximum-access-count-behavior)。默认为不指定。             |
| **密码**                 | 要求此 Send 的接收者输入[密码](send-privacy.md#send-passwords)才能获得访问权限。                                  |
| **备注**                 | 输入此 Send 的私密备注，该备注仅对发送者可见。                                                                    |
| **对接收者隐藏我的电子邮件地址**     | 对 Send 接收者[隐藏您的电子邮件](send-privacy.md#hide-email)。                                             |
| **禁用此 Send 以阻止任何人访问它** | 选中此复选框可阻止任何接收者访问此 Send。您仍然可以从 Send 视图中交互此 Send。                                               |

{% hint style="success" %}
本文的剩余部分将介绍如何将 Send 链接复制到剪贴板，但是您可以通过在**保存**之前勾选**保存时复制此 Send 的分享链接到剪贴板**以自动执行此操作。
{% endhint %}

对 Send 的配置满意后，请选择**保存**按钮以完成操作。

创建 Send 后，选择 **❐复制链接**按钮将生成的链接复制到剪贴板：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2PKATwmgbJ62JneH274vho/bc4ca798b95d254b3b4823a5f37d93b3/send-desktop-share.png?fm=webp&h=681&q=50&w=1136" %}
复制 Send 链接
{% endembed %}

复制后，与您期望的接收者分享 Send 链接。Send 是端到端加密的，因此您不必担心会将任何 Send 数据暴露给您使用的任何中间通信服务。
{% endtab %}

{% tab title="移动端" %}
要从移动应用程序创建一个新的 Send：

1、点击 ✈️**Send** 标签。

{% hint style="info" %}
该视图将列出尚未达到[删除日期](send-lifespan.md#deletion-date)的所有 Send。与**我的密码库**视图一样，您可以通过点击某一可用的**类型**来筛选 Send。
{% endhint %}

2、点击 ✚**添加**图标：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5vHsSA3o9O735MitlnOPVr/b49ca097df2897f677536f9494435768/send-mobile.png?fm=webp&h=686&q=50&w=675" %}
iOS 和 Android 上的 Send 视图
{% endembed %}

3、在**添加 Send** 视图中，为 Send 指定如下内容：

*   **类型**：指定此 Send 是**文本**还是**文件**：

    | **类型** | **描述**                                                                                      |
    | ------ | ------------------------------------------------------------------------------------------- |
    | **文本** | 在输入框中输入或粘贴所需的文本。切换**访问 Send 时，默认隐藏文本**选项，将要求接收者在打开 Send 时[切换可见性](send-privacy.md)。          |
    | **文件** | 点按**选择文件**按钮，然后浏览用于 Send 的文件。每个 Send 的最大文件大小为 100 MB（其他客户端为 500 MB）。 （**需要高级会员** & 已验证电子邮件） |
* **名称**：为此 Send 指定一个可识别的有含义的名称。

默认，Send 将在其创建后的 7 天后删除。您可以使用 **⮟选项**菜单配置此选项及其他选项（请参阅第 4 步），否则，点击**保存**以完成创建 Send。

4、点击 **⮟选项**菜单，根据需要配置以下选项：

| 选项                     | 描述                                                                                            |
| ---------------------- | --------------------------------------------------------------------------------------------- |
| **删除日期**               | 此 Send 将在指定的日期和时间被永久[删除](send-lifespan.md#deletion-behavior)。默认为创建后 7 天。**允许的最大值**为自创建后 31 天。 |
| **到期日期**               | 此 Send 将在指定的日期和时间[到期](send-lifespan.md#expiration-behavior)。默认为**永不**。                        |
| **最大访问次数**             | 在达到指定的访问次数后，此 Send 将被[禁用](send-lifespan.md#maximum-access-count-behavior)。默认为不指定。             |
| **密码**                 | 要求此 Send 的接收者输入[密码](send-privacy.md#send-passwords)才能获得访问权限。                                  |
| **备注**                 | 输入此 Send 的私密备注，该备注仅对发送者可见。                                                                    |
| **对接收者隐藏我的电子邮件地址**     | 对 Send 接收者[隐藏您的电子邮件](send-privacy.md#hide-email)。                                             |
| **禁用此 Send 以阻止任何人访问它** | 选中此复选框可阻止任何接收者访问此 Send。您仍然可以从 Send 视图中交互此 Send。                                               |

{% hint style="success" %}
在您点击**保存**之前切换**保存时分享**选项将打开您设备上的共享菜单，以便您可以快速分享您的 Send 链接。
{% endhint %}

对 Send 的配置满意后，请选择**保存**按钮以完成操作。

创建 Send 后，点击菜单图标（**≡** 或 **⋯**）然后点击**分享链接**选项：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6WZTQUop3KXnQKoGqgVzgu/a7a9406e21506e231e2daf13334761e9/send-share-mob.png?fm=webp&h=686&q=50&w=675" %}
复制 Send 链接
{% endembed %}

{% hint style="info" %}
如果您使用的是 iOS，您还可以直接从 iOS [共享菜单](https://developer.apple.com/design/human-interface-guidelines/ios/extensions/sharing-and-actions/)分享您的 Send。
{% endhint %}

将 Send 链接分享给您期望的接收者。Send 是端到端加密的，因此您不必担心会将任何 Send 数据暴露给您使用的任何中间通信服务。
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

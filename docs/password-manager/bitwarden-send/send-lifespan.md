# Send 生命周期

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/send-lifespan/)
{% endhint %}

与传统的 Bitwarden 密码库项目和文件附件不同，Send 是短暂的，**默认生命周期为 7 天**，使用[删除日期](send-lifespan.md#deletion-date)选项可设置为最长 31 天。当一个 Send 达到删除日期时，它将从 Bitwarden 系统中被清除，发送者和接收者都无法再次访问。

不同的客户端 App 允许您设置访问的额外限制，例如[到期日期](send-lifespan.md#expiration-date)和/或[最大访问次数](send-lifespan.md#maximum-access-count)选项。您也可以在任何时候手动[禁用或删除](send-lifespan.md#manually-disable-or-delete) Send。

## 删除日期 <a href="#deletion-date" id="deletion-date"></a>

默认情况下，Send 会在创建七天后自动删除。使用**删除日期**选项，您可以将其更改为一系列预先指定的选项（比如，1 小时、1 天、31 天）。

删除日期的**最大允许值为自创建后 31 天**。

### 删除行为 <a href="#deletion-behavior" id="deletion-behavior"></a>

当一个 Send 达到其配置的删除日期时：

* 对于 Send 的接收者（即任何拥有生成的链接的人），导航到 Send 链接时将显示一个界面，报告该 Send 不存在或不再可用。
* 对于发送者，一个 **🗑️等待删除**的图标将出现在 Send 旁边。Send 将在几分钟内等待删除，之后它将从 Bitwarden 系统和发送者的 Send 视图中永久删除。

{% hint style="info" %}
已删除的 Send 不会发送或存储在回收站中。一旦确认删除，您将无法访问 Send 内容。
{% endhint %}

## 到期日期 <a href="#expiration-date" id="expiration-date"></a>

{% hint style="info" %}
仅适用于网页 App 和桌面 App。
{% endhint %}

默认情况下，Send 永远不会过期，[但会被删除](send-lifespan.md#deletion-date)。使用**到期日期**选项，您可以将其更改为一系列预先指定的选项（比如，1 小时、1 天、7 天），或使用日期选择器指定一个**自定义**时间戳（或在文本输入中使用格式 `MM/DD/YYYY HH:MM AM/PM`）。

### 到期行为 <a href="#expiration-behavior" id="expiration-behavior"></a>

当一个 Send 达到指定的到期日期时：

* 对于 Send 的接收者（即任何拥有生成的链接的人），导航到 Send 链接时将显示一个界面，报告该 Send 不存在或不再可用。
* 对于发送者，一个 **🕘到期**图标将出现在 Send 旁边。在 Send 视图中，发送者仍可访问该 Send，直到达到指定的删除日期。

## 限制查看（或最大访问次数） <a href="#limit-views-or-maximum-access-count" id="limit-views-or-maximum-access-count"></a>

对于所有 Send，**当前查看次数**计数器将跟踪 Send 链接被访问的次数：

{% embed url="https://bitwarden.com/assets/0OzPRjLVfEDJ3EIZC90Cp/5f096d609bcd79b29d44c12f6073a2fa/send_limit.png?w=705&fm=avif" %}
当前查看次数计数器
{% endembed %}

您可以使用**限制查看**字段来指定查看限制。

### 最大访问次数行为 <a href="#maximum-access-count-behavior" id="maximum-access-count-behavior"></a>

当一个 Send 达到其指定的最大访问次数（或查看次数）时：

* 对于 Send 的接收者（即任何拥有生成的链接的人），导航到 Send 链接时将显示一个界面，报告该 Send 不存在或不再可用。
* 对于发送者，一个 **🚫达到最大访问次数**图标将出现在 Send 旁边。发送者仍可访问该 Send，直到达到指定的**删除日期**。

{% hint style="success" %}
**当前访问次数**（或**查看**）计数器的含义：

* 对于文本 Send，表示链接被访问的次数
* 对于文件 Send，表示内容被下载的次数
{% endhint %}

## 手动禁用或删除 <a href="#manually-disable-or-delete" id="manually-disable-or-delete"></a>

可以从任何 Bitwarden App 中手动禁用或删除 Send：

{% tabs %}
{% tab title="网页 App" %}
### 从网页 App 禁用 <a href="#disable-from-the-web-vault" id="disable-from-the-web-vault"></a>

要从网页 App 禁用 Send，请打开**编辑 Send** 视图，展开**选项**，然后勾选**禁用此 Send 以阻止任何人访问它**复选框。您可以随时取消选中此框以重新启用对此 Send 的访问。

Send 被禁用后：

* 对于 Send 的接收者（即任何拥有已生成的链接的人），导航到 Send 链接时将显示一个界面，报告该 Send 不存在或不再可用。
* 对于发送者，一个 **⚠️已禁用**图标将出现在 Send 旁边。在 Send 视图中，发送者仍可访问该 Send，直到达到指定的**删除日期**。

### 从网页 App 删除 <a href="#delete-from-the-web-vault" id="delete-from-the-web-vault"></a>

要从网页 App 删除 Send，请使用 **≡选项**菜单然后选择 **🗑️删除**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6y6TJ0P7YbMza7p90kxu6X/929e10a4eac5d842b4cf283d46a41824/2024-12-03_10-09-52.png?_a=DAJCwlWIZAAB" %}
Send 选项
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
### 从浏览器扩展删除 <a href="#delete-from-browser-extensions" id="delete-from-browser-extensions"></a>

要从浏览器扩展删除 Send，请选择在您要删除的 Send 旁边的 🗑️**回收站**图标：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/74CotzsfAWKjUQkXfuu7zq/83dfe90f44893fc674a980d884ddff60/2024-12-03_10-39-04.png?_a=DAJCwlWIZAAB" %}
从浏览器扩展删除 Send
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
### 从桌面 App 禁用 <a href="#disable-from-desktop-apps" id="disable-from-desktop-apps"></a>

要从桌面应 App 禁用 Send，请打开**编辑 Send** 视图并勾选**禁用此 Send 以阻止任何人访问它**复选框。您可以随时取消选中此框以重新启用对此 Send 的访问。

{% embed url="https://bitwarden.com/assets/49ar4y0apFFvUDIksGIr2C/87434a037bba73db72b85f1b21b75dec/sned-lifespan-1.png?w=1100&fm=avif" %}
从桌面 App 禁用 Send
{% endembed %}

Send 被禁用后：

* 对于 Send 的接收者（即任何拥有生成的链接的人），导航到 Send 链接时将显示一个界面，报告该 Send 不存在或不再可用。
* 对于发送者，一个 **⚠️已禁用**图标将出现在 Send 旁边。在 Send 视图中，发送者仍可访问该 Send，直到达到指定的**删除日期**。

### 从桌面 App 删除 <a href="#delete-from-desktop-apps" id="delete-from-desktop-apps"></a>

要从桌面 App 删除 Send，请打开**编辑 Send** 视图并选择 🗑️**删除**图标：

{% embed url="https://bitwarden.com/assets/12eLcz2aoBkcDRGS3U1jzP/1fb26cbaf36ce8cf3fa583b550d00dd6/send-lifespan-2.png?w=1100&fm=avif" %}
从桌面 App 删除 Send
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
### 从移动 App 删除 <a href="#delete-from-mobile-apps" id="delete-from-mobile-apps"></a>

要从移动 App 删除 Send，点击 **⋯**&#x9009;项菜单然后点击**删除**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4jWcljHXWnKZcSZZmVNyQo/af2acd968efa16f42b75b04b875d666d/2025-01-22_10-05-07.png?_a=DAJCwlWIZAAB" %}
从移动 App 删除 Send
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
### 从 CLI 禁用 <a href="#disable-from-the-cli" id="disable-from-the-cli"></a>

要从 CLI 禁用 Send，您需要使用 `edit` 命令将 `"disabled":false` 键值对更改为 `"disabled":true`，例如：

```batch
bw send get <id> | jq '.disabled=true' | bw encode | bw send edit
```

建议阅读 [CLI 上的 Send](send-from-cli.md)，以获取有关在 CLI 上使用 Send 的完整信息。

### 从 CLI 删除 <a href="#delete-from-the-cli" id="delete-from-the-cli"></a>

要从 CLI 删除 Send，请使用 `delete` 命令，并将 Send 的唯一 `id` 作为参数：

```batch
bw send delete <id>
```

建议阅读 [CLI 上的 Send](send-from-cli.md)，以获取有关在 CLI 上使用 Send 的完整信息。
{% endtab %}
{% endtabs %}

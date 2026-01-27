# 自动填充支付卡 & 身份

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-card-id/)
{% endhint %}

Bitwarden 不止于[自动填充用户名和密码](../autofill-from/autofill-from-browser-extensions.md)！某些 Bitwarden App 可以自动填充[支付卡](../../your-vault/vault-items/vault-items.md#zhi-fu-ka)和[身份信息](../../your-vault/vault-items/vault-items.md#shen-fen)，以简化网上购物、账户创建等操作。对于组织成员，策略可能会[阻止使用支付卡项目](../../../admin-console/oversight-visibility/enterprise-policies.md#remove-card-item-type)，因此也就无法自动填充支付卡。

{% hint style="info" %}
目前，自动填充支付卡适用于浏览器扩展和 Android。自动填充身份信息仅适用于浏览器扩展。
{% endhint %}

## 设置支付卡 & 身份自动填充 <a href="#set-up-card-and-identity-autofill" id="set-up-card-and-identity-autofill"></a>

{% hint style="success" %}
在 Android 上，自动填充支付卡不需要任何[基线自动填充设置](../autofill-from/autofill-from-android.md)以外的设置。以下说明仅适用于浏览器扩展。
{% endhint %}

您可以使用**设置** → **自动填充**菜单中的四个设置，从自动填充建议和内嵌自动填充菜单中添加或移除支付卡：

* **将身份显示为建议**：在内嵌自动填充菜单中包含身份。这要求**在表单字段上显示自动填充建议**选项已打开。
* **将支付卡显示为建议**：在内嵌自动填充菜单中包含卡片。这要求**在表单字段上显示自动填充建议**选项已打开。
* **在密码库视图中始终将支付卡显示为自动填充建议**：在密码库视图的建议中包含支付卡。可以使用**填充**按钮自动填充。
* **在密码库视图中始终将身份显示为自动填充建议**：在密码库视图的建议中包含身份。可以使用**填充**按钮自动填充。

## 自动填充支付卡 & 身份 <a href="#autofilling-cards-and-identities" id="autofilling-cards-and-identities"></a>

{% tabs %}
{% tab title="浏览器扩展" %}
### 使用内嵌菜单 <a href="#using-the-inline-menu" id="using-the-inline-menu"></a>

要使用内嵌自动填充菜单启用支付卡和身份自动填填充功能，请按照上一章节所述打开**将身份显示为建议**和**将支付卡显示为建议**选项。**在表单字段显示自动填充建议**选项也必须打开。

打开后，当您点击表单时，您存储的支付卡和身份信息就会显示出来。选择填充表格信息时希望使用的支付卡或身份信息：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2IZKkQJjPBvDgT3Z6IZMoR/2d00c6b6789b78addd486fd974720ddd/2024-08-13_13-10-20.png?_a=DAJAUVWIZAAB" %}
内嵌自动填充支付卡
{% endembed %}

{% hint style="info" %}
如果您的 Bitwarden 密码库中没有已保存的支付卡或身份信息，您可以在填写信息后从内嵌菜单中选择 ✚**新增支付卡** / **新增身份**，以将新项目保存到您的 Bitwarden 密码库中。
{% endhint %}

### 使用填充按钮 <a href="#using-the-fill-button" id="using-the-fill-button"></a>

要使用填充按钮自动填充支付卡或身份信息，请按照上一章节所述打开**在密码库视图中将支付卡显示为自动填充建议**和**在密码库视图中将身份显示为自动填充建议**选项。

打开后，您的支付卡和身份信息将出现在**密码库**视图的**自动填充建议**部分。选择**填充**按钮进行自动填充：

{% embed url="https://bitwarden.com/assets/78MbqVeoL6Juo7E5cMUUNh/57b31fd7fd315aa6334125bf168fb67d/Card___identity_fill.png?w=758&fm=avif&q=80" %}
自动填充支付卡和身份
{% endembed %}

该浏览器扩展会查找网页上与支付卡或身份信息相对应的任何字段，并自动填充。

### 使用上下文菜单 <a href="#using-the-context-menu" id="using-the-context-menu"></a>

{% hint style="info" %}
使用上下文菜单自动填充目前在 Safari 浏览器扩展中不可用。
{% endhint %}

无需打开浏览器扩展程序，您就可以通过右键点击输入字段然后使用 **Bitwarden** → **自动填充**选项来自动填充支付卡和身份。如果您在尝试执行此操作时密码库已锁定，则会打开一个窗口，提示您解锁。解锁后，浏览器扩展程序将自动继续自动填充您的信息。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6GKKvIe7GwwOBtp9gmh862/4d39f59a8a862bb83d53e50f9f68d107/2024-12-03_09-12-06.png?_a=DAJCwlWIZAAB" %}
浏览器扩展上下文菜单
{% endembed %}

### 使用键盘快捷键 <a href="#using-keyboard-shortcuts" id="using-keyboard-shortcuts"></a>

可以使用键盘快捷键自动填充支付卡和身份。要使用此功能，必须为支付卡和身份手动设置键盘快捷键：

1、打开 Bitwarden 浏览器扩展然后选择 **⚙️设置**。

2、从设置菜单中选择**自动填充**，然后选择**管理快捷键**以打开浏览器自动填充设置窗口。

3、在 Bitwarden Password Manager 键盘快捷键中，**为当前网站自动填充最后一次使用的支付卡**和**为当前网站自动填充最后一次使用的身份**配置您喜欢的键盘快捷键。
{% endtab %}

{% tab title="Android App" %}
在 Android 上，支付卡将自动以建议的形式内嵌（在您的键盘中），或以弹出的形式出现在字段上，具体取决于哪种自动填充方法处于激活状态。例如，以弹出形式显示：

{% embed url="https://bitwarden.com/assets/2ekny75ulY7xoyqz80Kz1z/f3954ac976db5283aa064efc6a78cc5e/2025-08-12_10-32-44.png?w=727&fm=avif&q=80" %}
Android 支付卡弹出
{% endembed %}
{% endtab %}
{% endtabs %}

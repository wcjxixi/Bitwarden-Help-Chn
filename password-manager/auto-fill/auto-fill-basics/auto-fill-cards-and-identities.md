# 自动填充支付卡和身份

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-card-id/)
{% endhint %}

Bitwarden 不止于[自动填充用户名和密码](auto-fill-logins-in-browser-extensions.md)！Bitwarden 浏览器扩展可以使用[独特的选项卡视图](auto-fill-logins-in-browser-extensions.md)自动填充[支付卡](../../../your-vault/vault-items.md#zhi-fu-ka)和[身份信息](../../../your-vault/vault-items.md#shen-fen)，以简化网上购物、账户创建等操作。

{% hint style="info" %}
目前，自动填充支付卡和身份的功能仅适用于浏览器扩展。Android 和 iOS 等移动平台不支持此类型的自动填充功能。
{% endhint %}

## 使用选项卡视图 <a href="#using-the-tab-view" id="using-the-tab-view"></a>

要使用**选项卡**视图自动填充支付卡和身份：

1、打开浏览器扩展，导航至 **📁选项卡**视图。

除非您[从该视图中隐藏了支付卡和/或身份](auto-fill-cards-and-identities.md#hide-cards-and-identities)，否则所有支付卡和身份将在此处与所有[匹配的登录项目](../../../auto-fill/using-uris.md)一起列出。

2、选择您想要自动填充的支付卡或身份：

{% embed url="https://bitwarden.com/_gatsby/image/204facef2242011f249823040697ee30/99e72e1b1d16b019d065b613ce37685e/Screen%20Shot%202022-05-19%20at%209.31.25%20AM.webp?eu=de8a03e5b59badd60c6aa3d56f70313be53a01feac5833d76961e1a919afcbd422f21104229629b37e610e88dae044b865c37a681fefd6d994e911f5ef66a80905d25ab863bb250f5828c1f9b7fc5011629e5e1ce1c0c217bc342f85b2e6f46e4a144a7aeb39edc5afb76b31f49c2870b4e5e0746494a325a71541529e5c74a43ff3eb8d416895a7cd5fbe8393ca719fcff8280512dcf560747f454c50ef7fbda0e45170392c475964cfa60c9132c3b135147e400d1d56a23955b30da4285ec1e4f9a340d97f66e0a1a66034e9cab083ec04ae2f1996b239e9dc6c&a=w%3D850%26h%3D612%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.760Z" %}
自动填充身份信息
{% endembed %}

浏览器扩展将在网页上找到任何映射到支付卡或身份信息的字段，并自动填充它们。

## 使用上下文菜单 <a href="#using-the-context-menu" id="using-the-context-menu"></a>

{% hint style="info" %}
目前在 Safari 浏览器扩展中不可用。
{% endhint %}

无需打开浏览器扩展程序，您就可以通过右键点击输入字段然后使用 **Bitwarden** → **自动填充**选项来自动填充支付卡和身份。如果您在尝试执行此操作时密码库已锁定，则会打开一个窗口，提示您解锁。解锁后，浏览器扩展程序将自动继续自动填充您的信息。

{% embed url="https://bitwarden.com/_gatsby/image/3aaa187916ae95fab12c894d1b713291/ceb511945f732fb3770dfc36b5a08ded/Screenshot%202023-10-18%20at%2010.07.46%20AM.webp?eu=8d8659eeb59af984096ca9d63d70683ce23855acf65230d13f62e4ab4aafca8320f11e0475967ae37e69528a85e840b332cf7b331deb84d996bd4ea7ea34ac5d00825abd34b07802057dc2f7b7a104416b94125ca3d79d5ca26b7582e2b0e6761d534a28fe29ebd2e5fa3166badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec33550c375921b82acce2f57b037d69490c6896a75ec57ec0b269143572565f06a63633d754f33832c6b5f8f208df292de2a1c835768297b1e3be58f97f28a49778eded397a0c0eb112ada17affbd354261802ae4954bac07035a31ff02c97a77&a=w%3D850%26h%3D453%26fm%3Dwebp%26q%3D75&cd=2023-11-01T12%3A58%3A48.183Z" %}
浏览器扩展上下文菜单
{% endembed %}

## 使用内嵌菜单 <a href="#using-the-inline-menu" id="using-the-inline-menu"></a>

使用内嵌自动填充菜单自动填充支付卡和身份。要启用内嵌自动填充菜单：

1、登录并解锁 Bitwarden [浏览器扩展](../../../getting-started/getting-started-browserext.md)。

2、选择 **⚙️设置** → **自动填充**，然后定位到「在表单字段上显示自动填充菜单」下拉列表。选择您喜欢的自动填充菜单行为。

3、我们建议您禁用浏览器的自动填充选项（如果已启用）。[了解更多](../../../auto-fill/disable-a-browsers-built-in-password-manager.md)。

启用内嵌自动填充设置后，当您点击某个表单时，将显示您存储的支付卡和身份信息。选择您在填写此表单信息时要使用的支付卡或身份：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2IZKkQJjPBvDgT3Z6IZMoR/2d00c6b6789b78addd486fd974720ddd/2024-08-13_13-10-20.png?_a=DAJAUVWIZAAB" %}
内嵌自动填充支付卡
{% endembed %}

{% hint style="info" %}
如果您的 Bitwarden 密码库中没有已保存的支付卡或身份信息，您可以在填写信息后从内嵌菜单中选择 ✚**新增支付卡** / **新增身份**，以将新项目保存到您的 Bitwarden 密码库中。
{% endhint %}

## 使用键盘快捷键 <a href="#using-keyboard-shortcuts" id="using-keyboard-shortcuts"></a>

可以使用键盘快捷键自动填充支付卡和身份。要使用此功能，必须为支付卡和身份手动设置键盘快捷键：

1、打开 Bitwarden 浏览器扩展然后选择 **⚙️设置**。

2、从设置菜单中选择**自动填充**，然后选择**自动填充键盘快捷键**以打开浏览器自动填充设置窗口。

3、在 Bitwarden 密码管理器键盘快捷键中，**为当前网站自动填充最后一次使用的支付卡信息**和**为当前网站自动填充最后一次使用的身份信息**配置您喜欢的键盘快捷键。

## 隐藏支付卡和身份 <a href="#hide-cards-and-identities" id="hide-cards-and-identities"></a>

如果您不希望将支付卡和身份用于自动填充，则可以禁止它们在 **📁选项卡**视图中显示：

1. 在浏览器扩展中，打开 **⚙️设置**选项卡，然后打开**自动填充**。
2. 向下滚动并取消勾选**在标签页上显示支付卡**和/或**标签页上显示身份**复选框。

# Bitwarden Authenticator

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-authenticator/)
{% endhint %}

Bitwarden Authenticator 是一款移动端的身份验证应用程序，可用于验证使用双因素身份验证 (2FA) 的网站和应用程序的身份。Bitwarden Authenticator 生成 5-10 位基于时间的一次性密码 (TOTP)，默认使用 SHA-1 并每 30 秒轮换一次。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4fMWMI0YBJQybhhyOlV0Zb/a9914cb08081d0dc424f2174dc3e62c7/bitwarden-authenticator-app.png?_a=BAJFJtWIB" %}
Bitwarden Authenticator
{% endembed %}

## 添加代码 <a href="#add-codes" id="add-codes"></a>

在您尝试为其设置 2FA 的网站或 App 中，导航至其 2FA 界面，然后**扫描二维码**或**手动添加代码**：

{% tabs %}
{% tab title="扫描二维码" %}
1. 点击 ✚图标。
2. 将相机对准二维码。扫描将自动进行。
{% endtab %}

{% tab title="手动添加代码" %}
1. 点击 ✚图标。
2. 点击屏幕底部的**手动输入密钥**。
3. 在**名称**字段中输入网站或应用程序的名称。
4. 输入网站或应用程序提供的**验证器密钥**。某些服务将此称为「机密密钥」或「TOTP 种子」。
{% endtab %}
{% endtabs %}

{% hint style="success" %}
当您有新的移动设备时，您可以从 Bitwarden Authenticator 导出数据，然后将数据导入新设备。[了解方法](import-and-export.md)。
{% endhint %}

### 编辑项目 <a href="#edit-an-item" id="edit-an-item"></a>

长按验**证码**界面上的条目可对其进行更改。除了更改已添加的名称和机密之外，您还可以：

* 将**用户名**添加到项目中。当您在同一网站拥有多个账户并且每个账户需要单独的验证码时，请使用此字段。
* 更改用于生成代码的**算法**。Bitwarden Authenticator 默认使用 SHA-1。
* 更改代码的**刷新周期**。Bitwarden Authenticator 默认使用 30 秒。
* 更改代码的**位数**。Bitwarden Authenticator 默认使用 6 位数字。

{% hint style="info" %}
**算法**、**刷新周期**和**位数**由您使用验证码的网站决定。除非该网站要求或允许您自定义验证码行为，否则请勿更改项目的这些设置。
{% endhint %}

## 使用代码 <a href="#use-codes" id="use-codes"></a>

要在该账户的机密存储在 Bitwarden Authenticator 中后使用验证码，请打开 Bitwarden Authenticator 并点击该条目以将其验证码复制到剪贴板。然后，将验证码粘贴到您要登录的网站或应用程序的输入框中。

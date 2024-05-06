# =Bitwarden Authenticator

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-authenticator/)
{% endhint %}

Bitwarden Authenticator 是一款移动端的身份验证应用程序，可用于验证使用双因素身份验证 (2FA) 的网站和应用程序的身份。Bitwarden Authenticator 生成 5-10 位基于时间的一次性密码 (TOTP)，默认使用 SHA-1 并每 30 秒轮换一次。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4fMWMI0YBJQybhhyOlV0Zb/a9914cb08081d0dc424f2174dc3e62c7/bitwarden-authenticator-app.png?_a=BAJFJtWIB" %}
Bitwarden Authenticator
{% endembed %}

## 添加代码 <a href="#add-codes" id="add-codes"></a>

在您尝试为其设置 2FA 的网站或应用程序中，导航至其 2FA 界面，然后**扫描二维码**或**手动添加代码**：

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

### 编辑项目 <a href="#edit-an-item" id="edit-an-item"></a>

## 使用代码 <a href="#use-codes" id="use-codes"></a>

## 导出数据 <a href="#export-data" id="export-data"></a>

## 常见问题 <a href="#faqs" id="faqs"></a>

问：新的 Bitwarden Authenticator 是 Bitwarden 密码管理器的一部分吗？

问：我可以使用 Bitwarden Authenticator 将 2FA 添加到我的 Bitwarden 账户吗？

问：如何将此应用设置为 iOS 上的默认验证码应用？

问：我什么时候应该使用这个独立的应用程序而不是集成的身份验证器？

问：我的数据如何存储和保护？

问：如何备份和恢复数据？

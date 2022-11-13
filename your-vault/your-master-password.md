# 主密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/master-password/)
{% endhint %}

主密码是访问密码库的主要方法。您的主密码非常重要：

* **好记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记你的主密码！**
* **强大**：您的主密码越长、越复杂、越不常见，您的密码库数据就越安全。使用我们提供的免费[**密码强度测试工具**](https://bitwarden.com/password-strength)来测试您考虑使用的密码的强度。

{% hint style="success" %}
你担心忘记您的主密码吗？这里有一些建议：

* **设置主密码提示**。设置好后，某些场景下你可以在登录界面申请主密码提示电子邮件。确保使用只有您自己能理解的提示。
* **指定一个**[**可信紧急联系人**](../security/emergency-access.md)。具有高级访问权限的用户可以在紧急情况下将密码库的访问权限授予朋友或家人。
{% endhint %}

## 更改主密码 <a href="#change-your-master-password" id="change-your-master-password"></a>

如果您知道当前的主密码，您可以通过[网页密码库](../getting-started/getting-started-webvault.md)更改它：

{% hint style="info" %}
如果您不知道主密码，请参阅[我忘记了主密码](i-forgot-my-master-password.md)**。**
{% endhint %}

1、在您的网页密码库中，选择配置文件图标并从下拉菜单中选择**帐户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F74BqYDU6qE9evz6wEz8K7Y%2F773eec1c0b00e00db4dedd3456e9a3f9%2FScreen_Shot_2022-05-13_at_10.34.10_AM.png&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.199Z" %}
账户设置
{% endembed %}

2、从帐户设置菜单中，选择**安全**页面然后选择**主密码**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/ccf1a90359236d79a3ee54a50831f079/645c0bfa3fe45223b54abb8b7c2aff65/Screen%20Shot%202022-05-16%20at%209.55.28%20AM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F2Svv0PwlH9i7SSK73dlv9A%2F799471ba82983694fb8ed0d9364b30c3%2FScreen_Shot_2022-05-16_at_9.55.28_AM.png&a=w%3D787%26h%3D402%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.271Z" %}
更改主密码
{% endembed %}

3、输入您的**当前主密码**。

4、输入并确认您的**新主密码**。

{% hint style="warning" %}
除非您完全了解其后果和所需的后续步骤，否则请不要选中**同时轮换帐户加密密钥**复选框。[了解更多](../security/account-encryption-key.md)。
{% endhint %}

5、选择**更改主密码**按钮。

更改主密码将会自动注销网页密码库会话，并要求您使用新的主密码重新登录。当前已登录的客户端应用程序可能保持活动状态长达一小时，但最终也会要求您使用新的主密码重新登录。

## 我忘记了主密码 <a href="#i-forgot-my-master-password" id="i-forgot-my-master-password"></a>

了解如果您[忘记了主密码](i-forgot-my-master-password.md)该怎么做。

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

现在您已经创建了**好记**且**强大**的主密码，我们建议：

* [通过两步登录进一步保护您的密码库](../two-step-login/two-step-login-methods.md)
* [启用紧急访问](../security/emergency-access.md)（需要付费）

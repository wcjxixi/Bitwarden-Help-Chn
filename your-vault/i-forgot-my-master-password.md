# 忘记主密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/forgot-master-password/)
{% endhint %}

Bitwarden 采用零知识加密技术。这意味着 Bitwarden 对您的主密码一无所知、也没有办法找回或重置您的主密码。但是，您可以采取一些措施来尝试重新获取对您的账户的访问权限：

1. 当您尝试登录时，请检查是否[选择了正确的服务器](../security/server-geographies.md#choose-your-cloud-server)。Bitwarden 数据区域是独立的，您的账户只存在于最初创建它的区域中。在尝试以下步骤之前，选择您的服务器是必要的。
2. 尝试在另外一台设备上登录。
3. [设置主密码提示](https://vault.bitwarden.com/#/hint)。如果您设置了提示，当您与此页面交互时，提示将通过电子邮件发送到您的收件箱。如果你没有设置提示，则会收到一封报告此情况的电子邮件。
4. 如果您启用了[紧急访问](../security/emergency-access.md)，请联系您信任的紧急联系人以重新获得对您的密码库的读取或接管访问权限。
5. 如果您的组织启用了[账户恢复](../organizations/admin-password-reset.md)功能，请联系管理员重置您的主密码。
6. 如果您用于访问网页 App 的浏览器是已知设备（即已通过[使用设备登录](log-in-with-device.md)注册过），则可以通过网页 App 访问您的账户。
7. 如果您的 Bitwarden 账户已经注册了启用加密（PRF）的[通行密钥登录](../my-account/log-in-and-unlock/log-in-with-passkeys.md)，您可以使用该通行密钥登录。

如果以上选项都不能让您访问您的账户，您需要删除您的账户并重新创建一个新的账户：

{% hint style="danger" %}
删除您的账户将删除其中存储的所有个人拥有的密码库项目，这将包括所有已保存的附件。

在删除您的账户之前，请检查您是否登录了任何 Bitwarden 移动应用程序、浏览器扩展程序或桌面应用程序。如果是，请花一些时间手动对您的数据进行分类，以便将其重新添加到新的账户中。
{% endhint %}

1. 导航至 [https://vault.bitwarden.com/#/recover-delete](https://vault.bitwarden.com/#/recover-delete) 或 [https://vault.bitwarden.eu/#/recover-delete](https://vault.bitwarden.eu/#/recover-delete)。
2. 输入您账户关联的电子邮箱地址然后选择**提交**。
3. 在您的电子邮箱收件箱中，打开邮件并确认您要删除此 Bitwarden 账户。

{% hint style="info" %}
如果您是某个组织的唯一所有者，尝试删除您的账户时会出现错误信息。请联系[支持团队](https://bitwarden.com/contact/)以获得删除组织的协助。
{% endhint %}

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

如果您删除了与高级订阅相关联的 Bitwarden 账户，请[联系我们](https://bitwarden.com/contact/)，我们会将您现有的订阅重新应用到新的账户中。

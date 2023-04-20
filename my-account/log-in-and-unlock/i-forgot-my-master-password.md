# 忘记主密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/forgot-master-password/)
{% endhint %}

Bitwarden 使用零知识加密运行。这意味着 Bitwarden 不知道、也没有办法找回或重置您的主密码。但是，您可以采取一些措施来尝试重新获取对您的密码库的访问权限：

1. 尝试在另外一台设备上登录。
2. [设置主密码提示](https://vault.bitwarden.com/#/hint)。如果您设置了，提示将通过电子邮件发送到您的收件箱。如果你没有设置提示，你会收到一封邮件来告知您。
3. 如果您启用了[紧急访问](../more/emergency-access.md)，请联系您信任的紧急联系人以重新获得对您的密码库的读取或接管访问权限。
4. 如果您的组织使用了[管理员密码重置](../../admin-console/user-management/admin-password-reset.md)，请联系管理员重置您的主密码。

如果以上选项都不能让您访问您的密码库，您需要删除您的帐户并重新创建一个新的帐户：

{% hint style="danger" %}
删除您的帐户将删除其中存储的所有个人拥有的密码库项目，这将包括所有已保存的附件。

在删除您的帐户之前，请检查您是否登录了任何 Bitwarden 移动应用程序、浏览器扩展程序或桌面应用程序。如果是，请花一些时间手动对您的数据进行分类，以便将其重新添加到新的帐户中。
{% endhint %}

1. 导航至 [https://vault.bitwarden.com/#/recover-delete](https://vault.bitwarden.com/#/recover-delete)。
2. 输入您帐户关联的电子邮件地址然后选择**提交**。
3. 在您的电子邮件收件箱中，打开邮件并确认您要删除此 Bitwarden 账户。

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

如果您删除了与高级订阅相关联的 Bitwarden 帐户，请[联系我们](https://bitwarden.com/contact/)，我们会将您现有的订阅重新应用到新的帐户中。

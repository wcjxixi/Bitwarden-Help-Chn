# 忘记主密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/forgot-master-password/)
{% endhint %}

Bitwarden 采用零知识加密技术。这意味着 **Bitwarden 无法访问、获取或重置您的主密码**。但是，您可以采取一些措施来尝试重新获取对您的账户的访问权限：

## 检查服务器地理位置 <a href="#check-server-geography" id="check-server-geography"></a>

当您尝试登录时，请检查是否[选择了正确的服务器](../../security/server-geographies.md#choose-your-cloud-server)。Bitwarden 数据区域是独立的，您的账户只存在于最初创建它的区域中。在尝试以下步骤之前，选择您的服务器是必要的。

{% embed url="https://bitwarden.com/assets/3H5fN6yR90aKaTg7gaCruo/020b9ca668f037ed1e6450309b4041b4/2025-11-24_15-26-15.png?w=234&fm=avif" %}
服务器地理位置
{% endembed %}

## 尝试在其他设备上登录 <a href="#attempt-to-log-in-on-another-device" id="attempt-to-log-in-on-another-device"></a>

尝试在其他设备或[客户端](https://bitwarden.com/download/)（网页、桌面端、浏览器或移动端）上访问 Bitwarden：

* 如果您能够使用其他设备重新获得访问权限，请创建当前密码库数据的备份。
  * 如果您能够使用生物识别登录来登录，则可以使用它来导出现有的密码库。
  * 如果您没有设置生物识别解锁并且无法访问主密码，您可以手动复制并粘贴以创建现有密码库项目的备份。
* 尝试使用不同的或新的浏览器登录。
* 检查任何可能阻止使用浏览器扩展登录的广告拦截器设置。

## 查看主密码提示 <a href="#review-master-password-hint" id="review-master-password-hint"></a>

通过访问 [https://vault.bitwarden.com/#/hint](https://vault.bitwarden.com/#/hinthttps://vault.bitwarden.com/#/hint) 或 [https://vault.bitwarden.eu/#/hint](https://vault.bitwarden.eu/#/hinthttps://vault.bitwarden.eu/#/hint) 获取主密码提示。如果您设置了提示，提示将通过电子邮件发送到您的收件箱。如果您没有设置提示，则会收到一封报告此情况的电子邮件。

## 使用紧急访问 <a href="#use-emergency-access" id="use-emergency-access"></a>

如果您启用了[紧急访问](more-log-in-options/emergency-access.md)，请联系您信任的紧急联系人以重新获得对您的密码库的读取或接管访问权限。

## 联系管理员恢复账户 <a href="#contact-administrator-for-account-recovery" id="contact-administrator-for-account-recovery"></a>

如果您的组织启用了[账户恢复](../../admin-console/manage-members/account-recovery/about-account-recovery.md)功能，请联系管理员重置您的主密码。

## 使用已知设备登录 <a href="#log-in-with-known-device" id="log-in-with-known-device"></a>

如果您使用的浏览器已设置为已知设备（即已通过[使用设备登录](more-log-in-options/log-in-with-device.md)注册过），请从网页 App 中选择使用设备登录，您可以使用其他应用程序批准该请求。

{% embed url="https://bitwarden.com/assets/7owqaTEe9Bo05wfLRZPhn8/38f1d0334964bb3d98a430b80b9d6b95/2025-09-09_10-03-52.png?w=692&fm=avif" %}
使用设备登录
{% endembed %}

## 使用通行密钥登录（若已启用） <a href="#log-in-with-passkey-if-enabled" id="log-in-with-passkey-if-enabled"></a>

如果您的 Bitwarden 账户已经注册了启用加密（PRF）的[通行密钥登录](more-log-in-options/log-in-with-passkeys.md)，您可以使用该通行密钥登录。

## 如果这些选项均未授予您对您的账户的访问权限 <a href="#if-none-of-these-options-grant-you-access-to-your-account" id="if-none-of-these-options-grant-you-access-to-your-account"></a>

如果以上选项都不能让您访问您的账户，您需要删除您的账户并重新创建一个新的账户：

{% hint style="danger" %}
删除您的账户将删除其中存储的所有个人拥有的密码库项目，这将包括所有已保存的附件。

在删除您的账户之前，请检查您是否登录了任何 Bitwarden 移动应用程序、浏览器扩展程序或桌面应用程序。如果是，请花一些时间手动对您的数据进行分类，以便将其重新添加到新的账户中。
{% endhint %}

1. 导航至 [https://vault.bitwarden.com/#/recover-delete](https://vault.bitwarden.com/#/recover-delete) 或 [https://vault.bitwarden.eu/#/recover-delete](https://vault.bitwarden.eu/#/recover-delete)。
2. 输入您账户关联的电子邮箱地址然后选择**提交**。
3. 在您的电子邮箱收件箱中，打开来自 Bitwarden 的电子邮件然后确认您是否要删除该账户。

{% hint style="info" %}
如果您是某个组织的唯一所有者，尝试删除您的账户时会出现错误信息。请联系[支持团队](https://bitwarden.com/contact/)以获得删除组织的协助。
{% endhint %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 如果您创建了一个新账户，Bitwarden 建议使用[安全准备工具包](https://bitwarden.com/resources/bitwarden-security-readiness-kit/)来为忘记主密码等事件做好准备。
* 如果您删除了与高级订阅相关联的 Bitwarden 账户，请[联系我们](https://bitwarden.com/contact/)，我们会将您现有的订阅重新应用到新的账户中。

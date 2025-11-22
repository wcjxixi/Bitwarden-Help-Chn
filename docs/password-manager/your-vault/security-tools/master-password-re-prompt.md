# 主密码重新提示

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/master-password-re-prompt/)
{% endhint %}

对于任何[项目](../vault-items/vault-items.md)，您可在添加或编辑界面启用**主密码重新提示**选项，要求在访问或自动填充密码库中的敏感项目时验证您的[主密码](../../../account/log-in-and-unlock/your-master-password.md)：

{% embed url="https://bitwarden.com/assets/sgKb0RX5hGdrdKLmXcR0R/f78654839e18b3f474dd3e95ed0d203c/2024-12-02_14-38-06.png?w=1036&fm=avif" %}
主密码重新提示
{% endembed %}

根据所使用的 App 不同，主密码重新提示功能的行为略有差异，例如：

* 在启用该功能的网页 App、浏览器扩展和桌面 App 中，查看项目或编辑任何内容时均需重新输入主密码。
* 在移动 App 中，仅查看隐藏字段（如密码、隐藏的自定义字段、信用卡卡号）时需重新输入主密码。编辑该条目的任何内容时同样需要重新输入主密码。

未设置主密码的用户（例如使用[受信任设备 SSO](../../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md) 的组织用户）将无法使用主密码重新提示功能。此外，使用[紧急访问](../../../account/log-in-and-unlock/more-log-in-options/emergency-access.md#use-emergency-access)的受信任联系人查看受保护的密码库项目时无需重新输入主密码。

{% hint style="danger" %}
主密码重新提示**并非**一种加密机制。该功能仅作为界面层面的防护措施，技术娴熟的用户可能找到绕过它的方法。建议您在离开无人看管的设备或使用共享工作站时，**务必**保持密码库处于锁定状态。
{% endhint %}

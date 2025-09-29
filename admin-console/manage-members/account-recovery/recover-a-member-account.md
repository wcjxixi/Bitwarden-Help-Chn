# =恢复成员账户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/recover-a-member-account/)
{% endhint %}

## 恢复账户 <a href="#recover-an-account" id="recover-an-account"></a>

{% hint style="info" %}
您必须是[所有者、管理员或允许的自定义用户](about-account-recovery.md#permissions)才能重置主密码。检查本文的[权限](about-account-recovery.md#permissions)章节以了解您可以重置谁的主密码。
{% endhint %}

要重置企业组织成员的主密码：

1、在管理控制台中，导航至**成员**。

2、对于要重置其主密码的成员，请使用 **≡选项**菜单选择 **🔑恢复账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/26oD8iqDY15SNJXCJlQE71/22e66b7e11a56d99c13ac41a1236c4e7/2024-12-03_15-35-51.png?_a=DAJCwlWIZAAB" %}
恢复账户
{% endembed %}

3、在恢复账户窗口中，为用户创建一个**新密码**。如果您的组织启用了[主密码策略](../../oversight-visibility/enterprise-policies.md#master-password)，您将需要创建一个满足实施要求的密码（例如，最少 8 个字符，包含数字）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/28qKke9XJLj6nTZJjg4mK4/7b1c2c5cb2c139bf08ea4c5f65c9a02a/2024-12-03_15-38-52.png?_a=DAJCwlWIZAAB" %}
创建一个新的密码
{% endembed %}

复制新的主密码并使用安全的通讯方式联系用户，例如使用 [Bitwarden Send](../../../bitwarden-send/create-a-send.md)。

4、选择**保存**以执行账户恢复。这样做会将用户从当前会话中注销。某些客户端应用程序（比如移动 App）上的活动会话可能会保持活动长达一小时。

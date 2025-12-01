# \*添加现有组织

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/add-existing-client-org/)
{% endhint %}

{% hint style="danger" %}
自版本 2024.7.0 起，不再支持将已有组织迁移到提供商的选项。
{% endhint %}

MSP、经销商及其他已代表客户管理组织的 Bitwarden 合作伙伴，可以将现有的组织添加到他们的提供商门户。

当 Bitwarden 检测到[提供商管理员](provider-users.md#provider-user-types)的账户是**非提供商组织的所有者**时，提供商门户将显示 ✚**添加现有组织**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3Ci2yJ6edQLwkgUON38T1v/07ce5dd908d82067e95eea52c8fa3c00/Screenshot_2024-02-29_at_10.19.05_AM.png?_a=DAJCwlWIZAAB" %}
添加现有的客户
{% endembed %}

选择 ✚**添加现有组织**按钮会弹出提示您选择此组织以添加到提供商：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7beHAnPEiOIZzSp3GjXyIH/4bb717c2412ea38a26dbe53b38a26a60/Screenshot_2024-02-29_at_10.20.07_AM.png?_a=DAJCwlWIZAAB" %}
确认添加现有的客户
{% endembed %}

添加后，该组织将与所有其他客户组织一起出现在**客户**列表中。

{% hint style="success" %}
**将现有组织添加到提供商后**，您（提供商管理员和组织所有者）可以从组织中被删除。这样做将释放之前由您的账户占用的用户席位。作为提供商的成员，您将保留对客户组织的所有权限：

1. 组织可能是无所有者的，因此请向组织[添加一个备份所有者](../admin-console/manage-members/user-management.md#invite)。
2. 新的所有者被邀请、接受和确认后，请告诉他们[将您从组织中移除](../admin-console/manage-members/user-management.md#offboard-users)。
{% endhint %}

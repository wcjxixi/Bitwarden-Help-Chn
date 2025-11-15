# 持续管理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/manage-client-orgs/)
{% endhint %}

要以[服务用户](provider-users.md#provider-user-types)身份访问[客户组织](provider-portal-overview.md#client-organizations)：

1、使用产品切换器打开**提供商门户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4xn04Sj9u8n73TPxZUWi5f/dac0d56f47a05e2d8b28754e997a1391/2025-02-25_15-16-00.png?_a=DAJCwlWIZAAB" %}
品切换器 - 提供商门户
{% endembed %}

2、从**客户**选项卡中选择要管理的客户组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7AoSHeZgJJTBXQmpZ13UBr/56ca464fe6987c8c5fc8e7099235d640/2025-02-25_15-17-46.png?_a=DAJCwlWIZAAB" %}
提供商门户
{% endembed %}

进入客户管理控制台后，您可以全面管理客户组织，包括以下重要的工作内容：

{% hint style="danger" %}
提供商用户不能再直接查看、管理、创建或导出客户组织密码库中的项目。但提供商用户可以直接向客户组织导入密码库数据。
{% endhint %}

| 工作内容         | 描述                                  | 资源                                                                                                                                                                                            |
| ------------ | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 添加和移除用户      | 当他们加入或离开客户的组织时，从 Bitwarden 入职和离职用户。 | <p><a href="../admin-console/manage-members/user-management.md#onboard-users">用入职用户</a><br><a href="../admin-console/manage-members/user-management.md#offboard-users">离职用户</a></p>           |
| 更改用户权限       | 当最终用户更改角色时，根据需要更改他们的权限。             | [用户类型和访问控制](../admin-console/manage-members/member-roles.md)                                                                                                                                  |
| 添加和移除用户席位    | 随着客户业务的增长，管理客户组织的用户席位的数量。           | [管理用户席位](../admin-console/manage-members/user-management.md#manage-user-seats)                                                                                                                |
| 重置用户主密码      | 如果启用，请使用管理员密码重置来恢复忘记主密码的最终用户帐户。     | [管理员密码重置](../admin-console/manage-members/account-recovery/about-account-recovery.md)                                                                                                         |
| 创建 & 共享密码库项目 | 当用户需要访问新系统时，即时添加和共享新的密码库项目。         | [共享](../password-manager/organization-members/sharing.md)                                                                                                                                     |
| 安全的一次性共享     | 使用 Bitwarden 安全地一次性共享凭证、文档等。        | [创建 Send](../password-manager/bitwarden-send/create-a-send.md)                                                                                                                                |
| 监控密码库健康      | 使用组织密码库健康报告和事件日志来密切关注客户组织的整体健康状况。   | <p><a href="../password-manager/your-vault/security-tools/vault-health-reports.md">密码库健康报告</a></p><p><a href="../admin-console/oversight-visibility/event-logging/event-logs.md">事件日志</a></p> |
| 管理计费         | 如果需要，更改客户组织的计费信息。                   | [更新计费信息](../plans-and-pricing/update-your-billing-information.md)                                                                                                                             |

此外，**如果您的服务用户帮助培训客户的最终用户使用 Bitwarden**，以下资源可能会有所帮助：

| 工作内容              | 描述                                          | 资源                                                                                 |
| ----------------- | ------------------------------------------- | ---------------------------------------------------------------------------------- |
| 用户注册              | 帮助最终用户注册 Bitwarden 账户。                      | [注册](https://vault.bitwarden.com/#/register)                                       |
| 观看培训视频            | 传递我们过去进行的一些培训。                              | [Bitwarden 入门](https://bitwarden.com/getting-started)                              |
| 帮助用户导入他们的数据       | 如果您的客户允许，请向用户提供将其个人数据导入 Bitwarden 的说明。      | [导入数据到密码库](../password-manager/import-and-export/import-data.md)                   |
| 帮助设置两步登录          | 向用户提供说明以帮助简化两步登录的设置。                        | [两步登录方式](../account/two-step-login/setup-two-step-login/two-step-login-methods.md) |
| 演示 Bitwarden 应用程序 | 帮助用户了解 Bitwarden 移动应用程序、浏览器扩展程序以及其他应用程序的好处。 | [入门指南](../password-manager/getting-started/)                                       |
| 演示注册              | 鼓励高级用户通过参加每周演示来独立学习。                        | [Bitwarden 事件](https://www.crowdcast.io/bitwarden)                                 |

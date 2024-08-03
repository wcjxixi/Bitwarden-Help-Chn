# 机密

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets/)
{% endhint %}

机密是您的组织需要安全存储、永远不应该以明码形式公开或通过未加密的渠道传输的敏感键值对，例如：

* API 密钥
* 应用配置
* 数据库连接字符串
* 环境变量

您的用户账户通过[已分配的工程](projects.md)可以访问的机密列在主要的 Secrets Manager 视图中，也可以通过从导航中选择**机密**来列出：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6a5Yuy6zL4ifepqTEwsHSL/6fe0360c721c96148f5a7d1cb4f9e07e/Screenshot_2024-04-10_at_9.32.00_AM.png?_a=BAJFJtWIB" %}
机密
{% endembed %}

## 创建机密 <a href="#create-a-secret" id="create-a-secret"></a>

要创建一个新的机密：

1、使用**新增**下拉菜单选择**机密**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3uEcZ7G5L2TJM4QgMmFZ4H/7db487049197b1a741749967d02a3cbb/Screenshot_2024-04-09_at_10.36.07_AM.png?_a=BAJFJtWIB" %}
新增机密
{% endembed %}

2、在「新增机密」窗口的最顶部部分，输入**名称**和**值**。可选添加**备注**。

3、在**工程**部分，选择一个现有[工程以关联机密](secrets.md#add-secrets-to-a-project)或创建一个将包含机密的新工程。每一个机密一次只能与一个工程相关联。

4、（可选）使用**人员**和**机器账户**选项卡授予人员或机器账户对机密的直接访问权限。

5、完成后，选择**保存**按钮。

## 添加机密到工程 <a href="#add-secrets-to-a-project" id="add-secrets-to-a-project"></a>

机密一次只能分配给一个工程。通过向工程添加机密：

* 有权访问该工程的组织成员将能够查看或操作此机密。
* 有权访问该工程的[机器账户](machine-accounts.md)将能够创建注入此机密的途径。

要将您的机密添加到工程中：

1. 导航到**机密**视图然后选择要添加的机密。
2. 在「编辑机密」窗口中，打开**工程**选项卡然后输入或选择要与机密关联的工程。每一个机密一次只能与一个工程相关联。
3. 完成后，选择**保存**按钮。

#### 将机密分配给人员或机器账户 <a href="#assign-secrets-to-people-or-machine-accounts" id="assign-secrets-to-people-or-machine-accounts"></a>

在同一窗口中，您可以直接向人员和机器账户授予对机密的访问权限：

* 直接向用户授予对机密的访问权限将允许他们从**机密**视图与其进行交互。
* 直接授予对机器账户的机密访问权限将使用机器账户的访问令牌授予对机密的程序化访问权限。

## 删除机密 <a href="#delete-a-secret" id="delete-a-secret"></a>

要删除机密，请使用要删除的机密的 (**≡**) 选项菜单选择**删除机密**。删除的机密将被发送到回收站，删除后它们会保留 30 天。 30 天过去后，机密将被永久删除且不可恢复。

在回收站中，您可以在 30 天等待期之前将机密**恢复**到您的密码库或**永久删除**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/35KZdrj3ve0EHvOC0nbxTf/fdc9ca87c5fd720022aacdc016d8906f/Screenshot_2024-04-10_at_9.33.21_AM.png?_a=BAJFJtWIB" %}
回收站
{% endembed %}

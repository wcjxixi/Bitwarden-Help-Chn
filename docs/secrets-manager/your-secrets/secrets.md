# 机密

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets/)
{% endhint %}

机密是您的组织需要安全存储、永远不应该以明码形式公开或通过未加密的渠道传输的敏感键值对，例如：

* API 密钥
* 应用配置
* 数据库连接字符串
* 环境变量

您的用户账户通过[已分配的工程](projects.md)可以访问的机密列在主要的 Secrets Manager 视图中，也可以通过从导航中选择**机密**来列出：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6a5Yuy6zL4ifepqTEwsHSL/d8c3db647c22e32c910c870ad5fef105/2024-12-03_11-37-29.png?_a=DAJCwlWIZAAB" %}
机密
{% endembed %}

## 创建机密 <a href="#create-a-secret" id="create-a-secret"></a>

要创建一个新的机密：

1、使用**新增**下拉菜单选择**机密**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3uEcZ7G5L2TJM4QgMmFZ4H/24d73aa7121de9c77383f51de618db02/2024-12-03_11-29-17.png?_a=DAJCwlWIZAAB" %}
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

### 将机密分配给人员或机器账户 <a href="#assign-secrets-to-people-or-machine-accounts" id="assign-secrets-to-people-or-machine-accounts"></a>

在同一窗口中，您可以直接向人员和机器账户授予对机密的访问权限：

* 直接向用户授予对机密的访问权限将允许他们从**机密**视图与其进行交互。
* 直接授予对机器账户的机密访问权限将使用机器账户的访问令牌授予对机密的程序化访问权限。

## 删除机密 <a href="#delete-a-secret" id="delete-a-secret"></a>

删除机密后，它会被移至回收站保留 30 天。在此之后，它将被永久删除。

{% hint style="danger" %}
机密被永久删除后，将无法恢复。
{% endhint %}

要删除机密：

1、转到**机密**。

2、在机密所在的同一行，选择 **≡**&#x56FE;标。

3、选择**删除机密**：

{% embed url="https://bitwarden.com/assets/mQdIhUsvlFy5YfC3d8G3p/62b16e096dbd7f2b60ad597b90807608/Delete_secret.png?w=1200&fm=avif" %}
删除机密
{% endembed %}

要在 30 天之前撤消删除或永久删除机密：

1、转到**回收站**。

2、在机密所在的同一行，选择 **≡**&#x56FE;标。

3、选择**恢复机密**或**永久删除**：

{% embed url="https://bitwarden.com/assets/35KZdrj3ve0EHvOC0nbxTf/7b793940ffe2e9c0dfbf035ae6f33529/Permanently_delete_secret.png?w=1200&fm=avif" %}
永久删除机密
{% endembed %}

4、选择**删除机密**进行确认。

# 工程

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/projects/)
{% endhint %}

工程是按逻辑组合在一起的[机密](secrets.md)的集合，由您的 DevOps 和网络安全团队对其进行访问权限的管理。您的用户账户有权访问的工程列在主要的 Secrets Manager 视图中，也可以通过从导航中选择**工程**来列出：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/71lYVBOdFFIcautbuha9k1/2c604acea9015d4487ac9149bf3438dd/Screenshot_2024-04-10_at_9.23.19_AM.png?_a=BAJFJtWIB" %}
工程
{% endembed %}

打开一个工程将列出与其相关联的**机密**、**人员**和**机器账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7IlJQx9yhxuO5ffABmKyqd/0d6c7319a8b2f970f004260af277b6f6/Screenshot_2024-04-10_at_9.26.02_AM.png?_a=BAJFJtWIB" %}
工程内部
{% endembed %}

## 创建工程 <a href="#create-a-project" id="create-a-project"></a>

要创建一个新的工程：

1、使用**新增**下拉菜单选择**工程**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gGgCYT0CgS3MKAngKDooL/e9c55079d352999db5cd76c55333c729/Screenshot_2024-04-09_at_10.29.34_AM.png?_a=BAJFJtWIB" %}
创建工程
{% endembed %}

2、输入**工程名称**。您可以随时使用「工程」页面上的 (**≡**) 选项菜单更改工程名称。

3、选择**保存**按钮。

## 添加机密到工程 <a href="#add-secrets-to-a-project" id="add-secrets-to-a-project"></a>

您可以将新的和现有的[机密](secrets.md)添加到您的工程中：

{% tabs %}
{% tab title="添加现有的机密" %}
要将现有机密添加到您的工程：

1. 导航到**机密**视图然后选择要添加的机密。
2. 在「编辑机密」窗口中，打开**工程**选项卡然后输入或选择要与机密关联的工程。每一个机密一次只能与一个工程相关联。
3. 完成后，选择**保存**按钮。
{% endtab %}

{% tab title="添加新的机密" %}
要为您的工程创建新的机密：

1、使用**新增**下拉菜单选择**机密**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3uEcZ7G5L2TJM4QgMmFZ4H/7db487049197b1a741749967d02a3cbb/Screenshot_2024-04-09_at_10.36.07_AM.png?_a=BAJFJtWIB" %}
创建机密
{% endembed %}

2、在「新增机密」窗口的名称/值对选项卡上，输入**名称**和**值**。可选添加**备注**。

3、选择**工程**选项卡然后输入或选择要与机密关联的工程。几个关键点。

* 只有有权访问该工程的组织成员才能查看或操作此机密。
* 只有有权访问该工程的[机器账户](machine-accounts.md)才能创建注入此机密的途径。
* 每一个机密一次只能与一个工程相关联。

4、完成后，选择**保存**按钮。
{% endtab %}
{% endtabs %}

## 添加人员到工程 <a href="#add-people-to-a-project" id="add-people-to-a-project"></a>

将组织成员添加到您的工程将允许这些人与此工程的机密进行交互。要将人员添加到您的工程：

1、在「工程」中，选择**人员**选项卡。

2、从「人员」下拉列表中，键入或选择要添加到工程的成员或群组。选择合适的人员后，选择**添加**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Vu9wuBd8ceEz7ji7V2kHZ/4bf1df872a882798d20f9aa868cc3ff8/Screenshot_2024-04-09_at_10.33.54_AM.png?_a=BAJFJtWIB" %}
将人员添加到工程
{% endembed %}

3、将成员或群组添加到工程后，为这些成员或群组设置**权限**级别。成员和群组可以具有以下权限级别之一：

* **可以读取**：成员/群组将能够查看此工程中的现有机密。
* **可以读取和写入**：成员/群组将能够查看此工程中的现有机密，以及在此工程中创建新的机密。

## 添加机器账户到工程 <a href="#add-service-accounts-to-a-project" id="add-service-accounts-to-a-project"></a>

您可以将新的和现有的[机器账户](machine-accounts.md)添加到工程中：

{% tabs %}
{% tab title="添加现有的机器账户" %}
要将现有服务账户添加到您的工程：

1、在「工程」中，选择**服务账户**选项卡。

2、从「服务账户」下拉列表中，键输入或选择要添加到工程的服务账户。选择正确的服务账户后，选择**添加**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1IJNE4LCOMqQsAMBYKN5pe/bc888b6c465d503b48a78e122fad50f2/Screenshot_2024-04-10_at_9.29.04_AM.png?_a=BAJFJtWIB" %}
添加机器账户
{% endembed %}

对于每个已添加的工程，选择一个权限级别：

* **可以读取**：机器账户可以从分配的工程中检索机密。
* **可以读取和写入**：机器账户可以从已分配的工程中检索和编辑机密，在已分配的工程中创建新的机密，或者创新的工程。

{% hint style="info" %}
机器账户的写入​​访问权限的充分利用取决于即将发布的 [CLI](../developer-tools/secrets-manager-cli.md) 版本。目前，这只是在 UI 中提供了此选项。请继续关注[发行说明](../../release-notes.md)以获取更多信息。
{% endhint %}
{% endtab %}

{% tab title="添加新的机器账户" %}
要为此工程添加机器账户：

1、使用新**新增**下拉菜单选择**机器账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1IJNE4LCOMqQsAMBYKN5pe/bc888b6c465d503b48a78e122fad50f2/Screenshot_2024-04-10_at_9.29.04_AM.png?_a=BAJFJtWIB" %}
新增机器账户
{% endembed %}

&#x20;2、输入**机器账户名称**，然后在「访问权限」部分中，输入或选择该服务账户应该能够访问的工程名称和/或个人机密。

{% hint style="info" %}
对于测试版，服务账户将被限制为对工程的只读访问权限
{% endhint %}
{% endtab %}
{% endtabs %}

## 删除工程 <a href="#delete-a-project" id="delete-a-project"></a>

要删除工程，请使用要删除的工程的 (**≡**) 选项菜单选择**删除工程**。删除工程不会删除与其关联的机密。工程一旦删除就会被完全删除，**不会**像[机密那样被发送到回收站](secrets.md#delete-a-secret)。

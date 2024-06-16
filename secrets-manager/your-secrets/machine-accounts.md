# 机器账户

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/service-accounts/)
{% endhint %}

{% hint style="info" %}
自 2024.4.1 版本起，在 Bitwarden Secrets Manager 中的服务账户现在称为机器账户。所有功能将保持不变。
{% endhint %}

机器账户代表非人类机器用户，例如，需要以编程方式访问一组谨慎的[机密](secrets.md)的应用程序或部署管道。机器账户可用于：

* 适当地限制机器用户对一定范围的机密的访问权限。
* 发布[访问令牌](access-tokens.md)以促进对机密的编程访问和解密能力。

您的用户账户有权访问的机器账户可以通过从导航中选择**机器账户**查看：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3IQzFGc9f4OAoqvJSgrEBn/f50b7408b99c322fcd79af14cd345c35/Screenshot_2024-04-10_at_9.39.52_AM.png?_a=BAJFJtWIB" %}
机器账户
{% endembed %}

打开机器账户将列出此机器账户有权访问的**机密**和**人员**，以及任何已生成的**访问令牌**和**事件日志**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3L9EGMDn7gGAMi3uwD1MIP/4350df2f99ba9f8ec17714dd05e0407c/Screenshot_2024-04-10_at_9.40.45_AM.png?_a=BAJFJtWIB" %}
机器账户内部
{% endembed %}

## 创建机器账户 <a href="#create-a-machine-account" id="create-a-machine-account"></a>

在管理控制台**计费** → **订阅**页面上，您可以分配可供组织使用的机器账户的数量。有关可用机器账户和机器账户扩展的更多信息，请参阅[此处](../get-started/secrets-manager-quick-start.md#user-seats-and-service-account-scaling)。

要创建一个新的机器账户：

1、使用**新增**下拉菜单选择**机器账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/LaVwicbqhvbliXPm6loOU/917efb20141bc4c18f6b9f19335f9306/Screenshot_2024-04-09_at_10.37.53_AM.png?_a=BAJFJtWIB" %}
新增机器账户
{% endembed %}

2、输入**机器账户名称**，然后然后选择**保存**。

3、打开「机器账户」，然后在**工程**选项卡中键入或选择该机器账户应能够访问的工程的名称。对于每个添加的工程，选择一个**权限**级别：

* **可以读取**：机器账户可以从分配的工程中检索机密。
* **可以读取、写入**：机器账户可以从分配的工程中检索和编辑机密，在分配的工程中创建新的机密，或者完全创建新的工程。

{% hint style="success" %}
机器账户的写入​​访问权限的充分利用取决于即将发布的 [CLI](../developer-tools/secrets-manager-cli.md) 版本。目前，这只是在 UI 中提供了此选项。请继续关注[发行说明](../../release-notes.md)以获取更多信息。
{% endhint %}

## 添加人员到机器账户 <a href="#add-people-to-a-machine-account" id="add-people-to-a-machine-account"></a>

将组织成员添加到机器账户将允许他们为机器账户生成访问令牌并与机器账户具有访问权限的所有机密进行交互。要将人员添加到您的机器账户：

1、在「服务账户」中，选择**人员**选项卡。

2、从「人员」下拉列表中，输入或选择要添加到工程的成员或群组。选择了合适的人员后，选择**添加**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3TrklnCquoynDHFX6nJ8w/37f2f05ec4d4fa82ac0cd65007110985/Screenshot_2024-04-10_at_9.43.05_AM.png?_a=BAJFJtWIB" %}
将组织成员添加到机器账户
{% endembed %}

## 添加工程到机器账户 <a href="#add-projects-to-a-machine-account" id="add-projects-to-a-machine-account"></a>

将工程添加到机器账户将允许使用访问令牌以编程方式访问包含的机密。您可以将新工程和现有工程添加到机器账户：

要将工程添加到机器账户：

1、在「机器账户」中，选择**工程**选项卡。

2、从「工程」下拉菜单中，键入或选择要添加到机器账户的工程。选择正确的工程后，选择**添加**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3XGkQt3MdNHmAoKLXXXMGh/50cc77ff9b31a05bb90e7eee6eff8fa3/Screenshot_2024-04-10_at_9.44.31_AM.png?_a=BAJFJtWIB" %}
添加工程
{% endembed %}

3、对于每个已添加的工程，选择一个**权限**级别：

* **可以读取**：机器账户可以从分配的工程中检索机密。
* **可以读取和写入**：机器账户可以从分配的工程中检索和编辑机密，在分配的工程中创建新的机密，或者完全创建新的工程。

## 删除机器账户 <a href="#delete-a-machine-account" id="delete-a-machine-account"></a>

要删除机器账户，请使用要删除的机器账户的 (**≡**) 选项菜单选择**删除机器账户**。删除机器账户不会删除与其关联的机密。机器账户一旦删除就会被完全移除，**不会**像[机密那样被发送到回收站](secrets.md#delete-a-secret)。

## 机器账户事件 <a href="#machine-account-events" id="machine-account-events"></a>

每个机器账户执行操作的时间戳记录可从机器账户的**事件日志**选项卡中获得：

{% embed url="https://bitwarden.com/_gatsby/image/9feb9274651fc97145948cb3d866b806/4daa32f8e75a6dc0af60401543c21650/Screenshot%202023-10-23%20at%2010.26.06%20AM.webp?eu=d9df03e4e19afcd20b6af3806c23656de23e02fff85265853f62b5a71aa89a872ca01d0723922fb82b600cde80b114eb63937d661aeed6dfc5ea1ba1eb3da30050d653ec63ba2556002cc1aabaad420128851047beda9559f43831cab6f7e1215a13496feb64e6d4a8b63226eed06968ebe0ae7322c5b47ae81a0456ad7c2b8f3dc299ac744994b9b27ab383a6b6089c9fb32c0213d8a53227764a1f5fb82db9a7b250753b2e4908309aa80c926689d56f5e3476001c5ba82355d255f96f2cc2e4e6a35eb62b3f8ea9c92f7280ddae86826bd13436b998&a=w%3D850%26h%3D323%26fm%3Dwebp%26q%3D75&cd=2023-11-01T12%3A58%3A47.993Z" %}
服务账户事件
{% endembed %}

有权访问给定机器账户的任何用户都可以查看该机器账户的事件。捕获的事件包括：

* 访问了机密 _secret-identifier._ (`2100`)

{% hint style="info" %}
每个事件都与类型代码（`1000`、`1001` 等）关联，用于标识事件捕获的操作。[Bitwarden 公共 API](../../organizations/bitwarden-public-api.md) 使用类型代码来识别事件记录的操作。
{% endhint %}

事件日志可导出并且无限期保留。导出事件将创建一个指定日期范围内所有事件的 `.csv` 文件，该日期范围不应超过 367 天。

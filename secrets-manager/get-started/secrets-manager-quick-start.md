# Secrets Manager 快速入门

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-quick-start/)
{% endhint %}

{% hint style="success" %}
如果您是开发人员，您可能更喜欢[开发人员快速入门](developer-quick-start.md)。您当前阅读的文章将从管理和设置的角度介绍 Secrets Manager。
{% endhint %}

Bitwarden Secrets Manager 使开发人员、DevOps 和网络安全团队能够大规模集中存储、管理和部署机密。

**Secrets Manager 网页应用程序**将是您设置机密管理基础设施的主页。您将使用它来添加和组织[机密](secrets-manager-quick-start.md#add-secrets)、创建适合您需要的[权限系统](secrets-manager-quick-start.md#assign-members-to-your-project)，以及生成供您的应用程序使用的[访问令牌](secrets-manager-quick-start.md#create-an-access-token)。完成后，您可以继续阅读[开发者快速入门指南](developer-quick-start.md)，以了解如何将机密注入您的机器和应用程序。

## 激活 Secrets Manager <a href="#activate-secrets-manager" id="activate-secrets-manager"></a>

您必须是组织所有者才能启用 Secrets Manager。要开始使用 Secrets Manager：

1、在管理控制台中，导航至您组织的**计费** → **订阅**页面

2、在**来自 Bitwarden 的更多产品**部分中，勾选**订阅 Secrets Manager** 复选框。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/eYPz7jQRhG0PvU7gclzXk/04bbea42872c078a1aa3d38e755ae2bc/Screenshot_2024-04-09_at_10.21.39_AM.png?_a=BAJFJtWIB" %}
添加 Secrets Manager
{% endembed %}

激活后，通过网页应用上的产品切换器切换到 Secrets Manager：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/919a2c332ed6a53707f80ac3f734e0a8/2024-06-04_10-13-18.png?_a=BAJFJtWIB" %}
产品切换器
{% endembed %}

在您使用 Secrets Manager 迈出第一步之前，您需要明确邀请一些组织成员加入。

### 给予成员访问权限 <a href="#give-members-access" id="give-members-access"></a>

{% hint style="success" %}
在继续之前，我们建议为 Secrets Manager 的用户设置一个或多个群组。您需要通过**成员**页面授予成员对 Secrets Manager 的访问权限，但一旦您的密码库被填充，您可以使用群组来大规模地分配对机密的访问权限。
{% endhint %}

要授予成员对 Secrets Manager 的访问权限，您必须是组织的所有者或者管理员：

1、打开您组织的**成员**选项卡，然后选中您要授予他们 Secrets Manager 访问权限的成员。

2、使用 **≡** 菜单，选择**启用 Secrets Manager** 以向选定成员授予访问权限：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3IBNL6FdndgPeuXa7m3rlP/429b9a1a63919be675b047521ff034a4/Screenshot_2024-02-27_at_2.16.52_PM.png?_a=BAJFJtWIB" %}
添加 Secrets Manager 用户
{% endembed %}

{% hint style="info" %}
向用户（或您自己）授予 Secrets Manager 访问权限后，您可能需要刷新密码库以使 Secrets Manager 出现在产品切换器中。
{% endhint %}

### 用户席位和机器账户扩展 <a href="#user-seats-and-service-account-scaling" id="user-seats-and-service-account-scaling"></a>

从您组织的**计费** → **订阅**页面，您可以为 Secrets Manager 组织分配允许的用户席位和服务账户总数。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3hOpU8WK6KsA2eMRwfpEoJ/3865ba0b4b91fcdfccd9c8de9a7ff993/Screenshot_2024-04-09_at_10.24.29_AM.png?_a=BAJFJtWIB" %}
Secrets Manager 用户管理
{% endembed %}

添加新用户或机器账户时，Secrets Manager 将自动扩展您的用户席位和机器账户。可以通过勾选**限制订阅**和**限制机器账户**复选框来设置限制。

{% hint style="info" %}
在**用户席位**字段中，指定的数量必须小于或等于您的 Password Manager 订阅指定的席位数量。

您还可以使用**附加机器账户**字段，明确添加高于计划预包装数量的机器账户；团队账户为 20 个，企业账户为 50 个。
{% endhint %}

## 第一步 <a href="#first-steps" id="first-steps"></a>

### 您的机密密码库 <a href="#your-secrets-vault" id="your-secrets-vault"></a>

使用产品切换器打开 Secrets Manager 网页应用程序。如果这是您第一次打开该应用程序，您将看到一个空的密码库，但最终它将充满您的工程和机密：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/644qYsogVg0ztLkZ90cKPi/37f6bfbea1a691513e77f4a36a723fbe/Screenshot_2024-04-09_at_10.28.33_AM.png?_a=BAJFJtWIB" %}
机密密码库
{% endembed %}

让我们开始填充您的密码库吧。

### 新增工程 <a href="#add-a-project" id="add-a-project"></a>

工程是按逻辑组合在一起的机密的集合，由您的 DevOps、网络安全或其他内部团队进行访问权限的管理。重要的是要考虑到，在创建工程时，工程将是**您分配的成员访问机密的主要机构**。要创建一个工程：

1、使用**新增**下拉菜单选择**工程**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gGgCYT0CgS3MKAngKDooL/e9c55079d352999db5cd76c55333c729/Screenshot_2024-04-09_at_10.29.34_AM.png?_a=BAJFJtWIB" %}
创建一个工程
{% endembed %}

2、输入**工程名称**。

3、选择**保存**按钮。

### 分配成员到工程 <a href="#assign-members-to-your-project" id="assign-members-to-your-project"></a>

将组织成员添加到您的工程将允许这些用户与此工程的机密进行交互。要将人员添加到您的工程：

1、在「新增工程」中，选择**人员**选项卡。

2、从「人员」下拉列表中，输入或选择要添加到工程的成员或群组。选择了合适的人员后，选择**添加**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Vu9wuBd8ceEz7ji7V2kHZ/4bf1df872a882798d20f9aa868cc3ff8/Screenshot_2024-04-09_at_10.33.54_AM.png?_a=BAJFJtWIB" %}
将人员添加到工程
{% endembed %}

3、将成员或组添加到工程后，为这些成员或群组设置**权限**级别。成员和群组可以具有以下权限级别之一：

* **可以读取**：成员/群组将能够查看此工程中的现有机密。
* **可以读取和写入**：成员/群组将能够查看此工程中的现有机密，以及在此工程中创建新的机密。

### 新增机密 <a href="#add-secrets" id="add-secrets"></a>

您的工程中已经有一些成员可以帮助您管理它了，现在让我们向该工程添加一些**机密**。机密是存储在您的密码库中的敏感键值对，通常是永远不应以纯代码公开或通过未加密通道传输的东西，例如：

* API 密钥
* 应用配置
* 数据库连接字符串
* 环境变量

您可以将机密作为 `.json` 文件直接导入您的密码库或手动添加机密：

{% tabs %}
{% tab title="导入机密" %}
要导入您的机密：

1、查看[此文档](../import-export/import-data.md)以帮助正确格式化导入的文件。

2、从左侧导航中选择**设置** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1YQuiYqXIuYYG1TpXoSJoU/ccb036a10f2c5e7abf28aec1f772ee2b/Screenshot_2024-04-09_at_10.35.18_AM.png?_a=BAJFJtWIB" %}
导入数据
{% endembed %}

3、选择**选择文件**然后选择要导入的 `.json` 文件。
{% endtab %}

{% tab title="手动添加机密" %}
要手动添加机密：

1、使用**新增**下拉菜单选择**机密**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3uEcZ7G5L2TJM4QgMmFZ4H/7db487049197b1a741749967d02a3cbb/Screenshot_2024-04-09_at_10.36.07_AM.png?_a=BAJFJtWIB" %}
创建机密
{% endembed %}

2、在「新增机密」窗口的最顶部部分，输入**名称**和**值**。可选添加**备注**。

3、在「工程」部分，输入或选择要与此机密关联的工程。几个关键点：

* 每一个机密一次只能与一个工程相关联。
* 只有有权访问该工程的组织成员才能查看或操作此机密。
* 只有有权访问该工程的服务账户才能创建注入此机密的途径（[稍后会详细介绍](secrets-manager-quick-start.md#add-a-service-account)）。

4、完成后，选择**保存**按钮。

对要添加到密码库的所有机密，重复此过程。
{% endtab %}
{% endtabs %}

### 新增机器账户 <a href="#add-a-service-account" id="add-a-service-account"></a>

现在您已经有了一个填满机密的工程了，是时候开始构建对这些机密的机器访问了。**机器账户**代表非人类机器用户或一组机器用户，他们需要以编程方式访问存储在您的密码库中的某些机密。机器账户用于：

* 适当地限制机器用户对一定范围的机密的访问权限。
* 发布访问令牌以促进对机密的编程访问和解密能力。

要为此工程添加机器账户：

1、使用**新增**下拉菜单选择**机器账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/LaVwicbqhvbliXPm6loOU/917efb20141bc4c18f6b9f19335f9306/Screenshot_2024-04-09_at_10.37.53_AM.png?_a=BAJFJtWIB" %}
新增服务账户
{% endembed %}

2、输入**机器账户名称**，然后点击**保存**。

3、打开机器账户，然后在“项目”选项卡中键入或选择该计算机帐户应能够访问的项目的名称。对于每个添加的项目，选择权限级别：

* **可以读取**：机器账户可以从已分配的工程中检索机密。
* **可以读取和写入**：机器账户可以从已分配的工程中检索和编辑机密，以及在已分配的工程中创建新的机密或创建新的工程。

{% hint style="info" %}
机器账户的写入​​访问权限的充分利用取决于即将发布的 [CLI](../developer-tools/secrets-manager-cli.md) 版本。目前，这只是在 UI 中提供了此选项。请继续关注[发行说明](../../release-notes.md)以获取更多信息。
{% endhint %}

### 创建访问令牌 <a href="#create-an-access-token" id="create-an-access-token"></a>

**访问令牌**有助于以编程方式访问和解密存储在您的密码库中的机密。访问令牌颁发给特定的服务账户，并将赋予应用它们的任何机器仅能访问**与该服务账户相关联的机密**的能力。要创建访问令牌：

1、从导航中选择**机器账户**。

2、选择要为其创建访问令牌的机器账户，然后打开**访问令牌**选项卡：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6EINDaXiPQp9qQcO6q1zt5/40e157b6e8385572f58e817d49100c7a/Screenshot_2024-04-09_at_10.40.41_AM.png?_a=BAJFJtWIB" %}
创建访问令牌
{% endembed %}

3、选择**创建访问令牌**按钮。

4、在「创建访问令牌」面板上，提供以下信息：

* 令牌的**名称**。
* 令牌的**到期**时间。默认为`从不`。

5、完成令牌配置后，选择**创建访问令牌**按钮。

6、将出现一个显示访问令牌的窗口。关闭此窗口之前请将您的令牌复制到安全的地方，因为您的令牌**以后无法获取**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3QfpdSQai2hFrWGdGSlQRN/8453d5425eba62421e443b4b7a677f7a/Screenshot_2024-04-09_at_10.41.34_AM.png?_a=BAJFJtWIB" %}
访问令牌示例
{% endembed %}

此访问令牌是身份验证工具，通过它您可以编写机密注入脚本到您的机器和应用程序中。

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经掌握了创建用于安全地管理机密的基础设施以及为机器访问机密创建路径的诀窍，让我们继续阅读[开发人员快速入门](developer-quick-start.md)指南。

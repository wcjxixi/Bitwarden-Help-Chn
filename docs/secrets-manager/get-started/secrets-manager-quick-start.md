# Secrets Manager 快速入门

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-quick-start/)
{% endhint %}

{% hint style="success" %}
如果您是开发人员，您可能更喜欢[开发人员快速入门](developer-quick-start.md)。您当前阅读的文章将从管理和设置的角度介绍 Secrets Manager。
{% endhint %}

Bitwarden Secrets Manager 使开发人员、DevOps 和网络安全团队能够大规模集中存储、管理和部署机密。使用 Secrets Manager 网页 App 来添加和组织[机密](secrets-manager-quick-start.md#add-secrets)、创建适合您需要的[权限系统](secrets-manager-quick-start.md#assign-members-to-your-project)，以及生成供您的应用程序使用的[访问令牌](secrets-manager-quick-start.md#create-an-access-token)。

设置 Secrets Manager 后，请继续阅读[开发者快速入门指南](developer-quick-start.md)，以了解如何将机密注入您的机器和应用程序。

## 访问 Secrets Manager <a href="#access-secrets-manager" id="access-secrets-manager"></a>

登录 Bitwarden 网页 App，然后从导航菜单的产品切换器中选择 Secrets Manager：

{% embed url="https://vimeo.com/840459200" %}

如果您或您的组织还不是 Secrets Manager 的活跃用户，请点击**立即尝试**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7iZGZNg39Z2l0OnoMIeFK9/88af82e4dec707e2b293c2ae60370b2b/2024-08-05_09-18-08.png?_a=DAJCwlWIZAAB" %}
Secrets Manager 主页
{% endembed %}

* **所有者**将被重定向到组织**订阅**页面的 Secrets Manager 部分。
* **用户**会询问是否要向其组织所有者发送一封电子邮件，请求访问 Bitwarden Secrets Manager。他们可以在发送前编辑电子邮件。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1yTEdQGVkLtkvZjRErjBkO/e68e6dafe143a5166ccddfdc4d61fc0e/2024-07-30_15-14-33.png?_a=DAJCwlWIZAAB" %}
请求对 Secrets Manager 的访问权限
{% endembed %}

## 设置 Secrets Manager <a href="#set-up-secrets-manager" id="set-up-secrets-manager"></a>

### 将 Secrets Manager 添加到您的组织 <a href="#add-secrets-manager-to-your-organization" id="add-secrets-manager-to-your-organization"></a>

只有所有者才能将 Secrets Manager 添加到他们的组织。要开始使用 Secrets Manager：

1、在您组织的管理控制台中，转到**计费** → **订阅**。

2、在**来自 Bitwarden 的更多产品**部分中，勾选**订阅 Secrets Manager**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/eYPz7jQRhG0PvU7gclzXk/04bbea42872c078a1aa3d38e755ae2bc/Screenshot_2024-04-09_at_10.21.39_AM.png?_a=DAJCwlWIZAAB" %}
添加 Secrets Manager
{% endembed %}

3、根据您组织的方案：

* 如果您使用免费版方案，请选择**提交**。
* 如果您使用的是升级版方案，请输入所需的**订阅席位**数量（最多不超过您的 Password Manager 订阅总数）以及超出方案已包含的总数量（团队版为 20 个，企业版为 50 个）的**附加机器账户**数量。选择**保存**。

{% hint style="info" %}
添加新用户或机器账户时，Secrets Manager 将自动扩展您的用户席位和机器账户。您可以随时转到**计费** → **订阅**来更改允许的用户席位和机器账户的总数。要设置扩展限制，请选择**限制订阅**和**限制计机器账户**：

<img src="https://bitwarden.com/assets/6tcOx1PSHT54CQGPkbBZZ2/33a91dde38fdad0fd921403c2de77e00/Limit_subscription_seats_and_machine_accounts.png?w=765&#x26;fm=avif" alt="" data-size="original">
{% endhint %}

激活后，从产品切换器打开 Secrets Manager：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

### 给予成员访问权限 <a href="#give-members-access" id="give-members-access"></a>

{% hint style="success" %}
在继续之前，我们建议为 Secrets Manager 用户[创建群组](../../admin-console/manage-members/groups.md#create-a-group)。用户拥有对 Secrets Manager 的访问权限后，您就可以通过群组快速分配对机密的访问权限。
{% endhint %}

组织所有者和管理员可以授予对 Secrets Manager 的访问权限。要授予成员访问权限：

1、在您组织的管理控制台中，转到**成员**。

2、单击 **≡图标**，然后选择**激活 Secrets Manager**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3IBNL6FdndgPeuXa7m3rlP/fd04ec9951123e5a0ccd5fe4f04fa4de/2024-12-03_11-18-52.png?_a=DAJCwlWIZAAB" %}
添加 Secrets Manager 用户
{% endembed %}

或者，转到**成员** → **成员角色**然后选择**此用户可以访问 Secrets Manager**：

{% embed url="https://bitwarden.com/assets/3xGmMTCDMgY5V3tYSdA6O7/49200a3fab891c0aa65008dda65f80e0/Edit_member_role_to_grant_Secrets_Manager_access.png?w=730&fm=avif" %}
编辑成员角色以授予 Secrets Manager 访问权限
{% endembed %}

{% hint style="info" %}
向用户（或您自己）授予 Secrets Manager 访问权限后，您可能需要刷新密码库以使 Secrets Manager 出现在产品切换器中。
{% endhint %}

## 第一步 <a href="#first-steps" id="first-steps"></a>

### 您的机密密码库 <a href="#your-secrets-vault" id="your-secrets-vault"></a>

使用产品切换器打开 Secrets Manager 网页 App。如果这是您第一次打开该 App，您将看到一个空的密码库，但最终它将充满您的工程和机密：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/644qYsogVg0ztLkZ90cKPi/a68037e16818da6ac3b335ab4a7d3a90/2024-12-03_11-24-23.png?_a=DAJCwlWIZAAB" %}
机密密码库
{% endembed %}

让我们开始填充您的密码库吧。

### 新增工程 <a href="#add-a-project" id="add-a-project"></a>

**工程**是按逻辑组合在一起的机密的集合，用于对您的 DevOps、网络安全或其他内部团队进行访问权限的管理。重要的是要考虑到，在创建工程时，工程将是**您分配的成员访问机密的主要结构**。要创建一个工程：

1、使用**新增**下拉菜单选择**工程**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gGgCYT0CgS3MKAngKDooL/03bd6080e1f8c695c46fd23918f56951/2024-12-03_11-25-44.png?_a=DAJCwlWIZAAB" %}
创建工程
{% endembed %}

2、输入**工程名称**。

3、选择**保存**按钮。

### 分配成员到工程 <a href="#assign-members-to-your-project" id="assign-members-to-your-project"></a>

将组织成员添加到您的工程将允许这些用户与此工程的机密进行交互。要将人员添加到您的工程：

1、在「新增工程」中，选择**人员**选项卡。

2、从「人员」下拉列表中，输入或选择要添加到工程的成员或群组。选择了合适的人员后，选择**添加**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Vu9wuBd8ceEz7ji7V2kHZ/2f11a06f3ed09a1cd64190ad8197e914/2024-12-03_11-27-19.png?_a=DAJCwlWIZAAB" %}
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

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1YQuiYqXIuYYG1TpXoSJoU/f76b3ee08dda7b470f96da9ebbe4f9b1/2024-12-03_11-28-29.png?_a=DAJCwlWIZAAB" %}
导入数据
{% endembed %}

3、选择**选择文件**然后选择要导入的 `.json` 文件。
{% endtab %}

{% tab title="手动添加机密" %}
要手动添加机密：

1、使用**新增**下拉菜单选择**机密**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3uEcZ7G5L2TJM4QgMmFZ4H/24d73aa7121de9c77383f51de618db02/2024-12-03_11-29-17.png?_a=DAJCwlWIZAAB" %}
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

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/LaVwicbqhvbliXPm6loOU/5559a5caf8ad70a95be3ea89f1b760ad/2024-12-03_11-29-17.png?_a=DAJCwlWIZAAB" %}
新增机器账户
{% endembed %}

2、输入**机器账户名称**，然后点击**保存**。

3、打开机器账户，然后在**工程**选项卡中键入或选择该机器账户具有访问权限的工程名称。对于每个添加的工程，选择一个**权限**级别：

* **可以读取**：机器账户可以从已分配的工程中检索机密。
* **可以读取和写入**：机器账户可以从已分配的工程中检索和编辑机密，以及在已分配的工程中创建新的机密或创建新的工程。

### 创建访问令牌 <a href="#create-an-access-token" id="create-an-access-token"></a>

**访问令牌**有助于以编程方式访问和解密存储在您的密码库中的机密。访问令牌颁发给特定的服务账户，并将赋予应用它们的任何机器仅能访问**与该服务账户相关联的机密**的能力。要创建访问令牌：

1、从导航中选择**机器账户**。

2、选择要为其创建访问令牌的机器账户，然后打开**访问令牌**选项卡：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6EINDaXiPQp9qQcO6q1zt5/259e6c2c6e91e0df63c83d03a89ac4a2/2024-12-03_11-31-26.png?_a=DAJCwlWIZAAB" %}
创建访问令牌
{% endembed %}

3、选择**创建访问令牌**按钮。

4、在「创建访问令牌」面板上，提供以下信息：

* 令牌的**名称**。
* 令牌的**到期**时间。默认为`从不`。

5、完成令牌配置后，选择**创建访问令牌**按钮。

6、将出现一个显示访问令牌的窗口。关闭此窗口之前请将您的令牌复制到安全的地方，因为您的令牌**以后无法获取**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3QfpdSQai2hFrWGdGSlQRN/a5a5483cfbbbf690a8436043be58cea7/2024-12-03_11-32-26.png?_a=DAJCwlWIZAAB" %}
访问令牌示例
{% endembed %}

此访问令牌是身份验证工具，通过它您可以编写机密注入脚本到您的机器和应用程序中。

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经掌握了创建用于安全地管理机密的基础设施以及为机器访问机密创建路径的诀窍，让我们继续阅读[开发人员快速入门](developer-quick-start.md)指南。

或者，了解更多有关 Secrets Manager 的信息：

* [Bitwarden 为秘密管理带来开源安全和零知识加密](https://bitwarden.com/blog/bitwarden-brings-open-source-security-to-secrets-management/)
* [为什么我的开发团队需要 Secrets Manager？](https://bitwarden.com/blog/why-does-my-development-team-need-a-secrets-manager/)
* [为什么端到端加密对开发人员的机密管理至关重要？](https://bitwarden.com/blog/why-end-to-end-encryption-is-crucial-for-developer-secrets-management/)

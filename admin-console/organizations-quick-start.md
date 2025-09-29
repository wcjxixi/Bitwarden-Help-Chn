# 组织快速入门

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/getting-started-organizations/)
{% endhint %}

像 Bitwarden 这样的密码管理器使您可以轻松地跨您的所有设备存储和访问唯一且安全的密码，从而使您的在线账户比以往任何时候都更加安全！使用 Bitwarden，你将不需要危险地重复使用简单的密码，也不必以电子表格、文档或便笺等未加密的格式暴露密码。

**Bitwarden 组织**为您的家庭、团队或企业的密码管理增加了一层协作和共享，使您可以安全地共享常见信息，例如办公室 wifi 密码、在线凭据或共享的公司信用卡。组织拥有的凭据的安全共享既**安全**又**简单**。

本文将帮助您开始使用**免费的 2 人组织**，这样您就可以立即体验安全的共享。

## 什么是组织？ <a href="#what-are-organizations" id="what-are-organizations"></a>

Bitwarden 组织将用户和密码库项目关联在一起，以[安全地共享](../organizations/sharing.md)组织拥有的登录、笔记、支付卡和身份。组织可以是一个家庭、团队、公司或需要安全共享数据的任何一群人。组织具有独立的密码库，[管理员](manage-members/member-roles.md)可以在其中管理组织的项目、用户和设置：

{% embed url="https://bitwarden.com/assets/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?w=1043&fm=avif&q=80" %}
免费组织管理控制台
{% endembed %}

除非您加入的组织使用[策略](oversight-visibility/enterprise-policies.md#single-organization)限制您只能加入一个组织，否则您可以成为任意多个组织的成员。

### 组织与高级会员比较 <a href="#comparing-organizations-with-premium" id="comparing-organizations-with-premium"></a>

关键的是要知道，**组织可以启用组织到用户之间的安全共享**。[高级个人计划](../plans-and-pricing/password-manager/about-bitwarden-plans.md#premium-individual)可解锁高级密码安全和管理功能，包括高级 2FA 选项、Bitwarden 验证器 (TOTP)、加密的文件附件等，但高级个人**不包含安全数据共享功能**。

付费组织（家庭、团队或企业）自动为组织中已注册的**每一个**用户提供这些高级功能（高级 2FA 选项、Bitwarden 验证器 (TOTP) 等）。

## 设置 Bitwarden 账户 <a href="#setup-bitwarden-accounts" id="setup-bitwarden-accounts"></a>

免费的 Bitwarden 组织允许 2 位用户安全地共享组织拥有的凭证。您可以使用免费的组织与朋友或伙伴共享，或者在[升级到不同的计划](../plans-and-pricing/password-manager/about-bitwarden-plans.md)之前测试组织。

Bitwarden 在许多设备上提供了应用程序，包括浏览器扩展、移动 App、桌面 App 和 CLI，但在本指南中，我们将重点介绍[网页 App](../getting-started/getting-started-webvault.md)。对于管理你的组织，**网页密码库提供了最丰富的 Bitwarden 体验**。

### 注册 Bitwarden <a href="#sign-up-for-bitwarden" id="sign-up-for-bitwarden"></a>

[创建一个 Bitwarden 账户](https://vault.bitwarden.com/#/register)，并确保您挑选了一个强大而难忘的[主密码](../account/log-in-and-unlock/your-master-password.md)。我们甚至建议您写下您的主密码，并将其存储在安全的地方。

{% hint style="success" %}
**不要忘记您的主密码！**&#x42;itwarden 是一种零知识的解决方案，这意味着 Bitwarden 团队以及 Bitwarden 系统本身对您的主密码一无所知，也没有办法找回或重置你的主密码。
{% endhint %}

创建账户后，登录到[网页 App](../getting-started/getting-started-webvault.md) 然后验证账户的电子邮箱地址以解锁对所有功能的访问权限：

{% embed url="https://bitwarden.com/assets/7bJkgn3Qjoon9c1h68WmgW/035a83d213860b7c5b92a29502fc315f/2024-12-03_13-54-17.png?w=1043&fm=avif&q=80" %}
发送验证电子邮件
{% endembed %}

### 再次注册 Bitwarden <a href="#sign-up-for-bitwarden-again" id="sign-up-for-bitwarden-again"></a>

为了使用免费的 2 人组织进行安全共享，您需要拥有 2 个 Bitwarden 账户。设置了第一个 Bitwarden 账户后，请按照相同的步骤（或帮助您的朋友或伴侣操作）来设置另一个账户。

{% hint style="success" %}
Bitwarden 组织具有深层次的[用户级别访问控制](manage-members/member-roles.md)。无论您用哪个用户来[设置您的组织](organizations-quick-start.md#setup-your-organization)，其都将成为**所有者**。
{% endhint %}

## 设置您的组织 <a href="#setup-your-organization" id="setup-your-organization"></a>

要设置您的组织：

1、在 Bitwarden 网页 App 中，选择 ✚**新建组织**按钮。

{% embed url="https://bitwarden.com/assets/3eSqWiTIuPSFxXdo5AAjT9/248b0fa7bb381add0d71682acd244a63/2024-12-03_13-57-58.png?w=1043&fm=avif&q=80" %}
**新建组织**
{% endembed %}

2、输入**组织名称**和**账单电子邮件**，我们可以通过此地址与您联系。在本指南中，我们将设置一个免费的组织，所以您将不会被收取任何费用。

**3、选择您的计划**。Bitwarden 提供适合任何需求的组织，但在这种情况下，请选择**免费**。

4、向下滚动并选择**提交**以完成组织的创建。

### 了解您的组织 <a href="#get-to-know-your-organization" id="get-to-know-your-organization"></a>

创建完成后，您将进入组织密码库，这是所有内容共享和组织管理的中心。作为[组织所有者](manage-members/member-roles.md)，您将能够查看您的**密码库**，管理用户和[集合](organizations-quick-start.md#get-to-know-collections)，使用一些 Bitwarden **工具**以及配置组织的**设置**：

{% embed url="https://bitwarden.com/assets/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?w=1043&fm=avif&q=80" %}
免费组织管理控制台
{% endembed %}

可以访问管理控制台的用户可以随时在网页 App 中通过左侧导航进入管理控制台：

{% embed url="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&fm=avif&q=80" %}
产品切换器
{% endembed %}

### 了解集合 <a href="#get-to-know-collections" id="get-to-know-collections"></a>

集合是 Bitwarden 组织的重要组成部分；它们代表[属于您的组织](organizations-quick-start.md#shared-items)拥有的密码库项目的逻辑分组。您的组织预设了一个**默认集合**和一个**未分配**标签。对于免费组织，您可以使用**密码库**选项卡创建最多 2 个集合：

{% embed url="https://bitwarden.com/assets/3rq5lVSQlvNT9gu2M2bCbk/8741dc155e8f2fa83d2caeb69218ce64/2024-12-02_15-35-48.png?w=1038&fm=avif&q=80" %}
创建新的集合
{% endembed %}

{% hint style="success" %}
在很多方面，集合类似于用来组织个人密码库的[文件夹](../your-vault/folders.md)。一个关键的区别是，[属于您的组织](organizations-quick-start.md#shared-items)的项目**必须包括在至少一个集合中**。
{% endhint %}

## 将用户添加到您的组织 <a href="#add-a-user-to-your-organization" id="add-a-user-to-your-organization"></a>

现在您已经熟悉了您的组织，现在是添加您将与之共享的其他组织成员的好时机。为了确保您组织的安全，Bitwarden 应用了一个 3 步流程来加入新成员，[邀请 ](organizations-quick-start.md#invite)→ [接受](organizations-quick-start.md#accept) → [确认](organizations-quick-start.md#confirm)。

{% hint style="info" %}
需要完成[邀请 ](organizations-quick-start.md#invite)→ [接受](organizations-quick-start.md#accept) → [确认](organizations-quick-start.md#confirm)的完整流程，才能确保成员获得对共享组织项目的完整访问权限。
{% endhint %}

### 邀请 <a href="#invite" id="invite"></a>

作为组织所有者，邀请新成员的步骤如下：

1、在管理控制台中，从导航栏选择**成员**选项卡然后选择 ✚**邀请成员**按钮：

{% embed url="https://bitwarden.com/assets/7AJjR4oqEnCH3A89YYoWpH/a4bd30d71a74ead44e13768dab8c5dff/2024-12-03_14-02-20.png?w=1043&fm=avif&q=80" %}
邀请成员加入组织
{% endembed %}

2、在**角色**选项卡中，输入第二个成员的**电子邮件**，该电子邮件应与他们[注册 Bitwarden](organizations-quick-start.md#sign-up-for-bitwarden-again) 的电子邮件相匹配。然后，选择一个[成员角色](manage-members/member-roles.md#member-roles)。

3、在**集合**选项卡中，选择允许该用户可以访问的集合，以及授予对每个集合的[权限](manage-members/member-roles.md#permissions)级别。

4、选择**保存**将邀请发送到指定的电子邮件地址。

发送邀请后，通知您的新成员并帮助他们[接受邀请](organizations-quick-start.md#accept)。

### 接受 <a href="#accept" id="accept"></a>

作为新的被邀请的成员，打开您的电子邮件收件箱并查找来自 Bitwarden 的邀请您加入组织的电子邮件。单击电子邮件中的链接将打开 Bitwarden 网页客户端邀请窗口：

{% embed url="https://bitwarden.com/_gatsby/image/958ce51e71025d451256ade85e478bd5/106d26c390438e4a0c9b999390e67465/Screen%20Shot%202023-04-28%20at%2010.40.35%20AM.webp?eu=8dd856e2e49af48f5e3da0816923316db66950f8f85437d93b67b2f91caa9b8120a14a5d21962bb22a6e0fddd5e416b23392716411ebd1dfc4ed1af4b93dad095bd75cb866e5710e592cc4fee2fd0e443d944b0ca9829a01f66b72d4e6b6bf774b01152ba92bbad7bfa83767b1d52e61e8e4f32f3794a120a4561e17c1076ea539eac78b7000bd8ae64eaca5bbed4ad3c2b269184799ad66642d4d4950b06abcbab46e3b4149031c7daff019a333cced5f7b3e77191744e86e39d854ae6e3695b0aef458d92e7eb2fe9c317684c7a983eb19af7f20e09a73b6e168385b58f27ccee424b3bd66060c8237fa9151b00b6a6404ed1d893a24d9265c8968f59c59d376ab&a=w%3D601%26h%3D594%26fm%3Dwebp%26q%3D75&cd=2023-04-28T14%3A41%3A41.708Z" %}
Bitwarden 邀请
{% endembed %}

由于您已经[注册了 Bitwarden](organizations-quick-start.md#sign-up-for-bitwarden-again)，请选择**登录**。完全登录到您的密码库将接受邀请。

{% hint style="info" %}
邀请将在 5 天后到期。确保您在该窗口内接受邀请，否则组织所有者将不得不[重新邀请您](organizations-quick-start.md#invite)。
{% endhint %}

### 确认 <a href="#confirm" id="confirm"></a>

确认组织接受成员是授予成员访问共享项目权限的最后一步。要完成此循环：

1、在管理控制台中，从导航栏选择**成员**选项卡。

2、选中任何`已接受`的用户并使用 **≡选项**菜单 **✔︎确认所选**：

{% embed url="https://bitwarden.com/assets/5eRDRAooRSGqRWJYZB5fgz/95422412e2a27069ca903f4a6ec1a8a7/2024-12-03_14-04-59.png?w=1197&fm=avif&q=80" %}
确认成员加入组织
{% endembed %}

3、验证您屏幕上显示的[指纹短语](../security/encryption/account-fingerprint-phrase.md)是否与您的新成员的匹配，指纹短语可以在**设置** → **我的账户**中找到。

每一个指纹短语对于其账户都是唯一的，它是确保安全添加用户的最后一层监督。如果它们匹配，请选择**提交**。

## 了解您的密码库 <a href="#get-to-know-your-vault" id="get-to-know-your-vault"></a>

Bitwarden组织的神奇之处在于，属于您的项目和[属于组织](organizations-quick-start.md#shared-items)的项目可以在**密码库**视图中并排访问。您可以在个人项目（**我的密码库**）和组织项目（**我的组织**）之间进行筛选：

{% embed url="https://bitwarden.com/assets/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?w=1197&fm=avif&q=80" %}
已启用的组织密码库
{% endembed %}

### 从组织共享的项目 <a href="#items-shared-from-an-organization" id="items-shared-from-an-organization"></a>

您可能还没有[从组织共享的项目](organizations-quick-start.md#items-shared-from-an-organization)，但是当您共享项目时，它会显示在您的密码库中，并带有一个**已共享**图标：

{% embed url="https://bitwarden.com/assets/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?w=604&fm=avif&q=80" %}
已共享项目徽章
{% endembed %}

已共享的项目归组织**所有**。这意味着任何有权限的人都可以更改或删除该项目，删除该项目也会将其从您的密码库中移除。

## 移动项目到组织 <a href="#move-an-item-to-the-organization" id="move-an-item-to-the-organization"></a>

安全共享之路的最后一步是创建一个项目并将其移动到组织以便共享。现有的[密码库项目](../your-vault/vault-items.md)可以在创建后被移动到组织，但在本指南中，我们将重点放在如何从您的个人密码库创建一个**新的**登录：

1. 在 **🔒我的密码库**页面上，选择 ✚**添加项目**按钮。
2. 为您的新登录项填写所有相关信息（例如用户名和密码）。该项目可以是您希望自己和其他组织用户都可以访问的任何内容，例如家庭流媒体帐户。
3. 在添加项目面板底部的**所有权**部分，勾选您的组织以指定用于共享的项目。
4. 选择一个或多个用于存放此项目的**集合**。两人组织的用户通常设置为两人对所有集合的访问权限。在更大或更复杂的组织中，您将项目存放到哪个集合将决定谁可以访问它。
5. 选择**保存**按钮完成组织所有的项目的创建。

您和组织的其他用户都可以访问这个新的项目！只要两个用户都可以访问它所在的集合，它就会与其他个人密码库项目一起出现在组织密码库以及**我的密码库**视图中。

### 从组织中取消共享项目 <a href="#unshare-an-item-from-an-organization" id="unshare-an-item-from-an-organization"></a>

如果您与某个组织共享了一个项目，有两个选项可以取消与该组织共享该项目。

1. 使用产品切换器打开管理控制台，从选项菜单中选择要**克隆**的项目，将项目克隆回您的个人密码库。只有用户类型为管理员或更高级别的用户才能通过更改**所有权**设置将项目克隆到其个人密码库中。
2. 从同一菜单中选择**删除**，从而从组织密码库中删除项目。

或者，也可以将项目移动到具有更高访问控制权限限制的其他集合中，从而取消共享。

## 恭喜！ <a href="#congratulations" id="congratulations"></a>

您已经设置了新的 Bitwarden 账户、创建了一个组织、了解了一些有关您的密码库的知识、并共享了一个项目！干得好！如果您想升级到付费组织以解锁[许多附加功能](../plans-and-pricing/password-manager/about-bitwarden-plans.md)，请导航到您的组织**设置** → **订阅**视图，然后选择**升级计划**按钮：

{% embed url="https://bitwarden.com/assets/c7MRk3qA3cxcVZHC2gBBs/4128a414a194af6e446ac39d9c250990/2024-12-03_14-09-22.png?w=1197&fm=avif&q=80" %}
升级免费组织
{% endembed %}

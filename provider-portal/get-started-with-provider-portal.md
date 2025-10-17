# 提供商门户快速入门

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/getting-started-providers/)
{% endhint %}

{% hint style="success" %}
有兴趣成为提供商吗？首先，我们要求：

* 您的业务有一个活跃的企业组织。&#x20;
* 您的业务有一个客户准备在您的提供商下入职。

[成为合伙人](https://bitwarden.com/partners/become-a-partner/)
{% endhint %}

## 为什么选择 Bitwarden 提供商？ <a href="#why-bitwarden-providers" id="why-bitwarden-providers"></a>

托管服务提供商（MSP）和经销商通常需要一种方式代表企业客户快速创建和轻松管理 Bitwarden 组织。**提供商**是管理实体，允许这些企业通过**提供商门户**创建和管理[客户组织](get-started-with-provider-portal.md#client-organizations)。通过提供商门户，可以：

* 查看所有受 MSP 管理的客户、上线新客户和现有客户、访问客户组织的集合，并为团队和企业组织管理服务。
* 将内部员工添加为成员，分配适当的用户角色，并委派管理职责。
* 查看用户在提供商门户网站上进行的带有时间戳的操作，包括创建新客户组织、邀请新提供商用户以及提供商用户何时访问了客户组织。

提供商门户是一个一体化的管理体验，使提供商能够大规模管理客户的 Bitwarden 组织。提供商门户通过一个集中的专用空间来访问和支持每一个客户，或创建一个新客户，从而简化管理任务：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7AoSHeZgJJTBXQmpZ13UBr/56ca464fe6987c8c5fc8e7099235d640/2025-02-25_15-17-46.png?_a=DAJCwlWIZAAB" %}
提供商门户
{% endembed %}

### 开始提供商之路 <a href="#start-a-provider" id="start-a-provider"></a>

[联系我们](https://bitwarden.com/contact)注册提供商计划。在您注册后，Bitwarden 团队的一名成员将与您联系并发出邀请以开启提供商之路：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3zxOwQqwIYO3hte6htfbiv/7e55c649273467fadb6d87bbd229a209/provider-invitation.png?_a=DAJCwlWIZAAB" %}
提供商邀请
{% endembed %}

选择 **Setup Provider Now** 按钮将提示您登录 Bitwarden，然后填写一些提供商的详细信息。

### 入职用户 <a href="#onboard-users" id="onboard-users"></a>

作为提供商的创建者，您将自动获得[提供商管理员](provider-users.md#provider-user-types)的身份，让您能够全面管理提供商和所有[客户组织](get-started-with-provider-portal.md#client-organizations)的所有方面。Bitwarden 强烈建议您为故障转移目的配置第二个提供商管理员。

现在，开始将您的员工添加为[服务用户](provider-users.md#provider-user-types)，这将使他们能够全面管理所有客户组织并创建新的组织或管理提供商本身：

1、**邀请用户**。从提供商门户 **☷管理** → **成员**选项卡中，邀请用户作为服务用户（或邀请其他提供商管理员）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6E5GA111xdiHHkA0gb5LtG/5e5b5fddb5911e1b2ed468c1d49134ad/2024-12-05_09-27-45.png?_a=DAJCwlWIZAAB" %}
添加提供商用户
{% endembed %}

2、**指导用户接受邀请**。受邀用户将收到一封来自 Bitwarden 的电子邮件，邀请他们加入提供商。通知用户他们应该收到了一个邀请，并且他们需要使用现有的 Bitwarden 账户**登录**或**创建账户**以继续：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/0FRQnrWufrfnbc8Q2GymX/ffcb260e1d90ff1a25d0f67ac9bc6c7a/provider-accept-invite.png?fm=webp&h=314&q=50&w=344" %}
提供商邀请
{% endembed %}

3、**确认已接受的邀请**。要完成提供商用户的安全入职，请从提供商门户的**人员**选项卡确认已接受的邀请：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/IxUeScxNYYmI4y8jceC5v/ebdf3fa89abbd69fbb028e0cff8c99aa/2024-12-05_09-29-04.png?_a=DAJCwlWIZAAB" %}
确认已邀请的提供商用户
{% endembed %}

有了服务用户组成的团队，您就可以开始设置[客户组织](get-started-with-provider-portal.md#client-organizations)了。

## 客户组织 <a href="#client-organizations" id="client-organizations"></a>

客户组织是附属于提供商或由提供商管理的任何[组织](../admin-console/organizations-overview.md)。对于您的客户来说，除了谁负责管理，「客户」组织和「常规」组织之间没有区别。

组织将 Bitwarden 用户和密码库项目联系在一起，用于[安全地共享](../password-manager/vault-basics/organization-members/sharing.md)登录、支付卡、笔记和身份信息。组织有一个独立的密码库，提供商服务用户可以在其中管理组织的项目、用户和设置：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5fXREt9aHmnVgLLRPBs8yg/dbecd580231e8ea2f4eec2be224a1e64/2025-02-25_15-20-08.png?_a=DAJCwlWIZAAB" %}
客户组织密码库
{% endembed %}

客户组织的成员（即您客户的最终用户）将在他们的**密码库**视图中找到已共享的项目以及个人拥有的项目，还可以使用多种方法过滤项目列表，使其只显示组织项目或特定[集合](../admin-console/manage-shared-items/collections/about-collections.md)中的项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?_a=DAJCwlWIZAAB" %}

### 创建客户组织 <a href="#create-a-client-organization" id="create-a-client-organization"></a>

要创建新的客户组织，您必须是提[供商管理员](provider-users.md#provider-user-types)。导航到提供商门户的**客户**选项卡，然后选择 ✚**添加**按钮 → **新增客户**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5WjBETB0YFm7TS1zpIHeSC/a22563b9172036b1c90bfb61d9ab310b/new_client_org_1.png?_a=DAJCwlWIZAAB" %}
新增客户组织
{% endembed %}

### 添加现有组织 <a href="#add-an-existing-organization" id="add-an-existing-organization"></a>

要添加现有组织，您必须是活跃的提供商用户，并且是要添加的组织的所有者。

{% hint style="info" %}
服务用户只能在提供商的最小席位范围内添加组织。 如果组织席位超过了提供商的可用席位，该组织将处于禁用状态。
{% endhint %}

1、前往提供商门户的户端标签页，然后选择 ✚**新增**按钮 → **现有组织**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/mA88mJFGTc9w6MEcisaME/af9d5d7d413cb01d9d18df783fd934fc/Existing_client_org.png?_a=DAJCwlWIZAAB" %}
管理控制台添加现有组织
{% endembed %}

2、将出现添加现有组织的对话框。选择您要添加的组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/19Ugi6eUIMQgcliZvxwuf3/9992b070d0dab4defa04639bef8baf01/2025-02-25_15-45-02.png?_a=DAJCwlWIZAAB" %}
选择现有组织
{% endembed %}

3、将提示您确认对提供商订阅的订阅和计费更改。完成后，选择**添加组织**。

### 设置客户组织 <a href="#setup-the-client-organization" id="setup-the-client-organization"></a>

使用您新创建的客户组织，开始为您的客户构建完美的解决方案。根据客户的需求，每个客户组织的确切设置会有所不同，但通常涉及：

1、**创建集合**。一个好的第一步是[创建一组集合](../admin-console/manage-shared-items/collections/about-collections.md#create-a-collection)，它为您在下一步中添加到密码库的项目提供组织结构。

常见的集合模式包括**按部门的集合**（即客户营销团队中的用户被分配到**营销**集合）或**按功能的集合**（即来自客户营销团队的用户被分配到**社交媒体**集合）：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6kJ7wMESirqmkfZ8KlfK09/9210ef5cf3cd2442b429760edb98001f/collections-graphic-1.png?fm=webp&h=140&q=50&w=509" %}
集合
{% endembed %}

2、**导入数据**。存储密码库项目的结构就位后，您就可以开始向组织导入数据了。

{% hint style="info" %}
请注意，作为提供商用户，您将无法直接查看、创建或管理个人项目。
{% endhint %}

3、**配置企业策略**。在开始用户管理部分的设置之前，[配置企业策略](../admin-console/oversight-visibility/enterprise-policies.md)以便为诸如[主密码复杂性](../admin-console/oversight-visibility/enterprise-policies.md#master-password)、[两步登录的使用](../admin-console/oversight-visibility/enterprise-policies.md#two-step-login)和[管理员密码重置](../admin-console/oversight-visibility/enterprise-policies.md#master-password-reset)等设置使用规则。

{% hint style="info" %}
企业策略**仅适用于企业组织**。
{% endhint %}

4、**设置 SSO 登录**。如果您的客户使用单点登录（SSO）与其他应用程序进行身份验证，请[将 Bitwarden 与他们的 IdP 连接](../login-with-sso/about-login-with-sso.md)，以允许使用最终用户的 SSO 凭据与 Bitwarden 进行身份验证。

5、**创建用户群组**。对于团队和企业组织，创建一组群组用于可扩展权限的分配。当您开始添加用户时，将他们添加到群组，以让每个用户自动继承群组的配置权限（例如可以访问哪些集合）。

一种常见的群组-集合模式是创建**按部门的群组**和**按功能的集合**，例如：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6qodHGqBPABEFv3XJxaOUe/780cd4624a5d0a5fe315677968003e2d/collections-graphic-2.png?fm=webp&h=304&q=50&w=449" %}
集合
{% endembed %}

### 邀请客户用户 <a href="#invite-client-users" id="invite-client-users"></a>

有了用于安全地和可扩展地共享凭据的基础架构，您就可以开始邀请用户加入组织了。可以通过两种方式让用户加入 Bitwarden，具体取决于您的客户规模：

1、**对于小型客户**，您可以从管理员控制台的 **☷成员**视图向用户发送电子邮件邀请：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4wUO7i6w8y4sqAvwuMVZyd/070a5b36b242b1e4871cc0f58e0b8f83/2024-12-05_09-31-35.png?_a=DAJCwlWIZAAB" %}
邀请成员作为提供者
{% endembed %}

2、**对于大型客户**（使用 Azure AD、Okta、OneLogin 或 JumpCloud 等 IdP 的），请使用 [SCIM](../admin-console/manage-members/scim/about-scim.md) 自动布建用户。

3、**对于大型客户**（使用活动目录、LDAP、Okta 等目录服务的），请使用[目录连接器](../admin-console/manage-members/directory-connector/)从源目录同步组织用户并自动发出邀请。

无论您是从组织密码库邀请用户还是使用目录连接器，在[入职提供商用户](get-started-with-provider-portal.md#onboard-users)时遵循的 3 步过程（邀请 → 接受 → 确认）也适用于这里。

## 管理自托管组织 <a href="#managing-self-hosted-organizations" id="managing-self-hosted-organizations"></a>

MSP 还可以为 Bitwarden 自托管实例提供管理支持和经销商服务。目前，对托管客户的提供商门户访问仅适用于云托管环境。要为自托管实例提供管理服务，需要购买额外的服务席位来管理自托管实例。

### 启用自托管实例 <a href="#enabling-the-self-hosted-instances" id="enabling-the-self-hosted-instances"></a>

1、创建一个新的 Bitwarden 用户作为服务账户。在初始安装期间，该用户将被授予以所有者身份管理客户的访问权限。

{% hint style="info" %}
如果您的客户端组织托管在同一服务器上，则此服务账户可以是被授予对所有组织的访问权限的单个用户。否则，请为每个客户或服务器创建单独的服务账户。
{% endhint %}

2、将新创建的用户凭据保存在您的内部 Bitwarden 密码库中。

接下来，访问位于主导航栏上的**提供商门户**。从提供商门户[创建一个新的企业组织](get-started-with-provider-portal.md#create-a-client-organization)。

{% hint style="info" %}
此步骤的目的是保存凭据，您不需要邀请用户加入您的组织。
{% endhint %}

3、在创建企业组织的过程中，添加在**步骤 1** 中创建的服务用户账户。

4、通过提供商门户访问客户端以下载组织许可证。

5、部署 Bitwarden 自托管实例然后[应用组织许可证](../self-hosting/licensing.md#apply-organization-license)。

6、将用户提升为托管客户的新的所有者。

{% hint style="info" %}
可选，新用户被提升为客户组织的经理后，您的服务账户用户可以被降级为自定义管理员角色。
{% endhint %}

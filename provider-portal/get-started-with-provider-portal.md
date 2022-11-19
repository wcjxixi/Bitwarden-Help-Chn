# 提供商门户入门

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/getting-started-providers/)
{% endhint %}

{% hint style="success" %}
有兴趣成为提供商吗？首先，我们要求：

* 您的企业有一个活跃的企业组织。&#x20;
* 您的企业有一个客户准备在您的提供商下入职。

如果您还没有准备好开始成为提供商，Bitwarden 团队希望支持你作为一个经销商或客户的 Bitwarden 之旅。

[联系我们](https://bitwarden.com/contact)
{% endhint %}

## 为什么选择 Bitwarden 提供商？ <a href="#why-bitwarden-providers" id="why-bitwarden-providers"></a>

托管服务提供商（MSP）和经销商通常需要一种方式代表企业客户快速创建和轻松管理 Bitwarden 组织。**提供商**是管理实体，允许这些企业通过**提供商门户**创建和管理[客户组织](get-started-with-provider-portal.md#client-organizations)。

提供商门户是一个一体化的管理体验，使提供商能够大规模管理客户的 Bitwarden 组织。提供商门户通过一个集中的专用空间来访问和支持每一个客户，或创建一个新客户，从而简化管理任务：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1PDUxFYw625wXCGDgYLez6/af8b2727c68469aa610409e97d1bb740/provider.png?fm=webp&h=359&q=50&w=691" %}
提供商门户
{% endembed %}

### 开始提供商之路 <a href="#start-a-provider" id="start-a-provider"></a>

[联系我们](https://bitwarden.com/contact)注册提供商计划。在您注册后，Bitwarden 团队的一名成员将与您联系并发出邀请以开启提供商之路：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3zxOwQqwIYO3hte6htfbiv/7e55c649273467fadb6d87bbd229a209/provider-invitation.png?fm=webp&h=309&q=50&w=552" %}
提供商邀请
{% endembed %}

选择 **Setup Provider Now** 按钮将提示您登录 Bitwarden，然后填写提供商的详细信息：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2yZmmIgtDtUMnwzMk46sHH/3b2e25622d3994f66d51a98a7700a4f2/provider-enrollment.png?fm=webp&h=363&q=50&w=783" %}
提供商设置
{% endembed %}

### 入职用户 <a href="#onboard-users" id="onboard-users"></a>

作为提供商的创建者，您将自动获得[提供商管理员](provider-users.md#provider-user-types)的身份，让您能够全面管理提供商和所有[客户组织](get-started-with-provider-portal.md#client-organizations)的所有方面。 Bitwarden 强烈建议您为故障转移目的配置第二个提供商管理员。

现在，开始将您的员工添加为[服务用户](provider-users.md#provider-user-types)，这将使他们能够全面管理所有客户组织并创建新的组织或管理提供商本身：

1、**邀请用户**。从提供商门户**管理**选项卡中，邀请用户作为服务用户（或邀请其他提供商管理员）：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6E5GA111xdiHHkA0gb5LtG/cbb05eb7912d47eedc497e9a0268519c/provider-adduser.png?fm=webp&h=299&q=50&w=765" %}
添加提供商用户
{% endembed %}

2、**指导用户接受邀请**。受邀用户将收到一封来自 Bitwarden 的电子邮件，邀请他们加入提供商。通知用户他们应该收到了一个邀请，并且他们需要使用现有的 Bitwarden 帐户**登录**或**创建帐户**才能继续：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/0FRQnrWufrfnbc8Q2GymX/ffcb260e1d90ff1a25d0f67ac9bc6c7a/provider-accept-invite.png?fm=webp&h=314&q=50&w=344" %}
提供商邀请
{% endembed %}

3、**确认已接受的邀请**。要完成提供商用户的安全入职，请从提供商门户的**管理**选项卡确认已接受的邀请：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/IxUeScxNYYmI4y8jceC5v/fc877a45f3894d4933b987601beac1b7/provider-confirm.png?fm=webp&h=372&q=50&w=774" %}
确认邀请的提供商用户
{% endembed %}

有了服务用户组成的团队，您就可以开始设置[客户组织](get-started-with-provider-portal.md#client-organizations)了。

## 客户组织 <a href="#client-organizations" id="client-organizations"></a>

客户组织是附属于提供商或由提供商管理的任何[组织](../organizations/organizations.md)。对于您的客户来说，除了谁负责管理，「客户」组织和「常规」组织之间没有区别。

组织将 Bitwarden 用户和密码库项目联系在一起，用于[安全地共享](../organizations/sharing.md)登录、支付卡、笔记和身份信息。组织有一个独立的密码库，提供商服务用户可以在其中管理组织的项目、用户和设置：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2Q6QjDRciHQAhKd7zPZkvD/95274cdb2fe38c44fcfa4ce725188d04/client-org.png?fm=webp&h=265&q=50&w=764" %}
客户组织的查看
{% endembed %}

客户组织的成员（即您客户的最终用户）将在他们的**我的密码库**视图中与个人项目一起找到已共享的项目，以及已分配[集合](../organizations/collections.md)的筛选器，集合对组织项目进行分组，类似于[文件夹](../your-vault/folders.md)组织个人项目：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2qhSaHsOWf7vnZ4yvpfXrZ/71a61811bf3f6e9e4f0f5acb14bf55c6/personal-vault-org-enabled.png?fm=webp&h=403&q=50&w=766" %}
最终用户密码库
{% endembed %}

### 创建一个客户组织 <a href="#create-a-client-organization" id="create-a-client-organization"></a>

要创建新的客户组织，您必须是提[供商管理员](provider-users.md#provider-user-types)。导航到提供商门户的**客户**选项卡，然后选择 ✚**新建客户组织**按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5WjBETB0YFm7TS1zpIHeSC/38b2b8a919d8b9c6cd6d0af286f90d71/provider-add-client.png?fm=webp&h=291&q=50&w=691" %}
创建客户组织
{% endembed %}

### 设置客户组织 <a href="#setup-the-client-organization" id="setup-the-client-organization"></a>

使用您新创建的客户组织，开始为您的客户构建完美的解决方案。根据客户的需求，每个客户组织的确切设置会有所不同，但通常涉及：

1、**创建集合**。一个好的第一步是[创建一组集合](../organizations/collections.md#create-a-collection)，它为您在下一步中添加到密码库的项目提供组织结构。

常见的集合模式包括**按部门的集合**（即客户营销团队中的用户被分配到**营销**集合）或**按功能的集合**（即来自客户营销团队的用户被分配到**社交媒体**集合）：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6kJ7wMESirqmkfZ8KlfK09/9210ef5cf3cd2442b429760edb98001f/collections-graphic-1.png?fm=webp&h=140&q=50&w=509" %}
集合
{% endembed %}

2、**填充组织密码库**。存储密码库项目的结构就位后，就可以开始使用客户的登录、笔记、支付卡和身份来填充组织了。

{% hint style="success" %}
您可以从头开始[创建共享项目](../organizations/sharing.md#create-an-organization-item)，但我们建议您[导入一个包含其所有密码库项目的文件](../import-export/import-data-to-an-organization.md)。
{% endhint %}

3、**配置企业策略**。在开始用户管理部分的设置之前，[配置企业策略](../organizations/enterprise-policies.md)以便为诸如[主密码复杂性](../organizations/enterprise-policies.md#master-password)、[两步登录的使用](../organizations/enterprise-policies.md#two-step-login)和[管理员密码重置](../organizations/enterprise-policies.md#master-password-reset)等设置使用规则。

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

1、**对于小型客户**，您可以从组织密码库的**管理**选项卡向用户发送电子邮件邀请：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4wUO7i6w8y4sqAvwuMVZyd/3ad582019781e3f8491c0467904329d5/org-people-invite.png?fm=webp&h=369&q=50&w=824" %}
邀请用户
{% endembed %}

2、对于使用目录服务（活动目录、LDAP、Okta 等）的大型客户，使用[目录连接器](../directory-connector/)从源目录同步组织用户并自动发出邀请。

无论您是从组织密码库邀请用户还是使用目录连接器，在[入职提供商用户](get-started-with-provider-portal.md#onboard-users)时遵循的 3 步过程（邀请 → 接受 → 确认）也适用于这里。

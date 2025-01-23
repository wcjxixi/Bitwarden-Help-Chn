# 添加客户组织

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/client-org-setup/)
{% endhint %}

本文将引导您完成[客户组织的创建](start-a-client-organization.md#create-a-client-organization)，并概述了开始管理客户组织的典型[设置步骤](start-a-client-organization.md#initial-setup-procedure)。

## 创建一个客户组织 <a href="#create-a-client-organization" id="create-a-client-organization"></a>

{% hint style="success" %}
**已经为您的客户设置了组织？**&#x60A8;可以[将现有的组织添加到提供商门户](providers-faqs.md#q-im-already-providing-bitwarden-as-a-service-for-my-clients-what-do-i-need-to-do-to-move-to-the-provider-portal)。
{% endhint %}

要创建客户组织，您必须是[提供商管理员](provider-users.md#provider-user-types)：

1、导航到提供商门户并选择 ✚**新建客户组织**按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5WjBETB0YFm7TS1zpIHeSC/38b2b8a919d8b9c6cd6d0af286f90d71/provider-add-client.png?fm=webp&h=291&q=50&w=691" %}
创建客户组织
{% endembed %}

2、在新建客户组织界面上，输入**组织名称**、**账单电子邮件地址**和**客户所有者的电子邮件地址**。

{% hint style="info" %}
邀请将自动发送到**客户所有者的电子邮件地址**，以作为[所有者](../admin-console/user-management/member-roles-and-permissions.md)加入组织。
{% endhint %}

3、从**选择您的计划**列表中，选择要创建的[组织类型](../plans-and-pricing/password-manager/about-bitwarden-plans.md#compare-the-plans)。

{% hint style="success" %}
团队和企业组织包含适用于所有注册用户的高级功能。
{% endhint %}

4、为组织设置以下选项：

* **用户席位**：指定客户组织所需的用户席位的数量。如果超过此数量，则会增加席位，除非您[指定限制](../organizations/user-management.md#set-a-seat-limit)。
* **额外存储空间（GB）**：组织包含了 1GB 的附件加密存储空间。以 $0.33 每 GB 每月添加额外的存储空间。
* **计费周期**：选择您要按年还是按月为此组织计费。

5、您对组织感到满意后，请输入您的**付款信息**并选择**提交**。

6、选择**提交**完成组织的创建。

创建后，从提供商门户导航到客户组织会将您带到组织密码库，您可以从中完成[初始化设置](start-a-client-organization.md#initial-setup-procedure)并参与[持续管理](ongoing-administration.md)：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/A3dca6m6j41ImTfCCcw5x/646a4f68a42be54bf36127b30dc87edc/client-org-manage.png?fm=webp&h=265&q=50&w=764" %}
客户组织密码库
{% endembed %}

## 初始化设置步骤 <a href="#initial-setup-procedure" id="initial-setup-procedure"></a>

有了新创建的客户组织，您就可以开始为客户构建完善的解决方案了。根据您客户的需求，每个客户组织的确切设置会有所不同，但通常会涉及以下步骤：

1、**创建集合**。一个好的第一步是[创建一组集合](../organizations/collections.md#create-a-collection)，集合为您在下一步中添加到密码库的项目提供组织结构。

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

6、**开始邀请用户**。现在，用于安全地和可扩展地共享凭据的基础架构已为您的客户准备就绪，您可以开始邀请用户加入组织了。为确保组织的安全，Bitwarden 对新用户的入职流程采用了 3 步流程，邀请 → 接受 → 确认。

{% hint style="success" %}
如果您的客户使用目录服务（活动目录、LDAP、Okta 等），请使用[目录连接器](../directory-connector/about-directory-connector.md)从源目录自动同步组织用户并自动发出邀请。
{% endhint %}

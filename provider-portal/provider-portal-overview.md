# 提供商门户概览

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/providers/)
{% endhint %}

{% hint style="success" %}
有兴趣成为提供商吗？首先，我们要求：

* 您的企业有一个活跃的企业组织。&#x20;
* 您的企业有一个客户准备在您的提供商下入职。

如果您还没有准备好开始成为提供商，Bitwarden 团队希望支持你作为一个经销商或客户的 Bitwarden 之旅。

[联系我们](https://bitwarden.com/contact)
{% endhint %}

## 什么是提供商？ <a href="#what-are-providers" id="what-are-providers"></a>

提供商是 Bitwarden 中的管理实体，允许托管服务提供商（MSP）和经销商代表个人企业客户创建并全面管理多个[客户组织](provider-portal-overview.md#client-organizations)。客户组织管理可通过**提供商门户**轻松访问：

### 什么是提供商门户 <a href="#what-is-the-provider-portal" id="what-is-the-provider-portal"></a>

提供商门户是一个一体化的管理体验，使提供商能够大规模管理客户的 Bitwarden 组织。提供商门户通过一个集中的专用空间来访问和支持每一个客户，或创建一个新客户，从而简化管理任务：

{% embed url="https://vimeo.com/591278367" %}

提供商由两种不同的[用户类型](provider-users.md#provider-user-types)构建：

* **服务用户**可以完全管理[客户组织](provider-portal-overview.md#client-organizations)。
* **提供商管理员**可以管理[客户组织](provider-portal-overview.md#client-organizations)和管理提供商本身，包括向团队中添加新的服务用户。

## 客户组织 <a href="#client-organizations" id="client-organizations"></a>

客户组织是附属于提供商或由提供商管理的任何[组织](../organizations/organizations.md)。对于您的客户来说，除了谁负责管理，「客户」组织和「常规」组织之间没有区别。提供商的所有成员​​对所有客户组织均拥有**完全**的访问权限：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/28M8mkU03SyVFq70ZgD0Bp/04e3c65eba73892ae3301d366ce97ce1/provider-diagram.png?fm=webp&h=319&q=50&w=719" %}
提供商的结构
{% endembed %}

{% hint style="info" %}
**如上面的图解所示**，如果提供商想使用一个[组织](../organizations/organizations.md)来管理他们自己的凭据，则不应该把它作为一个由提供商管理的客户组织。

为这种情况创建一个独立的组织将确保可以为用户提供适当的[用户类型和对凭据的访问控制](../admin-console/user-management/member-roles-and-permissions.md)。
{% endhint %}

组织将 Bitwarden 用户和密码库项目联系在一起，用于[安全地共享](../organizations/sharing.md)登录、支付卡、笔记和身份信息。组织有一个独立的密码库，提供商服务用户可以在其中管理组织的项目、用户和设置：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5fXREt9aHmnVgLLRPBs8yg/562be7bade97cb202724d81481dd7722/client-org.png?fm=webp&h=265&q=50&w=764" %}
客户组织密码库
{% endembed %}

客户组织的成员（即您客户的最终用户）将在他们的**我的密码库**视图中与个人项目一起找到已共享的项目，以及已分配[集合](../organizations/collections.md)的筛选器，集合对组织项目进行分组，类似于[文件夹](../your-vault/folders.md)组织个人项目：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2qhSaHsOWf7vnZ4yvpfXrZ/71a61811bf3f6e9e4f0f5acb14bf55c6/personal-vault-org-enabled.png?fm=webp&h=403&q=50&w=766" %}
最终用户数据库
{% endembed %}

你填写了提供商注册表并被 Bitwarden 团队的成员设置为提供商后，就可以[开始一个客户组织](start-a-client-organization.md)了。

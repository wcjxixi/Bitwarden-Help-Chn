# 提供商门户概览

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/providers/)
{% endhint %}

{% hint style="success" %}
有兴趣成为提供商吗？首先，我们要求：

* 您的业务有一个活跃的企业组织。&#x20;
* 您的业务有一个客户准备在您的提供商下入职。

[成为合伙人](https://bitwarden.com/partners/become-a-partner/)
{% endhint %}

## 什么是提供商？ <a href="#what-are-providers" id="what-are-providers"></a>

提供商是 Bitwarden 中的管理实体，允许托管服务提供商（MSP）和经销商代表个人企业客户创建并全面管理多个[客户组织](provider-portal-overview.md#client-organizations)。客户组织管理可通过**提供商门户**轻松访问：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4xn04Sj9u8n73TPxZUWi5f/dac0d56f47a05e2d8b28754e997a1391/2025-02-25_15-16-00.png?_a=DAJCwlWIZAAB" %}
产品切换器 - 提供商门户
{% endembed %}

### 什么是提供商门户 <a href="#what-is-the-provider-portal" id="what-is-the-provider-portal"></a>

提供商门户是一个一体化的管理体验，使提供商能够大规模管理客户的 Bitwarden 组织。提供商门户通过一个集中的专用空间来访问和支持每一个客户，或创建一个新客户，从而简化管理任务：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7AoSHeZgJJTBXQmpZ13UBr/56ca464fe6987c8c5fc8e7099235d640/2025-02-25_15-17-46.png?_a=DAJCwlWIZAAB" %}
提供商门户
{% endembed %}

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

组织将 Bitwarden 用户和密码库项目联系在一起，用于[安全地共享](../organizations/sharing.md)登录、支付卡、笔记和身份信息。组织有一个独立的视图，即管理控制台，提供商服务用户可以在其中管理组织的收藏、管理成员和群组、运行报告、导入数据和配置组织设置：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5fXREt9aHmnVgLLRPBs8yg/dbecd580231e8ea2f4eec2be224a1e64/2025-02-25_15-20-08.png?_a=DAJCwlWIZAAB" %}
客户组织密码库
{% endembed %}

客户组织的成员（如您客户的最终用户）可以在其**密码库**视图中找到共享项目和个人拥有的项目，还可以使用多种方法筛选项目列表，使其只显示组织项目或特定[集合](../organizations/collections.md)中的项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?_a=DAJCwlWIZAAB" %}

您[联系了我们](https://bitwarden.com/contact/)并被 Bitwarden 团队的成员设置为提供商后，就可以[开始一个客户组织](start-a-client-organization.md)了。

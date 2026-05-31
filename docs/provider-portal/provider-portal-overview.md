# 提供商门户概览

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/providers/)
{% endhint %}

{% hint style="success" %}
有兴趣成为提供商吗？要开始使用，我们要求：

* 您的业务有一个活跃的企业版组织。&#x20;
* 您的业务有一个客户准备入职到您的提供商下。

[成为合伙人](https://bitwarden.com/partners/)
{% endhint %}

## 什么是提供商？ <a href="#what-are-providers" id="what-are-providers"></a>

提供商是 Bitwarden 中的管理实体，允许托管服务提供商 (MSP) 代表单个企业客户创建并全面管理任意数量的[客户组织](provider-portal-overview.md#client-organizations)。客户组织管理可通过**提供商门户**中的产品切换器轻松访问：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4xn04Sj9u8n73TPxZUWi5f/dac0d56f47a05e2d8b28754e997a1391/2025-02-25_15-16-00.png?w=1080&#x26;fm=avif" alt=""><figcaption><p>产品切换器 - 提供商门户</p></figcaption></figure></div>

### 什么是提供商门户 <a href="#what-is-the-provider-portal" id="what-is-the-provider-portal"></a>

提供商门户是一种一体化的管理体验，使提供商能够大规模管理客户的 Bitwarden 组织。提供商门户通过一个专用空间来集中访问和支持每一个客户，或创建一个新客户，从而简化管理任务：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7AoSHeZgJJTBXQmpZ13UBr/56ca464fe6987c8c5fc8e7099235d640/2025-02-25_15-17-46.png?w=1050&#x26;fm=avif" alt=""><figcaption><p>提供商门户</p></figcaption></figure></div>

提供商由两种不同的[用户类型](provider-users.md#provider-user-types)构建：

* **服务用户**可以管理[客户组织](provider-portal-overview.md#client-organizations)。
* **提供商管理员**可以管理[客户组织](provider-portal-overview.md#client-organizations)和管理提供商本身，包括向团队中添加新的服务用户。

## 客户组织 <a href="#client-organizations" id="client-organizations"></a>

客户组织是指任何隶属于提供商或由提供商管理的[组织](../admin-console/organizations-overview.md)。对于您的客户来说，「客户」组织和「常规」组织之间没有区别，唯一的区别在于谁在进行管理。

提供商的所有成员都可以访问所有​​所有客户组织，但客户组织的成员无法查看或访问提供商的其他客户组织：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/28M8mkU03SyVFq70ZgD0Bp/04e3c65eba73892ae3301d366ce97ce1/provider-diagram.png?w=719&#x26;fm=avif" alt=""><figcaption><p>提供商的结构</p></figcaption></figure></div>

{% hint style="info" %}
**如上面的图解所示**，如果提供商想使用一个[组织](../admin-console/organizations-overview.md)来管理他们自己的凭据，则**不应**把它作为一个由提供商管理的客户组织。

为这种情况创建一个独立的组织，将确保可以为用户提供适当的[用户类型和对凭据的访问控制](../admin-console/manage-members/member-roles.md)。
{% endhint %}

组织将 Bitwarden 用户和密码库项目联系在一起，用于[安全地共享](../password-manager/organization-members/sharing.md)登录、支付卡、笔记和身份。组织有一个独立的视图，即管理控制台，提供商服务用户可以在其中管理组织的集合、管理成员和群组、运行报告、导入数据和配置组织设置：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5fXREt9aHmnVgLLRPBs8yg/dbecd580231e8ea2f4eec2be224a1e64/2025-02-25_15-20-08.png?w=1050&#x26;fm=avif" alt=""><figcaption><p>客户组织密码库</p></figcaption></figure></div>

客户组织的成员（即您客户的最终用户）将在他们的**密码库**视图中找到已共享的项目以及个人拥有的项目，还可以使用多种方法筛选项目列表，使其只显示组织项目或特定[集合](../admin-console/manage-shared-items/collections/about-collections.md)中的项目：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?w=1197&#x26;fm=avif" alt=""><figcaption><p>启用了组织的密码库</p></figcaption></figure></div>

[联系我们](https://bitwarden.com/contact-sales/)并经 Bitwarden 团队成员为您设置提供商后，即可开始[创建客户组织](start-a-client-organization.md)。

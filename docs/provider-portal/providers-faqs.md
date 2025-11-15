# 提供商 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/providers-faqs/)
{% endhint %}

## 提供商门户 <a href="#provider-portal" id="provider-portal"></a>

### 问：使用提供商门户是否需要启动费或月费？ <a href="#q-is-there-a-startup-or-monthly-fee-for-using-the-provider-portal" id="q-is-there-a-startup-or-monthly-fee-for-using-the-provider-portal"></a>

**答：**&#x4D;SP 或其用户使用提供商门户无需付费。它作为 Bitwarden 合作伙伴计划的一部分免费提供。如果您想建立一个组织供您的内部团队使用，这些席位将按折扣价计费。

### 问：如果我的门户管理员账户被锁定会怎样？ <a href="#q-what-happens-if-i-am-locked-out-of-my-provider-admin-account" id="q-what-happens-if-i-am-locked-out-of-my-provider-admin-account"></a>

**答：**&#x901A;过您的 Bitwarden 账户来访问提供商门户。如果您忘记了您的主密码，Bitwarden 不知道，也没有办法找回或重置您的主密码，您将无法访问提供商门户。**Bitwarden 强烈建议您配置第二个具有提供商管理员角色的用户，以实现故障切换。**

## 部署 <a href="#deployment" id="deployment"></a>

### 问：有哪些部署选项可用？ <a href="#q-what-deployment-options-are-available" id="q-what-deployment-options-are-available"></a>

**答：**&#x53EF;以通过 Bitwarden 云服务访问 Bitwarden 提供商门户。目前，自托管环境不支持提供商门户功能。

## 客户管理 <a href="#client-management" id="client-management"></a>

### 问：对于新客户入职，是否有推荐的工作流程？ <a href="#q-is-there-a-recommended-workflow-for-onboarding-new-clients" id="q-is-there-a-recommended-workflow-for-onboarding-new-clients"></a>

**答：**&#x6709;！我们[在这里](start-a-client-organization.md)概述了一种推荐的工作流程。

### 问：MSP 如何访问客户组织？ <a href="#q-how-does-an-msp-access-client-organizations" id="q-how-does-an-msp-access-client-organizations"></a>

**答：**&#x4D;SP 可以从提供商门户访问受管理的所有客户组织。在[此处](ongoing-administration.md)了解更多信息。

### 问：MSP 管理员能否查看或管理所有客户的凭据？ <a href="#q-can-an-msp-administrator-see-or-manage-credentials-for-all-clients" id="q-can-an-msp-administrator-see-or-manage-credentials-for-all-clients"></a>

**答：**&#x63D0;供商管理员和服务用户与客户组织中的所有者具有相同的权限。他们可以管理组织内的密码库项目、集合、用户、群组和其他功能。提供商管理员和服务用户无法访问或查看用户私有的密码库项目。

### 问：我们可以设置适用于所有客户的默认企业策略吗？ <a href="#q-can-we-set-default-enterprise-policies-that-apply-to-all-clients" id="q-can-we-set-default-enterprise-policies-that-apply-to-all-clients"></a>

**答：**&#x6BCF;个客户组织都通过单独配置的策略独立运作。[了解有关配置企业策略的更多信息](../admin-console/oversight-visibility/enterprise-policies.md)。

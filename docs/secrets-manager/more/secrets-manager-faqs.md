# Secrets Manager FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-faqs/)
{% endhint %}

## 问：Secrets Manager 是如何定价的？ <a href="#q-how-is-secrets-manager-priced" id="q-how-is-secrets-manager-priced"></a>

**答：**&#x42;itwarden Secrets Manager 提供免费订阅，具有无限数量的机密存储空间以及最多 2 个用户、3 个工程和 3 个机器账户。

对于团队和企业，Bitwarden Secrets Manager 提供团队和企业订阅，具有高级业务功能，如审核日志、目录和 SCIM 集成以及企业策略。

Teams 订阅起价为 $6/用户/月，拥有无限数量的机密、用户和工程，以及最多 20 个机器账户。Enterprise 订阅起价为 $12/用户/月，拥有无限数量的机密、用户和工程，以及最多 50 个机器账户。

[了解更多有关 Secrets Manager 定价的信息](https://bitwarden.com/products/secrets-manager/#pricing)。

## 问：我可以自行托管 Secrets Manager 吗？ <a href="#q-can-i-self-host-secrets-manager" id="q-can-i-self-host-secrets-manager"></a>

**答：**&#x4F01;业组织可以在现有的自托管安装旁边自行托管 Bitwarden Secrets Manager。如果您之前没有自行托管过 Bitwarden，请使用[本指南](../../self-hosting/plan-for-deployment/self-host-an-organization.md)让自己走上正确的道路。

如果您已经自行托管 Enterprise Bitwarden 组织并希望访问该服务器上的 Secrets Manager：

1. 在云托管的 Bitwarden 组织中注册 Secrets Manager 订阅。
2. 将您的自托管服务器至少更新到 2023.10.0。
3. 从您的云托管组织[获取新的许可证](../../self-hosting/licensing-on-premise.md#retrieve-organization-license)文件并[将其上传到您的自托管服务器](../../self-hosting/licensing-on-premise.md#update-organization-license)。

## 问：家庭方案支持 Secrets Manager 吗？ <a href="#q-do-families-plans-support-secrets-manager" id="q-do-families-plans-support-secrets-manager"></a>

**答：**&#x42;itwarden 为免费、团队和企业组织提供 Secrets Manager 订阅服务。如果您拥有家庭方案并希望使用 Bitwarden Secrets Manager，只需按照[这些步骤](../get-started/secrets-manager-quick-start.md)创建一个新的免费组织并注册 Secrets Manager 即可。

## 问：如果我有支持问题，如何联系 Bitwarden？ <a href="#q-how-do-i-contact-bitwarden-if-i-have-support-questions-during-the-beta" id="q-how-do-i-contact-bitwarden-if-i-have-support-questions-during-the-beta"></a>

**答：**&#x60A8;可以通过 [bitwarden.com/contact](https://bitwarden.com/contact/) 或 [ask the community](https://community.bitwarden.com/c/support/sm-ask-the-community/63) 提交问题。

## 问：如何开始概念验证？  <a href="#q-how-do-i-start-a-proof-of-concept" id="q-how-do-i-start-a-proof-of-concept"></a>

**答：**&#x542F;动 Secrets Manager 企业试用来测试概念验证并获得对 SSO 和 SCIM 集成、企业策略、自托管、事件日志和优先级支持等企业功能的访问权限。立即[注册 Secrets Manager 7 天免费试用](https://vault.bitwarden.com/#/register?org=enterprise\&layout=secretsManager)。

## 问：我能否以非管理员用户身份试用 Secrets Manager？ <a href="#q-can-i-try-secrets-manager-as-a-non-administrator-user" id="q-can-i-try-secrets-manager-as-a-non-administrator-user"></a>

**答：**&#x6FC0;活 Secrets Manager 要求组织管理员。不过，用户可以导航到网页 App上的 Secrets Manager 页面，然后选择**立即试用**按钮。这将生成一封电子邮件，您可以发送给您的管理员，以便为您自己或您的团队申请 Secrets Manager 访问权限。

## 问：Bitwarden Secrets Manager 和 Bitwarden Password Manager 有什么区别？  <a href="#q-what-is-the-difference-between-bitwarden-secrets-manager-and-bitwarden-password-manager" id="q-what-is-the-difference-between-bitwarden-secrets-manager-and-bitwarden-password-manager"></a>

**答：**&#x42;itwarden Secrets Manager 专为开发团队构建，用于集中存储、管理和部署特权机密。Secrets Manager 专为基础设施机密量身定制，仅受网页 App 和 CLI 客户端支持。如果您希望帮助您的员工管理他们的个人凭据，请使用 Bitwarden Password Manager。


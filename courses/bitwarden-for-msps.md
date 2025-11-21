# \*托管服务提供商

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-for-msps/)
{% endhint %}

在本视频指南中，您可以了解如何以托管服务提供商 (MSP) 的身份开始使用 Bitwarden Password Manager，并将其部署给您的客户。

{% embed url="https://vimeo.com/668382756" %}

[此处](https://bitwarden.com/partners/)了解更多有关成为 Bitwarden MSP 或经销商的信息，或跳转到视频中的以下时间点，了解特定主题：

* **01:36**：Bitwarden Password Manager 概述。
  * **01:46**：Bitwarden 客户端 App。
  * **02:15**：Bitwarden 如何与您的技术堆栈集成。
  * **04:53**：术语和概念概述。
* **08:34**：MSP 架构深度剖析。
  * **10:05**：您的组织。
  * **16:19**：提供商门户。
  * **23:13**：客户组织。
* **25:49**：管理您的客户。
  * **26:50**：管理策略。
  * **27:43**：导入数据。
  * **28:18**：设置 SSO 和 SCIM。
* **29:00**：问答。

## MSP 客户部署指南 <a href="#msp-customer-deployment-guide" id="msp-customer-deployment-guide"></a>

使用以下步骤和最佳实践将 Bitwarden 部署到您的客户。

### 第一阶段 - 入职前准备 <a href="#phase-1-pre-onboarding" id="phase-1-pre-onboarding"></a>

为您的客户的 Bitwarden 组织和环境定义技术要求和入职策略。

| 步骤 | 主题         | 操作                                                                                                                                             | 资源                                                                                       | 持续时间（小时） |
| -- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | -------- |
| 1  | 环境决策       | 确定云环境或自托管环境                                                                                                                                    | [托管 FAQ](../docs/self-hosting/hosting-faqs.md)                                           | 0.5      |
| 2  | 认证策略       | 确定客户是否将使用单点登录 (SSO)                                                                                                                            | [关于 SSO](../docs/admin-console/login-with-sso/about-login-with-sso.md)                   | 0.25     |
| 3  | 解密方式       | 如果使用 SSO 登录，请选择主密码或受信任设备进行解密                                                                                                                   | [关于受信任设备](../docs/admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) | 0.25     |
| 4  | 配置策略       | 选择配置策略，如 SCIM、目录连接器或手动配置。                                                                                                                      | [管理用户](../docs/admin-console/manage-members/user-management.md#onboard-users)            | 0.25     |
| 5  | 用户识别       | 为推广群组识别用户、团队或部门                                                                                                                                |                                                                                          | 0.25     |
| 6  | 培训策略       | 确定参加培训的团队和内部倡导者。例如：最终用户、服务台、管理员                                                                                                                |                                                                                          | 0.5      |
| 7  | 文档集合（共享）策略 | <p>确定集合将如何配置。需要考虑的因素包括：是否允许用户创建集合？<br><br>集合是否将按部门、工程、功能进行配置？<br><br>数据会从另一个通常定义结构的应用程序中导入吗？<br><br>管理员和所有者用户可以访问所有共享项目，还是只有委派了集合的管理员可以访问？</p> | [关于集合](../docs/admin-console/manage-shared-items/collections/about-collections.md)       | 1        |
| 8  | 策略方案       | 选择在启动时配置的策略                                                                                                                                    | [策略](../docs/admin-console/oversight-visibility/enterprise-policies.md)                  | 0.5      |
| 9  | 推广时间线      | 确定邀请和入职机制及时间                                                                                                                                   |                                                                                          | 0.5      |
| 10 | 内部沟通       | 创建关于 Bitwarden 推广的内部消息或备忘录。审查 Bitwarden 模板以了解沟通方式                                                                                              | [欢迎电子邮件模板](../docs/admin-console/onboarding/welcome-email-templates.md)                  | 1        |
| 11 | 领导层沟通      | 向内部领导者传达密码管理推广策略                                                                                                                               |                                                                                          | 0.25     |

### 第二阶段 - 组织设置 <a href="#phase-2-organization-set-up" id="phase-2-organization-set-up"></a>

为您的客户设置技术基础并配置 Bitwarden 设置。

| 步骤 | 主题     | 操作                                                                                                            | 资源                                                                                    | 持续时间（小时） |
| -- | ------ | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | -------- |
| 12 | 组织所有者  | 识别组织所有者。所有者是能够控制组织所有方面的超级用户。决定是否希望将电子邮件与特定用户或团队收件箱关联。此外，最佳实践是为冗余设置两个所有者账户                                     | [成员角色](../docs/admin-console/manage-members/member-roles.md)                          | 0.25     |
| 13 | 企业策略   | <p>配置企业策略。<br>任何策略都应在邀请用户之前启用。请务必查看以下策略：</p><p></p><p>账户恢复管理</p><p></p><p>强制执行组织数据所有权</p><p></p><p>激活自动填充</p> | [策略](../docs/admin-console/oversight-visibility/enterprise-policies.md)               | 1        |
| 14 | 集合管理设置 | 选择集合在组织中的行为方式。这些设置允许从完全的管理控制到完全的自助服务（用户可以创建自己的集合）的多种选择。这些设置可用于建立最小权限策略                                        | [管理用户](../docs/admin-console/manage-members/user-management.md)                       | 0.25     |
| 15 | 协同管理环境 | 向客户组织添加管理员或所有者以协同管理。最佳实践是为冗余设置两个所有者                                                                           | [管理用户](../docs/admin-console/manage-members/user-management.md)                       | 0.5      |
| 16 | 创建集合   | 集合是存放安全项目并与用户群组共享的地方                                                                                          | [集合](../docs/admin-console/manage-shared-items/collections/about-collections.md)      | 0.5      |
| 17 | 创建用户群组 | 创建用户群组可以轻松分配集合。如果您决定从您的身份提供程序或目录服务同步群组和用户，您可能需要稍后重新配置用户和群组分配                                                  | [群组](../docs/admin-console/manage-members/groups.md)                                  | 0.5      |
| 18 | 集合分配   | 将群组分配给集合，确保测试并展示“只读”和“隐藏密码”选项                                                                                 | [用户类型访问控制](../docs/admin-console/manage-members/member-roles.md)                      | 0.5      |
| 19 | 添加项目   | 手动将项目添加到测试集合中，或通过 CSV 或 JSON 从其他密码管理应用程序导入                                                                    | [集合](../docs/admin-console/manage-shared-items/collections/about-collections.md)      | 0.25     |
| 20 | SSO 登录 | <p>如适用，配置 SSO 登录和组织标识符<br>配置以与 SAML 2.0 或 OpenID Connect 协同工作</p>                                             | [开始使用 SSO](../docs/admin-console/login-with-sso/about-login-with-sso.md)              | 1.5      |
| 21 | 域名验证   | 如适用，验证公司和其他电子邮件域名，以允许您的用户在 Enterprise SSO 过程中跳过输入组织标识符。非 SSO 组织无需此操作                                          | [域名验证](../docs/admin-console/oversight-visibility/claimed-domains/claimed-domains.md) | 0.5      |

### 第三阶段 - 组织推广 <a href="#phase-3-organization-roll-out" id="phase-3-organization-roll-out"></a>

在客户的团队和职能中部署 Bitwarden。

| 步骤 | 主题            | 操作                                                                                           | 资源                                                                                                                                                                                                                                                                                                       | 持续时间（小时） |
| -- | ------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| 22 | 技术节奏会议        | 与客户计划实施阶段 3                                                                                  |                                                                                                                                                                                                                                                                                                          | 0.5      |
| 23 | 添加项目到集合       | 手动将项目添加到生产集合或从其他密码管理应用程序导入数据                                                                 | [关于集合](../docs/admin-console/manage-shared-items/collections/about-collections.md)                                                                                                                                                                                                                       | 0.25     |
| 24 | 企业策略          | <p>企业策略可用于根据您的安全需求定制您的 Bitwarden 组织。<br>在用户入职开始前，启用并配置所需的策略</p>                              | [策略](../docs/admin-console/oversight-visibility/enterprise-policies.md)                                                                                                                                                                                                                                  | 0.1      |
| 25 | SSO 登录        | 如适用，配置 Bitwarden 使用您的 SAML 2.0 或 OIDC 身份提供程序进行身份验证                                           | [关于 SSO](../docs/admin-console/login-with-sso/about-login-with-sso.md)                                                                                                                                                                                                                                   | 1.5      |
| 26 | 早期用户          | 手动将一组用户添加到客户端组织中，并将他们分配到不同的群组。使用这些用户，您将在下一步之前广泛测试所有预配置的功能，然后再转向目录连接器等高级功能。将附件中的入职工作流程说明与用户分享 | <p><a href="../docs/admin-console/manage-members/user-management.md#invite">管理用户 - 邀请</a></p><p></p><p><a href="../docs/admin-console/onboarding/onboarding-workflows.md">入职工作流程</a></p>                                                                                                                 | 0.5      |
| 27 | SIEM 集成       | 如适用，将 Bitwarden 连接到客户的 SIEM 工具                                                               | [SIEM](../docs/admin-console/oversight-visibility/event-logging/event-logs.md#siem-and-external-systems-integrations)                                                                                                                                                                                    | 0.5      |
| 28 | Bitwarden 客户端 | 试点小组的所有组织成员应在各种设备上下载 Bitwarden，登录并测试通过集合访问共享项目。他们应测试策略的正确实施                                  | [下载](https://bitwarden.com/download/)                                                                                                                                                                                                                                                                    | 0.5      |
| 29 | 部署客户端应用程序     | 配置您的应用程序管理或 MDM 工具，为批量部署 Bitwarden 应用程序做准备                                                   | [部署客户端应用程序](../docs/admin-console/deploy-client-apps/deploy-browser-extensions/)                                                                                                                                                                                                                         | 0.5      |
| 30 | 禁用内置的密码管理器    | 将 Bitwarden 密码管理器设为默认密码管理器，并关闭内置浏览器解决方案。在新员工入职时教育他们如何做同样操作                                   | [禁用内置的密码管理器](../docs/password-manager/getting-started/getting-started-browserext.md#disable-a-built-in-password-manager)                                                                                                                                                                                 | 0.25     |
| 31 | 测试用户入职        | 配置并测试 Bitwarden SCIM 或目录连接器集成，以自动同步用户和群组                                                     | <p><a href="../docs/admin-console/manage-members/scim/about-scim.md">关于 SCIM</a></p><p></p><p><a href="../docs/admin-console/manage-members/directory-connector/about-directory-connector.md">关于目录连接器</a></p>                                                                                            | 1.5      |
| 32 | 用户入职引导        | 执行 SCIM 或目录连接器同步，以邀请组中的其他用户加入组织。将附件中的用户入职工作流程说明与用户分享                                         | <p><a href="../docs/admin-console/manage-members/scim/about-scim.md">关于 SCIM</a></p><p></p><p><a href="../docs/admin-console/manage-members/directory-connector/about-directory-connector.md">关于目录连接器</a></p><p></p><p><a href="../docs/admin-console/onboarding/onboarding-workflows.md">入职工作流程</a></p> | 1        |

### 第四阶段 - 用户培训 <a href="#phase-4-user-training" id="phase-4-user-training"></a>

对所有用户和利益相关者进行如何使用 Bitwarden 的培训，并提供持续的教育。

| 步骤 | 主题                    | 操作                                                                                                                                                               | 资源                                                                                                                                                                 | 持续时间（小时） |
| -- | --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| 33 | 管理员培训                 | <p>为管理员用户提供日常任务培训，并根据需要增加任何特殊主题<br><br>示例特殊主题包括但不限于：<br>展示配置的 SSO 登录流程<br><br>用户入职和离职<br><br>自定义角色</p>                                                           | <p><a href="password-manager/admin.md#get-to-know-the-admin-console">了解管理员控制台</a></p><p></p><p><a href="password-manager/admin.md">Bitwarden 企业管理员</a></p>         | 0.75     |
| 34 | Service desk training | <p>指导服务台用户了解其角色/操作。<br><br>审查自定义角色可以完成哪些任务以及需要管理员干预的任务</p>                                                                                                       |                                                                                                                                                                    | 0.75     |
| 35 | 团队成员培训                | <p>针对最终用户的一般培训课程将涵盖：<br>适用于所有设备的 Bitwarden<br><br>设置 Bitwarden 浏览器扩展<br><br>创建您的账户<br><br>了解 Bitwarden 密码库<br><br>如何使用 Bitwarden 密码管理器<br><br>Bitwarden Send</p> | <p><a href="password-manager/team-member.md#get-to-know-your-vault">了解您的密码库</a></p><p></p><p><a href="get-to-know-password-manager.md">了解 Password Manager</a></p> | 0.75     |
| 36 | 持续教育                  | 所有用户都可以利用 Bitwarden 学习中心每月更新的学习内容                                                                                                                                | [学习](https://bitwarden.com/learning/)                                                                                                                              | 0.75     |

# =Bitwarden 入职手册

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-onboarding-playbook/)
{% endhint %}

该手册为 IT 管理员提供了一个灵活的路线图，帮助用户跨五个关键阶段使用 Bitwarden Password Manager。虽然各阶段按顺序呈现，但并非严格线性。根据团队需求和时间表，许多步骤可以并行进行。

在本指南中，您将在代码框中找到操作项，这些操作项可以直接复制并粘贴到项目管理工具、内部文档或团队沟通平台中。这使得您可以在 Bitwarden 推出期间轻松跟踪进度、分配任务和维护责任。使用本指南作为基础并对其进行调整以适应您的环境。

{% tabs %}
{% tab title="1：培训" %}
{% hint style="success" %}
第 1 阶段专注于培养利益相关者、准备系统，并建立成功设置的知识库。Bitwarden 建议在推广前或推广期间为每个群组或团队安排培训课程。
{% endhint %}

## 主要目标 <a href="#key-objectives" id="key-objectives"></a>

* 为所有用户级别建立培训计划
* 准备技术基础设施和需求
* 创建组织和集合管理策略和程序
* 建立内部专业知识和支持能力

## 活动 <a href="#activities" id="activities"></a>

### 步骤 1：管理员培训 <a href="#step-1-administrator-training" id="step-1-administrator-training"></a>

**关键人员：**&#x49;T 总监、系统管理员、所有者

**培训主题：**

* Bitwarden 架构和企业级功能
* 可扩展的共享功能
  * 集合设置；组织和分组相关的凭据、密钥或其他密码库项目
  * 将用户添加到 Bitwarden 组织
  * 为每个集合的成员或群组分配适当的权限
  * 将某些项目分配到多个集合，以便合适的人可以无重复地访问
* 设置和策略
  * SSO 设置和集成工作流程
  * 双重验证设置和策略
  * 安全策略和企业控制
* 管理和报告
  * 自定义字段和角色管理
  * 用户和群组管理最佳实践
  * 事件日志记录和报告功能

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Schedule administrator training sessions
[ ] Review enterprise feature requirements
[ ] Document SSO integration requirements
[ ] Plan custom roles and permission structures
[ ] Establish security policy framework
[ ] Document cyber insurance compliance requirement
     [ ] Prepare business case including insurance premium impact
     [ ] Align rollout timeline with insurance renewal dates
```

### 步骤 2：服务台培训 <a href="#step-2-service-desk-training" id="step-2-service-desk-training"></a>

**关键人员：** 帮助台工作人员、客户成功主管

**培训主题：**

* 常见用户问题及故障排除
* 密码重置程序和限制
* 账户恢复流程
* 复杂问题的升级流程

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Train support staff on Bitwarden functionality
[ ] Create troubleshooting documentation
[ ] Establish support ticket workflows
[ ] Define escalation procedures
```

### 步骤 3：最终用户培训 <a href="#step-3-end-user-training" id="step-3-end-user-training"></a>

注意：对于许多客户来说，最终用户培训通常在推广之前或推广期间进行，因为每个部门都在进行入职。Bitwarden 建议优先进行管理员培训。

**关键人员：** 公司内所有终端用户

**培训主题：**

* 如适用，密码导入流程和最佳实践
* 跨平台 Bitwarden 使用（桌面、移动、网页、浏览器）
* 账户创建和主密码指南
* 密码库导航和组织功能
* 如何保存新的登录
* 自动填充选项
* 密码生成器
* 用于安全共享的 Bitwarden Send
* 通过集合协作

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Schedule organization-wide training sessions by functions; recommend starting with more technical teams (ie. tech team, data team)
[ ] Create user documentation and quick reference guides. Leverage resources available in the Bitwarden help center
[ ] Prepare import templates and migration tools
[ ] Establish help desk support procedures
```

### 步骤 4：领导层培训 <a href="#step-4-leadership-training" id="step-4-leadership-training"></a>

**关键人员：** 部门主管、高管领导

**培训主题：**

* Bitwarden 对保障组织安全的重要性
* 如适用，密码导入流程和最佳实践
* 识别存在风险的密码（使用密码库健康报告）
* 跨平台 Bitwarden 使用（桌面、移动、网页、浏览器）
* 账户创建和主密码指南
* 密码库导航和组织功能
* 如何保存新的登录
* 自动填充选项
* 密码生成器
* 用于安全共享的 Bitwarden Send
* 通过集合协作

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Get leadership buy-in and identify advocates. Bitwarden research shows that company-wide password management mandates more than doubles regular usage. 
[ ] Train leadership on importance of using a password manager
[ ] Show leadership how easy it is to use
```
{% endtab %}

{% tab title="2：设置" %}
{% hint style="success" %}
第 2 阶段是技术设置阶段，在此阶段为您的组织部署并配置 Bitwarden。
{% endhint %}

## 主要目标 <a href="#key-objectives" id="key-objectives"></a>

* 部署 Bitwarden 基础设施（云端或自托管）
* 配置组织结构和策略
* 建立安全和身份集成（[SSO](https://bitwarden.com/resources/choose-the-right-sso-login-strategy/)，[SCIM](../manage-members/scim/about-scim.md)）
* 准备用户推广（参见[阶段 3](bitwarden-onboarding-playbook.md#id-3-ji-hua)）

## 选项 A：Bitwarden 云（推荐） <a href="#option-a-bitwarden-cloud" id="option-a-bitwarden-cloud"></a>

对于大多数组织，推荐使用 Bitwarden 托管的服务。享受易于扩展、自动更新以及由 Bitwarden 管理的安全可靠服务器上的最小维护。

### 步骤 1：预先规划 <a href="#step-1-pre-setup-planning" id="step-1-pre-setup-planning"></a>

在深入技术设置之前，建立您的组织策略和方法非常重要。以下是一些需要考虑的关键建议。

#### 选择 US 或 EU 云服务器区域 <a href="#choose-between-us-or-eu-cloud-server-regions" id="choose-between-us-or-eu-cloud-server-regions"></a>

组织必须根据数据驻留要求，在 [US 或 EU 云服务器区域](../../security/server-geographies.md)之间进行选择。Bitwarden 无法将客户账户从一个区域迁移到另一个区域。组织可以使用脚本来帮助促进迁移。通过联系支持，可以将订阅从一个区域转移到另一个区域。

#### 为集中所有权和可见性奠定基础 <a href="#set-the-foundation-for-centralized-ownership-and-visibility" id="set-the-foundation-for-centralized-ownership-and-visibility"></a>

* 通过集中报告，获得组织范围内的凭证健康状况和使用情况控制及洞察。
* 通过安全地重新分配或删除凭据，确保员工过渡的无缝衔接。
* 通过分配角色、按部门或功能将凭据划分为集合，强制执行最小权限原则，仅授予用户和群组访问他们所需的集合。
* 强化良好密码实践，并借助企业策略开始洞察凭据生命周期 - 创建、访问、转移和删除。

{% hint style="info" %}
**提前规划**

* Bitwarden 将很快允许组织自动将所有员工凭据统一到组织密码库下，确保一致的所有权和控制权。
* 一旦可用，启用强制组织数据所有权策略，以便所有项目都是组织拥有的，从而实现集中控制、报告、凭证健康洞察和简化的入职流程。
* 用户仍然可以在「我的项目」中为他们的工作凭据预留空间。
* 通过组织拥有的集合来共享和管理项目。
{% endhint %}

#### Bitwarden 推荐使用受信任设备 SSO <a href="#bitwarden-recommends-sso-with-trusted-devices" id="bitwarden-recommends-sso-with-trusted-devices"></a>

为获得最佳用户体验，Bitwarden 推荐使用[受信任设备 SSO](../login-with-sso/trusted-devices/about-trusted-devices.md)。这允许员工通过单步登录并解密他们的密码库，尽管它需要额外的 IT 管理员设置时间。以下是采用这种方法时需要考虑的事项：

* 强制执行「注销」的密码库超时策略，提供一致的用户体验：超时后，员工只需通过 SSO 重新认证，而无需输入主密码。
* 在受信任的设备环境中，「解锁」行为与「注销」相同，除非用户配置了 PIN 码或生物识别
* 如果您的组织积极推广 PIN 码或生物识别，管理员可以选择「解锁」，但前提是用户沟通必须明确这一预期。
* 密码库超时：Bitwarden 建议大多数用例设置为 4-10 小时，以平衡生产力和安全性。

将此列表直接复制安徽粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Determine cloud server region (US, EU)
[ ] Determine overall organizational data ownership
[ ] Choose authentication and decryption strategy
[ ] Define user onboarding and deprovisioning approach 
     [ ] Manual invitation
     [ ] Bitwarden Directory Connector
     [ ] SCIM
     [ ] Just-in-Time SSO
[ ] Define vault ownership strategy (Individual vaults vs. Organization-only)
[ ] Identify user groups for rollout phases
[ ] Stakeholder selections:
     [ ] Project lead
     [ ] Identity provider admin
     [ ] Executive sponsor
     [ ] Security and compliance admin
     [ ] Support/help desk admin
     [ ] Device management admin (for client deployment)
     [ ] Business continuity admin
     [ ] Directory/user management admin
```

### 步骤 2：组织创建 <a href="#step-2-organization-creation" id="step-2-organization-creation"></a>

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Create new Bitwarden organization account
[ ] Select appropriate enterprise plan
[ ] Configure billing and payment methods
```

### 步骤 3：核心设置 <a href="#step-3-core-setup" id="step-3-core-setup"></a>

遵循以下建议，确保 Bitwarden 设置顺利进行。

#### 声明所有企业邮箱域名 <a href="#claim-all-corporate-email-domains" id="claim-all-corporate-email-domains"></a>

为了限制某些用户操作，授予管理员更大的控制权，并简化用户的登录体验。

#### 在用户入职前设置企业策略 <a href="#set-up-enterprise-policies-before-user-onboarding" id="set-up-enterprise-policies-before-user-onboarding"></a>

在用户入职开始前设置所有[企业策略](../oversight-visibility/enterprise-policies.md) ，以确保从一开始就实施一致的安全控制。

#### 建立强大的安全基线 <a href="#establish-strong-security-baselines" id="establish-strong-security-baselines"></a>

使用至少 14-16 个字符的[主密码](../oversight-visibility/enterprise-policies.md#master-password-requirements) （包括大写字母、小写字母、数字和符号），并设置密码生成器的最小长度为至少 14 个字符，包含符号和数字。

#### 启用单一组织限制 <a href="#enable-single-organization-restriction" id="enable-single-organization-restriction"></a>

为防止用户加入其他 Bitwarden 组织，维护数据治理并防止潜在的数据泄露。

#### 设置您的组织密码库 <a href="#set-up-your-organization-vault" id="set-up-your-organization-vault"></a>

如果你已经在你的 IdP 或目录中使用了群组和对象，为了保持一致性，请在 Bitwarden 中镜像该框架。在导入过程中，类似文件夹的对象将自动转换为集合。

记住：Bitwarden 与传统应用程序不同。对于 Bitwarden，所有内容都通过端到端加密进行保护，访问策略在客户端级别强制执行。这意味着：

* 管理员可以定义和分配访问权限，但他们自己看不到凭据。
* 集合和群组是 Bitwarden 在保持零知识的同时强制执行访问权限的方式。
* 某些操作（同步、策略检查、密码库操作）需要在客户端进行额外处理，而不是以明文形式显示给服务器。

如果从零开始：

* [集合（共享的内容）](../manage-shared-items/collections/collection-settings.md)**：** 最佳实践是根据共享资源的职能来组织集合（例如：运输配置文件、广告平台登录信息）。最初保持集合范围较广；在必要时再添加细节。通常，IT 管理员管理组织范围的集合，而团队负责人管理部门特定的集合。
* [群组（谁具有访问权限）](../manage-members/groups.md)：使用群组来代表部门或团队（例如：市场部、财务部），并与集合一一对应以确保清晰。跨越职能的特殊群组也很常见（例如：行政助理、IT 管理员、采购审批人）。

{% hint style="info" %}
**记住** ：Bitwarden 的可扩展共享模型意味着项目可以同时存在于多个集合中，而不会影响安全性。团队可以访问他们需要的凭据，而无需暴露整个密码库。
{% endhint %}

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Configure domain claiming
[ ] Set up enterprise policies for mandatory security controls
[ ] Set up password and password generator minimums
[ ] Organization data ownership enforcement to require all vault items in organization
[ ] Create organizational structure - collections, groups
[ ] Configure user roles and permissions
```

### 步骤 4：集成设置 <a href="#step-4-integration-setup" id="step-4-integration-setup"></a>

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
SSO integration (if applicable):
[ ] Configure SAML 2.0 or OIDC with identity provider
[ ] Test SSO login workflows
[ ] Configure trusted devices (if applicable)
[ ] Document SSO troubleshooting procedures

Directory Integration (if applicable):
[ ] Install and configure Directory Connector
[ ] Set up SCIM provisioning (Azure AD, Okta, OneLogin, JumpCloud)
[ ] Test user and group synchronization
[ ] Schedule automated sync intervals
```

### 步骤 5：安全控制 <a href="#step-5-security-controls" id="step-5-security-controls"></a>

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Set up event logging and SIEM integration
[ ] Establish backup and recovery procedures
```

## 选项 B：自托管（高级） <a href="#option-b-self-hosted" id="option-b-self-hosted"></a>

自托管意味着什么？

在您的服务器上运行 Bitwarden 需要高级技术知识和 IT 基础设施。这也意味着您需要负责服务器的维护、安全、正常运行时间和更新。

要评估是否适合自托管：

* 您目前是否已经自托管了其他任何东西？
* 您是否有专门的硬件来运行服务器？
* 是否有 IT 或 DevOps 团队负责服务器？
* 您是否熟悉 Docker，或者 Kubernetes 和 Helm 图表？
* 您是否熟悉使用 [Linux 终端](../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md)或 [PowerShell](../../self-hosting/deploy-and-configure/docker/windows-standard-deployment.md#installation-procedure) 安装软件？

如果您决定自行托管 Bitwarden，请按照以下步骤操作。

### 步骤 1：预先规划 <a href="#step-1-pre-setup-planning" id="step-1-pre-setup-planning"></a>

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Choose self hosted deployment method (Linux standard/manual/offline, Windows standard/offline, or Kubernetes)
[ ] Define server/VM specs and hosting environment (environment variables, firewall or proxy)
[ ] Decide on SSL certificate approach
[ ] Plan network architecture, firewall or proxy rules, access controls
[ ] Scalability planning
[ ] Select key roles
     [ ] Project lead
     [ ] Executive sponsor
     [ ] Server admin
     [ ] Docker admin
     [ ] Network admin
     [ ] Firewall admin
     [ ] Support/help desk admin
     [ ] Database admin
     [ ] Identity provider admin
     [ ] SMTP admin
     [ ] Security and compliance admin
     [ ] Backups admin
     [ ] Business continuity admin
     [ ] Disaster recovery admin
     [ ] Device management admin
```

### 步骤 2：基础设施准备 <a href="#step-2-infrastructure-preparation" id="step-2-infrastructure-preparation"></a>

为您的 Bitwarden 服务器设置专用环境。具体要求因操作系统而异。请参阅[帮助中心](../../self-hosting/plan-for-deployment/self-host-bitwarden.md)获取详细说明。

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Provision hardware that meets minimum requirements 
[ ] Configure DNS records and domain name
[ ] Open ports 80 and 443
[ ] Install server offerings and containerization tools
[ ] Obtain installation ID and key from Bitwarden
[ ] Secure SSL certificates
```

### 步骤 3：Bitwarden 服务器安装 <a href="#step-3-bitwarden-server-installation" id="step-3-bitwarden-server-installation"></a>

在您的已准备好的环境中安装 Bitwarden。具体步骤因操作系统而异。

### 步骤 4：组织设置 <a href="#step-4-organization-setup" id="step-4-organization-setup"></a>

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Create cloud organization for billing purposes
[ ] Link self-hosted installation to billing organization
[ ] Configure enterprise settings and policies
[ ] Set up collections and groups structure
[ ] Test all integrations (SSO, SCIM)
```

### 步骤 5：维护计划 <a href="#step-5-maintenance-planning" id="step-5-maintenance-planning"></a>

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Create server update and maintenance schedule
[ ] Implement automated backup system
[ ] Set up off-site backup storage
[ ] Test disaster recovery procedures
[ ] Document maintenance and backup/recovery procedures
[ ] Set up monitoring and alerting for backup failures; evaluate backup methods
```
{% endtab %}

{% tab title="3：计划" %}
{% hint style="success" %}
第 3 阶段侧重于用户入职开始前的组织准备和沟通。此阶段通过设定适当预期、解决顾虑以及为变革创造组织动力，确保用户顺利采用。
{% endhint %}

## 主要目标 <a href="#key-objectives" id="key-objectives"></a>

* 向整个组织传达 Bitwarden 实施情况
* 解决用户顾虑和变革阻力
* 准备支持资源和文档
* 进行最终系统测试和验证
* 创建组织对改进安全的热情和认可

## 活动 <a href="#activities" id="activities"></a>

### 步骤 1：准备全公司范围的领导层沟通 <a href="#step-1-prepare-company-wide-communication-from-leadership" id="step-1-prepare-company-wide-communication-from-leadership"></a>

{% hint style="success" %}
领导层对采用成功至关重要。[Bitwarden 研究](https://bitwarden.com/resources/bitwarden-security-impact-report/)表明，公司范围内的密码管理要求将常规使用率提高了一倍以上。
{% endhint %}

**关键人员：** 行政领导层、IT 领导层、沟通团队、部门负责人。

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] Prepare leadership talking points about security benefits
[ ] Schedule leadership communication sessions (all-hands, team meetings)
[ ] CEO/Leadership announcement about password security initiative
[ ] Clear messaging about why Bitwarden was chosen
[ ] Timeline communication for rollout phases
[ ] Expectation setting for mandatory adoption
[ ] Emphasis on security benefits for both work and personal use
[ ] Highlight cyberinsurance benefits and that implementing Bitwarden is a prerequisite to get approved for higher level of coverage; document insurance coverage being met
```

### 步骤 2：组织沟通活动 <a href="#step-2-organizational-communication-campaign" id="step-2-organizational-communication-campaign"></a>

**关键人员：** 沟通团队、HR、IT 支持。

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
Communication strategy:
[ ] Develop multi-channel communication plan (email, intranet, meetings)
[ ] Create consistent messaging about security benefits
[ ] Address common concerns and objections proactively
[ ] Highlight ease of use and convenience benefits
[ ] Share success stories from pilot users or other organizations

Pre-rollout communications:
[ ] All hands meeting: Initial introduction to Bitwarden
     [ ] Why we're implementing password management / Bitwarden
     [ ] Security benefits for the organization and individuals
     [ ] Why it is important to follow the directions shared by IT
     [ ] Expect more details in your email inbox

[ ] Announcement email: More details on Bitwarden and roll out plan
     [ ] Recap: Why we're implementing password management / Bitwarden
     [ ] Recap: Security benefits for the organization and individuals
     [ ] Timeline for rollout and training
     [ ] What to expect in coming weeks

[ ] FAQ document: Address common questions and concerns
     [ ] "Will this slow down my workflow?"
     [ ] "What happens to my existing passwords?"
     [ ] "Is my personal information secure?"
     [ ] "What if I forget my master password?"
     [ ] "Do I have to use this for personal passwords, too?"
```

### 步骤 3：变更管理准备 <a href="#step-3-change-management-readiness" id="step-3-change-management-readiness"></a>

**关键人员：** HR、变革管理团队、部门经理。

**变更管理活动**

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
 [ ]  Identify and engage change champions in each department
 [ ]  Conduct department-specific communication sessions
 [ ]  Address cultural and workflow concerns
 [ ]  Plan for resistance management and additional support
 [ ]  Create peer support networks and feedback channels
```
{% endtab %}

{% tab title="4：推广" %}
{% hint style="success" %}
第 4 阶段确保用户开始使用 Bitwarden，通过向用户介绍 Bitwarden，确保正确设置账户和初始使用。

提醒管理员所有 Bitwarden **入职流程**：邀请 → 接受 → 确认
{% endhint %}

## 主要目标 <a href="#key-objectives" id="key-objectives"></a>

## 选择您的推广路径 <a href="#choose-your-rollout-path" id="choose-your-rollout-path"></a>

{% hint style="success" %}
运行一个小型试点（用户数量根据组织规模而定，20-100 人）有助于验证在所有主要使用场景（桌面、移动、浏览器、SSO 等）中的推广。这有助于完善沟通并培养内部拥护者。
{% endhint %}

### 步骤 1：推广规划 <a href="#step-1-rollout-planning" id="step-1-rollout-planning"></a>

{% hint style="success" %}
分阶段推广方式，按部门逐个实施，被 [Bitwarden 用户选为“非常有效”。](https://bitwarden.com/resources/bitwarden-security-impact-report/)
{% endhint %}

### 步骤 2：用户账户创建和访问权限 <a href="#step-2-user-account-creation-and-access" id="step-2-user-account-creation-and-access"></a>



### 步骤 3：客户端安装和设置 <a href="#step-3-client-installation-and-setup" id="step-3-client-installation-and-setup"></a>



### 步骤 4：密码库设置和导航 <a href="#step-4-vault-setup-and-navigation" id="step-4-vault-setup-and-navigation"></a>



### 步骤 5：密码管理实施 <a href="#step-5-password-management-implementation" id="step-5-password-management-implementation"></a>



### 步骤 6：密码迁移和导入 <a href="#step-6-password-migration-and-import" id="step-6-password-migration-and-import"></a>


{% endtab %}

{% tab title="5：采用" %}
{% hint style="success" %}
第 5 阶段侧重于推广、最大化价值、确保安全合规以及维护长期成功。
{% endhint %}

## 主要目标 <a href="#key-objectives" id="key-objectives"></a>



## 活动 <a href="#activities" id="activities"></a>



### 步骤 1：采用和优化 <a href="#step-1-adoption-and-optimization" id="step-1-adoption-and-optimization"></a>



### 步骤 2：安全审计与合规 <a href="#step-2-security-audit-and-compliance" id="step-2-security-audit-and-compliance"></a>



### 步骤 3：高级功能实施 <a href="#step-3-advanced-feature-implementation" id="step-3-advanced-feature-implementation"></a>



### 步骤 4：持续支持 <a href="#step-4-ongoing-support" id="step-4-ongoing-support"></a>



### 步骤 5：持续改进 <a href="#step-5-continuous-improvement" id="step-5-continuous-improvement"></a>



### 步骤 6：新员工入职 <a href="#step-6-new-employee-onboarding" id="step-6-new-employee-onboarding"></a>


{% endtab %}

{% tab title="资源" %}
使用这些额外资源来帮助您在 Bitwarden 旅程的各个阶段进行指导：

## 成功检查清单 <a href="#success-checklist" id="success-checklist"></a>

将此列表直接复制然后粘贴到您的项目管理工具、内部文档或团队沟通平台中，以便轻松跟踪进度、分配任务并保持责任明确：

```
[ ] 100% user adoption of all purchased Bitwarden seats 
[ ] Complete password migration from legacy systems and other password managers
[ ] Security posture improvements (reduction of breaches, promotes safe password habits) 
[ ] Reduce number of at-risk credentials (reused, exposed, weak) across the entire organization
[ ] Value achieved beyond password management (Bitwarden Send, storing sensitive information such as credit cards, identifies, notes, and more)
[ ] Internal champions excited to help others achieve password security success
[ ] Full integration with existing identity and security infrastructure
[ ] Established security policies and compliance procedures
[ ] Ongoing support and maintenance frameworks
[ ] Documented Bitwarden procedures for onboarding new employees
[ ] Optimized workflows for maximum efficiency and security
[ ] Regular monitoring and continuous improvement processes
```

## Bitwarden 支持 <a href="#bitwarden-support" id="bitwarden-support"></a>

* **计费支持：** 联系客户成功团队以获得加急计费协助
* **技术支持：** 为所有用户提供全面的技术故障排除服务
* **企业客户：** 与全球账户经理进行持续会议
* **高管访问权限：** 企业客户定期与 Bitwarden 高管会面

## 模板 <a href="#templates" id="templates"></a>

[推广电子邮件模板](welcome-email-templates.md)：用于向最终用户、管理员和 IT 团队宣布 Bitwarden 密码管理器的推广的电子邮件模板。将这些电子邮件附上您的品牌标识，并根据需要进行调整。

[最终用户引入职电子邮件模板](end-user-onboarding-emails.md)：由 care@bitwarden.com 向新 Bitwarden 企业版和团队版用户发送的引导电子邮件。

[客户激活套件](customer-activation-kit.md)：包括单页宣传册、培训视频、海报、电子邮件模板和促销资源的现成沟通材料，以支持您的推广。

[幻灯片演示公告模板](https://docs.google.com/presentation/d/1zK8NDB6E8ID_ok_yxn5x5qjO7mzeI5CZ-kqcOsfcQcU/edit?usp=sharing)：向整个公司或组织介绍 Bitwarden 密码管理器的幻灯片演示模板。根据需要附上公司品牌标识和推广详情。

## 深入了解 <a href="#go-deeper" id="go-deeper"></a>

[Bitwarden 学习中心](https://bitwarden.com/learning/) - 每月更新的视频内容

[每周直播演示](https://bitwarden.com/resources/demos/) - 互动问答环节

[企业功能列表](../../business-resources/bitwarden-for-enterprise-features-datasheet.md) - 全面的功能性文档

[API 文档](https://bitwarden.com/help/api/) - 适用于高级集成

[社区论坛](https://community.bitwarden.com/) - 用户社区和支持
{% endtab %}
{% endtabs %}

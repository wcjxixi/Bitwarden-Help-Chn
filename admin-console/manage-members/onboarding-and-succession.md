# 入职和继任概述

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/onboarding-and-succession/)
{% endhint %}

{% hint style="success" %}
阅读下面的全文或[下载 PDF](https://bitwarden.com/images/resources/GUIDE-enterprise-password-management-throughout-employee-lifecycle.pdf)。
{% endhint %}

## 适合您业务的密码管理 <a href="#password-management-that-fits-your-business" id="password-management-that-fits-your-business"></a>

让新员工快速上手并投入使用可以提高生产力。同样，适当的告别也能保证您企业系统和账户的安全。无论您的企业倾向于整合和集中化，还是更喜欢灵活和动态的环境，Bitwarden 都能满足您的需求。

本指南涵盖了 Bitwarden 为您的组织中的用户提供的入职和继任计划的方法，从我们对用户和组织之间的关系的方法开始，然后涵盖了入职和离职的最简单的用例，最后转向您可以支配的杠杆和选项，使 Bitwarden 符合您的需求。

## Bitwarden 理念 <a href="#the-bitwarden-approach" id="the-bitwarden-approach"></a>

Bitwarden 的愿景是想象一个没有人被黑客入侵的世界。我们将这一使命贯彻到我们的使命中，即帮助个人和公司轻松、安全地管理他们的敏感信息。Bitwarden 认为：

* 针对个人的基本密码管理可以而且应该是**免费**的。我们提供的就是这样，为个人提供[基本的免费账户](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#free-individual)。
* 个人和家庭应使用 [TOTP、紧急访问和其他支持的安全功能](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#premium-individual)，以在安全方面发挥积极作用。
* 组织可以通过[组织密码管理和安全共享](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#bitwarden-business-plans)极大地提高他们的安全配置。

{% hint style="success" %}
对于 Bitwarden 而言，[不同的计划](../../plans-and-pricing/password-manager/about-bitwarden-plans.md)和选项是相互关联和互补的，这些都源于我们对无黑客世界的愿景。通过密码管理赋予每个人在工作**和**家庭中的权力，使我们离这个目标更近了一步。
{% endhint %}

Bitwarden 的一个关键方面是，与许多软件应用程序不同，每个密码库中的所有内容都是[端到端加密](../../security/encryption/encryption-protocols.md)的。为了保持这种安全模式，每个使用 Bitwarden 的人都必须有一个唯一的账户和一个唯一的[主密码](../../account/log-in-and-unlock/your-master-password.md)。主密码应该是**强大**和**易记**的。

每一个用户负责他们的主密码。Bitwarden 是一种零知识加密解决方案，这意味着 Bitwarden 的团队以及 Bitwarden 系统本身不知道、无法获取或重置任何主密码。

{% hint style="success" %}
Bitwarden 已在 2021 年中期推出一项新的功能，使企业能够重置其组织用户的密码。这不会影响没有连接到启用了此功能的企业组织的个人账户。
{% endhint %}

### 随处使用 Bitwarden <a href="#use-bitwarden-anywhere" id="use-bitwarden-anywhere"></a>

无所不在的守护，方成就无处不在的安全，因此最好的密码管理器提供跨越您所有设备的访问。Bitwarden 支持[一系列客户端应用程序](https://bitwarden.com/download/)，任何一个都可以连接到我们的云托管服务器或您自己的自托管服务器：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/aONk4rWXWWHtOivPOt58m/e75d2f9876a86d7d9a81b7d9fd7182c3/bitwarden-clients-cloud-server.png?fm=webp&h=203&q=50&w=933" %}
Bitwarden 客户端/服务器
{% endembed %}

### 用户个人密码库 <a href="#users-personal-vaults" id="users-personal-vaults"></a>

创建 Bitwarden 账户的任何人都将拥有自己的个人密码库，可以从任何客户端应用程序访问。个人密码库对每个用户都是唯一的，并且只有该用户拥有访问它的钥匙，使用他们的电子邮箱地址和主密码的组合。账户所有者对个人账户以及存储在其中的个人[密码库项目](../../password-manager/your-vault/vault-items/vault-items.md)负责。组织[所有者、管理员和经理](member-roles.md)在设计上无法看到任何其他用户的个人密码库，从而确保某人的个人数据仍然属于他们自己。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/211wU2Nguupsr80j2vCSRz/d157eca06fe478049a3386cbe5b7ce56/bitwarden-individual-personal-vault.png?fm=webp&h=285&q=50&w=920" %}
个人了密码库
{% endembed %}

家庭、团队和企业组织自动为成员单独提供高级功能，如[紧急访问](../../account/log-in-and-unlock/more-log-in-options/emergency-access.md)和[加密附件存储](../../password-manager/your-vault/vault-items/file-attachments.md)，他们可以选择性使用。个人密码库仅仅是**个人**的，但个人密码库不支持共享，[组织密码库则可以](onboarding-and-succession.md#bitwarden-organizations)。

{% hint style="success" %}
**为什么默认提供个人密码库？**

个人密码库是 [Bitwarden 理念](onboarding-and-succession.md#the-bitwarden-approach)的一个重要组成部分。员工每天都会使用一系列的凭据，无论是个人的还是职业的，**在一个领域形成的习惯通常会成为另一个领域的习惯**。我们认为，在个人生活中使用适当的安全措施的员工会将这种良好的行为带到他们的职业生活中，从而在此过程中**保护您的业务**。

在这两个领域使用相同的工具有助于更快和更容易地形成这种习惯。企业组织拥有[配置策略](../oversight-visibility/enterprise-policies.md)选项，包括禁用个人密码库。
{% endhint %}

## Bitwarden 组织 <a href="#bitwarden-organizations" id="bitwarden-organizations"></a>

Bitwarden 组织为您的团队或企业的密码管理添加了一层协作和共享，使您可以安全地共享公共信息，例如办公室的 wifi 密码、在线凭据，或共享的公司信用卡等。通过组织进行安全共享既安全又容易。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/8wJfYqraeZpZLtfdsVRRF/f0eaf08e43e72d9ea4f728e2de197a1a/bitwarden-organization-collections.png?fm=webp&h=399&q=50&w=926" %}
组织密码库
{% endembed %}

任何人都可以直接从网页 App 创建一个组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3eSqWiTIuPSFxXdo5AAjT9/248b0fa7bb381add0d71682acd244a63/2024-12-03_13-57-58.png?_a=DAJCwlWIZAAB" %}
新增组织
{% endembed %}

创建后，您将进入管理控制台，这里是所有内容共享和组织管理的中心枢纽。启动该组织的人将成为所有者，他们能够完全控制**密码库**，以**管理**用户项目、成员、[集合](onboarding-and-succession.md#collections)和[群组](onboarding-and-succession.md#groups)，以及运行报告和配置[策略](onboarding-and-succession.md#enterprise-policies)等设置：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?_a=DAJCwlWIZAAB" %}
管理控制台
{% endembed %}

### 集合 <a href="#collections" id="collections"></a>

Bitwarden 组织以可扩展且安全的方式管理用户和数据。单独管理用户和数据对于大型企业来说效率低下，并且可能会出现错误。为了解决这个问题，组织提供了集合和[群组](onboarding-and-succession.md#collections)功能。

**集合**将登录、笔记、支付卡和身份收集在一起，以便在组织内[安全共享](../../password-manager/organization-members/sharing.md)：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3dkYfn5K3E4t3Ts3Rs5At0/02954064a4a43a626f03fc9746db4006/collections-graphic-1.png?fm=webp&h=140&q=50&w=509" %}
集合的使用
{% endembed %}

### 入职成员 <a href="#onboarding-members" id="onboarding-members"></a>

您的组织被建立并且用于存储数据的集合设置好后，此时，所有者和管理员应邀请新的成员。为了确保您组织的安全，Bitwarden 应用了一个 3 步流程来加入新的成员：[邀请](user-management.md#invite) → [接受](user-management.md#accept) → [确认](user-management.md#confirm)。

用户可以[直接从网页密码库](onboarding-and-succession.md#adding-users)登录，也可以使用[目录连接器](onboarding-and-succession.md#directory-connector)应用程序同步个人用户和[群组](onboarding-and-succession.md#groups)。

#### 添加成员 <a href="#adding-members" id="adding-members"></a>

在最简单的情况下，用户可以直接从网页 App 被添加到您的组织。在添加用户时，你可以指定授予他们可以访问哪些[集合](onboarding-and-succession.md#collections)、赋予他们哪个[角色](onboarding-and-succession.md#comprehensive-role-based-access-controls)，以及更多。

[了解如何一步一步将用户到您的组织。](user-management.md#onboard-users)

用户完全加入你的组织后，可以通过将他们分配给[集合](onboarding-and-succession.md#collections)来分配对组织密码库数据的访问权限。团队和企业组织可以将用户分配到[群组](onboarding-and-succession.md#groups)，以实现可扩展的权限分配，并构建群组-集合关联，而不是在个人层面上分配访问权限。

{% hint style="success" %}
对于大型组织，[目录连接器](onboarding-and-succession.md#directory-connector)是大规模入职和离职用户的最佳方式。
{% endhint %}

#### 群组 <a href="#groups" id="groups"></a>

群组将各个用户联系在一起，并提供一种可扩展的方式来分配权限，包括对[集合](onboarding-and-succession.md#collections)的访问和其他[访问控制](onboarding-and-succession.md#comprehensive-role-based-access-controls)。入职新用户时，将他们添加到群组中，他们将自动继承该群组的配置权限：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2BrgW8B8pbDiVAKyoYnxjR/e9348006d33dbd3ad25b9a25a5a27095/collections-graphic-2.png?fm=webp&h=304&q=50&w=449" %}
集合-群组的使用
{% endembed %}

#### 全面的基于角色的访问控制 <a href="#comprehensive-role-based-access-controls" id="comprehensive-role-based-access-controls"></a>

Bitwarden 使用了一种企业友好的方法来实现大规模的共享。用户可以被添加到具有[多个不同角色](member-roles.md)的组织中，隶属于不同的[群组](onboarding-and-succession.md#groups)，并将这些群组分配给不同的[集合](onboarding-and-succession.md#collections)，以实现精细化访问权限。可用的角色中有一个[自定义角色](member-roles.md#custom-role)，它用于管理权限的精细化配置。

### 离职用户 <a href="#offboarding-users" id="offboarding-users"></a>

在 Bitwarden，我们认为共享凭据是高效且安全地完成工作的一个重要方面。我们也认识到，从技术上来说，一旦一个凭据被共享，接收者就有可能保留它。出于这个原因，使用适当的[基于角色的访问控制](onboarding-and-succession.md#comprehensive-role-based-access-controls)和[实施策略](onboarding-and-succession.md#enterprise-policies)的安全入职，在促进安全离职方面起着重要作用。

Bitwarden 提供了多种工具，可用于定制工作流程和加强对继任的控制。下文将介绍一个基本的继任工作流程（不使用这些工具）和一些组织常用的高级继任策略：

### 基本离职 <a href="#basic-deprovisioning" id="basic-deprovisioning"></a>

从Bitwarden 中离职用户涉及到将用户从您的组织中移除，就像入职一样，可以[直接从网页密码库](user-management.md#offboard-users)中完成，也可以使用 [SCIM](scim/about-scim.md) 或 [Directory Connector](onboarding-and-succession.md#directory-connector) 自动完成。

Alice 是您企业中的一个**用户**，该组织托管在 Bitwarden Cloud 并使用公司电子邮箱地址（例如 `first-last@company.com`）。 目前，Alice 是这样使用 Bitwarden 的：

<table><thead><tr><th width="150">产品领域</th><th>描述</th></tr></thead><tbody><tr><td><strong>客户端应用程序</strong></td><td>在个人和职业上使用 Bitwarden 移动端和浏览器扩展，在组织上偶尔使用网页密码库进行相关工作。</td></tr><tr><td><strong>电子邮箱 &#x26; 主密码</strong></td><td>使用 <code>alice@company.com</code> 和 <code>p@ssw0rD</code> 登录 Bitwarden。</td></tr><tr><td><strong>个人项目</strong></td><td>在她的个人密码库中存储各种个人项目，包括登录和信用卡。</td></tr><tr><td><strong>两步登录</strong></td><td>使用组织层面的 <a href="../../account/two-step-login/setup-guides/two-step-login-via-duo.md">Duo 2FA</a>。</td></tr><tr><td><strong>集合</strong></td><td>Alice 对「Marketing Credentials」集合具有「可以管理」权限，授予她可以管理该集合的许多方面。</td></tr><tr><td><strong>已共享的项目</strong></td><td>创建并共享了多个归组织所有并驻留在她团队集合中的密码库项目。</td></tr></tbody></table>

#### 当 Alice 从您的组织中被移除后： <a href="#once-offboarded" id="once-offboarded"></a>

<table><thead><tr><th width="150">产品领域</th><th>描述</th></tr></thead><tbody><tr><td><strong>客户端应用程序</strong></td><td><p>可以继续使用任一个 Bitwarden 应用程序访问她的个人密码库，但将<strong>立即失去对组织密码库、所有集合和所有已共享项目的访问权限</strong>。</p><p></p><p>有关本地缓存的信息，请参阅本节末尾的提示。</p></td></tr><tr><td><strong>电子邮箱 &#x26; 主密码</strong></td><td>可以继续使用 <code>alice@company.com</code> 和 <code>p@ssw0rD</code> 登录，但是由于她无法访问她的 <code>@company.com</code> 收件箱，因此应该建议她更改为与她的 Bitwarden 账户关联的电子邮箱。</td></tr><tr><td><strong>个人项目</strong></td><td>仍然可以使用她的个人密码库并访问存储在其中的项目。</td></tr><tr><td><strong>组织中的权限</strong></td><td>将<strong>立即失去与组织相关的所有事物的所有权限和访问权限</strong>。</td></tr><tr><td><strong>两步登录</strong></td><td>将无法使用组织层面的 Duo 2FA 访问她的密码库，但可以设置为我们的免费两步登录选项之一或升级到高级版以获取更多功能。</td></tr><tr><td><strong>已创建的集合</strong></td><td>Alice 的「Marketing Credentials」集合，将由组织所有者和管理员保留，他们可以为某个新用户分配「可以管理」权限。</td></tr><tr><td><strong>已共享的项目</strong></td><td>集合和已共享项目的所有权<strong>属于组织</strong>，因此 Alice 将无法访问所有这些项目，尽管已创建它们。</td></tr></tbody></table>

{% hint style="success" %}
离线设备会缓存密码库数据（包括组织密码库数据）的只读副本。 某些客户端可能会在成员离职后的短时间内保留对该只读数据的访问权限。如果预计会有人恶意利用这一点，则应在将成员从组织中移除时更新其曾拥有访问权限的凭据。
{% endhint %}

### 高级离职 <a href="#advanced-deprovisioning" id="advanced-deprovisioning"></a>

{% hint style="danger" %}
对于那些使用[受信任设备 SSO](../login-with-sso/trusted-devices/about-trusted-devices.md) 而没有主密码的账户，[从您的组织中移除他们](user-management.md#offboard-users)将切断其对 Bitwarden 账户的所有访问权限，除非：

1. 您事先使用[账户恢复](account-recovery/about-account-recovery.md)为其分配了主密码。
2. 用户在账户恢复后至少登录一次，以便完全完成账户恢复工作流程。

此外，除非在用户从组织中删除之前采取上述步骤，否则用户将无法重新加入组织。在这种情况下，用户将被要求[删除其账户](../../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，并收到创建账户和加入组织的新邀请。

撤销对组织的访问权限，但不将其从组织中移除，将允许其登录 Bitwarden 并**仅**访问其个人密码库。
{% endhint %}

#### 管理接管 <a href="#administrative-take-over" id="administrative-take-over"></a>

使用[主密码重置策略](../oversight-visibility/enterprise-policies.md#account-recovery-administration)，您企业的所有者和管理员可以在继任期间重置用户的主密码。

重置用户的主密码后，用户将退出所有活动的 Bitwarden 会话，并将其登录凭据重置为管理员指定的凭据，这意味着该管理员（也只有该管理员）将拥有该用户密码库数据的密钥，包括个人密码库中的项目。 这种密码库接管策略通常被企业用来确保员工不会保留对可能与工作相关的个人密码库项目的访问权限，并可用于促进对员工可能使用的每个凭据的审计。

{% hint style="info" %}
**管理员密码重置不会绕过两步登录**。在许多情况下，我们建议使用 SSO，因为有些 IdP 允许您为用户配置 2FA 和 2FA 旁路策略。
{% endhint %}

#### 移除个人密码库 <a href="#removing-the-individual-vault" id="removing-the-individual-vault"></a>

如果组织需要实时控制所有密码库项目，您可以使用[禁用个人密码库策略](../oversight-visibility/enterprise-policies.md#remove-individual-vault)，要求用户将所有密码库项目保存到组织。这将避免在继任过程中接管和审计用户账户，因为一旦从组织中移除，账户中的数据将完全清空。

#### 删除不再登录的账户 <a href="#login-less-account-deletion" id="login-less-account-deletion"></a>

如前所述，从组织中移除用户并不会自动删除其 Bitwarden 账户。在基本的继任工作流程中，当用户被移除后，他们就不能再访问组织或任何共享项目和集合，但他们仍然可以使用现有的主密码登录 Bitwarden 并访问任何个人密码库项目。

组织如果希望完全删除账户，包括所有个人密码库项目，可以在继任过程中使用以下方法之一来实现：

1. 如果您是自行托管 Bitwarden，授权管理员可以从[系统管理员门户](../../self-hosting/system-administrator-portal.md)删除账户。
2. 如果该账户有一个由贵公司控制的 @yourcompany.com 电子邮箱地址，您可以使用[无需登录而删除](../../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)工作流程，并在 @yourcompany.com 收件箱中确认删除。

## 为您的业务设计您的组织 <a href="#designing-your-organization-for-your-business" id="designing-your-organization-for-your-business"></a>

在 Bitwarden，我们经常说密码管理就是人员管理，我们可以提供适合您的组织的工作流程。通过提供广泛的选择，通过我们的开源方法共享，客户可以放心，他们可以得到满足自己的个性化需求。

[立即开始](https://bitwarden.com/pricing/business/)免费试用企业版或团队版。

### SCIM

对于拥有使用受支持的身份（目前包括 Azure AD、Okta、OneLogin 和 JumpCloud）运营的庞大用户群的企业组织，SCIM 集成可用于自动配置 Bitwarden 组织中的成员和群组。[了解更多](scim/about-scim.md)。

### Directory Connector

对于使用目录服务（LDAP、AD、Okta 等）运营的拥有庞大用户群的公司，Directory Connector 可以将目录中的用户和群组同步到 Bitwarden 组织。Directory Connector 是一个独立的应用程序，用以访问您的目录和 Bitwarden，可以在任何地方运行。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6kt3QORL97ZWxcZX2gicVl/038aaad07a9c4e00dd4cf7d6303d9578/bitwarden-directory-connector.png?fm=webp&h=424&q=50&w=930" %}
目录连接器
{% endembed %}

许多 Bitwarden 团队和企业组织将他们的入职工作的重点放在 Directory Connector 上，并使用组织密码库管理区域来管理组​群组-集合关系。

Directory Connector 可以：

* 将基于 LDAP 的目录群组与 Bitwarden 群组同步
* 同步每个群组内的用户
* 邀请新用户加入组织
* 从组织中移除已删除的用户

### SSO 登录 <a href="#login-with-sso" id="login-with-sso"></a>

Bitwarden 企业组织可以使用 SAML 2.0 或 OIDC 与您现有的身份提供程序 (IdP) 集成，以允许您组织的成员使用 SSO 登录 Bitwarden。SSO 登录将用户身份验证与密码库解密分开：

**身份验证**通过您选择的 IdP 完成，并保留连接到该 IdP 的任何双重身份验证过程。密码库数据的**解密**需要用户的个人密钥，该密钥部分源自主密码。有两个[解密选项](../../login-with-sso/member-decryption-options.md)，这两个选项都会让用户使用他们的常规 SSO 凭据进行身份验证。

* **主密码**：通过身份验证后，组织成员将使用他们的主密码解密密码库数据。
* **客户管理的加密**：连接 SSO 登录到您的自托管解密密钥服务器。使用此选项，组织成员无需使用其主密码来解密密码库数据。相反，[Key Connector](../../self-hosting/key-connector/about-key-connector.md) 将获取安全地存储在您拥有和管理的数据库中的解密密钥。这种方法确保您可以：
  * 利用您现有的身份提供程序
  * 保护数据的端到端加密
  * 自动布建用户
  * 配置使用或不使用 SSO 访问
  * 根据贵公司的安全需求解密密码库数据

### 企业策略 <a href="#enterprise-policies" id="enterprise-policies"></a>

企业组织可以实施各种旨在为任何企业奠定安全基础的策略。这些策略包括：

* **要求两步登录**：要求用户在个人账户上设置两步登录。
* **主密码要求**：设置主密码强度的最低要求。
* **密码生成器**：设置密码生成器配置的最低要求。
* **单一组织**：限制用户加入任何其他组织。
* **禁用个人密码库**：要求用户通过删除个人所有权选项将密码库项目保存到组织。

{% hint style="success" %}
例如，**禁用个人密码库**策略与前面关于个人密码库和组织密码库之间相互作用的讨论相吻合。一些公司可能希望确保所有凭据都保留在组织密码库中。一种可能的实施方案是允许每个个人用户拥有自己的集合，这与个人密码库不同，集合可以由组织所有者和管理员来监督。
{% endhint %}

### 事件日志 <a href="#event-logs" id="event-logs"></a>

Bitwarden 组织包括了对[事件日志](../oversight-visibility/event-logging/event-logs.md)的访问，这些日志可以直接从网页密码库查看或[导出以在 Splunk 等安全信息和事件管理（SIEM）系统中进行分析](../oversight-visibility/event-logging/event-logs.md#siem-and-external-systems-integrations)。事件日志包括以下信息：

* 用户 - 项目交互
* 对密码库项目所做的更改
* 入职事件
* 组织配置更改
* 以及更多

{% hint style="success" %}
除了这些好处外，客户还很欣赏将 Bitwarden 紧密集成到他们现有系统中的能力。Bitwarden 提供了一个强大的公共 [API](https://bitwarden.com/help/api/) 和一个功能齐全的[命令行界面](../../password-manager/developer-tools/cli/password-manager-cli.md) (CLI)，以进一步整合到现有的组织工作流程中。
{% endhint %}

### 自托管 <a href="#self-hosting" id="self-hosting"></a>

为了与 Bitwarden 随时随地提供密码管理的方法保持一致，Bitwarden 提供了一个自托管选项，以为企业解决更广泛的使用情况。公司选择自托管的原因有很多。特别是在入职、离职和增强功能方面，以下是公司选择这样做的一些原因：

* **立即删除用户账户**：由于您控制服务器，因此可以完全删除用户（包括他们的个人密码库）。
* **网络访问控制**：组织所有者可以确定员工必须使用哪些网络访问权限来访问他们的 Bitwarden 服务器。
* **高级代理设置**：管理员可以选择启用或禁用某些类型的设备访问 Bitwarden 服务器。
* **使用现有的数据库集群**：连接到现有的 Microsoft SQL Server 数据库。将来会支持其他数据库。
* **增加文件附件和 Bitwarden Send 的存储空间**：Bitwarden 项目或 Bitwarden Send 的文件附件保留在用户提供的存储空间中。

## 把碎片放在一起 <a href="#put-the-pieces-together" id="put-the-pieces-together"></a>

Directory Connector、SSO 登录、企业策略和您的密码库独立或协调工作，以优化您的入职、离职和组织管理体验。下表详细说明了将这些部分串在一起形成一个平滑过程的方式：

<table><thead><tr><th width="150">步骤</th><th>描述</th></tr></thead><tbody><tr><td><strong>同步</strong></td><td>使用 Directory Connector 将群组和用户从您现有的目录服务同步到 Bitwarden。</td></tr><tr><td><strong>邀请</strong></td><td>Directory Connector 会自动向同步的用户发出邀请。</td></tr><tr><td>身份<strong>验证</strong></td><td>将您的 SSO 登录实施与 SSO 策略配对，以要求用户在接受邀请时注册 SSO。</td></tr><tr><td><strong>管理</strong></td><td>使用网页密码库界面将一些用户提升到不同的角色，并确保群组 - 集合关系被配置为授予正确的用户以正确的访问权限。</td></tr><tr><td><strong>重新同步</strong></td><td>定期重新运行 Directory Connector 以从 Bitwarden 中移除不再在您的目录服务中处于活动状态的用户并开始新员工入职。</td></tr></tbody></table>

## FAQ <a href="#faqs" id="faqs"></a>

### 问：如果员工已经有 Bitwarden 账户，是否可以将其附加到组织中，这样他们就不需要另一个 Bitwarden 账户了？ <a href="#q-if-an-employee-already-has-a-bitwarden-account-can-we-attach-it-to-the-organization-so-they-dont-n" id="q-if-an-employee-already-has-a-bitwarden-account-can-we-attach-it-to-the-organization-so-they-dont-n"></a>

**答：**&#x662F;的！可以。一些客户建议在将附加用户到组织之前，这些用户将 Bitwarden 密码库附加到他们的公司电子邮箱中。这种选择是特定于公司的，任何一种方法都可以。

### 问：当员工离职时，我们是否可以将他们的帐户从组织中分离出来，这样他们就无法再访问公司凭据，也不会丢失个人凭据？ <a href="#q-when-an-employee-leaves-can-we-detach-their-account-from-the-organization-so-that-they-dont-have-a" id="q-when-an-employee-leaves-can-we-detach-their-account-from-the-organization-so-that-they-dont-have-a"></a>

**答：**&#x53EF;以！这正是[离职](onboarding-and-succession.md#offboarding-users)所需要做的事情。

### 问：组织前成员创建或共享的项目会发生什么？这些项目是否也会被删除吗？ <a href="#q-what-happens-to-items-that-were-created-or-shared-by-a-former-member-of-the-organization-will-thes" id="q-what-happens-to-items-that-were-created-or-shared-by-a-former-member-of-the-organization-will-thes"></a>

**答：**&#x4E0D;会。将项目从个人密码库共享到组织密码库也会将项目所有权扩展到组织。

### 问：我们能否防止员工将公司组织的凭据复制到他们的个人密码库中？ <a href="#q-can-we-prevent-employees-from-duplicating-credentials-from-the-company-organization-to-their-indiv" id="q-can-we-prevent-employees-from-duplicating-credentials-from-the-company-organization-to-their-indiv"></a>

**答：**&#x53EF;以！使用我们[全面的基于角色的访问控制套件](member-roles.md#access-control)，您可以将凭据设为**只读**以防止复制副本。

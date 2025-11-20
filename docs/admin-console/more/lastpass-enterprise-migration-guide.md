# LastPass 企业版迁移指南

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/lastpass-enterprise-migration-guide/)、[GitHub 地址](https://github.com/bitwarden/help/blob/master/_articles/importing/lastpass-enterprise-migration-guide.md)
{% endhint %}

使用 Bitwarden 安全迁移您的组织，这既简单又安全。遵循本指南中的步骤从 LastPass 迁移数据和用户：

1. [创建和配置您的 Bitwarden 组织](lastpass-enterprise-migration-guide.md#step-1-setup-your-organization)。
2. [导入您的数据到 Bitwarden](lastpass-enterprise-migration-guide.md#step-2-import-data)。
3. [入职用户](lastpass-enterprise-migration-guide.md#step-3-onboard-users)
4. [配置对集合和密码库项目的访问权限](lastpass-enterprise-migration-guide.md#step-4-configure-access-to-collections-and-items)。

{% hint style="success" %}
如果您在迁移期间需要协助，我们的[客户成功团队将随时为您提供帮助](https://bitwarden.com/contact/)！
{% endhint %}

## 适用范围 <a href="#scope" id="scope"></a>

本文档描述了将安全数据从 LastPass 实例迁移到 Bitwarden [团队或企业组织](../organizations-overview.md)的最佳实践，基于简单和可扩展的方法构建安全基础设施。

[密码管理](https://bitwarden.com/products/business/)对于组织安全和运营效率至关重要。这里提供有关执行迁移和配置的最佳方法的见解，旨在最大程度地减少交换企业工具时经常需要的试错方法。

文档中的步骤**按推荐的顺序列出**，以便于用户轻松使用和顺利入职。

## 第 1 步：设置您的组织 <a href="#step-1-setup-your-organization" id="step-1-setup-your-organization"></a>

Bitwarden 组织将用户和密码库项目联系在一起，以便[安全地共享](../../password-manager/organization-members/sharing.md)登录、笔记、支付卡和身份。

{% hint style="success" %}
最佳的做法是，首先创建一个组织，然后直接[向组织导入数据](../manage-shared-items/import-organization-items/import-to-organization.md)，而不是先向个人账户导入数据，然后再将[移动项目](../../password-manager/organization-members/sharing.md)到组织。
{% endhint %}

1、**创建您的组织**。从创建组织开始。要了解如何操作，请查看[这篇文章](../organizations-overview.md#create-an-organization)。

{% hint style="info" %}
对于自托管 Bitwarden，请在 Bitwarden 云端创建一个组织，生成[许可证密钥](https://bitwarden.com/host/)，然后在您的服务器上使用该密钥[解锁组织](../../self-hosting/licensing-on-premise.md#organization-license)。
{% endhint %}

2、**入职管理用户**。创建好组织后，可以通过入职一些[管理用户](../manage-members/member-roles.md)来简化进一步的设置过程。此时**不要开始最终用户入职**，这一点很重要，因为还有几个步骤来准备您为组织。[此处](../manage-members/user-management.md#onboard-users)了解如何邀请管理员。

3、**配置身份服务**。企业组织支持使用 SAML 2.0 或 OpenID Connect (OIDC) 的[单点登录](../login-with-sso/about-login-with-sso.md) (SSO)。要配置 SSO，请在管理控制台中打开组织的**设置** → **单点登录**界面，[组织所有者和管理员](../manage-members/member-roles.md)都可以访问该界面。

4、**启用企业策略**。[企业策略](../oversight-visibility/enterprise-policies.md)使组织能够为用户实施规则，例如要求使用两步登录。强烈建议在用户入职前配置策略。

## 第 2 步：导入数据 <a href="#step-2-import-data" id="step-2-import-data"></a>

数据可以直接从 LastPass 导入，也可以使用 LastPass [导出的文件](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#export-from-lastpass)导入。如果您是使用 LastPass SSO 的团队成员，LastPass 管理员将需要完成一个简短的设置过程，然后您才能使用直接导入选项（[了解更多](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#direct-import-with-sso)）。

要使用**直接导入**方式将数据导入到您的组织：

1、登录到 Password Manager 浏览器扩展或桌面 App。

2、在浏览器扩展中，选择**设置**选项卡，然后选择**导入项目**选项。或者，在桌面 App 中，选择**文件** > **导入数据**。

3、从下拉菜单中填写以下字段：

* **导入目的地**：选择导入目的地，例如您具有访问权限的组织密码库。
* **文件夹**或**集合**：选择是否要将导入的内容移动到您具有访问权限的特定集合。
* [**文件格式**](../../password-manager/import-and-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择 LastPass。
* 在 LastPass 说明框中，选择**直接从 LastPass 导入**选项。
* 输入您的 **LastPass 电子邮箱**。

{% hint style="success" %}
如果您的 LastPass 账户激活了多重身份验证，系统将提示您从身份验证器 App 输入一次性密码。如果您使用 Duo 进行 MFA，则仅支持应用内审批来满足您的 MFA 要求。
{% endhint %}

4、选择**导入数据**按钮以触发导入。

5、系统将提示您输入 LastPass 主密码，或者如果您的 LastPass 账户使用 SSO，则系统将提示您登录到您的 IdP。无论哪种情况，请按照提示登录您的 LastPass 账户。

{% hint style="success" %}
您还应建议员工从现有的密码管理器中导出他们个人拥有的数据，并准备将其导入 Bitwarden。[了解更多](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md)。
{% endhint %}

## 第 3 步：入职用户 <a href="#step-3-onboard-users" id="step-3-onboard-users"></a>

Bitwarden 支持通过网页密码库手动入职和通过 SCIM 集成或从现有目录服务同步自动入职：

### 手动入职 <a href="#manual-onboarding" id="manual-onboarding"></a>

为确保您组织的安全，Bitwarden 采用了三步流程入职新成员：[邀请](../manage-members/user-management.md#invite) → [接受](../manage-members/user-management.md#accept) → [确认](../manage-members/user-management.md#confirm)。了解[如何邀请新用户](../manage-members/user-management.md#onboard-users)。

{% hint style="success" %}
用户入职后，指导他们使用导出的文件将其个人数据导入到 Bitwarden，如果他们的 LastPass 账户仍处于激活状态，则使用[此处](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#zhi-jie-dao-ru)描述的**直接导入**方法。
{% endhint %}

### 自动入职 <a href="#automated-onboarding" id="automated-onboarding"></a>

通过与 [Azure AD](../manage-members/scim/microsoft-entra-id-scim-integration.md)、[Okta](../manage-members/scim/okta-scim-integration.md)、[OneLogin](../manage-members/scim/onelogin-scim-integration.md) 和 [JumpCloud](../manage-members/scim/jumpcloud-scim-integration.md) 的 SCIM 集成，或使用 [Directory Connector](../manage-members/directory-connector/about-directory-connector.md)（一个可在[桌面 App](../manage-members/directory-connector/directory-connector-desktop-app.md) 和 [CLI](../manage-members/directory-connector/directory-connector-cli.md) 工具中使用的独立应用程序），可实现自动用户入职，从而同步现有目录服务中的用户和群组。

无论使用哪种方式，用户都会被自动邀请加入组织，并可使用 [Bitwarden CLI](../../password-manager/developer-tools/cli/password-manager-cli.md#confirm) 工具手动或自动确认。

{% hint style="success" %}
用户入职后，指导他们使用导出的文件将其个人数据导入到 Bitwarden，如果他们的 LastPass 账户仍处于激活状态，则使用[此处](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#zhi-jie-dao-ru)描述的**直接导入**方法。
{% endhint %}

## 第 4 步：配置对集合和项目的访问权限 <a href="#step-4-configure-access-to-collections-and-items" id="step-4-configure-access-to-collections-and-items"></a>

通过集合、群组、群组级别或用户级别权限配置访问权限，与最终用户共享密码库项目：

### 集合 <a href="#collections" id="collections"></a>

Bitwarden 使团队和组织能够以一种可扩展的方式轻松、安全地共享敏感数据。这是通过将共享的机密、项目、登录等划分为**集合**来实现的。

集合以多种方式来组织安全项目，包括但不限于：业务功能、群组分配、应用程序访问级别，甚至安全协议。集合与共享文件夹的功能相同，允许用户群组之间的共享和访问控制的一致性。

LastPass 的共享文件夹可以通过使用[这里](https://bitwarden.com/help/files/bitwarden_export_org.csv)的组织导入模板并将共享文件夹的名称放在 `collections` 列中，从而将 LastPass 中的共享文件夹作为集合导入到 Bitwarden 中。

集合既可以与群组共享，也可以与单个用户共享。限制可访问集合的个人用户数量将提高管理员的管理效率。[ 此处了解更多](../manage-shared-items/collections/about-collections.md)。

{% hint style="info" %}
嵌套集合不会继承顶层集合的权限。请参阅[使用群组](../manage-members/groups.md#using-groups)指定权限。
{% endhint %}

### 群组 <a href="#groups" id="groups"></a>

使用群组进行共享是提供凭证和安全访问的最有效方式。群组和用户一样，可以使用 SCIM 或目录连接器同步到组织中。

### 权限 <a href="#permissions" id="permissions"></a>

可以在群组或用户级别分配 Bitwarden 集合的权限。这意味着每一个群组或用户可以配置为对同一个集合拥有权限。集合权限选项包括：

* 可以查看
* 可以查看，密码除外
* 可以编辑
* 可以编辑，密码除外
* 可以管理

[此处](../manage-members/member-roles.md#permissions)了解有关权限的更多信息。Bitwarden 使用权限结合来确定用户和集合的最终访问权限。例如：

* 用户 A 是「Tier 1 Support」群组的成员，该群组可以访问「Support」集合，并拥有查看权限。
* 用户 A 也是「Support Management」群组的成员，该群组可以访问「Support」集合，并拥有编辑权限。
* 这种情况下，用户 A 将可以编辑该集合。

## 迁移支持 <a href="#migration-support" id="migration-support"></a>

Bitwarden 客户成功团队 24/7 全天候为企业和团队组织提供优先支持。如果您需要帮助或有疑问，请随时[联系我们](https://bitwarden.com/contact/)。

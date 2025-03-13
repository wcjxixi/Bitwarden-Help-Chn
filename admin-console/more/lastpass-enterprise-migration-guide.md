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
如果您在迁移期间需要协助，我们的[客户成功团队将随时为您提供帮助](lastpass-enterprise-migration-guide.md#migration-support)！
{% endhint %}

## 适用范围 <a href="#scope" id="scope"></a>

本文档将描述将安全数据从 LastPass 实例迁移到 Bitwarden [团队或企业组织](../../organizations/organizations.md)的最佳实践，基于简单和可扩展的方法构建安全基础设施。

[密码管理](https://bitwarden.com/products/business/)对于组织安全和运营效率至关重要。这里提供有关执行迁移和配置的最佳方法的见解，旨在最大程度地减少交换企业工具时经常需要的试错方法。

文档中的步骤**按推荐的顺序列出**，以便于用户轻松使用和顺利入职。

## 第 1 步：设置您的组织 <a href="#step-1-setup-your-organization" id="step-1-setup-your-organization"></a>

Bitwarden 组织将用户和密码库项目联系在一起，以便[安全地共享](../../organizations/sharing.md)登录、笔记、支付卡和身份。

{% hint style="success" %}
最佳的做法是，首先创建一个组织，然后直接[向组织导入数据](../../import-export/import-data-to-an-organization.md)，而不是先向个人账户导入数据，然后再将[移动项目](../../organizations/sharing.md)到组织。
{% endhint %}

1、**创建您的组织**。从创建组织开始。要了解如何创建，请查看[这篇文章](../../organizations/organizations.md#create-an-organization)。

{% hint style="info" %}
要自托管 Bitwarden，请在 Bitwarden 云端创建一个组织，生成一个[许可证密钥](https://bitwarden.com/host/)，并使用该密钥[解锁服务器上的组织](../../self-hosting/licensing-for-paid-features.md#organization-license)。
{% endhint %}

2、**入职管理用户**。创建好组织后，可以通过入职一些[管理用户](../user-management/member-roles-and-permissions.md)来简化进一步的设置过程。重要的是，此时**不要开始最终用户入职**，因为还有几个步骤需要您为组织做好准备。[此处](../../organizations/user-management.md#onboard-users)了解如何邀请管理员。

3、**配置身份服务**。企业组织支持使用 SAML 2.0 或 OpenID Connect (OIDC) 的[单点登录](../../login-with-sso/about-login-with-sso.md) (SSO)。要配置单点登录，请在管理控制台中打开组织的**设置** → **单点登录**界面，[组织所有者和管理员](../user-management/member-roles-and-permissions.md)都可以访问该界面。

4、**启用企业策略**。[企业策略](../../organizations/enterprise-policies.md)使组织能够为用户实施规则，例如要求使用两步登录。强烈建议在用户入职前配置策略。

## 第 2 步：导入数据 <a href="#step-2-import-data" id="step-2-import-data"></a>

### &#x20;从 LastPass 导出 <a href="#export-from-lastpass" id="export-from-lastpass"></a>

从 LastPass 网页密码库完整导出包含所有您的共享数据为 `.csv` 文件（[了解如何导出](https://support.lastpass.com/s/document-item?language=en_US\&bundleId=lastpass\&topicId=LastPass/export-generic-csv.html&_LANG=enus)）。收集完整导出可能需要在创建导出之前将所有共享文件夹分配给导出用户。

此外，在 LastPass 中创建的任何导出都将包含来自个人密码库和指定共享文件夹的数据。在此阶段，我们建议对创建的导出进行审核，以确保其中包含所有共享数据，而不包含个人数据。

### 导入到 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

要将数据导入您的组织：

1、登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航至**设置** → **导入数据**：

3、从下拉菜单中填写以下字段：

* **集合**：选择是否要将导入的内容移动到现有的集合中。在大多数情况下，您不会在 Bitwarden 中创建集合，因为导入会为您创建集合，所以请将此选项留空。
* [**文件格式**](../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择 **Lastpass (csv)**。

4、选择**选择文件**然后添加要导入的文件，或在输入框中复制并粘贴文件内容。

{% hint style="danger" %}
导入到 Bitwarden 无法检查要导入的文件中的项目是否与您密码库中的项目重复。这意味着，如果密码库和要导入的文件中都已经有一个项目，那么导入多个文件就会创建重复的密码库项目。
{% endhint %}

5、选择**导入数据**触发导入。

[文件附件](../../your-vault/file-attachments.md)需要手动上传到密码库。请注意，LastPass 中嵌套的共享文件夹会在你的 Bitwarden 组织中重新创建为嵌套的集合，但如果「父」集合中没有数据，需要您手动创建名称匹配的父集合。

{% hint style="success" %}
您还应建议员工从现有的密码管理器中导出个人拥有的数据，并准备将其导入 Bitwarden。[了解更多](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md)。
{% endhint %}

## 第 3 步：入职用户 <a href="#step-3-onboard-users" id="step-3-onboard-users"></a>

Bitwarden 支持通过网页密码库手动入职和通过 SCIM 集成或从现有目录服务同步自动入职：

### 手动入职 <a href="#manual-onboarding" id="manual-onboarding"></a>

为确保您组织的安全，Bitwarden 采用了三步流程入职新成员：[邀请](../../organizations/user-management.md#invite) → [接受](../../organizations/user-management.md#accept) → [确认](../../organizations/user-management.md#confirm)。了解[如何邀请新用户](../../organizations/user-management.md#onboard-users)。

{% hint style="success" %}
用户入职后，指导他们使用导出的文件将其个人数据导入到 Bitwarden，如果他们的 LastPass 账户仍处于激活状态，则使用[此处](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#zhi-jie-dao-ru)描述的**直接导入**方法。
{% endhint %}

### 自动入职 <a href="#automated-onboarding" id="automated-onboarding"></a>

通过 SCIM 与 [Azure AD](../../scim/azure-ad-scim-integration.md)、[Okta](../../scim/okta-scim-integration.md)、[OneLogin](../../scim/onelogin-scim-integration.md) 和 [JumpCloud](../../scim/jumpcloud-scim-integration.md) 的 SCIM 集成，或使用 [Directory Connector](../../directory-connector/about-directory-connector.md)（一个可在[桌面 App](../../directory-connector/directory-connector-desktop-app.md) 和 [CLI](../../directory-connector/directory-connector-cli.md) 工具中使用的独立应用程序），可实现自动用户入职，从而同步现有目录服务中的用户和群组。

无论使用哪种方式，用户都会被自动邀请加入组织，并可使用 [Bitwarden CLI](../../password-manager/developer-tools/password-manager-cli.md#confirm) 工具手动或自动确认。

{% hint style="success" %}
用户入职后，指导他们使用导出的文件将其个人数据导入到 Bitwarden，如果他们的 LastPass 账户仍处于激活状态，则使用[此处](../../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#zhi-jie-dao-ru)描述的**直接导入**方法。
{% endhint %}

## 第 4 步：配置对集合和项目的访问权限 <a href="#step-4-configure-access-to-collections-and-items" id="step-4-configure-access-to-collections-and-items"></a>

通过集合、群组、群组级别或用户级别权限配置访问权限，与最终用户共享密码库项目：

### 集合 <a href="#collections" id="collections"></a>

Bitwarden 使团队和组织能够以一种可扩展的方式轻松、安全地共享敏感数据。这是通过将共享的机密、项目、登录等划分为**集合**来实现的。

集合以多种方式来组织安全项目，包括但不限于：业务功能、群组分配、应用程序访问级别，甚至安全协议。集合与共享文件夹的功能相同，允许用户群组之间的共享和访问控制的一致性。

LastPass 的共享文件夹可以通过使用[这里](https://bitwarden.com/help/files/bitwarden_export_org.csv)的组织导入模板并将共享文件夹的名称放在 `collections` 列中，从而将 LastPass 中的共享文件夹作为集合导入到 Bitwarden 中。

集合既可以与群组共享，也可以与单个用户共享。限制可访问集合的个人用户数量将提高管理员的管理效率。[ 此处了解更多](../../organizations/collections.md)。

{% hint style="info" %}
嵌套集合不会继承顶层集合的权限。请参阅[使用群组](../../organizations/groups.md#using-groups)指定权限。
{% endhint %}

### 群组 <a href="#groups" id="groups"></a>

利用群组进行共享是提供凭证和安全访问的最有效方式。群组和用户一样，可以使用 SCIM 或目录连接器同步到组织中。

### 权限 <a href="#permissions" id="permissions"></a>

Bitwarden 集合的权限可以在群组或用户级别上分配。这意味着每个群组或用户可以为同一个集合配置不同的权限。集合权限选项包括：

* 可以查看
* 可以查看，密码除外
* 可以编辑
* 可以编辑，密码除外
* 可以管理

[此处](../user-management/member-roles-and-permissions.md#permissions)了解有关权限的更多信息。Bitwarden 使用权限结合来确定用户和集合的最终访问权限。例如：

* 用户 A 是「Tier 1 Support」群组的成员，该群组可以访问「Support」集合，并拥有查看权限。
* 用户 A 也是「Support Management」群组的成员，该群组可以访问「Support」集合，并拥有编辑权限。
* 这种情况下，用户 A 将可以编辑该集合。

## 迁移支持 <a href="#migration-support" id="migration-support"></a>

Bitwarden 客户成功团队 24/7 全天候为企业和团队组织提供优先支持。如果您需要帮助或有疑问，请随时[联系我们](https://bitwarden.com/contact/)。

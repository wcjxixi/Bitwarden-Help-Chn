# 团队版和企业版迁移指南

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/teams-enterprise-migration-guide/)
{% endhint %}

使用 Bitwarden 安全迁移您的组织，这既简单又安全。简单地遵循本指南中的步骤从您现有的密码管理器中迁移数据和用户：

1. [导出数据](teams-and-enterprise-migration-guide.md#step-1-export-your-data)
2. [创建和配置您的 Bitwarden 组织](teams-and-enterprise-migration-guide.md#step-2-setup-your-bitwarden-organization)
3. [导入数据到 Bitwarden](teams-and-enterprise-migration-guide.md#step-3-import-data-to-your-organization)
4. [入职用户](teams-and-enterprise-migration-guide.md#step-4-onboard-users-to-the-organization)
5. [配置对集合和密码库项目的访问权限](teams-and-enterprise-migration-guide.md#step-5-configure-access-to-collections-and-items)

{% hint style="success" %}
如果您在迁移期间需要协助，我们的[客户成功团队将随时为您提供帮助](https://bitwarden.com/contact/)！
{% endhint %}

## 适用范围 <a href="#scope" id="scope"></a>

本文档描述了将安全数据从您当前的密码管理器迁移到 Bitwarden [团队或企业组织](../organizations/organizations.md)的最佳实践，基于简单和可扩展的方法构建安全基础设施。

密码管理对于组织安全和运营效率至关重要。这里提供有关执行迁移和配置的最佳方法的见解，旨在最大程度地减少交换企业工具时经常需要的试错方法。

文档中的步骤**按推荐的顺序列出**，以便于用户轻松使用和顺利入职。

## 第 1 步：导出数据 <a href="#step-1-export-your-data" id="step-1-export-your-data"></a>

从其他密码管理器导出数据的方法因解决方案而异，并且在某些情况下可能有点棘手。请使用我们的[导入和导出指南](../import-export/)来获取帮助，例如，从 [Lastpass](../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#export-from-lastpass) 或 [1Password](../password-manager/import-and-export/import-guides/import-data-from-1password.md#export-your-1-password-1-pif-logins) 导出。

收集完整的数据导出可能需要将共享文件夹或项目分配给个人用户以进行导出，或者在具有适当权限的用户之间执行多个导出。此外，导出的数据可能包含个人数据以及共享/组织数据，所以在导入 Bitwarden 之前，请确保从导出文件中移除个人项目。

收集完整的数据导出可能需要将共享文件夹或项目分配给单个用户进行导出，或在具有适当权限的用户之间执行多次导出。 此外，导出的数据可能包括个人所有的数据和共享/组织数据，因此在[导入到 Bitwarden](teams-and-enterprise-migration-guide.md#step-3-import-data-to-your-organization) 之前，请务必从导出文件中移除个人项目。

{% hint style="info" %}
我们建议在导出过程中特别注意以下数据类型的位置：

* 安全文档
* 安全文件附件
* 安全笔记
* SSH/RSA 密钥文件
* 共享文件夹
* 嵌套的共享项目
* 密码管理基础架构中的任何自定义结构
{% endhint %}

## 第 2 步：设置您的组织 <a href="#step-2-setup-your-organization" id="step-2-setup-your-organization"></a>

Bitwarden 组织将用户和密码库项目联系在一起，以便[安全地共享](../organizations/sharing.md)登录、笔记、支付卡和身份。

{% hint style="success" %}
最佳的做法是，首先创建一个组织，然后直接[向组织导入数据](../import-export/import-data-to-an-organization.md)，而不是先向个人账户导入数据，然后再将[移动项目](../organizations/sharing.md)到组织。
{% endhint %}

1、**创建您的组织**。从创建组织开始。要了解如何操作，请查看[这篇文章](../organizations/organizations.md#create-an-organization)。

{% hint style="info" %}
对于自托管 Bitwarden，请在 Bitwarden 云端创建一个组织，生成[许可证密钥](https://bitwarden.com/host/)，然后在您的服务器上使用该密钥[解锁组织](../self-hosting/licensing.md#organization-license)。
{% endhint %}

2、**入职管理用户**。创建好组织后，可以通过入职一些[管理用户](https://help.ppgg.in/admin-console/user-management/member-roles-and-permissions)来简化进一步的设置过程。重要的是，此时**不要开始最终用户入职**，因为还有几个步骤需要您为组织做好准备。[此处](https://help.ppgg.in/admin-console/user-management/user-management#onboard-users)了解如何邀请管理员。

3、**配置身份服务**。企业组织支持使用 SAML 2.0 或 OpenID Connect (OIDC) 的[单点登录](https://help.ppgg.in/admin-console/login-with-sso/about-login-with-sso) (SSO)。要配置单点登录，请在管理控制台中打开组织的**设置** → **单点登录**界面，[组织所有者和管理员](https://help.ppgg.in/admin-console/user-management/member-roles-and-permissions)都可以访问该界面。

4、**启用企业策略**。[企业策略](https://help.ppgg.in/admin-console/organization-basics/enterprise-policies)使组织能够为用户实施规则，例如要求使用两步登录。强烈建议在用户入职前配置策略。

## 第 3 步：导入数据到组织 <a href="#step-3-import-data-to-your-organization" id="step-3-import-data-to-your-organization"></a>

要将数据导入您的组织：

1、登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航至**设置** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/12fA17Iq9LdCXdhPsPYQyq/6fb380ff6165058fefe6fd311e038364/2024-12-03_15-42-21.png?_a=DAJCwlWIZAAB" %}
管理控制台导入
{% endembed %}

3、从下拉菜单中填写以下字段：

* **集合**：选择是否要将导入的内容移动到现有的集合中。在大多数情况下，您不会在 Bitwarden 中创建集合，因为导入会为您创建集合，所以请将此选项留空。
* [**文件格式**](../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择 **Lastpass (csv)**。

4、选择**选择文件**然后添加要导入的文件，或在输入框中复制并粘贴文件内容。

{% hint style="danger" %}
导入到 Bitwarden 无法检查要导入的文件中的项目是否与您的密码库中的项目重复。这意味着，如果某个项目已经存在密码库和要导入的文件中，则**导入多个文件将创建重复**的密码库项目。
{% endhint %}

5、选择**导入数据**触发导入。

目前，文件附件不包含在 Bitwarden 导入操作中，需要手动上传到您的密码库。更多信息，请参阅[文件附件](../your-vault/file-attachments.md)。

{% hint style="success" %}
您还应该建议员工从您现有的密码管理器中导出他们的个人数据，并准备将其导入 Bitwarden。在[此处](../import-export/)了解更多信息。
{% endhint %}

### 导入建议 <a href="#import-recommendations" id="import-recommendations"></a>

当导入数据到组织时，有两个选项：

1. 从您之前的密码管理器导入默认的文件格式。
2. 调整 Bitwarden 特定的 `.CSV` 用于导入。

我们建议将文件格式化为 Bitwarden `.CSV` 以获得最佳的效果，或者对于高级用户，将文件格式化为 Bitwarden `.JSON` 文件。有关 Bitwarden 特定的导入文件的说明，请参阅[此导入指南](../import-export/condition-a-bitwarden-.csv-or-.json.md)。

## 第 4 步：入职用户 <a href="#step-4-onboard-users" id="step-4-onboard-users"></a>

Bitwarden 支持通过网页密码库手动入职和通过 SCIM 集成或从现有目录服务同步自动入职：

### 手动入职 <a href="#manual-onboarding" id="manual-onboarding"></a>

为确保您组织的安全，Bitwarden 采用了三步流程入职新成员：[邀请](../organizations/user-management.md#invite) → [接受](../organizations/user-management.md#accept) → [确认](../organizations/user-management.md#confirm)。了解[如何邀请新用户](../organizations/user-management.md#onboard-users)。

### 自动入职 <a href="#automated-onboarding" id="automated-onboarding"></a>

通过与 [Azure AD](../scim/azure-ad-scim-integration.md)、[Okta](../scim/okta-scim-integration.md)、[OneLogin](../scim/onelogin-scim-integration.md) 和 [JumpCloud](../scim/jumpcloud-scim-integration.md) 的 SCIM 集成，或使用 [Directory Connector](../directory-connector/about-directory-connector.md)（一个可在[桌面 App](../directory-connector/directory-connector-desktop-app.md) 和 [CLI](../directory-connector/directory-connector-cli.md) 工具中使用的独立应用程序），可实现自动用户入职，从而同步现有目录服务中的用户和群组。

无论使用哪种方式，用户都会被自动邀请加入组织，并可使用 [Bitwarden CLI](../password-manager/developer-tools/password-manager-cli.md#confirm) 工具手动或自动确认。

## 第 5 步：配置集合和项目的访问权限 <a href="#step-5-configure-access-to-collections-and-items" id="step-5-configure-access-to-collections-and-items"></a>

通过集合、群组、群组级别或用户级别权限配置访问权限，与最终用户共享密码库项目：

### 集合 <a href="#collections" id="collections"></a>

Bitwarden 使团队和组织能够以一种可扩展的方式轻松、安全地共享敏感数据。这是通过将共享的机密、项目、登录等划分为**集合**来实现的。

集合以多种方式来组织安全项目，包括但不限于：业务功能、群组分配、应用程序访问级别，甚至安全协议。集合与共享文件夹的功能相同，允许用户群组之间的共享和访问控制的一致性。

来自其他密码管理器的共享文件夹可以通过使用[这里](https://bitwarden.com/help/files/bitwarden_export_org.csv)的组织导入模板并将共享文件夹的名称放在 `Collections` 列中，从而将其作为集合导入到 Bitwarden 中。例如：

导出：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/27vlwgg9iWZ1glGPoRDfxN/0d3500975e0f4a9215b1f44d6d59f14c/lp-export.png?_a=DAJCwlWIZAAB" %}
迁移导出示例
{% endembed %}

导入：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6urMdzaW8jsmnGIXB4L1o2/681eccdc161cae3d944c4b2a658e814b/bw-import.png?_a=DAJCwlWIZAAB" %}
迁移导入示例
{% endembed %}

集合既可以与群组共享，也可以与单个用户共享。限制可访问集合的个人用户数量将提高管理员的管理效率。[ 此处了解更多](../admin-console/organization-basics/about-collections.md)。

### 群组 <a href="#groups" id="groups"></a>

使用群组进行共享是提供凭证和安全访问的最有效方式。群组和用户一样，可以使用 SCIM 或目录连接器同步到组织中。

### 权限 <a href="#permissions" id="permissions"></a>

可以在群组或用户级别分配 Bitwarden 集合的权限。这意味着每一个群组或用户可以配置为对同一个集合拥有权限。集合的权限包括**只读**和**隐藏密码**选项。

Bitwarden 使用权限结合来确定用户和集合项目的最终访问权限（[了解更多](../admin-console/user-management/member-roles-and-permissions.md#permissions)）。例如：

* 用户 A 是「Tier 1 Support」群组的成员，该群组可以访问「Support」集合，并拥有查看权限。
* 用户 A 也是「Support Management」群组的成员，该群组可以访问「Support」集合，并拥有编辑权限。
* 这种情况下，用户 A 将可以编辑该集合。

## 迁移支持 <a href="#migration-support" id="migration-support"></a>

Bitwarden 客户成功团队 24/7 全天候为企业和团队组织提供优先支持。如果您需要帮助或有疑问，请随时[联系我们](https://bitwarden.com/contact/)。

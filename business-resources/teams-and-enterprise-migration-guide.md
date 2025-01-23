# 团队和企业迁移指南

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/teams-enterprise-migration-guide/)
{% endhint %}

使用 Bitwarden 安全迁移您的组织，这既简单又安全。简单地遵循本指南中的步骤，以从您现有的密码管理器中迁移数据和用户：

1. [导出数据](teams-and-enterprise-migration-guide.md#step-1-export-your-data)
2. [创建和配置 Bitwarden 组织](teams-and-enterprise-migration-guide.md#step-2-setup-your-bitwarden-organization)
3. [导入数据到 Bitwarden](teams-and-enterprise-migration-guide.md#step-3-import-data-to-your-organization)
4. [入职用户](teams-and-enterprise-migration-guide.md#step-4-onboard-users-to-the-organization)
5. [配置对集合和密码库项目的访问权限](teams-and-enterprise-migration-guide.md#step-5-configure-access-to-collections-and-items)

{% hint style="success" %}
如果您在迁移期间需要协助，我们的[客户成功团队将为您提供帮助](../admin-console/more/lastpass-enterprise-migration-guide.md#migration-support)！
{% endhint %}

## 适用范围 <a href="#scope" id="scope"></a>

本文档描述了将安全数据从您当前的密码管理器迁移到 Bitwarden [团队或企业组织](../organizations/organizations.md)的最佳实践，基于简单和可扩展的方法构建安全基础设施。

密码管理对于组织安全和运营效率至关重要。这里提供有关执行迁移和配置的最佳方法的见解，旨在最大程度地减少交换企业工具时经常需要的试错方法。

本文档中的步骤**按推荐的顺序列出**，以便于用户轻松使用和顺利入门。

## 第 1 步：导出数据 <a href="#step-1-export-your-data" id="step-1-export-your-data"></a>

从另一个密码管理器导出数据，对于每个解决方案，都是不相同的，并且在某些情况下可能有点棘手。请使用我们的[导入和导出指南](../import-export/)来获取帮助，例如，从 [Lastpass](../password-manager/import-and-export/import-guides/import-data-from-lastpass.md#export-from-lastpass) 或 [1Password](../password-manager/import-and-export/import-guides/import-data-from-1password.md#export-your-1-password-1-pif-logins) 导出。

收集完整的数据导出可能需要将共享文件夹或项目分配给单个用户进行导出，或者在具有适当权限的用户之间执行多个导出。此外，导出的数据可能包含个人数据以及共享/组织数据，所以在导入 Bitwarden 之前，请确保从导出文件中移除个人项目。

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

## 第 2 步：设置 Bitwarden 组织 <a href="#step-2-setup-your-bitwarden-organization" id="step-2-setup-your-bitwarden-organization"></a>

Bitwarden 组织将用户和密码库项目联系在一起，以[安全地共享](../organizations/sharing.md)登录、笔记、卡支付卡身份信息。

{% hint style="success" %}
首先创建您的组织并[将数据直接导入其中](../import-export/import-data-to-an-organization.md)很重要，而不是将数据导入到个人帐户，然后再[将项目移动到组织](../organizations/sharing.md)。
{% endhint %}

1、**创建您的组织**。首先创建您的组织。要了解如何操作，请查看[这篇文章](../organizations/organizations.md#create-an-organization)。

{% hint style="info" %}
对于自托管 Bitwarden，请在 Bitwarden 云上创建一个组织，生成[许可证密钥](https://bitwarden.com/host/)，然后在您的服务器上使用该密钥[解锁组织](../self-hosting/licensing-for-paid-features.md#organization-license)。
{% endhint %}

2、**入职管理员用户**。创建您的组织后，可以通过入职一些[管理员用户](../admin-console/user-management/member-roles-and-permissions.md)来简化进一步的设置过程。此时**不要开始最终用户的入职**，这一点很重要，因为还有一些步骤来准备您的组织。在[此处](../organizations/user-management.md#onboard-users)了解如何邀请管理员。

3、**配置身份服务**。Bitwarden 企业组织支持使用 SAML 2.0 或 OpenID Connect（OIDC）的[单点登录（SSO）](../login-with-sso/about-login-with-sso.md)。要配置 SSO，请打开组织的**管理** → **单点登录**界面，[组织所有者和管理员](../admin-console/user-management/member-roles-and-permissions.md)可以从网页密码库访问。

4、**启用企业策略**。[企业策略](../organizations/enterprise-policies.md)使企业组织能够为用户实施角色，例如要求使用两步登录。强烈建议您在入职用户之前配置策略。

## 第 3 步：导入数据到组织 <a href="#step-3-import-data-to-your-organization" id="step-3-import-data-to-your-organization"></a>

要导入数据到您的组织：

1、打开您的组织并导航到**工具**选项卡：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3e6CTOgKkpGUwAsfYuUyn0/408b8cdcbba92c61ed96d5ff4bbc81b0/org-tools.png?fm=webp&h=459&q=50&w=819" %}
组织工具
{% endembed %}

2、从左侧工具菜单中选择**导入数据**。&#x20;

3、 从格式下拉列表中，选择一种**文件格式**（请参阅下面的[导入建议](teams-and-enterprise-migration-guide.md#import-recommendations)）。

4、选择**选择文件**按钮并添加要导入的文件。

{% hint style="warning" %}
导入到 Bitwarden 无法检查要导入的文件中的项目是否与您的密码库中的项目重复。这意味着，如果某个项目已经存在密码库和要导入的文件中，则**导入多个文件将创建重复**的密码库项目。
{% endhint %}

5、选择**导入数据**按钮以完成导入。

目前，文件附件不包含在 Bitwarden 导入操作中，需要手动上传到您的密码库。有关更多信息，请参阅[文件附件](../your-vault/file-attachments.md)。

{% hint style="success" %}
您还应该建议员工从您现有的密码管理器中导出他们的个人数据，并准备将其导入 Bitwarden。在[此处](../import-export/)了解更多信息。
{% endhint %}

### 导入建议 <a href="#import-recommendations" id="import-recommendations"></a>

当导入数据到组织时，有两个选项：

1. 从您之前的密码管理器导入默认的文件格式。
2. 使用 Bitwarden 特定的 `.CSV` 用于导入。

我们建议将文件格式化为 Bitwarden `.CSV` 以获得最佳的效果，或着对于高级用户，将文件格式化为 Bitwarden `.JSON` 文件。有关 Bitwarden 特定的导入文件的说明，请参阅[此导入指南](../import-export/condition-a-bitwarden-.csv-or-.json.md)。有关更多导入文档，请参阅[这些文章](../import-export/)。

## 第 4 步：将用户加入组织 <a href="#step-4-onboard-users-to-the-organization" id="step-4-onboard-users-to-the-organization"></a>

Bitwarden 支持通过网页密码库进行手动入职，以及通过同步到您现有的目录服务进行自动入职：

### 手动入职 <a href="#manual-onboarding" id="manual-onboarding"></a>

为了确保您组织的安全，Bitwarden 应用了一个 3 步流程来入职新成员，[邀请](../organizations/user-management.md#invite) → [接受](../organizations/user-management.md#accept) → [确认](../organizations/user-management.md#confirm)。在[此处](../organizations/user-management.md#onboard-users)了解如何邀请新用户。

### 自动入职 <a href="#automated-onboarding" id="automated-onboarding"></a>

可通过 Bitwarden [目录连接器](../directory-connector/about-directory-connector.md)实现自动化用户入职，Bitwarden 目录连接器是一个用于同步现有目录服务中的用户和群组的独立应用程序，可以在[桌面应用程序](../directory-connector/directory-connector-desktop-app.md)和 [CLI](../directory-connector/directory-connector-cli.md) 中使用。

用户会被自动邀请加入组织，并且可以使用 [Bitwarden CLI 工具](../password-manager/developer-tools/password-manager-cli.md#confirm)手动或自动确认。

* 在[这里](../directory-connector/about-directory-connector.md)了解同步是如何工作的
* 在[这里](../directory-connector/sync-options-and-filters.md)了解如何为目录连接器配置用户和群组筛选器
* 在[这里](../directory-connector/)了解更多目录连接器的文档

## 第 5 步：配置集合和项目的访问权限 <a href="#step-5-configure-access-to-collections-and-items" id="step-5-configure-access-to-collections-and-items"></a>

通过集合、群组和群组级别或用户级别权限配置访问权限，与您的最终用户共享密码库项目：

### 集合 <a href="#collections" id="collections"></a>

Bitwarden 使团队和组织能够以一种可扩展的方式轻松、安全地共享敏感数据。这是通过将共享的密码、项目、登录等划分为**集合**来实现的。

集合以多种方式来组织安全项目，包括但不限于：业务功能、群组分配、应用程序访问级别，甚至安全协议。集合与共享文件夹的功能相同，允许用户群组之间的共享和访问控制的一致性。

来自其他密码管理器的共享文件夹可以通过使用[这里](https://bitwarden.com/help/files/bitwarden_export_org.csv)的组织导入模板并将共享文件夹的名称放在 `Collections` 栏中，从而将其作为集合导入到 Bitwarden 中。

导出示例：

![备注：共享文件夹位于群组栏中](https://raw.githubusercontent.com/bitwarden/help/master/images/migration/lp-export.png)

Bitwarden 组织导入示例：

![备注：共享文件夹现在位于 Collections 栏中](https://raw.githubusercontent.com/bitwarden/help/master/images/migration/bw-import.png)

集合可以与群组以及个人用户共享。限制可以访问集合的个人用户数量将使管理员的管理更加有效。在[此处](../organizations/collections.md)了解更多信息。

### 群组 <a href="#groups" id="groups"></a>

利用群组进行共享是提供凭证和安全访问的最有效方式。理想情况下，群组是从 LDAP 服务中镜像出来的，但是 Bitwarden 支持通过目录连接器应用程序自动同步群组，也支持手动创建临时群组。

作为部署准备工作的一部分，可以在开始同步用户之前，**只**同步 LDAP 目录中的群组，这样，在用户开始访问 Bitwarden 之前，就可以将集合分配给群组。在[此处](../directory-connector/sync-options-and-filters.md)了解有关使用目录连接器同步群组的更多信息。

### 权限 <a href="#permissions" id="permissions"></a>

可以在群组或用户级别分配 Bitwarden 集合的权限。这意味着每一个群组或用户可以配置为对同一个集合拥有权限。集合的权限包括**只读**和**隐藏密码**选项。

Bitwarden 使用权限联合来确定一个用户和一个集合项目的最终访问权限。在[此处](../admin-console/user-management/member-roles-and-permissions.md#access-control)了解更多信息。

**示例：**

* 用户 A 是群组 Tier 1 Support 的成员，此群组可以访问集合 Support，具有只读权限。
* 用户 A 也是群组 Support Management  的成员，此群组可以访问集合 Support，具有读写权限。
* 这种情况下，用户 A 将可以读写此集合。

## 迁移支持 <a href="#migration-support" id="migration-support"></a>

Bitwarden 客户成功团队提供 24/7 全天候服务，为企业和团队组织提供优先支持。如果您需要帮助或有任何疑问，请随时[联系我们](https://bitwarden.com/contact)。

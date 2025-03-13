# LastPass 企业版迁移指南

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/lastpass-enterprise-migration-guide/)、[GitHub 地址](https://github.com/bitwarden/help/blob/master/_articles/importing/lastpass-enterprise-migration-guide.md)
{% endhint %}

## Bitwarden 独家内容：使迁移变得简单 <a href="#bitwarden-exclusive-content-making-migration-easy" id="bitwarden-exclusive-content-making-migration-easy"></a>

使用 Bitwarden 对您的组织进行安全迁移既直接又安全。请按照本指南中的步骤从 LastPass 迁移数据和用户：

1. [创建和配置 Bitwarden 组织](lastpass-enterprise-migration-guide.md#creating-an-organization)。
2. [导入数据到 Bitwarden](lastpass-enterprise-migration-guide.md#importing-data)。
3. [入职用户](lastpass-enterprise-migration-guide.md#onboarding-users)
4. 配置对集合和密码库项目的访问权限。

{% hint style="success" %}
如果您在迁移期间需要协助，我们的[客户成功团队将随时为您提供帮助](lastpass-enterprise-migration-guide.md#migration-support)！
{% endhint %}

## 适用范围 <a href="#scope" id="scope"></a>

本文档将描述将安全数据从 LastPass 实例迁移到 Bitwarden 团队或企业组织的最佳实践，基于简单和可扩展的方法构建安全基础设施。

密码管理对于组织安全和运营效率至关重要。这里提供有关执行迁移和配置的最佳方法的见解，旨在最大程度地减少交换企业工具时经常需要的试错方法。

以下步骤按推荐的顺序列出，以便于用户轻松使用和顺利上岗。

## 导出数据 <a href="#exporting-data" id="exporting-data"></a>

LastPass 数据可以从基于网络的密码库中导出，也可以从 LastPass 客户端导出。为了便于操作，建议使用 CSV 导出格式。

LastPass 在[这里](https://support.logmeininc.com/lastpass/help/how-do-i-nbsp-export-stored-data-from-lastpass-using-a-generic-csv-file)提供了逐步的说明。

### 有关导出数据的重要说明 <a href="#important-notes-on-exported-data" id="important-notes-on-exported-data"></a>

导入到 Bitwarden 的数据被定义为以下四种类型：

* 登录（用户名、密码、2FA 密钥）
* 支付卡（信用卡、银行卡）
* 身份（名称、地址字段、个人信息）
* 安全笔记

Bitwarden 当前将项目字段的长度限制为 1,000 个字符，将安全笔记限制为 10,000 个字符。超出该标准的项目应将其另存为单独的文件（文本、密钥、pem、ssh 等），并作为附件添加到项目中。

* [更多关于项目](../../your-vault/vault-items.md)
* [将文件附件到项目](../../your-vault/file-attachments.md)

要在 LastPass 组织中收集数据的完整导出，可能需要将所有共享文件夹分配给一个用户，或执行多个导出操作（每个共享文件夹导出一次）。

从 LastPass 导出的数据将包含您的个人密码库以及已分配给导出用户的所有共享文件夹中的数据。在将数据导入 Bitwarden 组织之前，请确保移除所有个人密码库项目。

## 创建组织 <a href="#creating-an-organization" id="creating-an-organization"></a>

已共享或公司级别的数据存储在 Bitwarden 组织中。最佳的做法是先创建这个组织，然后直接导入，而不是将数据先导入个人账户，然后再与组织进行二次共享。

有关创建 Bitwarden 组织的更多信息，请访问[这篇文章](../../organizations/organizations.md)。

对于自托管实例，需要先在 Bitwarden 云实例上创建一个组织来生成其[许可证密钥](https://bitwarden.com/host/)，然后再继续[安装和配置 Bitwarden 服务器实例](../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md)。

{% hint style="info" %}
自托管适用于企业计划。
{% endhint %}

### 配置身份服务 <a href="#configuring-identity-services" id="configuring-identity-services"></a>

Bitwarden 企业计划支持使用 SAML 2.0 或 OpenID Connect（OIDC）的单点登录（SSO）。

每个 Bitwarden 组织可以配置一个 SSO 提供程序。组织的所​​有者和管理员可以通过网页密码库访问此配置。

有关 SSO 登录的配置、身份提供程序（IdP）的示例以及命名约定的更多详细信息，请访问[帮助文章](../../login-with-sso/about-login-with-sso.md)。

### 启用企业策略 <a href="#enabling-enterprise-policies" id="enabling-enterprise-policies"></a>

策略可在组织**的管理 → 策略**界面中找到（有关详细信息，请参阅[此处](../../organizations/enterprise-policies.md)）。

策略允许您控制组织内用户的操作。建议在入职用户之前配置这些策略。有关企业策略的完整列表和详细信息，请参阅[此处](../../organizations/enterprise-policies.md)的帮助文章。

## 导入数据 <a href="#importing-data" id="importing-data"></a>

将信息导入 Bitwarden，这可以在个人密码库中执行，也可以在组织密码库中执行。以下说明适用于组织导入。

有两种方法将数据导入组织中：使用 LastPass 默认的 CSV 导出文件；根据导出的数据创建专用于 Bitwarden 的 CSV。

对于大多数组织而言，最佳实践是将数据格式化为 Bitwarden CSV，对于高级用户，则将其格式化为 Bitwarden JSON 文件，以导入到您的组织密码库中。

有关调整 Bitwarden 特定导入文件的说明，请参阅[此处](../../import-export/condition-a-bitwarden-.csv-or-.json.md)的指南。

[此处](../../import-export/)提供了数据导入和导出，以及协助从其他来源导入的说明文档的集合。。

{% hint style="warning" %}
多次导入将在您的 Bitwarden 密码库中创建重复记录。
{% endhint %}

### 个人用户数据的导入 <a href="#individual-user-data-import" id="individual-user-data-import"></a>

Bitwarden 支持从其他密码管理平台导入各种格式的数据。个人用户可以自行将他们的数据导入到他们的 Bitwarden 密码库中，而不需要管理员的协助。

有关导入个人数据的更多信息，请在[这里](../../import-export/)查看我们的有用文章。

## 入职用户 <a href="#onboarding-users" id="onboarding-users"></a>

Bitwarden 支持手动和自动邀请和入职用户。最佳的做法是在配置和初始部署期间手动入职任何必要的管理员用户，确保所有的组织配置，包括企业策略、SSO 登录和目录连接器，在自动化用户邀请和入职过程之前做好准备。

### 手动入职 <a href="#manual-onboarding" id="manual-onboarding"></a>

手动入职是通过网页密码库来完成的。有关手动入职用户的更多信息可以在[这篇帮助文章](../../organizations/user-management.md)中找到。

### 自动入职 <a href="#automated-onboarding" id="automated-onboarding"></a>

利用 Bitwarden 目录连接器（一个具有[桌面应用程序](../../directory-connector/directory-connector-desktop-app.md)和 [CLI 工具](../../directory-connector/directory-connector-cli.md)的独立应用程序）将用户和群组信息同步到 Bitwarden 组织时，也可实现自动入职用户。这些用户会被自动邀请加入组织，并可使用 [Bitwarden CLI 工具](../../password-manager/developer-tools/password-manager-cli.md#confirm)手动或自动确认。

* 在[这里](../../directory-connector/about-directory-connector.md)了解更多关于同步是如何工作的
* 在[这里](../../directory-connector/sync-options-and-filters.md)了解如何为目录连接器配置用户和群组筛选器
* [这里](../../directory-connector/)是关于各种目录连接器的文档

## 共享集合和项目 <a href="#sharing-collections-and-items" id="sharing-collections-and-items"></a>

### 集合 <a href="#collections" id="collections"></a>

Bitwarden 使团队和组织能够以一种可扩展的方式轻松、安全地共享敏感数据。这是通过将共享的密码、项目、登录等划分为集合来实现的。

集合以多种方式来组织安全项目，包括但不限于：业务功能、群组分配、应用程序访问级别，甚至安全协议。集合与共享文件夹的功能相同，允许用户群组之间的共享和访问控制的一致性。

LastPass 的共享文件夹可以通过使用[这里](https://bitwarden.com/help/files/bitwarden_export_org.csv)的组织导入模板并将共享文件夹的名称放在集合栏中，从而将其作为集合导入到 Bitwarden 中。

LastPass 导出示例：

![共享文件夹位于群组栏中](https://raw.githubusercontent.com/bitwarden/help/master/images/migration/lp-export.png)

Bitwarden 组织导入示例：

![共享文件夹现在位于集合栏中](https://raw.githubusercontent.com/bitwarden/help/master/images/migration/bw-import.png)

集合可以与群组以及个人用户共享。限制可以访问集合的个人用户数量将使管理员的管理更加有效。

有关将集合分配给用户和群组的更多信息，请参阅[我们的帮助文章](../../organizations/collections.md)。

### 群组 <a href="#groups" id="groups"></a>

利用群组进行共享是提供凭证和安全访问的最有效方式。理想情况下，群组是从 LDAP 服务中镜像出来的，但是 Bitwarden 支持通过目录连接器应用程序自动同步群组，也支持手动创建临时群组。

作为部署准备工作的一部分，可以在开始同步用户之前，**只**同步LDAP目录中的群组，这样，在用户开始访问 Bitwarden 之前，就可以将集合分配给群组。

有关使用 Bitwarden 目录连接器筛选和同步用户的更多信息，请查看[这里](../../directory-connector/sync-options-and-filters.md)的文章。

### 权限 <a href="#permissions" id="permissions"></a>

Bitwarden 集合的权限是在将群组或用户分配到一个具体的集合时分配的。这意味着，同一个集合可以为每个群组或用户配置权限。

集合权限可以通过只读选项以及隐藏密码选项轻松配置。

只读可以防止用户向该集合中添加新的项目，也可以防止编辑或删除现有的项目。隐藏密码可以防止用户看到密码字段、TOTP 字段以及项目中被列为隐藏的任何自定义字段。这个权限最好用于能够在浏览器中自动填写的项目集合，因为当配置了这个权限时，凭证的复制和粘贴就会被禁用。

Bitwarden 使用一个权限联合来确定一个用户和一个集合项目的最终访问权限。

**示例：**

* 用户 A 是群组 Tier 1 Support 的成员，此群组可以访问集合 Support，具有只读权限。
* 用户 A 也是群组 Support Management  的成员，此群组可以访问集合 Support，具有读写权限。
* 这种情况下，用户 A 将可以读写此集合。

有关权限的更多信息，请查看[我们的帮助文章](../user-management/member-roles-and-permissions.md)。

## 迁移支持 <a href="#migration-support" id="migration-support"></a>

Bitwarden 客户成功团队 24/7 全天候为企业和团队组织提供优先支持。如果您需要帮助或有疑问，请随时通过以下网址与我们联系：[bitwarden.com/contact](https://bitwarden.com/contact)。

## 术语及等效参考 <a href="#terms-and-equivalent-references" id="terms-and-equivalent-references"></a>

### 组织 <a href="#organization" id="organization"></a>

* Bitwarden 组织是将给定的共享实体的所有数据关联起来的涵盖「对象」。单击[此处](../../organizations/organizations.md)以获取有关组织的更多信息。

### 个人密码库的文件夹 <a href="#folders-for-individual-vaults" id="folders-for-individual-vaults"></a>

* 在 Bitwarden 中，个人用户可以创建文件夹，并将项目分配到这些文件夹中，以帮助组织他们的密码库。文件夹的功能很像「标签」，因为都是通过参考将它们链接到您的项目，删除文件夹不会删除里面的数据。组织使用集合将需要与相同用户或用户群组共享的安全项目进行分组。
* 在 LastPass 中，文件夹在个人用户和企业之间的行为方式是一样的。

### 组织密码库的集合 <a href="#collections-for-organizational-vaults" id="collections-for-organizational-vaults"></a>

* Bitwarden 组织使用集合将需要与相同用户或用户群组共享的安全项目进行分组。
* 大多数情况下，导出的共享文件夹都会变成集合，不过，您可以使用多种方式来组织集合。

### 用户 <a href="#user" id="user"></a>

* 作为 Bitwarden 组织成员的任何用户。

### 群组 <a href="#group" id="group"></a>

* Bitwarden 和 LastPass 支持用户群组。当迁移到 Bitwarden 时，您可以利用 [BWDC](../../directory-connector/)（Bitwarden Directory Connector）将 LDAP 群组同步到您的 Bitwarden 组织中。

### 只读 <a href="#read-only" id="read-only"></a>

* 只读权限可以防止用户向集合中的项目添加新数据。用户可以查看/访问项目中的所有数据，但不能添加新项目或修改现有数据。此权限是在将用户或群组分配给集合时设置的。

### 隐藏密码 <a href="#hide-password" id="hide-password"></a>

* 隐藏密码权限可以防止用户看到集合内的项目的任何密码部分。

### 用户类型 <a href="#user-type" id="user-type"></a>

* Bitwarden 内的用户可以被授予某个「用户类型」。通过目录连接器入职的用户默认为「用户」（对应的还有「经理」、「管理员」等），他们只能访问直接分配给他们的项目，不具有重新配置共享或权限的权限。

### 密码库 <a href="#vault" id="vault"></a>

* 密码库是加密数据的存储区域。属于组织成员的 Bitwarden 用户拥有个人密码库和组织密码库，并使用单独的密钥进行加密。

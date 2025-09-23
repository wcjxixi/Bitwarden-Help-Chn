# Bitwarden 入门：管理员

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/get-started-administrator/)
{% endhint %}

我们很高兴您正在考虑使用 Bitwarden 来满足您业务的安全凭据共享需求。让我们一起走进成功合作的第一步：

{% tabs %}
{% tab title="企业版" %}
{% hint style="success" %}
文档中的前几个步骤假设您要创建一个组织。如果您要加入现有组织，请跳到步骤**或加入现有组织**。
{% endhint %}

## 注册 Bitwarden <a href="#sign-up-for-bitwarden" id="sign-up-for-bitwarden"></a>

Bitwarden 提供随您使用的无设备数量限制或登录数量限制的免费账户。[现在就开始吧](https://bitwarden.com/go/start-free/)！

### 主密码 <a href="#your-master-password" id="your-master-password"></a>

注册时，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2pST1WXY0Xk7GQ4GpwzELn/59b88f130a5d65b51c75bbe3a742a702/2024-12-02_10-20-39.png?_a=DAJCwlWIZAAB" %}
设置主密码
{% endembed %}

## 创建组织 <a href="#create-an-organization" id="create-an-organization"></a>

通过在 Bitwarden 网页 App 中选择**新增组织**按钮，现在就创建您的组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3eSqWiTIuPSFxXdo5AAjT9/248b0fa7bb381add0d71682acd244a63/2024-12-03_13-57-58.png?_a=DAJCwlWIZAAB" %}
新增组织
{% endembed %}

### 或加入现有组织 <a href="#or-join-an-existing-organization" id="or-join-an-existing-organization"></a>

如果您的组织已经创建，请向您公司的 IT 团队或您的经理咨询有关如何加入 Bitwarden。有些组织会向您的工作收件箱发送电子邮件邀请，有些组织则允许您使用单点登录 (SSO) 账户登录即可加入。

## 了解管理控制台 <a href="#get-to-know-the-admin-console" id="get-to-know-the-admin-console"></a>

创建后，您将进入管理控制台，这是所有共享和组织管理的中心枢纽。作为组织所有者，您可以查看**密码库**项目和[集合](../admin-console/organizations-overview.md#collections)、管理**成员**、运行**报告**、更改**计费设置**以及配置其他组织**设置**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?_a=DAJCwlWIZAAB" %}
免费组织管理控制台
{% endembed %}

## 管理密码库项目和集合 <a href="#managing-vault-items-and-collections" id="managing-vault-items-and-collections"></a>

作为所有者或管理员，您可能负责管理公司或团队对**密码库项目**（如共享凭据）的访问权限。您可以直接从网页 App 中创建项目，并将其分配到集合，以便与团队共享：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1u6EPNgAlCnvC9DcmUIosQ/327c0c24e09dce687540499a8eaa5aac/2024-12-02_15-47-21.png?_a=DAJCwlWIZAAB" %}
批量分配到集合
{% endembed %}

说到[集合](../admin-console/manage-shared-items/collections/about-collections.md)，它们是一种重要的结构，用于将相关的登录、备注、支付卡和身份组合在一起，以便与组织安全地共享：

* 组织可以定义对集合的访问权限，允许用户或群组只能访问他们需要的项目。
* 存储在组织集合中的项目不属于任何个人用户，而是属于组织。
* 组织拥有的项目**必须**至少包含在一个集合中。

{% hint style="success" %}
数据也可以直接导入到您的组织中！[了解如何操作](../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md#import-to-your-organization)。
{% endhint %}

## 管理成员和群组 <a href="#managing-members-and-groups" id="managing-members-and-groups"></a>

作为所有者或管理员，您可能要负责管理团队成员或更广泛的公司成员。成员可以添加到您的组织中：

* 直接从管理控制台的**成员**页面添加（[了解更多](../admin-console/manage-members/user-management.md#invite)）
* 使用 SCIM 将 Bitwarden 与您的 IdP 集成（[了解更多](../admin-console/manage-members/scim/about-scim.md)）
* 使用 Directory Connector 将 Bitwarden 与您的目录服务集成（[了解更多](../admin-console/manage-members/directory-connector/about-directory-connector.md)）

成员可以直接分配给集合，以管理他们可以访问的密码库数据，但[群组](../admin-console/manage-members/groups.md)也可以。群组将单个成员联系在一起，提供了一种可扩展的方式来分配对特定集合的访问权限：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/FefJG4qBRiWkTzsxBKfm6/53093b4dd48e534cdde9f3e249d3c382/2024-12-03_14-22-27.png?_a=DAJCwlWIZAAB" %}
新增群组
{% endembed %}

## 策略、集成等 <a href="#policies-integrations-and-more" id="policies-integrations-and-more"></a>

企业版 Bitwarden 组织提供了强大的工具，用于提高在线安全性并与现有工作流程和工具集成。作为组织的管理员，您可能需要管理的其他事项包括：

* 设置[策略](../admin-console/manage-shared-items/enterprise-policies.md)以执行用户安全规则，例如强制使用两步登录。
* 审计[组织成员拥有哪些凭据的访问权限](../your-vault/vault-health-reports.md#member-access)。
* 将 Bitwarden 与现有的 [SSO](../login-with-sso/about-login-with-sso.md) 工作流程整合。
* [验证您的组织的域名](../admin-console/login-with-sso/claimed-domains.md)，实现无缝登录体验。
* 为成员[设置](../admin-console/login-with-sso/trusted-devices/setup-sso-with-trusted-devices.md)或[批准](../admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md)设备信任要求的系统。
* 将 Bitwarden 与现有的 SIEM 工具（如 [Microsoft Sentinel](../admin-console/reporting/configure-siem/microsoft-sentinel-siem.md)）集成。
{% endtab %}

{% tab title="团队版" %}
{% hint style="success" %}
文档中的前几个步骤假设您要创建一个组织。如果您要加入现有组织，请跳到步骤**或加入现有组织**。
{% endhint %}

## 注册 Bitwarden <a href="#sign-up-for-bitwarden" id="sign-up-for-bitwarden"></a>

Bitwarden 提供随您使用的无设备数量限制或登录数量限制的免费账户。[现在就开始吧](https://bitwarden.com/go/start-free/)！

### 主密码 <a href="#your-master-password" id="your-master-password"></a>

注册时，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2pST1WXY0Xk7GQ4GpwzELn/59b88f130a5d65b51c75bbe3a742a702/2024-12-02_10-20-39.png?_a=DAJCwlWIZAAB" %}
设置主密码
{% endembed %}

## 创建组织 <a href="#create-an-organization" id="create-an-organization"></a>

通过在 Bitwarden 网页 App 中选择**新增组织**按钮，现在就创建您的组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3eSqWiTIuPSFxXdo5AAjT9/248b0fa7bb381add0d71682acd244a63/2024-12-03_13-57-58.png?_a=DAJCwlWIZAAB" %}
新增组织
{% endembed %}

### 或加入现有组织 <a href="#or-join-an-existing-organization" id="or-join-an-existing-organization"></a>

如果您的组织已经创建，请请求您组织的其他成员向您发送邀请。

## 了解管理控制台 <a href="#get-to-know-the-admin-console" id="get-to-know-the-admin-console"></a>

创建后，您将进入管理控制台，这是所有共享和组织管理的中心枢纽。作为组织所有者，您可以查看**密码库**项目和[集合](../admin-console/organizations-overview.md#collections)、管理**成员**、运行**报告**、更改**计费设置**以及配置其他组织**设置**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?_a=DAJCwlWIZAAB" %}
免费组织管理控制台
{% endembed %}

## 管理密码库项目和集合 <a href="#managing-vault-items-and-collections" id="managing-vault-items-and-collections"></a>

作为所有者或管理员，您可能负责为您的公司或团队管理**密码库项目**（如共享凭据）的访问权限。您可以直接从网页 App 中创建项目，并将其分配到集合，以便与团队共享：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1u6EPNgAlCnvC9DcmUIosQ/327c0c24e09dce687540499a8eaa5aac/2024-12-02_15-47-21.png?_a=DAJCwlWIZAAB" %}
批量分配到集合
{% endembed %}

说到[集合](../admin-console/manage-shared-items/collections/about-collections.md)，它们是一种重要的结构，用于将相关的登录、备注、支付卡和身份组合在一起，以便与组织安全地共享：

* 组织可以定义对集合的访问权限，允许用户或群组只能访问他们需要的项目。
* 存储在组织集合中的项目不属于任何个人用户，而是属于组织。
* 组织拥有的项目**必须**至少包含在一个集合中。

{% hint style="success" %}
数据也可以直接导入到您的组织中！[了解如何操作](../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md#import-to-your-organization)。
{% endhint %}

## 管理成员和群组 <a href="#managing-members-and-groups" id="managing-members-and-groups"></a>

作为所有者或管理员，您可能要负责管理团队成员或更广泛的公司成员。成员可以添加到您的组织中：

* 直接从管理控制台的**成员**页面添加（[了解更多](../admin-console/manage-members/user-management.md#invite)）
* 使用 SCIM 将 Bitwarden 与您的 IdP 集成（[了解更多](../admin-console/manage-members/scim/about-scim.md)）
* 使用 Directory Connector 将 Bitwarden 与您的目录服务集成（[了解更多](../admin-console/manage-members/directory-connector/about-directory-connector.md)）

成员可以直接分配给集合，以管理他们可以访问的密码库数据，但[群组](../admin-console/manage-members/groups.md)也可以。群组将单个成员联系在一起，提供了一种可扩展的方式来分配对特定集合的访问权限：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/FefJG4qBRiWkTzsxBKfm6/53093b4dd48e534cdde9f3e249d3c382/2024-12-03_14-22-27.png?_a=DAJCwlWIZAAB" %}
新增群组
{% endembed %}

## 策略、集成等 <a href="#policies-integrations-and-more" id="policies-integrations-and-more"></a>

团队版 Bitwarden 组织提供了强大的工具，用于提高在线安全性并与现有工作流程和工具集成。作为组织的管理员，您可能需要管理的其他事项包括：

* 审计[组织成员拥有哪些凭据的访问权限](../your-vault/vault-health-reports.md#member-access)。
* 将 Bitwarden 与现有的 SIEM 工具（如 [Microsoft Sentinel](../admin-console/reporting/configure-siem/microsoft-sentinel-siem.md)）集成。
{% endtab %}

{% tab title="家庭版" %}
{% hint style="success" %}
文档中的前几个步骤假设您要创建一个组织。如果您要加入现有组织，请跳到步骤**或加入现有组织**。
{% endhint %}

## 注册 Bitwarden <a href="#sign-up-for-bitwarden" id="sign-up-for-bitwarden"></a>

Bitwarden 提供随您使用的无设备数量限制或登录数量限制的免费账户。[现在就开始吧](https://bitwarden.com/go/start-free/)！

### 主密码 <a href="#your-master-password" id="your-master-password"></a>

注册时，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2pST1WXY0Xk7GQ4GpwzELn/59b88f130a5d65b51c75bbe3a742a702/2024-12-02_10-20-39.png?_a=DAJCwlWIZAAB" %}
设置主密码
{% endembed %}

## 创建组织 <a href="#create-an-organization" id="create-an-organization"></a>

通过在 Bitwarden 网页 App 中选择**新增组织**按钮，现在就创建您的组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3eSqWiTIuPSFxXdo5AAjT9/248b0fa7bb381add0d71682acd244a63/2024-12-03_13-57-58.png?_a=DAJCwlWIZAAB" %}
新增组织
{% endembed %}

### 或加入现有组织 <a href="#or-join-an-existing-organization" id="or-join-an-existing-organization"></a>

如果您的组织已经创建，请请求您组织的其他成员向您发送邀请。

## 了解管理控制台 <a href="#get-to-know-the-admin-console" id="get-to-know-the-admin-console"></a>

创建后，您将进入管理控制台，这是所有共享和组织管理的中心枢纽。作为组织所有者，您可以查看**密码库**项目和[集合](../admin-console/organizations-overview.md#collections)、管理**成员**、运行**报告**、更改**计费设置**以及配置其他组织**设置**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?_a=DAJCwlWIZAAB" %}
免费组织管理控制台
{% endembed %}

## 管理密码库项目和集合 <a href="#managing-vault-items-and-collections" id="managing-vault-items-and-collections"></a>

作为所有者或管理员，您可能负责为您的家庭管理**密码库项目**（如共享凭据）的访问权限。您可以直接从网页 App 中创建项目，并将其分配到集合，以便与家庭共享：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1u6EPNgAlCnvC9DcmUIosQ/327c0c24e09dce687540499a8eaa5aac/2024-12-02_15-47-21.png?_a=DAJCwlWIZAAB" %}
批量分配到集合
{% endembed %}

说到[集合](../admin-console/manage-shared-items/collections/about-collections.md)，它们是一种重要的结构，用于将相关的登录、备注、支付卡和身份组合在一起，以便与组织安全地共享：

* 组织可以定义对集合的访问权限，允许用户或群组只能访问他们需要的项目。
* 存储在组织集合中的项目不属于任何个人用户，而是属于组织。
* 组织拥有的项目**必须**至少包含在一个集合中。

{% hint style="success" %}
数据也可以直接导入到您的组织中！[了解如何操作](../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md#import-to-your-organization)。
{% endhint %}

## 管理成员和群组 <a href="#managing-members-and-groups" id="managing-members-and-groups"></a>

作为所有者或管理员，您可能需要更广泛地管理家庭成员。成员可以直接从管理控制台的**成员**页面添加到您的组织中（[了解更多](../admin-console/manage-members/user-management.md#invite)）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7AJjR4oqEnCH3A89YYoWpH/0d8004ac55a7ce2dfb3525be56885e66/2024-12-03_14-02-20.png?_a=DAJCwlWIZAAB" %}
邀请成员到组织
{% endembed %}

## 确保家庭安全 <a href="#help-your-family-be-safe" id="help-your-family-be-safe"></a>

既然您已经设置好通过 Bitwarden 与家人安全地共享数据，那么请考虑一些其他方式来确保您所爱的人的上网安全：

* 帮助家人设置[两步登录](../account/two-step-login/setup-guides/two-step-login-methods.md)，以保护他们的 Bitwarden 账户。
* 帮助家人设置[紧急访问](../account/log-in-and-unlock/more-log-in-options/emergency-access.md)，以便在紧急情况下访问重要数据。
{% endtab %}

{% tab title="免费版" %}
{% hint style="success" %}
文档中的前几个步骤假设您要创建一个组织。如果您要加入现有组织，请跳到步骤**或加入现有组织**。
{% endhint %}

## 注册 Bitwarden <a href="#sign-up-for-bitwarden" id="sign-up-for-bitwarden"></a>

Bitwarden 提供随您使用的无设备数量限制或登录数量限制的免费账户。[现在就开始吧](https://bitwarden.com/go/start-free/)！

### 主密码 <a href="#your-master-password" id="your-master-password"></a>

注册时，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2pST1WXY0Xk7GQ4GpwzELn/59b88f130a5d65b51c75bbe3a742a702/2024-12-02_10-20-39.png?_a=DAJCwlWIZAAB" %}
设置主密码
{% endembed %}

## 创建组织 <a href="#create-an-organization" id="create-an-organization"></a>

通过在 Bitwarden 网页 App 中选择**新增组织**按钮，现在就创建您的组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3eSqWiTIuPSFxXdo5AAjT9/248b0fa7bb381add0d71682acd244a63/2024-12-03_13-57-58.png?_a=DAJCwlWIZAAB" %}
新增组织
{% endembed %}

### 或加入现有组织 <a href="#or-join-an-existing-organization" id="or-join-an-existing-organization"></a>

如果您的组织已经创建，请请求您组织的其他成员向您发送邀请。

## 了解管理控制台 <a href="#get-to-know-the-admin-console" id="get-to-know-the-admin-console"></a>

创建后，您将进入管理控制台，这是所有共享和组织管理的中心枢纽。作为组织所有者，您可以查看**密码库**项目和[集合](../admin-console/organizations-overview.md#collections)、管理**成员**、运行**报告**、更改**计费设置**以及配置其他组织**设置**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?_a=DAJCwlWIZAAB" %}
免费组织管理控制台
{% endembed %}

## 管理密码库项目和集合 <a href="#managing-vault-items-and-collections" id="managing-vault-items-and-collections"></a>

作为所有者或管理员，您可能负责为您的组织管理**密码库项目**（如共享凭据）的访问权限。您可以直接从网页 App 中创建项目，并将其分配到集合，以便与组织共享：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1u6EPNgAlCnvC9DcmUIosQ/327c0c24e09dce687540499a8eaa5aac/2024-12-02_15-47-21.png?_a=DAJCwlWIZAAB" %}
批量分配到集合
{% endembed %}

说到[集合](../admin-console/manage-shared-items/collections/about-collections.md)，它们是一种重要的结构，用于将相关的登录、备注、支付卡和身份组合在一起，以便与组织安全地共享：

* 组织可以定义对集合的访问权限，允许用户或群组只能访问他们需要的项目。
* 存储在组织集合中的项目不属于任何个人用户，而是属于组织。
* 组织拥有的项目**必须**至少包含在一个集合中。
* 作为免费组织，您最多可以拥有 2 个集合。

{% hint style="success" %}
数据也可以直接导入到您的组织中！[了解如何操作](../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md#import-to-your-organization)。
{% endhint %}

## 管理成员和群组 <a href="#managing-members-and-groups" id="managing-members-and-groups"></a>

作为所有者或管理员，您将负责直接从管理控制台的**成员**页面邀请其他成员加入您的组织（[了解更多](../admin-console/manage-members/user-management.md#invite)）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7AJjR4oqEnCH3A89YYoWpH/0d8004ac55a7ce2dfb3525be56885e66/2024-12-03_14-02-20.png?_a=DAJCwlWIZAAB" %}
邀请成员到组织
{% endembed %}
{% endtab %}
{% endtabs %}

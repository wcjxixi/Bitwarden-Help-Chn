# 团队管理员

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/courses/password-manager-teams-admin/)
{% endhint %}

了解如何设置和管理您的 Bitwarden 团队组织、邀请团队成员、使用集合控制访问权限，并确保团队凭据的安全和有序。

{% hint style="success" %}
文档的前几个步骤假设您要创建一个组织。如果您要加入现有组织，请跳转至**或加入现有组织**章节。
{% endhint %}

## 演示 <a href="#demo" id="demo"></a>

<details>

<summary>观看演示</summary>

{% hint style="info" %}
请注意，某些功能要求企业版方案。如需了解更多信息，请参阅[企业版功能和方案比较](https://bitwarden.com/pricing/business/)。
{% endhint %}

{% embed url="https://vimeo.com/734127077?fl=pl&fe=cm" %}

[此处](../../../../docs/plans-and-pricing/password-manager/about-bitwarden-plans.md)了解更多有关可用的 Bitwarden 方案的信息。

* **00:07**：介绍和功能
* **00:35**：加密与安全
* **02:22**：托管和管理
* **04:11**：数据组织
* **10:28**：管理和安全

</details>

<details>

<summary>参加公共培训课程</summary>

观看 Bitwarden 专家现场演示安全配置、管理用户权限，并展示企业版功能。了解 Bitwarden 的强大能力，并现场获得问题解答！

<a href="https://bitwarden.com/go/weekly-demo/" class="button primary">参加课程</a>

</details>

## 入职资源

<details>

<summary>客户成功中心</summary>

该资源中心为 IT 和安全领导者提供了一条行之有效的密码安全成功之路，其中包含一系列精心挑选的指南、清单、资源和里程碑。

<a href="../../../../docs/admin-console/onboarding/customer-success-hub.md" class="button primary">访问中心</a>

</details>

<details>

<summary>入职手册</summary>

该手册为 IT 管理员提供了一个灵活的路线图，帮助用户跨五个关键阶段使用 Bitwarden Password Manager。虽然各阶段按顺序呈现，但并非严格线性。根据团队需求和时间表，许多步骤可以并行进行。

<a href="../../../../docs/admin-console/onboarding/bitwarden-onboarding-playbook.md" class="button primary">查看手册</a>

</details>

<details>

<summary>客户激活套件</summary>

这个全面的套件为管理员和 IT 团队提供了所需的一切资源，以激发热情、传达密码安全的优势，并将您的最终用户转变为安全倡导者。无论您是向小团队推广还是进行企业级部署，这些资源都能在任何规模上支持成功的采用。

<a href="../../../../docs/admin-console/onboarding/customer-activation-kit.md" class="button primary">访问套件</a>

</details>

## 开始使用 <a href="#get-started" id="get-started"></a>

<details>

<summary>注册 Bitwarden</summary>

Bitwarden 提供随您使用的无设备数量限制或登录数量限制的免费账户。[现在就开始吧](https://bitwarden.com/go/start-free/)！

### 您的主密码 <a href="#your-master-password" id="your-master-password"></a>

注册时，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2pST1WXY0Xk7GQ4GpwzELn/258a7524e9ecbfe25d2b3a4e455257c0/Set_master_password.png?w=800&#x26;fm=avif" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>创建组织</summary>

通过在 Bitwarden 网页 App 中选择**新增组织**按钮，现在就[创建您的组织](../../../../docs/admin-console/organizations-overview.md#create-an-organization)：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3eSqWiTIuPSFxXdo5AAjT9/248b0fa7bb381add0d71682acd244a63/2024-12-03_13-57-58.png?w=800&#x26;fm=avif" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>或加入现有组织</summary>

如果您的组织已经创建，请要求组织的其他成员向您发送邀请。

</details>

<details>

<summary>了解管理控制台</summary>

创建后，您将进入管理控制台，这是所有共享和组织管理的中心枢纽。作为组织所有者，您可以查看**密码库**项目和[集合](../../../../docs/admin-console/organizations-overview.md#collections)、管理**成员**、运行**报告**、更改**计费**设置，以及配置其他组织**设置**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?w=800&#x26;fm=avif" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>管理密码库项目和集合</summary>

作为所有者或管理员，您可能负责管理公司或团队对**密码库项目**（如共享凭据）的访问权限。您可以直接从网页 App 中创建项目，并将其分配到集合，以便与团队共享：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1u6EPNgAlCnvC9DcmUIosQ/327c0c24e09dce687540499a8eaa5aac/2024-12-02_15-47-21.png?w=800&#x26;fm=avif" alt=""><figcaption></figcaption></figure></div>

说到[集合](../../../../docs/admin-console/manage-shared-items/collections/about-collections.md)，它们是一种重要的结构，用于将相关的登录、备注、支付卡和身份组合在一起，以便与组织安全地共享：

* 组织可以定义对集合的访问权限，允许用户或群组只能访问他们需要的项目。
* 存储在组织集合中的项目不属于任何个人用户，而是属于组织。
* 组织拥有的项目**必须**至少包含在一个集合中。

{% hint style="success" %}
数据也可以直接导入到您的组织中！[了解如何操作](../../../../docs/admin-console/manage-shared-items/import-organization-items/import-to-organization.md#import-to-your-organization)。
{% endhint %}

</details>

<details>

<summary>管理成员和群组</summary>

作为所有者或管理员，您可能要负责管理团队成员或更广泛的公司成员。成员可以添加到您的组织中：

* 直接从管理控制台的**成员**页面添加（[了解更多](../../../../docs/admin-console/manage-members/user-management.md#invite)）
* 使用 SCIM 将 Bitwarden 与您的 IdP 集成（[了解更多](../../../../docs/admin-console/manage-members/scim/about-scim.md)）
* 使用 Directory Connector 将 Bitwarden 与您的目录服务集成（[了解更多](../../../../docs/admin-console/manage-members/directory-connector/about-directory-connector.md)）

成员可以直接分配给集合，以管理他们可以访问的密码库数据，但[群组](../../../../docs/admin-console/manage-members/groups.md)也可以。群组将单个成员联系在一起，提供了一种可扩展的方式来分配对特定集合的访问权限：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/FefJG4qBRiWkTzsxBKfm6/53093b4dd48e534cdde9f3e249d3c382/2024-12-03_14-22-27.png?w=800&#x26;fm=avif" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>集成及更多</summary>

Bitwarden 团队版组织提供强大的工具，可帮助您提升在线安全，并与现有工作流程和工具集成。作为组织管理员，您还可以管理以下事项：

* 审计[组织成员具有访问权限](../../../../docs/password-manager/your-vault/security-tools/vault-health-reports.md#member-access)的凭据。
* 将 Bitwarden 与您现有的 SIEM 工具（例如 [Microsoft Sentinel](../../../../docs/admin-console/oversight-visibility/siem-integrations/microsoft-sentinel-siem.md)）集成。

</details>

## 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

<details>

<summary>网页 App</summary>

{% embed url="https://vimeo.com/1145638406?fl=pl&fe=cm" %}

了解如何使用 Bitwarden 网页 App 中的管理控制台将密码导入您的组织。

<a href="https://vault.bitwarden.com/" class="button primary">打开网页 App</a>

* **00:00**：简介
* **00:04**：开始使用
* **00:17**：  选择文件格式
* **00:20**：  定位导入文件
* **00:26**：  导入数据

</details>

<details>

<summary>桌面 App - 包括 Chromium 浏览器的直接导入</summary>

{% embed url="https://vimeo.com/1145638482?fl=pl&fe=cm" %}

了解如何使用桌面 App [导入密码](../../../../docs/password-manager/import-and-export/import-data.md)和其他数据到 Bitwarden。浏览器密码可以从 Chrome、Edge、Opera、Brave 和 Vivaldi [直接导入](../../../../docs/password-manager/import-and-export/import-guides/import-data-from-chrome.md#import-directly-from-browser)。

直接从 Bitwarden 网站下载桌面 App，以使用「从浏览器直接导入」选项。

<a href="https://bitwarden.com/download/#downloads-desktop-applications" class="button primary">下载桌面 App</a>

* **00:00**：简介
* **00:06**：开始使用
* **00:27**：直接从浏览器导入
* **01:03**：从文件导入

</details>

<details>

<summary>命令行界面</summary>

[了解](../../../../docs/password-manager/import-and-export/import-data.md#cli)如何通过 CLI 将数据导入您的组织。

</details>

<details>

<summary>从自定义文件</summary>

{% embed url="https://vimeo.com/1145638421?fl=pl&fe=cm" %}

了解从自定义文件[如何导入](../../../../docs/password-manager/import-and-export/condition-bitwarden-import.md)密码和其他数据。

<a href="../../../../docs/password-manager/import-and-export/condition-bitwarden-import.md" class="button primary">下载示例文件</a>

* **00:00**：简介
* **00:08**：开始使用
* **00:12**：下载示例 CSV
* **00:21**：查看列标题
* **00:25**：导入自定义文件

</details>

## 支持 <a href="#support" id="support"></a>

<details>

<summary>Smart Search</summary>

使用 **Bitwarden Smart Search** 立即寻找答案。

<a href="https://bitwarden.com/smart-search/" class="button primary">Try Smart Search</a>

</details>

<details>

<summary>询问社区</summary>

与经验丰富的 Bitwarden 用户联系，分享技巧并共同解决问题。在[社区论坛](https://community.bitwarden.com/c/support/pm-ask-the-community/?_gl=1*1gc3ljx*_gcl_au*NDkyNTE5NzM4LjE3NjU1Mzk5OTUuMTMxODM0NjMwLjE3NjY4OTA0MjUuMTc2Njg5MDQyNQ..*_ga*MTk5NzU0OTg5My4xNzU2OTg5NjI5*_ga_QBRN562QQQ*czE3Njc2MzE2MjUkbzE3OCRnMSR0MTc2NzYzMjUxNyRqNjAkbDAkaDA.)或 [Reddit](https://www.reddit.com/r/Bitwarden/new/) 上提问。

</details>

<details>

<summary>联系支持</summary>

遇到技术问题或有账户问题？请联系 Bitwarden 支持团队获取直接的协助。

<a href="https://bitwarden.com/contact/" class="button primary">联系支持</a>

</details>

# 组织

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-organizations/)
{% endhint %}

## 什么是组织？ <a href="#what-are-organizations" id="what-are-organizations"></a>

组织将 Bitwarden 用户和密码库项目联系在一起，以[安全地共享](sharing.md)登录、笔记、支付卡和身份信息。组织有一个独立的视图，即管理员控制台，[管理员](../admin-console/user-management/member-roles-and-permissions.md)可在此管理组织的项目和成员、运行报告以及配置组织设置等：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/hzBuypc5ISzqC3jUmYbea/edcb03ce3d3071cea4f9afb6c7f8eca9/2024-12-03_13-46-09.png?_a=DAJCwlWIZAAB" %}
免费组织管理控制台
{% endembed %}

组织的成员可以在他们的**密码库**视图中找到已共享的项目，其与个人项目列在一起，以及使用多种方法将项目列表筛选为组织项目或特定[集合](collections.md)中的项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?_a=DAJCwlWIZAAB" %}
组织密码库
{% endembed %}

### 组织的类型 <a href="#types-of-organizations" id="types-of-organizations"></a>

Bitwarden 提供了多种类型的组织，以满足您的企业或家庭的需求。关于每种组织类型的逐一功能细分，请参阅[关于 Bitwarden 计划](../plans-and-pricing/password-manager/about-bitwarden-plans.md)。

<table><thead><tr><th width="150">类型</th><th>描述</th></tr></thead><tbody><tr><td>免费组织</td><td>免费组织允许 2 个用户在最多 2 个<a href="collections.md">集合</a>中安全地共享。</td></tr><tr><td>家庭住址</td><td>家庭组织允许 6 个用户在无限的<a href="collections.md">集合</a>中安全地共享。</td></tr><tr><td>团队组织</td><td>团队组织允许无限的用户（按每用户每月计费）在无限的<a href="collections.md">集合</a>中安全地共享，并提供一套操作工具，如事件日志。</td></tr><tr><td>企业组织</td><td>企业组织允许无限的用户（按每用户每月计费）在无限的<a href="collections.md">集合</a>中安全地共享，并在 Bitwarden 的操作工具套件中添加了仅针对企业的功能，例如 <a href="../login-with-sso/about-login-with-sso.md">SSO 登录</a>和<a href="enterprise-policies.md">策略</a>。</td></tr></tbody></table>

### 组织与高级会员比较 <a href="#comparing-organizations-with-premium" id="comparing-organizations-with-premium"></a>

关键的是要知道，**组织可以实现从组织到用户的安全共享**。[高级个人计划](../plans-and-pricing/password-manager/about-bitwarden-plans.md#premium-individual)可解锁高级密码安全和管理功能，包括高级 2FA 选项、Bitwarden 验证器（TOTP）、加密的文件附件等，但高级个人计划**不包含安全数据共享功能**。

付费组织（家庭、团队或企业）自动为组织中已注册的**每一个**用户提供这些高级功能（高级 2FA 选项、Bitwarden 验证器（TOTP）等）。

### 组织与提供商比较 <a href="#comparing-organizations-with-providers" id="comparing-organizations-with-providers"></a>

[提供商](../provider-portal/provider-portal-overview.md)是密码库管理的实体，允许像托管服务提供商 （MSP）等企业代表商业客户快速创建和管理**多个 Bitwarden 组织**。

## 创建组织 <a href="#create-an-organization" id="create-an-organization"></a>

通过[网页 App](../getting-started/getting-started-webvault.md) 创建和管理组织。如果您是 Bitwarden 新手，请在开始一个组织之前[创建一个帐户](https://vault.bitwarden.com/#/register)，然后按照以下说明进行操作：

1、从 Bitwarden 网页 App 中选择**新建组织**按钮：

![新建组织](../.gitbook/assets/new-org-button-overlay.png)

输入**组织名称**和一个我们可以联系到您的**账单电子邮箱**。[了解计费电子邮箱持有者的权限](../plans-and-pricing/billing-faqs.md#wen-wo-de-zu-zhi-de-ji-fei-dian-zi-you-jian-de-chi-you-zhe-ke-yi-zhi-xing-na-xie-cao-zuo)。

2、**选择您的计划**。Bitwarden 提供适合任何需求的组织。查看[功能区别](../plans-and-pricing/password-manager/about-bitwarden-plans.md#compare-business-plans)，以找出最适合您的组织。

{% hint style="success" %}
所有付费组织（家庭、初创团队、团队或企业）都包含了所有注册用户的高级功能！
{% endhint %}

4、如果您选择**免费组织**，那么一切就准备好了！如果您选择我们的付费组织之一，

* **家庭/团队/企业**：您的计划随附了 1GB 加密[附件存储](../your-vault/file-attachments.md)空间。$0.33 /GB / 月添加**加附加存储（GB）**。
* **团队/企业**：指定组织所需的**用户席位**数量。以后可以随时添加更多席位。如果超过此数量，席位会自动增加，除非您[指定限制](user-management.md#set-a-seat-limit)。
* **团队/企业**：选择您要**按年**还是**按月**付费。家庭组织只能**按年**付费。

5、对组织满意后，请输入您的**付款信息**（如果您创建的是免费组织，则不需要），然后选择**提交**。

{% hint style="success" %}
新的家庭、团队和企业组织内置了 7 天免费试用！在您的试用期结束之前，我们不会向您收费，您可以随时从组织的**设置**选项卡中取消订阅。
{% endhint %}

创建您的组织后，就可以创建[集合](collections.md)、[邀请用户](user-management.md)并[开始共享](sharing.md)。

## 集合和群组 <a href="#collections-and-groups" id="collections-and-groups"></a>

Bitwarden 集合和群组是一种组织工具，可以让您安全地共享数据并管理大规模访问。

### 集合 <a href="#collections" id="collections"></a>

集合是一种关联和共享项目的方式，类似于共享文件夹。项目可以属于一个或多个集合。拥有相应权限的用户可以对集合进行管理。集合通常可以按以下方式组织：

* 部门（工程部、人力资源部）
* 责任领域（社交媒体、软件开发）
* 功能（合规报告、客户外联）

要开始使用集合，请参阅[此处](collections.md)。

### 群组 <a href="#groups" id="groups"></a>

群组关联组织成员的一种方式，类似于身份提供商中的用户群组。群组使管理员能够批量授予或撤销集合权限，或在新成员加入组织时充当模板。群组通通常可以按以下方式组织：

* 部门（工程部、人力资源部）
* 供应商或系统（AWS、生产服务器）
* 地区（美国员工、欧盟员工）

要开始使用群组，请参阅[此处](groups.md)。

## 升级组织 <a href="#upgrade-an-organization" id="upgrade-an-organization"></a>

如果您想将组织升级到另一个计划，以解锁[附加功能](../plans-and-pricing/password-manager/about-bitwarden-plans.md)：

1. 在管理控制台中，导航到组织的**计费** → **订阅**视图。
2. 选择**升级计划**按钮。

您只能将组织升级到更高的计划，例如从团队计划升级到企业计划。以这种方式升级组织不会像创建新组织那样启动 7 天免费试用。

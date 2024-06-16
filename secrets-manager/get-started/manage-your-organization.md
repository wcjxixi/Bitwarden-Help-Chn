# 管理您的组织

{% hint style="info" %}
对应的[方文档地址](https://bitwarden.com/help/manage-your-sercrets-org/)
{% endhint %}

作为一个使用 Secrets Manager 的组织，您会分享许多最初由 Password Manager 使用的工具。这篇文章涵盖了这些常见的领域，并在适当的地方链接到共享文档。

{% hint style="info" %}
如果您是 Bitwarden 组织的新手，我们建议您查看我们关于[组织管理员入门](../../miscellaneous/get-started-administrator.md)的文章。
{% endhint %}

## 企业策略 <a href="#enterprise-policies" id="enterprise-policies"></a>

策略允许企业组织为其成员实施安全规则，例如强制使用两步登录。虽然一些策略主要适用于 Password Manager，但有一些策略也广泛适用于 Secrets Manager 的用户：

* [要求两步登录](../../organizations/enterprise-policies.md#require-two-step-login)
* [主密码要求](../../organizations/enterprise-policies.md#master-password-requirements)
* [主密码重置](../../organizations/enterprise-policies.md#master-password-reset)
* [单一组织](../../organizations/enterprise-policies.md#single-organization)
* [要求单点登录验证](../../organizations/enterprise-policies.md#require-single-sign-on-authentication)
* [密码库超时](../../organizations/enterprise-policies.md#vault-timeout)

{% hint style="info" %}
如果您是 Bitwarden 的新手，我们建议您在入职用户之前先设置策略。
{% endhint %}

## 用户管理 <a href="#user-management" id="user-management"></a>

Secrets Manager 的组织用户管理与使用 Password Manager 的组织用户管理是相似的，除了一些 Secrets Manager 特定的元素（[授予组织成员对 Secrets Manager 的访问权限](manage-your-organization.md#access-to-secrets-manager)、[成员角色](manage-your-organization.md#member-roles)差异，以及指定[用户席位和机器账户](secrets-manager-quick-start.md#user-seats-and-service-account-scaling)）。

### 入职 <a href="#onboarding" id="onboarding"></a>

有几种不同的方式

可以让用户加入您的 Bitwarden 组织。我们将在此处列出一些要点，查看[这篇指南](../../business-resources/onboarding-and-succession.md)以获取更完整的信息：

#### 手动 <a href="#manual" id="manual"></a>

Bitwarden 网页密码库提供了一个简单直观的界面，用于邀请新用户加入您的组织。此方法最适合小型组织或不使用 Azure AD 或 Okta 等目录服务的组织。[了解如何开始](../../organizations/user-management.md#invite)。

#### SCIM

Bitwarden 服务器提供一个 SCIM 端点，该端点具有一个有效的 SCIM API 密钥，将接受来自您的身份提供商的请求，以进行用户和群组配置和取消配置。此方法最适合使用了支持 SCIM 的目录服务或 IdP 的大型组织。[了解如何开始](../../scim/about-scim.md)。

#### 目录连接器 <a href="#directory-connector" id="directory-connector"></a>

目录连接器通过从一系列源目录服务中提取，自动在您的 Bitwarden 组织中配置用户和群组。此方法最适合使用了不支持 SCIM 的目录服务的大型组织。[了解如何开始](../../directory-connector/about-directory-connector.md)。

### 访问 Secrets Manager <a href="#access-to-secrets-manager" id="access-to-secrets-manager"></a>

入职后，为您组织的个人成员授予对 Secrets Manager 的访问权限：

1、打开您组织的**成员**选项卡，然后选中您想要授予 Secrets Manager 访问权限的成员。

2、使用 **≡**菜单，选中**启用 Secrets Manager** 以向选定成员授予访问权限：

* 对于自托管组织，也必须在自托管实例中重复此步骤。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3IBNL6FdndgPeuXa7m3rlP/429b9a1a63919be675b047521ff034a4/Screenshot_2024-02-27_at_2.16.52_PM.png?_a=BAJFJtWIB" %}
添加 Secrets Manager 用户
{% endembed %}

{% hint style="success" %}
授予成员对 Secrets Manager 的访问权限不会自动授予他们对存储的工程或机密的访问权限。接下来，您需要[为人员或群组分配对工程的访问权限](../your-secrets/projects.md#add-people-to-a-project)。
{% endhint %}

### 成员角色 <a href="#member-roles" id="member-roles"></a>

下表概述了每个成员角色可以在 Secrets Manager 中执行的操作。在 Beta 期间，用户在 Secrets Manager 的成员角色与他们在 Password Manager 中被分配的成员角色相同：

| 成员角色 | 描述                                                                                                                                        |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| 用户   | <p>用户可以创建自己的机密、工程、服务账户和访问令牌。创建后，他们就可以编辑这些对象。</p><p>必须将用户分配给工程或服务账户才能与现有对象交互，并且可以授予<strong>可以读取</strong>或<strong>可以读取、写入</strong>访问权限。</p> |
| 管理员  | <p>管理员自动拥有对所有机密、项目、服务账户和访问令牌的<strong>读取、写入</strong>权限。</p><p>管理员可以为自己分配对 Secrets Manager 的访问权限，并为其他成员分配对 Secrets Manager 的访问权限。</p>       |
| 所有者  | <p>所有者自动拥有对所有机密、项目、服务账户和访问令牌的<strong>读取、写入</strong>权限。</p><p>所有者可以为自己分配对 Secrets Manager 的访问权限，并为其他成员分配对 Secrets Manager 的访问权限。</p>       |

{% hint style="info" %}
自定义角色目前不在 Secrets Manager 的选项范围内，但仍可用于分配具体的 Password Manager 或更广泛的组织功能。
{% endhint %}

### 群组 <a href="#groups" id="groups"></a>

群组将个人成员联系在一起，并提供一种可扩展的方式来访问特定工程的访问权和权限。添加新成员时，将他们添加到一个群组中，让他们自动继承该群组配置的权限。[了解更多](../../organizations/groups.md)。

在管理控制台中创建群组后，就可以从 Secrets Manager 网页应用程序中把它们分配给工程了。

## 单点登录 <a href="#single-sign-on" id="single-sign-on"></a>

SSO 登录是 Bitwarden 用于单点登录的解决方案。使用 SSO 登录，企业组织可以利用其现有的身份提供程序使用 SAML 2.0 或 Open ID Connect (OIDC) 协议对 Bitwarden 用户进行身份验证。[了解如何开始](../../login-with-sso/about-login-with-sso.md)。

## 账户恢复管理 <a href="#https-bitwarden.com-help-manage-your-secrets-org-account-recovery-administration" id="https-bitwarden.com-help-manage-your-secrets-org-account-recovery-administration"></a>

账户恢复允许指定的管理员恢复企业组织用户账户以及在员工忘记主密码时恢复访问权限。通过启用账户恢复管理策略，可以为组织激活账户恢复功能。[了解如何开始](../../organizations/admin-password-reset.md)。

## 事件日志 <a href="#event-logs" id="event-logs"></a>

[事件日志](../../admin-console/reporting/event-logs.md)是团队或企业组织内发生的事件的时间戳记录。Secrets Manager 事件可从组织密码库的**报告** → **事件日志**以及[机器账户事件日志页面](../your-secrets/machine-accounts.md#service-account-events)获取。

事件日志可以导出并无限期保留。虽然许多事件适用于所有 Bitwarden 产品，有些是特定于 Password Manager 的，但 Secrets Manager 将专门记录以下内容：

* 机密被机器账户访问

## 自托管

企业组织可以在 Linux 和 Windows 计算机上使用 Docker 自行托管 Bitwarden Secrets Manager。如果您之前没有自行托管过 Bitwarden，请使用[本指南](../../self-hosting/self-host-an-organization.md)让自己走上正轨。

如果您已经自行托管一个 Enterprise Bitwarden 组织，并希望在该服务器上访问 Secrets Manager：

1. 在云托管的 Bitwarden 组织中注册一个 Secrets Manager 订阅。
2. 将您的自托管服务器更新到至少 2023.10.0 版本。
3. 从您的云托管组织[获取新的许可证文件](../../self-hosting/licensing-for-paid-features.md#retrieve-organization-license)，然后[将其上传到您的自托管服务器](../../self-hosting/licensing-for-paid-features.md#update-organization-license)。
4. 授予个人用户对自托管实例中的 [Secrets Manager 访问权限](manage-your-organization.md#access-to-secrets-manager)。

{% hint style="info" %}
Bitwarden [统一自托管部署选项](../../self-hosting/install-and-deploy-guides/docker/unified-deployment-beta.md)不支持自托管 Secrets Manager。团队和企业组织应使用标准的 [Linux](../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md) 或 [Windows](../../self-hosting/install-and-deploy-guides/docker/windows-standard-deployment.md) 安装。
{% endhint %}

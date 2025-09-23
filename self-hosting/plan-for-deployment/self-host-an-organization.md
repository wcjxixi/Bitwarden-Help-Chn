# 自托管组织

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/self-host-an-organization/)
{% endhint %}

## 第 1 步：安装和部署您的服务器 <a href="#step-1-install-and-deploy-your-server" id="step-1-install-and-deploy-your-server"></a>

在您可以自托管组织之前，您需要安装和部署 Bitwarden 到您的服务器。Bitwarden 可以在 Linux 和 Windows 机器上使用 Docker 运行。虽然有多种安装 Bitwarden 的方式，包括用于离线或网闸环境的方式，但我们建议从以下指南之一开始：

* [安装和部署 - Linux](../deploy-and-configure/docker/linux-standard-deployment.md)
* [安装和部署 - Windows](../deploy-and-configure/docker/windows-standard-deployment.md)

> **\[译者注]**：[网闸](https://zh.wikipedia.org/wiki/%E7%BD%91%E9%97%B8) (air-gapped) 网络，是指与外部网络（如互联网或其他外部系统）完全隔离的计算机网络。这种隔离通过物理或逻辑手段实现，确保网络无法与外部环境进行数据交换，从而增强安全性。

## 第 2 步：配置组织环境变量 <a href="#step-2-configure-organization-environment-variables" id="step-2-configure-organization-environment-variables"></a>

Bitwarden 组织使用的某些功能未通过上述文章中记录的标准安装过程进行配置。要为您的自托管服务器配备 Bitwarden 组织可用的所有功能，请在您的 `./bwdata/env/global.override.env` 文件中设置以下变量：

| 变量                                                    | 描述                                                                                                                                               | 用途                                                                                                                                     |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| globalSettings\_\_mail\_\_smtp\_\_host=               | 您的 SMTP 服务器主机名（推荐）或 IP 地址。                                                                                                                       | 用于[邀请用户](../../admin-console/manage-members/user-management.md#invite)加入您的组织。                                                          |
| globalSettings\_\_mail\_\_smtp\_\_port=               | SMTP 服务器使用的 SMTP 端口。                                                                                                                             | 用于[邀请用户](../../admin-console/manage-members/user-management.md#invite)加入您的组织。                                                          |
| globalSettings\_\_mail\_\_smtp\_\_ssl=                | <p>（布尔值）您的 SMTP 服务器使用何种加密协议：</p><p><code>true</code> = SSL</p><p><code>false</code> = TLS</p>                                                    | 用于[邀请用户](../../admin-console/manage-members/user-management.md#invite)加入您的组织。                                                          |
| globalSettings\_\_mail\_\_smtp\_\_username=           | `smtp__host` 的有效用户名。                                                                                                                             | 用于[邀请用户](../../admin-console/manage-members/user-management.md#invite)加入您的组织。                                                          |
| globalSettings\_\_mail\_\_smtp\_\_passsword=          | `smtp__username` 的有效密码。                                                                                                                          | 用于[邀请用户](../../admin-console/manage-members/user-management.md#invite)加入您的组织。                                                          |
| globalSettings\_\_enableCloudCommunication=           | 设置为 `true` 以允许您的服务器和我们的云系统之间进行通信。                                                                                                                | 用于[计费和许可证同步](self-host-an-organization.md#step-4-setup-billing-and-license-sync)。                                                      |
| globalSettings\_\_duo\_\_aKey=                        | 随机生成的 Duo 密钥。有关详细信息，请参阅 [Duo 文档](https://duo.com/docs/duoweb-v2#1.-generate-an-akey)。                                                            | 用于[组织层面的 DUO 两步登录](../../account/two-step-login/setup-guides/two-step-login-via-duo.md)。                                               |
| globalSettings\_\_hibpApiKey=                         | 您的 HaveIBeenPwned (HIBP) API 密钥，可在[此处](https://haveibeenpwned.com/API/Key)获得。                                                                    | 允许用户在创建账户时运行[数据泄露报告](../../your-vault/vault-health-reports.md#data-breach-report-individual-vaults-only)并检查其主密码是否存在泄露。                 |
| globalSettings\_\_disableUserRegistration=            | 指定为 `true` 以禁止新用户通过注册页面在此实例上注册账户。                                                                                                                | 用于将服务器上的用户限制为受邀加入组织的用户。                                                                                                                |
| globalSettings\_\_sso\_\_enforceSsoPolicyForAllUsers= | 指定为 `true` 以对所有者和管理员角色强制执行[要求 SSO 身份验证](../../admin-console/manage-shared-items/enterprise-policies.md#require-single-sign-on-authentication)策略。 | 用于为所有者和管理员角色强制执行[要求 SSO 身份验证](../../admin-console/manage-shared-items/enterprise-policies.md#require-single-sign-on-authentication)策略。 |

对环境变量进行更改后，执行 `./bitwarden.sh rebuild` 以将更改应用到服务器。

## 第 3 步：启动您的组织 <a href="#step-3-start-your-organization" id="step-3-start-your-organization"></a>

### 启动云端组织 <a href="#start-a-cloud-organization" id="start-a-cloud-organization"></a>

在此阶段，您已准备好启动您的组织并将其移植到您的自托管服务器。出于计费目的，必须首先在 Bitwarden 云端密码库 ([https://vault.bitwarden.com](https://vault.bitwarden.com)) 中创建组织。按照[这些说明](../../admin-console/organizations-overview.md#create-an-organization)创建组织。

### 启动自托管组织 <a href="#start-a-self-hosted-organization" id="start-a-self-hosted-organization"></a>

创建云端组织后，请按照[这些说明](../licensing.md#organization-license)从云端获取您的许可证并将其上传到您的自托管服务器以创建该组织的自托管副本。

自托管的 Bitwarden 组织将能够使用他们选择的计划提供的所有付费功能。只有家庭和企业组织可以导入到自托管服务器。在[这里](../../plans-and-pricing/password-manager/about-bitwarden-plans.md)了解更多。

## 第 4 步：设置计费和许可证同步 <a href="#step-4-setup-billing-and-license-sync" id="step-4-setup-billing-and-license-sync"></a>

接下来，设置您的自托管组织以从您的云端组织同步计费和许可证。这个是可选的，但有一些好处：

* 当您更改组织的席位数量时，可以更轻松地更新许可证。
* 当您的订阅到了续订日期时，可以更轻松地更新许可证。
* 为企业组织的成员解锁[家庭组织赞助](../../plans-and-pricing/password-manager/redeem-families-sponsorship.md)。

按照[这些说明](../licensing.md#update-organization-license)为您的组织设置计费和许可同步。

{% hint style="info" %}
计费和许可证同步需要将 `globalSettings__enableCloudCommunication=` 环境变量设置为 `true`（[了解更多](../deploy-and-configure/configuration-options/environment-variables.md)）。
{% endhint %}

## 第 5 步：开始组织管理 <a href="#step-5-start-organization-administration" id="step-5-start-organization-administration"></a>

您现在已准备好开始管理您的自托管组织了！以下是您可以采用的方法：

{% tabs %}
{% tab title="Password Manager" %}
### 邀请您的管理团队 <a href="#invite-your-admin-team" id="invite-your-admin-team"></a>

每个全明星组织都需要一个全明星管理团队。开始邀请高权限成员，他们可以帮助您为与 Bitwarden 的安全凭证共享奠定基础。如果您正在构建企业组织，您可以为成员提供[满足您的要求的高度灵活的自定义权限](../../admin-console/manage-members/member-roles-and-permissions.md#custom-role)。

以保护冗余为目的，我们建议在您新成立的管理团队中至少包括一名额外的**组织所有者**。

### 设置策略（仅限企业） <a href="#set-policies-enterprise-only" id="set-policies-enterprise-only"></a>

您的业务具有独特的安全需求。使用策略为所有团队成员构建一致的部署和用户体验，例如要求 SSO 身份验证或在账户恢复管理中注册成员。为了让您的组织为更多团队成员做好准备，[尽早制定策略](../../admin-console/manage-shared-items/enterprise-policies.md)非常重要。

### 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

您需要从另一个密码管理器转到 Bitwarden 的吗？好消息！您可以将这些数据直接导入您的组织，以[避免痛苦的复制和粘贴一天](../../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md)。

### 建立群组和集合 <a href="#build-groups-and-collections" id="build-groups-and-collections"></a>

您的密码库中有了项目后，就可以设置集合和群组以确&#x4FDD;_&#x5408;&#x9002;_&#x7684;用户可以访&#x95EE;_&#x5408;&#x9002;_&#x7684;凭据。每个组织都是不同的，但这里有一些提示可以帮助您开始使用[集合入门](../../admin-console/manage-shared-items/collections/about-collections.md#using-collections)和[群组入门](../../admin-console/manage-members/groups.md#using-groups)。

### 邀请您的团队 <a href="#invite-your-team" id="invite-your-team"></a>

终于可以开始邀请用户了！如果您使用 Azure Active Directory 等身份提供商或目录服务，请使用 [SCIM](../../admin-console/manage-members/scim/about-scim.md) 或[目录连接器](../../admin-console/manage-members/directory-connector/about-directory-connector.md)自动同步用户。否则，请按照您建立管理团队所采取的相同步骤邀请更多用户加入组织。
{% endtab %}

{% tab title="Secrets Manager" %}
### 邀请您的管理团队 <a href="#invite-your-admin-team" id="invite-your-admin-team"></a>

每个全明星组织都需要一个全明星管理团队。开始邀请高权限成员，他们可以帮助您为与 Bitwarden 的安全机密共享奠定基础。

以保护冗余为目的，我们建议在您新成立的管理团队中至少包括一名额外的**组织所有者**。

### 设置策略（仅限企业） <a href="#set-policies-enterprise-only" id="set-policies-enterprise-only"></a>

您的业务具有独特的安全需求。使用策略为所有团队成员构建一致的部署和用户体验，例如要求 SSO 身份验证或在账户恢复管理中注册成员。为了让您的组织为更多团队成员做好准备，[尽早制定策略](../../admin-console/manage-shared-items/enterprise-policies.md)非常重要。

### 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

您需要从另一个密码管理器转到 Bitwarden 的吗？好消息！您可以将这些数据直接导入您的组织，[以避免痛苦的复制和粘贴一天](../../secrets-manager/import-export/import-data.md)。

### 邀请您的团队 <a href="#invite-your-team" id="invite-your-team"></a>

终于可以开始邀请用户了！如果您使用 Azure Active Directory 等身份提供商或目录服务，请使用 [SCIM](../../admin-console/manage-members/scim/about-scim.md) 或[目录连接器](../../admin-console/manage-members/directory-connector/about-directory-connector.md)自动同步用户。否则，请按照您建立管理团队所采取的相同步骤邀请更多用户加入组织。每个人都入职之后，[开始授予用户对 Secrets Manager 的访问权限](../../secrets-manager/get-started/secrets-manager-quick-start.md#give-members-access)。
{% endtab %}
{% endtabs %}

# 迁移到新服务器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/migration/)
{% endhint %}

本文将引导您完成从云端迁移到自托管、从自托管迁移到云端，以及从一个自托管服务器迁移到另一个自托管服务器的过程。

{% tabs %}
{% tab title="云端到自托管" %}
要从云端迁移到自托管服务器：

1、将 Bitwarden [安装和部署](../deploy-and-configure/docker/linux-standard-deployment.md)到您的服务器上。此过程大概涉及到：

1. 为 Bitwarden [配置一个域名](../deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain)。
2. [安装 Docker 和 Docker Compose](../deploy-and-configure/docker/linux-standard-deployment.md#install-docker-and-docker-compose)。
3. 运行[安装 Shell 脚本](../deploy-and-configure/docker/linux-standard-deployment.md#install-bitwarden)。
4. [配置您的环境](../deploy-and-configure/docker/linux-standard-deployment.md#configure-your-environment)以设置管理门户、SMTP 服务器连接等。

2、运行 `./bitwarden.sh start` 启动服务器。

3、打开云端网页密码库然后[下载您的许可证](../licensing.md)。

{% hint style="success" %}
[组织许可证](../licensing.md#organization-license)和[个人许可证](../licensing.md#individual-license)是独立的文件。**您不需要下载这两个许可证文件**。如果您要迁移组织，则只需要获取组织许可证，并且必须是[组织所有者](../../admin-console/manage-members/member-roles.md)才能执行此操作。
{% endhint %}

4、还是在云端网页密码库中，[导出您的个人密码库数据](../../import-export/export-vault-data.md#export-a-personal-vault)或[导出您的组织密码库数据](../../import-export/export-vault-data.md#export-an-organization-vault)。如果您要迁移组织，请鼓励您的最终用户也导出他们的个人密码库。

5、打开您的自托管网页密码库并创建一个账户。此账户**必须使用与您下载许可证所用的云端账户相同的电子邮箱地址**。

6、还是在您自托管的网页密码库中，上传您的[许可证](../licensing.md)。

{% hint style="success" %}
上传[组织许可证](../licensing.md#organization-license)和[个人许可证](../licensing.md#individual-license)的位置是不同的。和之前的一样，只上传与你相关的那一个。
{% endhint %}

7、还是在自托管的网页密码库中，将数据导入您的[个人密码库](../../password-manager/import-and-export/import-data.md)或[组织密码库](../../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md)。

{% hint style="info" %}
导入数据到组织将自动重新创建[集合](../../admin-console/manage-shared-items/collections/about-collections.md)，并将相关的密码库项目添加到其中。
{% endhint %}

### 下一步（仅针对组织）

如果您要将组织迁移到自托管服务器，请继续执行以下步骤：

1、**（仅企业组织）**&#x91CD;新实施您的[企业策略](../../admin-console/oversight-visibility/enterprise-policies.md)规范和/或配置 [SSO 登录](../../login-with-sso/about-login-with-sso.md)。

2、在自托管网页密码库中手动[重新创建用户群组](../../admin-console/manage-members/groups.md#create-a-group)，并将它们分配给适当的集合。

3、手动或使用[目录连接器](../../admin-console/manage-members/directory-connector/about-directory-connector.md)[邀请用户加入您的组织](../../admin-console/manage-members/user-management.md#invite)。
{% endtab %}

{% tab title="自托管到云端" %}
要从自托管服务器迁移到云端：

1、创建自托管 Bitwarden 服务器的 `./bwdata` 目录的完整备份。需要特别注意，您需要访问 `./bwdata/core/attachments` 手动将[文件附件](../../password-manager/your-vault/vault-items/file-attachments.md)上传到云端（**步骤 5**）。

{% hint style="success" %}
如果用户在一段时间内导出了他们的个人密码库，你可能需要从 `./bwdata/core/attachments` 目录中重新同步项目到你的备份位置，并上传任何在切换期间发生变化的新项目。
{% endhint %}

2、在您自托管网页密码库中，[导出您的个人密码库数据](../../import-export/export-vault-data.md#export-a-personal-vault)或[导出您的组织密码库数据](../../import-export/export-vault-data.md#export-an-organization-vault)。如果您要迁移组织，请鼓励您的最终用户也导出他们的个人密码库。

3、打开云端网页密码库。大多数用户在之前都已创建了用于计费目的的云端账户，因此请登录该账户。如果您之前的免费账户不是用于计费的云端账户，请立即创建一个账户。

{% hint style="success" %}
如果您要迁移组织，则您已经拥有了一个用于计费和许可目的的云端组织。为了最平稳地过渡，我们建议使用这个已经建立的组织，而不是[创建一个新的组织](../../admin-console/organizations-overview.md#create-an-organization)。
{% endhint %}

4、还是在云端网页密码库中，将数据导入您的[个人密码库](../../password-manager/import-and-export/import-data.md)或[组织密码库](../../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md)。

{% hint style="info" %}
导入数据到组织将自动重新创建您的[集合](../../admin-console/manage-shared-items/collections/about-collections.md)，并将相关的密码库项目添加到其中。
{% endhint %}

5、手动将[文件附件](../../password-manager/your-vault/vault-items/file-attachments.md)上传到您的个人或组织密码库。

### 下一步（仅针对组织）

如果您要将组织迁移到云端，请继续执行以下步骤：

1. **（仅企业组织）**&#x91CD;新实施您的[企业策略](../../admin-console/oversight-visibility/enterprise-policies.md)规范和/或配置 [SSO 登录](../../login-with-sso/about-login-with-sso.md)。
2. 在云端手动[重新创建用户群组](../../admin-console/manage-members/groups.md#create-a-group)，并将它们分配给适当的集合。
3. 手动或使用[目录连接器](../../admin-console/manage-members/directory-connector/about-directory-connector.md)[邀请用户加入您的组织](../../admin-console/manage-members/user-management.md#invite)。
{% endtab %}

{% tab title="主机到主机" %}
{% hint style="success" %}
这些说明目前只适用于从一个 Linux 托管服务器迁移到另一个 Linux 托管服务器。
{% endhint %}

要从一个自托管的 Bitwarden 服务器迁移到另一个：

1、运行 `./bitwarden.sh stop` 停止现有的 Bitwarden 服务器。当您运行此命令时，Bitwarden 将为当前使用它的任何人关闭。

2、制作旧服务器的 `./bwdata` 目录的完整副本。此副本将用于在新服务器上重新创建您的配置、数据库、附件等。

3、[安装并部署](../deploy-and-configure/docker/linux-standard-deployment.md) Bitwarden 到您的新服务器上。

4、新的 Bitwarden 服务器设置好后，将新创建的 `./bwdata` 目录替换为旧服务器的副本。

5、运行 `id -u bitwarden` 打印新 Bitwarden 服务器的 UID。

6、打开文件 `./bwdata/env/uid.env` 并检查列出的值是否与上一步中打印的值匹配。如果不匹配，则使用 `id -u bitwarden` 的结果替换这两个值。

7、如果您在**步骤 2** 中指定了一个不一样的服务器域名，请编辑以下内容：

* 在 `./bwdata/config.yml` 中，将 `url:` 的值更改为新的域名。
* 在 `./bwdata/env/global.override.env` 中，将 `globalSettings__baseServiceUri__vault=` 的值更改为的域名。

8、运行 `./bitwarden.sh rebuild` 以将更改应用于 `config.yml` 和 `global.override.env`。

9、使用 `./bitwarden.sh start` 启动您的 Bitwarden 服务器。
{% endtab %}

{% tab title="云端到云端" %}
要从一个 Bitwarden 云端服务器迁移到另一个 Bitwarden 云端服务器，例如，从美国服务器迁移到欧盟服务器：

1、[导出您的组织密码库](../../import-export/export-vault-data.md#export-an-organization-vault)，然后指导所有组织成员[导出他们的个人密码库](../../import-export/export-vault-data.md#export-a-personal-vault)。

{% hint style="success" %}
单独下载密码库项目的任何文件附件，并注明它们属于哪个项目。
{% endhint %}

2、在所需区域创建一个新的 Bitwarden 账户，并开始试用组织。Bitwarden 支持人员会将您的订阅迁移到新的地区（见**步骤 4**）。

3、建立新组织，配置企业策略、SSO 登录、构建群组收-集合关系以及使用目录连接器或 SCIM 邀请用户等。如需帮助，请参阅[概念验证清单](../../business-resources/proof-of-concept-project-checklist.md)。

4、[联系 Bitwarden 支持](https://bitwarden.com/contact/)，将您的新组织从试用期中移出，并在新区域恢复您订阅。&#x20;

5、导入在**步骤 1** 中获得的组织保密码库数据，并指导组织成员也导入他们的个人密码库。

{% hint style="info" %}
将**步骤 1** 中获得的文件附件手动上传回与之关联的密码库项目。
{% endhint %}

## 迁移 FAQ <a href="#migration-faqs" id="migration-faqs"></a>

### 问：我需要迁移吗？ <a href="#q-do-i-need-to-migrate" id="q-do-i-need-to-migrate"></a>

答：不需要迁移区域。区域选择器允许企业指定密码库数据的地理位置。不同区域的功能和作用是相同的。

### 问：迁移有流程吗？  <a href="#q-is-there-a-process-for-migrating" id="q-is-there-a-process-for-migrating"></a>

答：Bitwarden 区域是不同的云端环境。Bitwarden 不能为客户将账户从一个区域迁移到另一个区域。企业可以使用脚本来帮助迁移。您可以[联系我们](https://bitwarden.com/contact/)将订阅从一个区域转移到另一个区域。

### 问：迁移脚本的作用是什么？ <a href="#q-what-does-the-migration-script-do" id="q-what-does-the-migration-script-do"></a>

答：脚本与 Bitwarden CLI 配合使用，将数据从一个安装转移到另一个安装。[本文](../../miscellaneous/migration-script.md)提供了相关说明。该脚本会迁移所有组织密码库数据，包括附件、成员角色（不包括自定义角色）以及分配给成员和群组的集合权限。如果不使用目录集成进行自动配置，脚本还会在新组织中自动重新创建组。请注意，这不包括个人用户密码库的迁移。

### 问：手动迁移是怎样的？ <a href="#q-what-does-a-manual-migration-look-like" id="q-what-does-a-manual-migration-look-like"></a>

答：完整的手动迁移包括在首选区域创建一个新账户，并开始新机构创建流程。新组织配置完成后，重新邀请用户，然后从旧组织导出密码库数据并导入新组织。用户需要手动导出/导入他们的个人密码库。
{% endtab %}
{% endtabs %}

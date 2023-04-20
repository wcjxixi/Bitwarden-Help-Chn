# 迁移步骤

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/migration/)
{% endhint %}

本文将引导您完成从云端迁移到自托管、从自托管迁移到云端，以及从一个自托管服务器迁移到另一个自托管服务器的过程。

{% tabs %}
{% tab title="云端到自托管" %}
要从云端迁移到自托管服务器：

1、将 Bitwarden [安装和部署](install-deploy-guides/install-and-deploy-linux.md)到您的服务器上。此过程大概涉及到：

1. 为 Bitwarden [配置一个域名](install-deploy-guides/install-and-deploy-linux.md#configure-your-domain)。
2. [安装 Docker 和 Docker Compose](install-deploy-guides/install-and-deploy-linux.md#install-docker-and-docker-compose)。
3. 运行[安装 Shell 脚本](install-deploy-guides/install-and-deploy-linux.md#install-bitwarden)。
4. [配置您的环境](install-deploy-guides/install-and-deploy-linux.md#configure-your-environment)以设置管理门户、SMTP 服务器连接等。

2、运行 `./bitwarden.sh start` 启动服务器。

3、打开云端网页密码库然后[下载您的许可证](licensing-for-paid-features.md)。

{% hint style="success" %}
[组织许可证](licensing-for-paid-features.md#organization-license)和[个人许可证](licensing-for-paid-features.md#individual-license)是独立的文件。**您不需要下载这两个许可证文件**。如果您要迁移组织，则只需要获取组织许可证，并且必须是[组织所有者](../admin-console/user-management/user-types-and-access-control.md)才能执行此操作。
{% endhint %}

4、还是在云端网页密码库中，[导出您的个人密码库数据](../password-manager/import-and-export/export-vault-data.md#export-a-personal-vault)或[导出您的组织密码库数据](../password-manager/import-and-export/export-vault-data.md#export-an-organization-vault)。如果您要迁移组织，请鼓励您的最终用户也导出他们的个人密码库。

5、打开您的自托管网页密码库并创建一个帐户。此帐户**必须使用与您下载许可证所用的云端帐户相同的电子邮件地址**。

6、还是在您自托管的网页密码库中，上传您的[许可证](licensing-for-paid-features.md)。

{% hint style="success" %}
上传[组织许可证](licensing-for-paid-features.md#organization-license)和[个人许可证](licensing-for-paid-features.md#individual-license)的位置是不同的。和之前的一样，只上传与你相关的那一个。
{% endhint %}

7、还是在自托管的网页密码库中，将数据导入您的[个人密码库](../password-manager/import-and-export/import-data-to-your-vault.md)或[组织密码库](../admin-console/import-and-export/import-data-to-an-organization.md)。

{% hint style="info" %}
导入数据到组织将自动重新创建[集合](../admin-console/organization-basics/collections.md)，并将相关的密码库项目添加到其中。
{% endhint %}

### 后续步骤（仅针对组织）

如果您要将组织迁移到自托管服务器，请继续执行以下步骤：

1、**（仅企业组织）**重新实施您的[企业策略](../admin-console/organization-basics/enterprise-policies.md)规范和/或配置 [SSO 登录](../admin-console/login-with-sso/about-login-with-sso.md)。

2、在自托管网页密码库中手动[重新创建用户群组](../admin-console/organization-basics/groups.md#create-a-group)，并将它们分配给适当的集合。

3、手动或使用[目录连接器](../admin-console/user-management/directory-connector/about-directory-connector.md)[邀请用户加入您的组织](../admin-console/user-management/user-management.md#invite)。
{% endtab %}

{% tab title="自托管到云端" %}
要从自托管服务器迁移到云端：

1、创建自托管 Bitwarden 服务器的 `./bwdata` 目录的完整备份。需要特别注意，您需要访问 `./bwdata/core/attachments` 手动将[文件附件](../password-manager/vault-basics/file-attachments.md)上传到云端（**步骤 5**）。

{% hint style="success" %}
如果用户在一段时间内导出了他们的个人密码库，你可能需要从 `./bwdata/core/attachments` 目录中重新同步项目到你的备份位置，并上传任何在切换期间发生变化的新项目。
{% endhint %}

2、在您自托管网页密码库中，[导出您的个人密码库数据](../password-manager/import-and-export/export-vault-data.md#export-a-personal-vault)或[导出您的组织密码库数据](../password-manager/import-and-export/export-vault-data.md#export-an-organization-vault)。如果您要迁移组织，请鼓励您的最终用户也导出他们的个人密码库。

3、打开云端网页密码库。大多数用户在之前都已创建了用于计费目的的云端帐户，因此请登录该帐户。如果您之前的免费账户不是用于计费的云端账户，请立即创建一个帐户。

{% hint style="success" %}
如果您要迁移组织，则您已经拥有了一个用于计费和许可目的的云端组织。为了最平稳地过渡，我们建议使用这个已经建立的组织，而不是[创建一个新的组织](../admin-console/organization-basics/organizations.md#create-an-organization)。
{% endhint %}

4、还是在云端网页密码库中，将数据导入您的[个人密码库](../password-manager/import-and-export/import-data-to-your-vault.md)或[组织密码库](../admin-console/import-and-export/import-data-to-an-organization.md)。

{% hint style="info" %}
导入数据到组织将自动重新创建您的[集合](../admin-console/organization-basics/collections.md)，并将相关的密码库项目添加到其中。
{% endhint %}

5、手动将[文件附件](../password-manager/vault-basics/file-attachments.md)上传到您的个人或组织密码库。

### 后续步骤（仅针对组织）

如果您要将组织迁移到云端，请继续执行以下步骤：

1. **（仅企业组织）**重新实施您的[企业策略](../admin-console/organization-basics/enterprise-policies.md)规范和/或配置 [SSO 登录](../admin-console/login-with-sso/about-login-with-sso.md)。
2. 在云端手动[重新创建用户群组](../admin-console/organization-basics/groups.md#create-a-group)，并将它们分配给适当的集合。
3. 手动或使用[目录连接器](../admin-console/user-management/directory-connector/about-directory-connector.md)[邀请用户加入您的组织](../admin-console/user-management/user-management.md#invite)。
{% endtab %}

{% tab title="主机到主机" %}
要从一个自托管的 Bitwarden 服务器迁移到另一个：

1、运行 `./bitwarden.sh stop` 停止现有的 Bitwarden 服务器。当您运行此命令时，Bitwarden 将为当前使用它的任何人关闭。

2、制作旧服务器的 `./bwdata` 目录的完整副本。此副本将用于在新服务器上重新创建您的配置、数据库、附件等。

3、[安装并部署](install-deploy-guides/install-and-deploy-linux.md) Bitwarden 到您的新服务器上。

4、新的 Bitwarden 服务器设置好后，将新创建的 `./bwdata` 目录替换为旧服务器的副本。

5、运行 `id -u bitwarden` 打印新 Bitwarden 服务器的 UID。

6、打开文件 `./bwdata/env/uid.env` 并检查列出的值是否与上一步中打印的值匹配。如果不匹配，则使用 `id -u bitwarden` 的结果替换这两个值。

7、如果您在**步骤 2** 中指定了一个不一样的服务器域名，请编辑以下内容：

* 在 `./bwdata/config.yml` 中，将 `url:` 的值更改为新的域名。
* 在 `./bwdata/env/global.override.env` 中，将 `globalSettings__baseServiceUri__vault=` 的值更改为的域名。

8、运行 `./bitwarden.sh rebuild` 以将更改应用于 `config.yml` 和 `global.override.env`。

9、使用 `./bitwarden.sh start` 启动您的 Bitwarden 服务器。
{% endtab %}
{% endtabs %}

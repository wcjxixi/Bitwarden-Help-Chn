# 自托管 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/hosting-faqs/)
{% endhint %}

本文包含有关自托管的常见问题 (FAQ)。

## 通用 <a href="#general" id="general"></a>

### 问：我可以托管在哪些平台上？ <a href="#q-what-platforms-can-i-host-on" id="q-what-platforms-can-i-host-on"></a>

**答：**&#x42;itwarden 是一个跨平台的应用程序，使用 Docker Linux 容器进行部署。这意味着 Bitwarden 可以托管在 Linux、macOS 和 Windows 机器上。

Windows 上的 Docker Desktop 版可能需要许可证，这取决于贵公司是否符合 [Docker 许可证要求](https://www.docker.com/pricing/)，但 Linux 上的 Docker 是免费的。

要阅读更多关于 Docker 和容器技术的信息，请访问 [Docker 网站](https://www.docker.com/why-docker)。

### 问：Bitwarden 客户端 App 支持非官方服务器吗？ <a href="#q-do-bitwarden-client-apps-support-non-official-servers" id="q-do-bitwarden-client-apps-support-non-official-servers"></a>

**答：**&#x867D;然我们希望大多数客户端功能都能与非官方服务器（如 Vaultwarden）兼容，但 Bitwarden 不能保证官方客户端能与非官方服务器完美兼容。如果您使用的是非官方服务器，我们建议您尽可能保持其最新，以便利用其维护者编写的兼容性更新。如果您使用的是非官方服务器，Bitwarden 客户支持在协助您解决客户端问题时可能会受到限制。

例如，Vaultwarden 在 1.31.0 版本中引入了对原生移动 App 的支持。如果您使用的是原生移动 App，并且 Vaultwarden 的版本低于 1.31.0，您将会收到错误提示，此时应升级您的服务器。

### 问：如何在 AWS、Azure、GCP 或 VMware vCenter上部署 Bitwarden？ <a href="#q-how-do-i-deploy-bitwarden-on-aws-azure-gcp-or-vmware-vcenter" id="q-how-do-i-deploy-bitwarden-on-aws-azure-gcp-or-vmware-vcenter"></a>

**答：**&#x42;itwarden 通常以单个 Windows 或 Linux 虚拟机或机器集群的形式部署。目前，Bitwarden 并未发布针对这些平台的预构建镜像，但您可以在[这里](plan-for-deployment/self-host-an-organization.md)找到如何在上述所有平台上配置虚拟机的说明。

### 问：我应该如何实现高可用性？ <a href="#q-how-should-i-achieve-high-availability" id="q-how-should-i-achieve-high-availability"></a>

**答：**&#x76EE;前推荐使用 Helm 部署以实现高可用性。但是，增加 Bitwarden 容器副本可能会导致意外行为。[此处](deploy-and-configure/helm/self-host-with-helm.md)了解更多有关使用 Helm 自托管 Bitwarden 的信息。

### 问：我需要允许哪些 URL 吗？ <a href="#q-do-i-need-to-allow-any-urls" id="q-do-i-need-to-allow-any-urls"></a>

**答：**&#x5728;安装标准的自托管 Bitwarden 服务器部署时，您的服务器将进行出站连接以实现某些功能，例如更新、向客户端推送通知以及同步企业版赞助家庭。如果您不希望使用这些功能，可以使用其中一个离线部署指南进行部署，这样服务器就不会在您的基础架构之外进行任何出站连接。如果您希望允许标准的出站功能，您需要允许以下 URL 通过防火墙：

* [这里](../security/trusted-communications/bitwarden-addresses.md#bitwarden-applications)列出的 **Bitwarden 服务器安装/更新 URL**。
* [这里](../security/trusted-communications/bitwarden-addresses.md#application-endpoints)列出的**应用程序端点**。

### 问：如何备份和还原我的自托管实例？ <a href="#q-how-do-i-backup-and-restore-my-self-hosted-instance" id="q-how-do-i-backup-and-restore-my-self-hosted-instance"></a>

**答：**&#x42;itwarden 会每晚自动备份 `bitwarden-mssql` 数据库容器，以保护您存储的凭据。有关手动备份，或恢复备份的帮助，请参阅[备份您的托管数据](backup-server-data.md)。

### 问：我的安装 ID 和安装密钥是用来干什么的？ <a href="#q-what-are-my-installation-id-and-installation-key-used-for" id="q-what-are-my-installation-id-and-installation-key-used-for"></a>

**答：**&#x5728;安装 Bitwarden 自托管时，安装 ID 和密钥用于：

* 注册您的安装，并包含电子邮件，以便我们能就有重要的安全更新时可以联系到您。&#x20;
* 认证推送中继服务器，以便向 Bitwarden 客户端应用程序推送通知。&#x20;
* 验证付费功能的许可证。&#x20;

从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取安装 ID 和密钥。

{% hint style="info" %}
在获取您的安装 ID 和密钥时，请务必选择与您的 Bitwarden 客户端相对应的服务器区域。[此处](../security/server-geographies.md#connect-your-self-hosted-server)了解如何应用正确的自托管服务器区域。
{% endhint %}

**您不应该在多个 Bitwarden 安装中共享您的安装 ID 或安装密钥。**&#x5B83;们应被视为机密。

### 问：如何更改我的服务器名称？ <a href="#q-how-do-i-change-the-name-of-my-server" id="q-how-do-i-change-the-name-of-my-server"></a>

**答：**&#x5728; `./bwdata/config.yml` 中使用您的新服务器名称配置 `url:`，然后运行 `./bitwarden.sh rebuild` 命令重建 `bwdata` 资产。

检查您的服务器名称或 FQDN，确保它们已经扩散到 `./bwdata/env/global.override.env` 中的所有 `globalSettings_baseServiceUri__*` 变量中，并确保您的证书中包含一个带有新服务器 FQDN 的[主题备用名称](https://zh.wikipedia.org/wiki/%E4%B8%BB%E9%A2%98%E5%A4%87%E7%94%A8%E5%90%8D%E7%A7%B0)（SAN）（Subject Alternative Name）。

如果您正在使用 Let's Encrypt 证书，您需要[手动更新您的证书](deploy-and-configure/configuration-options/certificate-options.md#manually-update-a-lets-encrypt-certificate)。

### 问：如何更改我的自助托管组织的名称？ <a href="#q-how-do-i-change-the-name-of-my-self-hosted-organization" id="q-how-do-i-change-the-name-of-my-self-hosted-organization"></a>

答：首先，使用网页 App 更改云中的组织名称。更改云端组织后，重新下载许可证文件，然后将新的许可证文件上传到自托管组织，参阅[这里](licensing-on-premise.md#organization-license)。

### 问：为什么当运行更新命令显示是最新版本时，系统管理员门户还会显示有可用的更新？ <a href="#q-why-does-the-admin-portal-show-an-update-available-when-update-and-updateself-show-im-on-the-lates" id="q-why-does-the-admin-portal-show-an-update-available-when-update-and-updateself-show-im-on-the-lates"></a>

**答：**&#x7CFB;统管理员门户将在我们发布云端服务器后立即显示可用更新，但如[发行说明](../release-notes.md)中所述，自托管服务器更新通常在云端服务器后几天才可用。请等待几天，然后再次尝试[更新您的实例](update-a-server.md)。

### 问：我可以在域名子文件夹下运行 Bitwarden 吗？ <a href="#q-can-i-run-bitwarden-under-a-domain-subfolder" id="q-can-i-run-bitwarden-under-a-domain-subfolder"></a>

**答：**&#x4E0D;支持在域名子文件夹下运行 Bitwarden（例如，用 `https://mydomain.com/bitwarden` 代替 `https://mydomain.com`）。它必须在主机，以及子域名下运行，可以附加端口。

## SMTP 配置 <a href="#smtp-configuration" id="smtp-configuration"></a>

### 问：如何设置 SMTP 邮件服务器？ <a href="#q-how-do-i-set-up-an-smtp-mail-server" id="q-how-do-i-set-up-an-smtp-mail-server"></a>

**答：**&#x901A;过编辑 `./bwdata/env/global.overide.env` 中的所有 `globalSettingsmailsmtp__*` 值，以将您的自托管实例连接到现有的 SMTP 邮件服务器。更多信息，请参阅[配置环境变量](deploy-and-configure/configuration-options/environment-variables.md)。

如果您还没有可以中继电子邮件的 SMTP 邮件服务器，可以考虑使用 [Mailgun](https://www.mailgun.com/) 或 [SparkPost](https://www.sparkpost.com/) 等服务。

### 问：如何将 Gmail 用作 SMTP 邮件服务器？ <a href="#q-how-do-i-use-gmail-as-an-smtp-mail-server" id="q-how-do-i-use-gmail-as-an-smtp-mail-server"></a>

{% hint style="danger" %}
从 2024 年秋季开始，使用 Gmail 作为 SMTP 的 Bitwarden 等 App 将需要使用 [App 专用密码](https://support.google.com/mail/answer/185833?hl=zh-Hans)进行身份验证，因为基本身份验证（用户名和密码）支持将被淘汰。我们建议您尽快将 SMTP 配置迁移到 App专用 密码。[了解更多有关变更的信息](https://support.google.com/a/answer/14114704?hl=zh-Hans)。
{% endhint %}

**答：**&#x5728; `./bwdata/env/global.override.env` 中配置以下变量：

```systemd
globalSettings__mail__replyToEmail=no-reply@your.domain
globalSettings__mail__smtp__host=smtp.gmail.com
globalSettings__mail__smtp__port=587
globalSettings__mail__smtp__ssl=false
globalSettings__mail__smtp__username=<valid-gmail-username>
globalSettings__mail__smtp__password=<valid-gmail-password>
```

您还需要在 Google 中启用 SMTP 中继。更多信息，请参阅 [Google 文档](https://support.google.com/a/answer/176600?hl=zh-Hans)。

## 高级配置 <a href="#advanced-configuration" id="advanced-configuration"></a>

### 问：如何使用自定义服务器端口？ <a href="#how-do-i-use-custom-server-ports" id="how-do-i-use-custom-server-ports"></a>

**答：**&#x8981;使用非 80 和 443 的自定义端口，请编辑 `./bwdata/config.yml` 中的 `http_port=` 和 `https_port=` 值，然后运行 `./bitwarden.sh rebuild` 命令来重建您的服务器资产。

检查自定义端口值是否已经扩散到 `./bwdata/env/global.override.env` 中。

### 问：如何启用 syslog 日志记录？ <a href="#how-do-i-enable-logging-to-syslog" id="how-do-i-enable-logging-to-syslog"></a>

**答：**&#x44;ocker 的 `syslog` 日志记录驱动程序可与 Bitwarden 的容器配合使用。为了记录到 `syslog`，用户可以使用 Docker 的 `daemon.json` 文件（位于[此处](https://docs.docker.com/engine/logging/drivers/syslog/#usage)）在系统范围内设置 `syslog` 日志记录驱动程序。或者，您可以通过在 `bwdata/docker/docker-compose.override.yml` 文件中配置它来仅为 Bitwarden 容器进行配置，如下所示：

```yaml
services:
  admin:
    logging:
      driver: syslog
      options:
        syslog-address: tcp://192.168.0.42:123
  sso:
    logging:
      driver: syslog
      options:
        syslog-address: tcp://192.168.0.42:123
  identity:
    logging:
      driver: syslog
      options:
        syslog-address: tcp://192.168.0.42:123
  api:
    logging:
      driver: syslog
      options:
        syslog-address: tcp://192.168.0.42:123
  events:
    logging:
      driver: syslog
      options:
        syslog-address: tcp://192.168.0.42:123
```

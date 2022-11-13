# 托管常见问题

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/hosting-faqs/)
{% endhint %}

本文包含了关于**自托管**的常见问题（FAQ）。

## 通用 <a href="#general" id="general"></a>

### 问：我可以托管在哪些平台上？ <a href="#q-what-platforms-can-i-host-on" id="q-what-platforms-can-i-host-on"></a>

**答：**Bitwarden 是一个跨平台的应用程序，使用 Docker Linux 容器进行部署。这意味着 Bitwarden 可以托管在 Linux、macOS 和 Windows 机器上。

你可以在 [Docker 网站](https://www.docker.com/why-docker)上阅读更多关于 Docker 和容器技术的信息。

### 问：我应该如何实现高可用性？ <a href="#q-how-should-i-achieve-high-availability" id="q-how-should-i-achieve-high-availability"></a>

**答：**可以通过将容器的多个实例配置到 Docker Swarm 或 Kubernetes 环境中，和/或将容器引用的数据库连接字符串指向任何 MSSQL 数据库或集群来实现高可用性。然后，你可能会希望对 NGINX 容器进行负载平衡，或者你选择的任何方式来处理前端。

### 问：我需要将哪些 URL 加入白名单？ <a href="#q-do-i-need-to-whitelist-any-urls" id="q-do-i-need-to-whitelist-any-urls"></a>

**答：**要允许服务器**向 Bitwarden 客户端推送通知**，您需要允许以下 URL 通过防火墙：

* `api.bitwarden.com`
* `push.bitwarden.com`

{% hint style="success" %}
如果将这些 URL 加入白名单后在您的环境不起作用，则您不必使用推送通知。
{% endhint %}

### 问：如何备份和还原我的自托管实例？ <a href="#q-how-do-i-backup-and-restore-my-self-hosted-instance" id="q-how-do-i-backup-and-restore-my-self-hosted-instance"></a>

**答：**Bitwarden 每晚会自动备份 `bitwarden-mssql` 数据库容器，以保护您存储的凭据。有关手动备份，或恢复备份的帮助，请参阅[备份您的托管数据](backup-your-hosted-data.md)。

### 问：我的安装 ID 和安装密钥是用来干什么的？ <a href="#q-what-are-my-installation-id-and-installation-key-used-for" id="q-what-are-my-installation-id-and-installation-key-used-for"></a>

**答：**在自托管安装 Bitwarden 时，安装 ID 和密钥用于：

* 注册您的安装，并包含电子邮件，以便我们可以联系您进行重要的安全更新。&#x20;
* 认证到推送中继服务器，以便向 Bitwarden 客户端应用程序推送通知。&#x20;
* 验证付费功能的许可证。&#x20;

从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取安装 ID 和密钥。

**您不应该在多个 Bitwarden 安装中共享您的安装 ID 或安装密钥。**它们应被视为机密。

### 问：如何更改服务器名称？ <a href="#q-how-do-i-change-the-name-of-my-server" id="q-how-do-i-change-the-name-of-my-server"></a>

**答：**在 `./bwdata/config.yml` 中使用你的新服务器名称配置 `url:`，然后运行 `./bitwarden.sh rebuild` 命令重建 `bwdata` 资产。

检查你的服务器名称或 FQDN，确保它们已经扩散到 `./bwdata/env/global.override.env` 中的所有 `globalSettings_baseServiceUri__*` 变量中，并确保你的证书中包含一个带有新服务器 FQDN 的[主题备用名称](https://zh.wikipedia.org/wiki/%E4%B8%BB%E9%A2%98%E5%A4%87%E7%94%A8%E5%90%8D%E7%A7%B0)（SAN）（Subject Alternative Name）。

如果你正在使用 Let's Encrypt 证书，你需要[手动更新你的证书](certificate-options.md#manually-update-a-lets-encrypt-certificate)。

### 问：为什么当运行 `update` 和 `updateself` 显示是最新版本时，管理员门户还会显示有可用的更新？ <a href="#q-why-does-the-admin-portal-show-an-update-available-when-update-and-updateself-show-im-on-the-lates" id="q-why-does-the-admin-portal-show-an-update-available-when-update-and-updateself-show-im-on-the-lates"></a>

**答：**系统管理员门户将在我们发布云服务器后立即显示可用更新，但如[发行说明](../release-notes.md)中所述，自托管服务器更新通常在云服务器后几天才可用。请等待几天，然后再次尝试[更新您的实例](update-your-instance.md)。

## SMTP 配置 <a href="#smtp-configuration" id="smtp-configuration"></a>

### 问：如何设置 SMTP 邮件服务器？ <a href="#q-how-do-i-set-up-an-smtp-mail-server" id="q-how-do-i-set-up-an-smtp-mail-server"></a>

**答：**通过编辑 `./bwdata/env/global.overide.env` 中的所有 `globalSettingsmailsmtp__*` 值，以将您的自托管实例连接到现有的 SMTP 邮件服务器。有关更多信息，请参阅[配置环境变量](configure-environment-variables.md)。

如果你还没有 SMTP 邮件服务器来中继邮件，可以考虑诸如 [Mailgun](https://www.mailgun.com/) 或 [SparkPost](https://www.sparkpost.com/) 等服务，或者使用 Gmail 作为 SMTP 邮件服务器。

### 问：如何将 Gmail 用作 SMTP 邮件服务器？ <a href="#q-how-do-i-use-gmail-as-an-smtp-mail-server" id="q-how-do-i-use-gmail-as-an-smtp-mail-server"></a>

**答：**在 `./bwdata/env/global.override.env` 中配置以下变量：

```systemd
globalSettings__mail__replyToEmail=no-reply@your.domain
globalSettings__mail__smtp__host=smtp.gmail.com
globalSettings__mail__smtp__port=587
globalSettings__mail__smtp__ssl=false
globalSettings__mail__smtp__username=<valid-gmail-username>
globalSettings__mail__smtp__password=<valid-gmail-password>
```

无论你是 Workspace 管理员还是 Gmail 的个人用户，你都需要在 Google 中启用 SMTP 中继。更多信息，请参阅 [Google 文档](https://support.google.com/a/answer/176600?hl=zh-Hans)。

如果你的 Gmail 账户开启了两步验证，你需要生成一个用于 Bitwarden 的应用程序专用密码，并更新到 `./bwdata/env/global.override.env` 的 `globalSettingsmailsmtp__password=` 字段中。

## 高级配置 <a href="#advanced-configuration" id="advanced-configuration"></a>

### 问：如何使用自定义服务器端口？ <a href="#how-do-i-use-custom-server-ports" id="how-do-i-use-custom-server-ports"></a>

**答：**要使用非 80 和 443 的自定义端口，请编辑 `./bwdata/config.yml` 中的 `http_port=` 和 `https_port=` 值，然后运行 `./bitwarden.sh rebuild` 命令来重建你的服务器资产。

检查自定义端口值是否已经扩散到 `./bwdata/env/global.override.env` 中。

### 问：如何将 Bitwarden 添加到系统启动中？ <a href="#q-how-do-i-add-bitwarden-to-system-boot" id="q-how-do-i-add-bitwarden-to-system-boot"></a>

**答：**在将 Bitwarden 添加到系统启动之前，请先完成 [Docker 后安装](install-deploy-guides/install-and-deploy-linux.md#docker-post-installation-linux-only)以设置 bitwarden 专用服务帐户。&#x20;

然后，完成以下步骤：

1、创建 Bitwarden 服务文件：

```systemd
sudo vi bitwarden.service

[Unit]
Description=Bitwarden
Requires=docker.service
After=docker.service

[Service]
Type=oneshot
User=bitwarden
Group=bitwarden
ExecStart=<your-install-directory>/bitwarden.sh start
ExecStop=<your-install-directory>/bitwarden.sh stop
RemainAfterExit=true

[Install]
WantedBy=multi-user.target
```

2、将 Bitwarden 服务文件复制到 systemd：

```shell
sudo cp bitwarden.service /etc/systemd/system/bitwarden.service
```

3、设置 systemd 下的 Bitwarden 服务文件的权限：

```shell
sudo chmod 644 /etc/systemd/system/bitwarden.service
```

4、（可选）重新加载：

```shell
systemctl daemon-reload
```

5、添加服务以使用系统启动来启动 Bitwarden：

```shell
sudo systemctl enable bitwarden.service
```

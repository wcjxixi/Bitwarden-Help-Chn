# Linux 标准部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/install-on-premise-linux/)
{% endhint %}

这篇文章将指导您安装和部署 Bitwarden 到您自己的 Liunx 服务器。Bitwarden 也可以安装和部署在 [Windows](windows-standard-deployment.md) 机器上。请查看 Bitwarden [软件发布支持](../../../security/software-development/software-release-support.md)文档。

## 要求 <a href="#requirements" id="requirements"></a>

<table><thead><tr><th></th><th width="249.33333333333331">最低</th><th>推荐</th></tr></thead><tbody><tr><td>处理器</td><td>x64, 1.4GHz</td><td>x64, 2GHz 双核</td></tr><tr><td>内存</td><td>2GB RAM</td><td>4GB RAM</td></tr><tr><td>存储</td><td>12GB</td><td>25GB</td></tr><tr><td>Docker 版本</td><td>Engine 26+ 以及 Compose <mark style="color:red;"><strong>ª</strong></mark></td><td>Engine 26+ 以及 Compose <mark style="color:red;"><strong>ª</strong></mark></td></tr></tbody></table>

<mark style="color:red;">**ª**</mark> - 下载 Docker Engine 时，Docker Compose 会作为插件自动安装。

{% hint style="success" %}
如果您正在寻找价格实惠的优质供应商，我们推荐 DigitalOcean。[立即开始](https://marketplace.digitalocean.com/apps/bitwarden)或阅读我们[在 DigitalOcean 上的关于 Bitwarden 的博客文章](https://bitwarden.com/blog/digitalocean-marketplace/)。
{% endhint %}

## TL;DR <a href="#tl-dr" id="tl-dr"></a>

> **\[译者注]**：TL;DL - Too long; Don't read，直译为「太长，请不要看」，实际意思为「此文篇幅较长，看此总结」，一般用在比较长篇幅的内容前面，后面跟着一段简短的总结内容。

以下是本文中[安装步骤](linux-standard-deployment.md#installation-procedure)的摘要。本节中的链接将跳转至详细的**安装步骤**部分：

1、[**配置您的域名**](linux-standard-deployment.md#configure-your-domain)。设置您的域名 DNS 记录指向您的主机，并打开主机上的 80 和 443 端口。

2、在您的主机上[**安装 Docker 和 Docker Compose**](linux-standard-deployment.md#install-docker-and-docker-compose)。

3、[**创建一个 Bitwarden 用户和目录**](linux-standard-deployment.md#create-bitwarden-local-user-and-directory)。

4、从 [**https://bitwarden.com/host**](https://bitwarden.com/host) 获取安装 ID 和密钥用于安装过程。更多详细信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)。

5、在您机器上[**安装 Bitwarden**](linux-standard-deployment.md#install-bitwarden)。

6、在 `./bwdata/env/global.override.env` 中调整设置以[**配置您的环境**](linux-standard-deployment.md#post-install-configuration)。

{% hint style="success" %}
至少要配置 `globalSettings__mail__smtp...` 变量以设置用于邀请和验证用户的电子邮件服务器。
{% endhint %}

7、[**启动您的实例**](linux-standard-deployment.md#start-bitwarden)。

8、在网页浏览器中打开您配置的域名来测试您的安装。

9、部署完成后，我们建议定期[备份您的服务器](../../backup-server-data.md)并[检查系统更新](../../update-a-server.md)。

## 安装步骤 <a href="#installation-procedure" id="installation-procedure"></a>

### 配置您的域名 <a href="#configure-your-domain" id="configure-your-domain"></a>

默认情况下，Bitwarden 通过本地主机上的 80（`http`）和 443（`https`）端口提供服务。您应该打开这些端口，以便可以从网络内部和/或外部访问 Bitwarden。如果您愿意，也可以在安装过程中选择使用其他端口。

我们建议配置一个带 DNS 记录的域名（例如，`bitwarden.example.com`）指向您的托管主机，特别是当您通过互联网提供 Bitwarden 服务时。

### 安装 Docker 和 Docker Compose <a href="#install-docker-and-docker-compose" id="install-docker-and-docker-compose"></a>

使用一组 [Docker 容器](https://docs.docker.com/get-started/)在您的机器上部署和运行 Bitwarden。Bitwarden 可以使用任何 Docker 版本或计划运行。评估哪个版本最适合你的安装。

容器的部署是通过 [Docker Compose](https://docs.docker.com/compose/) 来协调的。下载 Docker Engine 时，Docker Compose 会作为插件自动安装。

[下载 Linux 版 Docker Engine](https://docs.docker.com/engine/install/#supported-platforms)。

### 创建 Bitwarden 本地用户和目录 <a href="#create-bitwarden-local-user-and-directory" id="create-bitwarden-local-user-and-directory"></a>

Bitwarden 建议在您的 Linux 服务器上配置一个专用的 `bitwarden` 服务账户，用来安装和运行 Bitwarden。这样做可以将您的 Bitwarden 实例与服务器上运行的其他应用程序隔离开来。

**这些步骤是 Bitwarden 推荐的最佳实践，但不是必须的**。更多信息，请参阅 Docker 的[用于 Linux 的后安装步骤](https://docs.docker.com/engine/install/linux-postinstall/)文档。

1、创建 bitwarden 用户：

```shell
sudo adduser bitwarden
```

2、为 bitwarden 用户设置密码（强密码）：

```shell
sudo passwd bitwarden
```

3、创建 docker 组（如果它不存在）：

```shell
sudo groupadd docker
```

4、将 bitwarden 用户添加到 docker 组：

```shell
sudo usermod -aG docker bitwarden
```

5、创建 bitwarden 目录：

```shell
sudo mkdir /opt/bitwarden
```

6、授予 `/opt/bitwarden` 目录权限：

```shell
sudo chmod -R 700 /opt/bitwarden
```

7、授予 bitwarden 用户对 `/opt/bitwarden` 目录的所有权：

```shell
sudo chown -R bitwarden:bitwarden /opt/bitwarden
```

### 安装 Bitwarden <a href="#install-bitwarden" id="install-bitwarden"></a>

{% hint style="danger" %}
如果[已创建 Bitwarden 用户和目录](linux-standard-deployment.md#create-bitwarden-local-user-and-directory)，请从 `/opt/bitwarden` 目录以 `bitwarden` 用户身份完成以下操作。 **请勿以 root 用户身份安装 Bitwarden**，否则会在安装过程中遇到问题。
{% endhint %}

Bitwarden 提供了一个 Shell 脚本，可以轻松地在 Linux 和 macOS（Bash）或 Windows（PowerShell）上安装。完成以下步骤以使用 shell 脚本安装 Bitwarden：

1、将 Bitwarden 安装脚本（`bitwarden.sh`）下载到您主机上：

```shell
curl -Lso bitwarden.sh "https://func.bitwarden.com/api/dl/?app=self-host&platform=linux" && chmod 700 bitwarden.sh
```

2、运行安装脚本。这将相对于 `bitwarden.sh` 的位置创建 `./bwdata` 目录：

```shell
./bitwarden.sh install
```

3、完成安装程序中的提示：

* **Enter the domain name for your Bitwarden instance（输入您的 Bitwarden 实例的域名）:**\
  通常，此值应该是已配置的 DNS 记录。
*   **Do you want to use Let's Encrypt to generate a free SSL certificate? (y/n)（您想使用 Let's Encrypt 生成免费的 SSL 证书吗？）:**\
    指定 `y` 来使用 Let's Encrypt 生成一个可信的 SSL 证书。您会被提示输入一个电子邮箱地址，以便从 Let's Encrypt 获取到期提醒。更多信息，请参阅[证书选项](../configuration-options/certificate-options.md)。

    或者，指定 `n` 并使用 **Do you have a SSL certificate to use?** 选项。
* **Enter your installation id（输入您的安装 ID）:**\
  通过 [https://bitwarden.com/host](https://bitwarden.com/host) 使用一个有效的电子邮件地址来获取安装 ID。更多详细信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)
*   **Enter your installation key（输入您的安装密钥）:**

    通过 [https://bitwarden.com/host](https://bitwarden.com/host) 使用一个有效的电子邮箱地址来获取安装密钥。更多详细信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)
* **Enter your region (US/EU)（输入您的区域 (US/EU)）：**\
  输入 US 或 EU，具体取决于您将用于许可付费功能的[云端服务器](../../../security/server-geographies.md)，仅适用于您将自托管账户或组织连接到付费订阅的情况。
*   **Do you have a SSL certificate to use? (y/n)（您拥有自己的 SSL 证书吗？）:**\
    如果您已经有自己的 SSL 证书，请指定 `y`，并将必要的文件放在 `/.bwdata/ssl/your.domain` 目录下。您会被问到是否使用受信任的 SSL 证书（y/n）。更多信息，请参阅[证书选项](../configuration-options/certificate-options.md)。

    或者，指定 `n` 并使用 **self-signed SSL certificate?** 选项，这只是为了测试目的而推荐的。
*   **Do you want to generate a self-signed SSL certificate? (y/n)（您想生成一个自签名证书吗？）:**\
    指定 `y` 让 Bitwarden 为您生成一个自签名证书。这个选项只推荐用于测试。更多信息，请参阅[证书选项](../configuration-options/certificate-options.md)。

    如果您指定 `n`，您的实例将不使用 SSL 证书，您需要使用前置 HTTPS 代理来安装，否则 Bitwarden 应用程序将无法正常运行。

### 安装后配置 <a href="#post-install-configuration" id="post-install-configuration"></a>

配置您的环境可能涉及对两个文件进行更改：一个环境变量文件和一个安装文件：

#### 环境变量（必须） <a href="#environment-variables-required" id="environment-variables-required"></a>

安装程序 `Bitwarden.sh` 未配置 Bitwarden 的某些功能。通过编辑位于 `./bwdata/env/global.override.env` 的环境文件来配置这些设置。**至少，您应该替换以下值**：

```systemd
...
globalSettings__mail__smtp__host=<placeholder>
globalSettings__mail__smtp__port=<placeholder>
globalSettings__mail__smtp__ssl=<placeholder>
globalSettings__mail__smtp__username=<placeholder>
globalSettings__mail__smtp__password=<placeholder>
...
adminSettings__admins=
...
```

替换 `globalSettings__mail__smtp...=` 的占位符将配置 SMTP 邮件服务器，该服务器将用于向新用户发送验证电子邮件和向组织发送邀请。将电子邮件地址添加到 `adminSettings__admins=` 将提供对管理门户的访问权限。

编辑 `global.override.env` 后，运行以下命令以使更改生效：

```shell
./bitwarden.sh restart
```

#### 安装文件 <a href="#installation-file" id="installation-file"></a>

Bitwarden 安装脚本使用 `./bwdata/config.yml` 中的设置来生成必要的资产，以用于安装。某些安装场景（例如，在代理服务器后面使用备用端口进行安装）可能需要对 `config.yml` 进行调整，这些调整在标准安装过程中没有提供。

根据需要编辑 `config.yml` 文件，并使用以下命令以使更改生效：

```shell
./bitwarden.sh rebuild
```

### 启动 Bitwarden <a href="#start-bitwarden" id="start-bitwarden"></a>

完成上面的所有步骤后，启动您的 Bitwarden 实例：

```shell
./bitwarden.sh start
```

{% hint style="info" %}
首次启动 Bitwarden 时，可能会花费一些时间，因为它会从 Docker Hub 下载所有镜像。
{% endhint %}

验证所有容器是否正常运行：

```shell
docker ps
```

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3Sq7MaJZ1jaEJUCW44wmwj/0671877450882e4c9f3a8d614bafd734/docker-healthy.png?fm=webp&h=232&q=50&w=1567" %}
显示健康容器的列表
{% endembed %}

恭喜你！Bitwarden 现在已启动并运行在您指定的域名（如上面的示例 `https://bitwarden.example.com`）上了。在网页浏览器中访问网页密码库以确认它是否已经正常工作。

现在，您可以注册一个新账户并登录了。您需要配置 `smtp` 环境变量（请参阅[环境变量](linux-standard-deployment.md#environment-variables)）以验证新账户的电子邮箱地址。

{% hint style="success" %}
部署完成后，我们建议定期[备份您的服务器](../../backup-server-data.md)并[检查系统更新](../../update-a-server.md)。
{% endhint %}

## 脚本命令参考 <a href="#script-commands-reference" id="script-commands-reference"></a>

Bitwarden 的安装脚本（`bitwarden.sh` 或 `bitwarden.ps1`）具有以下可用的命令：

{% hint style="info" %}
PowerShell 用户将以前缀`-`（开关）运行命令。例如`.\bitwarden.ps1 -start`。
{% endhint %}

<table><thead><tr><th width="186">命令</th><th>描述</th></tr></thead><tbody><tr><td>install</td><td>启动安装程序。</td></tr><tr><td>start</td><td>启动所有容器。</td></tr><tr><td>restart</td><td>重新启动所有容器（与 start 相同）。</td></tr><tr><td>stop</td><td>停止所有容器。</td></tr><tr><td>update</td><td>更新所有容器和数据库。</td></tr><tr><td>updatedb</td><td>更新/初始化数据库。</td></tr><tr><td>updaterun</td><td>更新 <code>run.sh</code> 文件。</td></tr><tr><td>updateself</td><td>更新主脚本。</td></tr><tr><td>updateconf</td><td>更新所有容器，而无需重新启动正在运行的实例。</td></tr><tr><td>uninstall</td><td><p>在执行此命令之前，系统会提示您保存数据库文件。选 <code>y</code> 将创建一个包含最新备份的数据库的 tar 文件。</p><p></p><p>停止容器，删除 <code>bwdata</code> 目录及其所有内容，并删除临时卷。执行后，系统会询问您是否还要清除所有 Bitwarden 镜像。</p></td></tr><tr><td>compresslogs</td><td><p>将所有服务器日志或指定日期范围内的服务器日志的压缩包下载到当前目录。</p><p></p><p>例如，使用 <code>./bitwarden.sh compresslogs 20240304 20240305</code> 下载 2024 年 3 月 4 日至 2024 年 3 月 5 日的日志。</p></td></tr><tr><td>renewcert</td><td>续签证书。</td></tr><tr><td>rebuild</td><td>重建从 <code>config.yml</code> 生成的安装资产。</td></tr><tr><td>help</td><td>列出所有命令。</td></tr></tbody></table>

## 下一步 <a href="#next-steps" id="next-steps"></a>

1. 如果您打算自托管一个 Bitwarden 组织，请参阅[自托管组织](../../plan-for-deployment/self-host-an-organization.md)以开始。
2. 如需了解更多信息，请参阅[自托管 FAQ](../../hosting-faqs.md)。

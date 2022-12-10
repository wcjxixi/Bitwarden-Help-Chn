# =安装和部署-Unified(Beta)

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/install-and-deploy-unified-beta/)
{% endhint %}

{% hint style="danger" %}
这是一个测试版，这意味着此部署选项可能不稳定并存在问题。如果您管理 Bitwarden 组织密码库，我们建议使用官方支持的标准部署选项。

[了解如何报告问题](install-and-deploy-unified-beta.md#reporting-issues)。
{% endhint %}

本文将引导您安装和启动 Bitwarden Unified 自托管部署。使用此部署方法可以：

* 通过使用单个 Docker 映像部署 Bitwarden 来简化配置并优化资源使用（CPU、内存）。
* 利用不同的数据库解决方案，例如 MSSQL、PostgreSQL、MySQL/MariaDB。
* 使用替代系统在 ARM 架构上运行，例如 Raspberry Pi 和 NAS 服务器。

## 系统要求 <a href="#system-requirements" id="system-requirements"></a>

Bitwarden Unified 部署要求：

* 至少 200 MB RAM
* 1GB 存储
* Docker Engine 19+

### 安装 Docker <a href="#install-docker" id="install-docker"></a>

Unified 部署使用 [Docker 容器](https://docs.docker.com/get-started/)在您的机器上运行。Unified 部署可以与任何 Docker 版本或计划一起运行。评估哪个版本最适合您的安装。

在继续安装之前在您的计算机上安装 Docker。请参阅以下 Docker 文档以获取帮助：

* [安装 Docker 引擎](https://docs.docker.com/engine/installation/)

## 运行 Bitwarden Unified <a href="#run-bitwarden-unified" id="run-bitwarden-unified"></a>

可以使用 `docker run` 命令（参见[此处](install-and-deploy-unified-beta.md#using-docker-run)）或使用 Docker Compose（参见[此处](install-and-deploy-unified-beta.md#using-docker-compose)）运行 Unified 部署。无论哪种情况，您都需要为容器指定环境变量。

### 指定环境变量 <a href="#specify-environment-variables" id="specify-environment-variables"></a>

运行 Unified 部署需要为容器设置环境变量。可以通过创建一个 `settings.env` 文件来指定环境变量，您可以在我们的 [GitHub 存储库](https://github.com/bitwarden/server/blob/master/docker-unified/settings.env)中找到该文件的示例，或者如果您使用的是 `docker run` 方法，则可以使用 `--env` 标志来指定。几个可选变量可用于更个性化的 Unified 部署体验。有关这些变量的更多详细信息，请参阅[此处](install-and-deploy-unified-beta.md#environment-variables)。

至少为示例 `.env` 文件的 `# Required Settings #` 部分下的变量设置值：

| 变量                    | 描述                                                                              |
| --------------------- | ------------------------------------------------------------------------------- |
| BW\_DOMAIN            | 将 `bitwarden.yourdomain.com` 替换为用于访问 Bitwarden 所使用域名。                           |
| BW\_DB\_PROVIDER      | 您将用于 Bitwarden 服务器的数据库提供程序。可用选项包括 `sqlserver`、`postgresql` 或 `mysql`/`mariadb`。 |
| BW\_DB\_SERVER        | 运行数据库的服务器的名称。                                                                   |
| BW\_DB\_DATABASE      | 您的 Bitwarden 数据库的名称。                                                            |
| BW\_DB\_USERNAME      | 用于访问 Bitwarden 数据库的用户名。                                                         |
| BW\_DB\_PASSWORD      | 用于访问 Bitwarden 数据库的密码。                                                          |
| BW\_INSTALLATION\_ID  | 从 [https://bitwarden.com/host/](https://bitwarden.com/host/) 生成的有效安装 ID。        |
| BW\_INSTALLATION\_KEY | 从 [https://bitwarden.com/host/](https://bitwarden.com/host/) 生成的有效安装密钥。         |

{% hint style="info" %}
与 Bitwarden 标准部署不同，Unified 部署并不是开箱即用的数据库。您可以使用现有数据库，也可以创建一个新数据库，如[本示例中](install-and-deploy-unified-beta.md#using-docker-compose)所述，在这两种情况下，您都必须在此处记录的 `BW_DB_...` 变量中输入有效信息。

使用非 MSSQL 数据库提供程序可能会导致性能问题，对这些平台的支持将在整个测试版中继续进行。请使用[此问题模板](https://github.com/bitwarden/server/issues/new?assignees=\&labels=bug%2Cbw-unified-deploy\&template=bw-unified.yml)报告与您的 Bitwarden Unified 部署相关的任何内容，并查看[此页面](https://github.com/bitwarden/server/issues/2480)以跟踪已知问题或加入讨论。
{% endhint %}

### 使用 Docker 运行 <a href="#using-docker-run" id="using-docker-run"></a>

可以使用 `docker run` 命令运行 Unified 部署，如下示例：

```shell
docker run -d --name bitwarden -v ./bwdata/:/etc/bitwarden -p 80:80  --env-file settings.env bitwarden/self-host:beta
```

上面的命令有几个 `docker run` 命令必需的选项，包括：

| 名称，简写          | 描述                                                                                                                                                                                                                                                                                                                                                     |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| --detach , -d  | 在后台运行容器并输出容器 ID。                                                                                                                                                                                                                                                                                                                                       |
| --name         | 为容器提供一个名称。该示例中使用的是 `bitwarden`。                                                                                                                                                                                                                                                                                                                        |
| --volume , -v  | 绑定挂载卷。至少挂载 `/etc/bitwarden`。                                                                                                                                                                                                                                                                                                                           |
| --publish , -p | 将容器端口映射到主机。该示例显示映射了端口 80 。配置 SSL 时需要端口 443。                                                                                                                                                                                                                                                                                                            |
| --env-file     | Path of the [file to read environment variables from](https://bitwarden.com/help/install-and-deploy-unified-beta/#specify-environment-variables). Alternatively, use the `--env` flag to declare environment variables inline ([learn more](https://docs.docker.com/engine/reference/commandline/run/#set-environment-variables--e---env---env-file)). |

### 使用 Docker Compose <a href="#using-docker-compose" id="using-docker-compose"></a>

## 更新您的服务器 <a href="#update-your-server" id="update-your-server"></a>

## 环境变量 <a href="#environment-variables" id="environment-variables"></a>

#### SSL

#### 服务 <a href="#services" id="services"></a>

#### 电子邮件 <a href="#mail" id="mail"></a>

#### Yubico API (YubiKey) <a href="#yubico-api" id="yubico-api"></a>

#### 其他 <a href="#other" id="other"></a>

### 重新启动容器 <a href="#restart-the-container" id="restart-the-container"></a>

## 内存使用 <a href="#memory-usage" id="memory-usage"></a>

## 报告问题 <a href="#reporting-issues" id="reporting-issues"></a>

## 附加资源 <a href="#additional-resources" id="additional-resources"></a>

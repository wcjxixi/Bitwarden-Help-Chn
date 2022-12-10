# =安装和部署-Unified(Beta)

{% hint style="success" %}
删除 Docker 容器：对应的[官方文档地址](https://bitwarden.com/help/install-and-deploy-unified-beta/)
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

### 使用 docker run <a href="#using-docker-run" id="using-docker-run"></a>

可以使用 `docker run` 命令运行 Unified 部署，如下示例：

```shell
docker run -d --name bitwarden -v ./bwdata/:/etc/bitwarden -p 80:80  --env-file settings.env bitwarden/self-host:beta
```

上面的命令有几个 `docker run` 命令必需的选项，包括：

| 名称，缩写          | 描述                                                                                                                                                                                                                                |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --detach , -d  | 在后台运行容器并输出容器 ID。                                                                                                                                                                                                                  |
| --name         | 为容器提供一个名称。该示例中使用的是 `bitwarden`。                                                                                                                                                                                                   |
| --volume , -v  | 绑定挂载卷。至少挂载 `/etc/bitwarden`。                                                                                                                                                                                                      |
| --publish , -p | 将容器端口映射到主机。该示例显示映射了 `80` 端口。配置 SSL 时需要使用 `443` 端口。                                                                                                                                                                                |
| --env-file     | [要从中读取环境变量的文件](install-and-deploy-unified-beta.md#specify-environment-variables)的路径。或者，在同一行中使用 `--env` 标志声明环境变量（[了解更多](https://docs.docker.com/engine/reference/commandline/run/#set-environment-variables--e---env---env-file)）。 |

运行此命令后，验证容器是否正在运行且运行状况良好：

```shell
docker ps
```

恭喜！您的 Unified 部署现已启动并运行在 `https://your.domain.com` 上了。在您的浏览器中访问网络密码库以确认它正在运行。您现在可以注册一个新帐户并登录。

### 使用 Docker Compose <a href="#using-docker-compose" id="using-docker-compose"></a>

使用 Docker Compose 运行 Unified 部署需要 Docker Compose 版本 1.24+。要使用 Docker compose 运行 Unified 部署，请创建一个 `docker-compose.yml` 文件，例如：

```javascript
---
version: "3.8"

services:
  bitwarden:
    depends_on:
      - db
    env_file:
      - settings.env
    image: bitwarden/self-host:beta
    restart: always
    ports:
      - "80:80"
    volumes:
      - bitwarden:/etc/bitwarden

  db:
    environment:
      MARIADB_USER: "bitwarden"
      MARIADB_PASSWORD: "super_strong_password"
      MARIADB_DATABASE: "bitwarden_vault"
      MARIADB_RANDOM_ROOT_PASSWORD: "true"
    image: mariadb:10
    restart: always
    volumes:
      - data:/var/lib/mysql

volumes:
  bitwarden:
  data:
```

在 `docker-compose.yml` 文件中，确保任何所需的配置包含：

* 日志和 Bitwarden 数据的映射卷。
* 映射端口。
* 配置数据库镜像。ª

ª 仅在 `docker-compose.yml` 中设置数据库，如上例所示，如果您想**创建一个新的数据库服务器**以与 Bitwarden 一起使用。 用于 MySQL、MSSQL 和 PostgreSQL 的示例配置包含在我们的[示例文件](https://github.com/bitwarden/server/blob/master/docker-unified/docker-compose.yml)中。

创建 `docker-compose.yml` 和 `settings.env` 文件后，运行以下命令启动 Unified 服务器：

```shell
docker compose up -d
```

验证所有容器是否正常运行：

```shell
docker ps
```

恭喜！您的 Unified 部署现已启动并运行在 `https://your.domain.com` 上了。在您的浏览器中访问网络密码库以确认它正在运行。您现在可以注册一个新帐户并登录。

## 更新您的服务器 <a href="#update-your-server" id="update-your-server"></a>

要更新您的 Unified 部署：

{% tabs %}
{% tab title="docker run 更新" %}
1、停止正在运行的 Docker 容器：

```bash
docker stop bitwarden
```

2、移除 Docker 容器：

```bash
docker rm bitwarden
```

3、运行以下命令来拉取最新的 Bitwarden Unified 镜像：

```bash
docker pull bitwarden/self-host:beta
```

4、再次运行 Docker 容器：

```bash
docker run -d --name bitwarden -v ./bwdata/:/etc/bitwarden -p 80:80 --env-file settings.env bitwarden/self-host:beta
```
{% endtab %}

{% tab title="Docker Compose 更新" %}
1、停止正在运行的 Docker 容器：

```bash
docker compose down
```

2、运行以下命令来拉取最新的 Bitwarden Unified 镜像：

```bash
docker compose pull
```

3、重新创建任何需要更新的容器：

```bash
docker compose up -d
```

4、验证容器是否正在运行：

```bash
docker compose ps
```
{% endtab %}
{% endtabs %}

## 环境变量 <a href="#environment-variables" id="environment-variables"></a>

默认情况下，Unified 部署可以在不具备一些列标准 Bitwarden 服务的情况下运行。这允许增加 Unified 部署的定制和优化。通过编辑各种环境变量来配置这些服务和更多可选设置。

{% hint style="info" %}
每当您更改环境变量后，都需要重新创建 Docker 容器。在[这里](install-and-deploy-unified-beta.md#restart-the-container)了解更多。
{% endhint %}

#### SSL

使用这些值更改证书设置。有关更多信息，请参阅[证书选项](../certificate-options.md)。

| 变量                  | 描述                                                                                                                                                                            |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BW\_ENABLE\_SSL     | <p>使用 SSL/TLS。<code>true</code>/<code>false</code>。默认为 <code>false</code>。</p><p></p><p>Bitwarden 需要 SSL 才能正常运行。如果您没有使用在 Bitwarden 容器中配置的 SSL，您应该在 Bitwarden 前面使用 SSL 代理。</p> |
| BW\_SSL\_CERT       | SSL 证书文件的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `ssl.crt`。 如果您希望使用现有证书，在[此处](../certificate-options.md#use-an-existing-ssl-certificate)了解更多信息。                               |
| BW\_SSL\_KEY        | SSL 密钥文件的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `ssl.key`。 如果您希望使用现有证书，在[此处](../certificate-options.md#use-an-existing-ssl-certificate)了解更多信息。                               |
| BW\_ENABLE\_SSL\_CA | 使用具有证书颁发机构 (CA) 支持服务 的 SSL。`true`/`false`。默认为 `false`。                                                                                                                        |
| BW\_SSL\_CA\_CERT   | SSL CA 证书的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `ca.crt`。                                                                                                                   |
| BW\_ENABLE\_SSL\_DH | 使用具有Diffie-Hellman 密钥交换的 SSL。`true`/`false`。默认为 `false`。                                                                                                                      |
| BW\_SSL\_DH\_CERT   | Diffie-Hellman 参数文件的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `dh.pem`。                                                                                                         |
| BW\_SSL\_PROTOCOLS  | NGINX 使用的 SSL 版本。建议默认留空。[了解更多](https://wiki.mozilla.org/Security/Server\_Side\_TLS)。                                                                                          |
| BW\_SSL\_CIPHERS    | NGINX 使用的 SSL 密码套件。建议默认留空。[了解更多](https://wiki.mozilla.org/Security/Server\_Side\_TLS)。                                                                                        |

#### 服务 <a href="#services" id="services"></a>

通过更改以下值，可以针对特定用例（例如企业或团队需求）启用或禁用其他服务：

| 变量                                | 描述   |
| --------------------------------- | ---- |
| BW\_ENABLE\_ADMIN                 | **** |
| BW\_ENABLE\_API                   | **** |
| BW\_ENABLE\_EVENTS                |      |
| BW\_ENABLE\_ICONS                 |      |
| BW\_ENABLE\_IDENTITY              | **** |
| BW\_ENABLE\_NOTIFICATIONS         |      |
| BW\_ENABLE\_SCIM                  |      |
| BW\_ENABLE\_SSO                   |      |
| BW\_ICONS\_PROXY\_TO\_CLOUD       |      |
| BW\_ENABLE\_KEY\_CONNECTOR        |      |
| BW\_KEY\_CONNECTOR\_INTERNAL\_URL |      |

#### 电子邮件 <a href="#mail" id="mail"></a>

为您的 Unified 部署配置 SMTP 设置。将您选择的邮件 SMTP 提供商的信息复制到以下字段中：

| 变量                                         | 描述 |
| ------------------------------------------ | -- |
| globalSettings\_\_mail\_\_replyToEmail     |    |
| globalSettings\_\_mail\_\_smtp\_\_host     |    |
| globalSettings\_\_mail\_\_smtp\_\_port     |    |
| globalSettings\_\_mail\_\_smtp\_\_ssl      |    |
| globalSettings\_\_mail\_\_smtp\_\_username |    |
| globalSettings\_\_mail\_\_smtp\_\_password |    |

#### Yubico API (YubiKey) <a href="#yubico-api" id="yubico-api"></a>

| 变量                               | 描述 |
| -------------------------------- | -- |
| globalSettings\_yubico\_clientId |    |
| globalSettings\_yubico\_key      |    |

#### 其他 <a href="#other" id="other"></a>

| 变量                                        | 描述 |
| ----------------------------------------- | -- |
| globalSettings\_\_disableUserRegistration |    |
| globalSettings\_\_hibpApiKey              |    |
| adminSettings\_\_admins                   |    |
| BW\_REAL\_IPS                             |    |
| BW\_CSP                                   |    |

### 重新启动容器 <a href="#restart-the-container" id="restart-the-container"></a>

要在更改环境变量后重新启动 Docker 容器，请从 Bitwarden Unified 部署目录运行以下命令：

{% tabs %}
{% tab title="Docker run" %}
1、停止正在运行的 Docker 容器：

```
docker stop bitwarden
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## 内存使用 <a href="#memory-usage" id="memory-usage"></a>

默认情况下，Bitwarden 容器消耗的内存，通常超过运行所需的最低内存。对于内存敏感的环境，您可以使用 docker `-m` 或 `--memory=` 来限制 Bitwarden 容器的内存使用。

| 名称，缩写         | 描述                                                                                                                                                             |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --memory=, -m | 容器可以使用的最大内存量。Bitwarden 至少需要 200M。请参阅 [Docker 文档](https://docs.docker.com/config/containers/resource\_constraints/#limit-a-containers-access-to-memory)以了解更多信息。 |

要使用 Docker Compose 控制内存使用，请使用 `mem_limit` 键：

```javascript
services:
  bitwarden:
    env_file:
      - settings.env
    image: bitwarden/self-host:beta
    restart: always
    mem_limit: 200m
```

## 报告问题 <a href="#reporting-issues" id="reporting-issues"></a>

虽然 Bitwarden Unified 部署仍处于测试版，但我们鼓励您通过 GitHub 报告问题并提供反馈。请使用[此问题模板](https://github.com/bitwarden/server/issues/new?assignees=\&labels=bug%2Cbw-unified-deploy\&template=bw-unified.yml)报告与您的 Bitwarden Unified 部署相关的任何内容，并查看[此页面](https://github.com/bitwarden/server/issues/2480)以跟踪已知问题或加入讨论。

## 附加资源 <a href="#additional-resources" id="additional-resources"></a>

有关 Bitwarden 标准自托管部署的更多信息，请参阅：

* [安装和部署 - Linux](install-and-deploy-linux.md)
* [安装和部署 - Windows](install-and-deploy-windows.md)
* [安装和部署 - 手动](install-and-deploy-manually.md)

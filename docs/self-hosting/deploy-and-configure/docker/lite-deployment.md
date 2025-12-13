# Lite 部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/install-and-deploy-unified-beta/)
{% endhint %}

{% hint style="danger" %}
~~该解决方案处于测试阶段，仅供个人使用。商业计划应使用官方支持的标准部署选项。~~

~~虽然 Bitwarden Unified 自托管部署还处于测试阶段，但 Unified 安装不会设置自动升级过程来获取最新的可用镜像。Bitwarden 建议，在升级之前，应留出一些时间让发布的版本趋于稳定。~~
{% endhint %}

> **\[译者注]**：测试阶段叫做「Bitwarden Unified」，现在更名为「Bitwarden Lite」，即 Bitwarden 最小化部署。

{% hint style="info" %}
Bitwarden Lite 适合个人和家庭实验室使用，不适用于商用环境。商用环境应使用[标准部署选项](../../plan-for-deployment/self-host-bitwarden.md)之一。
{% endhint %}

本文将指导您安装和启动 [Bitwarden Lite](https://github.com/bitwarden/self-host/tree/main/bitwarden-lite)。使用此部署方式可以：

* 通过使用单个 Docker 映像部署 Bitwarden 来简化配置并优化资源使用（CPU、内存）。
* 利用不同的数据库解决方案，例如 MSSQL、PostgreSQL、SQLite 以及 MySQL/MariaDB。当前只有 Lite 部署可以使用这些数据库，标准部署需要 MSSQL。
* 作为替代系统运行在 ARM 架构上，例如 Raspberry Pi 和 NAS 服务器。

## 要求 <a href="#requirements" id="requirements"></a>

Bitwarden Lite 部署要求：

* RAM：至少 200 MB
* 存储：至少 1 GB
* Docker Engine：版本 26+

## 设置 <a href="#setup" id="setup"></a>

在运行 Bitwarden Lite 服务器之前，请安装 Docker、设置 `settings.env` 文件并决定数据库配置：

### 安装 Docker <a href="#install-docker" id="install-docker"></a>

Bitwarden Lite 使用 [Docker 容器](https://docs.docker.com/get-started/)运行在您的机器上。Lite 可以与任何 Docker 版本或计划一起运行。请评估哪个版本最适合您的安装。**在继续安装之前需要在您的计算机上安装 Docker**。请参阅以下 Docker 文档获取帮助：

* [安装 Docker Engine](https://docs.docker.com/engine/installation/)

### 所需的环境变量 <a href="#required-environment-variables" id="required-environment-variables"></a>

可以通过创建一个 `settings.env` 文件来指定环境变量，您可以在我们的 [GitHub 存储库](https://github.com/bitwarden/server/blob/master/docker-unified/settings.env)中找到该文件的示例，或者如果您使用的是 `docker run` 方式，则可以使用 `--env` 标志来指定。至少为示例 `.env` 文件的 `# Required Settings #` 部分下的变量设置值。

{% hint style="success" %}
除了此表中列出的变量之外，还有更多可选的环境变量可用。
{% endhint %}

| 变量                    | 描述                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------- |
| BW\_DOMAIN            | 将 `bitwarden.yourdomain.com` 替换为用于访问 Bitwarden 所使用域名。                                 |
| BW\_DB\_PROVIDER      | 您将用于 Bitwarden 服务器的数据库提供程序。可用选项包括 `sqlserver`、`postgresql` 或 `mysql`/`mariadb`。       |
| BW\_DB\_SERVER        | 运行数据库的服务器的名称。                                                                         |
| BW\_DB\_DATABASE      | 您的 Bitwarden 数据库的名称。                                                                  |
| BW\_DB\_USERNAME      | 用于访问 Bitwarden 数据库的用户名。                                                               |
| BW\_DB\_PASSWORD      | 用于访问 Bitwarden 数据库的密码。                                                                |
| BW\_DB\_FILE          | 仅 `sqlite` 需要，如果您想指定数据库文件的路径。如果不指定，`sqlite` 会自动在 `/etc/bitwarden` 卷下创建 `vault.db` 文件。 |
| BW\_INSTALLATION\_ID  | 从 [https://bitwarden.com/host/](https://bitwarden.com/host/) 生成的有效安装 ID。              |
| BW\_INSTALLATION\_KEY | 从 [https://bitwarden.com/host/](https://bitwarden.com/host/) 生成的有效安装密钥。               |

### 数据库示例 <a href="#database-examples" id="database-examples"></a>

与标准 Bitwarden 部署不同，Lite 并不附带开箱即用的数据库。您可以使用现有数据库，也可以创建新数据库。您需要在 `settings.env` 文件或 `--env` 标志中包含哪些 `# Required Settings #` 将取决于您使用的受支持的数据库提供程序：

{% tabs %}
{% tab title="MySQL/MariaDB" %}
MySQL 或 MariaDB 数据库需要以下变量：

```systemd
# Database
BW_DB_PROVIDER=mysql
BW_DB_SERVER=db
BW_DB_DATABASE=bitwarden_vault
BW_DB_USERNAME=bitwarden
BW_DB_PASSWORD=super_strong_password
```
{% endtab %}

{% tab title="MSSQL" %}
MSSQL 数据库需要以下变量：

```systemd
# Database
BW_DB_PROVIDER=sqlserver
BW_DB_SERVER=db
BW_DB_DATABASE=bitwarden_vault
BW_DB_USERNAME=bitwarden
BW_DB_PASSWORD=super_strong_password
```
{% endtab %}

{% tab title="SQLite" %}
SQLite 数据库需要以下变量：

```systemd
# Database
BW_DB_PROVIDER=sqlite
BW_DB_FILE=/path/to/.db
```

指定 `sqlite` 值将自动在 `/etc/bitwarden` 卷中创建 `vault.db` 文件。只有在您想要指定不同数据库文件的路径时，才需要指定 `BW_DB_FILE`。
{% endtab %}

{% tab title="PostgreSQL" %}
PostgreSQL 数据库需要以下变量：

```systemd
# Database
BW_DB_PROVIDER=postgresql
BW_DB_SERVER=db
BW_DB_DATABASE=bitwarden_vault
BW_DB_USERNAME=bitwarden
BW_DB_PASSWORD=super_strong_password
```
{% endtab %}
{% endtabs %}

## 运行服务器 <a href="#run-the-server" id="run-the-server"></a>

可以使用 `docker run` 命令或使用 Docker Compose 运行 Lite 部署。无论哪种情况，请确保您已设置环境变量并使数据库可用，然后再继续。

{% tabs %}
{% tab title="Docker run" %}
可以使用 `docker run` 命令运行 Lite 部署，如下示例：

```shell
docker run -d --name bitwarden -v ./bwdata/:/etc/bitwarden -p 80:80  --env-file settings.env bitwarden/self-host:beta
```

使用 `docker run` 命令运行服务器有几个**必需**的选项，包括：

| 名称，缩写          | 描述                                                                                                                                                                                                                |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --detach , -d  | 在后台运行容器并输出容器 ID。                                                                                                                                                                                                  |
| --name         | 为容器提供一个名称。该示例中使用的是 `bitwarden`。                                                                                                                                                                                   |
| --volume , -v  | 绑定挂载卷。至少挂载 `/etc/bitwarden`。                                                                                                                                                                                      |
| --publish , -p | 将容器端口映射到主机。该示例显示映射了 `80:8080` 端口。配置 SSL 时需要使用 `443` 端口。                                                                                                                                                           |
| --env-file     | [要从中读取环境变量的文件](lite-deployment.md#specify-environment-variables)的路径。或者，在同一行中使用 `--env` 标志声明环境变量（[了解更多](https://docs.docker.com/engine/reference/commandline/run/#set-environment-variables--e---env---env-file)）。 |

运行此命令后，验证容器是否正在运行且运行状况良好：

```shell
docker ps
```

恭喜！Bitwarden Lite 现已启动并运行在 `https://your.domain.com` 上了。在您的浏览器中访问网页密码库以确认它正在运行。您现在可以注册一个新账户并登录了。
{% endtab %}

{% tab title="Docker Compose" %}
使用 Docker Compose 运行 Lite 部署要求 Docker Compose 版本 1.24+。要使用 Docker compose 运行 Lite 部署，请创建一个 `docker-compose.yml` 文件，例如：

```yaml
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
* 配置数据库镜像。<mark style="color:red;">**ª**</mark>

<mark style="color:red;">**ª**</mark> - 仅在 `docker-compose.yml` 中设置数据库，如上例所示，如果您想**创建一个新的数据库服务器**以与 Bitwarden 一起使用。 用于 MySQL、MSSQL 和 PostgreSQL 的示例配置包含在我们的[示例文件](https://github.com/bitwarden/server/blob/master/docker-unified/docker-compose.yml)中。

创建 `docker-compose.yml` 和 `settings.env` 文件后，运行以下命令启动 Lite 服务器：

```shell
docker compose up -d
```

验证所有容器是否正常运行：

```shell
docker ps
```

恭喜！Bitwarden Lite 现已启动并运行在 `https://your.domain.com` 上了。在您的浏览器中访问网页密码库以确认它正在运行。您现在可以注册一个新账户并登录了。
{% endtab %}
{% endtabs %}

### 更新或重启服务器 <a href="#update-or-restart-the-server" id="update-or-restart-the-server"></a>

让您的 Bitwarden Lite 服务器保持最新非常重要。与运行服务器一样，您可以使用 `docker run` 命令或 Docker Compose 来更新它：

{% tabs %}
{% tab title="Docker run" %}
{% hint style="success" %}
如果您要重新启动而不是更新服务器，例如在更改环境变量后，请跳过要求您拉取最新 Bitwarden Lite 映像的步骤。
{% endhint %}

要更新服务器：

1、停止正在运行的 Docker 容器：

```bash
docker stop bitwarden
```

2、移除 Docker 容器：

```bash
docker rm bitwarden
```

3、拉取最新的 Bitwarden Lite 镜像：

```bash
docker pull ghcr.io/bitwarden/lite
```

4、重新启动服务器：

```bash
docker run -d --name bitwarden -v /$(pwd)/bwdata/:/etc/bitwarden -p 80:8080 --env-file settings.env ghcr.io/bitwarden/lite
```
{% endtab %}

{% tab title="Docker Compose" %}
{% hint style="success" %}
如果您要重新启动而不是更新服务器，例如在更改环境变量后，请跳过要求您拉取最新 Bitwarden Lite 映像的步骤。
{% endhint %}

要更新服务器：

1、停止正在运行的 Docker 容器：

```bash
docker compose down
```

2、拉取最新的 Bitwarden Lite 镜像：

```bash
docker compose pull
```

3、重新启动服务器：

```bash
docker compose up -d
```
{% endtab %}
{% endtabs %}

## 可选环境变量 <a href="#optional-environment-variables" id="optional-environment-variables"></a>

默认情况下，Bitwarden Lite 可以在停用某些可用服务的情况下运行。这些服务以及许多其他服务器特性可以选择使用您的 `settings.env` 文件或 `--env` 标志来激活和自定义：

{% hint style="success" %}
每当更改环境变量时，您都需要重新启动服务器才能使更改生效。
{% endhint %}

### 服务 <a href="#services" id="services"></a>

可以使用以下变量激活或停用附加服务：

| 变量                          | 描述                                                                                                                                                 |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| BW\_ENABLE\_ADMIN           | <p><strong>不要禁用此服务</strong>。</p><p>在<a href="../../system-administrator-portal.md">此处</a>了解有关管理面板功能的更多信息。默认为 <code>true</code>。</p>                |
| BW\_ENABLE\_API             | **不要禁用此服务**。默认为 `true`。                                                                                                                            |
| BW\_ENABLE\_EVENTS          | 为团队和企业事件监控启用或禁用 Bitwarden 事件日志。默认为 `false`。                                                                                                        |
| BW\_ENABLE\_ICONS           | 启用或禁用登录项目 URI 设置的 Bitwarden 品牌图标。在[此处](../../../security/data/website-icons.md)了解更多。默认为 `true`。                                                    |
| BW\_ENABLE\_IDENTITY        | **不要禁用此服务**。默认为 `true`。                                                                                                                            |
| BW\_ENABLE\_NOTIFICATIONS   | 当使用设备登录、移动端密码库同步等时，启用或禁用用于接收移动设备推送通知的通知服务。默认为 `true`。                                                                                              |
| BW\_ENABLE\_SCIM            | 为企业组织启用或禁用 SCIM。默认为 `false`。                                                                                                                       |
| BW\_ENABLE\_SSO             | 为企业组织启用或禁用 SSO 服务。默认为 `false`。                                                                                                                     |
| BW\_ICONS\_PROXY\_TO\_CLOUD | <p>启用此服务将代理图标服务请求以通过云服务进行操作，以降低系统内存负载。</p><p>如果选择使用此设置，则应将 <code>BW_ENABLE_ICONS</code> 设置为 <code>false</code> 以减少容器负载。默认为 <code>false</code>。</p> |

### 证书 <a href="#certificates" id="certificates"></a>

使用这些变量来更改证书设置：

| 变量                  | 描述                                                                                                                                                                            |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BW\_ENABLE\_SSL     | <p>使用 SSL/TLS。<code>true</code>/<code>false</code>。默认为 <code>false</code>。</p><p></p><p>Bitwarden 需要 SSL 才能正常运行。如果您没有使用在 Bitwarden 容器中配置的 SSL，您应该在 Bitwarden 前面使用 SSL 代理。</p> |
| BW\_SSL\_CERT       | SSL 证书文件的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `ssl.crt`。 如果您希望使用现有证书，在[此处](../configuration-options/certificate-options.md#use-an-existing-ssl-certificate)了解更多信息。         |
| BW\_SSL\_KEY        | SSL 密钥文件的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `ssl.key`。 如果您希望使用现有证书，在[此处](../configuration-options/certificate-options.md#use-an-existing-ssl-certificate)了解更多信息。         |
| BW\_ENABLE\_SSL\_CA | 使用具有证书颁发机构 (CA) 支持服务 的 SSL。`true`/`false`。默认为 `false`。                                                                                                                        |
| BW\_SSL\_CA\_CERT   | SSL CA 证书的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `ca.crt`。                                                                                                                   |
| BW\_ENABLE\_SSL\_DH | 使用具有Diffie-Hellman 密钥交换的 SSL。`true`/`false`。默认为 `false`。                                                                                                                      |
| BW\_SSL\_DH\_CERT   | Diffie-Hellman 参数文件的名称。该文件必须位于容器内的 `/etc/bitwarden` 目录中。默认为 `dh.pem`。                                                                                                         |
| BW\_SSL\_PROTOCOLS  | NGINX 使用的 SSL 版本。建议默认留空。[了解更多](https://wiki.mozilla.org/Security/Server_Side_TLS)。                                                                                            |
| BW\_SSL\_CIPHERS    | NGINX 使用的 SSL 密码套件。建议默认留空。[了解更多](https://wiki.mozilla.org/Security/Server_Side_TLS)。                                                                                          |

{% hint style="info" %}
如果您使用的是现有的 SSL 证书，则必须在 `settings.env` 中启用相应的 SSL 选项。SSL 文件必须存储在 `/etc/bitwarden` 中，可以在 `docker-compose.yml` 文件中引用。这些文件必须与 `settings.env` 中配置的名称一致。

如果启用了 SSL，且预期位置 (`/etc/bitwarden`) 中不存在证书文件，默认情况下会生成自签名证书。
{% endhint %}

### SMTP

使用这些变量来设置或更改服务器的 SMTP 提供程序：

| 变量                                         | 描述                                                                                             |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------- |
| globalSettings\_\_mail\_\_replyToEmail     | 输入服务器的回复电子邮箱。                                                                                  |
| globalSettings\_\_mail\_\_smtp\_\_host     | 输入 SMTP 服务器的主机域名。                                                                              |
| globalSettings\_\_mail\_\_smtp\_\_port     | 输入来自 SMTP 主机的端口号。                                                                              |
| globalSettings\_\_mail\_\_smtp\_\_ssl      | <p>如果您的 SMTP 主机使用 SSL，请输入 <code>true</code>。<br>如果您的主机使用 TLS 服务，请将值设置为 <code>false</code>。</p> |
| globalSettings\_\_mail\_\_smtp\_\_username | 输入 SMTP 用户名。                                                                                   |
| globalSettings\_\_mail\_\_smtp\_\_password | 输入 SMTP 密码。                                                                                    |

### 端口 <a href="#ports" id="ports"></a>

使用这些变量来配置用于流量的端口：

| 变量              | 描述                           |
| --------------- | ---------------------------- |
| BW\_PORT\_HTTP  | 更改用于 HTTP 流量的端口。默认为 `8080`。  |
| BW\_PORT\_HTTPS | 更改用于 HTTPS 流量的端口。默认为 `8443`。 |

### Yubico API <a href="#yubico-api" id="yubico-api"></a>

使用这些变量连接 Yubico Web 服务：

| 变量                               | 描述                                                                                                         |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| globalSettings\_yubico\_clientId | <p>替换从 Yubico Key 获取的 ID 值。</p><p>在<a href="https://upgrade.yubico.com/getapikey/">此处</a>注册 Yubico 密钥。</p> |
| globalSettings\_yubico\_key      | 输入从 Yubico 获取的密钥值。                                                                                         |

### 其他 <a href="#miscellaneous" id="miscellaneous"></a>

使用这些变量来配置 Bitwarden lite 服务器的其他特征：

| 变量                                        | 描述                                                                                                                       |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| globalSettings\_\_disableUserRegistration | 启用或禁用用户帐户注册功能。                                                                                                           |
| globalSettings\_\_hibpApiKey              | 输入 Have I Been Pwnd 提供的 API 密钥。在[此处](https://haveibeenpwned.com/API/Key)注册以获取 API 密钥。                                    |
| adminSettings\_\_admins                   | 输入管理员电子邮箱地址。                                                                                                             |
| BW\_REAL\_IPS                             | 在 `nginx.conf` 中以逗号分隔列表定义真实 IP。用于定义转发客户端 IP 地址的代理服务器。[了解更多](https://nginx.org/en/docs/http/ngx_http_realip_module.html)。 |
| BW\_CSP                                   | 内容安全策略参数。重新配置此参数可能会破坏功能。更改此参数，您将负责维护此值。                                                                                  |
| BW\_DB\_PORT                              | 为数据库流量指定自定义端口。如果未指定，默认端口将取决于您选择的数据库提供程序。                                                                                 |

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

### 内存使用 <a href="#memory-usage" id="memory-usage"></a>

默认情况下，Bitwarden 容器消耗的内存，通常超过运行所需的最低内存。对于内存敏感的环境，您可以使用 docker `-m` 或 `--memory=` 来限制 Bitwarden 容器的内存使用。

| 名称，缩写         | 描述                                                                                                                                                            |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| --memory=, -m | 容器可以使用的最大内存量。Bitwarden 至少需要 200M。请参阅 [Docker 文档](https://docs.docker.com/config/containers/resource_constraints/#limit-a-containers-access-to-memory)以了解更多信息。 |

要使用 Docker Compose 控制内存使用，请使用 `mem_limit` 键：

```yaml
services:
  bitwarden:
    env_file:
      - settings.env
    image: bitwarden/self-host:beta
    restart: always
    mem_limit: 200m
```

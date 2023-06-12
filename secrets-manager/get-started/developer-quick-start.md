# 开发者快速入门

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/developer-quick-start/)
{% endhint %}

Bitwarden Secrets Manager 使开发人员、DevOps 和网络安全团队能够大规模集中存储、管理和部署机密。[Secrets Manager CLI](../developer-tools/secrets-manager-cli.md) 是您通过经身份验证的[服务账户](../your-secrets/service-accounts.md)将[机密](../your-secrets/secrets.md)注入应用程序和基础设施的主要工具。

在本文中，我们将通过查看几种检索存储在密码库中的数据库凭据以在容器运行时注入 [Bitwarden Unified](../../self-hosting/install-and-deploy-guides/install-and-deploy-unified-beta.md) Docker 镜像的方式来演示 Secrets Manager CLI 的使用。

如果您还没有阅读 [Secrets Manager 快速入门](secrets-manager-quick-start.md)文章，建议您在继续之前先阅读。

## 基础教程 <a href="#basic-tutorial" id="basic-tutorial"></a>

在这个最简单的示例中，您将获取存储在密码库中的数据库凭据，并将它们作为临时环境变量存储在 Linux 系统上。存储后，您将在运行时将它们注入 `docker run` 命令中。为此，您需要安装：

* Bitwarden [Secrets Manager CLI](../developer-tools/secrets-manager-cli.md)
* [Docker](https://docs.docker.com/get-docker/)
* [像 jq 这样的命令行 JSON 处理器](https://stedolan.github.io/jq/)

### 身份验证 <a href="#authenticate" id="authenticate"></a>

可以使用为特定[服务账户](../your-secrets/service-accounts.md)生成的[访问令牌](../your-secrets/access-tokens.md)登录 Secrets Manager CLI。这意味着**只有服务账户具有访问权限的机密和工程**可以使用 CLI 进行交互。有多种方法可以验证 CLI 会话，但最简单的方法是将环境变量 `BWS_ACCESS_TOKEN` 与您的访问令牌的值一起保存，例如：

```
export BWS_ACCESS_TOKEN=0.48c78342-1635-48a6-accd-afbe01336365.C0tMmQqHnAp1h0gL8bngprlPOYutt0:B3h5D+YgLvFiQhWkIq6Bow==
```

### 获取机密 <a href="#retrieve-the-secret" id="retrieve-the-secret"></a>

接下来，使用以下命令获取您的数据库用户名并将其存储为临时环境变量。在此示例中，`fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff` 表示数据库用户名机密的唯一标识符：

```
export SECRET_1=$(bws get secret fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff | jq '.value')
```

此命令会将您的机密的 `value` 保存到一个临时环境变量中，该变量将在系统重启、用户注销或任何新 shell 中被清除。现在，对数据库密码运行相同的命令：

```
export SECRET_2=$(bws get secret 80b55c29-5cc8-42eb-a898-acfd01232bbb | jq '.value')
```

### 注入机密 <a href="#inject-the-secret" id="inject-the-secret"></a>

现在您的数据库凭据已保存为临时环境变量，可以将它们注入到 `docker run` 命令中。在此示例中，我们省略了 [Bitwarden Unified](../../self-hosting/install-and-deploy-guides/install-and-deploy-unified-beta.md) 强调注入机密所需的许多变量：

```
docker run -d --name bitwarden .... -env BW_DB_USERNAME=$SECRET_1 BW_BD_PASSWORD=$SECRET_2 .... bitwarden/self-host:beta
```

运行此命令时，您的 Docker 容器将启动并从临时存储的环境变量中注入您的数据库凭据，从而使您能够安全地启动 Bitwarden Unified，而无需将敏感值作为明文传递。

## 高级教程 <a href="#advanced-tutorial" id="advanced-tutorial"></a>

在此示例中，您将使用 Docker 映像中的 Secrets Manager CLI 在运行时注入存储在密码库中的数据库凭证。您将通过操作 Dockerfile 将 CLI 安装在映像上而不是主机上，并在容器运行时获取数据库凭据来完成此操作。然后，您将准备用于注入的环境变量文件，并通过运行容器将它们串在一起。

### 设置你的 Dockerfile <a href="#setup-your-dockerfile" id="setup-your-dockerfile"></a>

要在您的 Docker 映像中安装 Secrets Manager CLI，您需要将以下内容添加到您的 Dockerfile：

```
RUN curl -O https://github.com/bitwarden/sdk/releases/download/bws-v0.2.1/bws-x86_64-unknown-linux-gnu-0.2.1.zip && unzip bws-x86_64-unknown-linux-gnu-0.2.1.zip && export PATH=/this/directory:$PATH
```

接下来，您需要构建 `RUN` 语句来获取每个凭据，以便它们可用于注入。这些语句将包括内联身份验证，但这并不是您能够实施的唯一方式：

```
RUN SECRET_1=$(bws get secret fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff --access-token $BWS_ACCESS_TOKEN | jq '.value')
```

```
RUN SECRET_2=$(bws get secret 80b55c29-5cc8-42eb-a898-acfd01232bbb --access-token $BWS_ACCESS_TOKEN | jq '.value')
```

这些 `RUN` 语句将提示您的 Dockerfile 获取指示的机密，其中 `fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff` 代表机密的唯一标识符。

### 准备您的环境文件 <a href="#prepare-your-env-file" id="prepare-your-env-file"></a>

现在您的数据库凭据将可用于注入，调整您的 `settings.env` 文件以能够接收这些值。为此，请将文件中的相关硬编码值替换为指定的变量名称（在本例中为 `SECRET_1` 和 `SECRET_2`）：

```
# Database
# Available providers are sqlserver, postgresql, mysql/mariadb, or sqlite
BW_DB_PROVIDER=mysql
BW_DB_SERVER=db
BW_DB_DATABASE=bitwarden_vault
BW_DB_USERNAME=$SECRET_1
BW_DB_PASSWORD=$SECRET_2
```

### 运行容器 <a href="#run-the-container" id="run-the-container"></a>

现在您的数据库凭据已准备好并准备好注入，启动您的容器并指定访问令牌以作为环境变量与 `bws login` 一起使用：

```
docker run -e BWS_ACCESS_TOKEN=<your-access-token> docker-unified
```

运行此命令时，您的 Docker 容器将启动并从容器获取到的值中注入您的数据库凭据，从而使您能够安全地启动 Bitwarden Unified，而无需将敏感值作为明文传递。

# 开发人员快速入门

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/developer-quick-start/)
{% endhint %}

Bitwarden Secrets Manager 使开发人员、DevOps 和网络安全团队能够大规模集中存储、管理和部署机密。[Secrets Manager CLI](../developer-tools/secrets-manager-cli.md) 是您通过经身份验证的[机器账户](../your-secrets/machine-accounts.md)将[机密](../your-secrets/secrets.md)注入应用程序和基础设施的主要工具。

在本文中，我们将通过查看几种检索存储在密码库中的数据库凭据以在容器运行时注入 [Bitwarden Lite](../../self-hosting/deploy-and-configure/docker/lite-deployment.md) Docker 镜像的方式来演示 Secrets Manager CLI 的使用。

{% hint style="success" %}
如果您正在查找 SDK 信息和 Secrets Manager 功能的语言封装，请参阅[本文](../developer-tools/secrets-manager-sdk.md)。
{% endhint %}

如果您还没有阅读 [Secrets Manager 快速入门](secrets-manager-quick-start.md)文章，建议您在继续之前先阅读。

## 基础教程 <a href="#basic-tutorial" id="basic-tutorial"></a>

在这个最简单的示例中，您将获取存储在密码库中的数据库凭据，并将它们作为临时环境变量存储在 Linux 系统上。存储后，您将在运行时将它们注入 `docker run` 命令中。为此，您需要安装：

* Bitwarden [Secrets Manager CLI](../developer-tools/secrets-manager-cli.md)
* [Docker](https://docs.docker.com/get-docker/)
* [像 jq 这样的命令行 JSON 处理器](https://stedolan.github.io/jq/)

### 身份验证 <a href="#authenticate" id="authenticate"></a>

可以使用为特定[服务账户](../your-secrets/machine-accounts.md)生成的[访问令牌](../your-secrets/access-tokens.md)登录 Secrets Manager CLI。这意味着**只有机器账户具有访问权限的机密和工程**可以使用 CLI 进行交互。有多种方法可以验证 CLI 会话，但最简单的方法是将环境变量 `BWS_ACCESS_TOKEN` 与您的访问令牌的值一起保存，例如：

```shellscript
export BWS_ACCESS_TOKEN=0.48c78342-1635-48a6-accd-afbe01336365.C0tMmQqHnAp1h0gL8bngprlPOYutt0:B3h5D+YgLvFiQhWkIq6Bow==
```

### 获取机密 <a href="#retrieve-the-secret" id="retrieve-the-secret"></a>

接下来，使用以下命令获取您的数据库用户名并将其存储为临时环境变量。在此示例中，`fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff` 表示数据库用户名机密的唯一标识符：

```shellscript
export SECRET_1=$(bws get secret fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff | jq '.value')
```

此命令会将您的机密的 `value` 保存到一个临时环境变量中，该变量将在系统重启、用户注销或任何新 shell 中被清除。现在，对数据库密码运行相同的命令：

```shellscript
export SECRET_2=$(bws get secret 80b55c29-5cc8-42eb-a898-acfd01232bbb | jq '.value')
```

### 注入机密 <a href="#inject-the-secret" id="inject-the-secret"></a>

现在您的数据库凭据已保存为临时环境变量，可以将它们注入到 `docker run` 命令中。在此示例中，我们省略了 [Bitwarden Lite](../../self-hosting/deploy-and-configure/docker/lite-deployment.md) 强调注入机密所需的许多变量：

```shellscript
docker run -d --name bitwarden .... -env BW_DB_USERNAME=$SECRET_1 BW_BD_PASSWORD=$SECRET_2 .... bitwarden/self-host:beta
```

运行此命令时，您的 Docker 容器将启动并从临时存储的环境变量中注入您的数据库凭据，从而使您能够安全地启动 Bitwarden Lite，而无需将敏感值作为明文传递。

## 高级教程 <a href="#advanced-tutorial" id="advanced-tutorial"></a>

在此示例中，您将使用 Docker 映像中的 Secrets Manager CLI 在运行时注入存储在密码库中的数据库凭证。您将通过操作 Dockerfile 将 CLI 安装在映像上而不是主机上，并在容器运行时获取数据库凭据来完成此操作。然后，您将准备用于注入的环境变量文件，并通过运行容器将它们串在一起。

### 设置你的 Dockerfile <a href="#setup-your-dockerfile" id="setup-your-dockerfile"></a>

要在您的 Docker 映像中安装 Secrets Manager CLI，您需要将以下内容添加到您的 Dockerfile：

```docker
# Install dependencies
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
  apt-get install -y \
  ca-certificates \
  curl \
  jq \
  unzip && \
  rm -rf /var/lib/apt/lists/*

# Download bws
RUN curl -LO https://github.com/bitwarden/sdk/releases/download/bws-v1.0.0/bws-x86_64-unknown-linux-gnu-1.0.0.zip && \
  unzip bws-x86_64-unknown-linux-gnu-1.0.0.zip -d /usr/local/bin/ && \
  rm -f bws-x86_64-unknown-linux-gnu-1.0.0.zip

# Add anything else you will need to your image

# Entrypoint script will retrieve secrets at runtime
COPY ./entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]
```

接下来，使用 `entrypoint.sh` 文件在运行时注入机密。一种方法是在 `entrypoint.sh` 文件中构建 `RUN` 语句，用于检索每个凭据。不过，这并不是你能实现的唯一方法：

```shellscript
#!/usr/bin/env bash
# One way to retrieve individual secrets is to use the `get` command and extract the value:
SECRET_1=$(bws secret get fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff | jq '.value')

# Another option., this method is sensitive to spaces in the secret name. See the `run` command documentation for more options
bws run -- 'echo $SECRET_NAME'

# Run your project
```

这些 `RUN` 语句将提示您的 Dockerfile 获取指示的机密，其中 `fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff` 代表机密的唯一标识符。代码示例中的另一个选项代表机密名称，即 `"echo $SECRET_NAME"`。

### 构建镜像 <a href="#build-the-image" id="build-the-image"></a>

要构建 docker 镜像，首先要使 `entrypoint.sh` 可执行：

```bash
chmod +x ./entrypoint.sh
```

构建镜像：

```bash
docker build -t image-name
```

### 运行容器 <a href="#run-the-container" id="run-the-container"></a>

现在您的数据库凭据已准备好并准备好注入，启动您的容器并指定访问令牌以作为环境变量与 `bws login` 一起使用：

```shellscript
docker run --rm -it -e BWS_ACCESS_TOKEN=<your-access-token> image-name
```

运行此命令时，您的 Docker 容器将启动并从容器获取到的值中注入您的数据库凭据，从而使您能够安全地启动 Bitwarden Lite，而无需将敏感值作为明文传递。

# Linux 手动部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/install-on-premise-manual/)
{% endhint %}

这篇文章将引导你完成手动安装和部署 Bitwarden 到你自己的服务器的过程。

{% hint style="warning" %}
**手动安装仅适合高级用户使用。**&#x4EC5;当您非常熟悉 Docker 技术，并且希望对您的 Bitwarden 安装进行更多控制时才可以进行此操作。

手动安装缺乏自动更新 Bitwarden 安装所需的某些依赖项的能力。当你将 Bitwarden 从一个版本升级到下一个版本时，你将负责修改所需的环境变量，修改 nginx 的 `default.conf`，修改 `docker-compose.yml` 等等。

我们会尽量在 [GitHub 上的发行说明](https://github.com/bitwarden/server/releases)中强调这些。你也可以在 GitHub 上监控 Bitwarden 安装脚本所使用的[依赖模板](https://github.com/bitwarden/server/tree/master/util/Setup/Templates)的更改。
{% endhint %}

## 要求 <a href="#installation-procedure" id="installation-procedure"></a>

在继续安装之前，请确保 [Docker Engine](https://docs.docker.com/engine/installation/) 和 [Docker Compose](https://docs.docker.com/compose/install/) 已安装并准备好在您的服务器上使用，并且您的机器符合以下系统规格：

### 系统规格要求 <a href="#system-specifications" id="system-specifications"></a>

|           | **最低**                      | **推荐**                      |
| --------- | --------------------------- | --------------------------- |
| 处理器       | x64, 1.4GHz                 | x64, 2GHz 双核                |
| 内存        | 2GB RAM                     | 4GB RAM                     |
| 存储        | 12GB                        | 25GB                        |
| Docker 版本 | Engine 19+ 以及 Compose 1.24+ | Engine 19+ 以及 Compose 1.24+ |

## 安装步骤 <a href="#installation-procedure" id="installation-procedure"></a>

### 创建 Bitwarden 本地用户和目录 <a href="#create-bitwarden-local-user-and-directory" id="create-bitwarden-local-user-and-directory"></a>

Bitwarden 建议在你的 Linux 服务器上配置一个专用的 `bitwarden` 服务账户，用来安装和运行 Bitwarden。这样做可以将您的 Bitwarden 实例与服务器上运行的其他应用程序隔离开来。

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

### 下载和配置 <a href="#download-and-configure" id="download-and-configure"></a>

要下载 Bitwarden 并配置 Bitwarden 服务器资产：

1、从 [GitHub 上的发行页面](https://github.com/bitwarden/server/releases)下载 Bitwarden 依赖项的存档版本 (`docker-stub.zip`)。例如：

```shell
curl -L https://github.com/bitwarden/server/releases/download/v<version_number>/docker-stub.zip \
 -o docker-stub.zip
```

2、创建一个名为 `bwdata` 的新目录，并将 `docker-stub.zip` 解压到其中，例如：

```shell
unzip docker-stub.zip -d bwdata
```

解压缩后，`bwdata` 目录需要与 `./docker/docker-compose.yml` 文件的映射卷所期望的目录相匹配。如果您愿意，您也可以更改这些映射在主机上的位置。

3、编辑 `./bwdata/env/global.override.env` 中的以下环境变量：

* `globalSettings__baseServiceUri__vault=`：输入您的 Bitwarden 实例的域名。
* `globalSettings__sqlServer__ConnectionString=`：将 `RANDOM_DATABASE_PASSWORD` 替换为在后续步骤中使用的安全密码。
* `globalSettings__identityServer__certificatePassword`：设置一个在后续步骤中使用的安全的证书密码。
* `globalSettings__internalIdentityKey=`：将 `RANDOM_IDENTITY_KEY` 替换为随机密钥字符串。
* `globalSettings__oidcIdentityClientKey=`：将 `RANDOM_IDENTITY_KEY` 替换为随机密钥字符串。
* `globalSettings__duo__aKey=`：将 `RANDOM_DUO_AKEY` 替换为随机密钥字符串。
* `globalSettings__installation__id=`：输入从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取到的安装 ID。
* `globalSettings__installation__key=`：输入从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取到的安装密钥。

{% hint style="success" %}
此时，还要考虑为所有 `globalSettings__mail__smtp__` 变量和 `adminSettings__admins` 设置值。这样做将配置用于向新组织成员发送邀请的 SMTP 邮件服务器，并提供对[系统管理员门户](../../system-administrator-portal.md)的访问权限。

[了解有关环境变量的更多信息](../../configure-environment-variables.md)。
{% endhint %}

4、从 `./bwdata` 为身份容器生成一个 `.pfx` 证书文件并将其移动到已映射的卷目录（默认为 `./bwdata/identity/`）。例如，运行以下命令：

```shell
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout identity.key -out identity.crt -subj "/CN=Bitwarden IdentityServer" -days 10950
```

然后

```shell
openssl pkcs12 -export -out ./identity/identity.pfx -inkey identity.key -in identity.crt -passout pass:IDENTITY_CERT_PASSWORD
```

在上述命令中，将 `IDENTITY_CERT_PASSWORD` 替换为在**步骤 3** 中创建和使用的证书密码。

5、将 `identity.pfx` 复制到 `./bwdata/ssl` 目录。

6、在 `./bwdata/ssl` 中创建一个以您的域名命名的子目录，例如：

```shell
mkdir ./ssl/bitwarden.example.com
```

7、在新创建的 `./bwdata/ssl/bitwarden.example.com` 子目录中提供受信任的 SSL 证书和私钥。

{% hint style="info" %}
此目录映射到 NGINX 容器的 `/etc/ssl` 目录。如果您无法提供受信任的 SSL 证书，请在安装前使用代理，以为 Bitwarden 客户端应用程序提供一个 HTTPS 端点。
{% endhint %}

8、在 `./bwdata/nginx/default.conf` 中：

1. 将所有实例 `bitwarden.example.com` 替换为您的域名，包括 `Content-Security-Policy` 标头。
2. 将 `ssl_certificate` 和 `ssl_certificate_key` 变量设置为**步骤 7** 中提供的证书和私钥的路径。
3. 根据您的证书设置，执行以下操作之一：
   * 如果您使用受信任的 SSL 证书，请将 `ssl_trusted_certificate` 变量设置为证书的路径。
   * 如果您使用自签名证书，请注释掉 `ssl_trusted_certificate` 变量。

9、在 `./bwdata/env/mssql.override.env` 中，将 `RANDOM_DATABASE_PASSWORD` 替换为在**步骤 3** 中创建的密码。

10、在 `./bwdata/web/app-id.json` 中，将 `bitwarden.example.com` 替换为您的域名。

11、在 `./bwdata/env/uid.env` 中，设置您[之前创建的](linux-standard-deployment-1.md#create-bitwarden-local-user-and-directory) `bitwarden` 用户和组的 UID 和 GID，以便容器在它们下面运行，例如：

```shell
LOCAL_UID=1001
LOCAL_GID=1001
```

### 启动您的服务器 <a href="#start-your-server" id="start-your-server"></a>

使用以下命令启动您的 Bitwarden 服务器：

```shell
docker-compose -f ./docker/docker-compose.yml up -d
```

验证所有容器是否正常运行：

```shell
docker ps
```

{% embed url="https://bitwarden.com/_gatsby/image/44cd09376223f66d253aa2a2c26bf420/d335a0afdef5beeea3a4ce0a3f3dcc88/docker-healthy.webp?eu=8b8652b4e29afd865c6ca5816d21676ee96d02abfd5037d96964e5a746ab9e8376f34c0029962ee32e6c5b8bd3b610ef66c678301fbb84d3c1ba18f6e33cf80a05840cba61b47607052891fdb1f406106dc6490ca7d1c90ba2697bd2e1e6b12548041579f928bc89e9fd3632b78a2833e8b6f27f6694a971e812540c8f5c31bf6ea48f876e4fb99bf301bca2b8f84a8ec9a36e191e8eb72a2535124c1eb72cedadef4376262a231a32b3fe22ad60cce749660450395b07b03a7d8a4afb6a36c2ecfca659dc7a73e9aa9c35238f95add1e54eaa2b72b59e71fd85387e1159f340f6e939ea8a315752c572b38b0cec54&a=w%3D850%26h%3D126%26fm%3Dwebp%26q%3D75&cd=2022-12-09T17%3A18%3A21.193Z" %}

恭喜！ Bitwarden 现已启动并运行在 `https://your.domain.com` 了。在您的浏览器中访问网络密码库以确认其正常工作。

您现在可以注册一个新帐户并登录了。您需要配置 SMPT 环境变量（请参阅[环境变量](../../configure-environment-variables.md)）以验证您的新帐户的电子邮件。

## 更新您的服务器 <a href="#update-your-server" id="update-your-server"></a>

更新已手动安装和部署的自托管服务器与[标准更新过程](../../update-your-instance.md)有所不同。要更新您手动安装的服务器：

1. 从 [GitHub 发行页面](https://github.com/bitwarden/server/releases)下载最新的 `docker-stub.zip` 存档。
2. 将此新的 `docker-stub.zip` 存档解压缩并将其内容与当前 `bwdata` 目录中的内容进行比较，将任何新内容复制到 `bwdata` 中预先存在的文件中。\
   **不要**使用此较新的 `docker-stub.zip` 存档的内容直接覆盖您预先存在的 `bwdata` 目录，因为这会覆盖您已经完成的任何自定义配置工作。
3.  运行以下命令以使用已更新的配置和最新的容器重新启动服务器：

    ```bash
    docker-compose -f ./docker/docker-compose.yml down && docker-compose -f ./docker/docker-compose.yml up -d
    ```

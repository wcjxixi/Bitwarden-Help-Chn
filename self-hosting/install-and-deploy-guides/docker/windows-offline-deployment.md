# Windows 离线部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/install-and-deploy-offline-windows/)
{% endhint %}

这篇文章将指导您在**离线或网闸环境**中安装和部署 Bitwarden 到您自己的 Windows 服务器。请查看 Bitwarden [软件发布支持](https://help.ppgg.in/security/bitwarden-software-release-support)文档。

> **\[译者注]**：[网闸](https://zh.wikipedia.org/wiki/%E7%BD%91%E9%97%B8) (air-gapped) 网络，是指与外部网络（如互联网或其他外部系统）完全隔离的计算机网络。这种隔离通过物理或逻辑手段实现，确保网络无法与外部环境进行数据交换，从而增强安全性。

{% hint style="warning" %}
**手动安装仅适合高级用户使用。**&#x4EC5;当您非常熟悉 Docker 技术，并且希望对您的 Bitwarden 安装进行更多控制时才可以进行此操作。

手动安装缺乏自动更新 Bitwarden 安装所需的某些依赖项的能力。当您将 Bitwarden 从一个版本升级到下一个版本时，您将负责修改所需的环境变量，修改 nginx 的 `default.conf`，修改 `docker-compose.yml` 等等。

我们会尽量在 [GitHub 上的发行说明](https://github.com/bitwarden/server/releases)中强调这些。您也可以在 GitHub 上监控 Bitwarden 安装脚本所使用的[依赖模板](https://github.com/bitwarden/server/tree/master/util/Setup/Templates)的更改。
{% endhint %}

## 系统规格要求 <a href="#requirements" id="requirements"></a>

<table><thead><tr><th></th><th width="249.33333333333331">最低</th><th>推荐</th></tr></thead><tbody><tr><td>处理器</td><td>x64, 1.4GHz</td><td>x64, 2GHz 双核</td></tr><tr><td>内存</td><td>2GB RAM</td><td>4GB RAM</td></tr><tr><td>存储</td><td>12GB</td><td>25GB</td></tr><tr><td>Docker 版本</td><td>Engine 26+ 以及 Compose <mark style="color:red;">ª</mark></td><td>Engine 26+ 以及 Compose <mark style="color:red;">ª</mark></td></tr></tbody></table>

<mark style="color:red;">ª</mark> - 下载 Docker Engine 时，Docker Compose 会作为插件自动安装。[为 Engine 和 Compose 安装 Docker Desktop](https://docs.docker.com/desktop/install/windows-install/)。

另外，请确保满足以下要求：

* 使用具有 Internet 访问权限的机器，您已经从 Bitwarden 服务器存储库的[发行页面](https://github.com/bitwarden/server/releases)下载了最新的 `docker-stub.zip` 或 `docker-stub-EU.zip` 文件，并已将该文件传输到您的服务器。
* 离线 SMTP 服务器已在您的环境中设置并处于活动状态。

运行您的 Bitwarden 部署的服务器不需要允许出站流量访问网络外部的任何地址，但客户端应用程序必须配置为访问服务器的完全限定域名 (FQDN)，默认情况下使用端口 80 和 443。在安装过程中，您可以选择使用不同的端口，但无论选择哪个端口，都必须开放这些端口以供客户端访问。

> **\[译者注]**：[FQDN](https://zh.wikipedia.org/wiki/%E5%AE%8C%E6%95%B4%E7%B6%B2%E5%9F%9F%E5%90%8D%E7%A8%B1)：即完全限定域名 (Fully Qualified Domain Name)，是互联网上用于标识特定主机或服务器的完整域名。它由主机名和域名组成，确保在全球范围内唯一地定位到一个网络资源。FQDN 从最具体的部分（主机名）到最一般的部分（顶级域名）依次排列，各部分之间用点（.）分隔。
>
> 例如，一个典型的 FQDN `mail.example.com` ：
>
> * `mail` 是主机名，指定了特定的服务器或服务。
> * `example.com` 是域名，指定了该主机所属的组织或实体。
> * `.com` 是顶级域名 (TLD)，表示这是一个商业实体。

### 嵌套虚拟化 <a href="#nested-virtualization" id="nested-virtualization"></a>

在 Windows 服务器上运行 Bitwarden 需要使用嵌套虚拟化。请检查您的  Hypervisor 文档以了解是否支持嵌套虚拟化以及如何启用它。

{% hint style="info" %}
如果您将 Windows Server 作为 Azure VM 运行，我们建议使用**运行 Windows Server 2019 Gen2 的标准 D2s v3 虚拟机**，它满足所有[系统规格要求](windows-offline-deployment.md#system-specifications)，包括对嵌套虚拟化的支持。
{% endhint %}

## 安装步骤 <a href="#installation-procedure" id="installation-procedure"></a>

### 配置您的域名 <a href="#configure-your-domain" id="configure-your-domain"></a>

默认情况下，Bitwarden 通过主机上的 80 (`http`) 和 443 (`https`) 端口提供服务。打开这些端口，以便可以从网络内部和/或外部访问 Bitwarden。您也可以在安装过程中选择不同的端口。

{% hint style="info" %}
**如果您使用的是 Windows 防火墙**，则 Docker Desktop for Windows 不会自动在 Windows 防火墙中为其自己添加例外。为 TCP 端口 80 和 443（或选择的备用端口）添加例外以避免相关错误。
{% endhint %}

我们建议使用指向您的主机的 DNS 记录配置域名（例如，`bitwarden.example.com`），尤其是当您通过 Internet 提供 Bitwarden 服务时。

### 创建 Bitwarden 本地用户和目录 <a href="#create-bitwarden-local-user-and-directory" id="create-bitwarden-local-user-and-directory"></a>

打开 PowerShell 并通过运行以下命令创建一个 Bitwarden 本地用户：

```batch
PS C:\> $Password = Read-Host -AsSecureString
```

运行上述命令后，在文本输入对话框中输入所需的密码。指定密码后，运行以下命令：

```batch
New-LocalUser "Bitwarden" -Password $Password -Description "Bitwarden Local Admin"
```

作为新创建的用户，在 `C:\` 下创建一个 `Bitwarden` 文件夹：

```batch
PS C:\> mkdir Bitwarden
```

安装 Docker Desktop 后，导航至 **Settings** → **Resources** → **File Sharing** 然后将已创建的目录 (`C:\Bitwarden`) 添加到资源列表。选择 **Apply & Restart** 以应用您的更改。

### 配置您的机器 <a href="#configure-your-machine" id="configure-your-machine"></a>

要使用 Bitwarden 服务器所需的资产配置您的机器：

{% hint style="success" %}
如果您[已创建 Bitwarden 用户和目录](windows-offline-deployment.md#create-bitwarden-local-user-and-directory)，请以 `bitwarden` 用户身份完成以下操作。
{% endhint %}

1、在 `C:\Bitwarden` 中创建一个名为 `bwdata` 的新目录，并将 `docker-stub.zip` 解压到其中，例如：

解压缩后，`bwdata` 目录需要与 `docker-compose.yml` 文件的卷映射所期望的目录相匹配。如果您愿意，您也可以更改这些映射在主机上的位置。

2、编辑 `bwdata\env\global.override.env` 中的以下环境变量：

* `globalSettings__baseServiceUri__vault=`：输入您的 Bitwarden 实例的域名。
* `globalSettings__sqlServer__ConnectionString=`：将 `RANDOM_DATABASE_PASSWORD` 替换为在后续步骤中使用的安全密码。
* `globalSettings__identityServer__certificatePassword`：设置一个在后续步骤中使用的安全的证书密码。
* `globalSettings__internalIdentityKey=`：将 `RANDOM_IDENTITY_KEY` 替换为随机密钥字符串。
* `globalSettings__oidcIdentityClientKey=`：将 `RANDOM_IDENTITY_KEY` 替换为随机密钥字符串。
* `globalSettings__duo__aKey=`：将 `RANDOM_DUO_AKEY` 替换为随机密钥字符串。
* `globalSettings__installation__id=`：输入从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取到的安装 ID。
* `globalSettings__installation__key=`：输入从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取到的安装密钥。
* `globalSettings__pushRelayBaseUri=`：这个变量应该是空。有关详细信息，请参阅[配置推送中继](../../configure-push-relay.md)。

{% hint style="success" %}
此时，还要考虑为所有 `globalSettings__mail__smtp__` 变量和 `adminSettings__admins` 设置值。这样做将配置用于向新组织成员发送邀请的 SMTP 邮件服务器，并提供对[系统管理员门户](../../system-administrator-portal.md)的访问权限。

[了解有关环境变量的更多信息](../../configure-environment-variables.md)。
{% endhint %}

3、为身份容器生成一个 `identity.pfx` 证书。您可以使用 OpenSSL 或使用任何工具来生成自签名证书。如果您使用的是 OpenSSL，请运行以下命令：

```batch
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout identity.key -out identity.crt -subj "/CN=Bitwarden IdentityServer" -days 10950
```

然后

```batch
openssl pkcs12 -export -out ./identity/identity.pfx -inkey identity.key -in identity.crt -passout pass:IDENTITY_CERT_PASSWORD
```

在上述命令中，将 `IDENTITY_CERT_PASSWORD` 替换为在**步骤 2** 中创建和使用的证书密码。

4、将 `identity.pfx` 移动到映射的卷目录（默认为 `.\bwdata\identity`）

5、将 `identity.pfx` 复制到 `.\bwdata\ssl` 目录。

6、在 `.\bwdata\ssl` 中创建一个以您的域命名的子目录。

7、在新创建的 `.\bwdata\ssl\bitwarden.example.com` 子目录中提供受信任的 SSL 证书和私钥。

{% hint style="info" %}
此目录映射到 NGINX 容器的 `\etc\ssl` 目录。如果您无法提供受信任的 SSL 证书，请在安装前使用代理，以为 Bitwarden 客户端应用程序提供一个 HTTPS 端点。
{% endhint %}

8、在 `.\bwdata\nginx\default.conf` 中：

1. 将所有实例的 `bitwarden.example.com` 替换为您的域名，包括 `Content-Security-Policy` 标头。
2. 将 `ssl_certificate` 和 `ssl_certificate_key` 变量设置为**步骤 7** 中提供的证书和私钥的路径。
3. 根据您的证书设置，执行以下操作之一：
   * 如果您使用受信任的 SSL 证书，请将 `ssl_trusted_certificate` 变量设置为证书的路径。
   * 如果您使用自签名证书，请注释掉 `ssl_trusted_certificate` 变量。

9、在 `.\bwdata\env\mssql.override.env` 中，将 `RANDOM_DATABASE_PASSWORD` 替换为在**步骤 2** 中创建的密码。

10、在 `.\bwdata\web\app-id.json` 中，将 `bitwarden.example.com` 替换为您的域名。

### 下载和传输镜像 <a href="#download-and-transfer-images" id="download-and-transfer-images"></a>

要获取 docker 镜像以在离线机器上使用：

1、从已连接互联网的机器上，下载如 `docker-stub.zip` 中的 `docker-compose.yml` 文件中所列的所有 `bitwarden/xxx:latest` docker 镜像，。

2、将每一个镜像保存为 `.img` 文件，例如：

```shell
docker image save -o mssql.img bitwarden/mssql:version
```

3、将所有 `.img` 文件传输到您的离线计机器上。

4、在离线机器上，加载每一个 `.img` 文件以创建本地 docker 映像，例如：

```shell
docker image load mssql.img
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

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3kcV9CFkWJrw5qCmKZsyBg/5cd5030d96352e6b1f5f20d1ffb79654/docker-ps-win.png?_a=DAJCwlWIZAAB" %}
显示健康容器的列表
{% endembed %}

恭喜！ Bitwarden 现已启动并运行在 `https://your.domain.com` 了。在您的浏览器中访问网络密码库以确认其正常工作。

您现在可以注册一个新账户并登录了。您需要配置 SMPT 环境变量（请参阅[环境变量](../../configure-environment-variables.md)）以验证您的新账户的电子邮箱。

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

1. 如果您打算自托管一个 Bitwarden 组织，请参阅[自托管组织](../../self-host-an-organization.md)以开始。
2. 如需了解更多信息，请参阅[自托管 FAQ](../../hosting-faqs.md)。

## 更新您的服务器 <a href="#update-your-server" id="update-your-server"></a>

更新已手动安装和部署的自托管服务器与[标准更新过程](../../update-your-instance.md)有所不同。要更新您手动安装的服务器：

1. 从 [GitHub 发行页面](https://github.com/bitwarden/server/releases)下载最新的 `docker-stub.zip` 存档。
2. 将此新的 `docker-stub.zip` 存档解压缩并将其内容与当前 `bwdata` 目录中的内容进行比较，将任何新内容复制到 `bwdata` 中预先存在的文件中。\
   **不要**使用此较新的 `docker-stub.zip` 存档的内容直接覆盖您预先存在的 `bwdata` 目录，因为这会覆盖您已经完成的任何自定义配置工作。
3.  运行以下命令以使用已更新的配置和最新的容器重新启动服务器：

    ```bash
    docker-compose -f ./docker/docker-compose.yml down && docker-compose -f ./docker/docker-compose.yml up -d
    ```

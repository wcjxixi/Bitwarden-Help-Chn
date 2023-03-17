# 安装和部署-Windows

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/install-on-premise-windows/)
{% endhint %}

这篇文章将引导你完成安装和部署 Bitwarden 到你自己的 Windows 服务器上的过程。Bitwarden 也可以安装和部署在 [Linux 和 macOS](install-and-deploy-linux.md) 机器上。

## 系统规格要求 <a href="#system-specifications" id="system-specifications"></a>

|           | **最低**                      | **推荐**                      |
| --------- | --------------------------- | --------------------------- |
| 处理器       | x64, 1.4GHz                 | x64, 2GHz 双核                |
| 内存        | 6GB RAM                     | 8+GB RAM                    |
| 存储        | 76GB                        | 90GB                        |
| Docker 版本 | Engine 19+ 以及 Compose 1.24+ | Engine 19+ 以及 Compose 1.24+ |

### 嵌套虚拟化 <a href="#nested-virtualization" id="nested-virtualization"></a>

在 Windows 服务器上运行 Bitwarden **需要使用嵌套虚拟化**。请检查您的管理程序的文档以了解是否支持嵌套虚拟化以及如何启用它。

{% hint style="success" %}
如果你将 Windows Server 作为 Azure VM 运行，我们建议**使用运行 Windows Server 2019 Gen2 的标准 D2s v3 虚拟机**，它满足所有[系统要求](install-and-deploy-windows.md#system-specifications)，包括对嵌套虚拟化的支持。
{% endhint %}

## TL;DR <a href="#tl-dr" id="tl-dr"></a>

> \[**译者注**]：TL;DL - Too long; Don't read，直译为「太长，请不要看」，实际意思为「此文篇幅较长，看此总结」，一般用在比较长篇幅的内容前面，后面跟着一段简短的总结内容。

以下是本文中[安装步骤](install-and-deploy-windows.md#installation-procedure)的摘要。本节中的链接将跳转至详细的**安装步骤**部分：

1、[**配置您的域名**](install-and-deploy-windows.md#configure-your-domain)。设置你的域名 DNS 记录指向你的主机，并打开主机上的 80 和 443 端口。

2、在您的主机上[**安装 Docker 和 Docker Compose**](install-and-deploy-windows.md#install-docker-and-docker-compose)。

3、[**安装和设置桌面版 Docker**](install-and-deploy-windows.md#zhi-docker-zhuo-mian)。

4、从 [**https://bitwarden.com/host**](https://bitwarden.com/host) 获取安装 ID 和密钥用于安装过程。更多详细信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)。

5、在你机器上[**安装 Bitwarden**](install-and-deploy-windows.md#install-bitwarden)。

6、在 `./bwdata/env/global.override.env` 中调整设置以[**配置您的环境**](install-and-deploy-windows.md#configure-your-environment)。

{% hint style="success" %}
至少要配置 `globalSettings__mail__smtp...` 变量以设置用于邀请和验证用户的电子邮件服务器。
{% endhint %}

7、[**启动您的实例**](install-and-deploy-windows.md#start-bitwarden)。

8、在网页浏览器中打开您配置的域名来测试您的安装。

## 安装步骤 <a href="#installation-procedure" id="installation-procedure"></a>

### 配置您的域名 <a href="#configure-your-domain" id="configure-your-domain"></a>

默认情况下，Bitwarden 通过本地主机上的 80（http）和 443（https）端口提供服务。您应该打开这些端口，以便可以从网络内部和/或外部访问 Bitwarden。如果你愿意，也可以在安装过程中选择使用其他端口。

{% hint style="success" %}
**如果您使用的是 Windows 防火墙**，Docker Desktop for Windows 不会自动在 Windows 防火墙中为自己添加例外。为 TCP 端口 80 和 443（或选择的替代端口）添加例外以防止出现一些错误。
{% endhint %}

我们建议配置一个带 DNS 记录的域名（例如，`bitwarden.example.com`）指向您的托管主机，特别是当您通过互联网提供 Bitwarden 服务时。

### 创建 Bitwarden 本地用户和目录 <a href="#create-bitwarden-local-user-and-directory" id="create-bitwarden-local-user-and-directory"></a>

打开 PowerShell 并通过运行以下命令创建一个 Bitwarden 本地用户：

```powershell
PS C:\> $Password = Read-Host -AsSecureString
```

运行上述命令后，在文本输入对话框中输入所需的密码。指定密码后，运行以下命令：

```powershell
New-LocalUser "Bitwarden" -Password $Password -Description "Bitwarden Local Admin"
```

作为新创建的用户，在 C:\ 下创建一个 Bitwarden 文件夹：

```powershell
PS C:\> mkdir Bitwarden
```

在桌面版 Docker 中，导航到 **Settings** → **Resources** → **File Sharing** 并将创建的目录（`C:\Bitwarden`）添加到 Resources 列表中。选择 **Apply & Restart** 以使您的更改生效。

### 设置桌面版 Docker <a href="#setup-docker-desktop" id="setup-docker-desktop"></a>

Bitwarden 将使用一系列 [Docker 容器](https://docs.docker.com/get-started/)部署并运行在您的机器上。适用于 Windows 的桌面版 Docker 包含了 Docker Engine 和 Docker Compose。下载并安装[适用于 Windows 的桌面版 Docker](https://docs.docker.com/desktop/windows/install/)，并在安装过程中选中**启用 Hyper-V Windows 功能**配置选项。

### 安装 Bitwarden <a href="#install-bitwarden" id="install-bitwarden"></a>

Bitwarden 提供了一个 Powershell Cmdlet 文件（`.ps1`），以便在 Windows 机器上轻松安装。完成以下步骤以使用 Cmdlet 安装 Bitwarden：

{% hint style="success" %}
如果您[已经创建 Bitwarden 用户和目录](install-and-deploy-windows.md#create-bitwarden-local-user-and-directory)，请以 `Bitwarden` 用户身份完成以下操作。
{% endhint %}

1、导航到[已创建](install-and-deploy-windows.md#create-bitwarden-local-user-and-directory)的目录：

```powershell
cd C:\Bitwarden
```

2、运行以下命令下载 Bitwarden 安装脚本（`bitwarden.ps1`）：

```powershell
Invoke-RestMethod -OutFile bitwarden.ps1 -Uri "https://func.bitwarden.com/api/dl/?app=self-host&platform=windows"
```

3、使用以下命令运行安装程序脚本：

```powershell
.\bitwarden.ps1 -install
```

4、完成安装程序中的以下提示：

* **Enter the domain name for your Bitwarden instance（输入您的 Bitwarden 实例的域名）:**\
  通常，此值应该是已配置的 DNS 记录。
*   **Do you want to use Let's Encrypt to generate a free SSL certificate? (y/n)（您想使用 Let's Encrypt 生成免费的 SSL 证书吗？）:**\
    ****指定 `y` 来使用 Let's Encrypt 生成一个可信的 SSL 证书。你会被提示输入一个电子邮件地址，以便从 Let's Encrypt 获取到期提醒。更多信息，请参阅[证书选项](../certificate-options.md)。

    或者，指定 `n` 并使用 **Do you have a SSL certificate to use?** 选项。
* **Enter your installation id（输入您的安装 ID）:**\
  ****通过 [https://bitwarden.com/host](https://bitwarden.com/host) 使用一个有效的电子邮件地址来获取安装 ID。更多详细信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)
*   **Enter your installation key（输入您的安装密钥）:**

    通过 [https://bitwarden.com/host](https://bitwarden.com/host) 使用一个有效的电子邮件地址来获取安装密钥。更多详细信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)
*   **Do you have a SSL certificate to use? (y/n)（您拥有自己的 SSL 证书吗？）:**\
    ****如果你已经有自己的 SSL 证书，请指定 `y`，并将必要的文件放在 `C:\Bitwarden\bwdata\ssl\<your_domain>` 目录下。你会被问到是否使用受信任的 SSL 证书（y/n）。更多信息，请参阅[证书选项](../certificate-options.md)。

    或者，指定 `n` 并使用 **self-signed SSL certificate?** 选项，这只是为了测试目的而推荐的。
*   **Do you want to generate a self-signed SSL certificate? (y/n)（您想生成一个自签名证书吗？）:**\
    ****指定 `y` 让 Bitwarden 为你生成一个自签名证书。这个选项只推荐用于测试。更多信息，请参阅[证书选项](../certificate-options.md)。

    如果你指定 `n`，你的实例将不使用 SSL 证书，你需要使用前置 HTTPS 代理来安装，否则 Bitwarden 应用程序将无法正常运行。

### 安装后配置 <a href="#post-install-configuration" id="post-install-configuration"></a>

配置您的环境可能涉及对两个文件进行更改：一个环境变量文件和一个安装文件：

#### 环境变量（_必须_） <a href="#environment-variables-required" id="environment-variables-required"></a>

`bitwarden.ps1` Cmdlet 未配置 Bitwarden 的某些功能。通过编辑位于 `./bwdata/env/global.override.env` 的环境文件来配置这些设置。至少，您应该替换以下值：

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

```powershell
.\bitwarden.ps1 restart
```

#### 安装文件 <a href="#installation-file" id="installation-file"></a>

Bitwarden 安装脚本使用 `./bwdata/config.yml` 中的设置来生成必要的资产，以用于安装。某些安装场景（例如，在代理服务器后面使用备用端口进行安装）可能需要对 `config.yml` 进行调整，这些调整在标准安装过程中没有提供。

根据需要编辑 `config.yml` 文件，并使用以下命令以使更改生效：

```powershell
.\bitwarden.ps1 -rebuild
```

### 启动 Bitwarden <a href="#start-bitwarden" id="start-bitwarden"></a>

完成所有前面的步骤后，通过运行以下命令启动您的 Bitwarden 实例：

```powershell
.\bitwarden.ps1 -start
```

{% hint style="info" %}
首次启动 Bitwarden 时，可能会花费一些时间，因为它会从 Docker Hub 下载所有镜像。
{% endhint %}

验证所有容器是否正常运行：

```powershell
docker ps
```

{% embed url="https://bitwarden.com/help/images/hosting/docker-ps-win.png" %}
显示健康容器的列表
{% endembed %}

恭喜你！Bitwarden 现在已启动并运行在`https://your.domain.com`上了。在网页浏览器中访问网页密码库以确认他是否已经正常工作。

现在，您可以注册一个新帐户并登录了。您需要配置 `smtp` 环境变量（请参阅[环境变量](install-and-deploy-linux.md#environment-variables)）以验证新帐户的电子邮件地址。

## 在启动时启动 Docker <a href="#start-docker-on-boot" id="start-docker-on-boot"></a>

如果您有已登录的 RDP 会话，桌面版 Docker 才会在启动时自动启动。无论是否有用户登录，都要在启动时启动桌面版 Docker：

{% hint style="warning" %}
桌面版 Docker 在启动后可能需要长达 15 分钟才能启动完成并可以从网络访问容器。
{% endhint %}

1、打开 Windows 任务计划程序并从操作菜单中选择**创建任务…** 。

2、使用以下安全选项配置任务：

* 将任务设置为使用[已创建](install-and-deploy-windows.md#create-bitwarden-local-user-and-directory)的 `Bitwarden` 用户帐户。
* 将任务设置为**不管用户是否登录都要运行**。

3、选择**触发器**选项卡并新建如下的触发器：

* 从开始任务下拉列表中，选择**启动时**。
* 在高级设置部分，勾选**延迟任务时间:**  复选框并从下拉列表中选择 **1 分钟**。

4、选择**操作**选项卡并新建如下的操作：

* 在程序或脚本输入栏中，指定 `“C:\Program Files\Docker\Docker\Docker Desktop.exe”`。

5、选择**确定**完成定时任务的创建。

## 脚本命令参考 <a href="#script-commands-reference" id="script-commands-reference"></a>

Bitwarden 安装脚本（`bitwarden.ps1`）具有以下可用的命令。所有命令都必须以开关（`-`）为前缀，例如 `.\bitwarden.ps1 -start`：

| 命令          | 描述                                                                                                                                                                |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -install    | 启动安装程序。                                                                                                                                                           |
| -start      | 启动所有容器。                                                                                                                                                           |
| -restart    | 重新启动所有容器。                                                                                                                                                         |
| -stop       | 停止所有容器。                                                                                                                                                           |
| -update     | 更新所有容器和数据库。                                                                                                                                                       |
| -updatedb   | 更新/初始化数据库。                                                                                                                                                        |
| -updaterun  | 更新 `run.sh` 文件。                                                                                                                                                   |
| -updateself | 更新安装脚本。                                                                                                                                                           |
| -updateconf | 更新所有容器，而无需重新启动正在运行的实例。                                                                                                                                            |
| -uninstall  | <p>在执行此命令之前，系统会提示您保存数据库文件。选 <code>y</code> 将创建一个包含最新备份的数据库的 tar 文件。</p><p></p><p>停止容器，删除 <code>bwdata</code> 目录及其所有内容，并删除临时卷。执行后，系统会询问您是否还要清除所有 Bitwarden 镜像。</p> |
| -renewcert  | 续签证书。                                                                                                                                                             |
| -rebuild    | 重建从 `config.yml` 生成的安装资产。                                                                                                                                         |
| -help       | 列出所有命令。                                                                                                                                                           |

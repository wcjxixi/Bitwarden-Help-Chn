# 更新服务器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/updating-on-premise/)
{% endhint %}

{% hint style="success" %}
自托管服务器的发布会比云端服务器的发布滞后几天。 因此请注意，[系统管理员门户](system-administrator-portal.md)可能会在自托管服务器更新可用**之前**报告有可用更新。

此外，请查看 Bitwarden [软件发布支持](../security/software-development/software-release-support.md#bitwarden-server)文档。
{% endhint %}

**将您的自托管 Bitwarden 实例保持为最新版本非常重要**。更新可能包括对 Bitwarden 实例的安全性很重要的修复，包括对任何漏洞的补丁。存储在 Bitwarden 密码库中的数据（包括密码）应被视为关键数据，因此应使用最新软件进行保护。

此外，较新版本的客户端应用程序可能不支持较早版本的自托管实例。

您可以通过导航至[此存储库](https://github.com/bitwarden/self-host)然后选择 **Watch** → **Custom** → **Releases** 来订阅自托管服务器发布的电子邮件通知。

{% hint style="warning" %}
我们强烈建议您在更新自托管实例之前备份数据。有关更多信息，请参阅[备份您的托管数据](backup-server-data.md)。
{% endhint %}

如果您运行的是标准安装，请使用与安装 Bitwarden 相同的 Bash（Linux 或 macOS）或 Powershell（Windows）脚本（`bitwarden.sh`）来更新 Bitwarden 实例。按顺序运行以下命令：

<img src="../.gitbook/assets/linux-24.png" alt="" data-size="line"><img src="../.gitbook/assets/apple-24.png" alt="" data-size="line"> Bash

```bash
./bitwarden.sh updateself
./bitwarden.sh update
```

<img src="../.gitbook/assets/os-windows-24.png" alt="" data-size="line"> PowerShell

```powershell
.\bitwarden.ps1 -updateself
.\bitwarden.ps1 -update
```

## 更新离线部署 <a href="#update-offline-deployment" id="update-offline-deployment"></a>

如果您运行的是[手动安装](deploy-and-configure/docker/linux-standard-deployment-1.md#update-your-server)或[离线 Linux](deploy-and-configure/docker/linux-offline-deployment.md#update-your-server) 或[离线 Windows](deploy-and-configure/docker/windows-offline-deployment.md#update-your-server) 安装，请按照链接文章中的步骤操作。

现在，您的 Bitwarden 安装应该已经完全更新并开始运行了。

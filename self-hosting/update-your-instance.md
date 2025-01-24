# 更新您的实例

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/updating-on-premise/)
{% endhint %}

{% hint style="warning" %}
请注意，自托管服务器的发行会比云服务器的发行滞后几天。。
{% endhint %}

**将您的自托管 Bitwarden 实例保持为最新版本非常重要**。更新可能包括对 Bitwarden 实例的安全性很重要的修复，包括对任何漏洞的补丁。存储在 Bitwarden 密码库中的数据（包括密码）应被视为关键数据，因此应使用最新软件进行保护。

此外，较新版本的客户端应用程序可能不支持较早版本的自托管实例。

{% hint style="warning" %}
我们强烈建议您在更新自托管实例之前备份数据。有关更多信息，请参阅[备份您的托管数据](backup-your-hosted-data.md)。
{% endhint %}

使用与安装 Bitwarden 相同的 Bash（Linux 或 macOS）或 Powershell（Windows）脚本（`bitwarden.sh`）来更新 Bitwarden 实例。按顺序运行以下命令：

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

您的 Bitwarden 安装现在应该是最新并且可以运行了。

{% hint style="info" %}
我们建议创建一个 cronjob 或计划任务以每周甚至每晚运行这些更新命令。这将自动使您的实例保持为最新。例如，以下 cron 作业将在每个星期日的 2:00 检查更新并关闭该作业的电子邮件输出：

```shell
0 2 * * 0 /opt/bitwarden/bwdata/scripts/updatebw.sh >/dev/null 2>&1
```

在上面的例子中，`updatebw.sh` 是一个你必须手动保存的脚本，它包含的内容：

```shell
#!/bin/bash
./bitwarden.sh updateself
./bitwarden.sh update
```
{% endhint %}

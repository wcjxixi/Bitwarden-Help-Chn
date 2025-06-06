# 离线使用 Bitwarden

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/using-bitwarden-offline/)
{% endhint %}

任何[已解锁](../account/log-in-and-unlock/vault-timeout-options.md#vault-timeout-action)的 Bitwarden App 都可以在**只读模式**下离线使用，例如在移动设备上使用飞行模式或未连接到您的自托管服务器时。

Bitwarden 的大多数功能都可以在离线模式下无障碍使用，但是您将无法编辑或添加密码库项目、附件、Send，或导入新的密码库项目。

## 离线安装 Bitwarden <a href="#installing-bitwarden-offline" id="installing-bitwarden-offline"></a>

客户偶尔希望将 Bitwarden 安装到离线机器上，例如在物网闸环境中。要在离线机器上安装 Bitwarden 桌面 App：

> **\[译者注]**：[网闸](https://zh.wikipedia.org/wiki/%E7%BD%91%E9%97%B8) (air-gapped) 网络，是指与外部网络（如互联网或其他外部系统）完全隔离的计算机网络。这种隔离通过物理或逻辑手段实现，确保网络无法与外部环境进行数据交换，从而增强安全性。

{% hint style="success" %}
**仅适用于 Windows**，作为以下过程的替代方法，您可以下载 `Bitwarden-Portable-x.xx.x.exe` 并将其传输到离线机器。便携式 App 不需要安装。
{% endhint %}

1. 在可以访问 Internet 的机器上，导航到 [https://github.com/bitwarden/desktop/releases](https://github.com/bitwarden/desktop/releases) 下载最新版本的安装程序（例如 `Bitwarden-Installer-1.32.1.exe`）和对应版本的资产包（例如 `Bitwarden-1.32.1-x64.nsis.7z`）。
2. 将下载的文件传输到离线机器，并**将它们放在同一目录下**。
3. 运行安装程序（例如 `Bitwarden-Installer-1.32.1.exe`）。如果所需的资产包位于同一目录下，则无需访问 Internet 即可安装 Bitwarden。

请注意，遵循离线安装过程意味着你的桌面 App 在新功能或补丁发布时将**不会自动更新**。

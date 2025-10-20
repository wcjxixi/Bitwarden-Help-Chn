# 软件发布支持

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/bitwarden-software-release-support/)、[GitHub 地址](https://github.com/bitwarden/help/blob/master/_articles/hosting/bitwarden-software-release-support.md)
{% endhint %}

Bitwarden 为 Bitwarden 服务器、Bitwarden 客户端以及其他支持的集成和模块维护软件版本。本文档介绍了 Bitwarden 遵循的软件生命周期政策，这些信息将帮助您准备适合您组织的更新。

作为一家打造全球可信产品的安全公司，Bitwarden 为我们所有的用户群维护最新和相应的软件版本，使其广泛可用且易于访问。

与此同时，我们也认识到需要在频繁的更新和发布周期之间取得平衡。我们还认识到，在较新系统上推进新功能和放弃对旧系统的支持之间需要取得平衡。（这里的「系统」指的是设备、操作系统、软件应用程序和框架）。

## Bitwarden 软件支持 <a href="#bitwarden-software-support" id="bitwarden-software-support"></a>

{% hint style="info" %}
如本文档中所述，「主版本」由 Bitwarden 客户端和服务器使用的版本格式中的第二个数字表示（例如 2025.`6`.0 或 2025.`7`.1）。
{% endhint %}

以下章节将介绍 Bitwarden 所开发软件的支持政策：

### Bitwarden Cloud 服务器 <a href="#bitwarden-cloud" id="bitwarden-cloud"></a>

Bitwarden Cloud 由 Bitwarden 直接运营和维护。我们会定期更新 Bitwarden Cloud 服务器，并在 [status.bitwarden.com](https://status.bitwarden.com/) 上发布更新信息。

### Bitwarden 自托管服务器 <a href="#bitwarden-server" id="bitwarden-server"></a>

对于采用订阅计划的自托管实施，Bitwarden 服务器会不断收到更新：

* 在给定时间内，Bitwarden 会维护当前的主要服务器版本和前 2 个主要服务器版本。
* 每个服务器版本都与同一主要客户端版本、前 2 个主要客户端版本以及后 2 个主要客户端版本兼容。

{% hint style="info" %}
自托管用户应保持其服务器最新，以获得最新的 Bitwarden 功能和支持，并与最新发布的客户端保持兼容。不根据 Bitwarden 版本支持策略更新客户端和服务器版本的自托管实例存在引入与其服务器不兼容的客户端变更的风险。
{% endhint %}

### Bitwarden 客户端 <a href="#bitwarden-clients" id="bitwarden-clients"></a>

对于 Bitwarden 客户端应用程序：

* 在给定时间内，Bitwarden 会维护当前的主要客户端版本和前两个主要客户端版本。
* 每个客户端版本都与同一主要服务器版本、前两个主要服务器版本以及后两个主要服务器版本兼容。

[了解如何检查客户端版本](versioning.md#client-version)。

### Bitwarden API

Bitwarden API 的发布周期和持续时间与 Bitwarden 服务器保持一致。作为一种惯例，我们的目标是通过语义版本化来无限期地提供 API 的向后兼容性。然而，如果我们添加的增强功能导致难以或无法保持向后兼容所有先前版本，我们将通过递增主要版本号来表示。

## 平台软件支持 <a href="#platform-software-support" id="platform-software-support"></a>

以下章节介绍了安装或使用 Bitwarden 的软件的支持政策：

### Bitwarden 客户端平台 <a href="#platforms-for-bitwarden-clients" id="platforms-for-bitwarden-clients"></a>

对于安装或使用 Bitwarden 客户端应用程序的所有底层平台，例如桌面或移动操作系统和网络浏览器版本，Bitwarden 致力于支持供应商当前支持的版本。

### 自托管 Bitwarden 服务器平台 <a href="#platforms-for-self-hosted-bitwarden-servers" id="platforms-for-self-hosted-bitwarden-servers"></a>

除非系统要求中另有规定，自托管安装应维护在最新的操作系统和计算平台上，并得到其供应商的积极支持。

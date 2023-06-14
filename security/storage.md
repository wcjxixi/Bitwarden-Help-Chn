# 数据存储

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/data-storage/)
{% endhint %}

本文介绍 Bitwarden 在何处存储您的密码库数据和管理数据。

在将任何内容发送到云服务器进行存储之前，Bitwarden **始终**会在本地设备上加密和/或哈希数据。**Bitwarden 服务器仅用于存储已被加密的数据**。有关更多信息，请参阅[加密](encryption.md)。

一些加密数据，包括用户的受保护对称密钥和主密码哈希，也由应用程序以透明方式静态加密，这意味着它们在流入和流出 Bitwarden 数据库时将被再次加密和解密。

Bitwarden 还使用 Azure 透明数据加密 (TDE) 通过对数据库、关联备份和静态事务日志文件执行实时加密和解密来防止恶意离线活动的威胁。

## 在 Bitwarden 服务器上 <a href="#on-bitwarden-servers" id="on-bitwarden-servers"></a>

Bitwarden 将所有数据安全地处理和存储在位于美国的 [Microsoft Azure Cloud](https://en.wikipedia.org/wiki/Microsoft\_Azure) 中，而 Microsoft Azure Cloud 使用由属于微软的团队管理的服务。由于 Bitwarden 仅使用 Azure 提供的服务，因此无需管理和维护服务器基础结构。运行时间、可伸缩性以及安全更新和保证均由 Microsoft 及其云基础架构提供支持。查看 [Microsoft Azure 合规性产品](https://azure.microsoft.com/en-us/resources/microsoft-azure-compliance-offerings/)文档以获取更多详细信息。

Bitwarden 维护用于灾难恢复的时间点恢复 (PITR) 策略。 Bitwarden 为此目的利用的功能不涉及创建或存储 BACPAC 或其他可移动备份文件，而是允许通过反向处理事务日志进行灾难恢复以使数据库与选定的时间点保持一致（请参阅 [Microsoft文档](https://learn.microsoft.com/en-us/azure/azure-sql/database/hyperscale-automated-backups-overview?view=azuresql)）。Bitwarden 为 PITR 配置了严格的 7 天保留策略和不长期保留策略。此功能**仅用于灾难恢复目的**，用户和组织负责创建和安全地存储他们自己的密码库数据的备份。Blob 存储的数据，特别是附件和 Send 文件，不受 PITR 功能的约束，一旦从 Bitwarden 中删除就无法恢复。

不信任 Bitwarden 服务器吗？不必这样。开源是美丽的，您可以轻松地自己托管整个 Bitwarden 堆栈，您的数据由你自己控制。在[这里](../self-hosting/install-and-deploy-guides/install-and-deploy-linux.md)了解更多。

## 在您的本地机器上 <a href="#on-your-local-machine" id="on-your-local-machine"></a>

存储在您的计算机/设备上的数据是被加密的，并且仅当您解锁您的密码库时才会被解密。被解密的数据仅存储在**内存中**，并且**永远不会被写入到持久存储**。加密的数据存储在以下静态位置：

### 桌面端 <a href="#desktop-app" id="desktop-app"></a>

* Windows
  * 标准安装版： `%AppData%\Bitwarden`
  * Microsoft Store 安装版：`%LocalAppData%\Packages\8bitSolutionsLLC.bitwardendesktop_h4e712dmw3xyy\LocalCache\Roaming\Bitwarden`
  * 便携版： `.\bitwarden-appdata`
* macOS
  * 标准安装版： `~/Library/Application Support/Bitwarden`
  * Mac App Store 版： `~/Library/Containers/com.bitwarden.desktop/Data/Library/Application Support/Bitwarden`
* Linux
  * 标准安装版： `~/.config/Bitwarden`
  * Snap 版： `~/snap/bitwarden/current/.config/Bitwarden`

{% hint style="success" %}
您可以通过将`BITWARDEN_APPDATA_DIR`环境变量值设置为绝对路径来覆盖 Bitwarden 桌面应用程序数据的存储位置。
{% endhint %}

### 浏览器扩展 <a href="#browser-extension" id="browser-extension"></a>

* Windows
  * Chrome：`%LocalAppData%\Google\Chrome\User Data\Default\Local Extension Settings\nngceckbapebfimnlniiiahkandclblb`
  * Firefox：`%AppData%\Roaming\Mozilla\Firefox\Profiles\your_profile\storage\default\moz-extension+++[UUID]^userContextId=[integer]`
  * Opera：`%AppData%\Opera Software\Opera Stable\Local Extension Settings\ccnckbpmaceehanjmeomladnmlffdjgn`
  * Vivaldi：`%LocalAppData%\Vivaldi\User Data\Default\Local Extension Settings\nngceckbapebfimnlniiiahkandclblb`
  * Brave：`%LocalAppData%\BraveSoftware\Brave-browser\User Data\Default\Local Extension Settings\nngceckbapebfimnlniiiahkandclblb`
  * Edge：`%LocalAppData%\Microsoft\Edge\User Data\Default\Extensions\jbkfoedolllekgbhcbcoahefnbanhhlh`
* macOS
  * Chrome：`~/Library/Application Support/Google/Chrome/Default/Local Extension Settings/nngceckbapebfimnlniiiahkandclblb`
  * Firefox：`~/Library/Application Support/Firefox/Profiles/your_profile/storage/default/moz-extension+++[UUID]^userContextID=[integer]`
  * Safari：`~/Library/Safari/Databases`
* Linux
  * Chrome：`~/.config/google-chrome/Default/Local Extension Settings/nngceckbapebfimnlniiiahkandclblb`
  * Firefox：`~/.mozilla/firefox/your_profile/storage/default/moz-extension+++[UUID]^userContextID=[integer]`

{% hint style="info" %}
为了增强安全性，Firefox 在扩展存储文件夹名称中使用通用唯一标识符（UUID）。打开`about:debugging#/runtime/this-firefox`页面（从 Firefox 的地址栏导航）找到您的 Bitwarden 扩展 UUID。用该 UUID 替换上面的 \[UUID]。还要注意，Firefox 允许用户自定义存储配置文件的位置（以及本地 Bitwarden 扩展数据）。上面指定的位置是默认位置。
{% endhint %}

### 移动端 <a href="#mobile" id="mobile"></a>

* iOS：`group.com.8bit.bitwarden` 应用程序组
* Android：`/data/data/com.x8bit.bitwarden/`

### CLI

* Windows：`%AppData%\Bitwarden CLI`
* macOS：`~/Library/Application Support/Bitwarden CLI`
* Linux：`~/.config/Bitwarden CLI`

{% hint style="success" %}
您可以通过将`BITWARDEN_APPDATA_DIR`环境变量值设置为绝对路径来覆盖 Bitwarden CLI 应用程序数据的存储位置。
{% endhint %}

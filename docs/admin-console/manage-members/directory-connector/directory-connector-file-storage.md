# Directory Connector 文件存储

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/directory-sync-shared/)
{% endhint %}

桌面 App 和 CLI [共享数据库和配置](directory-connector-file-storage.md)，因此不建议在一台机器上**同时**使用。建议使用[桌面 App](directory-connector-desktop-app.md) 完成配置和测试，然后使用 [CLI](directory-connector-cli.md) [调度自动同步](schedule-a-sync.md)到您的生产组织。

{% hint style="success" icon="lightbulb" %}
我们建议在调整 Directory Connector 配置文件之前使用桌面 App 或 CLI，因为**无法通过该文件设置 Directory Connector 的全部内容**。密钥或机密等身份验证的值必须通过[桌面 App](directory-connector-desktop-app.md) 或 [CLI](directory-connector-cli.md) 设置。
{% endhint %}

## 配置文件 <a href="#config-file" id="config-file"></a>

Directory Connector 配置文件 (`data.json`) 包含可以直接编辑的对象，以便于：

* 设置与您的目录的连接
* 配置同步选项

无法通过 `data.json` 文件设置 Directory Connector 的全部内容。例如密钥或密码等用于身份验证的值，这些值必须通过[桌面 App](directory-connector-desktop-app.md) 或 [CLI](directory-connector-cli.md) 来设置。

<i class="fa-arrow-down-to-bracket">:arrow-down-to-bracket:</i>[下载示例配置文件](https://bitwarden.com/assets/1Bkzdf50jZRPq0MRJ85FPi/68b92adf2f5399dc50df1b897a0c0729/data.json)

{% hint style="warning" %}
避免在 Directory Connector 桌面 App 或 CLI 可执行文件运行时打开或修改 `data.json` 文件。
{% endhint %}

### 位置 <a href="#location" id="location"></a>

&#x20;`data.json` 的位置取决于您使用的平台：

* Windows：
  * 安装版：`%AppData%\Bitwarden Directory Connector`
  * 便携版：`.\bitwarden-connector-appdata`
* macOS：`~/Library/Application Support/Bitwarden Directory Connector`
* Linux：`~/.config/Bitwarden Directory Connector`

{% hint style="success" icon="lightbulb" %}
当使用 Directory Connector CLI 时，运行 `data-file` 命令来获取 `data.json` 的绝对路径。
{% endhint %}

## 加密存储 <a href="#secret-storage" id="secret-storage"></a>

默认情况下，Directory Connector [桌面 App](directory-connector-desktop-app.md) 和 [CLI](directory-connector-cli.md) 都使用安全方法来持久化敏感数据（例如您的目录账户密码、API 密钥等等）。

在 Linux 系统上，这需要 [GNOME Ketring](https://wiki.archlinux.org/index.php/GNOME/Keyring) 和 [X11](https://en.wikipedia.org/wiki/X_Window_System)，它们通常保留用于桌面环境。如果您使用的是无头 Linux 环境，则可能会遇到以下错误：

```
Cannot autolaunch D-Bus without X11 $DISPLAY
```

### 无头环境下的加密存储 <a href="#secret-storage-in-headless-environments" id="secret-storage-in-headless-environments"></a>

如果没有安全的存储环境，则可以将 Directory Connector CLI 配置为使用纯文本存储密钥。要这样做，请设置以下环境变量以覆盖安全存储。比如通过运行 `sudo -H gedit /etc/environment`：

```systemd
BITWARDENCLI_CONNECTOR_PLAINTEXT_SECRETS=true
```

启用纯文本存储后，您可以直接从 `data.json` 配置文件中以纯文本配置所有设置项。

{% hint style="info" %}
纯文本的加密存储与 Directory Connector 桌面 App 不兼容。您只能将纯文本的加密存储与 Directory Connector CLI 一起使用。
{% endhint %}

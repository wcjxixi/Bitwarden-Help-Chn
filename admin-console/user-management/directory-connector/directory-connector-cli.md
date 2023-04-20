# 目录连接器 CLI

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/directory-sync-cli/)
{% endhint %}

目录连接器 CLI 适合在无法使用桌面 GUI 的环境中工作，或者如果您想要使用操作系统提供的工具（定时作业、计划任务等）对目录同步操作进行脚本编程时使用。目录连接器 CLI 可以在 Windows、macOS 和 Linux 发行版上跨平台使用。

## 入门 <a href="#getting-started" id="getting-started"></a>

要开始使用 Bitwarden 目录连接器 CLI：

1、从以下链接之一下载 CLI：

* <img src="../../../.gitbook/assets/os-windows-24.png" alt="" data-size="line"> [Windows CLI](https://vault.bitwarden.com/download/?app=connector\&platform=windows\&variant=cli-zip)
* <img src="../../../.gitbook/assets/apple-24.png" alt="" data-size="line">[ macOS CLI](https://vault.bitwarden.com/download/?app=connector\&platform=macos\&variant=cli-zip)
* <img src="../../../.gitbook/assets/linux-24.png" alt="" data-size="line">[ Linux CLI](https://vault.bitwarden.com/download/?app=connector\&platform=linux\&variant=cli-zip)

2、解压缩 `.zip` 并将其文件（`bwdc` 和 `keytar.node`）移动到您的  `$PATH` 中的 `/usr/local/bin` 或其他目录。请注意，`keytar.node` **必须**与主 `bwdc` 可执行文件位于同一目录中。

**对于 Linux：**如果尚未安装，请使用您的软件包管理器安装 `libsecret`：

```shell
apt-get install libsecret-1-0
brew install libsecret
```

**对于 Windows：**Windows 用户可以[将 `bwdc.exe` 添加到当前用户的 `PATH` 中](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/)。

3、运行下面的命令来验证 `bwdc` 命令在您的终端上是否可以正常工作：

```shell
bwdc --help
```

4、使用 `bwdc config <setting> <value>` 命令（参阅[命令参考](directory-connector-cli.md#ming-ling-can-kao)）将目录连接器 CLI 连接到您的目录。

5、通过编辑 `data.json` 文件（更多信息请参阅[目录连接器文件存储](directory-connector-file-storage.md)）来配置同步选项。使用 `bwdc data-file` 命令获取 `data.json` 文件的绝对路径。

可用的**同步选项**取决于使用的目录类型，因此请参考以下文章之一，以获取可供您使用的选项列表：

* [与 AD 或 LDAP 同步](sync-with-active-directory-or-ldap.md)
* [与 Azure AD 同步](sync-with-azure-ad.md)
* [与 G Suite（Google）同步](sync-with-google-workspace.md)
* [与 Okta 同步](sync-with-okta.md)
* [与 OneLogin 同步](sync-with-onelogin.md)

6、运行 `bwdc test` 命令以检查您的配置是否将同步预期结果。

7、当正确配置了目录和同步选项，并且 `bwdc test` 产生了预期的结果，请运行 `bwdc sync` 命令以启动实时同步操作。

## 命令参考

### login

`login` 命令用于使用您的[组织 API 密钥](../../bitwarden-public-api.md#authentication)登录目录连接器。如果您没有 API 密钥，请联系[组织的所有者](../user-types-and-access-control.md)。有以下几种使用 `login` 命令的方式：

* 自身：

```shell
bwdc login
```

通过 `bwdc login` 本身随后会提示您输入 `client_id` 和 `client_secret`。

* 带参数：

```shell
bwdc login organization.b5351047-89b6-820f-ad21016b6222 yUMB4trbqV1bavhEHGqbuGpz4AlHm9
```

* 使用保存的环境变量：

```systemd
BW_CLIENTID="organization.b5351047-89b6-820f-ad21016b6222"
BW_CLIENTSECRET="yUMB4trbqV1bavhEHGqbuGpz4AlHm9"

bwdc login
```

保存环境变量 `BW_CLIENTID` 和 `BW_CLIENTSECRET` 后，允许您仅使用 `bwdc login` 来登录目录连接器，这将检查这些变量，如果存在则使用它们。

如果这些环境变量不存在，系统将提示您输入 `client_id` 和 `client_secret`。

### logout

`logout` 命令用于登出目录连接器 CLI。

```shell
bwdc logout
```

### help <a href="#help" id="help"></a>

Bitwarden 目录连接器 CLI 是自带文档的，每条命令都有 `--help` 内容和示例。使用全局 `--help` 选项列出所有可用命令：

```shell
bwdc --help
```

在某一具体命令上使用 `--help` 选项以了解该命令的更多信息：

```shell
bwdc test --help
bwdc config --help
```

### test <a href="#test" id="test"></a>

`test` 命令用于查询您的目录并打印 JSON 格式的群组和用户数组，每当您运行真正的同步操作时，这些群组和用户将被同步到您的 Bitwarden 组织。

```shell
bwdc test
```

使用 `--last` 选项仅测试自上次成功同步以来的更改。

```shell
bwdc test --last
```

### sync <a href="#sync" id="sync"></a>

`sync` 命令用于运行实时的同步操作，并将数据推送到您的 Bitwarden 组织。

```shell
bwdc sync
```

同步的用户和群组将立即在您的 Bitwarden 组织中可用。新增加的用户将收到一封邀请加入您组织的电子邮件。

### last-sync <a href="#last-sync" id="last-sync"></a>

`last-sync` 命令用于返回上一次对用户或群组执行同步操作的 [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) 时间戳。您必须将 `<object>` 指定为 `users` 或 `groups` 才能运行此命令：

```shell
bwdc last-sync <object>
```

如果指定的对象未执行任何同步，则返回一个空响应。

### config <a href="#config" id="config"></a>

`config` 命令用于指定您的目录的设置。

```shell
bwdc config <setting> <value>
```

可用的选项包括：

* `server <server-url>`
* `directory <directory-type>`
* `ldap.password <password>`
* `azure.key <key>`
* `gsuite.key <key>`
* `okta.token <token>`
* `onelogin.secret <secret>`

{% hint style="success" %}
`ldap.password`、`azure.key`、`gsuite.key`、`okta.token` 以及 `onelogin.secret` **只能**使用 CLI 的 bwdc 命令修改，或者使用[桌面版应用程序](directory-connector-desktop-app.md)。
{% endhint %}

### data-file <a href="#data-file" id="data-file"></a>

`data-file` 命令用于返回目录连接器 CLI 所使用的 `data.json` 配置文件的绝对路径：

```shell
bwdc data-file
```

通过直接在您喜欢的文本编辑器中编辑 `data.json` 配置文件，来修改目录连接器 CLI 的配置设置项。

### clean-cache <a href="#clear-cache" id="clear-cache"></a>

`clear-cache` 命令用于清除在执行同步操作时应用程序存储的缓存数据。更多信息请参阅[清除同步缓存](clear-sync-cache.md)。

```shell
bwdc clear-cache
```

### update <a href="#update" id="update"></a>

`update` 命令用于检查目录连接器 CLI 是否是最新版本：

```shell
bwdc update
```

如果发现新版本，此命令将返回新版本的下载 URL 地址。**目录连接器 CLI 不会自动更新**。您需要使用此 URL 手动下载新版本。

{% hint style="warning" %}
如果您同时使用 CLI 和桌面版应用程序，确保它俩的版本是匹配的，这非常重要。运行两个不同版本的目录连接器，可能会导致意外问题。

使用全局选项 `--version` 查看目录连接器 CLI 的版本。
{% endhint %}

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

### 缺少 libsecret <a href="#libsecret-missing" id="libsecret-missing"></a>

如果收到有关 libsecret 共享对象的错误消息 `Error: libsecret-1.so.0: cannot open shared object file: No such file or directory`，您需要安装 libsecret，这是将内容安全地存储在主机上所必需的。

### dbus 错误 <a href="#dbus-errors" id="dbus-errors"></a>

如果您在使用 `bwdc config` 时收到有关 dbus 的错误消息，例如 `Failed to execute child process "dbus-launch" (No such file or directory)` 或 `Cannot autolaunch D-Bus without X11`，请分配以下环境变量以允许在 `data.json` 中明文存储密码：

```systemd
export BITWARDENCLI_CONNECTOR_PLAINTEXT_SECRETS=true
```

### 无法获取本地颁发者证书 <a href="#unable-to-get-local-issuer-certificate" id="unable-to-get-local-issuer-certificate"></a>

如果您收到一条 `unable to get local issuer certificate` 的错误消息，请将 `NODE_EXTRA_CA_CERTS` 变量设置到您的 `root.pem` 中，例如：

```systemd
export NODE_EXTRA_CA_CERTS="absolute/path/to/your/certificates.pem"
```

如果您使用的是桌面应用程序，可能收到以下错误：`Warning: Setting the NODE_TLS_REJECT_UNAUTHORIZED environment variable to '0' makes TLS connections and HTTPS requests insecure by disabling certificate verification.`

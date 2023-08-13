# =Secrets Manager CLI

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-cli/)
{% endhint %}

Secrets Manager 命令行界面 (CLI) 是用于检索和注入您的机密的强大工具。Secrets Manager CLI 通过 `create`、`delete`、`edit` 和 `list` 您的机密和工程来组织您的密码库。

Secrets Manager CLI 是自描述的。在命令行中，使用以下命令了解有关可用命令的更多信息：

```batch
bws --help, -h
```

## 下载和安装 <a href="#download-and-install" id="download-and-install"></a>

CLI 可以在 Windows、macOS 和 Linux 发行版上跨平台使用。要下载并安装 Secrets Manager CLI：

从 [https://github.com/bitwarden/sdk/releases](https://github.com/bitwarden/sdk/releases) 下载 Secrets Manager CLI。

## 身份验证 <a href="#authentication" id="authentication"></a>

可以使用为特定[服务账户](../your-secrets/service-accounts.md)生成的[访问令牌](../your-secrets/access-tokens.md)登录 Secrets Manager CLI。这意味着**只有对机密和工程有访问权限的服务账户可以使用 CLI 进行交互**。有多种方式可以对 CLI 会话进行身份验证：

{% tabs %}
{% tab title="环境变量" %}
您可以通过将访问令牌的值保存到环境变量 `BWS_ACCESS_TOKEN` 来对 CLI 会话进行身份验证，例如：

```batch
export BWS_ACCESS_TOKEN=0.48c78342-1635-48a6-accd-afbe01336365.C0tMmQqHnAp1h0gL8bngprlPOYutt0:B3h5D+YgLvFiQhWkIq6Bow==
```
{% endtab %}

{% tab title="Inline" %}
您可以在任何单个命令中使用 `-t`，`--access-token` 标志对单个 CLI 请求进行身份验证，例如：

```batch
bws list secrets --access-token 0.48c78342-1635-48a6-accd-afbe01336365.C0tMmQqHnAp1h0gL8bngprlPOYutt0:B3h5D+YgLvFiQhWkIq6Bow==
```
{% endtab %}
{% endtabs %}

## 命令 <a href="#commands" id="commands"></a>

命令用于与 Secrets Manager CLI 进行交互。机密和工程是否能被读取或写入，具体取决于授予您的特定访问令牌的权限。要获取 `secret` 和 `project` 命令的更多详细信息，请使用：

* `bws secret --help`
* `bws project --help`

{% hint style="info" %}
从 Secrets Manager 版本 0.3.0 开始，CLI 语法已更改。例如，列出机密的命令已从 `bws list secret` 更改为 `bws secret list`。

Secrets Manager CLI 将暂时保留对旧语法的支持。如果您不确定正在使用的 Secrets Manager CLI 的版本，请输入 `bws --version`。
{% endhint %}

## secret

### secret create

### secret delete

### secret edit

### secret get

### secret list

## project

### project create

### project delete

### project edit

### project get

### project list

## config

{% hint style="info" %}
虽然下面描述的功能是由 CLI 提供的，但有些功能是用于自托管的，这在 Secrets Manager 测试版期间不可用。
{% endhint %}

`config` 命令为 Secrets Manager CLI 指定要使用的服务器设置。可用的设置包括 `server-base`、`server-api` 和 `server-identity`，例如：

```batch
bws config server-base https://my_hosted_server.comText Copi
```

以这种方式完成后，您指定的服务器值将保存到 `~/.bws/config` 文件中作为默认个人资料。您可以使用后续选项来创建备用个人资料和配置文件：

### **config --profile**

将 `--profile` 选项与 `config` 命令一起使用可将指定的服务器值保存到备用个人资料，例如：

```batch
bws config server-base http://other_hosted_server.com --profile dev
```

创建后，您可以将该个人资料与其他命令一起使用以将请求路由到指定的服务器，例如：

```batch
bws get secret 2863ced6-eba1-48b4-b5c0-afa30104877a --profile dev
```

### **config --config-file**

将 `--config-file` 选项与 `config` 命令一起使用可将指定的服务器值保存到备用配置文件，例如将值保存到新配置文件中的默认个人资料：

```batch
bws config server-base http://third_hosted_server.com --config-file ~/.bws/alt_config
```

您可以将 `--config-file` 与 `--profile` 链接起来，以将值保存到备用配置文件中的备用个人资料，例如：

```batch
bws config server-base http://third_hosted_server.com --config-file ~/.bws/alt_config --profile alt_dev
```

创建后，您可以将该个人资料与其他命令一起使用以将请求路由到指定的服务器，例如：

```batch
bws get secret 2863ced6-eba1-48b4-b5c0-afa30104877a --config-file ~/.bws/alt_config --profile alt_dev
```

## 选项 <a href="#options" id="options"></a>

### -o, --output

默认情况下，Secrets Manager CLI 将返回一个 JSON 对象或 JSON 对象数组以响应命令。可以使用 `-o`，`--output` 标志以及以下选项之一更改输出的格式以满足您的需要：

* `json`：默认。输出 JSON。
* `yaml`：输出 YAML。
* `table`：输出一个 ASCII 表，其中键值作为列标题。
* `tsv`：输出没有键值的制表符分隔值。
* `none`：只输出错误和警告。

例如，命令 `bws get secret 2863ced6-eba1-48b4-b5c0-afa30104877a --output yaml` 将返回以下内容：

```javascript
object: secret
id: 2863ced6-eba1-48b4-b5c0-afa30104877a
organizationId: b8824f88-c57c-4a36-8b1a-afa300fe0b52
projectId: 1d0a63e8-3974-4cbd-a7e4-afa30102257e
key: Stripe API Key
value: osiundfpowubefpouwef
note: 'These are notes.'
creationDate: 2023-02-08T15:48:33.470701Z
revisionDate: 2023-02-08T15:48:33.470702Z
```

### -c, --color

可以通过指示是否需要彩色输出来进一步自定义输出。此选项的可用值为 `yes`、`no` 和 `auto`。

### --access-token

您可以将 `-t`，`--access-token` 选项与任何单个命令一起使用来验证单个 CLI 请求，例如：

```batch
bws list secrets --access-token 0.48c78342-1635-48a6-accd-afbe01336365.C0tMmQqHnAp1h0gL8bngprlPOYutt0:B3h5D+YgLvFiQhWkIq6Bow==
```

### --profile

将 `--profile` 选项与 `list` 或 `get` 命令一起使用以指定要使用的个人资料，例如：

```batch
bws get secret 2863ced6-eba1-48b4-b5c0-afa30104877a --profile dev
```

请参阅 `config` 命令（[此处](secrets-manager-cli.md#config)）以帮助理解和设置备用个人资料。

### --config-file

将 `--config-file` 选项与 `--profile` 选项和 `list` 或 `get` 命令一起使用，以指定要使用哪个配置文件中的哪个配置文件，例如：

```batch
bws get secret 2863ced6-eba1-48b4-b5c0-afa30104877a --config-file ~/.bws/alt_config --profile alt_dev
```

请参阅 `config` 命令（[此处](secrets-manager-cli.md#config)）以帮助理解和设置备用配置文件和个人资料。

### --server-url

此选项可用于设置 CLI 将向其发送与指定的命令关联的请求的服务器 URL，例如：

```batch
bws list secrets --server-url http://my_hosted_server.com
```

此选项将覆盖通过 `config` 命令配置的任何 URL（请参阅此处）。

### --help

使用此选项打印任何指定的 `bws` 命令的帮助。

### --version

使用此选项打印您正在使用的 `bws` 客户端的版本。

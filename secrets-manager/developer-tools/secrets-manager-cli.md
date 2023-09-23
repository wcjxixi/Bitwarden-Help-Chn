# Secrets Manager CLI

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

`secret` 命令用于访问、操作和创建[机密](../your-secrets/secrets.md)。与所有命令一样，访问令牌访问范围之外的机密和[工程](../your-secrets/projects.md)无法读取或写入。

### secret create

使用 `bws secret create` 创建一个新的机密。此命令需要 `KEY`、`VALUE` 和 `PROJECT_ID`：

```batch
bws secret create <KEY> <VALUE> <PROJECT_ID>
```

或者，您可以使用 `--note <NOTE>` 选项添加注释。例如：

```batch
bws secret create SES_KEY 0.982492bc-7f37-4475-9e60 f588b2f2-4780-4a78-be2a-b02d014d622f --note "API Key for AWS SES"
```

默认情况下，此命令将返回一个 JSON 对象并将机密保存到 Secrets Manager。您可以使用 `--output` 标志更改输出格式（[了解更多](secrets-manager-cli.md#o-output)）。

```javascript
{
  "object": "secret",
  "id": "be8e0ad8-d545-4017-a55a-b02f014d4158",
  "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
  "projectId": "e325ea69-a3ab-4dff-836f-b02e013fe530",
  "key": "SES_KEY",
  "value": "0.982492bc-7f37-4475-9e60",
  "note": "API Key for AWS SES",
  "creationDate": "2023-06-28T20:13:20.643567Z",
  "revisionDate": "2023-06-28T20:13:20.643567Z"
}
```

### secret delete

`bws secret delete` 命令用来删除 `SECRET_IDS` 指定的一个或多个机密。

```batch
bws secret delete <SECRET_IDS>
```

要删除 ID 为 `be8e0ad8-d545-4017-a55a-b02f014d4158` 的单个机密：

```batch
bws secret delete be8e0ad8-d545-4017-a55a-b02f014d4158
```

对于 ID 为 `382580ab-1368-4e85-bfa3-b02e01400c9f` 和 `47201c5c-5653-4e14-9007-b02f015b2d82` 的多个机密：

```batch
bws secret delete 382580ab-1368-4e85-bfa3-b02e01400c9f 47201c5c-5653-4e14-9007-b02f015b2d82
```

输出：

```
1 secret deleted successfully.
```

### secret edit

要编辑机密，以下结构会将更改应用于所选值。在 CLI 中，此命令可以编辑机密的 `KEY`、`VALUE`、`NOTE` 或 `PROJECT_ID`。

```batch
bws secret edit <SECRET_ID> --key <KEY> --value <VALUE> --note <NOTE> --project-id <PROJECT_ID>
```

例如，如果您希望向现有机密添加注释：

```batch
bws secret edit be8e0ad8-d545-4017-a55a-b02f014d4158 --note "I am adding a note"
```

{% hint style="info" %}
编辑包含空格的 `NOTE` 时，请在字符串两边加上引号。
{% endhint %}

要编辑多个字段，其中 `SES_KEY2` 是新的 `key`，`0.1982492bc-7f37-4475-9e60` 是新 `value`：

```batch
bws secret edit be8e0ad8-d545-4017-a55a-b02f014d4158 --key SES_KEY2 --value 0.1982492bc-7f37-4475-9e60
```

输出：

```javascript
{
  "object": "secret",
  "id": "be8e0ad8-d545-4017-a55a-b02f014d4158",
  "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
  "projectId": "e325ea69-a3ab-4dff-836f-b02e013fe530",
  "key": "SES_KEY2",
  "value": "0.1982492bc-7f37-4475-9e60",
  "note": "I am adding a note",
  "creationDate": "2023-06-28T20:13:20.643567Z",
  "revisionDate": "2023-06-28T20:45:37.46232Z"
}
```

### secret get

`bws secret get` 用于检索特定的机密：

```batch
bws secret get <SECRET_ID>
```

默认情况下，此命令将检索具有 `SECRET_ID` 的机密对象。

```batch
bws secret get be8e0ad8-d545-4017-a55a-b02f014d4158
```

默认情况下，`get` 将以 JSON 数组的形式返回对象，如以下示例所示。您可以使用 `--output` 标志更改输出格式（[了解更多](secrets-manager-cli.md#o-output)）。

```javascript
{
  "object": "secret",
  "id": "be8e0ad8-d545-4017-a55a-b02f014d4158",
  "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
  "projectId": "e325ea69-a3ab-4dff-836f-b02e013fe530",
  "key": "SES_KEY",
  "value": "0.982492bc-7f37-4475-9e60",
  "note": "",
  "creationDate": "2023-06-28T20:13:20.643567Z",
  "revisionDate": "2023-06-28T20:13:20.643567Z"
}
```

### secret list

要列出服务账户可以访问的机密，请使用以下命令：

```batch
bws secret list
```

您还可以使用以下命令仅列出特定项目中的机密，其中 `e325ea69-a3ab-4dff-836f-b02e013fe530` 表示项目标识符：

```batch
bws secret list e325ea69-a3ab-4dff-836f-b02e013fe530
```

默认情况下，`list` 将以 JSON 数组的形式返回对象，如下例所示。您可以使用 `--output` 标志更改输出格式（[了解更多](secrets-manager-cli.md#o-output)）。

```javascript
[
  {
    "object": "secret",
    "id": "382580ab-1368-4e85-bfa3-b02e01400c9f",
    "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
    "projectId": "e325ea69-a3ab-4dff-836f-b02e013fe530",
    "key": "Repository 1",
    "value": "1234567ertthrjytkuy",
    "note": "Main Repo",
    "creationDate": "2023-06-27T19:25:15.822004Z",
    "revisionDate": "2023-06-27T19:25:15.822004Z"
  },
  {
    "object": "secret",
    "id": "be8e0ad8-d545-4017-a55a-b02f014d4158",
    "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
    "projectId": "e325ea69-a3ab-4dff-836f-b02e013fe530",
    "key": "SES_KEY",
    "value": "0.982492bc-7f37-4475-9e60",
    "note": "",
    "creationDate": "2023-06-28T20:13:20.643567Z",
    "revisionDate": "2023-06-28T20:13:20.643567Z"
  }
]
```

## project

`project` 命令用于访问、操作和创建[工程](../your-secrets/projects.md)。分配给您的服务账户的访问范围将决定可以使用 `project` 命令完成哪些操作。

{% hint style="info" %}
工程可以由具有只读访问权限的服务账户创建。但是，如果此服务账户没有**读取**和**写入**访问权限，则无法编辑不是由其创建的现有工程。
{% endhint %}

### project create

`bws project create` 用于创建一个新的工程。此命令需要一个 `NAME`。

```batch
bws project create <NAME>
```

在此示例中，将创建一个名为 `My project` 的工程。

```batch
bws project create "My project"
```

默认情况下，`bws project create` 将以 JSON 数组的形式返回对象，如下例所示。您可以使用 `--output` 标志更改输出格式（[了解更多](secrets-manager-cli.md#huan-jing-bian-liang)）。

```javascript
{
  "object": "project",
  "id": "1c80965c-acb3-486e-ac24-b03000dc7318",
  "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
  "name": "My project",
  "creationDate": "2023-06-29T13:22:37.942559Z",
  "revisionDate": "2023-06-29T13:22:37.942559Z"
}
```

### project delete

`bws project delete` 用于删除 `PROJECT_IDS` 指定的一个或多个工程。

```batch
bws project delete <PROJECT_IDS>
```

对于单个项目，其中 `f1fe5978-0aa1-4bb0-949b-b03000e0402a` 代表 `PROJECT_ID`：

```batch
bws project delete f1fe5978-0aa1-4bb0-949b-b03000e0402a
```

对于多个项目，其中 `1c80965c-acb3-486e-ac24-b03000dc7318` 和 `f277fd80-1bd2-4532-94b2-b03000e00c6c` 代表 `PROJECT_IDS`：

```batch
bws project delete 1c80965c-acb3-486e-ac24-b03000dc7318 f277fd80-1bd2-4532-94b2-b03000e00c6c
```

输出：

```
1 project deleted successfully.
```

### project edit

用 `edit` 命令，您可以通过以下输入更改g工程的名称：

```batch
bws project edit <PROJECT_ID> --name <NEW_NAME>
```

例如，此命令会将项目名称更改为 `My project 2`。

```batch
bws project edit 1c80965c-acb3-486e-ac24-b03000dc7318 --name "My project 2"
```

默认情况下，`bws project edit` 将返回 JSON 数组形式的对象，如下例所示。您可以使用 `--output` 标志更改输出格式（[了解更多](secrets-manager-cli.md#o-output)）。

```javascript
{
  "object": "project",
  "id": "1c80965c-acb3-486e-ac24-b03000dc7318",
  "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
  "name": "My project 2",
  "creationDate": "2023-06-29T13:22:37.942559Z",
  "revisionDate": "2023-06-29T13:31:07.927829Z"
}
```

### project get

`get` 命令检索已登录的服务账户可以从您的密码库访问的特定工程。无法检索密码库中服务账户无权访问的对象。

```batch
bws project get <PROJECT_ID>
```

要获取特定工程，请使用以下命令，其中 `e325ea69-a3ab-4dff-836f-b02e013fe530` 代表 `PROJECT_ID`：

```batch
bws project get e325ea69-a3ab-4dff-836f-b02e013fe530
```

默认情况下，`get` 将返回 JSON 数组形式的对象，如下例所示。您可以使用 `--output` 标志更改输出格式（[了解更多](secrets-manager-cli.md#o-output)）。

```javascript
{
  "object": "project",
  "id": "e325ea69-a3ab-4dff-836f-b02e013fe530",
  "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
  "name": "App 1",
  "creationDate": "2023-06-27T19:24:42.181607Z",
  "revisionDate": "2023-06-27T19:24:42.181607Z"
}
```

### project list

要列出此服务账户有权访问的工程，请使用以下命令：

```batch
bws project list
```

默认情况下，`list` 将返回 JSON 数组形式的对象，如下例所示。您可以使用 `--output` 标志更改输出格式（[了解更多](secrets-manager-cli.md#o-output)）。

```javascript
[
  {
    "object": "project",
    "id": "e325ea69-a3ab-4dff-836f-b02e013fe530",
    "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
    "name": "App 1",
    "creationDate": "2023-06-27T19:24:42.181607Z",
    "revisionDate": "2023-06-27T19:24:42.181607Z"
  }.
  ...
]
```

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

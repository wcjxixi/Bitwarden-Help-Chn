# CLI 上的 Send

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/send-cli/)
{% endhint %}

> **\[译者注]**：
>
> * stdout：标准输出
> * stdin：标准输入
> * stderr：标准错误输出
>
> stdout 和 stderr 默认都是输出到终端（屏幕）。[参考链接](https://zh.wikipedia.org/wiki/%E6%A8%99%E6%BA%96%E4%B8%B2%E6%B5%81)

Bitwarden Send 是一套功能齐全的 CLI 命令。本文介绍了 `bw send` 命令的范围，但是 Send 并**不是一个独立于 Bitwarden 命令行界面（CLI）的工具**。因此，[CLI 文档](../password-manager/developer-tools/password-manager-cli.md)中的许多命令、选项和概念与这里的都是相关联的。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6hWfoRgu1yoyrXEB6JqN6E/35bc0f96642a57df42f1b2e6fa7c4c19/send-cli.png?fm=webp&h=433&q=50&w=961" %}

## send

`send` 命令是用于访问所有与 Send 相关的子命令的主命令：

```shell
bw send [options] [command] <data>
```

`send` 命令还可以作为快速 `create` 一个 Send 的快捷方式，例如：

```shell
bw send "Fastest Send in the West."
```

将创建一个内容为 `Fastest Send in the West` 的文本 Send 对象并输出 Send 链接。或者，例如：

```shell
bw send -f <path/to/file.ext>
```

将创建一个具有在指定 `path` 下的文件的文件 Send 对象并输出 Send 链接。

**选项**：

* `-n <name>` 或 `--name <name>` 用于指定 Send 的名称。如果没有指定名称，对于文本 Send，名称默认为 `id`，对于文件 Send，默认为文件名。对于多个字的名称，使用引号 `"<name>"`。
* `-d <days>` 或 `--deleteInDays <days>` 用于指定 Send 的删除日期（如果没有指定，默认为 7 天）。
* `--hidden` 用于指定文本 Send 要求接收者[切换可见性](send-privacy.md#hide-text)。
* `--notes <notes>` 用于添加私密备注到 Send 中。对于多个字的备注，使用引号 `"<notes>"`。
* `--fullObject` 用于将完整的 Send 对象输出为 JSON，而不是只输出 Send 链接（将此选项与 `--pretty` 选项配对使用，以获得格式化的 JSON）。

**完整的示例**：

```shell
bw send -n "My First Send" -d 7 --hidden "The contents of my first Send."
```

### create

`create` 命令用于创建一个 Send。与仅使用 `bw send` 相比，`create` 允许进行更高级的配置，接受已编码的 JSON 作为其参数：

```shell
bw send create [options] <encodedJson>
```

一个典型的工作流程大致像这样：

1. 使用 `template` 命令（参阅[详情](send-from-cli.md#template)）为您的 Send 类型输出合适的 JSON 模板。
2. 使用[像 jq 这样的命令行 JSON 处理器](https://stedolan.github.io/jq/)，根据需要处理输出的模板。
3. 使用 `encode` 命令（参阅[详情](../password-manager/developer-tools/password-manager-cli.md#encode)）对处理后的 JSON 进行编码。
4. 使用 `create` 命令从编码后的 JSON 创建一个 Send。

例如，要创建一个文本 Send：

```shell
bw send template send.text | jq '.name="My First Send" | .text.text="Secrets I want to share."' | bw encode | bw send create
```

例如，要创建一个文件 Send：

```shell
bw send template send.file | jq '.name="My File Send" | .type=1 | .file.fileName="paperwork.png" | .password="p@ssw0rd"' | bw encode | bw send create
```

例如，要创建一个有密码保护的文件 Send，并带有明确的[删除日期](send-lifespan.md#deletion-date)。不同的操作系统，对于指定 `.deletionDate=` 的方式不一样：

{% tabs %}
{% tab title="Windows" %}
```powershell
$delDate = (Get-Date).AddDays(14) | date -UFormat "%Y-%m-%dT%H:%M:%SZ"

bw send template send.text | jq ".name=\`"My Send\`" | .text.text=\`"Secrets I want to share.\`" | .password=\`"password\`" | .deletionDate=\`"$delDate\`"" | bw encode | bw send create
```

注意在此示例中，于在 Send 中配置了 `.deletionDate` 嵌套的 `date` 变量，因此 jq 调用必须使用双引号（`" "`）进行包裹，并对每个筛选器使用转义符（`\`）。
{% endtab %}

{% tab title="macOS" %}
```shell
bw send template send.text | jq ".name=\"My Send\" | .text.text=\"Secrets I want to share.\" | .password=\"mypassword\" | .deletionDate=\"$(date -uv+14d +"%Y-%m-%dT%H:%M:%SZ")\"" | bw encode | bw send create
```

注意在此示例中，于在 Send 中配置了 `.deletionDate` 嵌套的 `date` 变量，因此 jq 调用必须使用双引号（`" "`）进行包裹，并对每个筛选器使用转义符（`\`）。
{% endtab %}

{% tab title="Linux" %}
```shell
bw send template send.text | jq ".name=\"My Send\" | .text.text=\"Secrets I want to share.\" | .password=\"mypassword\" | .deletionDate=\"$(date "+%Y-%m-%dT%H:%M:%SZ" -d "+14 days")\"" | bw encode | bw send create
```

注意在此示例中，于在 Send 中配置了 `.deletionDate` 嵌套的 `date` 变量，因此 jq 调用必须使用双引号（`" "`）进行包裹，并对每个筛选器使用转义符（`\`）。
{% endtab %}
{% endtabs %}

**选项**：

* `--file <path>` 用于指定 Send 的文件（也可以在已编码的 JSON 中指定）。
* `--text <text>` 用于指定 Send 的文本（也可以在已编码的 JSON 中指定）。
*   `--hidden` 用于指定文本 Send 要求接收者[切换可见性](send-privacy.md#hide-text)。


* `--password <password>` 用于指定访问[密码保护](send-privacy.md#send-passwords)的密码。
* `--fullObject` 用于将完整的 Send 对象输出为 JSON，而不是只输出 Send 链接（将此选项与 `--pretty` 选项配对使用，以获得格式化的 JSON）。

### get&#xD;

`get` 命令用于检索您拥有的 Send 并将其作为 JSON 对象输出。`get` 接受一个确切的 `id` 值或任何字符串作为其参数。如果使用字符串，`get` 将会在您的 Send 中搜索一个与之匹配的值：

```shell
bw send get [options] <id / string>
```

如果你在另一个 Bitwarden 应用程序中创建了一个 Send，而这个会话仍然处于活动状态，使用 `bw sync` 命令将提取最近的 Send。有关更多信息，请参阅我们的 [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。

**选项**：

* `--text` 用于只输出文本 Send 的文本内容。
* `--file` 用于只输出文件 Send 的文件内容。将 `--file` 与 `--output` 搭配使用，用于指定一个目录，或者与 `--raw` 搭配使用，用于输出到 stdout。
* `--output <output>` 用于为 `--file` 选项指定输出目录。

### edit&#xD;

`edit` 命令用于编辑一个现有的 Send 对象。`edit` 接受已编码的 JSON 作为其参数：

```shell
bw send edit <encodedJson>
```

一个典型的工作流程大致像这样：

1. 使用 `get` 命令（参阅[详情](send-from-cli.md#get)）来根据 `<id>` 检索所需的 Send。
2. 使用[像 jq 这样的命令行JSON处理器](https://stedolan.github.io/jq/)，来根据需要处理检索到的 Send。
3. 使用 `encode` 命令（参阅[详情](../password-manager/developer-tools/password-manager-cli.md#encode)）对处理后的 JSON 进行编码。
4. 使用 `create` 命令从编码后的 JSON 创建一个 Send。

示例：

```shell
bw send get <id> | jq '.name="New Name" | .password=null' | bw encode | bw send edit
```

**选项**：

* `--itemid <itemid>` 用一个新的 id 值覆盖 Send 提供的 id 值。

{% hint style="info" %}
您不能 `edit` 一个文件 Send 的文件。要这样做，您需要删除此 Send 然后使用适当的文件重新创建它。
{% endhint %}

### list

`list` 命令用于列出您拥有的所有 Send 并将其作为 JSON 输出：

```shell
bw send list [options]
```

如果你在另一个 Bitwarden 应用程序中创建了一个 Send，而这个会话仍然处于活动状态，使用 `bw sync` 命令将提取最近的 Send。有关更多信息，请参阅我们的 [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。

**选项**：

* `--pretty` 用于格式化输出的 JSON。
*   `>` 运算符用于使用管道将 stdout 传输到文件，例如：

    ```
    bw send list --pretty  > /Users/myaccount/Documents/pretty_list_of_sends.json
    ```

### delete&#xD;

`delete` 命令用于删除您所拥有的一个 Send。`delete` 命令接受一个精确的 `id` 值作为其参数：

```shell
bw send delete <id>
```

{% hint style="success" %}
如果您不知道要删除的 Send 的确切 `id`，请使用 `bw send get <search term>` 进行查找。
{% endhint %}

### template&#xD;

`template` 命令用于返回一个 Send 对象的预期 JSON 格式，`template` 接受一个 `<object>` 规格作为其参数，可以是 `send.text` 或 `send.file`：

```shell
bw send template <object>
```

虽然你可以使用 `template` 将格式输出到你的屏幕上，但最常见的使用范例是将输出的内容用管道输送到 `bw send create` 操作中，使用[像 jq 这样的命令行 JSON 处理器](https://stedolan.github.io/jq/)和 `bw encode` 来操作从模板中检索的值，例如：

```shell
bw send template send.text | jq '.name="My First Send" | .text.text="Secrets I want to share."' | bw encode | bw send create
```

## receive

`receive` 命令用于访问 Send。`receive` 接受 Send `<url>`  作为其参数：

```shell
bw send receive [options] <url>
```

* 对于文本 Send，`receive` 将返回 Send 的文本内容到 stdout。
* 对于文件 Send，`receive` 将文件下载到当前工作目录。

**选项**：

* `--password <password>` 用于提供一个字符串作为访问受密码保护的 Send 所需的密码。
* `--passwordenv <passwordenv>` 用于指定一个已存储的环境变量作为访问受密码保护的 Send 所需的密码。
* `--passwordfile <passwordfile>` 用于指定文件的第一行作为访问受密码保护的 Send 所需的密码。
* `--obj` 用于将完整的 Send 对象输出为 JSON，而不是只输出 Send 链接（将此选项与 `--pretty` 选项配对使用，以获得格式化的 JSON）。
* `--ouput <output>` 用于指定文件 Send 内容的输出目录。

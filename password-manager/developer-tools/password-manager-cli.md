# 密码管理器 CLI

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/cli/)
{% endhint %}

Bitwarden 命令行界面（CLI）是一个强大且功能齐全的工具，用于访问和管理您的密码库。您在其他 Bitwarden 客户端应用程序（桌面、浏览器扩展等）能找到的许多功能也可以通过 CLI 实现。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/269bjiuC0f18YVu0VYJO9V/e192e552baa3bfe2f2efba30161f4a70/cli.png?fm=webp&h=578&q=50&w=799" %}
Bitwarden CLI
{% endembed %}

Bitwarden CLI 是自带文档的。在命令行中，使用以下命令了解可用的命令：

```batch
bw --help
```

或者，在任何 `bw` 命令上传递 `--help` 选项，以查看命令可用的选项和示例：

```batch
bw list --help

bw share --help
```

您所需要的大部分信息都可以通过 `--help` 来获取，然而这篇文章复制了所有这些信息，并对一些主题进行了更深入的探讨。

## 下载和安装 <a href="#download-and-install" id="download-and-install"></a>

可以在 Windows、macOS 和 Linux 发行版上跨平台使用 CLI。根据需要选择下载和安装 Bitwarden CLI 的方式：

{% tabs %}
{% tab title="本地可执行文件" %}
CLI 的本地打包版本可用于每个平台，并且无须依赖。使用以下链接之一下载：

* <img src="../../.gitbook/assets/os-windows-24.png" alt="" data-size="line"> [Windows x64](https://vault.bitwarden.com/download/?app=cli\&platform=windows)
* <img src="../../.gitbook/assets/apple-24.png" alt="" data-size="line"> [macOS x64](https://vault.bitwarden.com/download/?app=cli\&platform=macos)
* <img src="../../.gitbook/assets/linux-24.png" alt="" data-size="line"> [Linux x64](https://vault.bitwarden.com/download/?app=cli\&platform=linux)

{% hint style="success" %}
在 UNIX 系统中，您可能会收到 `Permission denied` （权限被拒绝）的消息。通过运行下面的命令授予权限：：

```batch
bash chmod +x </path/to/executable>
```
{% endhint %}
{% endtab %}

{% tab title="NPM" %}
如果您的系统上已安装了 Node.js，则可以使用 NPM 安装 CLI。使用 NPM 进行安装是使安装保持最新的最简单方式，并且**对于已经熟悉 NPM 的用户来说，它应该是首选的方式**：

```batch
npm install -g @bitwarden/cli
```

在 [npmjs.org](https://www.npmjs.com/package/@bitwarden/cli) 上查看该软件包。
{% endtab %}

{% tab title="Chocolatey" %}
要使用 Chocolatey 进行安装：

```batch
choco install bitwarden-cli
```

在 [community.chocolatey.org](https://chocolatey.org/packages/bitwarden-cli) 上查看该软件包。
{% endtab %}

{% tab title="Snap" %}
要使用 Snap 进行安装：

```batch
sudo snap install bw
```

在 [snapcraft.io](https://snapcraft.io/bw) 上查看该软件包。
{% endtab %}
{% endtabs %}

## 登录 <a href="#log-in" id="log-in"></a>

使用 `login` 命令登录 Bitwarden CLI 共有三种方式，每种方式适用于不同的场景。请查看以下选项以确定使用哪种方式：

* [使用电子邮件和密码](password-manager-cli.md#using-email-and-password)
* [使用 API 密钥](password-manager-cli.md#using-an-api-key)
* [使用 SSO](password-manager-cli.md#using-sso)

{% hint style="success" %}
[使用电子邮件和密码](password-manager-cli.md#using-email-and-password)方式登录将使用您的主密码，因此可以将 `login` 和 `unlock` 命令串在一起，以验证您的身份并同时解密您的密码库。如果您直接使用密码库数据，则[使用 API 密钥](password-manager-cli.md#using-an-api-key)或 [SSO](password-manager-cli.md#using-sso) 方式将要求您在 `login` 命令后紧接着使用显式 `bw unlock` 命令。

这是因为您的主密码是解密密码库数据所必须的密钥的来源。但是，有一些命令不需要您的密码库已解密，包括 `config`、`encode`、`generate`、`update` 以及 `status`。
{% endhint %}

### 使用电子邮件和密码 <a href="#using-email-and-password" id="using-email-and-password"></a>

电子邮件和密码方式的登录**建议用于交互式会话场景**。要使用电子邮件和密码登录：

```batch
bw login
```

此命令将提示您输入**电子邮件地址**、**主密码**和**两步登录代码**（若[已启用](../../two-step-login/two-step-login-methods.md)）。CLI 目前支持[身份验证器](../../two-step-login/setup-guides/two-step-login-via-authenticator.md)、[电子邮件](../../two-step-login/setup-guides/two-step-login-via-email.md)或 [YubiKey](../../two-step-login/setup-guides/two-step-login-via-yubikey.md) 方式的两步登录。

您可以像如下的示例那样将这些因素组合成一个命令，但是出于安全原因不建议这样操作。

```batch
bw login [email] [password] --method <method> --code <code>
```

有关两步登录的 `<method>` 值，请参阅[附录 → 枚举](password-manager-cli.md#enums)。

{% hint style="success" %}
**提示进行额外的身份验证**或收到 `Your authentication request appears to be coming from a bot.` 的错误提示？请使用您的 API 密钥 `client_secret` 回答身份验证挑战。[了解更多](cli-authentication-challenges.md)。
{% endhint %}

### 使用 API 密钥 <a href="#using-an-api-key" id="using-an-api-key"></a>

[个人 API 密钥](personal-api-key-for-cli-authentication.md)方式的登录**建议用于自动化工作流程或对外部应用程序提供访问的场景**。要使用 API ​​密钥方式登录：

```batch
bw login --apikey
```

此命令将提示您输入个人 `client_id` 和 `client_secret`。使用这些值对您的会话进行身份验证后，您就可以使用 `unlock` 命令了（[了解更多](password-manager-cli.md#unlock)）。

{% hint style="success" %}
如果您的组织[要求 SSO](../../organizations/enterprise-policies.md#single-sign-on-authentication)，您仍然可以使用 `--apikey` 登录 CLI。
{% endhint %}

#### 使用 API 密钥环境变量 <a href="#using-api-key-environment-variables" id="using-api-key-environment-variables"></a>

在使用 Bitwarden CLI 完成自动化工作的场景中，您可以保存环境变量以避免在身份验证时需要手动介入。

<table><thead><tr><th>环境变量名称</th><th>要求的值</th><th data-hidden></th></tr></thead><tbody><tr><td>BW_CLIENTID</td><td><code>client_id</code></td><td></td></tr><tr><td>BW_CLIENTSECRET</td><td><code>client_secret</code></td><td></td></tr></tbody></table>

### 使用 SSO <a href="#using-sso" id="using-sso"></a>

[SSO](../../login-with-sso/about-login-with-sso.md) 方式的登录**建议用于组织要求 SSO 身份验证的场景**。要使用 SSO 方式登录：

```batch
bw login --sso
```

此命令将在您的 Web 浏览器中启动 SSO 身份验证流程。您的会话通过身份验证后，您就可以使用 `unlock` 命令了（[了解更多](password-manager-cli.md#unlock)）。

{% hint style="success" %}
如果您的组织[要求 SSO](../../organizations/enterprise-policies.md#single-sign-on-authentication)，您仍然可以使用 `--apikey` 登录 CLI。
{% endhint %}

## 解锁 <a href="#unlock" id="unlock"></a>

如果您直接使用密码库数据，则[使用 API 密钥](password-manager-cli.md#using-an-api-key)或 [SSO](password-manager-cli.md#using-sso) 方式将要求您在 `login` 命令后紧接着使用显式 `bw unlock` 命令。

解锁密码库会生成一个**会话密钥**，此会话密钥作为解密密钥用于与密码库中的数据进行交互。[会话密钥必须用于](password-manager-cli.md#using-a-session-key)执行任何涉及密码库数据的命令（例如：`list`、`get`、`edit`）。您可以在任何时候使用以下方法生成一个新的会话密钥：

```batch
bw unlock
```

### 解锁选项 <a href="#unlock-options" id="unlock-options"></a>

您可以像如下的示例那样为 `bw unlock` 添加 `--passwordenv <passwordenv>` 选项或 `--passwordfile <passwordfiles>` 选项来使用您的主密码，而不需要手动输入：

```batch
bw unlock --passwordenv BW_PASSWORD
```

将查找环境变量 `BW_PASSWORD`。如果 `BW_PASSWORD` 为非空且具有正确的值，则 CLI 将成功解锁并返回一个会话密钥。

```batch
bw unlock --passwordfile ~/Users/Me/Documents/mp.txt
```

将查找文件 `~Users/Me/Documents/mp.txt`（必须将您的主密码作为第一行）。如果文件非空且具有正确的值，CLI 将成功解锁并返回一个会话密钥。

{% hint style="warning" %}
如果您使用 `--passwordfile` 选项，请通过将访问权限锁定到仅需要运行 `bw unlock` 的用户并仅向该用户提供读取访问权限来保护您的密码文件。
{% endhint %}

### 使用会话密钥 <a href="#using-a-session-key" id="using-a-session-key"></a>

当您使用电子邮件和密码方式的 `bw login` 或 `bw unlock` 解锁您的密码库时，CLI 将同时返回 `export BW_SESSION`（Bash）和 `env:BW_SESSION`（PowerShell）命令，其中包含了您的会话密钥。复制并粘贴相关条目以保存所需的环境变量。

如果设置了 `BW_SESSION` 环境变量，`bw` 命令将引用该变量，以干净清爽地运行，例如：

```batch
export BW_SESSION="5PBYGU+5yt3RHcCjoeJKx/wByU34vokGRZjXpSH7Ylo8w=="

bw list items
```

另外，如果您未设置环境变量，则可以在每个 `bw` 命令中将会话密钥作为选项传递：

```batch
bw list items --session "5PBYGU+5yt3RHcCjoeJKx/wByU34vokGRZjXpSH7Ylo8w=="
```

{% hint style="success" %}
`BW_SESSION` 环境变量仅绑定到活动的终端会话，因此关闭终端窗口等同于锁定密码库。您也可以通过运行以下命令来销毁一个活动会话密钥以锁定您的密码库：

```shell
bw lock
```
{% endhint %}

## 核心命令 <a href="#core-commands" id="core-commands"></a>

### create

`create` 命令用于在您的密码库中创建一个新的对象（ `item`，`attachment` 等）：

```batch
bw create (item|attachment|folder|org-collection) <encodedJson> [options]
```

`create` 命令使用已编码的 JSON。创建一个对象的典型工作流程大致为：

1. 使用 `get template` 命令（请参阅[详细信息](password-manager-cli.md#get-template)）为对象类型输出适当的 JSON 模板。
2. 使用 [jq 之类的命令行 JSON 处理器](https://stedolan.github.io/jq/)根据需要操作已输出的模板。
3. 使用 `encode` 命令（请参阅[详细信息](password-manager-cli.md#encode)）对已操作的 JSON 进行编码。
4. 使用 `create` 命令从已编码的 JSON 创建一个对象。

示例：

```batch
bw get template folder | jq '.name="My First Folder"' | bw encode | bw create folder
```

或：

```batch
bw get template item | jq ".name=\"My Login Item\" | .login=$(bw get template item.login | jq '.username="jdoe" | .password="myp@ssword123"')" | bw encode | bw create item
```

创建成功后，新创建的对象将作为 JSON 返回。

#### create 其他项目类型 <a href="#create-other-item-types" id="create-other-item-types"></a>

`create` 命令默认创建登录项目，但您可以使用 [jq 之类的命令行 JSON 处理器](https://stedolan.github.io/jq/)更改 `.type=` 属性以创建其他项目类型：

| 名称   | 值         |
| ---- | --------- |
| 登录   | `.type=1` |
| 安全笔记 | `.type=2` |
| 支付卡  | `.type=3` |
| 身份   | `.type=4` |

例如，以下命令将创建一个安全笔记：

```batch
bw get template item | jq '.type = 2 | .secureNote.type = 0 | .notes = "Contents of my Secure Note." | .name = "My Secure Note"' | bw encode | bw create item
```

{% hint style="info" %}
请注意，在上面的示例中，安全笔记需要一个子模板（`.secureNote.type`）。您可以使用 `bw get template` 查看项目类型的子模板（详细见[此处](password-manager-cli.md#get)）。
{% endhint %}

#### **create** attachment <a href="#create-attachment" id="create-attachment"></a>

`create attachment` 命令用于将一个文件附加到一个**现有的**项目上。

与其他 `create` 操作不同，您无需使用 JSON 处理器或 `encode` 即可创建附件。相反，它使用 `--file` 选项指定要附加的文件，使用 `--itemid` 选项指定要附加到的项目。例如：

```batch
bw create attachment --file ./path/to/file --itemid 16b15b89-65b3-4639-ad2a-95052a6d8f66
```

{% hint style="success" %}
如果您不知道您要使用的确切的 `itemid`，请使用 `bw get item <search-term>` 以返回该项目（请参阅[详细信息](password-manager-cli.md#get)），包括它的 `id`。
{% endhint %}

### get

`get` 命令用于从您的密码库中检索单个对象（ `item`、`username`、`password`等）：

```batch
bw get (item|username|password|uri|totp|exposed|attachment|folder|collection|organization|org-collection|template|fingerprint) <id> [options]
```

`get` 命令使用项目 `id` 或字符串作为它的参数。如果你使用一个字符串（即除确切的 `id` 以外的任何东西），`get` 将检索您的密码库以寻找一个具有匹配值的对象。例如，下面的命令将返回一个 Github 密码：

```batch
bw get password Github
```

{% hint style="info" %}
`get` 命令**只能返回一个结果**，因此您应该使用明确的搜索词。如果找到多个结果，CLI 将返回错误。
{% endhint %}

#### **get attachment** <a href="#get-attachment" id="get-attachment"></a>

`get attachment` 命令用于下载文件附件：

```batch
bw get attachment <filename> --itemid <id>
```

`get attachment` 命令使用一个 `filename` 和**确切的** `id`。默认情况下，`get attachment` 将附件下载到当前工作目录。你可以使用 `--output` 选项来指定一个不同的输出目录，例如：

```batch
bw get attachment photo.png --itemid 99ee88d2-6046-4ea7-92c2-acac464b1412 --output /Users/myaccount/Pictures/
```

{% hint style="info" %}
使用 `--output` 时，路径必须以正斜杠（`/`）结尾，以指定一个目录或者一个文件名（`/Users/myaccount/Pictures/photo.png`）。
{% endhint %}

#### **get template** <a href="#get-template" id="get-template"></a>

&#x20;`get template` 命令用于返回对象预期的 JSON 格式（`item`、`item.field`、`item.login` 等）：

```batch
bw get template (item|item.field|item.login|item.login.uri|item.card|item.identity|item.securenote|folder|collection|item-collections|org-collection)
```

虽然你_可以_使用 `get template` 将格式输出到你的屏幕上，但最常见的用法是将输出的数据输送到  `bw create` 操作中，使用 [jq 之类的命令行 JSON 处理器](https://stedolan.github.io/jq/)和 `bw encode` 来处理从模板获取的值，例如：

```batch
bw get template folder | jq '.name="My First Folder"' | bw encode | bw create folder
```

{% hint style="info" %}
任何 `item.xxx` 模板都应作为 `item` 模板的子对象使用，例如：

```batch
bw get template item | jq ".name=\"My Login Item\" | .login=$(bw get template item.login | jq '.username="jdoe" | .password="myp@ssword123"')" | bw encode | bw create item
```
{% endhint %}

### edit

&#x20;`edit` 用于编辑密码库中的对象（ `item`、`item-collections` 等）：

```batch
bw edit (item|item-collections|folder|org-collection) <id> [encodedJson] [options]
```

`edit` 命令使用一个**确切的** `id`（要编辑的对象）和编码的 JSON（要进行的编辑）。典型的工作流程大致为：

1. 使用 `get` 命令（请参阅[详细信息](password-manager-cli.md#get)）输出对象用于编辑。
2. 使用 [jq 之类的命令行 JSON 处理器](https://stedolan.github.io/jq/)根据需要操作已输出的模板。
3. 使用 `encode` 命令（请参阅[详细信息](password-manager-cli.md#encode)）对已操作的 JSON 进行编码。
4. 使用 `edit` 命令（包括对象 `id`）编辑对象。

示例：

```batch
bw get item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328 | jq '.login.password="newp@ssw0rd"' | bw encode | bw edit item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328
```

或者，编辑一个集合：

```batch
bw get collection ee9f9dc2-ec29-4b7f-9afb-aac8010631a1 | jq '.name="My Collection"' | bw encode | bw edit item-collections ee9f9dc2-ec29-4b7f-9afb-aac8010631a1
```

`edit` 命令将对对象执行**替换**操作。成功后，更新后的对象将作为 JSON 返回。

### list

`list` 命令用于从您的密码库中检索一组对象（ `items`、`folders`、`collections` 等）：

```batch
bw list (items|folders|collections|organizations|org-collections|org-members) [options]
```

`list` 命令的选项是**筛选器**，其决定了返回的内容，其包括 `--url <url>`、`--folderid <folderid>`、`--collectionid <collectionid>`、`--organizationid <organizationid>` 以及 `--trash`。任何筛选器都接受 `null` 或 `notnull`。在一个命令中组合多个筛选器将执行逻辑 OR 运算，例如：

```batch
bw list items --folderid null --collectionid null
```

此命令将返回_不属于_任何文件夹或集合的项目。

另外，您可以使用 `--search <search-term>` 来搜索明确的对象。将筛选器和搜索结合在一个命令中将执行逻辑 AND 运算，例如：

```batch
bw list items --search github --folderid 9742101e-68b8-4a07-b5b1-9578b5f88e6f
```

此命令将在指定的文件夹中搜索具有字符串为 `github` 的项目。

### delete

`delete` 命令用于从您的密码库中删除一个对象。`delete` 仅使用确切的 `id` 作为其参数。

```batch
bw delete (item|attachment|folder|org-collection) <id> [options]
```

默认情况下，delete 将「软删除」一个项目（即将其发送到回收站）。您可以使用 `-p`，`--permanent` 选项永久删除项目。

```batch
bw delete item 7063feab-4b10-472e-b64c-785e2b870b92 --permanent
```

要删除 `org-collection`，您还需要指定 `--organizationid <organizationid>` 。请参阅[组织 ID](password-manager-cli.md#organization-ids)。

{% hint style="warning" %}
使用 `delete` 「软删除」的项目可以使用 `restore` 命令恢复（请参阅[详细信息](password-manager-cli.md#restore)），但是使用 `delete --permanent` 删除的项目**将被完全删除并且无法恢复**。
{% endhint %}

### restore

`restore` 命令用于从回收站中恢复已删除的对象。`restore` 仅使用确切的 `id` 作为其参数。

```batch
bw restore (item) <id> [options]
```

例如：

```batch
bw restore item 7063feab-4b10-472e-b64c-785e2b870b92
```

### send

`send` 命令用于创建一个 [Bitwarden Send](../../bitwarden-send/about-send.md) 对象进行短暂的共享。本节将详细介绍简单的 `send` 操作，然而 Send 是一个高度灵活的工具，我们建议参阅 [CLI 上的 Send](../../bitwarden-send/send-from-cli.md) 这篇专门的文章。

要创建一个简单的文本 Send：

```batch
bw send -n "My First Send" -d 7 --hidden "The contents of my first text Send."
```

要创建一个简单的文件 Send：

```batch
bw send -n "A Sensitive File" -d 14 -f /Users/my_account/Documents/sensitive_file.pdf
```

### receive

`receive` 命令用于访问 [Bitwarden Send](../../bitwarden-send/about-send.md) 对象。要接收 Send 对象：

```batch
bw receive --password passwordforaccess https://vault.bitwarden.com/#/send/yawoill8rk6VM6zCATXv2A/9WN8wD-hzsDJjfnXLeNc2Q
```

## 组织命令 <a href="#organizations-commands" id="organizations-commands"></a>

### 组织 ID <a href="#organization-ids" id="organization-ids"></a>

从 CLI 访问组织经常需要知道组织的 ID 以及单个[成员](../../organizations/user-management.md)的 ID 和[集合](../../organizations/collections.md)的 ID。

使用 `bw list` 命令从 CLI 直接检索这些信息，例如：

```batch
bw list organizations
bw list org-members --organizationid 4016326f-98b6-42ff-b9fc-ac63014988f5
bw list org-collections --organizationid 4016326f-98b6-42ff-b9fc-ac63014988f5
```

{% hint style="success" %}
您可以同时 `bw list`  `collections` 和 `org-collections`。`bw list collections`  将列出_所有_集合，而与它们所属的组织无关。`bw list org-collections` 将_仅_列出属于使用 `--organizationid` 指定的组织的集合。
{% endhint %}

### move

{% hint style="info" %}
**2021 年 8 月**：`share` 命令已被更改为 `move`。[了解更多](../../release-notes.md)。
{% endhint %}

`move` 命令用于将密码库项目[转移到组织](../../organizations/sharing.md)：

```batch
bw move <itemid> <organizationid> [encodedJson]
```

`move` 命令要求您 `encode` 集合 ID，并使用一个**确切的** `id`（要共享的对象）和一个**确切的** `organizationid`（要与之共享对象的组织）。例如：

```batch
echo '["bq209461-4129-4b8d-b760-acd401474va2"]' | bw encode | bw move ed42f44c-f81f-48de-a123-ad01013132ca dfghbc921-04eb-43a7-84b1-ac74013bqb2e
```

成功后，将返回更新后的项目。

### confirm

`confirm` 命令用于确认已接受邀请的[受邀成员](../../organizations/user-management.md#confirm)加入您的组织：

```batch
bw confirm org-member <id> --organizationid <orgid>
```

`confirm` 命令使用**确切的**成员 `id` 和**确切的**组织 `id`，例如：

```batch
bw confirm org-member 7063feab-4b10-472e-b64c-785e2b870b92 --organizationid 310d5ffd-e9a2-4451-af87-ea054dce0f78
```

## 其他命令 <a href="#other-commands" id="other-commands"></a>

### config

`config` 命令用于指定 Bitwarden CLI 说使用的设置：

```batch
bw config server <setting> [value]
```

`bw config` 的主要用途是[将 CLI 连接到自托管 Bitwarden 服务器](../../self-hosting/connect-clients-to-your-instance.md#cli)：

```batch
bw config server https://your.bw.domain.com
```

{% hint style="success" %}
您可以通过传递不带值的 `bw config server` 来读取当前已连接的服务器。
{% endhint %}

具有唯一设置的用户可以选择使用以下方法单独指定每一个服务的 URL：

```batch
bw config --web-vault <url>
bw config --api <url>
bw config --identity <url>
bw config --icons <url>
bw confbw config server --web-vault <url>
bw config server --api <url>
bw config server --identity <url>
bw config server --icons <url>
bw config server --notifications <url>
bw config server --events <url>
bw config server --key-connector <url>
```

{% hint style="info" %}
如果您的组织使用 [Key Connector](../../login-with-sso/about-key-connector.md) 并且您在[移除您的主密码](../../login-with-sso/using-login-with-sso.md#login-using-sso)后使用 `--apikey` 选项登录，则需要运行 `bw config server --key-connector` 命令。

联系组织所有者以获取所需的 URL。
{% endhint %}

### sync

`sync` 命令用于从 Bitwarden 服务器下载加密的密码库。[登录](password-manager-cli.md#log-in) CLI 后，您又在其他客户端应用程序（例如网页密码库、浏览器扩展、移动应用程序）上对 Bitwarden 密码库进行了某些更改时，此命令很有用。

```batch
bw sync
```

您可以传递 `--last` 选项，以仅返回上次执行同步的时间戳（[ISO 8601](https://zh.wikipedia.org/wiki/ISO\_8601)）。

{% hint style="success" %}
重要的是要知道 `sync` **仅从服务器执行拉取操作**。任何时候您更改密码库时（例如 `create`、`edit`、`delete`），数据都会自动推送到服务器。
{% endhint %}

### encode

`encode` 命令用于对 stdin（标准输入） 进行 Base 64 编码。在执行 `create` 和 `edit` 操作时，此命令通常与 [json 这样的命令行 JSON 处理器](https://stedolan.github.io/jq/)结合使用，例如：

```batch
bw get template folder | jq '.name="My First Folder"' | bw encode | bw create folder

bw get item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328 | jq '.login.password="newp@ssw0rd"' | bw encode | bw edit item 7ac9cae8-5067-4faf-b6ab-acfd00e2c328
```

### import

`import` 命令用于从之前的 Bitwarden 导出或[其他受支持的密码管理应用程序](../../import-export/import-data-to-your-vault.md)中导入数据。该命令必须指向一个**文件**并包含如下参数：

```batch
bw import <format> <path>
```

例如：

```batch
bw import lastpasscsv /Users/myaccount/Documents/mydata.csv
```

{% hint style="success" %}
Bitwarden 支持多种导入格式，太多了而无法在这里一一列出！使用 `bw import --formats` 在  CLI 中返回列表，或[参阅这里](../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。
{% endhint %}

### export

`export` 命令用于将密码库数据导出为 `.json` 或 `.csv` 或[加密的 .json](../../import-export/encrypted-exports.md) 文件：

```batch
bw export [--output <filePath>] [--format <format>] [--password <password>] [--organizationid <orgid>]
```

默认情况下，`export` 命令将在当前工作目录下生成一个 `.csv`（相当于指定 `--format csv`）文件，但您也可以指定：

* `--format json`：导出为 `.json` 文件
* `--format encrypted_json`：导出为[加密的 .json](../../import-export/encrypted-exports.md) 文件
  * `--password <password>`：指定用于加密 `encrypted_json` 导出的密码，而不是您的[账户加密密钥](../../security/account-encryption-key.md)
* `--output <path>`：指定导出位置
* `--raw`：将导出返回到 stdout（标准输出）而不是文件

#### 导出组织密码库 <a href="#export-an-organization-vault" id="export-an-organization-vault"></a>

使用带有 `--organizationid` 选项的 `export` 命令，可以导出组织密码库：

```batch
bw export myp@ssw0rd --organizationid 7063feab-4b10-472e-b64c-785e2b870b92 --format json --output /Users/myaccount/Downloads/
```

### generate

`generate` 命令用于生成一个强密码或[密码短语](password-manager-cli.md#generate-a-passphrase)：

```batch
bw generate [--lowercase --uppercase --number --special --length <length> --passphrase --separator <separator> --words <words>]
```

默认情况下，`generate` 命令将生成一个包含 14 个字符的密码，其中包含大写字符、小写字符和数字。其等效于：

```batch
bw generate -uln --length 14
```

您可以使用该命令可用的选项来生成更复杂的密码，选项包括：

* `--uppercase` 或 `-u`（包含大写字符）
* `--lowercase` 或 `-l`（包含小写字符）
* `--number` 或 `-n`（包含数字）
* `--special` 或 `-s`（包含特殊字符）
* `--length <length>`（密码长度，最小值为 5）

#### 生成密码短语 <a href="#generate-a-passphrase" id="generate-a-passphrase"></a>

使用带有 `--passphrase` 选项的 `generate` 命令，可以生成一个密码短语而不是密码：

```batch
bw generate --passphrase --words <words> --separator <separator>
```

默认情况下，`bw generate --passphrase` 命令将生成一个 3 个单词的密码短语，并用破折号（-）分隔。这等效于：

```batch
bw generate --passphrase --words 3 --separator -
```

您可以使用该命令可用的选项来生成更复杂的密码短语，选项包括：

* `--words <words>`（单词数量）
* `--separator <separator>`（分隔符）
* `--capitalize, -c`（密码短语中首字母大写）
* `--includeNumber`（密码短语中包含数字）

### update

`update` 命令用于检查您的 Bitwarden CLI 是否正在运行最新版本。`update` **不会为您自动更新 CLI**。

```batch
shbw update
```

如果检测到新的版本，则需要使用打印的可执行文件 URL 来下载新版本的 CLI，或使用用于[下载 CLI](password-manager-cli.md#download-and-install) 的程序包管理器工具（例如 `npm install -g @bitwarden/cli`）来下载新版本的 CLI。

### status

`status` 命令用于返回 Bitwarden CLI 的状态信息，包括[已配置](password-manager-cli.md#config)的服务器 URL、最后一次同步的时间戳（[ISO 8601](https://zh.wikipedia.org/wiki/ISO\_8601)）、用户电子邮件和 ID，以及密码库状态。

```batch
bw status
```

状态将以 JSON 对象的形式返回信息，例如：

```yaml
{
  "serverUrl": "https://bitwarden.example.com",
  "lastSync": "2020-06-16T06:33:51.419Z",
  "userEmail": "user@example.com",
  "userId": "00000000-0000-0000-0000-000000000000",
  "status": "unlocked"
}
```

`status` 的值可能是以下之一：

* `"unlocked"`：表示您已登录并且您的密码库已解锁（即保存了含活动[会话密钥](password-manager-cli.md#using-a-session-key)的 `BW_SESSION` 密钥环境变量）。
* &#x20;`"locked"`：表示您已登录但是您的密码库已锁定（即**没有**保存含活动[会话密钥](password-manager-cli.md#using-a-session-key)的 `BW_SESSION` 密钥环境变量）。
* &#x20;`"unauthenticated"`：表示您尚未登录。

{% hint style="success" %}
当使用 `"status": "unauthenticated"` 时，`lastSync`、`userEmail` 和 `userID` 将始终返回 `null`。
{% endhint %}

### serve

`serve` 命令用于启动一个本地紧急 Web 服务器，该服务器用于执行所有可从 CLI 访问的操作，这些操作以来自 HTTP 接口的 RESTful API 调用的形式。

```batch
bw serve --port <port> --hostname <hostname>
```

默认情况下，`serve` 将在 8087 端口启动 Web 服务器，但您可以使用 `--port` 选项指定备用端口。

默认情况下，`serve` 会将您的 API Web 服务器绑定到 `localhost`，但您可以使用 `--hostname` 选项指定备用主机名。API 请求只能从绑定的主机名发出。

默认情况下，`serve` 将阻止任何带有 Origin 标头的请求。您可以使用 `--disable-origin-protection` 选项绕过此保护，但**不建议这样做**。

{% hint style="danger" %}
您可以指定 `--hostname all` 以不绑定主机名，但这将允许网络上的任何机器发出 API 请求。
{% endhint %}

[查看 API 规范](https://bitwarden.com/help/vault-management-api/)以获取使用 `serve` 进行调用的帮助。

## 附录 <a href="#appendix" id="appendix"></a>

### 全局选项 <a href="#global-options" id="global-options"></a>

以下选项全局可用：

| 选项                    | 描述                      |
| --------------------- | ----------------------- |
| `--pretty`            | 格式化输出。JSON 使用两个空格的制表符。  |
| `--raw`               | 返回原始输出，而不是描述性消息。        |
| `--response`          | 返回响应输出的 JSON 格式版本。      |
| `--quiet`             | 不要将任何东西返回 stdout（标准输出）。 |
| `--nointeraction`     | 对于输入交互式用户，不做提示。         |
| `--session <session>` | 传递会话密钥，而不是从环境变量中读取会话密钥。 |
| `-v, --version`       | 输出 Bitwarden CLI 的版本号。  |
| `-h, --help`          | 显示命令的帮助文本。              |

### ZSH Shell 补全 <a href="#zsh-shell-completion" id="zsh-shell-completion"></a>

Bitwarden CLI 支持 ZSH Shell 补全。要设置 Shell 补全，请使用下面的方法之一：

1、**Vanilla ZSH**：将下面行添加到您的 `.zshrc` 文件中：

```batch
eval "$(bw completion --shell zsh); compdef _bw bw;"
```

2、**Vanilla (vendor-completions)**：运行如下命令：

```batch
bw completion --shell zsh | sudo tee /usr/share/zsh/vendor-completions/_bw
```

3、[**zinit**](https://github.com/zdharma/zinit)：运行如下命令：

```batch
bw completion --shell zsh > ~/.local/share/zsh/completions/_bw
zinit creinstall ~/.local/share/zsh/completions
```

### 使用自签名证书 <a href="#using-self-signed-certificates" id="using-self-signed-certificates"></a>

如果您的自托管 Bitwarden 服务器公开为自签名 TLS 证书，请指定 Node.js 环境变量 [`NODE_EXTRA_CA_CERTS`](https://nodejs.org/api/cli.html#cli\_node\_extra\_ca\_certs\_file)：

<img src="../../.gitbook/assets/linux-24.png" alt="" data-size="line"><img src="../../.gitbook/assets/apple-24.png" alt="" data-size="line">Bash：

```batch
export NODE_EXTRA_CA_CERTS="absolute/path/to/your/certificates.pem"
```

<img src="../../.gitbook/assets/os-windows-24.png" alt="" data-size="line">PowerShell：

```powershell
$env:NODE_EXTRA_CA_CERTS="absolute/path/to/your/certificates.pem"
```

### 枚举 <a href="#enums" id="enums"></a>

下面的表格列举了在自文档情景下所需要的值：

#### 两步登录方式 <a href="#two-step-login-methods" id="two-step-login-methods"></a>

用于指定在[登录](password-manager-cli.md#log-in)时使用哪一种[两步登录方式](../../two-step-login/two-step-login-methods.md)：

| 名称      | 值 |
| ------- | - |
| 验证器     | 0 |
| 电子邮件    | 1 |
| Yubikey | 3 |

{% hint style="info" %}
CLI 不支持 FIDO2 和 Duo。
{% endhint %}

#### 项目类型 <a href="#item-types" id="item-types"></a>

与 `create` 命令一起使用以指定[项目的类型](../../your-vault/vault-items.md)：

| 名称   | 值 |
| ---- | - |
| 登录   | 1 |
| 安全笔记 | 2 |
| 支付卡  | 3 |
| 身份   | 4 |

#### 登录 URI 匹配类型 <a href="#login-uri-match-types" id="login-uri-match-types"></a>

与 `create` 和 `edit` 命令一起使用以指定 [URI 匹配检测](../../auto-fill/using-uris.md)行为：

| 名称    | 值 |
| ----- | - |
| 基础域   | 0 |
| 主机    | 1 |
| 开始于   | 2 |
| 精确    | 3 |
| 正则表达式 | 4 |
| 从不    | 5 |

#### 字段类型 <a href="#field-types" id="field-types"></a>

与 `create` 和 `edit` 命令一起使用以配置[自定义字段](../../your-vault/custom-fields.md)：

| 名称  | 值 |
| --- | - |
| 文本  | 0 |
| 隐藏  | 1 |
| 布尔型 | 2 |

#### 组织用户类型 <a href="#organization-user-types" id="organization-user-types"></a>

指示[用户的类型](../../admin-console/user-management/member-roles-and-permissions.md)：

| 名称  | 值 |
| --- | - |
| 所有者 | 0 |
| 管理员 | 1 |
| 用户  | 2 |
| 经理  | 3 |

#### 组织用户状态类型 <a href="#organization-user-statuses" id="organization-user-statuses"></a>

指示[用户在组织内的状态](../../organizations/user-management.md)：

| 名称  | 值 |
| --- | - |
| 受邀  | 0 |
| 已接受 | 1 |
| 已确认 | 2 |

# Terraform 提供程序

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/terraform-provider/)
{% endhint %}

Bitwarden 提供了一个用于获取、创建和管理机密的 Terraform 提供程序，帮助您使用 Terraform 保护您的基础设施机密。[Bitwarden Terraform registry](https://registry.terraform.io/providers/bitwarden/bitwarden-secrets/latest/docs) 中提供了更多提供程序文档。

## 要求 <a href="#requirements" id="requirements"></a>

* Terraform 版本 1.5 或更高版本。
* 拥有[机器账户](../your-secrets/machine-accounts.md)和附加[访问令牌](../your-secrets/access-tokens.md)的 [Secrets Manager](../secrets-manager-overview.md) 组织。

{% hint style="success" %}
我们推荐：

* 在使用配置**之前**，先使用 Secrets Manager 网页 App 指定您的机器账户可以访问哪些[工程](../your-secrets/projects.md)和[机密](../your-secrets/secrets.md)。
* **在准备配置 Terraform 提供程序时**，使用 Secrets Manager 网页 App 生成访问令牌。访问令牌的值只能在创建时复制。
{% endhint %}

## 配置 <a href="#configuration" id="configuration"></a>

您的 Terraform 配置文件 ( `.tf` ) 至少必须包含以下内容：

```bash
terraform {
  required_providers {
    bitwarden-secrets = {
      source = "registry.terraform.io/bitwarden/bitwarden-secrets"
    }
  }
}
```

您可以在您的 `.tf` 文件中添加几个可选属性。其中一些值应被视为敏感信息。所有这些值也可以通过环境变量提供，但是所有这些值只能使用这两种方法中的一种来提供：

| 属性                | 等效变量                 | 描述                                                                                                                                          |
| ----------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `access_token`    | `BW_ACCESS_TOKEN`    | （敏感）配置的机器账户的[访问令牌](../your-secrets/access-tokens.md)值。这将允许 Terraform 提供程序仅访问 Secrets Manager 中的特定数据。                                        |
| `organization_id` | `BW_ORGANIZATION_ID` | 您组织的唯一标识符。您登录到 Secrets Manager 网页 App 时，可以在地址栏中找到。                                                                                          |
| `api_url`         | `BW_API_URL`         | Bitwarden Secrets Manager `/api` 终端的 URI。对于美国和欧盟云托管的客户，这将分别是 `https://api.bitwarden.com` 和 `https://identity.bitwarden.eu`，对于自托管的客户，则由部署决定。 |
| `identity_url`    | `BW_IDENTITY_URL`    | Secrets Manager `/identity` 终端的 URI。对于美国和欧盟云托管的客户，这将分别是 `https://api.bitwarden.com` 和 `https://identity.bitwarden.eu`，对于自托管的客户，则由部署决定。      |

一个明确包含所有属性（而不是由环境变量传递）的 `.tf` 文件应如下所示：

```bash
terraform {
  required_providers {
    bitwarden-secrets = {
      source = "registry.terraform.io/bitwarden/bitwarden-secrets"
    }
  }
}

provider "bitwarden-secrets" {
  api_url         = "https://api.bitwarden.com"
  identity_url    = "https://identity.bitwarden.com"
  access_token    = "<access_token_value>"
  organization_id = "< organization_unique_identifier>"
}
```

## 快速入门 <a href="#quick-start" id="quick-start"></a>

以下步骤将指导您通过将 Bitwarden Secrets Manager 中的机密添加到状态和配置中，以将其纳入 Terraform 管理范围：

1、使用 `bitwarden-secrets_secret` 资源将机密添加到 `.tf` 配置文件中：

```bash
resource "bitwarden-secrets_secret" "my_secret" {}
```

2、使用 Terraform CLI 中的 `terraform import` 命令将机密导入到状态，将指示的占位符值替换为机密的唯一标识符（可直接从 Secrets Manager 网页 App 的机密条目复制）：

```bash
terraform import "bitwarden-secrets_secret.my_secret" "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```

3、将您的机密导入 Terraform 状态后，在 Terraform CLI 中使用 `terraform show` 命令显示导入的数据。从输出中复制键值，并将其添加到 `.tf` 配置中以完成设置：

```bash
resource "bitwarden-secrets_secret" "my_secret" {
  key = "db_admin_password"
}
```

`bitwarden-secrets_secret` 资源将使用键值（在此情况下为 `db_admin_password` ）在后续操作中操作机密，确保机密在 Bitwarden Secrets Manager 和 Terraform 之间保持安全和同步。

## 数据源 <a href="#data-sources" id="data-sources"></a>

### bitwarden-secrets\_projects <a href="#bitwarden-secrets-projects" id="bitwarden-secrets-projects"></a>

`bitwarden-secrets_projects` 数据源获取机器账户可访问的所有工程列表。以下是一个包含 `bitwarden-secrets_projects` 数据源声明的 `data` 块示例，以及一个使用 `.projects` 属性引用它的 `output` 块示例：

```bash
data "bitwarden-secrets_projects" "example" {}

output "example" {
  value = data.bitwarden-secrets_projects.projects
}
```

对于每个工程，以下属性可以导出到输出：

* `creation_date`：（字符串）工程创建的时间戳。
* `id`：（字符串型）工程的唯一标识符。
* `name`：（字符串型）工程的名称。
* `organization_id`：（字符串型）工程所属组织的唯一标识符。
* `revision_date`：（字符串型）工程最近一次修订的时间戳。

### bitwarden-secrets\_list\_secrets <a href="#bitwarden-secrets-list-secrets" id="bitwarden-secrets-list-secrets"></a>

`bitwarden-secrets_list_secrets` 数据源获取机器账户可访问的所有机密列表。以下是一个 `data` 块的示例，其中包含 `bitwarden-secrets_list_secrets` 数据源声明，以及一个使用 `.secrets` 属性引用它的 `output` 块示例：

```bash
data "bitwarden-secrets_list_secrets" "example" {}

output "example" {
  value = data.bitwarden-secrets_list_secrets.secrets
}
```

对于每个机密，可以在输出中导出以下属性：

* `id`：（字符串型）机密的唯一标识符。
* `key`：（字符串型）与机密关联的键，在 Secrets Manager UI 中称为「名称」。

{% hint style="info" %}
`bitwarden-secrets_list_secrets` 数据源无法获取机密值。
{% endhint %}

### bitwarden-secrets\_secret <a href="#bitwarden-secrets-secret" id="bitwarden-secrets-secret"></a>

`bitwarden-secrets_secret` 数据源获取特定的机密，该机密必须可被机器账户访问。使用 `bitwarden-secrets_secret` 数据源获取机密时，需要以下参数：

* `id`：（字符串型）要获取的机密的唯一标识符。此值可以直接从 Secrets Manager 网页 App 中的机密条目中复制。

以下是一个包含 `data` 数据源声明和引用所有可导出属性的 `output` 示例代码块：

```bash
data "bitwarden-secrets_secret" "example" {
  id = "e6a8066c-81e6-428e-bf5d-b1b900fe1b42"
}

output "example" {
  value = {
    id  = data.bitwarden-secrets_secret.secret.id
    key = data.bitwarden-secrets_secret.secret.key
    value           = data.bitwarden-secrets_secret.secret.value #The actual secret value is marked sensitive and will not be printed to stdout
    note            = resource.bitwarden-secrets_secret.secret.note
    project_id      = resource.bitwarden-secrets_secret.secret.project_id
    organization_id = resource.bitwarden-secrets_secret.secret.organization_id
    creation_date   = resource.bitwarden-secrets_secret.secret.creation_date
    revision_date   = resource.bitwarden-secrets_secret.secret.revision_date
  }
}
```

对于每个密钥，可以在输出中导出以下属性：

* `id`：（字符串型）机密的唯一标识符。
* `key` ：（字符串型）与机密关联的键，在 Secrets Manager UI 中称为「名称」。
* `value`：（字符串型）与机密关联的值。被视为敏感信息，永远不会打印到 stdout。
* `note`：（字符串型）保存于机密**备注**字段中的任何文本。
* `project_id`：（字符串型）机密所属工程的唯一标识符。
* `organization_id`：（字符串型）机密所属组织的唯一标识符。
* `creation_date`：（字符串型）机密创建的时间戳。
* `revision_date`：（字符串型）机密最近一次修订的时间戳。

## 资源 <a href="#resources" id="resources"></a>

### bitwarden-secrets\_secret <a href="#bitwarden-secrets-secret" id="bitwarden-secrets-secret"></a>

`bitwarden-secrets_secret` 资源可用于在 Bitwarden 密钥管理器中创建新机密或管理现有机密。要声明一个 `bitwarden-secrets_secret` 资源块，至少需要以下参数：

* `key` ：（字符串型）与机密关联的键，在 Secrets Manager UI 中称为「名称」。

以下是一个包含 `bitwarden-secrets_secret` 资源声明的 `resource` 块示例：

```
resource "bitwarden-secrets_secret" "db_admin_secret" {
  key = "db_admin_password"
  value      = var.value #It is not recommended to provide the actual secret value via configuration file! By using a terraform variable, users can inject the secret value during runtime via environment variables.
  project_id = var.project_id
  note       = "The secret value was provided via terraform configuration."
}
```

在上述示例中，其他可选参数包括：

* `value`：（字符串型）机密的值。**不推荐**通过配置文件提供机密值。通过使用 terraform 变量，用户可以在运行时通过环境变量注入机密值。
* `project_id`：（字符串型）机密应添加到的工程的唯一标识符。机器账户**必须**对该工程有访问权限。
* `note`：（字符串型）保存于机密**备注**字段中的任何文本。

### 机密值生成 <a href="#secret-value-generation" id="secret-value-generation"></a>

如果没有提供机密值，Terraform 提供者将为您生成一个。**这是推荐的方法**。您可以指定可选属性来自定义值的生成，例如：

```bash
resource "bitwarden-secrets_secret" "db_admin_secret" {
  key         = "db_admin_password"
  project_id  = var.project_id
  length      = 32
  special     = true
  min_special = 5
}
```

对于每个机密，可以使用以下属性来自定义值的生成：

* `avoid_ambiguous`：（布尔型）默认为 `false` 。设置为 `true` 时，生成的值将不包含歧义字符（`I`、`l`、`1`、`0`、`o`、`O`）。
* `length`：（数值型）默认为 `64` 个字符。设置为其他数字时，生成的值将是该数字数量的字符。
* `lowercase`：（布尔型）默认为 `true` 。设置为 `false` 时，生成的值将不包含小写字符。
  * `min_lowercase`：（数值型）如果 `lowercase` 为 `false` ，则忽略。设置为数字时，生成的值将至少包含该数字数量的小写字符（必须为 1-9 之间的数字）。
* `uppercase`：（布尔型）默认为 `true` 。如果设置为 `false` ，生成的值将不包含大写字母。
  * `min_uppercase`：（数值型）如果 `uppercase` 为 `false` ，则忽略。如果设置为数字，生成的值将至少包含该数字数量的大写字母（必须为 1-9 之间的数字）。
* `numbers`：（布尔型）默认为 `true` 。如果设置为 `false` ，生成的值将不包含数字（`0` - `9`）。
  * `min_numbers`：（数值型）如果 `numbers` 为 `false` ，则忽略。如果设置为数字，生成的值将至少包含该数字数量的数字（必须为 1-9 之间的数字）。
* `special`：（布尔型）默认为 `true` 。如果设置为 `false` ，生成的值将不包含特殊字符（`@`，`#`，`$`，`%`，`^`，`&`，`*`）。
  * `min_special`：（数值型）如果 `special` 为 `false` ，则忽略。如果设置为数字，生成的值将至少包含该数字数量的特殊字符（必须为 1-9 之间的数字）。

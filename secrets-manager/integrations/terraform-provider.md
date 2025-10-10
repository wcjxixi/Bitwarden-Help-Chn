# =Terraform 提供程序

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/terraform-provider/)
{% endhint %}

Bitwarden 提供了一个 Terraform 提供程序，可以获取、创建和管理机密，帮助您使用 Terraform 保护您的基础设施机密。[Bitwarden Terraform registry](https://registry.terraform.io/providers/bitwarden/bitwarden-secrets/latest/docs) 中提供了更多提供程序文档。

## 要求 <a href="#requirements" id="requirements"></a>

* Terraform 版本 1.5 或更高版本。
* 一个拥有[机器账户](../your-secrets/machine-accounts.md)和附加[访问令牌](../your-secrets/access-tokens.md)的 [Secrets Manager](../secrets-manager-overview.md) 组织。

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

### bitwarden-secrets\_list\_secrets <a href="#bitwarden-secrets-list-secrets" id="bitwarden-secrets-list-secrets"></a>

### bitwarden-secrets\_secret <a href="#bitwarden-secrets-secret" id="bitwarden-secrets-secret"></a>

## 资源 <a href="#resources" id="resources"></a>

### bitwarden-secrets\_secret <a href="#bitwarden-secrets-secret" id="bitwarden-secrets-secret"></a>

### 密钥值生成 <a href="#secret-value-generation" id="secret-value-generation"></a>


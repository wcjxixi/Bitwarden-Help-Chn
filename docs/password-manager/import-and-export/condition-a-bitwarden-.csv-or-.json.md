# 从自定义文件导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/condition-bitwarden-import/)
{% endhint %}

本文介绍了如何格式化 `.csv` 和 `.json` 文件以导入 Bitwarden。其格式与 [Bitwarden 密码库导出](export-vault-data.md)相同。要选择文件类型和格式，请确定目标密码库以及需要导入的项目类型：

* 基于您要[导入到个人密码库](import-data.md#import-to-your-personal-vault)还是[导入到组织密码库](../../admin-console/manage-shared-items/import-organization-items/import-to-organization.md#import-to-an-organization-vault)来格式化文件。
* Bitwarden .`csv` 文件仅包含登录和安全笔记。如果您还需要处理身份和支付卡，请使用 `.json` 文件。

{% hint style="info" %}
虽然某些项目类型无法导入，但您仍可将其添加到密码库：

* 将[文件附件](../your-vault/vault-items/file-attachments.md)单独上传到新的密码库。
* 在新的密码库中重新创建 [Send](../bitwarden-send/about-send.md)。
{% endhint %}

## 调整 .csv <a href="#condition-a-csv" id="condition-a-csv"></a>

### 个人密码库 .csv <a href="#csv-for-individual-vault" id="csv-for-individual-vault"></a>

创建具有如下标头作为第一行的 UTF-8 编码的纯文本文件：

```
folder,favorite,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
```

示例：

```
folder,favorite,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
Social,1,login,Twitter,,,0,twitter.com,me@example.com,password123,
,,login,EVGA,,,,https://www.evga.com/support/login.asp,hello@bitwarden.com,fakepassword,TOTPSEED123
,,login,My Bank,Bank PIN is 1234,"PIN: 1234",,https://www.wellsfargo.com/home.jhtml,john.smith,password123456,
,,note,My Note,"This is a secure note.",,,,,
```

导入此文件时，请选择 **Bitwarden (csv)** 作为您的文件格式。

⬇️[下载示例 csv 文件](https://assets.ctfassets.net/7rncvj1f8mw7/4j3wYIYVQYW2MZUBogVxM3/2299910bb8fc93f6a8916d870be0458c/bitwarden_export.csv)

### 组织密码库 .csv <a href="#csv-for-organization" id="csv-for-organization"></a>

创建具有如下标头作为第一行的 UTF-8 编码的纯文本文件：

```
collections,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
```

示例：

```
collections,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
"Social,Marketing",login,Twitter,,,0,twitter.com,me@example.com,password123,
"Finance",login,My Bank,"Bank PIN is 1234","PIN: 1234",0,https://www.wellsfargo.com/home.jhtml,john.smith,password123456,
"Finance",login,EVGA,,,0,https://www.evga.com/support/login.asp,hello@bitwarden.com,fakepassword,TOTPSEED123
"Finance",note,My Note,"This is a secure note.",,0,,,
```

{% hint style="success" %}
如果您要对包含嵌套集合的 .`csv` 文件进行调整，请为**每个不包含任何项目的集合**创建专用条目，例如：

```
collections,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
Parent Collection,,,,,,,,,,
Parent Collection/First Child Collection,,,,,,,,,,
Parent Collection/First Child Collection/Second Child Collection,login,Shared Credential,,,,https://website.com,username,password,,
```
{% endhint %}

导入此文件时，请选择 **Bitwarden (csv)** 作为您的文件格式。

⬇️[下载示例 csv 文件](https://assets.ctfassets.net/7rncvj1f8mw7/YYnGrBJO8O5Xv2O0dFW9Z/6de667ded7567da41dcdf4af5186311a/bitwarden_export_org.csv)

### 最少要求值 <a href="#minimum-required-values" id="minimum-required-values"></a>

您可能没有上述格式中显示的所有值的数据，但他们大多数是可选的。为了让 Bitwarden `.csv` 导入器能正常工作，您只需为每个对象提供以下值即可：

```
folder,favorite,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
,,login,Login Name,,,,,,
,,note,Secure Note Name,,,,,,
```

## 调整 .json <a href="#condition-a-json" id="condition-a-json"></a>

### 个人密码库 .json <a href="#json-for-individual-vault" id="json-for-individual-vault"></a>

创建如下格式的 UTF-8 编码的纯文本文件：

```bash
{
  "folders": [
    {
      "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
      "name": "Folder Name"
    },
    ...
  ],
  "items": [
    {
    "passwordHistory": [
        {
          "lastUsedDate": "YYYY-MM-00T00:00:00.000Z",
          "password": "passwordValue"
        }
    ],
    "revisionDate": "YYYY-MM-00T00:00:00.000Z",
    "creationDate": "YYYY-MM-00T00:00:00.000Z",
    "deletedDate": null,    
    "id": "yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy",
    "organizationId": null,
    "folderId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "type": 1,
    "reprompt": 0,
    "name": "My Gmail Login",
    "notes": "This is my gmail login for import.",
    "favorite": false,
    "fields": [
        {
          "name": "custom-field-1",
          "value": "custom-field-value",
          "type": 0
        },
        ...
      ],
      "login": {
        "uris": [
          {
            "match": null,
            "uri": "https://mail.google.com"
          }
        ],
        "username": "myaccount@gmail.com",
        "password": "myaccountpassword",
        "totp": otpauth://totp/my-secret-key
      },
      "collectionIds": null
    },
    ...
  ]
}
```

导入此文件时，请选择 **Bitwarden (json)** 作为您的文件格式。

⬇️[下载示例 json 文件](https://assets.ctfassets.net/7rncvj1f8mw7/2iwtn9YFqooYJmw1JWwCXa/8b03a95f1c27240c22a7578aa703f7b1/individual.json)

### 组织密码库 .json <a href="#json-for-organization" id="json-for-organization"></a>

创建如下格式的 UTF-8 编码的纯文本文件：

```bash
{
  "collections": [
    {
      "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
      "organizationId": "yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy",
      "name": "My Collection",
      "externalId": null
    },
    ...
  ],
  "items": [
    {
      "passwordHistory": [
        {
          "lastUsedDate": "YYYY-MM-00T00:00:00.000Z",
          "password": "passwordValue"
        }
      ],
    "revisionDate": "YYYY-MM-00T00:00:00.000Z",
    "creationDate": "YYYY-MM-00T00:00:00.000Z",
    "deletedDate": null,
    "id": "vvvvvvvv-vvvv-vvvv-vvvv-vvvvvvvvvvvv",
    "organizationId": "yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy",
    "folderId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz",
    "type": 1,
    "reprompt": 1,
    "name": "Our Shared Login",
    "notes": "A login for sharing",
    "favorite": false,
    "fields": [
        {
          "name": "custom-field-1",
          "value": "custom-field-value",
          "type": 0
        },
        ...
      ],
      "login": {
        "uris": [
          {
            "match": null,
            "uri": "https://mail.google.com"
          }
        ],
        "username": "myaccount@gmail.com",
        "password": "myaccountpassword",
        "totp": otpauth://totp/my-secret-key
      },
      "collectionIds": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
    },
    ...
  ]
}
```

导入此文件时，请选择 **Bitwarden (json)** 作为您的文件格式。

⬇️[下载示例 json 文件](https://assets.ctfassets.net/7rncvj1f8mw7/2Pui1E5uLs2FSw6GhO6pdU/141c68c6ad63ea8f395067c02592ddbc/organization.json)

### 导入到现有集合 <a href="#import-to-existing-collections" id="import-to-existing-collections"></a>

通过适当调整组织的 `.json` 文件，可以将新的登录项目导入到预先存在的[集合](../../admin-console/manage-shared-items/collections/about-collections.md)中。

下面的示例演示了将单个项目导入到预先存在的集合中的正确格式。请注意，您需要：

* 获取组织 ID 和集合 ID。这些可以通过导航到网页 App 的集合，然后从地址栏中提取（例如 `https://vault.bitwarden.com/#/organizations/<organizationId>/vault?collectionId=<collectionId>` ）。
* 定义一个 `"collections": []` 数组，其中包含预先存在的集合的数据，包括组织 ID 和集合 ID（见上文）及其名称。只要这 3 个数据点匹配，导入时就不会创建新的集合，而是将文件中的项目导入到预先存在的集合中。

```bash
{
  "encrypted": false,
  "collections": [
    {
      "id": "b8e6df17-5143-495e-92b2-aff700f48ecd",
      "organizationId": "55d8fa8c-32bb-47d7-a789-af8710f5eb99",
      "name": "My Existing Collection",
      "externalId": null
    }
  ],
  "folders": [],
  "items": [
    {
      "id": "2f27f8f8-c980-47f4-829a-aff801415845",
      "organizationId": "55d8fa8c-32bb-47d7-a789-af8710f5eb99",
      "folderId": null,
      "type": 1,
      "reprompt": 0,
      "name": "Item to Import",
      "notes": "A login item for sharing.",
      "favorite": false,
      "login": {
        "uris": [
          {
            "match": null,
            "uri": "https://mail.google.com"
          }
        ],
        "username": "my_username",
        "password": "my_password",
        "totp": null
      },
      "collectionIds": ["b8e6df17-5143-495e-92b2-aff700f48ecd"]
    }
  ]
}

```

### 最少要求键值对 <a href="#minimum-required-key-value-pairs" id="minimum-required-key-value-pairs"></a>

您可能没有上述格式中显示的所有键值对的数据，但他们大多数是可选的。为了让 Bitwarden `.json` 导入器能正常工作，您只需要为每个对象提供以下键值对即可：

```bash
{
  "items": [
    {
    "type": 1,
    "name": "Login Item's Name",
    "login": {}                         
  },
  {
    "type": 2,
    "name": "Secure Note Item's Name",
    "secureNote": {}                     
  },
  {
    "type": 3,
    "name": "Card Item's Name",
    "card": {}                         
  },
  {
    "type": 4,
    "name": "Identity Item's Name",
    "identity": {}                     
  }
  ]
}
```

`"login":`、`"secureNote":`、`"card":` 以及 `"identity":` 对象可以作为空对象导入，但是我们建议使用尽可能多的数据来调整文件。

## 导入到 Bitwarden <a href="#import-into-bitwarden" id="import-into-bitwarden"></a>

准备好 `.csv` 或 `.json` 文件后，就可以将其导入[个人密码库](import-data.md#import-to-your-personal-vault)或[组织密码库](../../admin-console/manage-shared-items/import-organization-items/import-to-organization.md#import-to-an-organization-vault)了。从**文件格式**列表中选择 **Bitwarden (csv)** 或 **Bitwarden (json)**。

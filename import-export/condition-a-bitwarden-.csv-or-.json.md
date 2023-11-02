# 调整 Bitwarden .csv 或 .json

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/condition-bitwarden-import/)
{% endhint %}

这篇文章定义了当你手动调整用于导入 Bitwarden 的 `.csv` 或 `.json` 文件时应使用的格式。此格式与[导出你的 Bitwarden 密码库](export-vault-data.md)时创建的 `.csv` 或 `.json` 文件所使用的格式是一样的。

根据您是将数据导入个人密码库或者是导入组织密码库，请确保使用正确的格式。

## 调整 .csv <a href="#condition-a-csv" id="condition-a-csv"></a>

{% hint style="info" %}
Bitwarden `.csv` 文件仅处理登录和安全笔记。如果还需要导入或导出身份和支付卡信息，请[使用 JSON](condition-a-bitwarden-.csv-or-.json.md#condition-a-json)。
{% endhint %}

### 对于个人密码库 <a href="#for-your-personal-vault" id="for-your-personal-vault"></a>

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

⬇️[下载示例 csv 文件](https://assets.ctfassets.net/7rncvj1f8mw7/70BRfxAoqXCQXvNvBmpjyt/60a86b19b0d9a349478110b17d1fc698/bitwarden\_export.csv)

### 对于组织密码库 <a href="#for-your-organization" id="for-your-organization"></a>

创建具有如下标头作为第一行的 UTF-8 编码的纯文本文件：

```
collections,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
```

示例：

```
collections,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
"Social,Marketing",login,Twitter,,,0,twitter.com,me@example.com,password123,
"Finance",login,My Bank,Bank PIN is 1234,"PIN: 1234",0,https://www.wellsfargo.com/home.jhtml,john.smith,password123456,
,login,EVGA,,,https://www.evga.com/support/login.asp,hello@bitwarden.com,fakepassword,TOTPSEED123
,note,My Note,"This is a secure note.",,,,,
```

导入此文件时，请选择 **Bitwarden (csv)** 作为您的文件格式。

⬇️[下载示例 csv 文件](https://assets.ctfassets.net/7rncvj1f8mw7/4DdJLATeuhMYlE581pPErF/ef60b56917b58f59141ae9aa58b5a46d/bitwarden\_export\_org.csv)

### 最少要求值 <a href="#minimum-required-values" id="minimum-required-values"></a>

你可能没有上述格式中显示的所有值的数据，但他们大多数是可选的。为了让 Bitwarden `.csv` 导入器能正常工作，你只需为每个对象提供以下值即可：

```
folder,favorite,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
,,login,Login Name,,,,,,
,,note,Secure Note Name,,,,,,
```

## 调整 .json <a href="#condition-a-json" id="condition-a-json"></a>

### 对于个人密码库 <a href="#for-your-personal-vault" id="for-your-personal-vault"></a>

创建如下格式的 UTF-8 编码的纯文本文件：

```yaml
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

⬇️[下载示例 csv 文件](https://assets.ctfassets.net/7rncvj1f8mw7/2gWg0hxdS1y4a3SSZnesDN/3baec2b17ce618ec2296cd4dbcbd8f31/bitwarden\_export.json)

### 对于组织密码库 <a href="#for-your-organization" id="for-your-organization"></a>

创建如下格式的 UTF-8 编码的纯文本文件：

```yaml
{
  "collections": [
    {
      "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
      "organizationId": "yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy",
      "name": "My Collection"
      "externalId": null
    },
    ...
  ],
  "items": [
    {
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

⬇️[下载示例 csv 文件](https://assets.ctfassets.net/7rncvj1f8mw7/3qTuEXkLZiEXewdcHxzttW/a6f4ba7f7ac5fbe94059d1d9416074f4/bitwarden\_org\_export.json)

### 导入到现有集合 <a href="#import-to-existing-collections" id="import-to-existing-collections"></a>

通过适当调整组织的 `.json` 文件，可以将新的登录项目导入到预先存在的[集合](../organizations/collections.md)中。

下面的示例演示了将单个项目导入到预先存在的集合中的正确格式。请注意，您需要：

* 获取组织和集合 ID。这些可以通过导航到网页应用程序中的集合，然后从地址栏中提取（例如 `https://vault.bitwarden.com/#/organizations/<organizationId>/vault?collectionId=<collectionId>` ）。
* 定义一个 `"collections": []` 数组，其中包含预先存在的集合的数据，包括组织和集合 ID（见上文）及其名称。只要这 3 个数据点匹配，导入时就不会创建新的集合，而是将文件中的项目导入到预先存在的集合中。

```yaml
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

你可能没有上述格式中显示的所有键值对的数据，但他们大多数是可选的。为了让 Bitwarden `.json` 导入器能正常工作，你只需要为每个对象提供以下键值对即可：

```yaml
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

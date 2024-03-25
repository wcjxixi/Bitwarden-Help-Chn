# 导入数据到密码库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-data/)
{% endhint %}

Bitwarden 提供了一个数据导入工具，可以轻松地将任何密码管理解决方案迁移到您的个人密码库或组织密码库。您也可以使用数据导入工具从一个 Bitwarden 密码库导入到另一个 Bitwarden 密码库，或者导入一个 Bitwarden [加密导出](encrypted-exports.md)。

关于支持的导入格式的完整列表，请参阅 [Bitwarden 支持导入哪些文件格式？](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)，或者使用这些文章用于从最流行的解决方案导入：

* [从 LastPass 导入](import-guides/import-your-data-from-lastpass.md)
* [从1Password 导入](import-guides/import-your-data-from-1password.md)
* [从 Firefox 导入](import-guides/import-your-data-from-firefox.md)
* [从 Google Chrome 或 Chromium 导入](import-guides/import-your-data-from-google-chrome.md)
* [从 Microsoft Edge 导入](import-guides/import-your-data-from-google-chrome.md)
* [从 Password Safe 导入](import-guides/import-data-from-password-safe.md)

## 导入到您的个人密码库 <a href="#import-to-your-personal-vault" id="import-to-your-personal-vault"></a>

数据可以从 **Web 密码库**或 **CLI** 导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行加密。要导入您的数据：

{% tabs %}
{% tab title="网页端程序" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com)、[https://vault.bitwarden.eu](https://vault.bitwarden.eu,) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从导航条选择**工具** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/6d09a2630cdb4c4499575997af5569ea/Screenshot_2024-02-27_at_11.21.15_AM.png?_a=BAJFJtWIB" %}
导入数据
{% endembed %}

3、从下拉菜单中完成以下字段：

* **导入目的地**：选择导入目的地，例如您拥有访问权限的个人密码库或组织密码库。
* **文件夹或集合**：选择您是否希望将导入的内容移动到您拥有访问权限的特定文件夹或组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

4、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

5、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

6、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../your-vault/file-attachments.md)、[Send](../bitwarden-send/about-send.md)、回收站以及密码历史记录等附加项目需要手动上传到您的密码库。
{% endtab %}

{% tab title="浏览器扩展" %}
要导入数据到您的密码库：

1、选择**设置**选项卡，然后选择**导入项目**选项。

2、从下拉菜单中完成以下字段：

* **导入目的地**：选择导入目的地，例如您拥有访问权限的个人密码库或组织密码库。
* **文件夹或集合**：选择您是否希望将导入的内容移动到您拥有访问权限的特定文件夹或组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

3、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

4、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

5、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="桌面端程序" %}
要导入数据到您的密码库：

1、选择**文件** -> **导入数据**。

2、从下拉菜单中完成以下字段：

* **导入目的地**：选择导入目的地，例如您拥有访问权限的个人密码库或组织密码库。
* **文件夹或集合**：选择您是否希望将导入的内容移动到您拥有访问权限的特定文件夹或组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

3、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

4、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

5、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="CLI" %}
要通过 CLI 将数据导入您的密码库，请使用以下命令：

```batch
bw import <format> <path>
```

`bw import` 命令需要格式（使用 `bw import --formats` 获取格式列表）和路径，例如：

```batch
bw import lastpasscsv /Users/myaccount/Documents/mydata.csv
```

成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}
{% endtabs %}

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

### 导入文件附件 <a href="#importing-file-attachments" id="importing-file-attachments"></a>

文件附件只能手动迁移到您的 Bitwarden 密码库，因为它们目前不包含在批量导入操作中。请注意，文件附件的存储仅适用于高级用户，以及付费组织（家庭、团队或企业）的成员。

### 长度相关导入错误 <a href="#length-related-import-errors" id="length-related-import-errors"></a>

尝试导入 `.csv` 时通常会收到如下的错误信息，这些信息表明导入文件中的某个特定值超出了该字段类型所允许的**加密**字符的限制：

{% embed url="https://bitwarden.com/_gatsby/image/1ae5b6b8d8ce6f6f4df15d95f5ffdcde/753d98128cb9b6556367e944a99d0205/ciphererror_2021.webp?eu=dd8c02b2b5cbadd45a3ca5d56f73673be96b01feaf023ed93b60e3fd1aaecdd476a2105175907fb6283f08dd85b44bbe62c57f6019bad7dfc0b811fdec36ae0e57875ebf6fe77004052f92afb8f202463dc51c09a882c00eaa6a26d4e6bab5721c544e22fb29b2d9a8ed7527ba9c306bb7e7f17b26dcf83cb6431d179e5c32e23aeed4c1345cb09df645eeb0e6f44eca83e05b5d1d9fa15d23170b6d0d9156e0fde958395b411c443098a85ec26497e3691e622b5c0b55f3643a825dfd696096e2ffa958dd7328b5b79a6830de96ecd5af58f36819e5cf25a89c7b2459&a=w%3D500%26h%3D336%26fm%3Dwebp%26q%3D75&cd=2022-12-09T19%3A03%3A12.435Z" %}
Web 密码库中的密码错误
{% endembed %}

要解决这个问题，请在文本编辑器或电子表格程序中打开 `.csv` 文件，将违规项目移除或减少其字符数。Bitwarden 不会导入您的 `.csv` 文件直到无任何违规项目。错误信息中的内容包含了几条相关的数据，这可以帮助你识别违规项目。例如，在上面的示例中：

* `[1]` 标识违规项目所在的索引号，调整后与大多数电子表格程序中的行号一致
* `[Login]` 标识违规项目的项目 `type`（类型）
* `"Facebook"` 标识违规项目的 `name`（名称）
* `Notes` 标识超出字符数限制的字段（列）
* `10000` 标识该字段（列）允许的字符数限制

{% hint style="success" %}
在导入到 Bitwarden 时，任何给定字段的字符数都会因为被加密而增加，比如`.csv` 中具有 8000 个字符的`备注`字段在与 Bitwarden 接触时，会扩展到 10000 多个字符，从而触发这个错误。根据经验，加密后字符数会增长 30-50%。
{% endhint %}

如果您在使用错误信息中提供的数据来查找违规项目时遇到问题，可以首先将重点放在备注上，因为备注通常会导致此错误。

### 文件大小导入限制 <a href="#file-size-import-limitations" id="file-size-import-limitations"></a>

超过以下任一项数据限制，导入可能会被拒绝：

* 如果您的导入超过 ~~6,000~~ 7,000 条项目。
* 如果您的导入超过 ~~1,000~~ 2,000 个文件夹。
* 如果您的导入超过 ~~1,000~~ 2,000 个集合。
* 如果您的导入超过 ~~6,000~~ 7,000 个项目-文件夹关系（例如，3 个文件夹中的单个项目可以说具有 3 个项目-文件夹关系）。
* 如果您的导入超过 ~~6,000~~ 14,000 个项目-集合关系（例如，3 个集合中的单个项目可以说具有 3 个项目-集合关系）。

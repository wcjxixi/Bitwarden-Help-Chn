# =导入数据到密码库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-data/)
{% endhint %}

Bitwarden 提供了一个数据导入工具，可以轻松地将任何密码管理解决方案迁移到您的个人密码库或组织密码库。您也可以使用数据导入工具从一个 Bitwarden 密码库导入到另一个 Bitwarden 密码库，或者导入一个 Bitwarden [加密导出](encrypted-exports.md)。

关于支持的导入格式的完整列表，请参阅 [Bitwarden 支持导入哪些文件格式？](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)，或者使用这些文章用于从最流行的解决方案导入：

* [从 LastPass 导入](import-guides/import-your-data-from-lastpass.md)
* [从1Password 导入](import-guides/import-your-data-from-1password.md)
* [从 Firefox 导入](import-guides/import-your-data-from-firefox.md)
* [从 Google Chrome 导入](import-guides/import-your-data-from-google-chrome.md)
* [从 Password Safe 导入](import-guides/import-data-from-password-safe.md)

{% hint style="success" %}
**还没有注册吗？**从 Bitwarden 计划中选择一个计划，并立即开始：[创建免费账户](https://vault.bitwarden.com/#/register)
{% endhint %}

## 导入到您的个人密码库 <a href="#import-to-your-personal-vault" id="import-to-your-personal-vault"></a>

**只能从**[**网页密码库**](../getting-started/getting-started-webvault.md)**或** [**CLI**](../password-manager/developer-tools/password-manager-cli.md#import) **完成**导入数据到 Bitwarden 的操作。数据在发送到服务器存储之前会在本地进行加密。要导入您的数据：

1. 在[网页密码库](../getting-started/getting-started-webvault.md)中，从顶部导航条选择**工具**。
2. 从左侧工具菜单选择**导入数据**。
3. 从格式下拉菜单，选择一个**文件格式**（参阅 [Bitwarden 支持导入哪些文件格式？](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)）。
4. 选择**选择文件**按钮并添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。
5. 选择**导入数据**按钮以完成导入。
6. 成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

{% hint style="warning" %}
Bitwarden 无法检查要导入的文件中的项目是否与密码库中的项目重复。这意味着如果一个项目同时存在于密码库和要导入的文件中，则**多次导入文件将创建重复的密码库项目**。
{% endhint %}

目前，文件附件不包含在 Bitwarden 导入操作中，需要手动上传到您的密码库。有关更多信息，请参阅[文件附件](../your-vault/file-attachments.md)。

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

### 文件大小导入限制 <a href="#file-size-import-limitations" id="file-size-import-limitations"></a>

超过以下任一数据限制的导入可能会被拒绝：

* 如果您的导入超过 6,000 条项目。
* 如果您的导入超过 1,000 个文件夹。
* 如果您的导入超过 1,000 个集合。
* 如果您的导入超过 6,000 个项目-文件夹关系（例如，3 个文件夹中的单个项目可以说具有 3 个项目-文件夹关系）。
* 如果您的导入超过 6,000 个项目-集合关系（例如，3 个集合中的单个项目可以说具有 3 个项目-集合关系）。

### 长度相关导入错误 <a href="#length-related-import-errors" id="length-related-import-errors"></a>

尝试导入 `.csv` 时通常会收到以下错误信息，这些信息表明导入文件中的某个特定值超出了该字段类型所允许的加密字符的限制：

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

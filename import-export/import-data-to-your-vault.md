# 导入数据到密码库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-data/)
{% endhint %}

将数据导入您的个人 Bitwarden 密码库，以便从任何密码管理解决方案轻松迁移。您也可以从一个 Bitwarden 密码库导入数据到另一个 Bitwarden 密码库，或者导入一个 Bitwarden [加密导出](encrypted-exports.md)。

关于支持的导入格式的完整列表，请参阅 [Bitwarden 支持导入哪些文件格式？](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)，或者使用这些文章用于从最流行的解决方案导入：

* [从 LastPass 导入](../password-manager/import-and-export/import-guides/import-data-from-lastpass.md)
* [从 1Password 导入](../password-manager/import-and-export/import-guides/import-data-from-1password.md)
* [从 Firefox 导入](../password-manager/import-and-export/import-guides/import-data-from-firefox.md)
* [从 Google Chrome 或 Chromium 导入](../password-manager/import-and-export/import-guides/import-data-from-google-chrome.md)
* [从 Microsoft Edge 导入](../password-manager/import-and-export/import-guides/import-data-from-google-chrome.md)
* [从 Password Safe 导入](import-guides/import-data-from-password-safe.md)

{% hint style="info" %}
如果您需要导入到您的组织而不是您的个人密码库，请[参阅本文](import-data-to-an-organization.md)。
{% endhint %}

## 导入到您的个人密码库 <a href="#import-to-your-personal-vault" id="import-to-your-personal-vault"></a>

数据可以从网页密码库、CLI、桌面 App 或浏览器扩展导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行[加密](../security/encryption.md)。要导入您的数据：

{% tabs %}
{% tab title="网页 App" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com)、[https://vault.bitwarden.eu](https://vault.bitwarden.eu,) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从导航选择**工具** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/7ed2e5650e9988bf7595bccebe8a5114/2024-12-03_08-52-08.png?_a=DAJCwlWIZAAB" %}
导入数据
{% endembed %}

3、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

4、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入过程不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

5、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

6、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../your-vault/file-attachments.md)、[Send](../bitwarden-send/about-send.md)、回收站以及密码历史记录等附加项目需要手动上传到您的密码库。
{% endtab %}

{% tab title="浏览器扩展" %}
要导入数据到您的密码库：

1、在**设置**选项卡中，选择**密码库**然后选择**导入项目**选项。

2、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

3、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入过程不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

4、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

5、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="桌面 App" %}
要导入数据到您的密码库：

1、选择**文件** -> **导入数据**。

2、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

3、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入过程不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
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

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7FjmtbX1PwBeLKkhklxRXl/ed7e4cd0fcaba916e75725c9153890da/2024-12-05_16-21-00.png?_a=DAJCwlWIZAAB" %}
网页密码库中的密码错误
{% endembed %}

要解决这个问题，请在文本编辑器或电子表格程序中打开 `.csv` 文件，将违规项目移除或减少其字符数。Bitwarden 不会导入您的 `.csv` 文件直到无任何违规项目。错误信息中的内容包含了几条相关的数据，这可以帮助您识别违规项目。例如，在上面的示例中：

* `[1]` 标识违规项目所在的索引号，该索引号已调整为与大多数电子表格程序中的行号匹配
* `[Login]` 标识违规项目的项目 `type`（类型）
* `"Facebook"` 标识违规项目的 `name`（名称）
* `Notes` 标识超出了字符数限制的字段（列）
* `10000` 标识该字段（列）允许的字符数限制

{% hint style="success" %}
导入时，任何给定字段的字符数都会因为被加密而增加，比如`.csv` 中具有 8000 个字符的`备注`字段在与 Bitwarden 接触时，字符数会扩展到 10000 多个，从而触发这个错误。一般来说，加密后字符数会增加 30-50%。
{% endhint %}

如果您在使用错误信息中提供的数据来查找违规项目时遇到问题，可以首先将重点放在备注上，因为备注通常会导致此错误。

### 文件大小导入限制 <a href="#file-size-import-limitations" id="file-size-import-limitations"></a>

超过以下任一项数据限制，导入可能会被拒绝：

* 如果您的导入包含超过 ~~6,000~~ 4,000 个项目。
* 如果您的导入包含超过 ~~1,000~~ 2,000 个文件夹。
* 如果您的导入包含超过 ~~1,000~~ 2,000 个集合。
* 如果您的导入包含超过 ~~6,000~~ 7,000 个项目-文件夹关系（例如，1 个项目存在于 3 个文件夹中，可以算作 3 个项目 - 文件夹关系）。
* 如果您的导入包含超过 ~~6,000~~ 8,000 个项目-集合关系（例如，1 个项目存在于 3 个集合中，可以算作 3 个项目 - 集合关系）。

### 文件包含未分配的项目 <a href="#file-contains-unassigned-items" id="file-contains-unassigned-items"></a>

如果您是用户，而不是管理员或所有者，则向组织导入数据要求所有要导入的凭据至少有一个与之关联的集合。要解决此错误，您可以：

* 在导入数据之前，从导入界面上的**集合**下拉菜单中选择一个您具有**可以管理**访问权限的现有集合。这样做会将项目添加到该集合中。
* 为导入文件中未分配的项目指定一个新的集合名称。这样做将自动创建该集合并将项目添加到其中。有关调整导入文件的帮助，请[参阅本文](condition-a-bitwarden-.csv-or-.json.md)。

{% hint style="info" %}
只有当您的组织关闭了**限制为所有者和管理员可以创建和删除集合**选项时，才会出现此错误，因为关闭这个选项将允许用户创建和导入自己的集合。
{% endhint %}

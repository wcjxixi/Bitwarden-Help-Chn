# 导入数据到组织

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-to-org/)
{% endhint %}

直接将数据导入您的组织，以便于从任何密码管理解决方案迁移。您可以从一个组织导入另一个组织，管理员可以从其个人密码库导入到组织密码库。为了获得其他安全性，您还可以导入[加密导出](encrypted-exports.md)。

有关支持的导入格式的完整列表，请参阅 [Bitwarden 支持导入哪些文件格式？](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

{% hint style="info" %}
您可以在上传 `.json` 文件之前，根据本文的步骤对其进行适当调整，从而将新的密码库项目直接导入现有的集合。 [了解如何操作](condition-a-bitwarden-.csv-or-.json.md)。
{% endhint %}

## 导入到您的组织 <a href="#import-to-your-organization" id="import-to-your-organization"></a>

数据可从网页 App 导入 Bitwarden。数据先在本地[加密](../security/encryption.md)，然后再发送到服务器进行存储。要将数据导入一个组织，请执行以下操作：

1、登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**设置** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/12fA17Iq9LdCXdhPsPYQyq/6fb380ff6165058fefe6fd311e038364/2024-12-03_15-42-21.png?_a=DAJCwlWIZAAB" %}
管理控制台导入
{% endembed %}

3、从下拉菜单中填写以下字段：

* **集合**：选择是否要将导入的内容移至现有的集合。
* **文件格式**：选择要导入的文件的格式。

4、选择**选择文件**并添加要导入的文件，或将文件内容复制/粘贴到输入框中。

{% hint style="warning" %}
导入时不会检查要导入文件中的项目是否已存在于密码库中。如果您导入多个文件或导入的文件中的项目已经存在于您的密码库中，**则会产生重复**。
{% endhint %}

5、选择**导入数据**按钮以触发导入。如果要导入受密码保护的 `.json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

[文件附件](../your-vault/file-attachments.md)需要手动上传至您的密码库。

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

### 导入文件附件 <a href="#importing-file-attachments" id="importing-file-attachments"></a>

文件附件必须手动迁移到您的 Bitwarden 密码库，因为它们目前不包括在批量导入操作中。请注意，只有高级用户，包括付费组织（家庭、团队或企业）成员才能存储文件附件。

### 长度相关的导入错误 <a href="#length-related-import-errors" id="length-related-import-errors"></a>

尝试导入 `.csv` 时通常会收到以下错误信息，这些信息表明导入文件中的某个特定值超出了该字段类型所允许的**加密**字符的限制：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7FjmtbX1PwBeLKkhklxRXl/ed7e4cd0fcaba916e75725c9153890da/2024-12-05_16-21-00.png?_a=DAJCwlWIZAAB" %}
网页密码库中的 Cipher 错误
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

* 如果您的导入包含超过 4,000 个项目。
* 如果您的导入包含超过 2,000 个文件夹。
* 如果您的导入包含超过 2,000 个集合。
* 如果您的导入包含超过 7,000 个项目-文件夹关系（例如，1 个项目存在于 3 个文件夹中，可以算作 3 个项目 - 文件夹关系）。
* 如果您的导入包含超过 8,000 个项目-集合关系（例如，1 个项目存在于 3 个集合中，可以算作 3 个项目 - 集合关系）。

### 文件包含未分配的项目 <a href="#file-contains-unassigned-items" id="file-contains-unassigned-items"></a>

如果您是用户，而不是管理员或所有者，则向组织导入数据要求所有要导入的凭据至少有一个与之关联的集合。要解决此错误，您可以：

* 在导入数据之前，从导入界面上的**集合**下拉菜单中选择一个您具有**可以管理**访问权限的现有集合。这样做会将项目添加到该集合中。
* 为导入文件中未分配的项目指定一个新的集合名称。这样做将自动创建该集合并将项目添加到其中。有关调整导入文件的帮助，请[参阅本文](condition-a-bitwarden-.csv-or-.json.md)。

{% hint style="info" %}
只有当您的组织关闭了**限制为所有者和管理员可以创建和删除集合**选项时，才会出现此错误，因为关闭这个选项将允许用户创建和导入自己的集合。
{% endhint %}

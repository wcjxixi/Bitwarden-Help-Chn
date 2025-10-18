# 从 Password Safe 导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-passwordsafe/)
{% endhint %}

使用这篇文章帮助您从 Password Safe 导出数据并将其导入 Bitwarden 中。Password Safe (V8) 目前仅支持导出为 `.csv` 文件，旧版本还支持 `.xml`。

## 从 Password Safe 导出 <a href="#export-from-password-safe" id="export-from-password-safe"></a>

完成以下步骤以从 Password Safe 桌面 App 导出数据：

1、打开 Password Safe 8 并从左上角打开 **Extras** 菜单。

2、在左侧找到 **Export** 选项，然后选择 **Passwords**。

3、对于类型，请选择 `CSV` 并输入保存导出文件的路径。将编码保留为 UTF-8。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/26qcwkrIZzv8l6n1OkaNEd/195eab889c39b8783523dbc38bfe2f93/passwordsafeV8-export.png?fm=webp&h=688&q=50&w=1422" %}
从桌面应用程序导出
{% endembed %}

4、单击右侧的灰色大箭头进入导出设置界面。

5、将分隔符设置为 **Semicolon**（分号）。

6、将文本限定符设置为 `"`（双引号）。

7、选中复选框以保留标题列。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2wnAE5NRWB76CL43QgOLz3/28cd5a175a779294a774ad9ed6cf2cbc/passwordsafeV8-exportsettings.png?fm=webp&h=620&q=50&w=810" %}
从桌面应用程序导出设置界面
{% endembed %}

8、单击 **Finish** 以开始导出。

{% hint style="warning" %}
请注意，Password Safe 将为您拥有的**每一个**类别分别导出一个 `.csv`，而不是单独一个 `.csv`。
{% endhint %}

## 准备导出的文件 <a href="#prepare-exported-file" id="prepare-exported-file"></a>

目前，我们没有为此种文件类型提供专门的导入器。要准备导出文件，请遵循[这些说明](../condition-a-bitwarden-.csv-or-.json.md)。

## 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

数据可以从网页 App、CLI、桌面 App 或浏览器扩展导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行[加密](../../security/encryption/encryption-protocols.md)。

{% tabs %}
{% tab title="网页 App" %}
要将数据导入到您的密码库：

1、选择**工具**。

2、选择**导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/7ed2e5650e9988bf7595bccebe8a5114/2024-12-03_08-52-08.png?_a=DAJAUVWIZAAB" %}
导入数据
{% endembed %}

3、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

4、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

5、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

6、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../../your-vault/file-attachments.md)、[Send](../../bitwarden-send/about-send.md)、回收站等附加项目需要手动上传到您的密码库。
{% endtab %}

{% tab title="浏览器扩展" %}
要导入数据到您的密码库：

1、选择**设置**。

2、选择**密码库选项**。

3、选择**导入项目**。将出现一个新窗口。

4、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**或（可选）选择移动到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(要求[**管理集合**](../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

5、从**文件格式**下拉菜单中，选择[导入文件的格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

6、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

7、选择**导入数据**。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

8、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="移动 App" %}
在大多数情况下，在移动设备上导入数据需要您通过在移动浏览器中打开的网页 App 执行此操作。您可以通过导航到**设置** → **密码库** → **导入项目**，从 Password Manager 快速访问此位置。

在 iOS 26 上，Bitwarden 支持通过 [Fido 凭证交换协议 (CXP)](https://fidoalliance.org/specifications-credential-exchange-specifications) 实现凭证的直接导入，轻松迁移至您的密码库。导入源 App 也需支持 CXP 协议，具体操作步骤因 App 而异。

例如，在 iOS 密码 App 中，请通过 **⋯**&#x9009;项菜单选择**导出数据至其他 App**，然后选择 Bitwarden。
{% endtab %}

{% tab title="桌面 App" %}
要将数据导入到您的密码库：

1、选择**文件**。

2、选择**导入数据**。

3、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**或（可选）选择移动到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(要求[**管理集合**](../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

4、从**文件格式**下拉菜单中，选择[导入文件的格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

5、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

6、选择**导入数据**。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
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

如果出现「导入错误」消息，则表明没有数据添加到您的密码库中。[修复导入文件问题](../../password-manager/import-and-export/import-data.md#troubleshoot-import-errors)然后重试。

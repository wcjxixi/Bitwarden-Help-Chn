# 从 Password Safe 导入数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-from-passwordsafe/)
{% endhint %}

使用这篇文章帮助您从 Password Safe 导出数据并将其导入 Bitwarden 中。 Password Safe（V8）目前仅支持导出为 `.csv` 文件，旧版本还支持 `.xml`。

## 从 Password Safe 导出 <a href="#export-from-password-safe" id="export-from-password-safe"></a>

完成以下步骤以从 Password Safe 桌面应用程序导出数据：

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



**数据必须从网页密码库或 CLI 导入到 Bitwarden**。数据在发送到服务器存储之前会在本地进行[加密](../../security/encryption.md)。

{% tabs %}
{% tab title="网页密码库" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从顶部导航条选择**工具**。

3、从工具菜单选择**导入数据**。

4、从格式下拉菜单，选择一个[文件格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import) 。

5、选择**选择文件**按钮并添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此**多次导入文件或导入具有已存在于密码库中的项目的文件将创建重复项目**。
{% endhint %}

6、选择**导入数据**按钮以开始导入。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../../your-vault/file-attachments.md)需要手动上传到您的密码库。
{% endtab %}

{% tab title="CLI" %}
要从 CLI 将数据导入您的密码库，请使用以下命令：

```shell
bw import <format> <path>
```

`bw import` 命令需要格式（使用 `bw import --formats` 获取格式列表）和路径，例如：

```shell
bw import lastpasscsv /Users/myaccount/Documents/mydata.csv
```

成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}
{% endtabs %}

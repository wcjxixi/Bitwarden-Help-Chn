# 从 1Password 导入数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-from-1password/)
{% endhint %}

使用这篇文章帮助您从 1Password 导出数据并将其导入 Bitwarden 中。1Password 数据支持导出为 `.1pif` 或 `.csv` 文件，这取决于您使用的客户端版本和操作系统。

## 从 1Password 导出 <a href="#export-your-1-password-1-pif-logins" id="export-your-1-password-1-pif-logins"></a>

完成以下步骤以从 1Password 桌面端应用程序导出数据：

1、导航到您想要导出数据的密码库

目前，1Password 不允许一次性从多个密码库中导出数据。

2、在密码库中，选择您要导出的项目

按住 Ctrl/Cmd 键可以选择多个密码库项目，或者按 Ctrl/Cmd + A 键选择所有项目。

3、在 Windows 中，选择**文件** → **导出**或右键单击并选择**导出**/在 macOS 中，选择**文件** → **导出** → **所有项目...**。

4、在导出窗口中，指定一个位置和文件格式。

根据您的客户端版本和操作系统，您可能需要在 1Password Interchange Format (.1pif) 和 Comma Delimited Text (.csv) 之间选择。

{% hint style="info" %}
**如果您从 macOS 导出 `.csv` 文件**，您还必须选择 **All Fields** 单选按钮，并选中 **Include Column Labels** 复选框。
{% endhint %}

## 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

**数据必须从网页密码库或 CLI 导入到 Bitwarden**。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption.md)。

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

[文件附件](../../vault-basics/file-attachments.md)需要手动上传到您的密码库。
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

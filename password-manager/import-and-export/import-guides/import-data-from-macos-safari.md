# 从 macOS 和 Safari 导入数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-from-safari/)
{% endhint %}

使用这篇文章帮助您从 Safari 或 macOS 导出数据并导入到 Bitwarden。

{% hint style="success" %}
导出密码要求 **Safari 15.0+** 或 **macOS Monterey (12.0)+**。
{% endhint %}

## 从 Safari 或 macOS 导出 <a href="#export-from-safari-or-macos" id="export-from-safari-or-macos"></a>

您可以直接从 Safari 或 macOS 系统偏好设置里导出密码：

{% tabs %}
{% tab title="Safari" %}
要从 Safari 导出数据：

1、从 macOS 菜单栏中选择**文件** → **导出** → **密码...**：

{% embed url="https://bitwarden.com/help/images/importing/safari.png" %}
从 Safari 导出
{% endembed %}

2、系统将弹出一个对话框，以确认您想要导出已保存的密码。选择**导出密码...**以继续。

3、将导出保存到任何位置，然后使用触控 ID 或您的 macOS 密码来完成导出。
{% endtab %}

{% tab title="macOS 系统偏好设置" %}
要从 macOS 导出数据：

1、打开 macOS **系统偏好设置**应用程序。

2、在系统偏好设置中，选择**密码**。系统会提示您使用触控 ID 或密码以继续。

3、在密码对话框中，选择菜单图标（**⋯**）然后选择**导出密码...**：

{% embed url="https://d33wubrfki0l68.cloudfront.net/63dc688ce144a4c7e8f4b438a19cd7b3f03926f4/6ba3a/help/images/importing/macos.png" %}
从 macOS 系统偏好设置导出
{% endembed %}

4、系统将弹出一个对话框，以确认您想要导出已保存的密码。选择**导出密码...**以继续。

5、将导出保存到任何位置，然后使用触控 ID 或您的 macOS 密码来完成导出。
{% endtab %}
{% endtabs %}

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

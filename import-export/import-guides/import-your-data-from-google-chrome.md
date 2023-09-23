# 从 Google Chrome 导入数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-from-chrome/)
{% endhint %}

使用这篇文章帮助您从 Google Chrome 导出数据并将其导入 Bitwarden 中。

{% hint style="success" %}
本文中的步骤也适用于任何基于 Chromium 的浏览器，包括 Opera、Microsoft Edge (Chromium)、Brave 和 Vivaldi。
{% endhint %}

## 从 Chrome 中导出 <a href="#export-from-chrome" id="export-from-chrome"></a>

您可以从桌面浏览器或移动浏览器导出 Google Chrome 的数据：

{% tabs %}
{% tab title="桌面端 Chrome" %}
要从桌面端 Chrome 导出密码：

1. 使用地址栏导航到 `chrome://settings/passwords`。
2. 在**已保存的密码**部分选择 **≡** 菜单按钮，并从下拉列表中选择**导出密码...** （可能会提示您输入计算机密码用于验证）。
3. 指定一个保存导出文件的位置，并从**格式：**字段选择 **comma-separated values**。
4. 选择**保存**以完成从 Chrome 的导出。
{% endtab %}

{% tab title="移动端 Chrome" %}
要从移动设备 Chrome 导出密码：

1. 点击 **⋯** 菜单按钮并点击**设置**。
2. 点击**密码**。
3. 点击**导出密码**（可能会提示您输入设备 PIN 码或生物特征用于验证）。
4. 指定一个位置以保存您的导出文件。
{% endtab %}
{% endtabs %}

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

# 从 Chrome、Edge & Chromium 浏览器导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-chrome/)
{% endhint %}

将您在基于 Chromium 的浏览器（例如 Google Chrome、Microsoft Edge 和 Opera）中保存的密码快速传输到您的 Bitwarden密码库。有两种方式：

* [导出浏览器数据](import-data-from-chrome.md#export-from-your-browser)然后将其导入 Bitwarden
* [从浏览器直接导入](import-data-from-chrome.md#import-directly-from-browser)（仅适用于桌面 App）

## 从浏览器导出 & 导入文件 <a href="#export-and-import-a-file-from-your-browser" id="export-and-import-a-file-from-your-browser"></a>

### 从浏览器导出 <a href="#export-from-your-browser" id="export-from-your-browser"></a>

从桌面浏览器或移动浏览器导出数据：

{% tabs %}
{% tab title="桌面端浏览器" %}
要从桌面端 Chrome 或 Edge 导出密码：

1. 使用地址栏导航至 `chrome://password-manager/settings` 或 `edge://wallet/passwords`。
2. 定位到**导出密码**，然后点击**下载文件**。可能会提示您输入计算机的密码以进行授权。对于 Microsoft Edge，这可能隐藏在已保存密码部分的 **⋯**&#x83DC;单后面。
3. 指定一个保存导出文件的位置，并验证格式是否为 **comma-separated values (CSV)**。
4. 选择**保存**以完成导出。
{% endtab %}

{% tab title="移动端浏览器" %}
要从移动设备 Chrome 或 Edge 导出密码：

1. 点击 **⋯**&#x83DC;单按钮然后点击**密码管理器**。
2. 点击**设置**。
3. 点击**导出密码**。可能会提示您输入计算机的密码以进行授权。
4. 指定一个位置以保存您的导出文件。
{% endtab %}
{% endtabs %}

### 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

数据可以从网页 App、CLI、桌面 App 或浏览器扩展导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

{% hint style="info" %}
虽然某些项目类型无法导入，但您仍然可以将它们添加到密码库：

* 将[文件附件](../../../your-vault/file-attachments.md)单独上传到新密码库。
* 在新密码库中重新创建 [Send](../../../bitwarden-send/about-send.md)。
{% endhint %}

{% tabs %}
{% tab title="网页 App" %}
要导入数据到您的密码库：

1、选择**工具**。

2、选择**导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/7ed2e5650e9988bf7595bccebe8a5114/2024-12-03_08-52-08.png?_a=DAJAUVWIZAAB" %}
导入数据
{% endembed %}

3、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

4、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

5、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

6、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../../../your-vault/file-attachments.md)、[Send](../../../bitwarden-send/about-send.md)、回收站等附加项目需要手动上传到您的密码库。
{% endtab %}

{% tab title="浏览器扩展" %}
要导入数据到您的密码库：

1、在**设置**选项卡中，选择**密码库**然后选择**导入项目**选项。

2、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

3、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

4、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

5、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="桌面 App" %}
要导入数据到您的密码库：

1、选择**文件** → **导入数据**。

2、从下拉菜单中完成以下字段：

* **导入目的地**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

3、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

4、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

5、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="CLI" %}
要通过 CLI 将数据导入您的密码库，请使用以下命令：

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

## 从浏览器直接导入 <a href="#import-directly-from-browser" id="import-directly-from-browser"></a>

您可以将密码从 Microsoft Edge、Opera 和 Vivaldi 导入 Bitwarden，而无需手动导出文件。此方法目前不适用于 Google Chrome。所有 Bitwarden 桌面 App 均兼容，但从 Mac App Store 安装的 App 除外。

要导入您的数据：

1、登录到 Bitwarden 桌面 App。

2、选择**文件**。

3、选择**导入数据**。

4、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**或（可选）选择移动到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(需要[**可以管理**](../../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

5、从**文件格式**下拉菜单中选择您的浏览器。下方将显示两个选项。

6、选择**直接从浏览器导入**：

{% embed url="https://bitwarden.com/assets/1dZKYVPQpd1TVDcmUuwLq2/23e9b222768964108ade8c02e52134ee/Directly_import_with_Chromium.png?w=652&fm=avif" %}

7、选择包含密码的**浏览器配置文件**。

8、选择**导入数据**。

9、输入计算机密码以确认。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

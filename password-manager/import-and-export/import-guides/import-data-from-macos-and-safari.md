# 从 macOS & Safari 导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-safari/)
{% endhint %}

使用这篇文章帮助您从以下平台导出数据并导入到 Bitwarden。

* Safari
* macOS
* iCloud
* Mac Keychain

{% hint style="success" %}
导出密码要求 **Safari 15.0+** 或 **macOS Monterey (12.0)+**。
{% endhint %}

## 从 Safari 或 macOS 导出 <a href="#export-from-safari-or-macos" id="export-from-safari-or-macos"></a>

您可以直接从 Safari 或 macOS 系统偏好设置里导出密码：

{% tabs %}
{% tab title="Safari" %}
要从 Safari 导出数据：

1、从 macOS 菜单栏中选择**文件** → **导出浏览器数据到文件**，选择**密码**，然后选择**下载**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3j4W80s3G7wqFtVrbzKMO4/36308c2c647912bf204739f2bc5f80f2/2024-12-30_12-58-55.png?_a=DAJAUVWIZAAB" %}
从 Safari 导出
{% endembed %}

2、将导出保存到任何位置，然后使用触控 ID 或您的 macOS 密码来完成导出。
{% endtab %}

{% tab title="macOS 系统偏好设置" %}
要从 macOS 导出数据：

1、打开 macOS 的**系统偏好设置** App。

2、在系统偏好设置中，选择**密码**。系统会提示您使用触控 ID 或密码以继续。

3、在密码对话框中，选择菜单图标 (**⋯**) 然后选择**导出密码...**：

{% embed url="https://d33wubrfki0l68.cloudfront.net/63dc688ce144a4c7e8f4b438a19cd7b3f03926f4/6ba3a/help/images/importing/macos.png" %}
从 macOS 系统偏好设置导出
{% endembed %}

4、系统将弹出一个对话框，以确认您想要导出已保存的密码。选择**导出密码...**&#x4EE5;继续。

5、将导出保存到任何位置，然后使用触控 ID 或您的 macOS 密码来完成导出。
{% endtab %}
{% endtabs %}

## 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

**数据可以从网页 App、CLI、桌面 App 或浏览器扩展导入到 Bitwarden**。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

{% tabs %}
{% tab title="网页 App" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com/)，[https://vault.bitwarden.eu/](https://vault.bitwarden.eu/) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从导航栏选择**工具** → **导入数据**：

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

## 导入错误故障排除 <a href="#troubleshoot-import-errors" id="troubleshoot-import-errors"></a>

如果出现「导入错误」消息，则表明没有数据添加到您的密码库中。[修复导入文件问题](../import-data.md#troubleshoot-import-errors)然后重试。

### iCloud/Mac 钥匙串/Safari 导入问题 <a href="#icloud-mac-keychain-safari-import-issues" id="icloud-mac-keychain-safari-import-issues"></a>

* 从 Safari 15.0 开始，您可以将密码从 Safari 导出到 `.csv` 文件中。导出后，[调整您的 .csv](../../../import-export/condition-a-bitwarden-.csv-or-.json.md) 以符合 Bitwarden 的格式，然后导入您的数据。

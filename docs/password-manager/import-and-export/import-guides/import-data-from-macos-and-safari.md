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

数据可以从网页 App、CLI、桌面 App 或浏览器扩展导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

{% tabs %}
{% tab title="网页 App" %}
要将数据导入到您的密码库：

1、选择**工具**。

2、选择**导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/7ed2e5650e9988bf7595bccebe8a5114/2024-12-03_08-52-08.png?_a=DAJAUVWIZAAB" %}
导入数据
{% endembed %}

3、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**并（可选）选择移动项目到的**文件夹**。
* **组织密码库**：选择组织密码库的名称然后选择一个**集合**。(需要[**可以管理**](../../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

4、从**文件格式**下拉菜单中，选择[导入文件的格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

5、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

6、选择**导入数据**。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="浏览器扩展" %}
要导入数据到您的密码库：

1、选择**设置**。

2、选择**密码库选项**。

3、选择**导入项目**。将出现一个新窗口。

4、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**并（可选）选择移动项目到的**文件夹**。
* **组织密码库**：选择组织密码库的名称然后选择一个**集合**。(需要[**可以管理**](../../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

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

* **个人密码库**：选择**我的密码库**并（可选）选择移动项目到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(要求[**管理集合**](../../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

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

## 导入错误故障排除 <a href="#troubleshoot-import-errors" id="troubleshoot-import-errors"></a>

如果出现「导入错误」消息，则表明没有数据添加到您的密码库中。[修复导入文件问题](../import-data.md#troubleshoot-import-errors)然后重试。

### iCloud/Mac 钥匙串/Safari 导入问题 <a href="#icloud-mac-keychain-safari-import-issues" id="icloud-mac-keychain-safari-import-issues"></a>

* 从 Safari 15.0 开始，您可以将密码从 Safari 导出到 `.csv` 文件中。导出后，[调整您的 .csv](../condition-a-bitwarden-.csv-or-.json.md) 以符合 Bitwarden 的格式，然后导入您的数据。

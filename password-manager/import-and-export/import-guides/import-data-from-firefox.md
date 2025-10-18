# 从 Firefox 导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-firefox/)
{% endhint %}

使用这篇文章帮助您从 Firefox 导出数据并将其导入 Bitwarden 中。

## 从 Firefox 导出 <a href="#export-from-firefox" id="export-from-firefox"></a>

从 Firefox 导出可能会有所不同，具体取决于您所使用的版本，或者如果您使用的是基于 Firefox 的浏览器（例如 Tor 浏览器或 Waterfox）：

{% tabs %}
{% tab title="最新版本" %}
要从最新版 Firefox 导出您的登录信息：

1、使用地址栏导航到 `about:logins`。

2、选择右上方的 **⋯**&#x83DC;单按钮，并从下拉列表中选择**导出登录信息...**。

将提示您指定一个位置来保存导出的登录信息。

Firefox 会将登录信息导出为 `.csv` 文件。
{% endtab %}

{% tab title="旧版本" %}
某些旧版本的 Firefox 不支持本地导出。完成以下步骤以使用 FF Password Exporter 导出：

1、[下载](https://github.com/kspearrin/ff-password-exporter)，安装然后打开 FF Password Exporter。

2、从检测到的 Firefox 用户配置中或从指定的自定义配置目录中，选择一个用户配置。如果您为用户配置设置了主密码，请输入该密码。

![](../../../.gitbook/assets/image.png)

3、选择**导出密码**按钮。

4、选择 `.csv` 文件格式，并将文件保存到设备中。
{% endtab %}

{% tab title="基于 Firefox" %}
某些基于 Firefox 的浏览器提供了不同于 vanilla Firefox 的登录导出位置。如果从**最新版本**导出不成功，请尝试以下方法：

1、使用地址栏导航到 `about:preferences#privacy`。

2、点击**保存登录信息**按钮。

3、选择右上方的 **⋯**&#x83DC;单按钮，并从下拉列表中选择**导出登录信息**。

将提示您指定一个位置来保存导出的登录信息。

大多数基于 Firefox 的浏览器会将登录信息导出为 `.csv` 文件。
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

4、从**文件格式**下拉菜单中，选择[导入文件的格式](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

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
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(要求[**管理集合**](../../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

5、从**文件格式**下拉菜单中，选择[导入文件的格式](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

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

4、从**文件格式**下拉菜单中，选择[导入文件的格式](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

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

如果出现「导入错误」消息，则表明没有数据添加到您的密码库中。[修复导入文件问题](../import-data.md#troubleshoot-import-errors)然后重试。

# 从 1Password 导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-1password/)
{% endhint %}

使用这篇文章帮助您从 1Password 导出数据并将其导入 Bitwarden 中。1Password 数据支持导出为 `.1pux`（要求 1Password v8.5+）、`.1pif` 或 `.csv` 文件，这取决于您使用的客户端版本和操作系统。了解 [1Password 导出包含哪些数据](https://support.1password.com/export/?mac#get-help)。

## 从 1Password 导出 <a href="#export-your-1-password-1-pif-logins" id="export-your-1-password-1-pif-logins"></a>

完成以下步骤以从 1Password 桌面 App 导出数据：

{% hint style="success" %}
目前，只有 1Password 8 允许您一次导出多个密码库。如果您使用 1Password 8，请跳至**步骤 3**。
{% endhint %}

1、导航到您想要导出数据的密码库。

2、在密码库中，选择您要导出的项目。按住 Ctrl/Cmd 键可以选择多个密码库项目，或者按 Ctrl/Cmd + A 键选择所有项目。

3、在 Windows 中，选择**文件** → **导出**或右键单击并选择**导出**/在 macOS 中，选择**文件** → **导出** → **所有项目...**。

4、在导出窗口中，指定一个位置和文件格式。

{% hint style="info" %}
如果您从 macOS 导出 `.csv` 文件，您还必须选择 **All Fields** 单选按钮，然后选中 **Include Column Labels** 复选框。
{% endhint %}

## 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

**数据可以从网页 App、CLI、桌面 App 或浏览器扩展导入到 Bitwarden**。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

{% tabs %}
{% tab title="网页 App" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com)，[https://vault.bitwarden.eu/](https://vault.bitwarden.eu/) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

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

{% tab title="桌面端 App" %}
要导入数据到您的密码库：

1、选择**文件** → **导入数据**。

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

## 导入故障排除 <a href="#import-troubleshooting" id="import-troubleshooting"></a>

### 文件大小导入限制 <a href="#file-size-import-limitations" id="file-size-import-limitations"></a>

超过以下任一项数据限制，导入可能会被拒绝：

* 如果您的导入包含超过 4,000 个项目。
* 如果您的导入包含超过 2,000 个文件夹。
* 如果您的导入包含超过 2,000 个集合。
* 如果您的导入包含超过 7,000 个项目-文件夹关系（例如，1 个项目存在于 3 个文件夹中，可以算作 3 个项目 - 文件夹关系）。
* 如果您的导入包含超过 8,000 个项目-集合关系（例如，1 个项目存在于 3 个集合中，可以算作 3 个项目 - 集合关系）。

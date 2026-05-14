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
3. 点击**导出密码...** 。可能会提示您输入设备 PIN 码或生物识别信息以进行授权。
4. 指定一个位置以保存您的导出文件。
{% endtab %}
{% endtabs %}

### 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

数据可以从网页 App、浏览器扩展、桌面 App 以及 CLI 导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

{% hint style="info" %}
虽然某些项目类型无法导入，但您仍然可以将它们添加到密码库：

* 将[文件附件](../../your-vault/vault-items/file-attachments.md)单独上传到新密码库。
* 在新密码库中重新创建 [Send](../../bitwarden-send/about-send.md)。
{% endhint %}

{% tabs %}
{% tab title="网页 App" %}
要将数据导入到您的 Bitwarden 密码库：

1、选择**工具**。

2、选择**导入**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1NbyPb9dN545ZqKGRZYB3x/e6b8f3f31aa82bb05cef12c5a5c4c193/2025-12-17_11-25-08.png?w=1156&#x26;fm=avif" alt=""><figcaption><p>导入项目</p></figcaption></figure></div>

3、从**密码库**下拉菜单中，选择数据的保存目的地：

* 要将数据保存到您的个人密码库中，请选择**我的密码库**。（可选）选择一个现有[**文件夹**](../../your-vault/vault-navigation/folders.md)来组织导入的项目。

{% hint style="success" %}
如果您的数据文件包含您之前密码管理器中的文件夹，并且您从下拉菜单中选择了一个目标文件夹，则导入的文件夹将被嵌套在您选择的文件夹内。
{% endhint %}

* 要将数据保存到某个组织的密码库中，请选择该组织的名称。（可选）选择一个集合来组织导入的项目并与其他成员共享。（您只能选择您拥有[**可以管理**](../../../admin-console/manage-shared-items/collections/collection-permissions.md)权限的集合。）

4、从**文件格式**下拉菜单中，选择您的导出数据的[文件格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

5、要输入您的数据，请执行以下操作之一：

* 选择**选择文件**，然后从您的计算机中选择已导出的文件。
* 将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

6、选择**导入**。如果您正在导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

7、数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。如果您是从其他密码管理器或浏览器导入到 Bitwarden，您可能还需要从该工具中删除数据。
{% endtab %}

{% tab title="浏览器扩展" %}
要将数据导入到您的密码库：

1、选择**设置**。

2、选择**密码库选项**。

3、选择**导入项目**。将出现一个新窗口。

4、从**密码库**下拉菜单中，选择数据的保存目的地：

* 要将数据保存到您的个人密码库中，请选择**我的密码库**。（可选）选择一个现有[**文件夹**](../../your-vault/vault-navigation/folders.md)来组织导入的项目。

{% hint style="success" %}
如果您的数据文件包含您之前密码管理器中的文件夹，并且您从下拉菜单中选择了一个目标文件夹，则导入的文件夹将被嵌套在您选择的文件夹内。
{% endhint %}

* 要将数据保存到某个组织的密码库中，请选择该组织的名称。（可选）选择一个集合来组织导入的项目并与其他成员共享。（您只能选择您拥有[**可以管理**](../../../admin-console/manage-shared-items/collections/collection-permissions.md)权限的集合。）

5、从**文件格式**下拉菜单中，选择[导入文件的格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

6、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

7、选择**导入**。如果您正在导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

8、数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。如果您是从其他密码管理器或浏览器导入到 Bitwarden，您可能还需要从该工具中删除数据。
{% endtab %}

{% tab title="移动端" %}
在大多数情况下，在移动设备上导入数据需要您通过在移动浏览器中打开的网页 App 执行此操作。您可以通过导航到**设置** → **密码库** → **导入项目**，以从 Password Manager 快速访问此位置。

在 iOS 26 上，Bitwarden 支持使用 [Fido 凭证交换协议 (CXP)](https://fidoalliance.org/specifications-credential-exchange-specifications) 导入，以直接轻松地将密码、通行密钥、信用卡和个人身份信息迁移到您的密码库中。要导出数据的 App 也必须支持 CXP，具体操作步骤因 App 而异。

例如，在 iOS 密码 App 中，使用 **⋯**&#x9009;项菜单选择**导出数据至其他 App**，然后选择 Bitwarden。
{% endtab %}

{% tab title="桌面端" %}
要将数据导入到您的密码库：

1、从导航菜单选择**导入**。

2、从**密码库**下拉菜单中，选择数据的保存目的地：

* 要将数据保存到您的个人密码库中，请选择**我的密码库**。（可选）选择一个现有[**文件夹**](../../your-vault/vault-navigation/folders.md)来组织导入的项目。

{% hint style="success" %}
如果您的数据文件包含您之前密码管理器中的文件夹，并且您从下拉菜单中选择了一个目标文件夹，则导入的文件夹将被嵌套在您选择的文件夹内。
{% endhint %}

* 要将数据保存到某个组织的密码库中，请选择该组织的名称。（可选）选择一个集合来组织导入的项目并与其他成员共享。（您只能选择您拥有[**可以管理**](../../../admin-console/manage-shared-items/collections/collection-permissions.md)权限的集合。）

3、从**文件格式**下拉菜单中，选择[导入文件的格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

4、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

5、选择**导入**。如果您正在导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

6、数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。如果您是从其他密码管理器或浏览器导入到 Bitwarden，您可能还需要从该工具中删除数据。
{% endtab %}

{% tab title="CLI" %}
要将数据导入您的密码库，请使用以下 [CLI](../../developer-tools/cli/password-manager-cli.md) 命令：

```shell
bw import <format> <path>
```

`bw import` 命令需要格式（使用 `bw import --formats` 获取格式列表）和路径，例如：

```shell
bw import <format> /Users/myaccount/Documents/mydata.csv
```

数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。如果您是从其他密码管理器或浏览器导入到 Bitwarden，您可能还需要从该工具中删除数据。
{% endtab %}
{% endtabs %}

如果出现「导入错误」消息，则不会有任何数据添加到您的密码库中。[修复导入文件问题](../import-data.md#troubleshoot-import-errors)然后重试。

## 从浏览器直接导入 <a href="#import-directly-from-browser" id="import-directly-from-browser"></a>

Bitwarden 桌面 App 可以从这些浏览器导入密码，而无需手动导出文件：

* Chrome
* Edge（仅限 Windows 和 macOS）
* Opera
* Brave
* Vivaldi（仅限 Windows 和 macOS）
* Arc（仅限 macOS）

此选项适用于从此[下载页面](https://bitwarden.com/download/#downloads-desktop)安装的 Windows 和 Mac 桌面 App。直接导入方式不适用于 Linux 系统，也不适用于从 Mac App Store 或 Windows Microsoft Store 安装的桌面 App。

{% hint style="info" %}
已知在 2025.11.0 及更高版本中，**从浏览器直接导入**选项（具体来说是 `bitwarden_chromium_import_helper.exe` 进程）在尝试从浏览器存储中提取凭据时，可能会被某些 EDR 软件或 Windows 用户账户控制 (UAC) 标记。

* **作为管理员**，您可以主动通过 UAC 或 EDR 软件将 `bitwarden_chromium_import_helper.exe` 设置为以管理员身份运行，以防止用户尝试导入时出现失败或警告。
* **作为用户**，如果在此过程中出现允许 App 更改您的设备的提示，请选择**是**以继续导入。

**\[译者注]**：EDR - Endpoint Detection and Response（终端威胁检测与响应）。EDR 是一种企业级安全软件，用来监控电脑（终端）上的可疑行为，并及时阻止或警告潜在的攻击。
{% endhint %}

要从浏览器导入您的数据：

1、登录到 Bitwarden 桌面 App。

2、选择**文件**。

3、选择**导入数据**。

4、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**以及（可选）选择移动项目到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(需要[**管理集合**](../../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

5、从**文件格式**下拉菜单中选择您的浏览器。如果该浏览器兼容并安装在同一设备上，下方将显示两个选项。

6、选择**从浏览器直接导入**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1dZKYVPQpd1TVDcmUuwLq2/23e9b222768964108ade8c02e52134ee/Directly_import_with_Chromium.png?w=652&#x26;fm=avif" alt=""><figcaption><p>直接从浏览器导入</p></figcaption></figure></div>

7、选择包含密码的**浏览器配置文件**。

8、选择**导入**。

9、输入计算机密码以确认。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

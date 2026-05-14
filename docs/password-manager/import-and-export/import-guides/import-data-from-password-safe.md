# 从 Password Safe 导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-passwordsafe/)
{% endhint %}

使用这篇文章帮助您从 Password Safe 导出数据并导入到 Bitwarden。Password Safe (V8) 目前仅支持导出为 `.csv` 文件，旧版本还支持 `.xml`。

## 从 Password Safe 导出 <a href="#export-from-password-safe" id="export-from-password-safe"></a>

完成以下步骤以从 Password Safe 桌面 App 导出数据：

1、打开 Password Safe 8 并从左上角打开 **Extras** 菜单。

2、在左侧找到 **Export** 选项，然后选择 **Passwords**。

3、对于类型，请选择 `CSV` 并输入保存导出文件的路径。将编码保留为 UTF-8。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/26qcwkrIZzv8l6n1OkaNEd/195eab889c39b8783523dbc38bfe2f93/passwordsafeV8-export.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>从桌面 App 导出</p></figcaption></figure></div>

4、单击右侧的灰色大箭头进入导出设置界面。

5、将分隔符设置为 **Semicolon**（分号）。

6、将文本限定符设置为 `"`（双引号）。

7、选中复选框以保留标题列。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2wnAE5NRWB76CL43QgOLz3/28cd5a175a779294a774ad9ed6cf2cbc/passwordsafeV8-exportsettings.png?w=810&#x26;fm=avif" alt=""><figcaption><p>桌面 App 导出设置界面</p></figcaption></figure></div>

8、单击 **Finish** 以开始导出。

{% hint style="warning" %}
请注意，Password Safe 将为您拥有的**每一个**类别分别导出一个 `.csv`，而不是单独一个 `.csv`。
{% endhint %}

## 准备导出的文件 <a href="#prepare-exported-file" id="prepare-exported-file"></a>

目前，我们没有为此种文件类型提供专门的导入器。要准备导出文件，请遵循[这些说明](../condition-bitwarden-import.md)。

## 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

数据可以从网页 App、浏览器扩展、桌面 App 以及 CLI 导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

{% hint style="info" %}
虽然某些项目类型无法导入，但您仍可将其添加到密码库：

* 将[文件附件](../../your-vault/vault-items/file-attachments.md)单独上传到新的密码库。
* 在新的密码库中重新创建 [Send](../../bitwarden-send/about-send.md)。
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

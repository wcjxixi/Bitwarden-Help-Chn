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

* 将[文件附件](../../your-vault/vault-items/file-attachments.md)逐个上传到新的密码库。
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

{% hint style="info" %}
如果您的数据文件包含您之前密码管理器中的文件夹，并且您从下拉菜单中选择了一个目标文件夹，则导入的文件夹将被嵌套在您选择的文件夹内。
{% endhint %}

* 要将数据保存到某个组织密码库中，请选择组织的名称。（可选）选择一个[集合](../../../admin-console/manage-shared-items/collections/create-collections.md)来组织导入的项目并与其他成员共享。（您只能选择您具有[**管理集合**](../../../admin-console/manage-shared-items/collections/collection-permissions.md#permissions)权限的集合。）

4、从**文件格式**下拉菜单中，选择您的导出数据的[文件格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

5、要输入您的数据，请执行以下操作之一：

* 选择**选择文件**，然后从您的计算机中选择已导出的文件。
* 将已导出的文件的内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

6、选择**导入**。如果您正在导入受密码保护的 `.json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

7、数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。如果您是从其他密码管理器或浏览器导入到 Bitwarden，您可能还需要从该工具中删除数据。
{% endtab %}

{% tab title="浏览器扩展" %}
要将数据导入到您的密码库：

1、选择**设置**。

2、选择**密码库选项**。

3、选择**导入项目**。将出现一个新窗口。

4、从**密码库**下拉菜单中，选择数据的保存目的地：

* 要将数据保存到您的个人密码库中，请选择**我的密码库**。（可选）选择一个现有[**文件夹**](../../your-vault/vault-navigation/folders.md)来组织导入的项目。

{% hint style="info" %}
如果您的数据文件包含您之前密码管理器中的文件夹，并且您从下拉菜单中选择了一个目标文件夹，则导入的文件夹将被嵌套在您选择的文件夹内。
{% endhint %}

* 要将数据保存到某个组织密码库中，请选择组织的名称。（可选）选择一个[集合](../../../admin-console/manage-shared-items/collections/create-collections.md)来组织导入的项目并与其他成员共享。（您只能选择您具有[**管理集合**](../../../admin-console/manage-shared-items/collections/collection-permissions.md#permissions)权限的集合。）

5、从**文件格式**下拉菜单中，选择[导入文件的格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

6、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

7、选择**导入**。如果您正在导入受密码保护的 `.json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

8、数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。如果您是从其他密码管理器或浏览器导入到 Bitwarden，您可能还需要从该工具中删除数据。
{% endtab %}

{% tab title="移动端" %}
在移动设备上导入数据有两种方式。使用 CXP 直接导入通常最为简便，但目前仅支持少数密码管理 App。

### 移动设备最常用的方式 <a href="#most-common-method-for-mobile" id="most-common-method-for-mobile"></a>

对于大多数设备，打开移动浏览器，登录 Bitwarden，然后按照[网页 App 的导入步骤](import-data-from-password-safe.md#wang-ye-app)操作。

### 使用凭据交换协议 (CXP) 直接导入 <a href="#direct-import-with-the-cxp" id="direct-import-with-the-cxp"></a>

Bitwarden 支持 [FIDO 凭据交换协议 (CXP)](https://fidoalliance.org/specifications-credential-exchange-specifications/?lang=zh-hans)。该协议通过省去手动下载和处理数据文件的步骤，提供了一种替代且通常更快的导入方式。当前存储您数据的密码管理器 App 也必须支持 CXP，具体步骤因 App 而异。

#### 使用 iOS 设备 CXP <a href="#cxp-with-ios-devices" id="cxp-with-ios-devices"></a>

要使用 **iOS 26+** 移动设备导入数据：

1、打开保存有数据的其他兼容 CXP 的密码管理器 App。

2、根据 App 的不同，找到导出数据选项，然后选择要导入的项目。您可能需要完成额外步骤，例如登录或确认您要移动数据。

{% hint style="info" %}
例如，在 **Apple 密码** App 中：

1. 点击 <i class="fa-ellipsis">:ellipsis:</i>选项图标。
2. 点击**导出数据到其他 App**。
3. 在出现的列表中，勾选您想要转移的密码和通行密钥。完成后，点击**继续**。
{% endhint %}

3、在**导出密码**界面上，点击**继续**。

4、选择 **Bitwarden** 作为目标位置，然后点击**继续**。

5、点击**在 Bitwarden 中继续**。

6、Bitwarden App 将打开。点击**继续**以确认导入。

7、完成后，将出现一条消息，确认您的数据已成功导入。

#### 使用 **Android** 设备 CXP <a href="#cxp-with-android-devices" id="cxp-with-android-devices"></a>

要使用 **Android 10+** 移动设备导入数据：

1、打开 Bitwarden App。

2、点击**设置**。

3、点击**密码库**。

4、点击**导入项目**。

5、点击**从其他 App 导入**。

6、选择您保存数据的其他兼容 CXP 的密码管理器 App，然后点击**继续**。

7、根据 App 的不同，选择要导入的项目。您可能需要完成额外步骤，例如登录或确认您要移动数据。

8、完成后，将出现一条消息，确认您的数据已成功导入。

{% hint style="info" %}
目前，Android 不支持通过 CXP 导入 Dashlane 数据。
{% endhint %}
{% endtab %}

{% tab title="桌面端" %}

{% endtab %}

{% tab title="CLI" %}

{% endtab %}
{% endtabs %}

如果出现「导入错误」消息，则不会有任何数据添加到您的密码库中。[修复导入文件问题](../import-data.md#troubleshoot-import-errors)然后重试。

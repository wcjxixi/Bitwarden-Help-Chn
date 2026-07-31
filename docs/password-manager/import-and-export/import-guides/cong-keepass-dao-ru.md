# 从 KeePass 导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-keepass/)
{% endhint %}

从 KeePass 迁移时，您可以选择要导入到 Bitwarden 的文件类型：

* 导入使用密码和可选的密钥文件保护的加密 KeePass `.kdbx` 文件。
* 从 KeePass2 或 KeePassX 导入 `.csv` 或 `.xml` 文件。

{% hint style="info" %}
虽然某些项目类型无法导入，但您仍可将其添加到密码库：

* 将[文件附件](../../your-vault/vault-items/file-attachments.md)逐个上传到新的密码库。
* 在新的密码库中重新创建 [Send](../../bitwarden-send/about-send.md)。
{% endhint %}

## 从 KeePass 导出 <a href="#export-from-keepass" id="export-from-keepass"></a>

从 KeePass 导出的步骤可能因版本而异。例如，要在 macOS 上从 KeePassXC 导出数据：

* `.kdbx`：前往**数据库** → **另存数据库为**。输入文件名然后选择**保存**。
* `.csv` 或 `.xml`：前往**数据库** → **导出**。选择**是**确认导出，输入密码，然后选择**解锁**。

## 导入到 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

导出 KeePass 数据后，请根据您的文件类型执行相应步骤。

{% tabs %}
{% tab title="KDBX" %}
此选项可能更受青睐，因为它会创建一个加密文件，您可以使用密码或密钥文件对其进行保护。您可以使用 Bitwarden 网页 App、浏览器扩展、桌面 App 或 CLI。

{% hint style="info" %}
使用 [CLI 导入](../import-data.md#cli) `.kdbx` 文件时，将提示您输入 KeePass 密码，如果已添加到 KeePass 数据库中，还会要求提供密钥文件路径。
{% endhint %}

要将 `.kdbx` 文件导入到您的 Bitwarden 密码库中：

1、在 Bitwarden 网页 App、浏览器扩展或桌面 App 中，打开**导入**页面：

* 网页 App：前往**工具** → **导入**。
* 浏览器扩展：前往**设置** → **密码库选项** → **导入**。
* 桌面 App：从导航栏中选择**导入**。

2、从**密码库**下拉菜单中，选择数据保存的位置：

* 要将数据保存到您的个人密码库中，请选择**我的密码库**。（可选）选择一个现有[**文件夹**](../../your-vault/vault-navigation/folders.md)来组织导入的项目。

{% hint style="info" %}
当您将 KeePass 数据导入到「我的密码库」时，您已设置的任何 KeePass 群组都将迁移为 Bitwarden [文件夹](../../your-vault/vault-navigation/folders.md)。如果您在导入文件时还选择了**文件夹**，则导入的文件夹将被嵌套在您选择的文件夹内。
{% endhint %}

* 要将数据保存到某个组织密码库中，请选择组织的名称。（可选）选择一个[集合](../../../admin-console/manage-shared-items/collections/create-collections.md)来组织导入的项目并与其他成员共享。（您只能选择您具有[**管理集合**](../../../admin-console/manage-shared-items/collections/collection-permissions.md#permissions)权限的集合。）

{% hint style="info" %}
当您将 KeePass 数据导入到组织密码库时，您已设置的任何 KeePass 群组都将迁移为 Bitwarden [集合](../../../admin-console/manage-shared-items/collections/about-collections.md)，并嵌套在您选择的导入目标集合中。
{% endhint %}

3、从**文件格式**下拉菜单中选择 **KeePass (kdbx)**。

4、输入您的 **KeePass 主密码**。

5、如果您在 KeePass 数据库安全设置中添加了密钥文件：

1. 选择**添加密钥文件**。
2. 在**密钥文件上传**中，选择**选择文件**然后选取您导出的密钥文件。文件名以 `.keyx` 结尾。

6、在 **KDBX 文件上传**中，选择**选择文件**然后选取您导出的文件。文件名以 `.kdbx` 结尾。

7、选择**导入**。

8、数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。您可能还需要从 KeePass 中删除您的数据。

{% hint style="info" %}
如果您的文件中包含任何启用了高级设置**在进程内存中保护值**的 KeePass 字段，该字段在 Bitwarden 密码库中将变为[隐藏字段](../../your-vault/vault-items/custom-fields.md)。
{% endhint %}
{% endtab %}

{% tab title="CSV 或 XML" %}
如果您将数据导出为 `.csv` 或 `.xml` 文件，您可以通过 Bitwarden 网页 App、浏览器扩展、桌面 App 或 CLI 导入该文件。数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

要导入您的 KeePass 数据：

1、在 Bitwarden 网页 App、浏览器扩展或桌面 App 中，打开**导入**页面：

* 网页 App：前往**工具** → **导入**。
* 浏览器扩展：前往**设置** → **密码库选项** → **导入**。
* 桌面 App：从导航栏中选择**导入**。

2、从**密码库**下拉菜单中，选择数据保存的位置：

* 要将数据保存到您的个人密码库中，请选择**我的密码库**。（可选）选择一个现有[**文件夹**](../../your-vault/vault-navigation/folders.md)来组织导入的项目。

{% hint style="info" %}
当您将 KeePass 数据导入到「我的密码库」时，您已设置的任何 KeePass 群组都将迁移为 Bitwarden [文件夹](../../your-vault/vault-navigation/folders.md)。如果您在导入文件时还选择了**文件夹**，则导入的文件夹将被嵌套在您选择的文件夹内。
{% endhint %}

* 要将数据保存到某个组织密码库中，请选择组织的名称。（可选）选择一个[集合](../../../admin-console/manage-shared-items/collections/create-collections.md)来组织导入的项目并与其他成员共享。（您只能选择您具有[**管理集合**](../../../admin-console/manage-shared-items/collections/collection-permissions.md#permissions)权限的集合。）

{% hint style="info" %}
当您将 KeePass 数据导入到组织密码库时，您已设置的任何 KeePass 群组都将迁移为 Bitwarden [集合](../../../admin-console/manage-shared-items/collections/about-collections.md)，并嵌套在您选择的导入目标集合中。
{% endhint %}

3、从**文件格式**下拉菜单中选择 **KeePass (csv)** 或 **KeePass (xml)**。

4、选择**选择文件**，然后从您的电脑中选取导出的文件。

5、选择**导入**。

6、数据导入后，请从您的计算机中删除已导出的数据文件。这将在您的计算机受到威胁时为您提供保护。您可能还需要从 KeePass 中删除您的数据。

{% hint style="info" %}
如果您的文件中包含任何启用了高级设置**在进程内存中保护值**的 KeePass 字段，该字段在 Bitwarden 密码库中将变为[隐藏字段](../../your-vault/vault-items/custom-fields.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

如果出现「导入错误」消息，则不会有任何数据添加到您的密码库中。[修复导入文件问题](../import-data.md#troubleshoot-import-errors)然后重试。

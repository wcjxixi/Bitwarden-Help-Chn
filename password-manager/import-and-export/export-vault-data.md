# 导出密码库数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/export-your-data/)
{% endhint %}

您通过任一个客户端应用程序导出你的个人密码库数据，或通过网页密码库或 CLI 导出组织密码库。导出的数据可以下载为纯文本的 `.json` 或 `.csv` 文件，或 `.json` [加密导出](encrypted-exports.md)。

我们建议使用 `.json` 作为更完整的导出，而 `.csv` 目前不能导出支付卡和身份。有关 Bitwarden `.csv` 和 `.json` 文件格式的完整信息，请参阅[使用 Bitwarden .csv 或 .json](condition-a-bitwarden-.csv-or-.json.md)。

密码库导出**不包含**[文件附件](../vault-basics/file-attachments.md)、回收站中的项目、密码历史记录以及 Send。

{% hint style="warning" %}
除非您使用[加密导出](encrypted-exports.md)，否则不要通过不安全的渠道（例如电子邮件）来存储或发送导出的文件，用完后请立即将其删除。
{% endhint %}

## 导出个人密码库 <a href="#export-a-personal-vault" id="export-a-personal-vault"></a>

{% hint style="warning" %}
从个人密码库导出数据**不会**导出您所属组织的任何数据。要导出组织数据，请遵循[此说明](export-vault-data.md#export-an-organization-vault)。
{% endhint %}

{% tabs %}
{% tab title="网页密码库" %}
要从网页密码库导出您的个人密码库数据：

1、从顶部导航栏中选择**工具**。

2、从左侧工具菜单中选择**导出密码库**。

3、在导出密码库页面中，选择一个**文件格式**（`.json`、`.csv` 或 `.json (Encrypted)`）。

4、如果选择 `.json (Encrypted)`，请选择您希望用于加密导出的**文件类型**：

* **账户备份**：该文件只能导入到当前生成加密导出文件的 Bitwarden 账户。
* **密码保护**：可以使用加密导出过程中设置的密码将此文件导入任何 Bitwarden 帐户。

5、选择**确认格式**，输入您的主密码，然后选择**导出密码库**按钮以完成。
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展导出您的个人密码库数据：

1、打开 **⚙️设置**标签。

2、向下滚动到**工具**部分并选择**导出密码库**选项。

3、在导出密码库视图中，选择一个**文件格式**（`.json`、`.csv`，或 `.json (Encrypted)`）。

{% hint style="success" %}
如果您需要将此数据导入新的 Bitwarden 帐户，我们建议使用网络密码库创建**密码保护**的导出。
{% endhint %}

4、输入您的**主密码**然后选择**提交**。

{% hint style="info" %}
如果您是从 Vivaldi 浏览器扩展导出，您可能需要弹出浏览器扩展以便导出能正常工作。
{% endhint %}
{% endtab %}

{% tab title="桌面端" %}
要从桌面应用程序导出您的个人密码库数据：

1、从菜单栏中，导航到**文件** → **导出密码库**。

2、在导出密码库窗口中，选择一个**文件格式**（`.json`、`.csv`，或 `.json (Encrypted)`）。

{% hint style="success" %}
如果您需要将此数据导入新的 Bitwarden 帐户，我们建议使用网络密码库创建**密码保护**的导出。
{% endhint %}

3、输入您的**主密码**然后选择 **📥下载**按钮。
{% endtab %}

{% tab title="移动端" %}
要从移动应用程序导出您的个人密码库数据：

1、点击 ⚙️**设置**标签。

2、向下滚动到**工具**部分并点击**导出密码库**选项。

3、在导出密码库视图中，选择一个**文件格式**（`.json`、`.csv`，或 `.json (Encrypted)`）。

{% hint style="success" %}
如果您需要将此数据导入新的 Bitwarden 帐户，我们建议使用网络密码库创建**密码保护**的导出。
{% endhint %}

4、输入您的**主密码**然后点击**导出密码库**按钮。
{% endtab %}

{% tab title="CLI" %}
要从 CLI 导出您的个人密码库数据，需使用 `export` 命令。默认情况下，`export` 导出密码库为 `.csv` 文件并保存在工作目录下，然而，这种行为可以通过使用选项来更改：

```shell
bw export --output /users/me/documents/ --format json --password mYP@ssw0rd
```

`--password` 选项可用于指定一个加密 `encrypted_json` 导出的密码，而不是您的[帐户加密密钥](../../security/account-encryption-key.md)。

更多详情，请参阅我们的 [CLI 文档](../getting-started/bitwarden-cli.md)。
{% endtab %}
{% endtabs %}

## 导出组织密码库 <a href="#export-an-organization-vault" id="export-an-organization-vault"></a>

组织的[管理员和所有者](../../admin-console/user-management/user-types-and-access-control.md)可以通过网页密码库或 CLI 导出他们的组织密码库（即组织拥有的所有项目）：

{% tabs %}
{% tab title="网页密码库" %}
要从网页密码库导出您的组织密码库：

1、打开您的组织并选择**工具**标签页：

{% embed url="https://bitwarden.com/_gatsby/image/311837f02e3437995c8358a122e5cd27/bbe264169e2cda0721f81dc34b00459b/Screen%20Shot%202022-05-16%20at%2011.06.12%20AM.webp?eu=dd8c06e1e0c0f5d10968f4816876636de0385eaba85363d63a62e5fb48adca822df31c57209529e224385e8f86e841b367c779694ae7d7d3c3ba1ca6ec61a90e07d15fe936e27651522290fcb1f5034c6ec44b5fa3d29c59ab6924d7e6b3b5771c011f78fb2cbdd2b9ae6760b78a7a63bee2a1266f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32b9c0d34d245f6e0326669dae0ec027c5cc43423f46214055f6633a8406ad6538c5e3fda80fd17f7de5a0ca3475d2c0af83eb12ac7872b1d044fac06e2f5062cf4bf2f814f5d2660413812fe7944add52415a41830289223ed83a30fd7a9aa119c4&a=w%3D779%26h%3D457%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.366Z" %}
导出组织密码库
{% endembed %}

2、在工具菜单中选择**导出密码库**。

3、在导出密码库页面，选择一个**文件格式**（`.json`、`.csv` 或 `.json (Encrypted)`）。

4、输入您的**主密码**然后选择**导出密码库**按钮。

{% hint style="info" %}
导出组织密码库数据将被事件日志捕获。[了解更多](../../admin-console/organization-basics/event-logs.md)。
{% endhint %}
{% endtab %}

{% tab title="CLI" %}
要从 CLI 导出您的组织密码库，需使用带 `--organizationid <orgId>` 选项的 `export` 命令。

默认情况下，`export` 导出密码库为 `.csv` 文件并保存在工作目录下，然而，这种行为可以通过使用选项来更改：

```shell
bw export my-master-password --organizationid 7063feab-4b10-472e-b64c-785e2b870b92 --output /users/me/documents/ --format json
```

{% hint style="success" %}
如果您一时不知道您的 `organizationid` 值，可以在命令行使用 `bw list organizations` 来获取它。
{% endhint %}

更多详情，请参阅我们的 [CLI 文档](../getting-started/bitwarden-cli.md)。

{% hint style="info" %}
导出组织密码库数据将被事件日志捕获。[了解更多](../../admin-console/organization-basics/event-logs.md)。
{% endhint %}


{% endtab %}
{% endtabs %}

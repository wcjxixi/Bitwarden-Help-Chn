# =导出密码库数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/export-your-data/)
{% endhint %}

您通过任一个 Bitwarden App 导出您的个人密码库数据，或通过网页 App 或 CLI 导出组织密码库。导出的数据可以下载为纯文本的 `.json` 或 `.csv` 文件，或[加密导出](encrypted-exports.md)的 `.json` 文件。

我们建议使用 `.json` 作为更完整的导出，而 `.csv` 目前不能导出支付卡和身份。有关 Bitwarden `.csv` 和 `.json` 文件格式的完整信息，请参阅[调整 Bitwarden .csv 或 .json](condition-a-bitwarden-.csv-or-.json.md)。

密码库导出**将不会包含**[文件附件](../your-vault/file-attachments.md)、回收站中的项目、~~密码历史记录~~以及 Send。

{% hint style="warning" %}
除非您使用[加密导出](encrypted-exports.md)，否则不要通过不安全的渠道（例如电子邮件）来存储或发送导出的文件，用完后请立即将其删除。
{% endhint %}

## 导出个人密码库 <a href="#export-a-personal-vault" id="export-a-personal-vault"></a>

{% hint style="info" %}
从个人密码库导出数据**不会**导出您所属组织的任何数据。要导出组织数据，请遵循[此说明](export-vault-data.md#export-an-organization-vault)。
{% endhint %}

{% tabs %}
{% tab title="网页 App" %}
要通过网页 App 导出您的个人密码库数据：

1、从导航选择**工具** → **导出密码库**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5PUGzasNsQnABG9gtso4o3/9be00b37afafd779c20fd9624dd9512d/2024-12-03_08-59-25.png?_a=DAJCwlWIZAAB" %}
导出个人密码库
{% endembed %}

2、选择**导出自**的位置和**文件格式**（`.json`、`.csv` 或 `.json (Encrypted)`）。如果从**导出自**下拉菜单中选择组织，则只会导出您拥有「[可以管理](../admin-console/manage-members/member-roles.md)」权限的集合。

3、如果您选择了 `.json (Encrypted)`，请选择您希望用于加密导出的**文件类型**：

* **账户限制**：该文件只能导入到当前生成加密导出文件的 Bitwarden 账户。
* **密码保护**：可以使用加密导出过程中设置的密码将此文件导入任何 Bitwarden 账户。

4、选择**确认格式**，输入您的主密码，然后选择**导出密码库**按钮以完成。将需要使用您的主密码或电子邮件验证码确认您的权限。

您的导出文件将被发送到「下载」文件夹或网页浏览器设置的下载文件的位置。
{% endtab %}

{% tab title="浏览器扩展" %}
要通过浏览器扩展导出您的个人密码库数据：

1、打开 **⚙️设置**标签。

2、选择**密码库**然后选择**导出密码库**。

3、在导出密码库视图中，选择一个**文件格式**（`.json`、`.csv`，或 `.json (Encrypted)`）。

4、如果您选择了 `.json (Encrypted)`，请选择您希望用于加密导出的**文件类型**：

* **账户限制**：该文件只能导入到当前生成加密导出文件的 Bitwarden 账户。
* **密码保护**：可以使用加密导出过程中设置的密码将此文件导入任何 Bitwarden 账户。

4、选择**导出密码库**。

4、确认您的**主密码**然后选择**导出密码库**。

{% hint style="info" %}
如果您是从 Vivaldi 导出，您可能需要弹出浏览器扩展以便导出能正常工作：

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1cbJy0jLBmSQmRumvYzVwp/be8132e558dd91c6d282f08a02e2d5fa/2024-12-02_14-10-52.png?_a=DAJCwlWIZAAB" alt="" data-size="original">
{% endhint %}
{% endtab %}

{% tab title="桌面端" %}
要通过桌面 App 导出您的个人密码库数据：

1、从菜单栏中，导航到**文件** → **导出密码库**。

2、在导出密码库窗口中，选择一个**文件格式**（`.json`、`.csv`，或 `.json (Encrypted)`）。

{% hint style="success" %}
如果您需要将此数据导入新的 Bitwarden 帐户，我们建议使用网络密码库创建**密码保护**的导出。
{% endhint %}

3、输入您的**主密码**然后选择 **📥下载**按钮。
{% endtab %}

{% tab title="移动端" %}
要通过移动 App 导出您的个人密码库数据：

1、点击 ⚙️**设置**标签。

2、向下滚动到**工具**部分并点击**导出密码库**选项。

3、在导出密码库视图中，选择一个**文件格式**（`.json`、`.csv`，或 `.json (Encrypted)`）。

{% hint style="success" %}
如果您需要将此数据导入新的 Bitwarden 帐户，我们建议使用网络密码库创建**密码保护**的导出。
{% endhint %}

4、输入您的**主密码**然后点击**导出密码库**按钮。
{% endtab %}

{% tab title="CLI" %}
要通过 CLI 导出您的个人密码库数据，需使用 `export` 命令。默认情况下，`export` 导出密码库为 `.csv` 文件并保存在工作目录下，然而，这种行为可以通过使用选项来更改：

```batch
bw export --output /users/me/documents/ --format json --password mYP@ssw0rd
```

`--password` 选项可用于指定一个加密 `encrypted_json` 导出的密码，而不是您的[帐户加密密钥](../security/encryption/encryption-key-rotation.md)。

更多详情，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/cli/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

有关个人密码库导出中包含的所有项目和字段的完整列表，请参阅此 **⬇️**[JSON 示例](https://assets.ctfassets.net/7rncvj1f8mw7/3klSoZBBd57skEvwFkcMJc/9dfe5d696c102cd32da88dc325706738/Individual_vault_export.json)。

## 导出组织密码库 <a href="#export-an-organization-vault" id="export-an-organization-vault"></a>

组织的[管理员和所有者](../admin-console/manage-members/member-roles.md)可以通过网页密码库或 CLI 导出他们的组织密码库（即组织拥有的所有项目）：

组织成员可以按照上述说明，从**导出自**下拉菜单中选择组织，导出其拥有「可以管理」权限的来自任何集合的数据。具有访问导入/导出权限的管理员、所有者和[自定义角色](../admin-console/manage-members/member-roles.md#custom-role)用户可以使用以下说明导出**所有**组织数据：

{% tabs %}
{% tab title="网页 App" %}
要通过网页 App 导出您的组织密码库：

1、使用产品切换器打开**管理控制台**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、从导航栏选择**导出** → **导出密码库**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2UQyeVwsMcc1f7vcJOnnUO/4949e1a6b8422222865fdd7a6275aea5/2024-12-03_09-01-45.png?_a=DAJCwlWIZAAB" %}
导出组织密码库
{% endembed %}

3、在导出密码库页面，选择一个**文件格式**（`.json`、`.csv` 或 `.json (Encrypted)`），然后选择**确认格式**按钮。

4、输入您的主密码然后选择**导出密码库**按钮。

{% hint style="info" %}
导出组织密码库数据将被事件日志捕获。[了解更多](../admin-console/oversight-visibility/event-logging/event-logs.md)。
{% endhint %}
{% endtab %}

{% tab title="CLI" %}
要通过 CLI 导出您的组织密码库，需使用带 `--organizationid <orgId>` 选项的 `export` 命令。

默认情况下，`export` 导出密码库为 `.csv` 文件并保存在工作目录下，然而，这种行为可以通过使用选项来更改：

```batch
bw export my-master-password --organizationid 7063feab-4b10-472e-b64c-785e2b870b92 --output /users/me/documents/ --format json
```

{% hint style="success" %}
如果您一时不知道您的 `organizationid` 值，可以在命令行使用 `bw list organizations` 来获取它。
{% endhint %}

更多详情，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/cli/password-manager-cli.md)。

{% hint style="info" %}
导出组织密码库数据将被事件日志捕获。[了解更多](../admin-console/oversight-visibility/event-logging/event-logs.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

有关组织密码库导出中包含的所有项目和字段的完整列表，请参阅此 **⬇️**[JSON 示例](https://assets.ctfassets.net/7rncvj1f8mw7/2oQPd5ZsY1N0hph4N6pBrY/b5fc7c05ac238d71d9a1902a58559cc6/Organization_vault_export.json)。

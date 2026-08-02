# 导出密码库数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/export-your-data/)
{% endhint %}

导出您的密码库数据，包括登录和笔记，以备份重要信息或[转移到新的 Bitwarden 密码库](import-data.md)。在导出前，数据会通过客户端本地解密，因此不会在互联网上传输未加密的数据。

{% hint style="success" icon="lightbulb" %}
如果您将 Bitwarden 添加到新设备，并且您的账户托管在我们的云服务器上，您无需创建导出，只需在您的新设备上[下载 Bitwarden](https://bitwarden.com/download/)，然后使用您现有的账户登录即可。
{% endhint %}

{% hint style="warning" %}
除非您使用[加密导出](encrypted-exports.md)，否则不要通过不安全的渠道（例如电子邮件）来存储或发送导出的文件，用完后请立即将其删除。
{% endhint %}

## 导出的文件类型 <a href="#export-file-types" id="export-file-types"></a>

导出可以下载为以下几种格式：

* `.json`（纯文本）
* `.csv`（纯文本）
* [`.json (Encrypted)`](encrypted-exports.md)（加密）
* `.zip (with attachments)`（包含 `.json` 文件和您的附件）

{% hint style="info" %}
`.zip` 导出目前仅适用于个人密码库数据。
{% endhint %}

* **（仅限 iOS 26）**&#x76F4;接导出到其他 App

{% hint style="info" %}
直接导出到其他 App 需要目标 App 支持 [FIDO 凭证交换协议 (CXP)](https://fidoalliance.org/specifications-credential-exchange-specifications/?lang=zh-hans)。
{% endhint %}

查看[示例 `.csv` 和 `.json` 文件](condition-bitwarden-import.md)以决定哪种格式最适合您。我们推荐使用加密的 `.json` 选项以获得最佳安全性和最完整的导出。只有 `.json` 导出包含：

* 支付卡
* 身份
* [存储的通行密钥](../autofill/more-autofill-options/autofill-passkeys.md)
* [SSH 密钥](../developer-tools/ssh/ssh-agent.md)

所有导出格式都不包含回收站项目或 [Send](../bitwarden-send/about-send.md)。有关个人密码库导出中包含的所有项目和字段的完整列表，请查看这个 <i class="fa-arrow-down-to-bracket">:arrow-down-to-bracket:</i>**️** [.json 示例](https://bitwarden.com/assets/3klSoZBBd57skEvwFkcMJc/9dfe5d696c102cd32da88dc325706738/Individual_vault_export.json)。

## 导出个人密码库 <a href="#export-a-personal-vault" id="export-a-personal-vault"></a>

{% hint style="info" %}
个人密码库导出不包括组织拥有的数据。只有管理员、所有者和某些自定义角色可以通过网页 App 或命令行工具[导出组织项目](../../admin-console/manage-shared-items/export-organization-items/export-organization-items.md)。但是，具有**管理集合**[权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)的成员可以导出他们可以访问的集合中的数据。
{% endhint %}

{% tabs %}
{% tab title="网页 App" %}
要导出密码库数据：

1、选择**工具**。

2、选择**导出**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5PUGzasNsQnABG9gtso4o3/4e4880193ff45c22f0474c129e68e4e3/2025-12-17_11-43-59.png?w=1156&#x26;fm=avif" alt=""><figcaption><p>导出项目</p></figcaption></figure></div>

3、从**导出自**下拉菜单，中选择要下载的数据：

* 选择**我的密码库**以导出您个人密码库中的项目。
* 选择某个组织密码库的名称，这将导出您拥有[**管理集合**](../../admin-console/manage-shared-items/collections/collection-permissions.md)权限的集合中的数据。

4、选择**文件格式**：`.json`、`.csv`、`.json (Encrypted)` 或 `.zip (with attachments)`。

5、（可选）如果您选择 `.json (Encrypted)`，请为此[加密文件](encrypted-exports.md)选择**导出类型**：

* **账户限制**：该文件只能导入到生成加密导出文件的当前 Bitwarden 账户。

{% hint style="warning" %}
**账户限制**的导出只能导入到其来源的同一账户。账户限制的导出不能导入到其他账户。包括：

* 具有相同电子邮箱地址但位于不同[地理位置](../../security/server-geographies.md)或自托管服务器上的账户
* 具有相同电子邮箱地址的其他账户，即使原始账户已被删除

此外，[轮换您的账户加密密钥](../../security/encryption/encryption-key-rotation.md)将使账户限制的导出无法解密。**如果您轮换了账户加密密钥，请使用新加密密钥导出的新文件替换任何旧文件。**

如果您希望将加密的 `.json` 文件导入到不同的 Bitwarden 账户，请改为生成**密码保护**的导出。
{% endhint %}

* **密码保护**：可以使用加密导出过程中设置的密码将此文件导入任何 Bitwarden 账户。

{% hint style="success" icon="lightbulb" %}
选择 <i class="fa-arrows-rotate-reverse">:arrows-rotate-reverse:</i> 以安全地生成用于导出的唯一密码。如果您选择此操作，请务必将此密码保存在安全的地方。
{% endhint %}

6、选择**导出**。

7、输入您的主密码或电子邮件验证码以确认。

导出的文件将保存到**浏览器设置的位置**。默认情况下，这通常是「下载」文件夹，但您可以在网页浏览器中更改它。
{% endtab %}

{% tab title="浏览器扩展" %}
要导出密码库数据：

1、选择 <i class="fa-gear-complex">:gear-complex:</i>**设置**图标。

2、选择**密码库选项**。

3、选择**导出密码库**。

4、从**导出自**下拉菜单，中选择要下载的数据：

* 选择**我的密码库**以导出您个人密码库中的项目。
* 选择某个组织密码库的名称，这将导出您具有[**管理集合**](../../admin-console/manage-shared-items/collections/collection-permissions.md)权限的集合中的数据。

5、选择**文件格式**：`.json`、`.csv`、`.json (Encrypted)` 或 `.zip (with attachments)`。

6、（可选）如果您选择 `.json (Encrypted)`，请为[加密文件](encrypted-exports.md)选择**导出类型**：

* **账户限制**：该文件只能导入到生成加密导出文件的当前 Bitwarden 账户。

{% hint style="danger" %}
**账户限制**的导出只能导入到其来源的同一账户。账户限制的导出不能导入到其他账户。包括：

* 具有相同电子邮箱地址但位于不同[地理位置](../../security/server-geographies.md)或自托管服务器上的账户
* 具有相同电子邮箱地址的其他账户，即使原始账户已被删除

此外，[轮换您的账户加密密钥](../../security/encryption/encryption-key-rotation.md)将使账户限制的导出无法解密。**如果您轮换了账户加密密钥，请使用新加密密钥导出的新文件替换任何旧文件。**

如果您希望将加密的 `.json` 文件导入到不同的 Bitwarden 账户，请改为生成**密码保护**的导出。
{% endhint %}

* **密码保护**：可以使用加密导出过程中设置的密码将此文件导入任何 Bitwarden 账户。

{% hint style="success" %}
选择 <i class="fa-arrows-rotate-reverse">:arrows-rotate-reverse:</i> 以安全地生成用于导出的唯一密码。如果您选择此操作，请务必将此密码保存在安全的地方。
{% endhint %}

7、选择**导出密码库**。

8、输入您的主密码或电子邮件验证码以确认。

9、选择**导出密码库**。

导出的文件将保存到**浏览器设置的位置**。默认情况下，这通常是「下载」文件夹，但您可以在网页浏览器中更改它。
{% endtab %}

{% tab title="桌面端" %}
要导出密码库数据：

1、从导航菜单中选择**导出**。

2、从**导出自**下拉菜单，中选择要下载的数据：

* 选择**我的密码库**以导出您个人密码库中的项目。
* 选择某个组织密码库的名称，这将导出您具有[**管理集合**](../../admin-console/manage-shared-items/collections/collection-permissions.md)权限的集合中的数据。

3、选择**文件格式**：`.json`、`.csv`、`.json (Encrypted)` 或 `.zip (with attachments)`。

4、（可选）如果您选择 `.json (Encrypted)`，请为[加密文件](encrypted-exports.md)选择**导出类型**：

* **账户限制**：该文件只能导入到生成加密导出文件的当前 Bitwarden 账户。

{% hint style="danger" %}
**账户限制**的导出只能导入到其来源的同一账户。账户限制的导出不能导入到其他账户。包括：

* 具有相同电子邮箱地址但位于不同[地理位置](../../security/server-geographies.md)或自托管服务器上的账户
* 具有相同电子邮箱地址的其他账户，即使原始账户已被删除

此外，[轮换您的账户加密密钥](../../security/encryption/encryption-key-rotation.md)将使账户限制的导出无法解密。**如果您轮换了账户加密密钥，请使用新加密密钥导出的新文件替换任何旧文件。**

如果您希望将加密的 `.json` 文件导入到不同的 Bitwarden 账户，请改为生成**密码保护**的导出。
{% endhint %}

* **密码保护**：可以使用加密导出过程中设置的密码将此文件导入任何 Bitwarden 账户。

{% hint style="success" %}
选择 <i class="fa-arrows-rotate-reverse">:arrows-rotate-reverse:</i> 以安全地生成用于导出的唯一密码。如果您选择此操作，请务必将此密码保存在安全的地方。
{% endhint %}

5、选择**导出密码库**。

6、输入您的主密码或电子邮件验证码以确认。

7、选择**导出密码库**。

导出的文件将保存到**设备设置的位置**。默认情况下，这通常是「下载」文件夹，但您可以在设备设置中更改它。
{% endtab %}

{% tab title="移动端" %}
您可以通过下载文件在移动设备上导出 Bitwarden 数据。如果您要迁移到其他支持 [FIDO 凭据交换协议 (CXP)](https://fidoalliance.org/specifications-credential-exchange-specifications/?lang=zh-hans) 的移动 App，可以直接传输数据。iOS 26+ 和 Android 10+ 支持使用 CXP 来[导入](import-data.md#yi-dong-duan)和导出数据。

以下是 iOS 和 Android 上的文件导出步骤，以及 iOS 上的 CXP 操作步骤。要在 Android 上使用 CXP，您需要从目标 App 开始操作，具体步骤取决于您使用的 App。

要导出密码库数据：

1、点击 <i class="fa-gears">:gears:</i>**设置**图标。

2、点击**密码库**。

3、点击**导出密码库**。

{% hint style="info" %}
在 iOS 26+ 上，您可以选择**将密码库导出到文件**和**将密码库导出到其他 App**。

如果您选择**将密码库导出到文件**，请继续执行这些说明。如果您选择**将密码库导出到其他 App**，请按照屏幕上的简单流程，将数据直接导出到支持 [FIDO 凭证交换协议 (CXP)](https://fidoalliance.org/specifications-credential-exchange-specifications/?lang=zh-hans) 的任何其他 App。
{% endhint %}

4、选择一个**文件格式**：`.json`、`.csv` 或 `.json (Password protected)`。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6IvRA9oYfTvO9GxylX2MMh/528b65ca6d83f0f28c469b62078570d5/2025-01-22_09-51-29.png?w=715&#x26;fm=avif" alt=""><figcaption><p>在移动端导出密码库</p></figcaption></figure></div>

5、（可选）如果您选择 `.json (Password protected)`，请输入一个新密码。如果您将此文件导入回 Bitwarden，则需要输入该密码。

6、输入您的主密码。

7、选择**导出**。

导出的文件将保存到**设备设置的位置**。默认情况下，这通常是「下载」文件夹，但您可以在设备设置中更改它。
{% endtab %}

{% tab title="CLI" %}
{% hint style="success" icon="lightbulb" %}
在导出之前请使用 `bw sync` 同步您的密码库，以确保包含最新的信息。
{% endhint %}

要通过 [CLI](../developer-tools/cli/password-manager-cli.md) 导出您的个人密码库数据，请使用 `export` 命令。默认情况下，`export` 导出密码库为 `.csv` 文件并保存在工作目录下，然而，这种行为可以通过使用选项来更改：

```batch
bw export --output /users/me/documents/ --format json --password mYP@ssw0rd
```

`--password` 选项可用于指定一个密码以加密 `encrypted_json` 导出，而不是您的[账户加密密钥](../../security/encryption/encryption-key-rotation.md)。
{% endtab %}
{% endtabs %}

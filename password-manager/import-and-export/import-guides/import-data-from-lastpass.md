# 从 LastPass 导入

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-from-lastpass/)
{% endhint %}

使用这篇文章帮助您从 LastPass 导出数据并将其导入 Bitwarden 中。

## 从 LastPass 导出 <a href="#export-from-lastpass" id="export-from-lastpass"></a>

您可以从 LastPass 的网页密码库或从 LastPass 浏览器扩展导出数据：

{% hint style="success" %}
您可以跳过此步骤并立即开始使用[直接导入选项](import-data-from-lastpass.md#import-to-bitwarden)导入到 Bitwarden。
{% endhint %}

{% tabs %}
{% tab title="LastPass 网页密码库" %}
要从 LastPass 网页密码库导出您的数据：

1、从左侧边栏选择 **🚀Advanced Options** 选项。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5uCdlKvfGTjYIEJvKtpbQw/14cd0e6bfb36a53b1f1d6f88d3808a90/lastpassadvancedoptions.png?fm=webp&h=864&q=50&w=1272" %}
从网页密码库导出
{% endembed %}

2、从管理您的密码库部分，选择 **Export** 选项。此时，LastPass 将向您发送一封电子邮件以确认导出。

3、在您的收件箱中，确认此导出操作，返回到您的 LastPass 网页密码库，并再次选择 **Export** 选项以完成导出。

根据您的浏览器，您的密码库数据将自动保存为 `.csv` 文件或以 `.csv` 格式显示在屏幕上：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6TIRhpByBC4coLrP58zG8a/fb2da8df01a2e0f56e87f45612182e86/lastpass-copy.png?fm=webp&h=320&q=50&w=749" %}
LastPass 导出
{% endembed %}

4、如果您的密码库数据显示在屏幕上，全选显示的数据，将其复制并粘帖到一个新的 `export.csv` 文件中。

{% hint style="warning" %}
一些用户报告了一个 bug：密码中的特殊字符（`&`、`<`、`>` 等）在导出时，被更改成了 HTML 编码的值（如，`&amp;`）。

如果您在导出的数据中发现了这个 bug，请在导入 Bitwarden 之前，使用文本编辑器查找并替换所有被更改的值。
{% endhint %}
{% endtab %}

{% tab title="LastPass 浏览器扩展" %}
要从 LastPass 浏览器扩展导出您的数据：

1、在浏览器扩展中，导航到 **Account** → **Fix a problem yourself** → **Export vault items** → **Export data for use anywhere**。

{% hint style="info" %}
如果您使用旧版本的 LastPass 浏览器扩展，则可能需要导航至 **Account Options** → **Advanced** → **Export** → **LastPass CSV File**。
{% endhint %}

2、输入您的主密码以验证导出尝试。

根据您的浏览器，您的密码库数据将自动保存为 `.csv` 文件或以 `.csv` 格式显示在屏幕上：

{% embed url="https://bitwarden.com/_gatsby/image/5d00d7966772b2eebd82f4eab311a41e/9c99d13d898028d2b23c9e80ec2865fe/lastpass-copy.webp?eu=dc8603e4e4ceaa810d3aa2823d23363ce43702f8ff053fd93561b1f946adc88775fa4f5571922eb37e3f538bdbe110bc33922b661dec84ddc8b84bf4e264ad5b51d60cbb63b17201032a96f7b4f10e453cc51259a3d69b59ab3e788ca1f7f733134f0372f52befd4afb76620e6d26c71bff2e5303b97ef67e75000078d4270aa6ce6d7d92c188ab7d247af94a7db7ac9cfb8514520defb7f557f1d000ebf2feff4ba50273928115960cef95dc1349eb16a1864255f5d02ff656fd853e4306080a0bbf01e9a6728bee8802f30d894&a=w%3D749%26h%3D320%26fm%3Dwebp%26q%3D75&cd=2022-08-31T14%3A01%3A10.043Z" %}
LastPass 导出
{% endembed %}

3、如果您的密码库数据显示在屏幕上，全选显示的文本数据，然后将其复制并粘帖到一个新的 `export.csv` 文件中。
{% endtab %}
{% endtabs %}

## 导入到 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

数据可以直接从 LastPass 导入，也可以使用 LastPass [导出的文件](import-data-from-lastpass.md#export-from-lastpass)导入。如果您是使用 LastPass SSO 的团队成员，LastPass 管理员将需要完成一个简短的设置过程，然后您才能使用**直接导入**选项（[了解更多](import-data-from-lastpass.md#direct-import-with-sso)）。在所有情况下，数据在发送到服务器存储之前会在本地进行[加密](../../../security/encryption/encryption-protocols.md)。

{% hint style="info" %}
请参阅这篇 [LastPass 支持文章](https://support.lastpass.com/help/export-your-passwords-and-secure-notes-lp040004)，了解 LastPass 支持和不支持哪些导出内容。请注意，Bitwarden 不支持导入附件。
{% endhint %}

{% tabs %}
{% tab title="直接导入" %}
{% hint style="info" %}
如果您是使用 LastPass SSO 的团队成员，LastPass 管理员需要先完成一个简单的设置过程，然后您才能使用**直接导入**选项（[了解更多](import-data-from-lastpass.md#direct-import-with-sso)）。
{% endhint %}

可以使用 Password Manager 浏览器扩展和桌面 App 从您的 LastPass 账户直接导入个人密码库数据，而无需您上传文件。要进行直接导入：

1、登录到 Password Manager 浏览器扩展或桌面 App。

2、在浏览器扩展中，选择**设置**选项卡，然后选择密码库然后选择**导入项目**选项。或者，在桌面 App 中，选择**文件** -> **导入数据**。

3、从下拉菜单中完成以下字段：

* **密码库**或**导入目的地**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择 LastPass。
* 在 LastPass 说明框中，选择**直接从 LastPass 导入**选项。
* 输入您的 **LastPass 电子邮箱地址**。如果您代表企业进行导入，我们建议您使用 LastPass [管理员](https://support.lastpass.com/s/document-item?language=en_US\&bundleId=lastpass\&topicId=LastPass/uac_admin_roles.html&_LANG=enus)凭据。使用超级管理员凭据可能会导致导入失败。

4、选择**导入数据**按钮以触发导入。

5、将提示您输入 LastPass 主密码，或者如果您的 LastPass 账户使用 SSO，登录到您的 IdP。无论哪种情况，请按照提示登录到您的 LastPass 账户。

{% hint style="success" %}
如果您的 LastPass 账户激活了多重身份验证，系统将提示您输入来自身份验证器 App 的一次性通行代码。如果您使用 Duo 方式的 MFA，则仅支持应用内审批以满足您的 MFA 要求。
{% endhint %}

[文件附件](../../../your-vault/file-attachments.md)、回收站等附加项目需要手动上传到您的密码库。
{% endtab %}

{% tab title="文件导入" %}
从大多数 Password Manager App 导出的文件可以导入到 Bitwarden（了解如何[从 LastPass 导出文件](import-data-from-lastpass.md#export-from-lastpass)）。在本节中，我们将重点介绍使用网页 App 进行导入：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com)，[https://vault.bitwarden.eu](https://vault.bitwarden.eu) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从导航选择**工具** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/7ed2e5650e9988bf7595bccebe8a5114/2024-12-03_08-52-08.png?_a=DAJAUVWIZAAB" %}
导入数据
{% endembed %}

3、从下拉菜单中完成以下字段：

* **导入目的地**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](../../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

4、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

5、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

6、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../../../your-vault/file-attachments.md)、回收站等附加项目需要手动上传到您的密码库。
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

## 使用 SSO 直接导入 <a href="#direct-import-with-sso" id="direct-import-with-sso"></a>

{% hint style="danger" %}
以下 IdP 不支持使用 SSO 的 LastPass 账户的直接导入：

* Google Workspace
* ADFS
* Microsoft Entra ID
{% endhint %}

如果您是使用 SSO 的 LastPass 团队管理员，则您需要先完成以下操作，然后您的团队才能使用**直接导入**选项：

* 在 IdP 的 LastPass 应用程序中添加 `bitwarden://sso-callback-lp` 和 `bitwarden://import-callback-lp` 作为允许的回调 URL。

如果您的用户使用 Password Manager 浏览器扩展：

* 在您的 IdP 的 LastPass 应用程序中添加 `[protocol]://[identifier]/sso-connector.html?lastpass=1` 或 `https://your.server.com/sso-connector.html?lp=1` 作为允许的回调 URL。
* 在您的 IdP 的 LastPass 应用程序中添加 `chrome-extension://nngceckbapebfimnlniiiahkandclblb`，`ms-browser-extension://jbkfoedolllekgbhcbcoahefnbanhhlh` 和/或 `moz-extension://23462205-0e62-4cc8-80c4-910cf54b82c2` 作为允许的回调 URL。

## 导入故障排除 <a href="#import-troubleshooting" id="import-troubleshooting"></a>

### 文件大小导入限制 <a href="#file-size-import-limitations" id="file-size-import-limitations"></a>

超过以下任一项数据限制，导入可能会被拒绝：

* 如果您的导入包含超过 4,000 个项目。
* 如果您的导入包含超过 2,000 个文件夹。
* 如果您的导入包含超过 2,000 个集合。
* 如果您的导入包含超过 7,000 个项目-文件夹关系（例如，1 个项目存在于 3 个文件夹中，可以算作 3 个项目 - 文件夹关系）。
* 如果您的导入包含超过 8,000 个项目-集合关系（例如，1 个项目存在于 3 个集合中，可以算作 3 个项目 - 集合关系）。

### 字段大小导入错误 <a href="#field-size-import-errors" id="field-size-import-errors"></a>

尝试导入 `.csv` 时通常会收到以下错误信息，这些信息表明导入文件中的某个特定值超出了该字段类型所允许的加密字符的限制：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7FjmtbX1PwBeLKkhklxRXl/ed7e4cd0fcaba916e75725c9153890da/2024-12-05_16-21-00.png?_a=DAJAUVWIZAAB" %}
网页密码库中的密码错误
{% endembed %}

要解决这个问题，请在文本编辑器或电子表格程序中打开 `.csv` 文件，将违规项目移除或减少其字符数。Bitwarden 不会导入您的 `.csv` 文件直到无任何违规项目。错误信息中的内容包含了几条相关的数据，这可以帮助您识别违规项目。例如，在上面的示例中：

* `[1]` 标识违规项目所在的索引号，该索引号已调整为与大多数电子表格程序中的行号匹配
* `[Login]` 标识违规项目的项目 `type`（类型）
* `"Facebook"` 标识违规项目的 `name`（名称）
* `Notes` 标识超出了字符数限制的字段（列）
* `10000` 标识该字段（列）允许的字符数限制

{% hint style="success" %}
导入时，任何给定字段的字符数都会因为被加密而增加，比如`.csv` 中具有 8000 个字符的`备注`字段在与 Bitwarden 接触时，字符数会扩展到 10000 多个，从而触发这个错误。一般来说，加密后字符数会增加 30-50%。
{% endhint %}

如果您在使用错误信息中提供的数据来查找违规项目时遇到问题，可以首先将重点放在备注上，因为备注通常会导致此错误。

### 最大集合错误 <a href="#maximum-collections-error" id="maximum-collections-error"></a>

当将 Lastpass 的 `.csv` 导出文件导入到[免费组织](../../../plans-and-pricing/password-manager/about-bitwarden-plans.md)时，您可能会看到如下错误：

{% embed url="https://bitwarden.com/_gatsby/image/1fc86e561312a1d2ee8810743571dfd9/7d9c8827861df387d48095fa03565c23/Screen%20Shot%202022-11-02%20at%209.51.25%20AM.webp?eu=dadc03b7e099a9835d3df38a697b6060e93d52f8fc546583346cb1af4ffa9e8075f7480320c028b12f6c5bd881b316ef65c77d3048bdd48fc8bf1ff3bb37f90a01850bee36e67507507e91adb7f754103ec71f58abdb8c4ce32e78cbfaeaea214e055f35fb3eeed0afea6020f39d7167aea9a16c3b91ed22e14456098c1f6ef818efc896456be79ada19ae9cbdc04394c5bd2e5f35c4fb33247f44160cee2ce9f3bb01733c2a140f329aad5a94609eb36d4e692057581c9434788500a503529bbbbfce5fd97879fca9c82c7084acffc48213b22f77f9cd22c6f346644e53fb&a=w%3D831%26h%3D327%26fm%3Dwebp%26q%3D75&cd=2022-11-29T13%3A10%3A06.522Z" %}
免费组织最大集合错误
{% endembed %}

当 Lastpass 导出包含 3 个或更多 `grouping` 值时，就会发生该错误。`grouping` 字段中的值被 Bitwarden 解释为[集合](../../../admin-console/organization-basics/about-collections.md)，但[免费组织](../../../plans-and-pricing/password-manager/about-bitwarden-plans.md)限制为仅两个集合。例如，下面的 `.csv` 将导致该错误：

```
url,username,password,totp,extra,name,grouping,fav
https://www.facebook.com/login.php,username,password,,,Facebook,Social,0
https://twitter.com/login,username,password,,,Twitter,Social,0
https://asana.com/,login,password,,,Asana,Productivity Tools,0
https://github.com/login,username,password,,,Github,Productivity Tools,0
https://www.paypal.com/login,username,password,,,Paypal,Finance,0
https://www.bankofamerica.com/,username,password,,,Bankofamerica,Finance,0
```

要解决这个问题，删除每个项目的 `grouping` 列和 `grouping` 基准，包括后面的逗号，例如，编辑：

```
https://github.com/login,username,password,,,Github,Productivity Tools,0
```

将其减少为：

```
https://github.com/login,username,password,,,Github,0
```

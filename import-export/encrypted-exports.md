# 加密导出

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/encrypted-export/)
{% endhint %}

密码库数据可以[导出](export-vault-data.md)为加密的 `.json` 文件。加密的导出文件将包含来自您的组织或个人密码库的项目，但不包含 Send、~~密码历史记录、~~回收站或项目附件。可以使用网页密码库或 [CLI](../password-manager/developer-tools/password-manager-cli.md#export) 创建受密码保护的导出。Bitwarden 提供两种加密导出类型：

* **账户限制**：导出加密文件，只能重新导入到生成加密导出文件的 Bitwarden 账户。此过程使用专用于 Bitwarden 账户的[账户加密密钥](../security/account-encryption-key.md)。
* **密码保护**：使用您选择的密码保护导出的加密文件。该文件使用您选择的密码解密，并且可以导入任何 Bitwarden 账户。此指定的密码经过加盐处理，使用 PBKDF2 以 100,000 次迭代派生出加密密钥，最后使用 HDKF 拉伸为一个新的加密密钥，用于加密您的数据以及消息身份验证代码 (MAC)。

{% hint style="warning" %}
**账户限制**的导出不能导入到其他账户。此外，[轮换您账户的加密密钥](../security/account-encryption-key.md)将导致已加密的导出无法解密。**如果您轮换了您的加密密钥，请使用新的加密密钥导出新文件以替换所有旧文件。**

如果您希望将加密的 `.json` 文件导入不同的 Bitwarden 账户，请在创建导出时选择**密码保护**的导出类型。
{% endhint %}

加密导出将包含所有密码库数据，包括登录、支付卡、安全笔记和身份。比如如下明文的登录项目：

```yaml
{
      ...
      "login": {
        "username": "mylogin",
        "password": "mypassword",
        "totp": "otpauth://totp/my-secret-key"
      },
      ...
```

加密导出后看起来会像这样：

```yaml
{
      ...
      "login": {
        "username": "9.dZwQ+b9Zasp98dnfp[g|dHZZ1p19783bn1KzkEsA=l52bcWB/w9unvCt2zE/kCwdpiubAOf104os}",
        "password": "1o8y3oqsp8n8986HmW7qA=oiCZo872b3dbp0nzT/Pw=|A2lgso87bfDBCys049ano278ebdmTe4:",
        "totp": "2CIUxtpo870B)*^GW2ta/xb0IYyepO(*&G(&BB84LZ5ByZxu0E9hTTs6PHg0=8q5DHEPU&bp9&*bns3EYgETXpiu9898sxO78l"
      },
      ...
```

## 创建加密导出 <a href="#create-an-encrypted-export" id="create-an-encrypted-export"></a>

创建加密导出遵循[普通的导出过程](export-vault-data.md)。当提示**文件格式**时，请选择 `.json (Encrypted)`：

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
导出组织密码库数据将被事件日志捕获。[了解更多](../admin-console/reporting/event-logs.md)。
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

更多详情，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。

{% hint style="info" %}
导出组织密码库数据将被事件日志捕获。[了解更多](../admin-console/reporting/event-logs.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

## 导入加密导出 <a href="#import-an-encrypted-export" id="import-an-encrypted-export"></a>

导入加密导出遵循[普通的导入过程](import-data-to-your-vault.md)。当提示**文件格式**时，请选择 `.json`：

{% hint style="success" %}
没有专门针对加密导出的导入选项。处理程序将确定 `.json` 文件已加密，并尝试使用您的[账户加密密钥](../security/account-encryption-key.md)解密该文件。
{% endhint %}

{% tabs %}
{% tab title="网页 App" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com)，[https://vault.bitwarden.eu](https://vault.bitwarden.eu,) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从导航栏选择**工具** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/7ed2e5650e9988bf7595bccebe8a5114/2024-12-03_08-52-08.png?_a=DAJCwlWIZAAB" %}
导入数据
{% endembed %}

3、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

4、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

5、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

6、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../your-vault/file-attachments.md)、[Send](../bitwarden-send/about-send.md)、回收站等附加项目需要手动上传到您的密码库。
{% endtab %}

{% tab title="浏览器扩展" %}
要导入数据到您的密码库：

1、在**设置**选项卡中，选择**密码库**然后选择**导入项目**选项。

2、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

3、选择**选择文件**然后添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件**将创建重复项目**。
{% endhint %}

4、选择**导入数据**按钮以开始导入。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

5、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="桌面 App" %}
要导入数据到您的密码库：

1、选择**文件** → **导入数据**。

2、从下拉菜单中完成以下字段：

* **密码库**：选择导入目的地，例如您的个人密码库或您拥有访问权限的组织密码库。
* **文件夹**或**集合**：选择您希望将导入的内容移动到的特定文件夹或您拥有访问权限的组织集合。
* [**文件格式**](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)：选择导入文件的格式。

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

`bw import` 命令需要一个格式（使用 `bw import --formats` 获取格式列表）和一个路径，例如：

```batch
bw import lastpasscsv /Users/myaccount/Documents/mydata.csv
```

成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}
{% endtabs %}

# 加密导出

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/encrypted-export/)
{% endhint %}

密码库数据可以[导出](export-vault-data.md)为加密的 `.json` 文件。加密的导出文件将包含来自您的组织或个人密码库的项目，但不包含 Send、密码历史记录、回收站或项目附件。可以使用网页密码库或 CLI 创建受密码保护的导出。Bitwarden 提供两种加密导出类型：

* **账户备份**：导出的加密文件，只能重新导入到生成加密导出文件的 Bitwarden 账户。此过程使用专用于 Bitwarden 帐户的[帐户加密密钥](../security/account-encryption-key.md)。
* **密码保护**：使用您选择的密码保护导出的加密文件。该文件使用您选择的密码解密，并且可以导入任何 Bitwarden 帐户。

{% hint style="warning" %}
**帐户备份**的导出不能导入到其他帐户。此外，[轮换您账户的加密密钥](../security/account-encryption-key.md)将导致已加密导出无法解密。**如果您轮换了您的加密密钥，请使用新的加密密钥导出新文件以替换所有旧文件。**

如果您希望将加密的 `.json` 文件导入不同的 Bitwarden 帐户，请在创建导出时选择**密码保护**的导出类型。
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

3、在导出密码库视图中，选择一个**文件格式**（`.json`、`.csv` 或 `.json (Encrypted)`）。

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

2、在导出密码库窗口中，选择一个**文件格式**（`.json`、`.csv` 或 `.json (Encrypted)`）。

{% hint style="success" %}
如果您需要将此数据导入新的 Bitwarden 帐户，我们建议使用网络密码库创建**密码保护**的导出。
{% endhint %}

3、输入您的**主密码**然后选择 **📥下载**按钮。
{% endtab %}

{% tab title="移动端" %}
要从移动应用程序导出您的个人密码库数据：

1、点击 ⚙️**设置**标签。

2、向下滚动到**工具**部分并点击**导出密码库**选项。

3、在导出密码库视图中，选择一个**文件格式**（`.json`、`.csv` 或 `.json (Encrypted)`）。

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

`--password` 选项可用于指定一个加密 `encrypted_json` 导出的密码，而不是您的[帐户加密密钥](../security/account-encryption-key.md)。

更多详情，请参阅我们的 [CLI 文档](../getting-started/bitwarden-cli.md)。
{% endtab %}
{% endtabs %}

## 导入加密导出 <a href="#import-an-encrypted-export" id="import-an-encrypted-export"></a>

导入加密导出遵循[普通的导入过程](import-data-to-your-vault.md)。当提示**文件格式**时，请选择 `.json`：

{% hint style="success" %}
没有专门针对加密导出的导入选项。处理程序将确定 `.json` 文件已加密，并尝试使用您的[帐户加密密钥](../security/account-encryption-key.md)解密该文件。
{% endhint %}

{% tabs %}
{% tab title="网页密码库" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从顶部导航条选择**工具**。

3、从工具菜单选择**导入数据**。

4、从格式下拉菜单，选择一个[文件格式](import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import) **** 。

5、选择**选择文件**按钮并添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中。如果多次导入文件或导入具有已存在于密码库中的项目的文件，**这将创建重复项目**。
{% endhint %}

6、选择**导入数据**以触发导入。如果您要导入受密码保护的 `.json` 文件，请在将出现的**确认密码库导出**窗口中输入密码。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../your-vault/file-attachments.md)、[Send](../bitwarden-send/about-send.md)、回收站和密码历史记录不包含在导入文件中。这些额外的项目需要手动上传到您的密码库。
{% endtab %}

{% tab title="CLI" %}
要通过 CLI 将数据导入您的密码库，请使用以下命令：

```shell
bw import <format> <path>
```

`bw import` 命令需要一个格式（使用 `bw import --formats` 获取格式列表）和一个路径，例如：

```shell
bw import lastpasscsv /Users/myaccount/Documents/mydata.csv
```

成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}
{% endtabs %}

# 导入 & 导出 Authenticator 数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/authenticator-import-export/)
{% endhint %}

您可以将验证码从支持的应用程序导入 Bitwarden Authenticator，从而使您能够快速迁移现有代码，而无需手动重新添加每一个验证码。您还可以随时导出代码以创建备份。

## 导入数据 <a href="#import-data" id="import-data"></a>

要将基于时间的一次性密码 (TOTP) 导入 Bitwarden Authenticator：

1. 点击 <i class="fa-gear-complex">:gear-complex:</i>**设置**图标。
2. 点击**导入**。
3. 从**文件格式**下拉菜单中，选择导入文件的来源：
   * **Authenticator 导出 (JSON)**：导入 Bitwarden Authenticator 或 Bitwarden Password Manager `.json` 的导出。使用下面章节中的说明，了解如何使用 Bitwarden Authenticator 创建 `.json` 导出的信息。导入 [Bitwarden Password Manager .json 的导出](../password-manager/import-and-export/export-vault-data.md)将解析文件并导入 TOTP 种子。
   * **Google Authenticator（二维码）**：从 Google Authenticator 中的**转移账户**界面，使用二维码从 Google Authenticator 导入。使用 Bitwarden Authenticator 扫描生成的二维码即可完成导入。
   * **LastPass (JSON)**：从 LastPass Authenticator **设置** → **转移账户**界面，以导入 LastPass Authenticator 账户的导出，。
   * **2FAS (.2fas)**：导入 2FAS 备份文件，该文件可以从 2FAS **设置** → **2FAS 备份**界面制作。只有不受密码保护的备份文件才能导入到 Bitwarden Authenticator。
   * **Raivo (JSON)（仅限 iOS）**：从 Raivo **设置**界面，使用**导出 OTP 到 ZIP 存档**选项进行导出，以导入 Raivo OTP 的导出。您需要使用您的主密码解密 `.zip` 文件，并将随附的 `raivo-otp-export.json` 文件导入 Bitwarden Authenticator。
   * **Aegis（仅 Android）**：从 Aegis **导入 & 导出**界面进行导出，以导入未加密的 Aegis .json 导出。

{% hint style="success" %}
在 Android 上，使用主界面上的 <i class="fa-plus">:plus:</i>**添加**图标扫描 Google Authenticator 二维码，而不是导航到**设置** → **导入**。
{% endhint %}

## 导出数据 <a href="#export-data" id="export-data"></a>

您可以导出 Bitwarden Authenticator App 中本地存储的数据。但是，从 Bitwarden 密码库同步的任何 TOTP 都需要单独[通过您的密码库导出](../password-manager/import-and-export/export-vault-data.md)，因为它们不包含在 Bitwarden Authenticator 的导出中。

要从 Bitwarden Authenticator 导出数据：

1. 打开 <i class="fa-gear-complex">:gear-complex:</i>**设置**选项卡。
2. 点击**导出**。
3. 从下拉菜单中选择您的导出的**文件格式**：`.json` 或 `.csv`。
4. 点击**导出项目**。

{% hint style="info" %}
导出的数据将包含每个条目的 `otpauth://totp/?secret=` 字符串。如果您希望将此数据存储在其他地方或设置第二个身份验证器 App，这就是您要保存的最重要的数据。
{% endhint %}

### 导出示例 <a href="#example-exports" id="example-exports"></a>

Bitwarden Authenticator 将以以下格式导出数据。如果您从当前不受支持的提供程序导入，您还可以参考此部分来调整您自己的导入文件：

{% tabs %}
{% tab title=".json" %}
```bash
{
  "encrypted": false,
  "items": [
    {
      "favorite": false,
      "id": "52A4DFB0-F19E-4C9D-82A1-BBEE95BBEF81",
      "login": {
        "totp": "otpauth://totp/Amazon:alice@bitwarden.com?secret=IIO5SCP3766LMSAB5HJCQPNDCCNAZ532&issuer=Amazon&algorithm=SHA1&digits=6&period=30",
        "username": "alice@bitwarden.com"
      },
      "name": "Amazon",
      "type": 1
    },
    {
      "favorite": false,
      "id": "DC81A830-ED98-4F45-9B73-B147E40134AB",
      "login": {
        "totp": "otpauth://totp/Apple:alice@bitwarden.com?secret=IIO5SCQ3766LMSBB5HJCQPNDCCNAZ532&issuer=Apple&algorithm=SHA1&digits=6&period=30",
        "username": "alice@bitwarden.com"
      },
      "name": "Apple",
      "type": 1
    },
    {
      "favorite": false,
      "id": "4EF44090-4B6A-4E98-A94C-CF7B0F2CC35D",
      "login": {
        "totp": "otpauth://totp/Bitwarden:alice@bitwarden.com?secret=IIO5SCP3766LMSBB5HJCQPNDCCNAZ532&issuer=Bitwarden&algorithm=SHA1&digits=6&period=30",
        "username": "alice@bitwarden.com"
      },
      "name": "Bitwarden",
      "type": 1
    },
    {
      "favorite": false,
      "id": "59B09168-502A-4D38-B218-FACF66E6A365",
      "login": {
        "totp": "otpauth://totp/Microsoft:alice@bitwarden.com?secret=IIO5SCP3766LMSBB5HJCHPNDCCNAZ532&issuer=Microsoft&algorithm=SHA1&digits=6&period=30",
        "username": "alice@bitwarden.com"
      },
      "name": "Microsoft",
      "type": 1
    },
    {
      "favorite": false,
      "id": "789F095B-95B2-4816-A5F7-01095116C10E",
      "login": {
        "totp": "otpauth://totp/Reddit:alice@bitwarden.com?secret=IIO5SCP3766LNSBB5HJCQPNDCCNAZ532&issuer=Reddit&algorithm=SHA1&digits=6&period=30",
        "username": "alice@bitwarden.com"
      },
      "name": "Reddit",
      "type": 1
    }
  ]
}
```
{% endtab %}

{% tab title=".csv" %}
```
folder,favorite,type,name,notes,fields,reprompt,login_uri,login_username,login_password,login_totp
,,login,Amazon,,,0,,alice@bitwarden.com,,otpauth://totp/Amazon:alice@bitwarden.com?secret=IIO5SCP3766LMSAB5HJCQPNDCCNAZ532&issuer=Amazon&algorithm=SHA1&digits=6&period=30
,,login,Apple,,,0,,alice@bitwarden.com,,otpauth://totp/Apple:alice@bitwarden.com?secret=IIO5SCQ3766LMSBB5HJCQPNDCCNAZ532&issuer=Apple&algorithm=SHA1&digits=6&period=30
,,login,Bitwarden,,,0,,alice@bitwarden.com,,otpauth://totp/Bitwarden:alice@bitwarden.com?secret=IIO5SCP3766LMSBB5HJCQPNDCCNAZ532&issuer=Bitwarden&algorithm=SHA1&digits=6&period=30
,,login,Microsoft,,,0,,alice@bitwarden.com,,otpauth://totp/Microsoft:alice@bitwarden.com?secret=IIO5SCP3766LMSBB5HJCHPNDCCNAZ532&issuer=Microsoft&algorithm=SHA1&digits=6&period=30
,,login,Reddit,,,0,,alice@bitwarden.com,,otpauth://totp/Reddit:alice@bitwarden.com?secret=IIO5SCP3766LNSBB5HJCQPNDCCNAZ532&issuer=Reddit&algorithm=SHA1&digits=6&period=30
```
{% endtab %}
{% endtabs %}

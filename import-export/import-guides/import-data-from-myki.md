# 从 Myki 导入数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/import-data-from-myki/)
{% endhint %}

使用这篇文章帮助您从 Myki 导出数据并将其导入 Bitwarden 中。Myki 数据支持导出为 `.csv` 文件。

## 从 Myki 导出 <a href="#export-from-myki" id="export-from-myki"></a>

根据您使用的平台，从 Myki 导出数据的过程会有所不同。我们建议尽可能从 Myki Web 应用程序导出，以获得最流畅的导入 Bitwarden 的体验。

有关从 Myki 导出的帮助，请参阅[这些 Myki 文章](https://support.myki.com/en/articles/6007957-how-to-export-my-myki-vault)。

### 调整您的 CSV <a href="#condition-your-csvs" id="condition-your-csvs"></a>

**如果您从 Myki 移动应用程序导出**，则需要调整您的 `.csv` 文件以导入 Bitwarden。主要包括重命名列标题，某些情况下，还需要对 `.csv` 中的列重新排序。

以下每个部分将首先记录 Myki 导出的格式，其次是 Bitwarden 要求的格式。

#### UserAccount.csv

导出的格式：

```
Nickname,Url,Username,Password,Additional Info,Two Factor Secret,Status
```

要求的格式：

```
nickname,url,username,password,additionalInfo,twofaSecret,status,tags
```

#### CreditCard.csv

导出的格式：

```
Nickname,Card Number,CardName,Exp Month,Exp Year,CVV,Additional Info,Status
```

要求的格式：

```
nickname,status,tags,cardNumber,cardName,exp_month,exp_year,cvv,additionalInfo
```

#### IdCard.csv

导出的格式：

```
Nickname,Id Type,Id Number,Id Name,Id Issuance Date,Id Expiration Date,Id Country,Additional Info,Status
```

要求的格式：

```
nickname,status,tags,idType,idNumber,idName,idIssuanceDate,idExpirationDate,idCountry,additionalInfo
```

#### Address.csv

导出的格式：

```
Nickname,First Name,Middle Name,Last Name,Email,First Address Line,Second Address Line,Title,Gender,Number,City,Country,Zip Code,Additional Info,Status
```

要求的格式：

```
nickname,status,tags,firstName,middleName,lastName,email,firstAddressLine,secondAddressLine,title,gender,number,city,country,zipCode,additionalInfo
```

#### Note.csv

导出的格式：

```
Title,Content,Status
```

要求的格式：

```
nickname,status,content
```

#### User2FA.csv

导出的格式：

```
Nickname,Additional Info,Two Factor Secret,Status
```

要求的格式：

```
nickname,status,tags,authToken,additionalInfo
```

## 导入 Bitwarden <a href="#import-to-bitwarden" id="import-to-bitwarden"></a>

**数据必须从网页密码库或 CLI 导入到 Bitwarden**。数据在发送到服务器存储之前会在本地进行[加密](../../security/encryption.md)。

{% tabs %}
{% tab title="网页密码库" %}
要导入数据到您的密码库：

1、通过 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或自托管的 `https://your.bitwarden.domain.com` 登录到网页密码库。

2、从顶部导航条选择**工具**。

3、从工具菜单选择**导入数据**。

4、从格式下拉菜单，选择一个[文件格式](../import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import) 。

5、选择**选择文件**按钮并添加一个文件用于导入，或将文件内容**复制/粘贴**到输入框中。

{% hint style="warning" %}
导入时不会检查要导入的文件中的项目是否已存在于您的密码库中，因此**多次导入文件或导入具有已存在于密码库中的项目的文件将创建重复项目**。
{% endhint %}

6、选择**导入数据**按钮以开始导入。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。

[文件附件](../../your-vault/file-attachments.md)需要手动上传到您的密码库。
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

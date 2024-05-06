# Bitwarden Authenticator

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-authenticator/)
{% endhint %}

Bitwarden Authenticator 是一款移动端的身份验证应用程序，可用于验证使用双因素身份验证 (2FA) 的网站和应用程序的身份。Bitwarden Authenticator 生成 5-10 位基于时间的一次性密码 (TOTP)，默认使用 SHA-1 并每 30 秒轮换一次。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4fMWMI0YBJQybhhyOlV0Zb/a9914cb08081d0dc424f2174dc3e62c7/bitwarden-authenticator-app.png?_a=BAJFJtWIB" %}
Bitwarden Authenticator
{% endembed %}

## 添加代码 <a href="#add-codes" id="add-codes"></a>

在您尝试为其设置 2FA 的网站或应用程序中，导航至其 2FA 界面，然后**扫描二维码**或**手动添加代码**：

{% tabs %}
{% tab title="扫描二维码" %}
1. 点击 ✚图标。
2. 将相机对准二维码。扫描将自动进行。
{% endtab %}

{% tab title="手动添加代码" %}
1. 点击 ✚图标。
2. 点击屏幕底部的**手动输入密钥**。
3. 在**名称**字段中输入网站或应用程序的名称。
4. 输入网站或应用程序提供的**验证器密钥**。某些服务将此称为「机密密钥」或「TOTP 种子」。
{% endtab %}
{% endtabs %}

### 编辑项目 <a href="#edit-an-item" id="edit-an-item"></a>

长按验**证码**界面上的条目可对其进行更改。除了更改已添加的名称和机密之外，您还可以：

* 将**用户名**添加到项目中。当您在同一网站拥有多个账户并且每个账户需要单独的验证码时，请使用此字段。
* 更改用于生成代码的**算法**。Bitwarden Authenticator 默认使用 SHA-1。
* 更改代码的**刷新周期**。Bitwarden Authenticator 默认使用 30 秒。
* 更改代码的**位数**。Bitwarden Authenticator 默认使用 6 位数字。

{% hint style="info" %}
**算法**、**刷新周期**和**位数**由您使用验证码的网站决定。除非该网站要求或允许您自定义验证码行为，否则请勿更改项目的这些设置。
{% endhint %}

## 使用代码 <a href="#use-codes" id="use-codes"></a>

要在该账户的机密存储在 Bitwarden Authenticator 中后使用验证码，请打开 Bitwarden Authenticator 并点击该条目将其验证码复制到剪贴板。然后，将验证码粘贴到您要登录的网站或应用程序的输入框中。

## 导出数据 <a href="#export-data" id="export-data"></a>

要从 Bitwarden Authenticator 导出数据，请打开 **⚙️设置**选项卡，然后点击**导出**按钮。您可以选择将数据导出为 `.json` 或 `.csv` 文件。

{% hint style="info" %}
导出的数据将包含每个条目的 `otpauth://totp/?secret=` 字符串。如果您希望将此数据存储在其他地方或设置第二个身份验证器应用程序，这些是要保存的最重要的数据。
{% endhint %}

## 常见问题 <a href="#faqs" id="faqs"></a>

**问：新的 Bitwarden Authenticator 是 Bitwarden 密码管理器的一部分吗？**

**答：**Bitwarden Authenticator 是一款独立的应用程序，可供所有人使用，甚至是非 Bitwarden 客户。 Bitwarden Password Manager 将保留一个集成的身份验证器，供高级用户或付费组织成员使用。

**问：我可以使用 Bitwarden Authenticator 将 2FA 添加到我的 Bitwarden 账户吗？**

**答：**可以！由于 Bitwarden Authenticator 允许您在 Bitwarden 账户之外存储代码，因此该应用程序可用于将 2FA 添加到您的 Bitwarden 账户。

**问：如何将此应用设置为 iOS 上的默认验证码应用？**

**答：**运行 iOS 16+ 的 iOS 用户可以将任何应用程序设置为直接从相机应用程序扫码时默认存储验证码的应用程序，包括 [Bitwarden Authenticator](bitwarden-authenticator.md) 和 Password Manager [集成身份验证](../your-vault/totp.md)。要进行此设置：

1. 打开设备上的 iOS **设置**应用程序。
2. 点击**密码**。
3. 点击**密码选项**。
4. 从**验证码**部分的**设置验证码**下拉列表中选择一个应用程序。

**问：我什么时候应该使用这个独立的应用程序而不是集成的身份验证器？**

**答：**除了使用独立应用程序为您的 Bitwarden 账户设置 2FA 之外，您还可以使用任一应用程序为所有其他账户存储和生成验证码。它们可以一起使用，也可以单独使用，具体取决于您的安全偏好。

**问：我的数据如何存储和保护？**

**答：**您的身份验证密钥（有时称为「机密密钥」或「TOTP 种子」）和所有关联的元数据都存储在您设备上的本地数据库中。此数据未同步到 Bitwarden 服务器。加密数据的备份由您设备的云备份系统（例如 iCloud 或 Google One）进行备份。为了保护应用程序中的数据，您还可以设置生物识别登录。

**问：如何备份和恢复数据？**

**答：**您的加密数据的备份是由您设备的云备份系统（例如 iCloud 或 Google One）进行的。要恢复数据，请恢复设备的云备份。

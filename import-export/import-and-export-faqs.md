# 导入 & 导出 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-faqs/)
{% endhint %}

本文包含有关导入和导出的常见问题 (FAQ)。

### 问：如果在导入选项列表中没有看到我的服务，如何导入我的数据？ <a href="#q-how-do-i-import-my-data-if-i-dont-see-my-service-on-the-import-options-list" id="q-how-do-i-import-my-data-if-i-dont-see-my-service-on-the-import-options-list"></a>

**答：**&#x5982;果我们对您使用的服务没有提供官方支持，请手动调整 `.csv` 或 `.json` 来导入 Bitwarden。关于如何操作的更多信息，请参阅[调整 Bitwarden .csv 或 .json](condition-a-bitwarden-.csv-or-.json.md)。

### 问：我可以从 iCloud/Mac 钥匙串/Safari 导入 Bitwarden 吗？ <a href="#q-can-i-import-to-bitwarden-from-icloud-mac-keychain-safari" id="q-can-i-import-to-bitwarden-from-icloud-mac-keychain-safari"></a>

**答：**&#x4ECE; Safari 15.0 开始，您可以从 Safari 导出密码到 `.csv` 文件。完成后，[调整您的 .csv](condition-a-bitwarden-.csv-or-.json.md) 以符合 Bitwarden 的格式然后[导入您的数据](../password-manager/import-and-export/import-data.md)。

Safari 15.0 之前，苹果还没有提供一个官方的从 iCloud、Mac 钥匙串或 Safari 导出数据的方法。

这里有一些第三方程序可以导出这些数据：

* [https://gist.github.com/rmondello/b933231b1fcc83a7db0b](https://gist.github.com/rmondello/b933231b1fcc83a7db0b)
* [https://github.com/lifepillar/CSVKeychain](https://github.com/lifepillar/CSVKeychain)

{% hint style="danger" %}
**请注意：**&#x8FD9;些第三方脚本/程序不受 Bitwarden 和 Apple 的支持，请自行承担使用风险。
{% endhint %}

### 问：如何将项目直接导入到集合中？ <a href="#q-how-can-i-import-items-directly-to-collections" id="q-how-can-i-import-items-directly-to-collections"></a>

**答：**&#x60A8;可以在导入前通过适当调整 `.json` 文件将项目导入现有的集合，也可以在导入文件中定义新的集合，以便在上传文件时创建新的集合。[了解方法](condition-a-bitwarden-.csv-or-.json.md)。

### 问：如何将文件附件导入 Bitwarden？ <a href="#q-how-do-i-import-file-attachments-to-bitwarden" id="q-how-do-i-import-file-attachments-to-bitwarden"></a>

**答：**&#x6587;件附件必须手动迁移到您的 Bitwarden 密码库，因为它们目前不包含在批量导入操作中。

请注意，文件附件的存储只适用于高级用户，包括付费组织的成员（家庭、团队或企业）。

### 问：为什么导入时会产生重复的密码库项目？ <a href="#q-why-did-importing-create-duplicate-vault-items" id="q-why-did-importing-create-duplicate-vault-items"></a>

**答：**&#x65E0;论您的密码库中是否已经存在匹配的项目，每次导入操作都会在您的密码库中作为一个项目创建新的记录。在导入之前，我们建议执行以下操作之一：

* 编辑您的导入文件，使只包含全新的密码库项目。
* 在导入操作前清空您的密码库。

个人密码库可以从**设置** → **我的账户**页面清空。组织密码库可以从组织**设置** → **组织信息**页面清空。

### 问：Bitwarden 支持导入哪些文件格式？ <a href="#q-what-file-formats-does-bitwarden-support-for-import" id="q-what-file-formats-does-bitwarden-support-for-import"></a>

**答：**&#x4EE5;下格式支持开箱即用：

> **\[译者注]**：out-of-the-box，开箱即用。「out-of-the-box」 是一个常用短语，表示「无需额外配置或修改即可直接使用」。在这里，表示以下格式可以直接在 Bitwarden 中导入，而无需额外手动[调整 Bitwarden .csv 或 .json](condition-a-bitwarden-.csv-or-.json.md)。

{% hint style="info" %}
如果您的格式没有在下面列出，请手动[调整 Bitwarden .csv 或 .json](condition-a-bitwarden-.csv-or-.json.md)。
{% endhint %}

* [1Password (1pif)](../password-manager/import-and-export/import-guides/import-data-from-1password.md)
* [1Password 6 & 7 Windows (.sv)](../password-manager/import-and-export/import-guides/import-data-from-1password.md)
* [1Password 6 & 7 Mac (csv)](../password-manager/import-and-export/import-guides/import-data-from-1password.md)
* Ascendo DataVault (csv)
* Avast Passwords (csv)
* Avast Passwords (json)
* Avira (json)
* BlackBerry Password Keeper (csv)
* Blur (csv)
* [Brave (csv)](../password-manager/import-and-export/import-guides/import-data-from-chrome.md)（请选择 **Chrome**）
* Buttercup (csv)
* [Chrome (csv)](../password-manager/import-and-export/import-guides/import-data-from-chrome.md)
* Clipperz (html)
* Codebook (csv)
* Dashlane (json)
* Encryptr (csv)
* Enpass (csv)
* Enpass (json)
* [Firefox (csv)](../password-manager/import-and-export/import-guides/import-data-from-firefox.md)
* F-Secure KEY (fsk)
* GNOME Passwords and Keys/Seahorse (json)
* Kaspersky Password Manager (txt)
* KeePass 2 (xml)
* KeePassX (csv)
* Keeper (csv)
* [LastPass (csv)](../password-manager/import-and-export/import-guides/import-data-from-lastpass.md)
* LogMeOnce (csv)
* Meldium (csv)
* mSecure (csv)
* Myki (csv)
* [Microsoft Edge (csv)](../password-manager/import-and-export/import-guides/import-data-from-chrome.md)（请选择 **Chrome**）
* Nordpass (csv)
* Netwrix Password Secure (csv)
* [Opera (csv)](../password-manager/import-and-export/import-guides/import-data-from-chrome.md)（请选择 **Chrome**）
* Padlock (csv)
* Passbolt (csv)
* PassKeep (csv)
* Passky (json)
* Passman (json)
* Passpack (csv)
* Password Agent (csv)
* Password Boss (json)
* Password Dragon (xml)
* Password Depot 17 (xml)
* Password Safe (xml)
* PasswordWallet (txt)
* ProtonPass (json)
* Psono (json)
* RememBear (csv)
* RoboForm (csv)
* SafeInCloud (xml)
* SaferPass (csv)
* SecureSafe (csv)
* SplashID (csv)
* Sticky Password (xml)
* True Key (csv)
* Universal Password Manager (csv)
* [Vivaldi (csv)](../password-manager/import-and-export/import-guides/import-data-from-chrome.md)
* Yoti (csv)
* Zoho Vault (csv)

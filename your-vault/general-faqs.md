# 一般常见问题

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/product-faqs/)
{% endhint %}

本文包含有关一般的密码库管理和 Bitwarden 功能的常见问题（FAQ）。

## 最常问的问题 <a href="#most-asked-questions" id="most-asked-questions"></a>

### 问：我忘记了主密码，该怎么办？ <a href="#q-i-have-forgotten-my-master-password-what-can-i-do" id="q-i-have-forgotten-my-master-password-what-can-i-do"></a>

**答：**作为一个零知识解决方案，Bitwarden 及其系统对您的主密码不了解，没有办法找回，也没有办法重置您的主密码。如果您已经丢失了您的主密码，很遗憾，团队没有办法恢复账户。想了解下一步该怎么做，或者如何主动保护自己，避免出现这种情况，请参考[您的主密码](your-master-password.md)这篇文章。

### 问：在紧急情况下，是否有办法让别人访问我的密码库项目？ <a href="#q-is-there-a-way-for-someone-to-access-my-vault-items-in-case-of-emergency" id="q-is-there-a-way-for-someone-to-access-my-vault-items-in-case-of-emergency"></a>

**答：**有！拥有高级订阅的用户可以主动设置受信任的紧急联系人，以便在紧急情况下访问您的密码库。如需了解更多信息，请参阅[紧急访问](../security/emergency-access.md)。

### 问：如何更改我的主密码提示？ <a href="#q-how-do-i-change-my-master-password-hint" id="q-how-do-i-change-my-master-password-hint"></a>

**答：**要更改您的主密码提示：

1. 打开[网页密码库](https://vault.bitwarden.com/)，从顶部导航栏中选择**设置**。
2. 在**我的帐户**页面，找到**主密码提示**的输入框。
3. 输入提示并选择**保存**按钮。

### 问：如何更改电子邮件地址？ <a href="#q-how-do-i-change-my-email-address" id="q-how-do-i-change-my-email-address"></a>

{% hint style="info" %}
如果您使用[电子邮件方式的两步登录](../two-step-login/setup-guides/two-step-login-via-email.md)，则更改您的帐户电子邮件地址不会更改用于接收 2FA 代码的地址。
{% endhint %}

**答：**要更改帐户所附属的电子邮件地址：

1. 打开[网页密码库](https://vault.bitwarden.com)，从顶部导航栏选择**设置**
2. 在**我的账户**页面，找到**更改电子邮件**部分
3. 输入您当前的**主密码**，以证明您有权进行此操作，并指定您想更改为的**新电子邮件**
4. 选择**更改电子邮件**按钮\
   Bitwarden 将通过电子邮件发送一个验证码到指定的电子邮件地址。检查您的收件箱中的代码，并将其输入到您的网页密码库中显示的**代码**文本输入框中，以完成更改。如果您没有收到 验证码，请检查您的垃圾邮件文件夹。您也可以将 `no-reply@bitwarden.com` 加入白名单，以确保今后的交付。

{% hint style="success" %}
**如果您有付费订阅**，也请[联系我们](https://bitwarden.com/contact)告知我们有关更改的信息，以便我们更改您的计费信息。
{% endhint %}

更改了电子邮件地址后，你应该立即注销你使用的所有 Bitwarden 客户端应用程序，然后使用新的凭证重新登录。使用“陈旧”的电子邮件地址的会话最终将被注销。

### 问：为什么我的移动应用程序、桌面应用程序或浏览器扩展程序中丢失了密码库项目？ <a href="#q-why-is-a-vault-item-missing-from-my-mobile-app-desktop-app-or-browser-extension" id="q-why-is-a-vault-item-missing-from-my-mobile-app-desktop-app-or-browser-extension"></a>

**答：**通常，这是因为客户端应用程序的密码库数据已经落后于网页密码库或其他客户端应用程序的数据。执行密码库同步应该可以使所有数据为最新。有关更多信息，请参阅[同步您的密码库](syncing-your-vault.md)。

### 问：有啥安全的方式备份我的密码库数据？ <a href="#q-whats-the-safest-way-to-make-a-backup-of-my-vault-data" id="q-whats-the-safest-way-to-make-a-backup-of-my-vault-data"></a>

**答：**您可以使用[加密导出](../import-export/encrypted-exports.md)（将使用您的[账户加密密钥](../security/account-encryption-key.md)进行加密）对您的密码库数据进行安全的长期备份。

另外，您也可以在从 Bitwarden 导出纯文本文件后，使用诸如 PeaZip 来创建文件的加密存档。

您可以在这里了解更多关于 PeaZip 的信息：

* [http://www.peazip.org/](http://www.peazip.org/)
* [https://github.com/giorgiotani/PeaZip](https://github.com/giorgiotani/PeaZip)

{% hint style="warning" %}
**免责声明：**PeaZip 是第三方程序，不受 Bitwarden 支持。这些链接是作为替代方案与您分享的，使用时风险自担。
{% endhint %}

### 问：如何设置当计算机启动时自动启动 Bitwarden？ <a href="#q-can-i-set-bitwarden-to-automatically-start-when-my-computer-starts" id="q-can-i-set-bitwarden-to-automatically-start-when-my-computer-starts"></a>

**答：**你可以将 Bitwarden 桌面应用程序设置为启动时打开：

1. 点击**开始**（Windows 徽标）按钮，选择所有应用程序，然后滚动并找到 Bitwarden 桌面应用程序/快捷方式。
2. 右键单击 Bitwarden 桌面应用程序，选择**更多**，然后选择**打开文件位置**。
3. 文件位置打开后，按 Windows 徽标键 + R 键，键入 `shell:startup`，然后点击**确定**。这将打开启动文件夹。
4. 将 Bitwarden 桌面应用程序的快捷方式从文件位置复制并粘贴到到启动文件夹中。

### 问：为什么会收到「新的设备」电子邮件消息？ <a href="#q-why-am-i-getting-a-new-device-email-message" id="q-why-am-i-getting-a-new-device-email-message"></a>

**答：**通常情况下，是因为用户在浏览器上设置了每当他们关闭或使用浏览器时，将清除他们的本地存储和/或缓存。某些扩展程序也可以执行这些操作。如果发生这种情况，你就会失去告诉我们的服务器这是一个现有设备的指示器。新设备通知信息不取决于 IP 地址，只取决于设备本身。我们使用浏览器或客户端中的本地存储为设备贴上一个 id 标签。如果这个 id 之前从未登录过，那么你会收到一封邮件。如果用户清除了本地存储，将会为该设备生成一个新的 id，并且会收到一封新的邮件。

你可能需要为 Bitwarden 做一个例外，或者为 Bitwarden 配置你的白名单来防止缓存或本地存储被清除。如果你的浏览器设置为永远记录历史记录，也可能会发生这种情况。

## 其他问题 <a href="#other-questions" id="other-questions"></a>

### 问：可以在没有 Google Play 的情况下安装 Bitwarden 吗，例如通过 F-Droid？ <a href="#can-i-install-bitwarden-without-google-play-for-instance-on-f-droid" id="can-i-install-bitwarden-without-google-play-for-instance-on-f-droid"></a>

**答：**可以！您可以直接从GitHub [https://github.com/bitwarden/mobile/releases](https://github.com/bitwarden/mobile/releases)下载，也可以添加我们的仓库 [https://mobileapp.bitwarden.com/fdroid/](https://mobileapp.bitwarden.com/fdroid/) 后通过 F-Droid 下载，这删除了所有未经批准的库。

不幸的是，F-Droid 无法从源代码编译我们的应用程序，因为它基于 Xamarin，而 F-Droid 当前的编译器方法不支持 Xamarin，因此我们必须使用单独的仓库。

### 问：可以关闭 Bitwarden 的自动更新吗？ <a href="#q-can-i-turn-off-automatic-updates-for-bitwarden" id="q-can-i-turn-off-automatic-updates-for-bitwarden"></a>

**答：**可以！在 Windows 上，您可以将环境变量 `ELECTRON_NO_UPDATER=1` 添加到您的桌面应用程序模板中，以使自动更新进程在您的终端用户工作站上失效和阻止尝试。[了解如何为桌面应用程序设置环境变量](https://www.twilio.com/blog/2017/01/how-to-set-environment-variables.html)。

{% hint style="danger" %}
与任何软件一样，运行旧版本可能会带来安全风险。
{% endhint %}

### 问：需要旧密码！可以查看我在 Bitwarden 中更改过的密码的历史记录吗？ <a href="#q-i-need-an-old-password-can-i-view-the-history-of-a-password-that-i-changed-in-bitwarden" id="q-i-need-an-old-password-can-i-view-the-history-of-a-password-that-i-changed-in-bitwarden"></a>

**答：**可以。你可以查看登录项目的最近 5 个密码的历史记录。打开该项目，并点击窗口底部密码历史记录旁边的数字，例如「1」。（备注：数字代表密码历史记录数）

{% hint style="danger" %}
点击数字将立即以纯文本的方式展示历史密码值。
{% endhint %}

### 问：忘记保存生成的密码！可以查看已生成的密码的历史记录吗？ <a href="#q-i-forgot-to-save-a-generated-password-can-i-view-the-history-of-generated-passwords" id="q-i-forgot-to-save-a-generated-password-can-i-view-the-history-of-generated-passwords"></a>

**答：**可以。您可以查看密码生成器的历史记录，**但请注意**，每个应用程序/客户端的此历史记录是独立的。此信息在设备之间不会同步。

### 问：当我清空我的密码库时会发生什么？ <a href="#what-happens-when-i-purge-my-vault" id="what-happens-when-i-purge-my-vault"></a>

**答：**清空**个人密码库**时，所有密码库项目和文件夹都将被删除。当您清空**组织密码库**时，所有已共享（即归组织所有）的密码库项目都将被删除，但现有的用户、集合和群组将保留在原来的位置。

### 问：可以打印密码库数据吗？ <a href="#q-can-i-print-my-vault-data" id="q-can-i-print-my-vault-data"></a>

**答：**无法直接从 Bitwarden 打印，但是您可以将密码库数据导出为 `.csv` 或 `.json` 文件然后从文本编辑器中打印。

# Password Manager 常见问题

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/product-faqs/)
{% endhint %}

本文包含有关一般的密码库管理和 Bitwarden 功能的常见问题 (FAQ)。

## 最常问的问题 <a href="#most-asked-questions" id="most-asked-questions"></a>

### 问：如果我忘记了主密码应该该怎么办？ <a href="#q-what-do-i-do-if-i-forgot-my-master-password" id="q-what-do-i-do-if-i-forgot-my-master-password"></a>

**答：**&#x4F5C;为一个零知识解决方案，Bitwarden 及其系统对您的主密码不了解，没有办法找回，也没有办法重置您的主密码。如果您已经丢失了您的主密码，很遗憾，团队没有办法恢复账户。想了解下一步该怎么做，或者如何主动保护自己，避免出现这种情况，请参考[您的主密码](your-master-password.md)这篇文章。

### 问：在紧急情况下，是否有办法让别人访问我的密码库项目？ <a href="#q-is-there-a-way-for-someone-to-access-my-vault-items-in-case-of-emergency" id="q-is-there-a-way-for-someone-to-access-my-vault-items-in-case-of-emergency"></a>

**答：**&#x6709;！拥有高级订阅的用户可以主动设置受信任的紧急联系人，以便在紧急情况下访问您的密码库。如需了解更多信息，请参阅[紧急访问](../security/emergency-access.md)。

### 问：如何更改我的主密码提示？ <a href="#q-how-do-i-change-my-master-password-hint" id="q-how-do-i-change-my-master-password-hint"></a>

**答：**&#x8981;更改您的主密码提示：

1. 打开[网页密码库](https://vault.bitwarden.com/)，选择配置文件图标，然后从下拉列表中选择**账户设置**。
2. 从账户设置菜单中，选择**安全**页面然后**主密码**选项卡。
3. &#x8981;_&#x4EC5;_&#x66F4;改您的提示，请在**当前主密码**、**新主密码**和**确认主密码**框中全部输入您当前的主密码以防止更改，然后在**主密码提示**框中输入提示。
4. 选择**更改主密码**按钮。

### 问：如何更改电子邮件地址？ <a href="#q-how-do-i-change-my-email-address" id="q-how-do-i-change-my-email-address"></a>

{% hint style="info" %}
如果您使用[电子邮件方式的两步登录](../two-step-login/setup-guides/two-step-login-via-email.md)，则更改您的账户电子邮件地址不会更改用于接收 2FA 代码的地址。
{% endhint %}

**答：**&#x8981;更改账户所附属的电子邮件地址：

1. 打开[网页密码库](https://vault.bitwarden.com)，选择配置文件图标，然后从下拉列表中选择**账户设置**。
2. 在**我的账户**页面，找到**更改电子邮件**部分。
3. 输入您当前的**主密码**，以证明您有权进行此操作，并指定您想更改为的**新电子邮件**。
4. 选择**继续**按钮。\
   Bitwarden 将通过电子邮件发送一个验证码到指定的电子邮件地址。检查您的收件箱中的代码，并将其输入到您的网页密码库中显示的**代码**文本输入框中，以完成更改。如果您没有收到验证码，请检查您的垃圾邮件文件夹。您也可以将 `no-reply@bitwarden.com` 加入白名单，以确保今后的交付。

更改了电子邮件地址后，你应该立即注销你使用的所有 Bitwarden 客户端应用程序，然后使用新的凭证重新登录。使用“陈旧”的电子邮件地址的会话最终将被注销。

### 问：验证邮箱后会解锁哪些功能？ <a href="#q-what-features-are-unlocked-when-i-verify-my-email" id="q-what-features-are-unlocked-when-i-verify-my-email"></a>

**答：**&#x5F53;验证您的电子邮件地址后，将解锁[创建文件 Send](../bitwarden-send/create-a-send.md)（前提是您具有高级功能权限）。

### 问：为什么我的移动应用程序、桌面应用程序或浏览器扩展程序中丢失了密码库项目？ <a href="#q-why-is-a-vault-item-missing-from-my-mobile-app-desktop-app-or-browser-extension" id="q-why-is-a-vault-item-missing-from-my-mobile-app-desktop-app-or-browser-extension"></a>

**答：**&#x901A;常，这是因为客户端应用程序的密码库数据已经落后于网页密码库或其他客户端应用程序的数据。执行密码库同步应该可以使所有数据为最新。有关更多信息，请参阅[同步您的密码库](syncing-your-vault.md)。

### 问：有啥安全的方式备份我的密码库数据？ <a href="#q-whats-the-safest-way-to-make-a-backup-of-my-vault-data" id="q-whats-the-safest-way-to-make-a-backup-of-my-vault-data"></a>

**答：**&#x60A8;可以使用[加密导出](../import-export/encrypted-exports.md)（将使用您的[账户加密密钥](../security/account-encryption-key.md)进行加密）对您的密码库数据进行安全的长期备份。

另外，您也可以在从 Bitwarden 导出纯文本文件后，使用诸如 PeaZip 来创建文件的加密存档。

您可以在这里了解更多关于 PeaZip 的信息：

* [http://www.peazip.org/](http://www.peazip.org/)
* [https://github.com/giorgiotani/PeaZip](https://github.com/giorgiotani/PeaZip)

{% hint style="warning" %}
**免责声明：**&#x50;eaZip 是第三方程序，不受 Bitwarden 支持。这些链接是作为替代方案与您分享的，使用时风险自担。
{% endhint %}

### 问：如何设置当计算机启动时自动启动 Bitwarden？ <a href="#q-can-i-set-bitwarden-to-automatically-start-when-my-computer-starts" id="q-can-i-set-bitwarden-to-automatically-start-when-my-computer-starts"></a>

**答：**&#x4F60;可以将 Bitwarden 桌面应用程序设置为启动时打开：

1. 点击**开始**（Windows 徽标）按钮，选择所有应用程序，然后滚动并找到 Bitwarden 桌面应用程序/快捷方式。
2. 右键单击 Bitwarden 桌面应用程序，选择**更多**，然后选择**打开文件位置**。
3. 文件位置打开后，按 **Windows 徽标键** + **R** 键，键入 `shell:startup`，然后点击**确定**。这将打开启动文件夹。
4. 将 Bitwarden 桌面应用程序的快捷方式从文件位置复制并粘贴到到启动文件夹中。

### 问：为什么会收到「新的设备」电子邮件消息？ <a href="#q-why-am-i-getting-a-new-device-email-message" id="q-why-am-i-getting-a-new-device-email-message"></a>

**答：**&#x901A;常情况下，是因为用户在浏览器上设置了每当他们关闭或使用浏览器时，将清除他们的本地存储和/或缓存。某些扩展程序也可以执行这些操作。如果发生这种情况，你就会失去告诉我们的服务器这是一个现有设备的指示器。新设备通知信息不取决于 IP 地址，只取决于设备本身。我们使用浏览器或客户端中的本地存储为设备贴上一个 id 标签。如果这个 id 之前从未登录过，那么你会收到一封邮件。如果用户清除了本地存储，将会为该设备生成一个新的 id，并且会收到一封新的邮件。

你可能需要为 Bitwarden 做一个例外，或者为 Bitwarden 配置你的白名单来防止缓存或本地存储被清除。如果你的浏览器设置为永远记录历史记录，也可能会发生这种情况。

## 其他问题 <a href="#other-questions" id="other-questions"></a>

### 问：可以在没有 Google Play 的情况下安装 Bitwarden 吗，例如通过 F-Droid？ <a href="#can-i-install-bitwarden-without-google-play-for-instance-on-f-droid" id="can-i-install-bitwarden-without-google-play-for-instance-on-f-droid"></a>

**答：**&#x53EF;以！您可以直接从GitHub [https://github.com/bitwarden/mobile/releases](https://github.com/bitwarden/mobile/releases)下载，也可以添加我们的仓库 [https://mobileapp.bitwarden.com/fdroid/](https://mobileapp.bitwarden.com/fdroid/) 后通过 F-Droid 下载，这删除了所有未经批准的库。

不幸的是，F-Droid 无法从源代码编译我们的应用程序，因为它基于 Xamarin，而 F-Droid 当前的编译器方法不支持 Xamarin，因此我们必须使用单独的仓库。

### 问：可以关闭 Bitwarden 的自动更新吗？ <a href="#q-can-i-turn-off-automatic-updates-for-bitwarden" id="q-can-i-turn-off-automatic-updates-for-bitwarden"></a>

**答：**&#x53EF;以！在 Windows 上，您可以将环境变量 `ELECTRON_NO_UPDATER=1` 添加到您的桌面应用程序模板中，以使自动更新进程在您的终端用户工作站上失效和阻止尝试。[了解如何为桌面应用程序设置环境变量](https://www.twilio.com/blog/2017/01/how-to-set-environment-variables.html)。

{% hint style="danger" %}
与任何软件一样，运行旧版本可能会带来安全风险。
{% endhint %}

### 问：我需要旧密码！可以查看我在 Bitwarden 中更改过的密码的历史记录吗？ <a href="#q-i-need-an-old-password-can-i-view-the-history-of-a-password-that-i-changed-in-bitwarden" id="q-i-need-an-old-password-can-i-view-the-history-of-a-password-that-i-changed-in-bitwarden"></a>

**答：**&#x53EF;以。你可以查看登录项目的最近 5 个密码的历史记录。打开该项目，并点击窗口底部**密码历史记录**旁边的数字，例如「1」。（备注：数字代表密码历史记录数）

{% embed url="https://bitwarden.com/_gatsby/image/0bb681832d149c6061897a987182029b/557d3f27253653e121d356eb9a00ff16/Screen%20Shot%202023-01-10%20at%2010.06.42%20AM.webp?eu=d68d55b0b6c0fc8f096ea8803a243661e73c52fafd5031843b6ce6fd4ffb9cd523f01807249728b12d3a58da86e110b362972b3748e8d38b92ea4af1ee33fe0959db1eaa27f07a184e7299afe7a0455b3b824c09e2c09d4ce0732c81a1acb03247035a71a92cb0dcabae2a60b4eb2831aac2d35138a1fc3ee56f2c179c7b389c7bb3c4886518bb9cb016bde7ebad0b989db17c551389fa6426264a1659e82eb2a1ad67227b7c15055aadf707830e94b63e1f7c235f4202f7086b943afa6c2fc3e2e5a55fb60b06ffe89766&a=w%3D850%26h%3D273%26fm%3Dwebp%26q%3D75&cd=2023-01-10T15%3A07%3A35.833Z" %}
查看密码历史记录
{% endembed %}

{% hint style="danger" %}
点击数字将立即以纯文本的方式展示历史密码值。
{% endhint %}

### 问：忘记了保存已生成的密码！可以查看已生成的密码的历史记录吗？ <a href="#q-i-forgot-to-save-a-generated-password-can-i-view-the-history-of-generated-passwords" id="q-i-forgot-to-save-a-generated-password-can-i-view-the-history-of-generated-passwords"></a>

**答：**&#x53EF;以。您可以查看密码生成器的历史记录，但请注意，每个应用程序/客户端的此历史记录是独立的。此信息在设备之间不会同步。

### 问：当我清空我的密码库时会发生什么？ <a href="#what-happens-when-i-purge-my-vault" id="what-happens-when-i-purge-my-vault"></a>

**答：**&#x6E05;空**个人密码库**时，所有密码库项目和文件夹都将被删除。当您清空**组织密码库**时，所有已共享（即归组织所有）的密码库项目都将被删除，但现有的用户、集合和群组将保留在原来的位置。

### 问：可以打印密码库数据吗？ <a href="#q-can-i-print-my-vault-data" id="q-can-i-print-my-vault-data"></a>

**答：**&#x65E0;法直接从 Bitwarden 打印，但是您可以[将密码库数据导出](../import-export/export-vault-data.md)为 `.csv` 或 `.json` 文件然后从文本编辑器中打印。

### 问：Windows 剪贴板是否会存储已复制的密码？ <a href="#q-does-windows-clipboard-store-copied-passwords" id="q-does-windows-clipboard-store-copied-passwords"></a>

**答：**&#x57;indows 剪贴板将保存以前复制的项目的列表。可以通过访问**设置**和**剪贴板**来设置 Windows 剪贴板设置。

{% hint style="danger" %}
可以在**剪贴板**设置菜单中打开/关闭 Windows 剪贴板历史记录。但是，这不会删除剪贴板中的现有项目。要清除已复制的密码，请选择**清除剪贴板数据**选项下的**清除**。
{% endhint %}

### 问：卸载或删除我的 Bitwarden 应用程序是否也会删除我的密码库数据吗？ <a href="#q-does-uninstalling-or-deleting-my-bitwarden-app-also-delete-my-vault-data" id="q-does-uninstalling-or-deleting-my-bitwarden-app-also-delete-my-vault-data"></a>

**答：**&#x4E0D;会，删除 Bitwarden 应用程序/扩展程序并不会删除您的密码库数据。密码库数据加密保存在服务器上。如果您希望**永久**删除您的密码库数据，请参阅[删除账户或组织](../plans-and-pricing/delete-an-account-or-organization.md)。

### 问：Bitwarden 是否管理 Android 手机上的 Firefox 浏览器扩展？ <a href="#q-does-bitwarden-manage-the-firefox-browser-extension-on-android-mobile" id="q-does-bitwarden-manage-the-firefox-browser-extension-on-android-mobile"></a>

**答：**&#x41;ndroid 移动设备上有适用于 Firefox 的 Bitwarden 浏览器扩展。但是，此扩展并未得到 Bitwarden 的正式支持，并且团队意识到此客户端中的某些功能无法正常工作。Android 用户可能更喜欢使用 Bitwarden [移动应用程序](../getting-started/getting-started-mobile.md)作为官方支持的密码管理器客户端。

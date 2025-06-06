# Password Manager FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/product-faqs/)
{% endhint %}

本文包含有关一般的密码库管理和 Bitwarden 功能的常见问题 (FAQ)。

## 最常问的问题 <a href="#most-asked-questions" id="most-asked-questions"></a>

### 问：如果我忘记了主密码应该该怎么办？ <a href="#q-what-do-i-do-if-i-forgot-my-master-password" id="q-what-do-i-do-if-i-forgot-my-master-password"></a>

**答：**&#x4F5C;为一个零知识解决方案，Bitwarden 及其系统对您的主密码不了解，没有办法找回，也没有办法重置您的主密码。如果您已经丢失了您的主密码，很遗憾，团队没有办法恢复账户。想了解下一步该怎么做，或者如何主动保护自己，避免出现这种情况，请参考[您的主密码](../account/log-in-and-unlock/your-master-password.md)这篇文章。

### 问：在紧急情况下，是否有办法让别人访问我的密码库项目？ <a href="#q-is-there-a-way-for-someone-to-access-my-vault-items-in-case-of-emergency" id="q-is-there-a-way-for-someone-to-access-my-vault-items-in-case-of-emergency"></a>

**答：**&#x6709;！拥有高级订阅的用户可以主动设置受信任的紧急联系人，以便在紧急情况下访问您的密码库。如需了解更多信息，请参阅[紧急访问](../account/log-in-and-unlock/more-log-in-options/emergency-access.md)。

### 问：如何更改我的主密码提示？ <a href="#q-how-do-i-change-my-master-password-hint" id="q-how-do-i-change-my-master-password-hint"></a>

**答：**&#x8981;更改您的主密码提示：

1. 在网页 App 中，导航至**设置** → **安全** → **主密码**。
2. 要仅更改您的提示，请在**当前主密码**、**新主密码**和**确认主密码**框中全部输入您当前的主密码以防止被更改，然后在**主密码提示**框中输入提示。
3. 选择**更改主密码**按钮。

### 问：如何更改电子邮箱地址？ <a href="#q-how-do-i-change-my-email-address" id="q-how-do-i-change-my-email-address"></a>

{% hint style="info" %}
如果您使用[电子邮箱方式的两步登录](../account/two-step-login/setup-guides/two-step-login-via-email.md)，则更改您的账户电子邮箱地址不会更改用于接收 2FA 代码的地址。
{% endhint %}

**答：**&#x8981;更改账户所附属的电子邮箱地址：

1. 在网页 App 中，导航至**设置** → **我的帐户**。
2. 在**我的账户**页面，找到**更改电子邮箱**部分。
3. 输入您当前的**主密码**，以证明您有权进行此操作，并指定您想更改为的**新电子邮箱**。
4. 选择**继续**按钮。\
   Bitwarden 将通过电子邮件发送一个验证码到指定的电子邮箱地址。检查您的收件箱中的代码，并将其输入到您的网页密码库中显示的**代码**文本输入框中，以完成更改。如果您没有收到验证码，请检查您的垃圾邮件文件夹。您也可以将 `no-reply@bitwarden.com` 加入白名单，以确保今后的交付。

更改了电子邮箱地址后，您应该立即注销您使用的所有 Bitwarden 客户端 App，然后使用新的凭证重新登录。使用「陈旧」的电子邮箱地址的会话最终将被注销。

### 问：验证邮箱后会解锁哪些功能？ <a href="#q-what-features-are-unlocked-when-i-verify-my-email" id="q-what-features-are-unlocked-when-i-verify-my-email"></a>

**答：**&#x5F53;验证您的电子邮箱地址后，将解锁[创建文件 Send](../bitwarden-send/create-a-send.md)（前提是您具有高级功能权限）。

### 问：为什么我的移动 App、桌面 App 或浏览器扩展程序中丢失了密码库项目？ <a href="#q-why-is-a-vault-item-missing-from-my-mobile-app-desktop-app-or-browser-extension" id="q-why-is-a-vault-item-missing-from-my-mobile-app-desktop-app-or-browser-extension"></a>

**答：**&#x901A;常，这是因为某个 App 的密码库数据已经滞后于网页 App 或其他客户端 App 的数据。执行密码库同步应该可以使所有数据为最新。有关更多信息，请参阅[同步您的密码库](syncing-your-vault.md)。

### 问：有啥安全的方式备份我的密码库数据？ <a href="#q-whats-the-safest-way-to-make-a-backup-of-my-vault-data" id="q-whats-the-safest-way-to-make-a-backup-of-my-vault-data"></a>

**答：**&#x60A8;可以使用[加密导出](../import-export/encrypted-exports.md)（将使用您的[账户加密密钥](../security/account-encryption-key.md)进行加密）对您的密码库数据进行安全的长期备份。这些备份使用账户加密密钥、组织加密密钥或您选择的密码进行加密。

### 问：如何设置当计算机启动时自动启动 Bitwarden？ <a href="#q-can-i-set-bitwarden-to-automatically-start-when-my-computer-starts" id="q-can-i-set-bitwarden-to-automatically-start-when-my-computer-starts"></a>

**答：**&#x4F60;可以将 Bitwarden 桌面 App 设置为启动时打开：

1. 点击**开始**（Windows 徽标）按钮，选择**所有应用程序**，然后滚动并找到 Bitwarden 快捷方式。
2. 右键单击 Bitwarden 桌面 App，选择**更多**，然后选择**打开文件位置**。
3. 文件位置打开后，按 **Windows 徽标键** + **R** 键，键入 `shell:startup`，然后点击**确定**。这将打开启动文件夹。
4. 将 Bitwarden 桌面应 App 的快捷方式从文件位置复制并粘贴到到启动文件夹中。

### 问：为什么会收到「新的设备」电子邮件消息？ <a href="#q-why-am-i-getting-a-new-device-email-message" id="q-why-am-i-getting-a-new-device-email-message"></a>

**答：**&#x901A;常情况下，是因为用户在浏览器上设置了每当他们关闭或使用浏览器时，将清除他们的本地存储和/或缓存。某些扩展程序也可以执行这些操作。如果发生这种情况，您就会失去告诉我们的服务器这是一个现有设备的指示器。新设备通知信息不取决于 IP 地址，只取决于设备本身。我们使用浏览器或客户端中的本地存储为设备贴上一个 id 标签。如果这个 id 之前从未登录过，那么您会收到一封邮件。如果用户清除了本地存储，将会为该设备生成一个新的 id，并且会收到一封新的邮件。

您可能需要为 Bitwarden 做一个例外，或者为 Bitwarden 配置你的白名单来防止缓存或本地存储被清除。如果您的浏览器设置为永远记录历史记录，也可能会发生这种情况。

## 其他问题 <a href="#other-questions" id="other-questions"></a>

### 问：可以在没有 Google Play 的情况下安装 Bitwarden 吗，例如通过 F-Droid？ <a href="#can-i-install-bitwarden-without-google-play-for-instance-on-f-droid" id="can-i-install-bitwarden-without-google-play-for-instance-on-f-droid"></a>

**答：**&#x53EF;以！您可以直接从GitHub [https://github.com/bitwarden/mobile/releases](https://github.com/bitwarden/mobile/releases)下载，也可以添加我们的仓库 [https://mobileapp.bitwarden.com/fdroid/](https://mobileapp.bitwarden.com/fdroid/) 后通过 F-Droid 下载，这删除了所有未经批准的库。

不幸的是，F-Droid 无法从源代码编译我们的 App，因为它基于 Xamarin，而 F-Droid 当前的编译器方法不支持 Xamarin，因此我们必须使用单独的仓库。

### 问：可以关闭 Bitwarden 的自动更新吗？ <a href="#q-can-i-turn-off-automatic-updates-for-bitwarden" id="q-can-i-turn-off-automatic-updates-for-bitwarden"></a>

**答：**&#x53EF;以！在 Windows 上，您可以将环境变量 `ELECTRON_NO_UPDATER=1` 添加到您的桌面 App 模板中，以使自动更新进程在您的终端用户工作站上失效和阻止尝试。

{% hint style="danger" %}
与任何软件一样，运行旧版本可能会带来安全风险。
{% endhint %}

### 问：如何获取桌面应用程序的日志？ <a href="#q-how-do-i-get-logs-for-the-desktop-app" id="q-how-do-i-get-logs-for-the-desktop-app"></a>

**答：**&#x5728;桌面 App 模板中添加环境变量 `ELECTRON_ENABLE_LOGGING=true`，以便将桌面 App 的日志打印到控制台，或者从控制台启动桌面 App 并使用命令行开关将日志写入文件：

* (Windows) `Bitwarden.exe --enable-logging=file --log-file=bitwarden.log`
* (macOS) `./Bitwarden.app/Contents/MacOS/Bitwarden --enable-logging=file --log-file=bitwarden.log`

### 问：我需要旧密码！可以查看我在 Bitwarden 中更改过的密码的历史记录吗？ <a href="#q-i-need-an-old-password-can-i-view-the-history-of-a-password-that-i-changed-in-bitwarden" id="q-i-need-an-old-password-can-i-view-the-history-of-a-password-that-i-changed-in-bitwarden"></a>

**答：**&#x53EF;以。您可以查看登录项目的最近 5 个密码的历史记录。

{% tabs %}
{% tab title="网页 App" %}
打开相关项目然后选择**密码历史记录**：

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/RT3R5a33WrejA8qnIcmqa/7600909424c7c74ac3b6b5fa76ae42ea/2024-12-02_13-56-29.png?_a=DAJCwlWIZAAB" alt=""><figcaption><p>网页密码历史记录</p></figcaption></figure>
{% endtab %}

{% tab title="移动 App" %}
打开相关项目，然后选择窗口底部**密码历史记录**旁边的数字：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1RJbcOMMkIfVTprx3NZbyQ/bd471e08b166d936958927dcacdbd0d8/IMG_1998.jpg?_a=DAJCwlWIZAAB" %}
移动端密码历史记录
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
打开相关项目然后选择**密码历史记录**：

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2XVetRKi7VLJ7Ctq7scOll/b8addc21adcad38e50def42abebc1e80/Password_History.png?_a=DAJCwlWIZAAB" alt=""><figcaption><p>浏览器扩展密码历史记录</p></figcaption></figure>
{% endtab %}

{% tab title="桌面 App" %}
打开相关项目，然后选择窗口底部**密码历史记录**旁边的数字：

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/lvf2rvKuNcJNUYzXOTI99/35f48c812a083b0987b6f3fc2c022764/2025-03-05_15-42-55.png?_a=DAJCwlWIZAAB" alt=""><figcaption><p>桌面端密码历史记录</p></figcaption></figure>
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
查看密码历史会立即以纯文本的方式展示历史密码值。
{% endhint %}

### 问：忘记了保存已生成的密码！可以查看已生成的密码的历史记录吗？ <a href="#q-i-forgot-to-save-a-generated-password-can-i-view-the-history-of-generated-passwords" id="q-i-forgot-to-save-a-generated-password-can-i-view-the-history-of-generated-passwords"></a>

**答：**&#x53EF;以。您可以查看密码生成器的历史记录，但请注意，每个 App 的历史记录是独立的，不会在设备之间同步。

### 问：当我清空我的密码库时会发生什么？ <a href="#what-happens-when-i-purge-my-vault" id="what-happens-when-i-purge-my-vault"></a>

**答：**&#x6E05;空**个人密码库**时，所有密码库项目和文件夹都将被删除。当您清空**组织密码库**时，所有已共享（即归组织所有）的密码库项目都将被删除，但现有的用户、集合和群组将保留在原来的位置。要清空您的密码库：

{% tabs %}
{% tab title="个人密码库" %}
{% hint style="danger" %}
清空密码库是永久性的。无法撤销。
{% endhint %}

要清空您的个人密码库：

1. 在 Bitwarden 网页 App 中，导航至**设置** → **我的账户**。
2. 在**危险区域**部分，选择**清除密码库**。您需要确认主密码才能完成清除。
{% endtab %}

{% tab title="组织密码库" %}
{% hint style="danger" %}
清空密码库是永久性的。无法撤销。
{% endhint %}

要清除组织密码库，您必须是组织的所有者：

1. 在 Bitwarden 网页 App 中，打开管理控制台并导航至**设置** → **组织信息**。
2. 在**危险区域**部分，选择**清除密码库**。您需要确认主密码才能完成清除。
{% endtab %}
{% endtabs %}

### 问：可以打印密码库数据吗？ <a href="#q-can-i-print-my-vault-data" id="q-can-i-print-my-vault-data"></a>

**答：**&#x65E0;法直接从 Bitwarden 打印，但是您可以[将密码库数据导出](../import-export/export-vault-data.md)为 `.csv` 或 `.json` 文件然后从文本编辑器中打印。

### 问：我可以阻止将我的凭据保存到剪贴板吗？ <a href="#q-can-i-prevent-my-credentials-from-being-saved-to-the-clipboard" id="q-can-i-prevent-my-credentials-from-being-saved-to-the-clipboard"></a>

**答：**&#x53EF;以！要从剪贴板自动清除从 Bitwarden 复制的值：

* 在浏览器扩展中，导航至**设置** → **自动填充**，然后将**清除剪贴板**设置为**从不**以外的值。
* 在移动 App 中，导航至**设**置 → **其他**，然后将**清除剪贴板**设置为**从不**以外的值。
* 在桌面 App 中，导航至**设置**，在**首选项**部分将**清除剪贴板**设置为**从不**以外的值。

### 问：卸载或删除我的 Bitwarden App 是否也会删除我的密码库数据吗？ <a href="#q-does-uninstalling-or-deleting-my-bitwarden-app-also-delete-my-vault-data" id="q-does-uninstalling-or-deleting-my-bitwarden-app-also-delete-my-vault-data"></a>

**答：**&#x4E0D;会，删除 Bitwarden App/扩展程序并不会删除您的密码库数据。密码库数据加密保存在服务器上。如果您希望**永久**删除您的密码库数据，请参阅[删除账户或组织](../plans-and-pricing/delete-an-account-or-organization.md)。

### 问：Bitwarden 是否管理 Android 手机上的 Firefox 浏览器扩展？ <a href="#q-does-bitwarden-manage-the-firefox-browser-extension-on-android-mobile" id="q-does-bitwarden-manage-the-firefox-browser-extension-on-android-mobile"></a>

**答：**&#x41;ndroid 移动设备上有适用于 Firefox 的 Bitwarden 浏览器扩展。但是，此扩展并未得到 Bitwarden 的正式支持，并且团队意识到此客户端中的某些功能无法正常工作。Android 用户可能更喜欢使用 Bitwarden [移动 App](../getting-started/getting-started-mobile.md) 作为官方支持的密码管理器客户端。

### 问：Bitwarden 是否有任何可以调整图形或性能的设置？ <a href="#q-does-bitwarden-have-any-settings-that-can-be-adjusted-for-graphics-or-performance" id="q-does-bitwarden-have-any-settings-that-can-be-adjusted-for-graphics-or-performance"></a>

**答：**&#x662F;的，Bitwarden 桌面 App 中确实包含调整系统性能的设置。在 Bitwarden 桌面 App 中，有两种方法可以禁用图形 (GPU) 加速：

* 导航至**设置** → **应用程序设置（所有帐户）**，取消选中**使用硬件加速**复选框。
* 从导航栏栏中，**帮助** → **故障排除** → **禁用硬件加速并重新启动**。

### 问：Bitwarden 可以安装在 Android 私人空间中吗？ <a href="#q-can-bitwarden-be-installed-in-an-android-private-space" id="q-can-bitwarden-be-installed-in-an-android-private-space"></a>

**答：**&#x76EE;前，Bitwarden 不建议在私人空间（15.0 以上）安装 Android 应用程序，因为私人空间不适合需要在后台运行自动填充和同步等功能的 App。

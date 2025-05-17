# 自动填充 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/autofill-faqs/)
{% endhint %}

### 问：如何禁用 Bitwarden 无障碍气泡？ <a href="#q-how-do-i-disable-the-bitwarden-accessbility-bubble" id="q-how-do-i-disable-the-bitwarden-accessbility-bubble"></a>

1. 在您的 Android 设备中打开**设置**。
2. 导航到**无障碍**。
3. 选择 **Bitwarden**。
4. 将 Bitwarden 快捷方式切换为关闭。

### 问：可以自动填充分离式登录工作流吗？ <a href="#q-can-i-auto-fill-on-a-split-login-workflow" id="q-can-i-auto-fill-on-a-split-login-workflow"></a>

**答：**&#x5206;离式登录工作流（即用户名和密码字段分别显示在不同的屏幕上）可以被 Bitwarden 浏览器扩展程序自动填充，但目前不支持移动 App。

### 问：在 iPad 上使用物理键盘时，可以使用自动填充功能吗？ <a href="#q-can-i-use-auto-fill-while-using-a-physical-keyboard-on-an-ipad" id="q-can-i-use-auto-fill-while-using-a-physical-keyboard-on-an-ipad"></a>

**答：**&#x53EF;以。要在使用物理键盘时使用自动填充功能：

1. 打开您设备上的 iOS **⚙️设置** App。
2. 点击**通用**。
3. 点击**键盘**。
4. 在「所有键盘」部分，将**快捷键**切换为打开。

### 问：Android 设备中如何禁用 Google 自动填充？ <a href="#q-how-do-i-disable-google-auto-fill-in-my-android-device" id="q-how-do-i-disable-google-auto-fill-in-my-android-device"></a>

**答：**&#x8981;在您的 Android 设备中禁用 Google 自动填充：

1. 在您的 Android 设备中打开**设置**。
2. 向下滚动并点按 **Google**。
3. 点击 **Google 自动填充**然后将其切换为关闭。

### 问：出现「生物识别解锁已禁用，等待验证主密码」时怎么办？ <a href="#q-what-do-i-do-about-biometric-unlock-disabled-pending-verification-of-master-password" id="q-what-do-i-do-about-biometric-unlock-disabled-pending-verification-of-master-password"></a>

**答：**&#x5728; iOS 系统中，当您更改了设备的生物识别设置时（例如在触控 ID 中添加了另一个手指），这种情况最常发生。要解决这个错误：

1. **如果您已激活了** [**PIN 码**](../your-vault/unlock-with-pin.md)**验证**，禁用它。
2. 注销您的 Bitwarden 移动 App。
3. 检查您的设备设置是否设置为[使用 Bitwarden 进行自动填充](../password-manager/auto-fill/auto-fill-basics/auto-fill-logins-on-ios.md#keyboard-auto-fill)。
4. 重新登录到您的 Bitwarden 移动 App。
5. 如果要将 PIN 码验证用作[生物识别](../your-vault/unlocking-with-biometrics.md)的备份，请重新启用 [PIN 码](../your-vault/unlock-with-pin.md)验证。

### 问：当「基础域名」是设定的规则时，URI 匹配是否对某些网站无效？ <a href="#q-does-uri-matching-not-work-with-certain-websites-when-base-domain-is-the-set-rule" id="q-does-uri-matching-not-work-with-certain-websites-when-base-domain-is-the-set-rule"></a>

**答：**&#x67D0;些通常应该匹配的结果被过滤掉了，因为您当前所在的 URL 可能为多个网站提供服务。要了解更多有关这些网站的更多信息，请访问 [publicsuffix.org](https://publicsuffix.org/)。

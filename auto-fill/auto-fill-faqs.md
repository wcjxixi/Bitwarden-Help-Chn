# 自动填充常见问题

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/autofill-faqs/)
{% endhint %}

### 问：如何禁用 Bitwarden 无障碍气泡？ <a href="#q-how-do-i-disable-the-bitwarden-accessbility-bubble" id="q-how-do-i-disable-the-bitwarden-accessbility-bubble"></a>

1. 在您的安卓设备中打开**设置**。
2. 导航到**无障碍**。
3. 选择 **Bitwarden**。
4. 将 Bitwarden 快捷方式切换为关闭。

### 问：可以自动填充分离式登录工作流吗？ <a href="#q-can-i-auto-fill-on-a-split-login-workflow" id="q-can-i-auto-fill-on-a-split-login-workflow"></a>

**答：**分离式登录工作流（即用户名和密码字段分别显示在不同的屏幕上）可以被 Bitwarden 浏览器扩展程序自动填充，但目前不支持移动应用程序。

### 问：在 iPad 上使用物理键盘时，可以使用自动填充功能吗？ <a href="#q-can-i-use-auto-fill-while-using-a-physical-keyboard-on-an-ipad" id="q-can-i-use-auto-fill-while-using-a-physical-keyboard-on-an-ipad"></a>

**答：**可以。要在使用物理键盘时使用自动填充功能：

1. 打开您设备上的 iOS **⚙️设置**应用程序。
2. 点击**通用**。
3. 点击**键盘**。
4. 在所有键盘部分，将**快捷键**切换到打开状态。

### 问：如何在我的 Android 设备中禁用 Google 自动填充？ <a href="#q-how-do-i-disable-google-auto-fill-in-my-android-device" id="q-how-do-i-disable-google-auto-fill-in-my-android-device"></a>

**答：**要在您的 Android 设备中禁用 Google 自动填充：

1. 在您的 Android 设备中打开**设置**。
2. 向下滚动并点按 **Google**。
3. 点击 **Google 自动填充**然后将其关闭。

### 问：出现「生物识别解锁已禁用，等待验证主密码」时怎么办？ <a href="#q-what-do-i-do-about-biometric-unlock-disabled-pending-verification-of-master-password" id="q-what-do-i-do-about-biometric-unlock-disabled-pending-verification-of-master-password"></a>

**答：**在 iOS 系统中，当你更改了设备的生物识别设置时（例如在触控 ID 中添加另一个手指），这种情况最常发生。要解决这个错误：

1. **如果你已激活了** [**PIN 码**](../your-vault/unlock-with-pin.md)**验证**，禁用它。
2. 注销你的 Bitwarden 移动应用程序。
3. 检查你的设备设置是否设置为[使用 Bitwarden 进行自动填充](../password-manager/auto-fill/auto-fill-basics/auto-fill-logins-on-ios.md#keyboard-auto-fill)。
4. 重新登录到您的 Bitwarden 移动应用程序。
5. 如果要将 PIN 码验证用作[生物识别](../your-vault/unlocking-with-biometrics.md)的备份，请重新启用 [PIN 码](../your-vault/unlock-with-pin.md)验证。

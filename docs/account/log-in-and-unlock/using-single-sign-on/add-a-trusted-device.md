# 添加受信任设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/add-a-trusted-device/)
{% endhint %}

当您成为某个组织的成员时，您首次登录的设备将自动被注册为受信任设备。注册成功后，您只需完成公司既定的单点登录流程，即可登录 Bitwarden 并解密您的密码库数据。

{% hint style="success" %}
当您登录设备时，设备将默认受到信任。强烈建议您在登录公共或共享设备时取消选中**记住此设备**选项。
{% endhint %}

当您登录新设备时，您需要批准或信任该设备。有几种方法可以做到这一点：

* **从其他设备批准**：如果您已在另一台设备上登录 Bitwarden，您可以从那里批准新设备：

{% tabs %}
{% tab title="移动 App" %}
要使用移动 App 批准请求：

1、在移动 App 中，导航至**设置** → **账户安全** → **待处理的登录请求**：

{% embed url="https://bitwarden.com/assets/1ZB3Pc8T0mlP96W3IZefrR/a22c8efe63a88941bad11a278b1d113d/2025-09-09_09-39-13.png?w=1193&fm=avif" %}
移动端上待处理的登录请求
{% endembed %}

2、定位并点击待处理的设备请求。

3、验证指纹短语然后选择**确认访问**：

{% embed url="https://bitwarden.com/assets/6xeP36n7g2dbwLI9YWjNg4/2aa9fdc96e765e963ee07f38ad0b6c06/2025-09-09_09-39-44.png?w=1192&fm=avif" %}
在移动端上批准登录
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
要使用浏览器扩展批准请求：

1、在浏览器扩展中，等待接收到设备批准请求或导航至**设置** → **账户安全** → **设备**：

{% embed url="https://bitwarden.com/assets/6OZfQt2jDDqa9F0MaUdBUq/1460f0ec04c63ab55da1f5eaf37ca469/2025-09-09_09-49-23.png?w=1190&fm=avif" %}
浏览器扩展上的设备视图
{% endembed %}

2、在**设备**选项卡上，定位并选择待处理的设备请求：

{% embed url="https://bitwarden.com/assets/64f1jZ30In2BbWDEUZVtxO/9de965d59fedca2bad4e325f4181f69a/2025-09-09_09-49-42.png?w=1187&fm=avif" %}
浏览器扩展上的列表
{% endembed %}

3、验证指纹短语然后选择**确认访问**：

{% embed url="https://bitwarden.com/assets/2LFY10MMpI9G0ZcojcXveg/0a891ec5fa8f6052e5804841e7ec7724/2025-09-09_09-48-55.png?w=1193&fm=avif" %}
在浏览器扩展上批准设备
{% endembed %}
{% endtab %}

{% tab title="网页 App" %}
要使用网页 App 批准请求：

{% hint style="info" %}
当请求批准登录浏览器扩展程序时，即使您单击退出或最小化扩展程序窗口，该扩展程序也会等待最多两分钟以获得批准，以便使用网页 App 批准请求。
{% endhint %}

1、在网页 App 中，选择横幅通知中的**审查登录请求**链接或导航至**设置** → **安全** → **设备**：

{% embed url="https://bitwarden.com/assets/1K9FeC1OVOwyu0T8DMiwOp/90852f4e82b80827750bffd19cb6493d/2025-09-09_09-23-06.png?w=1189&fm=avif" %}
在网页 App 上批准请求
{% endembed %}

2、在**设备**选项卡上，定位并选择待处理的设备请求：

{% embed url="https://bitwarden.com/assets/7GLmOwtReFuUD3uxPQ0LB8/2abd84049d99f0dc0c21158c636ab55d/2025-09-09_09-22-11.png?w=1193&fm=avif" %}
网页 App 上的设备列表
{% endembed %}

3、验证指纹短语然后选择**确认访问**：

{% embed url="https://bitwarden.com/assets/6s6Hdn9L1EyeRfBsmOcfgX/a4e9e4996abc1ac63b8c6f2b3880cd07/2025-09-09_09-22-44.png?w=1189&fm=avif" %}
使用网页 App 批准访问
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
要使用桌面 App 批准请求：

1、在桌面 App 中，等待接收到设备批准请求：

{% embed url="https://bitwarden.com/assets/5cpkevhyuiSg82yfopvmc1/7d19d6377dbba8d4c6abee37b96a5037/2025-09-09_09-07-05.png?w=1200&fm=avif" %}
在桌面 App 上批准
{% endembed %}

2、验证指纹短语然后选择**确认访问**。
{% endtab %}
{% endtabs %}

* **使用主密码批准**：如果您是管理员或所有者，或者在受信任设备 SSO 实施之前加入了您的组织，因此仍然拥有与您的账户关联的主密码，则可以输入主密码来批准设备。

{% embed url="https://bitwarden.com/assets/5IMJBQOrklcOuLVEpaR6gX/60ead8f10e34f7acd2467eaaa34ff93d/2025-06-16_15-22-15.png?w=642&fm=avif" %}

* **请求管理员批准**：您可以向组织内的管理员和所有者发送设备批准请求以供批准。您必须[注册账户恢复](../../../admin-console/manage-members/account-recovery/account-recovery-enrollment.md#self-enroll-in-account-recovery)才能请求管理员批准，不过您在加入组织时可能已[自动注册](../../../admin-console/manage-members/account-recovery/account-recovery-enrollment.md#automatic-enrollment)。在许多情况下，这将是您唯一可用的选择（[了解更多](../../../admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md)）。

{% hint style="info" %}
如果您使用此选项，（当设备请求获得批准后）您将收到一封电子邮件，通知您可以继续在该设备登录。您必须在 12 小时内登录新设备，否则批准将失效。
{% endhint %}

新设备成为受信任设备后，您只需完成公司既定的单点登录流程，即可登录 Bitwarden 并解密您的密码库数据。

## 添加第一台受信任设备 <a href="#adding-your-first-trusted-device" id="adding-your-first-trusted-device"></a>

对于通过[使用 SSO 登录](../../../admin-console/login-with-sso/about-login-with-sso.md)即时 (JIT) 配置而被邀请的用户，用于访问 Bitwarden 的初始客户端将成为他们的第一台受信任设备。如果访问的初始客户端是 Bitwarden 桌面 App 或移动 App，则该设备可用于批准其他设备。

要使桌面 App 或移动 App 成为第一个受信任设备，用户不应使用组织邀请链接，而是打开桌面 App 或移动 App，选择**企业单点登录**选项，以开始 JIT 流程。

> **\[译者注]**：JIT：Just-In-Time，指的是「即时配置」或「按需配置」，是一种用户管理和资源配置的方式。Bitwarden 使用这种方式简化了管理流程并提升了安全性。

## 移除受信任设备 <a href="#remove-a-trusted-device" id="remove-a-trusted-device"></a>

设备将保持信任状态，直到：

* 应用程序或扩展被卸载。
* 网页浏览器的内存被清除（仅限网页 App）。
* 用户的加密密钥被轮换。

{% hint style="info" %}
只有拥有主密码的用户才能轮换其[账户加密密钥](../../../security/encryption/encryption-key-rotation.md)。[了解更多](../../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md#impact-on-master-passwords)。
{% endhint %}

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

如果您在建立设备信任时遇到问题：

* 在 Chrome 上，检查是否已开启**允许网站将数据保存在设备上**（**设置** → **隐私与安全** → **网站设置** → **更多内容设置** → **设备端网站数据** → **允许网站将数据保存在设备上**）。

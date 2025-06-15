# 添加受信任设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/add-a-trusted-device/)
{% endhint %}

当您成为某个组织的成员时，您首次登录的设备将自动被注册为受信任设备。注册成功后，您只需完成公司既定的单点登录流程，即可登录 Bitwarden 并解密您的密码库数据。

{% hint style="success" %}
当您登录设备时，设备将默认受到信任。强烈建议您在登录公共或共享设备时取消选中**记住此设备**选项。
{% endhint %}

不过，当您登录新设备时，您需要批准或信任该设备。有几种方法可以做到这一点：

* **从其他设备批准**：如果您有其他 Bitwarden 密码管理器网页 App、移动 App 或桌面 App，您可以从那里批准新设备，类似于设备登录。在移动端，首先确保已启用**批准登录请求**选项。

{% tabs %}
{% tab title="移动 App" %}
发起设备登录后，要使用移动 App 批准请求：

1、登录到移动 App。

2、导航至**设置** → **账户安全** → **待处理的登录请求**。

3、定位并选择活动设备请求。

4、验证指纹短语然后选择**确认登录**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6xeP36n7g2dbwLI9YWjNg4/dbc18de80ace51b789021cc7083e76e0/IMG_1954.jpeg?_a=DAJAUVWIZAAB" %}
{% endtab %}

{% tab title="网页 App" %}
发起设备登录后，要使用网页 App 批准请求：

1、登录到网页 App。

{% hint style="info" %}
在请求批准登录浏览器扩展时，扩展窗口必须保持打开状态，直到程序完成。Bitwarden 建议：

* **对于 Chrome 和 chromium 浏览器**： 在单独的浏览器窗口中打开网络应用程序，这将允许扩展在原始窗口中保持打开状态。
* **对于 Safari 浏览器**：在单独的浏览器窗口中打开网页 App，这将允许扩展在原始窗口中保持打开状态。
* **对于 Firefox**：在侧边栏中打开扩展，这样就可以在打开网页 App 时继续保留扩展。

这将在以后的版本中得到改进。
{% endhint %}

2、导航至**设置** → **安全** → **设备**。

3、定位并选择活动设备请求。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7GLmOwtReFuUD3uxPQ0LB8/71b896fcc76d3918e3fe37dee978e2dd/2025-01-14_12-35-31.png?_a=DAJAUVWIZAAB" %}

4、验证指纹短语然后选择**确认登录**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6s6Hdn9L1EyeRfBsmOcfgX/ada1215dc8e370c7b82f1a0fc6bd8923/2025-01-14_15-55-10.png?_a=DAJAUVWIZAAB" %}
{% endtab %}

{% tab title="桌面 App" %}
发起设备登录后，要使用桌面 App 批准请求：

1、登录到桌面 App。

2、验证请求将发送到您的桌面 App。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5cpkevhyuiSg82yfopvmc1/3bccaff5f02ad79bab67fb7ed941ed0e/2025-01-16_11-44-40.png?_a=DAJAUVWIZAAB" %}

3、验证指纹短语然后选择**确认登录**。
{% endtab %}
{% endtabs %}

{% hint style="info" %}
我们建议您先信任一个移动或桌面 App，然后立即打开**批准登录请求**选项。这样您就可以使用**从其他设备批准**选项来添加后续设备。
{% endhint %}

* **请求管理员批准**：您可以向组织内的管理员和所有者发送设备批准请求以供批准。在许多情况下，这将是您唯一可用的选择（[了解更多](../../../admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md)）。

{% embed url="https://bitwarden.com/_gatsby/image/2ae6ef9b326ba69fa7233cda5cd242b6/46e040f6b375ce8ca8c6e3e1ae8af9f6/request%20admin%20approval.webp?eu=d98b02e0b1c8fc830d6ca28a6d233460e13d5ffef65567d86f64b5a91ea89cd276a74f0472942ee07d3c08dd80b317e961907a6818e9d889c1be1df2bf61aa0e008153e866b42107007accfab7a002446bc51b0df2d2cf5aa16e7a82b6e6b1781b04187fa222fcc5acea3f7bafda7263bde3e5303686fd29a3510b1088062fa920a4979c6d4da894b149e7bba9ae16c8e59a577521a4b16e7e24335a248b58fbf4d002265136165a33c6f95dcf64c3e26a1864230c5c57f2356bd951aa6c6492b0f2a45edd2f64a3fd887425c587c1d1b947f57419b68f67ebdd7d2b5213ec4dfa&a=w%3D493%26h%3D550%26fm%3Dwebp%26q%3D75&cd=2023-08-31T17%3A56%3A38.040Z" %}
请求管理员批准
{% endembed %}

{% hint style="info" %}
如果您使用此选项，（当设备请求获得批准后）您将收到一封电子邮件，通知您可以继续在该设备登录。您必须在 12 小时内登录新设备，否则批准将失效。
{% endhint %}

* **使用主密码批准**：如果您是管理员或所有者，或者在受信任设备 SSO 实施之前加入了您的组织，因此仍然拥有与您的账户关联的主密码，则可以输入主密码来批准设备。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/Zutl0zizn3ZdFAHRHGaH1/a4fbd196221ffcf80fac80ab9f0835ea/requires_device_approval.png?_a=DAJAUVWIZAAB" %}
使用主密码批准
{% endembed %}

新设备成为受信任设备后，您只需完成公司既定的单点登录流程，即可登录 Bitwarden 并解密您的密码库数据。

## 添加第一台受信任设备 <a href="#adding-your-first-trusted-device" id="adding-your-first-trusted-device"></a>

对于通过[使用 SSO 登录](../../../login-with-sso/about-login-with-sso.md)即时 (JIT) 配置而被邀请的用户，用于访问 Bitwarden 的初始客户端将成为他们的第一台受信任设备。如果访问的初始客户端是 Bitwarden 桌面 App 或移动 App，则该设备可用于批准其他设备。

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

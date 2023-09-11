# 添加受信任设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/add-a-trusted-device/)
{% endhint %}

当您成为某个组织的成员时，您首次登录的设备将自动注册为受信任设备。注册成功后，您只需完成公司既定的单点登录流程，即可登录 Bitwarden 并解密您的密码库数据。

{% hint style="info" %}
当您登录设备时，设备将默认受到信任。强烈建议您在登录公共或共享设备时取消选中**记住此设备**选项。
{% endhint %}

不过，当您登录新设备时，您需要批准或信任该设备。有几种方法可以做到这一点：

* **从其他设备批准**：如果您有其他 Bitwarden 密码管理器移动应用程序或桌面应用程序，您可以从那里批准新设备，类似于设备登录。

{% hint style="info" %}
我们建议您先信任一个移动或桌面应用程序，这样您就可以使用**从其他设备批准**选项来添加后续设备。
{% endhint %}

* **请求管理员批准**：您可以向组织内的管理员和所有者发送设备批准请求以供批准。在许多情况下，这将是您唯一可用的选择（[了解更多](approve-a-trusted-device.md)）。

{% embed url="https://bitwarden.com/_gatsby/image/2ae6ef9b326ba69fa7233cda5cd242b6/46e040f6b375ce8ca8c6e3e1ae8af9f6/request%20admin%20approval.webp?eu=d98b02e0b1c8fc830d6ca28a6d233460e13d5ffef65567d86f64b5a91ea89cd276a74f0472942ee07d3c08dd80b317e961907a6818e9d889c1be1df2bf61aa0e008153e866b42107007accfab7a002446bc51b0df2d2cf5aa16e7a82b6e6b1781b04187fa222fcc5acea3f7bafda7263bde3e5303686fd29a3510b1088062fa920a4979c6d4da894b149e7bba9ae16c8e59a577521a4b16e7e24335a248b58fbf4d002265136165a33c6f95dcf64c3e26a1864230c5c57f2356bd951aa6c6492b0f2a45edd2f64a3fd887425c587c1d1b947f57419b68f67ebdd7d2b5213ec4dfa&a=w%3D493%26h%3D550%26fm%3Dwebp%26q%3D75&cd=2023-08-31T17%3A56%3A38.040Z" %}
请求管理员批准
{% endembed %}

{% hint style="info" %}
如果使用此选项，您将收到一封电子邮件，通知您继续在新设备上登录。您必须在 12 小时内登录新设备，否则批准将失效。
{% endhint %}

* **使用主密码批准**：如果您是管理员或所有者，或者在受信任设备 SSO 实施之前加入了您的组织，因此仍然拥有与您的账户关联的主密码，则可以输入主密码来批准设备。

{% embed url="https://bitwarden.com/_gatsby/image/de2933daf25a7a11c475abdf52457c94/06b22fd7741271198dde2e569fe19e3e/requires%20device%20approval.webp?eu=d8df59b2e09aa8d50868a683607b646cb23d55affd5163813a30edfb1bfdca8125f04804739772b3793c0cddd7e541b861c329301eee85d2c9bd49fce961aa5e058553ec35b57801537ec2afb2f10e426dcf1f50a38b9b01f0387481edb4e4751058192ca828be85b8fd3231b98b2f66bce4a7293096a120a4561e17c1076ea539eac78b7000bd8ae64eaca5bbed4ad3c2b269184799ad66642d4d4950b06abcbad8413565290a027f90ac329317e7ce5e641672265e1ca6636c8201fa6537c1e6faf70b8a2c73e1fe9862788692fc89bb1aa42973b29e38ebd77a3f574ff950c2e82eb18b375361d06abad713f452592b00dc4b&a=w%3D504%26h%3D555%26fm%3Dwebp%26q%3D75&cd=2023-08-31T17%3A56%3A43.270Z" %}
使用主密码批准
{% endembed %}

新设备成为可信设备后，您只需完成公司既定的单点登录流程，即可登录 Bitwarden 并解密您的密码库数据。

## 移除受信任设备 <a href="#remove-a-trusted-device" id="remove-a-trusted-device"></a>

设备将保持信任状态，直到：

* 应用程序或扩展被卸载。
* Web 浏览器的内存被清除（仅限 Web 应用程序）。
* 用户的加密密钥被轮换。

{% hint style="info" %}
只有拥有主密码的用户才能轮换其[账户加密密钥](../../../security/account-encryption-key.md)。[了解更多](about-trusted-devices.md#impact-on-master-passwords)。
{% endhint %}

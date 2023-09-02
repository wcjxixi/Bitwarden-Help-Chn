# 设备登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/log-in-with-device/)
{% endhint %}

您知道吗？您可以使用辅助设备而不是您的主密码来登录 Bitwarden。设备登录是一种无密码的身份验证方式，通过向您当前已登录的任何移动设备发送身份验证请求以获得批准，而无需输入您的主密码。[了解我们的零知识加密实施方案](log-in-with-device.md#yun-zuo-fang-shi)。

可以在网页密码库、浏览器扩展、桌面应用程序和移动应用程序上发起设备登录。这些应用程序发出的请求可以在移动应用程序和桌面应用程序上获得批准。

## 设备登陆准备 <a href="#prepare-to-log-in-with-a-device" id="prepare-to-log-in-with-a-device"></a>

要设置设备登录：

* 正常登录一次发起设备登录的应用程序（网页密码库、浏览器扩展、桌面或移动应用程序），以便 Bitwarden 可以识别您的设备。

{% hint style="info" %}
使用隐身模式或隐私浏览会阻止 Bitwarden 注册您的浏览器，因此您将无法在隐私浏览器窗口中使用设备登录。
{% endhint %}

* 在用于批准的应用程序（移动或桌面应用程序）上拥有认可的账户。要识别账户，您必须随时已成功登录该设备。
* 在用于批准的应用程序中，打开 **⚙️设置**（或 iOS 桌面上的**首选项**），在**安全**部分，打开**批准登录请求**。

{% hint style="info" %}
作为企业组织的成员，您需要遵守 SSO 策略，如果您无法使用**设备登录**选项，则需要改用 [SSO 登录](../login-with-sso/using-login-with-sso.md#login-using-sso)。
{% endhint %}

## 使用设备登录 <a href="#logging-in-with-a-device" id="logging-in-with-a-device"></a>

在网页密码库的登录界面，输入您的电子邮件地址并选择**继续**。然后，选择**设备登录**选项：

{% embed url="https://bitwarden.com/_gatsby/image/2c94e98a15f2d8ca5d4b77082f8dc44a/ee6b7982ad0bb5d39c9a2fa12fd64110/Screen%20Shot%202022-11-01%20at%209.08.26%20AM.webp?eu=d88f03b0e0c9ad835c6ea2826874333de53c57adfa0236d73f6ce7ac4ea096d276fa1855769d2be22c3d588c86e647bb6197793510ebd9d396bc10a1ec33ad0952800ebb60e174055979c0fcb7a752436f901e5da1d79908f6647282b7b3e1731156157da978b0d4b9ff3437e4842d3ab8e3a4286f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32bcfaf545205d5c15524791af5d8037ead4567c397d564055f26e3d8203fa6d3390ecffa654dc2c7eb3aecd3479d590ff87ed1fac7e71e7d044fac06e2f5062cf4bf2f814f5d2660413802be7954ddd52415a499c1c813a22df572ef119c4bf10&a=w%3D731%26h%3D491%26fm%3Dwebp%26q%3D75&cd=2022-11-29T13%3A10%3A06.427Z" %}
设备登录
{% endembed %}

使用**设备登录**会将身份验证请求发送到您当前登录并已启用该选项的任何移动应用程序以获得批准。如果请求未获批准或拒绝，则请求将在 15 分钟后过期。如果您没有收到登录请求，请尝试从移动应用程序[手动同步您的密码库](syncing-your-vault.md)。

如果请求未被批准或被拒绝，则请求将在 15 分钟后过期。如果您没有收到登录请求或正在使用 F-Droid，请尝试从移动应用程序[手动同步您的密码库](syncing-your-vault.md)。

{% hint style="info" %}
如果您使用**设备登录**选项，您仍然需要使用任何当前有效的[两步登录方法](../two-step-login/two-step-login-methods.md)。
{% endhint %}

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

当发起设备登录时：

1. 网页密码库客户端向 Bitwarden 数据库中的身份验证请求表发送一个请求，其中包括账户电子邮件地址、唯一的身份验证请求公钥ᵃ 和访问代码。
2. 已注册的设备，即已登录并在 Bitwarden 数据库中存储了[特定于设备的 GUID](../security/administrative-data.md) 的移动应用程序客户端，将收到此请求。
3. 请求获得批准后，移动应用程序客户端使用此请求中包含的身份验证请求公钥加密账户的主密钥和主密码哈希。
4. 移动应用程序客户端然后将加密的主密钥和加密的主密码哈希 PUT 到身份验证请求记录，并将请求标记为已完成。
5. 网页密码库客户端获取加密的主密钥和加密的主密码哈希。
6. 然后，网页密码库客户端使用身份验证请求私钥在**本地**解密主密钥和主密码哈希。
7. 然后，网页密码库客户端使用访问代码和已完成的身份验证请求通过 Bitwarden Identity 服务对用户进行身份验证。

ª - 身份验证请求公钥和私钥是为每一个无密码登录请求生成的唯一密钥，其存在时间与请求的存在时间相同。如果请求未被批准或被拒绝，请求将在 15 分钟后过期并从数据库中清除。

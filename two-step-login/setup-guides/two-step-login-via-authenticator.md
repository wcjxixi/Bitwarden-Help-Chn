# 两步登录-验证器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-authenticator/)
{% endhint %}

第三方验证器应用程序（例如 [Authy](https://authy.com/)，[Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en) 或 [FreeOTP](https://freeotp.github.io/)）方式的两步登录对于所有 Bitwarden 用户是免费的。

{% hint style="info" %}
某些身份验证器应用程序（例如 Google 身份验证器）不会自动备份您的 2FA 令牌以方便迁移到新的移动设备。在这些情况下，您应该手动保存每个令牌的身份验证器恢复代码。

其他应用程序如 Authy 等，支持跨设备备份和同步。在这些情况下，请务必设置一个强大的备份密码并将其记录在您的 Bitwarden 密码库中。
{% endhint %}

## 设置验证器 <a href="#setup-an-authenticator" id="setup-an-authenticator"></a>

完成以下步骤以启用验证器应用程序方式的两步登录：

{% hint style="warning" %}
**丢失对验证器应用程序的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。
{% endhint %}

1、登录您的[网页密码库](https://vault.bitwarden.com/)。

2、选择个人资料图标并然后下拉列表中选择**账户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?eu=8adb56b0eaccf885076fa2d66f746161e56956aaac0032d43465b6f94bfe9b8e71fa1151289528b0796d528bd7e816bc31c67d691befd18991bc4af4be3da80d07835fb836b07807052ec4fde4a1574d60c11b5fa8d1c90ca76a21ddb4b4e47711571b23ae7ebbd7e8fa3064badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec3226050d762c882bfad0bb5137732f072e7fc6d45fae7e91b13f4934705f0c03a5673a8555fb3863c7b0aef509da7e7ee7fdc06073d0cab1e3be58f97f2888ac7ff6c654780e0fae0eadb966f6d10b574aee2bfa8b4fb61d04352ff36197647e8e&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A24%3A03.707Z" %}
账户设置
{% endembed %}

3、选择**安全**页面和**两步登录**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/825426d227e1afce2f4b644e6a3e9e84/3cbf2a88c5de2a53993ef05ef68dd09e/Screen%20Shot%202022-05-16%20at%2011.13.53%20AM.webp?eu=8a8a51b0e0ccfdd5073bf1d23e766960e83d03fffc0737d33964e4f91dafcb8e23a01855769673e42e3808de85e016b86ec12b341ce7818fc1ea4bf3bc32fb5a028b0cef61e678540728c3afb1fd0f4c6a974b5ea986c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bb9e29d485de6cde71bbcbbb7da6c8ad4b12f5614d3f02a2172494950bc2bbca7e056706b7d415235ccfb5f926191b06d1b6425590b0bf378598317ae396fac87a3fe19b6787be3aad431759bc2a8efbc5ec32b77f9ce24b78738157f70b253f3eb&a=w%3D779%26h%3D301%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.371Z" %}
两步登录
{% endembed %}

4、定位到**验证器应用**选项然后选择**管理**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/ce0f5b2f6ec4ce0a7d1f6d1826315eac/9cd93fc2542897e9860b9a4630f212f1/twostep-options-authoverlay.webp?eu=8adb56e4e3c9fc85093da0d26f236338e33c01abf75267d56866e2a84aab9f8077a21807269c7ab22b3f5fdfdbe94ab264c27a344cead4ddc4b91da0eb60ab5e50d10cef67e725560579c6f6b8f6034469951850f4d0ce00a2387ad3e2b5b3221e591b7aaf2cbf84b8ac6062e4832830b8e2a57d34cbac2be0135f54c14035b824f89ac12c47b39fe74aacf8bded5f9cdfa4784303c5ad6066684b5d06be6be1a4e40c2c7e2e5f5e428fce119918febf387c3969243e03b3015dd1048e7360c0b7fea20b8c7a72e4fd9c3978d5c3a9d1bf4ff97975b1cd75ffd6382b5b08b357eae338b387241b51c16ea3ca12f11e547004da43cf71628569169247dab6&a=w%3D754%26h%3D391%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A18%3A21.383Z" %}
选择管理按钮
{% endembed %}

将提示您输入您的主密码以继续。

5、使用您的验证器应用程序扫描 QR 码。

如果您的移动设备上还未安装验证器应用程序，下载一个并扫描 QR 码。我们建议使用 [Authy](https://authy.com/)。

6、扫描后，您的验证器应用程序将返回一个 6 位数的验证码。将此代码输入您的网页密码库对话框并单击**启用**按钮。

一个绿色的 `已启用` 消息表明验证器应用的两步登录已被启用。

7、单击**关闭**按钮，并确认**验证器应用**选项现在已被启用（通过一个绿色勾号 **✔️** 指示）。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，你应该注销所有的 Bitwarden 应用程序，以为每个应用程序立即激活两步登录。您最终会被自动注销。
{% endhint %}

## 使用验证器 <a href="#use-an-authenticator" id="use-an-authenticator"></a>

以下内容假设**验证器**是您[已启用的最高优先级方式](../two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用两步登录访问您的密码库：

1、在任一个 Bitwarden 应用程序上输入您的电子邮件地址和主密码以登录密码库。\
将提示您**输入来自您的验证器应用程序的 6 位验证码**。

2、打开您的验证器应用程序并找到用于您的 Bitwarden 密码库的 6 位验证码。在密码库登录界面输入此代码。通常，验证码每 30 秒会更新一次。

{% hint style="info" %}
勾选**记住我**方框，以记住您的设备，为期30天。记住你的设备意味着你不会被要求完成两步登陆步骤。
{% endhint %}

3、选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../your-vault/vault-timeout-options.md)。

# 两步登录-YubiKey

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-yubikey/)
{% endhint %}

[YubiKey](https://www.yubico.com/) 方式的两步登录适用于高级用户，包括付费组织（家庭、团队或企业）的成员。

可以使用任何[支持 OTP 功能的 YubiKey](https://www.yubico.com/products/yubikey-hardware/compare-yubikeys/) ，包括所有 YubiKey 4 和 5 系列设备以及 YubiKey NEO 和 YubiKey NFC。最多可以添加 5 个 YubiKey 到您的账户中。

{% hint style="success" %}
大多数现代 YubiKeys，包括 5 系列钥匙，都支持 FIDO2 WebAuthn 协议。如果您的密钥支持它，我们建议按照[这些说明](two-step-login-via-fido2-webauthn.md)将您的密钥设置为 FIDO2 WebAuthn 设备。您可以使用 [YubiKey Manager](https://www.yubico.com/support/download/yubikey-manager/) 应用程序来检测是否支持 FIDO2 WebAuthn。
{% endhint %}

## 设置 YubiKey <a href="#setup-yubikey" id="setup-yubikey"></a>

要启用 YubiKey 方式的两步登录：

{% hint style="warning" %}
**丢失对您的 YubiKey 的访问会永久性将您锁定在您的账户之外**。除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。
{% endhint %}

1、登录您的[网页密码库](https://vault.bitwarden.com/)。

2、选择个人资料图标并然后下拉列表中选择**账户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?eu=8adb56b0eaccf885076fa2d66f746161e56956aaac0032d43465b6f94bfe9b8e71fa1151289528b0796d528bd7e816bc31c67d691befd18991bc4af4be3da80d07835fb836b07807052ec4fde4a1574d60c11b5fa8d1c90ca76a21ddb4b4e47711571b23ae7ebbd7e8fa3064badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec3226050d762c882bfad0bb5137732f072e7fc6d45fae7e91b13f4934705f0c03a5673a8555fb3863c7b0aef509da7e7ee7fdc06073d0cab1e3be58f97f2888ac7ff6c654780e0fae0eadb966f6d10b574aee2bfa8b4fb61d04352ff36197647e8e&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A24%3A03.707Z" %}
账户设置
{% endembed %}

3、选择**安全**页面和**两步登录**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/825426d227e1afce2f4b644e6a3e9e84/3cbf2a88c5de2a53993ef05ef68dd09e/Screen%20Shot%202022-05-16%20at%2011.13.53%20AM.webp?eu=d68c06e6e6c9fcd5083ba2d73a7b663de43a51fffd5731d03c63e2a846feccd577a24b5776c17fe72a3b0f88d4e942b961937f6319ef86dfc7ba19f0eb30fb5906d00beb6deb34431168cee1afac5b143f935946f2c79e59e02e2790a6ade9255d4f1b69f629fedbedff3d39f784303098f5dd6d6dc1fc7cb34f0727ae5f39aa66eac4d63001edcbb549e7b7e8ae0b9fcee67f5341d2f3377670191f5feb7cbca0b40325312d5f38668cfa0d990ef5ee63580e215e5d01ea673fcd54fd0360878bfaa043d87965e4aba6400d9883f0d7&a=w%3D779%26h%3D301%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.371Z" %}
两步登录
{% endembed %}

4、定位到 **YubiKey 安全钥匙**选项然后选择**管理**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/9a6ae5639d1ea970b340b832bb3c142b/9cd93fc2542897e9860b9a4630f212f1/twostep-options-yubioverlay.webp?eu=dddc57b2b1ccae850969a58261716561b13704f9f70433866b65b0fc1bad9b802df51b5d20942fe2793f0cdd87b314bb6ec571624cbdd8d2c8b54efcbf31fc5c05d10cef36e17205072cc6fab1a40f4061ce1e5da18ac05baa6c74dce3e1e4234d541423a222fcc5acea3f7bafda7263bde3e5303686fd29a3510b1088062fa920a4979c6d4da894b149e7bba9ae16cec1a56d4f13ac9a342a014d4305af5ec0ece965786c36460a3cc9a60dc468c3e03f1e62245c5802f361698603ae6c3697b5ffa95cdb7964a5ef967234d383b3dfad5ef57528a4d26eecd062254858ee4ffcf565b78c33&a=w%3D754%26h%3D391%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A14%3A58.074Z" %}
选择管理按钮
{% endembed %}

将提示您输入主密码以继续。

5、将 YubiKey 插入计算机的 USB 端口。

6、在您的网页密码库对话框中选择第一个空白的 Yubikey 输入字段。

7、触摸 YubiKey 上的按钮。

如果您要在支持 NFC 的移动设备上使用 Yubikey，请勾选**我的钥匙之一支持 NFC** 复选框。

8、选择**保存**按钮。一个绿色的 `已启用` 消息表明已成功启用 FIDO U2F 的两步登录。

9、选择**关闭**按钮，并确认 **YubiKey OPT 安全钥匙**选项现在已启用（通过一个绿色的勾号 **✔️** 指示）。

重复此过程以向您的账户中添加最多 5 个 YubiKey。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，你应该注销所有的 Bitwarden 应用程序，以为每个应用程序立即激活两步登录。您最终会被自动注销。
{% endhint %}

## 自托管设置 <a href="#self-hosted-setup" id="self-hosted-setup"></a>

如果您是组织管理员，则需要在 `global.override.env` 中配置一对环境变量，以允许调用 YubiKey OTP API：

| globalSettings\_\_yubico\_\_clientId | <p>使用从 Yubico 钥匙收到的 ID 替换这个值。</p><p>在<a href="https://upgrade.yubico.com/getapikey/">此处</a>注册 Yubico 密钥。</p> |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| globalSettings\_\_yubico\_\_key      | 输入从 Yubico 收到的键值。                                                                                            |

## 使用 YubiKey <a href="#use-yubikey" id="use-yubikey"></a>

以下内容假设 **YubiKey** 是您[已启用的最高优先级方式](../two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用两步登录访问您的密码库：

1、在任一个 Bitwarden 应用程序中输入您的电子邮件地址和主密码登录密码库。

系统将提示您将 YubiKey 插入计算机的 USB 端口，或将 YubiKey 靠近支持 NFC 的设备背面：

{% embed url="https://bitwarden.com/_gatsby/image/9392233faa5b11af6693f99e90c1b9e5/6a8fb0f3170a253b814eb0085de74ee9/using-yubi.webp?eu=8eda01b7e3ceadd50e3aa6806d7b696fe43c56aeaa513e846830e3a84ea09f8f22a64d5774957db225690fd6d7b24aba62c72e631be8d3da92be11f3bb60aa5907875de667b425525b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b9293f9bf038a2643800c87013a41bccf2ad4f5c9ba7d400bcb4b8ff0bcccfe7290112dba76076234d1a09b97feaadb052703978450836cfb01d8438c8e121552471074143a930&a=w%3D850%26h%3D571%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A14%3A29.733Z" %}
YubiKey 提示
{% endembed %}

{% hint style="info" %}
勾选**记住我**方框，以记住您的设备，为期30天。记住你的设备意味着你不会被要求完成两步登陆步骤。
{% endhint %}

**如果您在移动设备上使用的是非 NFC 的 YubiKey：**

1. 将 YubiKey 插入设备。
2. 点击**取消**以结束 NFC 提示。
3. 点击用灰色下划线表示的文本输入字段
4. 点击或按下您 YubiKey 上的按钮以插入代码

2、点击或选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../your-vault/vault-timeout-options.md)。

## NFC 故障排除 <a href="#nfc-troubleshooting" id="nfc-troubleshooting"></a>

如果您的 YubiKey 的 NFC 功能无法正常使用：

**检查 NFC 是否已启用：**

1. 下载 [YubiKey Manager](https://www.yubico.com/products/services-software/download/yubikey-manager/)
2. 将 YubiKey 插入设备
3. 选择 **Interface** 选项卡，然后检查 NFC 部分中的所有复选框是否都已选中

**检查 NFC 的配置是否正确：**

1. 下载 [YubiKey Personalization Tool](https://www.yubico.com/products/services-software/download/yubikey-personalization-tools/)
2. 将 YubiKey 插入设备
3. 选择 **Tools** 选项卡
4. 选择 **NDEF Programming** 按钮
5. 选择您希望 YubiKey 在 NFC 上使用的配置插槽
6. 选择 **Program** 按钮。

（**仅 Android）检查如下项目：**

1. 在设置过程中勾选了**我的钥匙之一支持 NFC** 复选框。
2. 您的 Android 设备支持 [NFC](https://en.wikipedia.org/wiki/List\_of\_NFC-enabled\_mobile\_devices)，并且[很确定](https://forum.yubico.com/viewtopic1c5f.html?f=26\&t=1302)地可以与 YubiKey NEO 或 YubiKey 5 NFC 一起正常使用。
3. 您已在 Android 设备上启用了 NFC（**设置** → **更多**）。
4. 您的键盘布局/格式/模式已设置为 QWERTY。

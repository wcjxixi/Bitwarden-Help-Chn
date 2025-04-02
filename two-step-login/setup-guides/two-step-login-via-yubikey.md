# 两步登录 - YubiKey

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-yubikey/)
{% endhint %}

[YubiKey](https://www.yubico.com/) 方式的两步登录适用于高级用户，包括付费组织（家庭、团队或企业）的成员。

可以使用任何[支持 OTP 功能的 YubiKey](https://www.yubico.com/products/yubikey-hardware/compare-yubikeys/) ，包括所有 YubiKey 4 和 5 系列设备以及 YubiKey NEO 和 YubiKey NFC。最多可以添加 5 个 YubiKey 到您的账户中。

{% hint style="success" %}
大多数现代 YubiKeys，包括 5 系列钥匙，都支持 FIDO2 WebAuthn 协议。如果您的密钥支持它，我们建议按照[这些说明](../../my-account/two-step-login/setup-guides/two-step-login-via-fido.md)将您的密钥设置为 FIDO2 WebAuthn 设备。您可以使用 [YubiKey Manager](https://www.yubico.com/support/download/yubikey-manager/) 应用程序来检测是否支持 FIDO2 WebAuthn。
{% endhint %}

## 设置 YubiKey <a href="#setup-yubikey" id="setup-yubikey"></a>

要启用 YubiKey 方式的两步登录：

{% hint style="warning" %}
**丢失对两步登录设备的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。此外，用户还可以创建 Bitwarden [导出](../../import-export/export-vault-data.md)来备份密码库数据。
{% endhint %}

1、登录您的网页 App。

2、从导航选择**设置** → **安全** → **两步登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2BsKs83g4cmiCUwxf2ad83/b2a90e85355f3d937aeb46139203737e/2024-12-02_10-54-31.png?_a=DAJCwlWIZAAB" %}
两步登录
{% endembed %}

3、定位到 **YubiKey 安全钥匙**选项然后选择**管理**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5GqQynIX94PhzJQ0tVW1aE/5dcea8d04c8a543daa7f96989f220756/2024-12-02_10-55-22.png?_a=DAJCwlWIZAAB" %}
两步登录提供程序
{% endembed %}

将提示您输入您的主密码以继续。

4、将 YubiKey 插入计算机的 USB 端口。

5、在您的网页密码库对话框中选择第一个空白的 Yubikey 输入字段。

6、触摸 YubiKey 上的按钮。

如果您要在支持 NFC 的移动设备上使用 Yubikey，请勾选**我的钥匙之一支持 NFC** 复选框。

7、选择**保存**按钮。一个绿色的 `已启用` 消息表明已成功启用 FIDO U2F 的两步登录。

8、选择**关闭**按钮，并确认 **YubiKey OPT 安全钥匙**选项现在已启用（通过一个绿色的勾号 **✔️** 指示）。

重复此过程以向您的账户中添加最多 5 个 YubiKey。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，您应该注销所有的 Bitwarden App，以为每个 App 立即激活两步登录。您最终会被自动注销。
{% endhint %}

## 自托管设置 <a href="#self-hosted-setup" id="self-hosted-setup"></a>

如果您是组织管理员，则需要在 `global.override.env` 中配置一对环境变量，以允许调用 YubiKey OTP API：

| globalSettings\_\_yubico\_\_clientId | <p>使用从 Yubico 钥匙获取的 ID 替换这个值。</p><p>在<a href="https://upgrade.yubico.com/getapikey/">此处</a>注册 Yubico 密钥。</p> |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| globalSettings\_\_yubico\_\_key      | 输入从 Yubico 获取的键值。                                                                                            |

## 使用 YubiKey <a href="#use-yubikey" id="use-yubikey"></a>

以下内容假设 **YubiKey** 是您[已启用的最高优先级方式](../two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用 YubiKey 访问您的密码库：

1、在任一个 Bitwarden App 中输入您的电子邮件地址和主密码登录您的密码库。

系统将提示您将 YubiKey 插入计算机的 USB 端口，或将 YubiKey 靠近支持 NFC 的设备背面：

{% embed url="https://bitwarden.com/_gatsby/image/9392233faa5b11af6693f99e90c1b9e5/6a8fb0f3170a253b814eb0085de74ee9/using-yubi.webp?eu=8eda01b7e3ceadd50e3aa6806d7b696fe43c56aeaa513e846830e3a84ea09f8f22a64d5774957db225690fd6d7b24aba62c72e631be8d3da92be11f3bb60aa5907875de667b425525b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b9293f9bf038a2643800c87013a41bccf2ad4f5c9ba7d400bcb4b8ff0bcccfe7290112dba76076234d1a09b97feaadb052703978450836cfb01d8438c8e121552471074143a930&a=w%3D850%26h%3D571%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A14%3A29.733Z" %}
YubiKey 提示
{% endembed %}

{% hint style="success" %}
勾选**记住我**复选框，以记住您的设备，有效期 30 天。记住您的设备意味着您不会被要求完成两步登陆步骤。
{% endhint %}

**如果您在移动设备上使用的是非 NFC 的 YubiKey：**

1. 将 YubiKey 插入设备。
2. 点击**取消**以结束 NFC 提示。
3. 点击用灰色下划线表示的文本输入字段
4. 点击或按下您 YubiKey 上的按钮以插入代码

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/0SakpfPW6yFdTU34AHxNu/431a5a859949f5d8da8e1a64e0072291/nonfc.png?_a=DAJCwlWIZAAB" %}
取消 NFC
{% endembed %}

2、点击或选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../your-vault/vault-timeout-options.md)。

## NFC 故障排除 <a href="#nfc-troubleshooting" id="nfc-troubleshooting"></a>

如果您的 YubiKey 的 NFC 功能无法正常使用：

**检查 NFC 是否已启用：**

1. 下载 [YubiKey Manager](https://www.yubico.com/products/services-software/download/yubikey-manager/)。
2. 将 YubiKey 插入设备。
3. 选择 **Interface** 选项卡，然后检查 NFC 部分中的所有复选框是否都已选中。

**检查 NFC 配置是否正确：**

1. 下载 [YubiKey Personalization Tool](https://www.yubico.com/products/services-software/download/yubikey-personalization-tools/)。
2. 将 YubiKey 插入设备。
3. 选择 **Tools** 选项卡。
4. 选择 **NDEF Programming** 按钮。
5. 选择您希望 YubiKey 在 NFC 上使用的配置插槽。
6. 选择 **Program** 按钮。

（**仅 Android）检查如下项目：**

1. 在设置过程中勾选了**我的钥匙之一支持 NFC** 复选框。
2. 您的 Android 设备支持 [NFC](https://en.wikipedia.org/wiki/List_of_NFC-enabled_mobile_devices)，并且[很确定](https://forum.yubico.com/viewtopic1c5f.html?f=26\&t=1302)地可以与 YubiKey NEO 或 YubiKey 5 NFC 一起正常使用。
3. 您已在 Android 设备上启用了 NFC（**设置** → **更多**）。
4. 您的键盘布局/格式/模式已设置为 QWERTY。

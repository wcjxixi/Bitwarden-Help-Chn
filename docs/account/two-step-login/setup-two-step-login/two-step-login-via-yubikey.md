# 两步登录 - YubiKey OTP

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-yubikey/)
{% endhint %}

YubiKey OTP 方式的两步登录适用于高级用户，包括付费组织（家庭版、团队版或企业版）的成员。可以使用任何[支持 OTP 功能的 YubiKey](https://www.yubico.com/products/yubikey-hardware/compare-yubikeys/) ，包括所有 YubiKey 4 和 5 系列设备以及 YubiKey NEO 和 YubiKey NFC。最多可以添加 5 个 YubiKey 到您的账户中。

{% hint style="success" %}
大多数现代 YubiKey，包括 5 系列钥匙，都支持 FIDO2 WebAuthn 协议。如果您的钥匙支持（可以使用 [Yubico Authenticator](https://www.yubico.com/products/yubico-authenticator/) 桌面应用程序来检测），我们建议按照[这些说明](two-step-login-via-fido.md)将您的钥匙设置为 FIDO2 WebAuthn 设备。
{% endhint %}

## 设置 YubiKey <a href="#setup-yubikey" id="setup-yubikey"></a>

要启用 YubiKey 方式的两步登录：

{% hint style="danger" %}
**丢失对两步登录设备的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。此外，用户还可以创建 Bitwarden [导出](../../../password-manager/import-and-export/export-vault-data.md)来备份密码库数据。
{% endhint %}

1、登录到 Bitwarden 网页 App。

2、从导航选择**设置** → **安全** → **两步登录**：

{% embed url="https://bitwarden.com/assets/2IjxRoQwl1powHRhah6Bq/39067a5fe6c53732054f323e4afb431b/Screenshot_2025-12-31_at_1.52.00%C3%A2__PM.png?w=1200&fm=avif" %}
两步登录设置
{% endembed %}

3、定位到 **YubiKey OTP 安全密钥**选项然后选择**管理**按钮。将提示您输入您的主密码以继续。

4、将 YubiKey 插入计算机的 USB 端口。

5、在您的网页密码库对话框中选择第一个空白的 Yubikey 输入字段。

6、触摸 YubiKey 上的按钮。

7、（可选）如果您要在支持 NFC 的移动设备上使用 Yubikey，请勾选**我的某个密钥支持 NFC** 复选框。

8、选择**保存**按钮。一个绿色的 `已启用` 消息表明已成功启用 YubiKey 两步登录。

9、选择**关闭**按钮，并确认 **YubiKey OPT 安全密钥**选项现在已启用（通过一个绿色的勾号 **✔️** 指示）。

重复此过程以向您的账户中添加最多 5 个 YubiKey。

{% hint style="info" %}
我们建议在继续测试两步登录之前，将活动的网页密码库选项卡保持为打开状态，以防配置错误。确认其正常工作后，请注销所有的 Bitwarden App，以要求每个 App 使用两步登录。您最终会被自动注销。
{% endhint %}

## 自托管设置 <a href="#self-hosted-setup" id="self-hosted-setup"></a>

如果您是组织管理员，则需要在 `global.override.env` 中配置一对环境变量，以允许调用 YubiKey OTP API：

| globalSettings\_\_yubico\_\_clientId | <p>使用从您的 Yubico 钥匙获取的 ID 替换这个值。</p><p>在<a href="https://upgrade.yubico.com/getapikey/">此处</a>注册 Yubico 密钥。</p> |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| globalSettings\_\_yubico\_\_key      | 输入从 Yubico 获取的密钥的值。                                                                                            |

## 使用 YubiKey <a href="#use-yubikey" id="use-yubikey"></a>

以下内容假设 **YubiKey** 是您[已启用的最高优先级方式](two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用 YubiKey 访问您的密码库：

1、使用您的电子邮箱地址和主密码登录您的 Bitwarden 密码库。

2、当出现提示时，将您的 YubiKey 插入计算机的 USB 端口，或将 YubiKey 靠近启用了 NFC 的设备背面：

{% embed url="https://bitwarden.com/assets/7jikprFVd3XRhOGRCLrEYT/82b0a7332797a1c6ee6add081ea40ab9/2025-03-25_10-15-37.png?w=874&fm=avif" %}
YubiKey 提示
{% endembed %}

{% hint style="success" %}
勾选**记住我**复选框，以记住您的设备，有效期 30 天。选择此选项意味着在此期间您无需完成两步登录步骤。
{% endhint %}

3、如果您在移动设备上使用的是**非 NFC** 的 YubiKey：

1. 将 YubiKey 插入设备。
2. 点击**取消**以结束 NFC 提示。
3. 点击用灰色下划线表示的文本输入字段。
4. 点击或按下您 YubiKey 上的按钮以插入代码。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/0SakpfPW6yFdTU34AHxNu/431a5a859949f5d8da8e1a64e0072291/nonfc.png?_a=DAJCwlWIZAAB" %}
取消 NFC
{% endembed %}

4、点击或选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../log-in-and-unlock/vault-timeout-options.md)。

## NFC 故障排除 <a href="#nfc-troubleshooting" id="nfc-troubleshooting"></a>

如果您的 YubiKey 的 NFC 功能无法正常使用：

**检查 NFC 是否已启用：**

1. 下载 [Yubico Authenticator](https://www.yubico.com/products/yubico-authenticator/)。
2. 将 YubiKey 插入设备。
3. 在 Yubico Authenticator 中打开钥匙然后选择 **Toggle applications**。
4. 为您的密钥启用可用的所有 NFC 选项。如果没有列出 NFC 选项，则您的密钥可能不支持 NFC。

**检查 NFC 配置是否正确：**

1. 下载 [YubiKey Personalization Tool](https://www.yubico.com/products/services-software/download/yubikey-personalization-tools/)。
2. 将 YubiKey 插入设备。
3. 选择 **Tools** 选项卡。
4. 选择 **NDEF Programming** 按钮。
5. 选择您希望 YubiKey 使用 NFC 功能的配置插槽。
6. 选择 **Program** 按钮。

（**仅 Android）检查如下项目：**

* 在设置过程中勾选了**我的某个密钥支持 NFC** 复选框。
* 您的 Android 设备支持 [NFC](https://en.wikipedia.org/wiki/List_of_NFC-enabled_mobile_devices)，并且[已知可以正常与 YubiKey NEO 或 YubiKey 5 NFC 配合使用](https://forum.yubico.com/viewtopic1c5f.html?f=26\&t=1302)。
* 您已在 Android 设备上启用了 NFC 功能（**设置** → **更多**）。
* 您的键盘布局/格式/模式已设置为 QWERTY。

> **\[译者注]**：QWERTY 是一种键盘布局，指的是键盘左上角第一排字母的排列顺序为 `Q W T R E Y`。绝大多数电脑、手机默认都是 QWERTY。大多数国家使用 QWERTY，法国和比利时使用 AZERTY，德国和部分欧洲国家使用 QWERTZ。

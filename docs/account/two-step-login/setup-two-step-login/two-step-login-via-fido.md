# 两步登录 - 通行密钥

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/setup-two-step-login-fido/)
{% endhint %}

> **\[译者注]**：
>
> * **FIDO**：Fast IDentity Online（在线快速身份认证）。FIDO 是一套身份认证框架协议，由 [FIDO 联盟](https://fidoalliance.org/)维护并制定相应的技术规范和标准。
> * [**U2F**](https://zh.wikipedia.org/wiki/%E9%80%9A%E7%94%A8%E7%AC%AC%E4%BA%8C%E5%9B%A0%E7%B4%A0)：Universal 2nd Factor（通用第二因素）。由 [FIDO 联盟](https://fidoalliance.org/)制定的一个开放认证标准，使用专门的 USB 或 NFC 设备来加强并简化双重认证。
> * [**YubiKey**](https://zh.wikipedia.org/wiki/YubiKey)：YubiKey 是由 [Yubico](https://www.yubico.com/) 公司生产的用于身份认证的硬件设备。部分 Yubikey 型号支持 FIDO。其他支持 FIDO 的硬件还有 Google 的 [Titan 安全钥匙](https://cloud.google.com/titan-security-key)、FEITIAN 的[安全钥匙](https://www.ftsafe.com/Products/FIDO)等。

所有 Bitwarden 用户均可免费使用 FIDO2 WebAuthn 凭据进行两步登录。

> **\[译者注]**：2023.9.0 之前，FIDO2 WebAuthn 方式的两步登录适用于高级用户，包括付费组织（家庭、团队或企业）的成员，不适用于免费用户。

可以使用任何经过 FIDO2 WebAuthn 认证的验证器，包括 [YubiKey](https://www.yubico.com/)、[SoloKeys](https://solokeys.com/)、[Google Titan](https://store.google.com/product/titan_security_key)、[Nitrokey](https://www.nitrokey.com/) 等安全密钥，以及 Windows Hello 和 Touch ID 等原生生物识别选项。

{% hint style="success" %}
所有通过 Bitwarden 设置的新 FIDO 密钥都会注册为 WebAuthn 密钥。如果您已注册的 FIDO 密钥在网页 App 的两步登录 → 管理 FIDO2 WebAuthn 视图中被标记为（**迁移自 FIDO**），则说明该密钥为 U2F 密钥，应将其删除并重新注册，以便自动将该密钥设置为 WebAuthn 密钥。Bitwarden 将于 2025 年开始逐步停止对（**迁移自 FIDO**）U2F 密钥的支持。
{% endhint %}

FIDO2 WebAuthn 与大多数 Bitwarden 应用程序兼容。如果您想要使用不支持 FIDO2 WebAuthn 的应用程序版本，请确保您开启了其他两步登录方式。支持的应用程序包括：

* 具有[支持 FIDO2](https://fidoalliance.org/fido2/fido2-web-authentication-webauthn/) 的浏览器的设备上的**网页密码库**
* [支持 FIDO2](https://fidoalliance.org/fido2/fido2-web-authentication-webauthn/) 的浏览器上的**浏览器扩展**
* 具有[支持 FIDO2](https://fidoalliance.org/fido2/fido2-web-authentication-webauthn/) 的浏览器的 Android 和 iOS 13.3+ 上的**移动 App**
* macOS 和 Windows 10+ 上的**桌面 App**

## 设置 FIDO2 WebAuthn <a href="#setup-fido-2-webauthn" id="setup-fido-2-webauthn"></a>

要启用 FIDO2 WebAuthn 方式的两步登录：

{% hint style="danger" %}
**丢失对两步登录设备的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。此外，用户还可以创建 Bitwarden [导出](../../../password-manager/import-and-export/export-vault-data.md)来备份密码库数据。
{% endhint %}

1、登录到 Bitwarden 网页 App。

2、从导航选择**设置** → **安全** → **两步登录**：

{% embed url="https://bitwarden.com/assets/2IjxRoQwl1powHRhah6Bq/39067a5fe6c53732054f323e4afb431b/Screenshot_2025-12-31_at_1.52.00%C3%A2__PM.png?w=1200&fm=avif" %}
两步登录设置
{% endembed %}

3、定位到**通行密钥**选项然后选择**管理**按钮。将提示您输入您的主密码以继续。

4、给您的安全密钥起一个友好的**名称**。

5、将安全密钥插入设备的 USB 端口，然后选择**读取密钥**。如果安全密钥具有按钮，请触摸它。

{% hint style="info" %}
某些设备（包括支持通行密钥的 Windows Hello 或 macOS 设备）是原生 FIDO2 身份验证器，它们将默认提供这些选项。如果您想注册安全密钥或其他验证器，您可能需要选择**尝试另一种方式**、**其他选项**或**取消**按钮以打开其他选项。
{% endhint %}

6、选择**保存**按钮。一个绿色的 `已启用` 消息表明已成功启用了 FIDO2 WebAuthn 方式的两步登录，并且您的密钥旁边将显示绿色的勾号 **✔️**。

7、选择**关闭**按钮，并确认 **FIDO2 WebAuthn** 选项现在已启用（通过一个绿色的勾号 **✔️** 指示）。

重复此过程以向您的账户中添加最多 5 个 FIDO2 WebAuthn 安全密钥。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，您应该注销所有的 Bitwarden App，以为每个 App 立即激活两步登录。您最终会被自动注销。
{% endhint %}

## 使用 FIDO2 WebAuthn <a href="#use-fido-2-webauthn" id="use-fido-2-webauthn"></a>

以下内容假设 **FIDO 2 WebAuthn** 是您[已启用的最高优先级方式](two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用FIDO2 WebAuthn 设备访问您的密码库：

1、输入您的电子邮箱地址和主密码登录您的 Bitwarden 密码库。

2、系统会提示您读取安全密钥，例如将安全密钥插入设备的 USB 端口并轻按按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3RuttlEwwfVX3UJKA8GTFg/ab7e0ba835a7f42ea3f10369cb66c008/2025-03-25_10-28-20.png?_a=DAJCwlWIZAAB" %}
FIDO2 提示
{% endembed %}

{% hint style="success" %}
勾选**记住我**复选框，以记住您的设备，有效期 30 天。选择此选项意味着在此期间您无需完成两步登录步骤。
{% endhint %}

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../log-in-and-unlock/vault-timeout-options.md)。

## NFC 故障排除 <a href="#nfc-troubleshooting" id="nfc-troubleshooting"></a>

{% hint style="success" %}
硬件安全密钥通常有一个物理插头，在 NFC 识别困难的情况下会更可靠地工作。
{% endhint %}

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

* 在设置过程中勾选了**我的钥匙之一支持 NFC** 复选框。
* 您的 Android 设备支持 [NFC](https://en.wikipedia.org/wiki/List_of_NFC-enabled_mobile_devices)，并且[很确定](https://forum.yubico.com/viewtopic1c5f.html?f=26\&t=1302)地可以与 YubiKey NEO 或 YubiKey 5 NFC 一起正常使用。
* 您已在 Android 设备上启用了 NFC（**设置** → **更多**）。
* 您的键盘布局/格式/模式已设置为 QWERTY。

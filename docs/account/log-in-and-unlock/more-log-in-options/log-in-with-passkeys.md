# 使用通行密钥登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/login-with-passkeys/)
{% endhint %}

{% hint style="success" %}
Bitwarden 同时提供[使用通行密钥登录 Bitwarden](log-in-with-passkeys.md) 和[为其他网站和服务自动填充已存储的通行密钥](../../../password-manager/autofill/more-autofill-options/autofill-passkeys.md)的功能。
{% endhint %}

通行密钥可以作为使用主密码和电子邮箱的替代方式来登录 Bitwarden。用于登录 Bitwarden 的通行密钥：

* 可用于网页 App 和基于 chromium 的浏览器扩展。计划在未来版本中支持其他客户端 App。
* 需要用户验证，这意味着您需要使用生物识别因素或安全密钥等来成功建立对通行密钥的访问。
* 仅当身份验证器（例如 YubiKey 5）和浏览器（例如 Google Chrome）都[支持 PRF](log-in-with-passkeys.md#set-up-encryption) 时，才能解密您的密码库。非 PRF 设置将要求您在登录后输入主密码才能解密您的密码库。
* 使用了[要求 SSO](../../../admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication) 策略的组织成员无法使用[受信任设备 SSO](../../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
* 绕过 Bitwarden 的两步登录。

要了解更多有关通行密钥的基础知识，请查看 [来自 Bitwarden 的这篇博客](https://bitwarden.com/blog/log-into-bitwarden-with-a-passkey/)。

## 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

您最多可以拥有 5 个通行密钥。要创建用于登录 Bitwarden 的通行密钥：

1、在网页 App 中，从导航选择**设置** → **安全**。

2、选择**主密码**选项卡。

3、在**使用通行密钥登录**部分，选择**启用**，或者如果您已经设置了通行密钥，则选择**新增通行密钥**。系统将提示您输入主密码。

4、按照浏览器的提示创建 FIDO2 通行密钥。您可以使用生物识别等因素或创建 PIN 码来完成用户验证。

{% hint style="success" %}
您可能需要取消浏览器希望您使用的默认验证器，例如，如果您想在 macOS 设备上使用硬件安全钥匙，它会优先使用 Touch ID。
{% endhint %}

5、给您您的通行密钥起个**名称**。

6、如果不想将通行密钥用于密码库加密和解密，请取消选中**用于密码库加密**复选框：

{% embed url="https://bitwarden.com/assets/2gsO1o5tDU7s7LXvcpaL7w/56a8a797155760fe6fbd1d2e2d92b59b/2025-12-31_11-19-58.png?w=999&fm=avif" %}
使用通行密钥用于密码库加密
{% endembed %}

仅当您的浏览器（如 Google Chrome）和身份验证器（如 YubiKey 5）都[支持 PRF](log-in-with-passkeys.md#set-up-encryption) 时，才会出现此选项。

7、选择**启用**。

{% hint style="info" %}
Bitwarden 不会提示或允许您在密码库中保存登录 Bitwarden 的通行密钥。这样可以防止出现登录 Bitwarden 需要访问您的密码库的情况。
{% endhint %}

### 设置加密 <a href="#set-up-encryption" id="set-up-encryption"></a>

要支持使用通行密钥进行密码库加密和解密，您的浏览器（例如 Google Chrome）和身份验证器（例如 YubiKey 5）都必须[支持 PRF](https://bitwarden.com/blog/prf-webauthn-and-its-role-in-passkeys/)。

{% hint style="success" %}
虽然 Google Chrome 支持 PRF，但 Chrome 配置文件不支持作为 PRF 功能的身份验证器。以 YubiKey 5 为反例，YubiKey 5 是一种支持 PRF 身份验证器，而 Firefox 浏览器只能在 Windows 系统上支持 PRF。此外，已知 Windows 10 在支持 PRF 通行密钥方面存在问题。

您所拥有的设备和所处的环境将决定您使用通行密钥进行加密的能力。
{% endhint %}

您的通行密钥列表将显示每个密码是可否用于加密，是否受支持但未启用，或不支持：

{% embed url="https://bitwarden.com/assets/TpXTFNlF2hzRaUaLmxAXr/6710e5ab7c98efcb11547dc6038fdf7d/Passkeys_list.png?w=832&fm=avif" %}
通行密钥列表
{% endembed %}

如果您在最初设置通行密钥时未勾选**用于密码库加密**复选框，或者例如您当时使用的浏览器不支持 PRF，请导航至此菜单然后选择**设置加密**按钮。

### 移除通行密钥 <a href="#remove-a-passkey" id="remove-a-passkey"></a>

您可以使用同一界面上的**移除**按钮从 Bitwarden 中移除现有的通行密钥。从 Bitwarden 中移除通行密钥不会删除存储在 FIDO2 身份验证器中的私钥，但您将无法再使用它登录 Bitwarden。

## 使用通行密钥登录 <a href="#log-in-with-your-passkey" id="log-in-with-your-passkey"></a>

创建了您的通行密钥后，您就可以使用它来登录 Bitwarden 网页 App 和基于 chromium 的浏览器扩展了：

{% hint style="danger" %}
由于已知缺陷，如果您使用的是 Linux，则需要先弹出浏览器扩展，然后才能尝试使用通行密钥登录。

<img src="https://bitwarden.com/assets/1cbJy0jLBmSQmRumvYzVwp/a9e43f4c154686249056924eb3e56323/pop_out_screenshot.png?w=407&#x26;fm=avif" alt="" data-size="original">
{% endhint %}

1. 在 Bitwarden 登录界面，在通常输入电子邮箱地址的地方，选择**使用通行密钥登录**。
2. 按照浏览器的提示读取通行密钥，这将用于验证您与 Bitwarden 的身份。
3. 如果您的通行密钥[设置为用于密码库加密](log-in-with-passkeys.md#set-up-encryption)，那么就完成了！否则，请输入您的主密码然后选择**解锁**以解密您的密码库数据。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

以下内容描述了使用通行密钥进行登录的机制。哪个选项卡与您相关，取决于您的通行密钥是否[设置了加密](log-in-with-passkeys.md#set-up-encryption)。

{% tabs %}
{% tab title="启用了加密的通行密钥" %}
### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

当已注册的通行密钥用于登录 Bitwarden 时：

* 通过 WebAuthn API，验证器生成一个**通行密钥公钥和私钥对**。根据定义，该密钥对构成了您的通行密钥。
* 通过 WebAuthn API PRF 扩展，验证器生成一个 **PRF 对称密钥**。该密钥源自于您的通行密钥的特有的**内部机密**和 Bitwarden 提供的**盐化**。
* Bitwarden 客户端生成一个 **PRF 公钥和私钥对**。PRF 公钥对您的**账户加密密钥**进行加密，您的客户端可以通过登录和解锁来访问该密钥，然后将生成的 **PRF 加密的账户加密密钥**发送到服务器。
* 使用 **PRF 对称密钥**对 **PRF 私钥**进行加密（参见第 2 步），然后将得到的 **PRF 加密的私钥**发送到服务器。
* 您的客户端将数据发送到 Bitwarden 服务器，以用于为您的账户创建一个新的通行密钥凭据记录。如果您的通行密钥凭据被注册为支持密码库加密和解密，此记录将包括：
  * 通行密钥名称
  * 通行密钥公钥
  * PRF 公钥
  * PRF 加密的账户加密密钥
  * PRF 加密的私钥

完成身份验证所必需的通行密钥私钥只会以加密格式保留在客户端中。

### 使用通行密钥登录 <a href="#log-in-with-your-passkey" id="log-in-with-your-passkey"></a>

当使用通行密钥登录，特别是解密您的密码库数据时：

* 使用 WebAuthn API 公钥加密技术，您的身份验证请求将被断言和确认。
* 您的 **PRF 加密的账户加密密钥**和 **PRF 加密的私钥**将从服务器发送到您的客户端。
* 使用 Bitwarden 提供的相同**盐化**和您的通行密钥特有的**内部机密**，**PRF 对称密钥**在本地被重新创建。
* **PRF 对称密钥**用于解密您的 **PRF 加密的私钥**，从而生成您的 **PRF 私钥**。
* **PRF 私钥**用于解密您的 **PRF 加密的账户加密密钥**，从而得到您的**账户加密密钥**。您的账户加密密钥用于解密您的密码库数据。
{% endtab %}

{% tab title="停用了加密的通行密钥" %}
### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

当已注册的通行密钥用于登录 Bitwarden 时：

1. 创建**通行密钥公钥和私钥对**。根据定义，该密钥对构成了您的通行密钥。
2. 您的客户端将数据发送到 Bitwarden 服务器，以用于为您的账户创建一个新的通行密钥凭据记录。如果您的通行密钥凭据未被注册为支持密码库加密和解密，此记录将包括：
   * 通行密钥名称
   * 通行密钥公钥

完成身份验证所需的通行密钥私钥只会以加密格式保留在客户端中。

### 使用通行密钥登录 <a href="#log-in-with-your-passkey" id="log-in-with-your-passkey"></a>

当使用通行密钥登录时，您的身份验证请求将使用 WebAuthn API 公钥加密技术进行断言和确认。然后，您需要使用主密码解密您的密码库。
{% endtab %}
{% endtabs %}

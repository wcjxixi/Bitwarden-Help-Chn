# 使用通行密钥登录 & 解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/login-with-passkeys/)
{% endhint %}

{% hint style="info" %}
Bitwarden 提供三种通行密钥功能：[使用通行密钥登录和解锁](log-in-with-passkeys.md#log-in-and-unlock-with-your-passkey)您的 Bitwarden 账户、在您的 Bitwarden 账户上使用[通行密钥 2FA](../../two-step-login/setup-two-step-login/two-step-login-via-fido.md)，以及为其他网站和服务[自动填充已存储的通行密钥](../../../password-manager/autofill/more-autofill-options/autofill-passkeys.md)。
{% endhint %}

通行密钥为您的 Bitwarden 账户提供安全身份验证。使用它们登录，并通过[支持 PRF 的设置](log-in-with-passkeys.md#unlock-vault-requirements)自动[解锁您的密码库](../understand-log-in-vs-unlock.md)，而无需输入主密码。通行密钥绕过两步登录，为传统的基于密码的身份验证提供了简化的替代方案。

## 要求 <a href="#requirements" id="requirements"></a>

目前，这些 Bitwarden App 支持使用通行密钥登录和解锁您的 Bitwarden 账户：

* 基于 Chromium 的浏览器中的浏览器扩展
* 网页 App

{% hint style="info" %}
在 macOS 上，创建和使用支持 PRF 的通行密钥来解锁您的密码库需要基于 Chromium 的浏览器。
{% endhint %}

用于登录 Bitwarden 的通行密钥需要用户验证，例如生物识别或安全密钥来验证和使用您的通行密钥。

### 解锁密码库要求 <a href="#unlock-vault-requirements" id="unlock-vault-requirements"></a>

要使用通行密钥解密并解锁您的密码库，您需要为该通行密钥[设置加密](log-in-with-passkeys.md#set-up-encryption-for-unlock)。您的浏览器（例如 Google Chrome）和身份验证器（例如 YubiKey 5）都必须同时[支持 PRF](https://bitwarden.com/blog/prf-webauthn-and-its-role-in-passkeys/) 才能使用此解锁方式。如果其中任何一个不支持 PRF，您需要使用其他解锁方式，例如您的主密码或 PIN 码。

**​​PRF 功能因设备和环境而异**。例如，Google Chrome 支持 PRF，但 Chrome 配置文件不支持。YubiKey 5 是一款支持 PRF 的身份验证器。此外，已知 Windows 10 与支持 PRF 的通行密钥存在兼容性问题。

### 通行密钥限制 <a href="#passkey-restrictions" id="passkey-restrictions"></a>

如果您所在的组织使用了[要求 SSO](../../../admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication) 策略、使用[受信任设备 SSO](../../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)，则无法在 Bitwarden 中使用通行密钥。

Bitwarden 不会提示或允许您保存用于登录任何 Bitwarden 账户的通行密钥。这避免了需要访问您的密码库才能登录到同一个密码库的循环问题。

## 管理通行密钥 <a href="#manage-passkeys" id="manage-passkeys"></a>

使用网页 App 创建、更新和删除用于访问您的 Bitwarden 账户的通行密钥。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

您最多可以添加 5 个通行密钥到您的 Bitwarden 账户。要创建用于登录 Bitwarden 的通行密钥：

1、在网页 App 中，转到**设置** → **安全**。

2、选择**主密码**。

3、在**使用通行密钥登录**部分，选择**启用**，或者如果您已经设置了通行密钥，则选择**新增通行密钥**。系统将提示您输入主密码。

4、按照浏览器的提示创建 FIDO2 通行密钥。您可以使用生物识别等因素或通过创建 PIN 码来完成用户验证。

{% hint style="success" %}
您可能需要取消浏览器希望您使用的默认验证器，例如，如果您想在 macOS 设备上使用硬件安全钥匙，它会优先使用 Touch ID。
{% endhint %}

5、输入您的通行密钥的**名称**。

6、（可选）如果您的[浏览器和身份验证器支持 PRF](log-in-with-passkeys.md#unlock-vault-requirements)，则**用于密码库加密**设置默认会被选中。这允许使用您的通行密钥解密和解锁您的密码库。如果不想将通行密钥用于密码库解锁，请取消选中此选项：

{% embed url="https://bitwarden.com/assets/2gsO1o5tDU7s7LXvcpaL7w/56a8a797155760fe6fbd1d2e2d92b59b/2025-12-31_11-19-58.png?w=999&fm=avif" %}
使用通行密钥用于密码库加密
{% endembed %}

7、选择**启用**。

### 设置加密用于解锁 <a href="#set-up-encryption-for-unlock" id="set-up-encryption-for-unlock"></a>

如果您的[浏览器和身份验证器支持 PRF](log-in-with-passkeys.md#unlock-vault-requirements)，您可以使用通行密钥解密和解锁您的密码库。有两种方法可以做到这一点：

* 创建通行密钥时，请选中**用于密码库加密**设置（[步骤 6](log-in-with-passkeys.md#create-a-passkey)）。
* 对于现有的通行密钥，请转至**设置** → **安全** → **主密码**，然后选择通行密钥旁边的**设置加密**：

{% embed url="https://bitwarden.com/assets/TpXTFNlF2hzRaUaLmxAXr/6710e5ab7c98efcb11547dc6038fdf7d/Passkeys_list.png?w=832&fm=avif" %}
通行密钥列表
{% endembed %}

您的通行密钥列表显示了每个通行密钥的加密状态：**用于加密**、支持但未激活（**设置加密**）或**不支持加密**。

### 移除通行密钥 <a href="#remove-a-passkey" id="remove-a-passkey"></a>

要从 Bitwarden 账户中删除通行密钥，请转到**设置** → **安全** → **主密码**，然后选择通行密钥旁边的**移除**。这将断开通行密钥与 Bitwarden 的连接，但私钥仍将保留在您的 FIDO2 身份验证器中。

## 使用通行密钥登录和解锁 <a href="#log-in-and-unlock-with-your-passkey" id="log-in-and-unlock-with-your-passkey"></a>

创建了通行密钥后，您就可以将其使用于 Bitwarden 网页 App 和基于 Chromium 的浏览器扩展了。对于 macOS 上支持 PRF 的通行密钥，您需要使用基于 Chromium 的浏览器来访问网页 App。

{% hint style="info" %}
如果您要登录 **Linux** 上的浏览​​器扩展，则需要先弹出该扩展，然后再尝试使用通行密钥登录或解锁：

<img src="https://bitwarden.com/assets/1cbJy0jLBmSQmRumvYzVwp/a9e43f4c154686249056924eb3e56323/pop_out_screenshot.png?w=407&#x26;fm=avif" alt="" data-size="original">
{% endhint %}

要使用通行密钥登录和解锁您的密码库：

1. 在 Bitwarden 登录界面，在通常输入电子邮箱地址的地方，选择**使用通行密钥登录**。
2. 按照浏览器的提示读取通行密钥，这将使用 Bitwarden 验证您的身份。
3. 接下来的操作取决于您的通行密钥是否已[设置为用于密码库加密](log-in-with-passkeys.md#set-up-encryption-for-unlock)：
   * 如果您的通行密钥已设置为用于密码库加密，则操作就完成了！通行密钥将用于解密并解锁您的密码库。
   * 如果您的通行密钥未设置为用于密码库加密，请输入您的主密码然后选择**解锁**，或使用您之前已配置的其他解锁方式。

如果您已登录，想要解锁密码库，请在密码库锁定界面选择**使用通行密钥解锁**。按照浏览器提示读取通行密钥。这将解锁您的账户并打开您的密码库。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

使用通行密钥登录的机制取决于您的通行密钥是否[设置为用于加密](log-in-with-passkeys.md#set-up-encryption)。

{% tabs %}
{% tab title="启用了加密的通行密钥" %}
### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

当已注册的通行密钥用于登录 Bitwarden 时：

* 通过 WebAuthn API，验证器生成一个**通行密钥公钥和私钥对**。根据定义，该密钥对构成了您的通行密钥。
* 通过 WebAuthn API PRF 扩展，验证器生成一个 **PRF 对称密钥**。该密钥源自于您的通行密钥的特有的**内部机密**和 Bitwarden 提供的**盐化**。
* Bitwarden 客户端生成一个 **PRF 公钥和私钥对**。PRF 公钥对您的**账户加密密钥**进行加密，您的客户端可以通过登录和解锁来访问该密钥，然后将生成的 **PRF 加密的账户加密密钥**发送到服务器。
* 使用 **PRF 对称密钥**对 **PRF 私钥**进行加密（参见第 2 步），然后将得到的 **PRF 加密的私钥**发送到服务器。
* 您的客户端将数据发送到 Bitwarden 服务器，以用于为您的账户创建一个新的通行密钥凭据记录。如果您的通行密钥凭据被注册为支持密码库加密和解密，此记录将包含：
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

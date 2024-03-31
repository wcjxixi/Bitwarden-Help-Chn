# =通行密钥登录 (Beta)

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/login-with-passkeys/)
{% endhint %}

{% hint style="info" %}
使用通行密钥登录目前尚处于测试阶段。
{% endhint %}

通行密钥可以作为使用主密码和电子邮件的替代方式来登录 Bitwarden。用于登录 Bitwarden 的通行密钥需要用户验证，这意味着您需要使用生物识别因素或安全钥匙等来成功建立对通行密钥的访问。

通行密钥登录可以绕过 Bitwarden 的两步登录，但只有[支持 PRF](https://bitwarden.com/blog/prf-webauthn-and-its-role-in-passkeys/) 的浏览器（例如 Google Chrome）和身份验证器（例如 YubiKey 5）的组合才能用来设置使用通行密钥登录以进行密码库解密。如果不使用 PRF 通行密钥，则需要在登录后输入主密码才能解密密码库。

通行密钥目前可用于登录 Bitwarden 网页应用程序，并计划在未来的版本中支持其他客户端应用程序。

{% hint style="info" %}
使用[要求单点登录身份验证策略](../../organizations/enterprise-policies.md#require-single-sign-on-authentication)、[受信任设备 SSO](../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 或 [Key Connector ](../../login-with-sso/about-key-connector.md)的组织成员无法使用通行密钥登录。
{% endhint %}

## 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

您最多可以拥有 5 个通行密钥。要创建用于登录 Bitwarden 的通行密钥：

1、在 Web 应用程序中选择个人档案图标，然后从下拉菜单中选择**账户设置**。

2、在账户设置菜单中选择**安全**页面然后选择**主密码**选项卡。

3、在**使用通行密钥登录**部分，选择**启用**，或者如果已经设置了通行密钥，则选择**新建通行密钥**。系统将提示您输入主密码：

{% embed url="https://bitwarden.com/_gatsby/image/67e65931420b7935c32d08a54f2c8e24/dc63008adb670b0c8565ed02c8da8576/Screenshot%202023-11-27%20at%202.00.44%20PM.webp?eu=da8f52e7b5ccfb87063bf48669746938b23c50a8f65430846c36e6fc1dae9b8424f04f06769373b92a6c58dd81e443b262c72c624ab8d88cc6ed1ef5e236ae5a508a5dea67e07151072f90a8e5f5054761c44f5ff582c10ba43f20d7b6bbe1791856182ca87bee87baad3465b5852f33e9bea4783794f87eea4a1a108b5b7be37be2cd8f644badd0e35bb9b7adea5c89dff9735204c4f4777c240a4559bb25e6e2b51b70385a201873bbd310c422e2e95d5e1d4a5d2c01843525d453f86d60c3e5f3a358dd7d72e1fecb33258196acd2ee48a92975b5cf24fb8024195d4ff946f3ff23a8960b040e8329e7944daf01025a11c6738b3a20d9265b8868e49c59d376ab&a=w%3D707%26h%3D142%26fm%3Dwebp%26q%3D75&cd=2024-01-10T12%3A38%3A32.442Z" %}
打开通行密钥登录
{% endembed %}

4、按照浏览器的提示创建 FIDO2 通行密钥。您可以使用生物识别等因素或创建 PIN 码来完成用户验证。

在此过程中，您可能需要取消浏览器希望您使用的默认验证器，例如，如果您想在 macOS 设备上使用硬件安全钥匙，它会优先使用 Touch ID。

5、给你您的通行密钥起个**名称**。

6、如果不想将通行密钥用于密码库加密和解密，请取消选中**用于密码库加密**复选框：

{% embed url="https://bitwarden.com/_gatsby/image/5a8a134cdd413fd104cdd7899e3d3da4/21cb5846083657010037ec57cf07aced/Screenshot%202023-11-27%20at%202.03.07%20PM.webp?eu=deda55b4e29aaad50b3ea1d76d266468e53e50afaa5832d93467e4fa48ab968775a51e55769778e77a3a59dfd6e64bba67c179671eebd4dd95b449a6ef61fb0101d20cba66e773540779c0abe3f5544669954f0da6d1c95ba33c7687b6e2b2701c06492ba829ec80e5f86631e3807c61efe0a27a33caaa7eea4a1a108b5b7be37be2cd8f644badd0e35bb9b7adea5c89dff9735204c4f4777c240a4559bb25e6e2b51b736e6a3f5a6acbeb2ca266d5b1407427701e0e7ff02025d850f96c39c0b5fca355d97229e2accc607886c0f8d6e919ae2e72b5c92fa98624195d4ff946f3ff23a8960b040e8329e7944daf01025a11c6738b3a20da265f8b68e49c59d376ab&a=w%3D691%26h%3D385%26fm%3Dwebp%26q%3D75&cd=2024-01-10T12%3A38%3A32.444Z" %}
使用通行密钥用于密码库加密
{% endembed %}

仅当您的浏览器（如 Google Chrome）和身份验证器（如 YubiKey 5）都支持 PRF 功能时，才会出现此选项。[了解更多](log-in-with-passkeys.md#set-up-encryption)。

7、选择**启用**。

### 设置加密 <a href="#set-up-encryption" id="set-up-encryption"></a>

您的浏览器（例如 Google Chrome）和身份验证器（例如 YubiKey 5）都必须[支持 PRF](https://bitwarden.com/blog/prf-webauthn-and-its-role-in-passkeys/)，以便支持使用[密码密钥](https://bitwarden.com/blog/prf-webauthn-and-its-role-in-passkeys/)进行密码库的加密和解密。

{% hint style="success" %}
虽然 Google Chrome 支持 PRF，但 Chrome 配置文件不支持作为 PRF 功能的身份验证器。以 YubiKey 5 为反例，它是一种支持 PRF 身份验证器。

您所拥有的设备和所处的环境将决定您使用通行密钥进行加密的能力。
{% endhint %}

您的通行密钥列表将显示每个密码是否用于加密，是否受支持但未启用，或不支持：



如果您在最初设置通行密钥时未勾选**用于密码库加密**复选框，或者例如您当时使用的浏览器不支持 PRF，请导航至此菜单然后选择**设置加密**按钮。

### 移除通行密钥 <a href="#remove-a-passkey" id="remove-a-passkey"></a>

您可以使用同一界面上的**移除**按钮从 Bitwarden 中移除现有的通行密钥。从 Bitwarden 中移除通行密钥不会删除存储在 FIDO2 身份验证器中的私钥，但您将无法再使用它登录 Bitwarden。

## 使用通行密钥登录 <a href="#log-in-with-your-passkey" id="log-in-with-your-passkey"></a>

创建了您的通行密钥后，您就可以使用它来登录 Bitwarden 网络应用程序了：

1. 在 Bitwarden 登录界面，在通常输入电子邮件地址的地方，选择**使用通行密钥登录**。
2. 按照浏览器的提示读取通行密钥，这将用于验证您与 Bitwarden 的身份。
3. 如果您的通行密钥设置为用于密码库加密，那么就完成了！否则，请输入您的主密码然后选择**解锁**以解密您的密码库数据。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

以下描述了使用通行密钥进行登录的机制。哪个选项卡与您相关，取决于您的通行密钥是否设置了加密。

{% tabs %}
{% tab title="启用了加密的通行密钥" %}
### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

### 使用通行密钥登录 <a href="#log-in-with-your-passkey" id="log-in-with-your-passkey"></a>
{% endtab %}

{% tab title="关闭了加密的通行密钥" %}
### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

### 使用通行密钥登录 <a href="#log-in-with-your-passkey" id="log-in-with-your-passkey"></a>
{% endtab %}
{% endtabs %}

## 轮换加密密钥 <a href="#rotating-your-encryption-key" id="rotating-your-encryption-key"></a>

[轮换您的账户加密密钥](../../security/account-encryption-key.md#rotate-your-encryption-key)将使[设置为用于密码库加密的任何通行密钥](log-in-with-passkeys.md#set-up-encryption)的加密和解密功能失效。在您轮换账户加密密钥时，该通行密钥用于在登录 Bitwarden 时进行身份验证的功能不会受到影响。

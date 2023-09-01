# =关于受信任设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/about-trusted-devices/)
{% endhint %}

受信任设备 SSO 允许用户[使用 SSO 进行身份验证](../../../login-with-sso/about-login-with-sso.md)，并使用设备存储的加密密钥解密其密码库，而无需输入主密码。受信任设备必须在登录尝试前注册，或[通过几种不同的方法获得批准](add-a-trusted-device.md)。

受信任设备 SSO 可为企业终端用户提供零知识和端到端加密的无密码体验。这可以防止用户因忘记主密码而被锁定，让他们享受简化的登录体验。

受信任设备 SSO 适用于云组织，未来版本将支持自托管组织。

## 开始使用受信任设备 <a href="#start-using-trusted-devices" id="start-using-trusted-devices"></a>

要开始使用受信任设备 SSO：

1. 为您的组织[设置受信任设备 SSO](setup-sso-with-trusted-devices.md)。
2. 向管理员提供有关[如何批准设备请求](approve-a-trusted-device.md)的信息。
3. 向最终用户提供有关[如何添加受信任设备](add-a-trusted-device.md)的信息。

## 运行方式 <a href="#how-it-works" id="how-it-works"></a>

{% tabs %}
{% tab title="入职" %}
当新用户加入组织时，将使用组织的公钥对其加密密钥进行加密来创建**账户恢复密钥**（[了解更多](../../../organizations/admin-password-reset.md)）。账户恢复是启用受信任设备 SSO 的先决条件。

然后询问用户是否想要记住或信任此设备。当他们选择这样做时：

1. 客户端生成新的**设备密钥**。该密钥永远不会离开客户端。
2. 客户端生成新的 RSA 密钥对：**设备私钥**和**设备公钥**。
3. 用户的账户加密密钥使用未加密的设备公钥进行加密，并将结果值作为**公钥-已加密的用户密钥**发送到服务器。
4. **设备公钥**使用用户的账户加密密钥进行加密，并将结果值作为**用户密钥-已加密的公钥**发送到服务器。
5. **设备私钥**使用第一设备密钥进行加密，并将所得值作为**设备密钥-已加密的私钥**发送到服务器。

最重要的是，当用户开始登录时，**公钥-已加密的用户密钥**和**设备密钥-已加密的私钥**将从服务器发送到客户端。

如果用户需要轮换其账户加密密钥，将使用**用户密钥-已加密的公钥**。
{% endtab %}

{% tab title="登录" %}

{% endtab %}

{% tab title="批准" %}

{% endtab %}

{% tab title="密钥轮换" %}

{% endtab %}
{% endtabs %}

### 对主密码的影响 <a href="#impact-on-master-passwords" id="impact-on-master-passwords"></a>

### 对其它功能的影响 <a href="#impact-on-other-features" id="impact-on-other-features"></a>

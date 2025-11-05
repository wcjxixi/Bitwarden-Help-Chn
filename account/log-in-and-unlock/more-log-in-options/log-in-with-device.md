# 使用设备登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/log-in-with-device/)
{% endhint %}

虽然大多数人都使用主密码登录他们的 Bitwarden 密码库，但还有一种更方便的方法，叫做无密码验证。使用**设备登录**，当您在一台设备上登录 Bitwarden 时，您可以选择使用另一台已登录的网页 App、移动 App 或桌面 App 来批准这些验证请求，而无需输入主密码。

设备登录可以在网页 App、浏览器扩展、移动 App 或桌面 App 上启动。这些 App 发出的请求可在网页 App、移动 App 或桌面 App 上批准。

[了解我们的零知识加密实施方案](log-in-with-device.md#how-it-works)。

## 准备设备登录 <a href="#prepare-to-log-in-with-a-device" id="prepare-to-log-in-with-a-device"></a>

要设置设备登录：

* 至少正常登录一次发起 App（网页 App、浏览器扩展、桌面或移动 App），以便 Bitwarden 可以识别您的设备。

{% hint style="info" %}
使用隐身模式或隐私浏览会阻止 Bitwarden 注册您的浏览器，因此您将无法在隐私浏览器窗口中使用设备登录。
{% endhint %}

* 在用于批准的 App （网页 App、移动 App 或桌面 App）上拥有认可的账户。要认可该账户，您必须随时已成功登录到该设备。

{% hint style="info" %}
作为企业组织的成员，您需要遵守[要求 SSO 策略](../../../admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)，如果您无法使用**设备登录**选项，则需要改用 [SSO 登录](../using-single-sign-on/using-login-with-sso.md#login-using-sso)。
{% endhint %}

## 使用设备登录 <a href="#logging-in-with-a-device" id="logging-in-with-a-device"></a>

在发起 App 的登录界面，输入您的电子邮箱地址并选择**继续**。然后，选择**使用设备登录**选项：

{% embed url="https://bitwarden.com/assets/7owqaTEe9Bo05wfLRZPhn8/38f1d0334964bb3d98a430b80b9d6b95/2025-09-09_10-03-52.png?w=692&fm=avif" %}
使用设备登录
{% endembed %}

### 批准登录请求 <a href="#approve-a-log-in-request" id="approve-a-log-in-request"></a>

使用**设备登录**会将身份验证请求发送到您当前已登录的 Bitwarden App 以用于批准。

{% tabs %}
{% tab title="移动 App" %}
要使用移动 App 批准请求：

1、在移动 App 中，导航至**设置** → **账户安全** → **待处理的登录请求**：

{% embed url="https://bitwarden.com/assets/1ZB3Pc8T0mlP96W3IZefrR/a22c8efe63a88941bad11a278b1d113d/2025-09-09_09-39-13.png?w=1193&fm=avif" %}
移动端上待处理的登录请求
{% endembed %}

2、定位并点击待处理的设备请求。

3、验证指纹短语然后选择**确认访问**：

{% embed url="https://bitwarden.com/assets/6xeP36n7g2dbwLI9YWjNg4/2aa9fdc96e765e963ee07f38ad0b6c06/2025-09-09_09-39-44.png?w=1192&fm=avif" %}
在移动端上批准登录
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
要使用浏览器扩展批准请求：

1、在浏览器扩展中，等待接收到设备批准请求或导航至**设置** → **账户安全** → **设备**：

{% embed url="https://bitwarden.com/assets/6OZfQt2jDDqa9F0MaUdBUq/1460f0ec04c63ab55da1f5eaf37ca469/2025-09-09_09-49-23.png?w=1190&fm=avif" %}
浏览器扩展上的设备视图
{% endembed %}

2、在**设备**选项卡上，定位并选择待处理的设备请求：

{% embed url="https://bitwarden.com/assets/64f1jZ30In2BbWDEUZVtxO/9de965d59fedca2bad4e325f4181f69a/2025-09-09_09-49-42.png?w=1187&fm=avif" %}
浏览器扩展上的列表
{% endembed %}

3、验证指纹短语然后选择**确认访问**：

{% embed url="https://bitwarden.com/assets/2LFY10MMpI9G0ZcojcXveg/0a891ec5fa8f6052e5804841e7ec7724/2025-09-09_09-48-55.png?w=1193&fm=avif" %}
在浏览器扩展上批准设备
{% endembed %}
{% endtab %}

{% tab title="网页 App" %}
要使用网页 App 批准请求：

{% hint style="info" %}
当请求批准登录浏览器扩展程序时，即使您单击退出或最小化扩展程序窗口，该扩展程序也会等待最多两分钟以获得批准，以便使用网页 App 批准请求。
{% endhint %}

1、在网页 App 中，选择横幅通知中的**审查登录请求**链接或导航至**设置** → **安全** → **设备**：

{% embed url="https://bitwarden.com/assets/1K9FeC1OVOwyu0T8DMiwOp/90852f4e82b80827750bffd19cb6493d/2025-09-09_09-23-06.png?w=1189&fm=avif" %}
在网页 App 上批准请求
{% endembed %}

2、在**设备**选项卡上，定位并选择待处理的设备请求：

{% embed url="https://bitwarden.com/assets/7GLmOwtReFuUD3uxPQ0LB8/2abd84049d99f0dc0c21158c636ab55d/2025-09-09_09-22-11.png?w=1193&fm=avif" %}
网页 App 上的设备列表
{% endembed %}

3、验证指纹短语然后选择**确认访问**：

{% embed url="https://bitwarden.com/assets/6s6Hdn9L1EyeRfBsmOcfgX/a4e9e4996abc1ac63b8c6f2b3880cd07/2025-09-09_09-22-44.png?w=1189&fm=avif" %}
使用网页 App 批准访问
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
要使用桌面 App 批准请求：

1、在桌面 App 中，等待接收到设备批准请求：

{% embed url="https://bitwarden.com/assets/5cpkevhyuiSg82yfopvmc1/7d19d6377dbba8d4c6abee37b96a5037/2025-09-09_09-07-05.png?w=1200&fm=avif" %}
在桌面 App 上批准
{% endembed %}

2、验证指纹短语然后选择**确认访问**。
{% endtab %}
{% endtabs %}

请注意，这是一个独特的指纹，与您的[账户指纹短语](../../../security/encryption/account-fingerprint-phrase.md)不一样。

如果请求未被批准或被拒绝，则请求将在 15 分钟后过期。如果您没有收到登录请求或正在使用 F-Droid，请尝试从移动 App [手动同步您的密码库](../../../your-vault/syncing-your-vault.md)。

{% hint style="info" %}
如果您使用**设备登录**选项，您仍然需要使用任何当前有效的[两步登录方式](../../two-step-login/setup-guides/two-step-login-methods.md)。
{% endhint %}

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

当发起设备登录时：

1. 发起客户端向 Bitwarden 数据库中的身份验证请求表发送一个请求，其中包括账户电子邮箱地址、唯一的**身份验证请求公钥ᵃ** 和访问代码。已注册的设备，即已登录并在 Bitwarden 数据库中存储了[特定于设备的 GUID](../../../security/data/administrative-data.md) 的客户端，将收到此请求。
2. 请求获得批准后，批准客户端使用此请求中包含的**身份验证请求公钥**对账户的**用户加密密钥**进行加密。
3. 批准客户端然后将**用户加密密钥**发送到身份验证请求记录，并将此请求标记为已完成。
4. 发起客户端请求已加密的**用户加密密钥**。
5. 然后，发起客户端使用**身份验证请求私钥**在**本地**解密**用户加密密钥**。
6. 然后，发起客户端使用访问代码通过 Bitwarden Identity 服务对用户进行身份验证。
7. 然后，发起客户端可以获取用户的密码库数据并使用**用户加密密钥**对其进行解密。

**ª** - **身份验证请求公钥和私钥**是为每一个无密码登录请求生成的唯一密钥，其存在时间与请求的存在时间相同。如果请求未被批准或被拒绝，请求将过期并定期清除。

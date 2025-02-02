# 设备登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/log-in-with-device/)
{% endhint %}

您知道吗？您可以使用辅助设备而不是您的主密码来登录 Bitwarden。设备登录是一种无密码的身份验证方式，通过向您当前已登录的任何特定设备发送身份验证请求以获得批准，从而无需输入您的主密码。[了解我们的零知识加密实施方案](log-in-with-device.md#yun-zuo-fang-shi)。

可以在网页密码库、浏览器扩展、桌面应用程序和移动应用程序上发起设备登录。这些应用程序发出的请求可以在网页密码库、移动应用程序和桌面应用程序上获得批准。

## 设备登录准备 <a href="#prepare-to-log-in-with-a-device" id="prepare-to-log-in-with-a-device"></a>

要设置设备登录：

* 正常登录发起设备登录的应用程序（网页密码库、浏览器扩展、桌面或移动应用程序），以便 Bitwarden 可以识别您的设备。

{% hint style="info" %}
使用隐身模式或隐私浏览会阻止 Bitwarden 注册您的浏览器，因此您将无法在隐私浏览器窗口中使用设备登录。
{% endhint %}

* 在用于批准的应用程序（网页密码库、移动或桌面应用程序）上拥有认可的账户。要识别账户，您必须随时已成功登录到该设备。

{% hint style="info" %}
作为企业组织的成员，您需要遵守[要求 SSO 策略](../organizations/enterprise-policies.md#require-single-sign-on-authentication)，如果您无法使用**设备登录**选项，则需要改用 [SSO 登录](../login-with-sso/using-login-with-sso.md#login-using-sso)。
{% endhint %}

## 设备登录使用 <a href="#logging-in-with-a-device" id="logging-in-with-a-device"></a>

在发起的应用程序的登录界面，输入您的电子邮件地址并选择**继续**。然后，选择**使用设备登录**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7owqaTEe9Bo05wfLRZPhn8/7b66e262c26b4d4cb98cdb9584fafe13/2024-12-02_10-39-22.png?_a=DAJAUVWIZAAB" %}
设备登录
{% endembed %}

使用**设备登录**会将身份验证请求发送到您当前已登录并且已启用了该选项的任何网页密码库、移动或桌面应用程序以获得批准。

{% tabs %}
{% tab title="移动应用程序" %}
发起**设备登录**后，要使用移动应用程序批准请求：

1、登录到移动应用程序。

2、导航到**设置** → **账户安全** → **待处理的登录请求**。

3、找到并选择活动设备请求。

4、验证指纹短语然后选择**确认登录**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6xeP36n7g2dbwLI9YWjNg4/dbc18de80ace51b789021cc7083e76e0/IMG_1954.jpeg?_a=DAJAUVWIZAAB" %}
移动设备批准
{% endembed %}
{% endtab %}

{% tab title="网页应用程序" %}
发起**设备登录**后，要使用网页应用程序批准请求：

1、登录到网页应用程序。

{% hint style="info" %}
在为浏览器扩展批准登录请求时，扩展窗口必须保持打开状态，直到过程完成。Bitwarden 建议：

* **对于 Chrome 和 chromium 浏览器**：在单独的浏览器窗口中打开网页应用程序，这将允许扩展在原始窗口中保持打开状态。
* **对于 Safari 浏览器**：在单独的浏览器窗口中打开网页应用程序，这将允许扩展在原始窗口中保持打开状态。
* **对于 Firefox**：在侧边栏中打开扩展，这将允许在打开网页应用程序时继续保留扩展。

这些将在以后的版本中得到改进。
{% endhint %}

2、导航到**设置** → **安全** → **设备**。

3、找到并选择活动设备请求。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7GLmOwtReFuUD3uxPQ0LB8/71b896fcc76d3918e3fe37dee978e2dd/2025-01-14_12-35-31.png?_a=DAJAUVWIZAAB" %}
网页应用程序批准设备登录
{% endembed %}

4、验证指纹短语然后选择**确认登录**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6s6Hdn9L1EyeRfBsmOcfgX/ada1215dc8e370c7b82f1a0fc6bd8923/2025-01-14_15-55-10.png?_a=DAJAUVWIZAAB" %}
网页应用程序确认指纹
{% endembed %}
{% endtab %}

{% tab title="桌面应用程序" %}
发起**设备登录**后，要使用桌面应用程序批准请求：

1、登录到桌面应用程序。

2、验证请求将发送到您的桌面应用程序：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5cpkevhyuiSg82yfopvmc1/3bccaff5f02ad79bab67fb7ed941ed0e/2025-01-16_11-44-40.png?_a=DAJAUVWIZAAB" %}
桌面应用程序批准设备
{% endembed %}

3、验证指纹短语然后选择**确认登录**。
{% endtab %}
{% endtabs %}

请注意，这是一个独特的指纹，与您的[账户指纹短语](../security/account-fingerprint-phrase.md)不一样。

如果请求未被批准或被拒绝，则请求将在 15 分钟后过期。如果您没有收到登录请求或正在使用 F-Droid，请尝试从移动应用程序[手动同步您的密码库](syncing-your-vault.md)。

{% hint style="info" %}
如果您使用**设备登录**选项，您仍然需要使用任何当前有效的[两步登录方法](../two-step-login/two-step-login-methods.md)。
{% endhint %}

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

当发起设备登录时：

1. 网页密码库客户端向 Bitwarden 数据库中的身份验证请求表 POST（发送）一个请求，其中包括账户电子邮件地址、唯一的身份验证请求公钥**ᵃ** 和访问代码。
2. 已注册的设备，即已登录并在 Bitwarden 数据库中存储了[特定于设备的 GUID](../security/administrative-data.md) 的移动或桌面应用程序客户端，将收到此请求。
3. 请求获得批准后，批准客户端使用此请求中包含的身份验证请求公钥加密账户的主密钥和主密码哈希。
4. 批准客户端然后将已加密的主密钥和已加密的主密码哈希 PUT（放置）到身份验证请求记录，并将请求标记为已完成。
5. 发起客户端 GET（获取）已加密的主密钥和已加密的主密码哈希。
6. 然后，发起客户端使用身份验证请求私钥在**本地**解密主密钥和主密码哈希。
7. 然后，发起客户端使用访问代码和已完成的身份验证请求通过 Bitwarden Identity 服务对用户进行身份验证。

**ª** - 身份验证请求公钥和私钥是为每一个无密码登录请求生成的唯一密钥，其存在时间与请求的存在时间相同。如果请求未被批准或被拒绝，请求将在 15 分钟后过期并从数据库中清除。

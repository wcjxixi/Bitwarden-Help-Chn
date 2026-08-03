# 高级版续费

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/premium-renewal/)
{% endhint %}

个人高级版订阅按年自动续费。您可以在您的[网页版 App](../../password-manager/getting-started/getting-started-webvault.md) 中，导航到**设置** → **订阅**，来查看您的续费日期：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3Ru9TSLguhRNYtLe2TLwXk/bec6794eb58efa8780504720d4acb250/2026-03-03_10-24-17.png?w=1180&#x26;fm=avif" alt=""><figcaption><p>订阅页面</p></figcaption></figure></div>

当您的续费日期临近时，Bitwarden 建议您导航到**设置** → **订阅** → **付款方式**来验证付款方式。有关更新您的付款方式的帮助，请参阅[更新您的计费信息](../update-your-billing-information.md)。

{% hint style="warning" %}
如果我们无法处理您的付款方式，或者您取消了订阅，您的账户将恢复为[个人免费版](about-bitwarden-plans.md#free-individual)。在您重启您的高级版订阅之前，将导致以下情况：

#### **两步登录** <a href="#two-step-login" id="two-step-login"></a>

您**不会**被锁定在您的密码库之外，但您将无法使用高级两步登录选项，如 YubiKey、FIDO2 或 Duo。

* 如果您启用了核心的两步登录选项（验证器 App 或电子邮件），您将被提示使用这些可用的选项。&#x20;
* 如果您没有启用其他两步登录选项，您将在没有两步登录的情况下验证进入密码库。

您的机密密匙将继续存储在密码库项目的**验证器密钥 (TOTP)** 字段中，但是 Bitwarden 不会生成 TOTP 代码。

#### **加密文件附件** <a href="#encrypted-file-attachments" id="encrypted-file-attachments"></a>

文件**不会**从您的密码库中删除，但您无法上传或下载。

#### **紧急访问** <a href="#emergency-access" id="emergency-access"></a>

已信任的紧急联系人仍然可以请求并获得对您的密码库的访问权限。但是，作为授予人，您将无法添加新的或编辑现有的可信任的紧急联系人。
{% endhint %}

# 两步登录 - 电子邮箱

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-email/)
{% endhint %}

电子邮箱方式的两步登录对于所有 Bitwarden 用户是免费的。

{% hint style="danger" %}
如果您[使用 SSO 登录](../../log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)，则不建议使用电子邮箱方式的两步登录，因为使用多个方法会导致错误。可以考虑改为设置[免费的验证器方式的两步登录](two-step-login-via-authenticator.md)。
{% endhint %}

## 设置电子邮箱验证 <a href="#setup-email-verification" id="setup-email-verification"></a>

要启用电子邮箱方式的两步登录：

{% hint style="danger" %}
**丢失对两步登录设备的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。此外，用户还可以创建 Bitwarden [导出](../../../password-manager/import-and-export/export-vault-data.md)来备份密码库数据。
{% endhint %}

1、登录到 Bitwarden 网页 App。

2、从导航选择**设置** → **安全** → **两步登录**：

{% embed url="https://bitwarden.com/assets/2IjxRoQwl1powHRhah6Bq/39067a5fe6c53732054f323e4afb431b/Screenshot_2025-12-31_at_1.52.00%C3%A2__PM.png?w=1200&fm=avif" %}
两步登录设置
{% endembed %}

3、定位到**电子邮箱**选项然后选择**管理**按钮。将提示您输入您的主密码以继续。

4、输入您用于接收验证码的电子邮箱地址，然后点击**发送电子邮件**按钮。

{% hint style="success" %}
如果您有多个电子邮箱地址，用于两步登录的地址不必使用与注册 Bitwarden 时使用的地址相同。
{% endhint %}

5、检查您的收件箱接收到的 6 位验证码，将此代码填入网页密码库的对话框中并选择**启用**按钮。

一个绿色的 `已启用` 消息表明电子邮箱方式的两步登录已被启用。

6、单击**关闭**按钮，并确认**电子邮箱**选项现在已被启用（通过一个绿色勾号 **✔️** 指示）。

{% hint style="info" %}
我们建议在继续测试两步登录之前，将活动的网页密码库选项卡保持为打开状态，以防配置错误。确认其正常工作后，请注销所有的 Bitwarden App，以要求每个 App 使用两步登录。您最终会被自动注销。
{% endhint %}

## 使用电子邮件验证 <a href="#use-email-verification" id="use-email-verification"></a>

以下内容假设**电子邮箱**是您[已启用的最高优先级方式](two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用两步登录访问您的密码库：

1、在任一个 Bitwarden App 上输入您的电子邮箱地址和主密码以登录您的密码库。\
将提示您输入发送到您配置的电子邮箱的 6 位验证码。

2、检查您的收件箱接收到的 6 位数验证码。在**验证您的身份**界面上输入此代码：：

{% embed url="https://bitwarden.com/assets/ewFBMVRtmfZ3fsEC7LZmG/fcda3ce63380357797c2d41987854318/2026-01-12_15-08-12.png?w=754&fm=avif" %}
验证您的身份
{% endembed %}

{% hint style="success" %}
勾选**记住我**复选框，以记住您的设备，有效期 30 天。选择此选项意味着在此期间您无需完成两步登录步骤。
{% endhint %}

3、选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../log-in-and-unlock/vault-timeout-options.md)。

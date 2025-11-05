# 两步登录 - 电子邮箱

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-email/)
{% endhint %}

电子邮箱方式的两步登录对于所有 Bitwarden 用户是免费的。

{% hint style="warning" %}
如果您[使用 SSO 登录](../../log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)，则不建议使用电子邮箱方式的两步登录，因为使用多个方法会导致错误。可以考虑改为设置[免费的验证器方式的两步登录](two-step-login-via-authenticator.md)。
{% endhint %}

## 设置电子邮箱验证 <a href="#setup-email-verification" id="setup-email-verification"></a>

要启用电子邮箱方式的两步登录：

{% hint style="warning" %}
**丢失对两步登录设备的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。此外，用户还可以创建 Bitwarden [导出](../../../import-export/export-vault-data.md)来备份密码库数据。
{% endhint %}

1、登录到 Bitwarden 网页 App。

2、从导航选择**设置** → **安全** → **两步登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2BsKs83g4cmiCUwxf2ad83/b2a90e85355f3d937aeb46139203737e/2024-12-02_10-54-31.png?_a=DAJCwlWIZAAB" %}
两步登录
{% endembed %}

3、定位到**电子邮箱**选项然后选择**管理**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5GqQynIX94PhzJQ0tVW1aE/5dcea8d04c8a543daa7f96989f220756/2024-12-02_10-55-22.png?_a=DAJCwlWIZAAB" %}
两步登录提供程序
{% endembed %}

将提示您输入您的主密码以继续。

4、输入您用于接收验证码的电子邮箱地址，然后点击**发送电子邮件**按钮。

{% hint style="info" %}
如果您有多个电子邮箱地址，用于两步登录的地址不必使用与注册 Bitwarden 时使用的地址相同。
{% endhint %}

5、检查您的收件箱接收到的 6 位验证码，将此代码填入网页密码库的对话框中并选择**启用**按钮。

一个绿色的 `已启用` 消息表明电子邮箱方式的两步登录已被启用。

6、单击**关闭**按钮，并确认**电子邮箱**选项现在已被启用（通过一个绿色勾号 **✔️** 指示）。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，您应该注销所有的 Bitwarden App，以为每个 App 立即激活两步登录。您最终会被自动注销。
{% endhint %}

## 使用电子邮件验证 <a href="#use-email-verification" id="use-email-verification"></a>

以下内容假设**电子邮箱**是您[已启用的最高优先级方式](two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用两步登录访问您的密码库：

1、在任一个 Bitwarden App 上输入您的电子邮箱地址和主密码以登录您的密码库。\
将提示您输入发送到您配置的电子邮箱的 6 位验证码。

2、检查您的收件箱接收到的 6 位数验证码。在密码库登录界面输入此代码。

{% hint style="success" %}
勾选**记住我**方框，以记住您的设备，为期30天。记住您的设备意味着您不会被要求完成两步登录步骤。
{% endhint %}

3、选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../log-in-and-unlock/vault-timeout-options.md)。

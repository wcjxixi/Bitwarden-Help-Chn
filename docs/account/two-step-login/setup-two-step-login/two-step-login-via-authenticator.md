# 两步登录 - 验证器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-authenticator/)
{% endhint %}

第三方验证器 App（例如独立的 [Bitwarden Authenticator](../../../bitwarden-authenticator/bitwarden-authenticator.md)）方式的两步登录对于所有 Bitwarden 用户是免费的。

{% hint style="info" %}
某些身份验证器 App（例如 Google 身份验证器）不会自动备份您的 2FA 令牌以方便迁移到新的移动设备。在这些情况下，您应该手动保存每个令牌的身份验证器恢复代码。有关安全存储和使用恢复代码的更多信息，请参阅[恢复代码](../recovery-codes.md)。

其他 App 如 Authy 等，支持跨设备备份和同步。在这些情况下，请务必设置一个强大的备份密码并将其记录在您的 Bitwarden 密码库中。
{% endhint %}

## 设置验证器 <a href="#setup-an-authenticator" id="setup-an-authenticator"></a>

完成以下步骤以启用验证器 App 方式的两步登录：

{% hint style="warning" %}
**丢失对两步登录设备的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。此外，用户还可以创建 Bitwarden [导出](../../../password-manager/import-and-export/export-vault-data.md)来备份密码库数据。
{% endhint %}

1、登录到 Bitwarden 网页 App。

2、从导航选择**设置** → **安全** → **两步登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2BsKs83g4cmiCUwxf2ad83/b2a90e85355f3d937aeb46139203737e/2024-12-02_10-54-31.png?_a=DAJCwlWIZAAB" %}
两步登录
{% endembed %}

3、定位到**验证器 App** 选项然后选择**管理**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5GqQynIX94PhzJQ0tVW1aE/5dcea8d04c8a543daa7f96989f220756/2024-12-02_10-55-22.png?_a=DAJCwlWIZAAB" %}
两步登录提供程序
{% endembed %}

将提示您输入您的主密码以继续。

4、使用所选的验证器 App 扫描二维码或手动输入密钥。

如果您的移动设备上还没有验证器 App，请下载诸如 Bitwarden Authenticator 等，然后扫描二维码。

5、扫描后，您的验证器 App 将返回一个 6 位数的验证码。将此代码输入您的网页密码库对话框并单击**启用**按钮。

一个绿色的 `已启用` 消息表明验证器方式的两步登录已被启用。

6、单击**关闭**按钮，并确认**验证器 App** 选项现在已被启用（通过一个绿色勾号 **✔️** 指示）。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，你应该注销所有的 Bitwarden App，以为每个 App 立即激活两步登录。您最终会被自动注销。
{% endhint %}

### 在多个设备或验证器上进行设置 <a href="#setup-on-multiple-devices-or-authenticators" id="setup-on-multiple-devices-or-authenticators"></a>

Bitwarden 两步登录可以在多个兼容设备上运行。要在其他设备上添加 2FA，请按照上述步骤，用其他设备扫描二维码或手动输入二维码密钥，以在其他设备上启用 2FA。也可以在一台设备上为多个验证器设置两步登录。

## 使用验证器 <a href="#use-an-authenticator" id="use-an-authenticator"></a>

以下内容假设**验证器 App** 是您[已启用的最高优先级方式](two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用验证器访问您的密码库：

1、在任一个 Bitwarden App 上输入您的电子邮箱地址和主密码以登录您的密码库。\
将提示您输入来自您的验证器 App 的 6 位验证码。

2、打开您的验证器 App 并找到用于您的 Bitwarden 密码库的 6 位验证码。在密码库登录界面输入此代码。通常，验证码每 30 秒会更新一次。

{% hint style="success" %}
勾选**记住我**方框，以记住您的设备，为期30天。记住您的设备意味着您不会被要求完成两步登录步骤。
{% endhint %}

3、选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../log-in-and-unlock/vault-timeout-options.md)。

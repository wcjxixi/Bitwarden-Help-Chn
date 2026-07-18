# 主密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/master-password/)
{% endhint %}

您的主密码是访问密码库的主要方式。请务必确保您的主密码：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：更长、更复杂、更不常见的密码是保护账户的最佳方式。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记密码的强度。

[2023.3.0 版本](../release-notes.md)发布后，主密码要求必须至少包含 12 个字符。

{% hint style="success" %}
担心忘记您的主密码吗？这里有一些建议：

* **设置主密码提示**。如果您需要提醒，可以在登录界面请求主密码提示电子邮件。确保使用只有您自己能理解的提示。
* **指定一个**[**信任的紧急联系人**](emergency-access/about-emergency-access.md)。具有高级访问权限的用户可以在紧急情况下授予账户访问权限给朋友或家庭成员。
{% endhint %}

## 更改主密码 <a href="#change-your-master-password" id="change-your-master-password"></a>

您可以从网页 App、浏览器扩展或桌面 App 更改您的主密码。您需要知道您当前的主密码才能进行此操作：

{% tabs %}
{% tab title="网页 App" %}
在网页 App 中：

1、从导航栏选择**设置** → **安全**。

2、选择**主密码**选项卡：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2Svv0PwlH9i7SSK73dlv9A/e451afb190346e492110a7bf1bd3a518/Master_password_settings.png?w=1200&#x26;fm=avif" alt=""><figcaption><p>在网页 App 上更改主密码</p></figcaption></figure></div>

3、输入您的**当前主密码**。

4、输入并确认您的**新主密码**。

5、（可选） **输入主密码提示** ，它用于帮助您回忆密码。提示会在收到请求后发送到账户持有人的电子邮箱。

6、（可选） 如果您想在提交主密码之前通过 [HIBP](https://haveibeenpwned.com/) 检查您的主密码，请选中**检查密码的已知数据泄露情况**以运行[数据泄露报告](../password-manager/your-vault/security-tools/vault-health-reports.md#data-breach-individual-vaults-only)。这会将您的主密码的哈希值将发送到 HIBP，并将其与存储的暴露哈希值进行比较。Bitwarden 绝不会暴露您的主密码本身。

{% hint style="danger" %}
除非您完全了解其后果和所需的后续步骤，否则请不要选中**轮换账户加密密钥**复选框。[了解更多](../security/encryption/encryption-key-rotation.md)。
{% endhint %}

7、选择**更改主密码**按钮。

更改主密码将会自动注销网页密码库会话。其他已登录的 App 可能保持活动状态长达一小时，但最终也会要求您使用新的主密码重新登录。
{% endtab %}

{% tab title="浏览器扩展" %}
在浏览器扩展中：

1、打开**设置**选项卡，然后选择**账户安全**。

2、滚动到**其他选项**部分，然后选择**更改主密码**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/13NQDBUne0d99ssQlhxnTy/5320be0c494c351f808db48db48105ba/2026-04-21_09-58-31.png?w=800&#x26;fm=avif" alt=""><figcaption><p>在浏览器扩展上更改主密码</p></figcaption></figure></div>

3、输入您的**当前主密码**。

4、输入并确认您的**新主密码**。

5、（可选） **输入主密码提示** ，它用于帮助您回忆密码。提示会在收到请求后发送到账户持有人的电子邮箱。

6、（可选） 如果您想在提交主密码之前通过 [HIBP](https://haveibeenpwned.com/) 检查您的主密码，请选中**检查密码的已知数据泄露情况**以运行[数据泄露报告](../password-manager/your-vault/security-tools/vault-health-reports.md#data-breach-individual-vaults-only)。这会将您的主密码的哈希值将发送到 HIBP，并将其与存储的暴露哈希值进行比较。Bitwarden 绝不会暴露您的主密码本身。

7、选择**更改主密码**按钮。

更改主密码将会自动注销网页密码库会话。其他已登录的 App 可能保持活动状态长达一小时，但最终也会要求您使用新的主密码重新登录。
{% endtab %}

{% tab title="桌面 App" %}
在桌面 App 中：

1、从菜单栏中选择**账户** → **更改主密码**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5X1HjOgjvRg0ewMD30zYaY/4d9dfb5f92429b3b42d5111e0b759ca5/2026-04-21_09-00-24.png?w=800&#x26;fm=avif" alt=""><figcaption><p>在桌面 App 上更改主密码</p></figcaption></figure></div>

2、输入您的**当前主密码**。

3、输入并确认您的**新主密码**。

4、（可选） **输入主密码提示** ，它用于帮助您回忆密码。提示会在收到请求后发送到账户持有人的电子邮箱。

5、（可选） 如果您想在提交主密码之前通过 [HIBP](https://haveibeenpwned.com/) 检查您的主密码，请选中**检查密码的已知数据泄露情况**以运行[数据泄露报告](../password-manager/your-vault/security-tools/vault-health-reports.md#data-breach-individual-vaults-only)。这会将您的主密码的哈希值将发送到 HIBP，并将其与存储的暴露哈希值进行比较。Bitwarden 绝不会暴露您的主密码本身。

6、选择**更改主密码**按钮。

更改主密码将会自动注销网页密码库会话。其他已登录的 App 可能保持活动状态长达一小时，但最终也会要求您使用新的主密码重新登录。
{% endtab %}
{% endtabs %}

## 我忘记了主密码 <a href="#i-forgot-my-master-password" id="i-forgot-my-master-password"></a>

了解如果您[忘记了主密码](i-forgot-my-master-password.md)该怎么做。

## 附加登录选项 <a href="#additional-login-options" id="additional-login-options"></a>

您的主密码是设置 Bitwarden 账户的必要条件。根据您或您的组织与 Bitwarden 交互的方式，可以使用其他选项来访问您的 Bitwarden 账户。

| 方式                                                                                                                                                                  | 描述                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [使用设备登录](log-in-and-unlock/more-log-in-unlock-options/log-in-with-device.md)                                                                                        | 设备登录是一种利用受信任的辅助设备向 Bitwarden 发送身份验证请求的选项。                           |
| [使用 SSO 登录](../admin-console/login-with-sso/about-sso.md)                                                                                                           | Bitwarden 用户如果属于使用单点登录 (SSO) 的组织，可以利用现有的身份提供程序进行登录，该提供程序将对用户进行身份验证。 |
| [使用通行密钥登录](log-in-and-unlock/more-log-in-unlock-options/log-in-with-passkeys.md)                                                                                    | 通行密钥可用作使用主密码和电子邮件登录 Bitwarden 的替代方式，并且某些通行密钥还可用于密码库加密和解密。           |
| [使用生物识别解锁](log-in-and-unlock/more-log-in-unlock-options/unlocking-with-biometrics.md)和[使用 PIN 码解锁](log-in-and-unlock/more-log-in-unlock-options/unlock-with-pin.md) | 生物识别或 PIN 解锁并不是一种替代登录方法，但是，它允许您使用系统生物识别或 PIN 而不是主密码来访问已锁定的账户。       |

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经创建了**易记**且**强大**的主密码，我们建议：

* [通过两步登录进一步保护您的密码库](two-step-login/setup-two-step-login/two-step-login-methods.md)
* [启用紧急访问](emergency-access/about-emergency-access.md)（需要高级版）

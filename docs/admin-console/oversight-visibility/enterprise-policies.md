# 企业策略

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/policies/)
{% endhint %}

## 什么是企业策略？ <a href="#what-are-enterprise-policies" id="what-are-enterprise-policies"></a>

企业策略允许企业组织为所有成员强制实施安全规则和默认设置，例如强制使用两步登录。

{% hint style="danger" %}
Bitwarden 强烈建议在邀请用户加入您的组织之前先设置好企业策略。某些策略会在启用时撤销不符合要求的用户，而某些策略无法追溯性地执行。
{% endhint %}

## 设置企业策略 <a href="#setting-enterprise-policies" id="setting-enterprise-policies"></a>

组织所有者和管理员可以应用企业策略。要更新策略：

1、使用 Bitwarden 网页 App，打开管理控制台。

2、选择**设置**。

3、选择**策略**。

4、选择您要更改的策略的名称：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2flohk6BsRKvazjztwvzsJ/4258307d845b33cd9f765388ca6bfea6/2024-12-03_14-24-58.png?_a=DAJCwlWIZAAB" %}
设置策略
{% endembed %}

5、选中或取消选中**启用**。

6、（可选）如果出现更多选项，请配置它们。

7、选择**保存**。

## 可用的策略 <a href="#available-policies" id="available-policies"></a>

### 要求两步登录 <a href="#require-two-step-login" id="require-two-step-login"></a>

启用**要求两步登录**策略将要求成员使用任何两步登录方法访问其密码库。如果使用的是 SSO 或身份提供程序的 2FA 功能，则无需启用此策略。即使对于仅[接受](../manage-members/user-management.md#accept)组织邀请的用户，也会强制执行此策略。

{% hint style="danger" %}
**当您激活此策略时，非所有者或管理员且不遵守此策略的组织成员的访问权限将被撤销**。由于此策略而被撤销访问权限的用户将收到电子邮件通知，并且必须采取措施使其合规，然后才能恢复其访问权限。
{% endhint %}

### 主密码要求 <a href="#master-password-requirements" id="master-password-requirements"></a>

启用**主密码要求**策略，将对用户的主密码强度执行一套可配置的最低要求。组织可以强制执行：

* 最小主密码复杂度
* 最小主密码长度
* 所需字符类型

密码的复杂度按照 0（弱）到 4（强）的比例计算。Bitwarden 使用 [zxcvbn 库](https://github.com/dropbox/zxcvbn)来计算密码复杂度。

使用**要求现有成员更改他们的密码**选项以要求现有的、不合要求的组织成员（无论其角色如何）在下次登录时更新他们的主密码。通过组织邀请创建新账户的用户会被提示创建一个符合要求的主密码。

### 禁用 PIN 码解锁 <a href="#remove-unlock-with-pin" id="remove-unlock-with-pin"></a>

启用**禁用 PIN 码解锁**策略后，成员将无法在网页 App、浏览器扩展和桌面 App 上配置或使用 PIN 码解锁。该策略打开后适用于所有组织成员，包括管理员和所有者。

{% hint style="info" %}
计划在今后的版本中支持在移动 App 上执行这一策略。
{% endhint %}

在该策略实施前使用 PIN 码解锁的成员将在下次登录时执行该策略，也就是说，如果他们已经登录了会话，他们仍将在用户界面中看到该选项，并能使用 PIN 码解锁，直到他们注销或关闭客户端中的 PIN 码解锁选项。

### 账户恢复管理 <a href="#account-recovery-administration" id="account-recovery-administration"></a>

启用**账户恢复管理**策略将允许所有者和管理员帮助成员重新获得对其账户的访问权限。使用此策略，所有者和管理员可以向已注册[账户恢复](../manage-members/account-recovery/about-account-recovery.md)的成员发送重置他们的主密码的链接。默认情况下，用户必须[自行注册账户恢复](../manage-members/account-recovery/account-recovery-enrollment.md#self-enroll-in-account-recovery)才有资格拥有此功能。

要简化账户恢复注册，请选中**为新成员启用自动注册**。当新成员[接受组织邀请](../manage-members/user-management.md#accept)时，这会为新成员注册账户恢复，并阻止他们从账户恢复中退出。当前组织成员不会追溯地添加，因此仍需要他们自行注册。

要在您的组织中使用[受信任设备 SSO](../login-with-sso/trusted-devices/about-trusted-devices.md)，您的组织必须开启**账户恢复管理**策略。

{% hint style="info" %}
在激活此策略之前，必须启用[**单一组织**](enterprise-policies.md#single-organization)策略。
{% endhint %}

### 密码生成器 <a href="#password-generator" id="password-generator"></a>

启用**密码生成器**策略将对任何用户生成的密码强制执行一套可配置的最低要求。组织可以强制执行：

* 密码、密码短语、或用户偏好

**对于密码：**

* 最小密码长度
* 最少数字 (0-9) 数量
* 最少特殊字符 (!@#$%^&\*) 数量
* 所需字符类型

**对于密码短语：**

* 最少单词数
* 是否大写
* 是否包含数字

{% hint style="danger" %}
启用此策略后，现有的不符合要求的密码**不会**被更改，相关的项目也不会从组织中移除。启用此策略后，当更改或生成密码时，将强制要求符合此策略。

密码生成器界面上将显示一条横幅给用户，表明某个策略正在影响他们的生成器设置。
{% endhint %}

### 单一组织 <a href="#single-organization" id="single-organization"></a>

启用**单一组织**策略将限制组织内的非所有者/非管理员成员加入其他组织或创建其他组织。即使对于仅[接受](../manage-members/user-management.md#accept)组织邀请的用户，也会强制执行此策略，但所有者和管理员不受此策略的约束。

{% hint style="danger" %}
**当您激活此策略时，非所有者或管理员且不遵守此策略的组织成员的访问权限将被撤销**。由于此策略而被撤销访问权限的用户将收到电子邮件通知，并且必须采取措施使其合规，然后才能恢复其访问权限。
{% endhint %}

在激活以下策略之前，必须启用**单一组织**策略：

* [账户恢复管理](enterprise-policies.md#account-recovery-administration)
* [要求单点登录身份验证](enterprise-policies.md#require-single-sign-on-authentication)
* [默认 URI 匹配检测](enterprise-policies.md#default-uri-match-detection)
* [会话超时](enterprise-policies.md#vault-timeout)

如果您无法停用**单一组织**策略，请验证上述所有策略是否已停用，然后重试。

### 要求单点登录身份验证 <a href="#require-single-sign-on-authentication" id="require-single-sign-on-authentication"></a>

启用**要求单点登录身份验证**策略将要求非所有者/非管理员用户使用 SSO 登录。如果是自托管，可以使用[环境变量](../../self-hosting/deploy-and-configure/configuration-options/environment-variables.md)对所有者和管理员强制执行该策略。有关更多信息，请参阅 [SSO 登录的使用](../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)。所有者和管理员不受此策略的约束。

使用此策略的组织成员将无法[使用通行密钥登录](../../account/log-in-and-unlock/more-log-in-options/log-in-with-passkeys.md)。

{% hint style="info" %}
在激活此策略之前，必须启用[**单一组织**](enterprise-policies.md#single-organization)策略。
{% endhint %}

### 强制组织数据所有权 <a href="#enforce-organization-data-ownership" id="enforce-organization-data-ownership"></a>

启用**强制组织数据所有权**策略将阻止个人拥有密码库项目。启用后，将添加「[我的项目](../../password-manager/organization-members/my-items.md)」，这是一个组织拥有的位置，只有该成员才能访问。「**我的项目**」将取代个人的「**我的密码库**」，并将所有权从用户转移到组织。只要该成员在组织中处于活跃状态，管理员就无法编辑或导出该用户的「我的项目」。

{% hint style="info" %}
此策略仅影响非组织所有者或管理员的成员。组织所有者和管理员可以继续使用「**我的密码库**」。
{% endhint %}

启用后，所有新保存的项目默认都会放入该成员的「**我的项目**」中。在「添加项目」界面上将向用户显示一条横幅，表明某个策略正在影响他们的所有权选项。

[成员被移除](../manage-members/revoke-remove/permanently-remove-access.md)后，「**我的项目**」中的数据仍保留在组织中。所有者、管理员和某些自定义角色用户可以为其他成员分配对已移除成员的「**我的项目**」的访问权限。

{% hint style="danger" %}
目前，Bitwarden 建议仅尚未开始入职成员的组织启用[强制组织数据所有权策略](enterprise-policies.md#enforce-organization-data-ownership)。

如果您的组织在 [2025.11.0](../../release-notes.md#id-2025.11.0) 版本之前激活了该策略，则系统会为该版本发布后确认的成员创建「**我的项目**」。现有成员不会拥有「**我的项目**」，可以继续使用他们的「**我的密码库**」。未来的版本将允许已经开始入职成员并使用个人密码库的组织将所有凭据迁移到组织所有权。
{% endhint %}

### 禁用 Send <a href="#disable-send" id="disable-send"></a>

启用**禁用 Send** 策略将阻止非所有者/非管理员用户使用 [Bitwarden Send](../../password-manager/bitwarden-send/about-send.md) 创建或编辑 Send。受此策略约束的用户仍然可以删除尚未达到[删除日期](../../password-manager/bitwarden-send/send-lifespan.md)的现有 Send。所有者和管理员不受此策略的约束。

在 **Send** 视图中和打开任何现有的 Send 时，会向用户显示一个横幅，以表明某个策略限制他们只能删除 Send。

### Send 选项 <a href="#send-options" id="send-options"></a>

启用 **Send 选项**策略将允许所有者和管理员指定用于创建和编辑 Send 的选项。所有者和管理员不受此策略的约束。选项包括：

| 选项             | 描述                                                                                                                                                                           |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 不允许用户隐藏其电子邮箱地址 | 启用该选项可以禁用[隐藏电子邮箱](../../password-manager/bitwarden-send/send-privacy.md#hide-email)选项，这意味着所有[接收到的 Send](../../password-manager/bitwarden-send/receive-a-send.md) 都将包含其发送者信息。 |

### 禁用支付卡项目类型 <a href="#remove-card-item-type" id="remove-card-item-type"></a>

启用**禁用支付卡项目类型**策略将阻止成员创建或导入信用卡到组织和个人密码库。

作为多个组织成员的用户仍只能在允许使用支付卡的组织中使用支付卡，即使不同的组织已激活此策略。

现有支付卡将自动隐藏，但数据不会被删除，如果管理员禁用该策略，支付卡将重新出现。

### 默认 URI 匹配检测 <a href="#default-uri-match-detection" id="default-uri-match-detection"></a>

启用**默认 URI 匹配检测**策略以为您的成员设置[默认 URI 匹配检测](../../password-manager/autofill/troubleshoot-autofill/forming-uris-for-autofill.md#default-match-detection)。这可以帮助您配置自动填充，以最好地满足您组织的安全和策略需求。

启用此策略时，从下拉菜单中选择您组织的**默认 URI 匹配检测**：

* 基础域名
* 主机
* 精确
* 从不

{% hint style="info" %}
不受此策略约束的用户在设置其个人账户的默认匹配检测时还有两个选项：**开始于**和**正则表达式**。组织默认不提供这些选项，因为它们可能匹配非预期页面并暴露凭据。
{% endhint %}

激活策略后，成员无法在 **⚙️设置** → **自动填充**中查看或更改其账户的**默认 URI 匹配检测**。但是，他们仍然可以为个人登录项目选择 URI 匹配。此策略不会影响组织所有者和管理员。

{% hint style="info" %}
在激活此策略之前，必须启用[**单一组织**](enterprise-policies.md#single-organization)策略。
{% endhint %}

### 会话超时 <a href="#session-timeout" id="session-timeout"></a>

启用**会话超时**策略以设置限制并控制成员的会话超时行为。启用此策略后，然后用户编辑其账户的**密码库超时**设置时，**超时**选项将不会超过您为组织选择的最大值，并且某些选项（例如**浏览器重启时**和**从不**）将不可用。所有者和管理员不受此策略的约束。

您可以自定义两个选项：

* 从**最大允许的超时**下拉菜单中，设置会话可以保持活动状态的时间限制：
  * **立即**：当用户停止与 Bitwarden 交互时
  * **自定义**：在输入的**小时**数量和**分钟**数量之后
  * **系统锁定时**：当您的设备锁定或屏幕保护程序激活时（仅限浏览器扩展和桌面 App）
  * **App 重启时**：当 Bitwarden App 关闭然后重新打开时
  * **从不**：不设置最大会话持续时间

{% hint style="danger" %}
**从不**超时选项会将未加密的加密密钥存储在您的设备上，这可能会影响安全性。为了确保您的数据安全，我们强烈建议您选择其他选项。
{% endhint %}

* 从**会话超时操作**下拉菜单中，选择会话结束后发生的行为。您可以指定[锁定或注销](../../account/log-in-and-unlock/vault-timeout-options.md#session-timeout-action)，或选择**用户首选项**以让成员在其账户设置中进行选择。

{% hint style="success" %}
如果您的组织使用[受信任设备](../login-with-sso/trusted-devices/about-trusted-devices.md)，请考虑选择**注销**。会话超时后，成员无需主密码即可通过受信任设备上的 SSO 访问其密码库。
{% endhint %}

{% hint style="info" %}
[~~版本 2025.11.0~~](../../release-notes.md#id-2025.11.0) ~~中添加了新的超时选项，以下超时选项目前仅在 Android App 中被支持：**系统锁定时**、**App 重新启动时**和**从不**。在以后的版本中，更多客户端将支持这些超时选项。~~
{% endhint %}

{% hint style="info" %}
在激活此策略之前，必须启用[**单一组织**](enterprise-policies.md#single-organization)策略。
{% endhint %}

### 禁用导出 <a href="#remove-export" id="remove-export"></a>

启用**禁用导出**策略将禁止您组织的非所有者/非管理员成员[导出其私人密码库数据](../../password-manager/import-and-export/export-vault-data.md#export-a-personal-vault)。所有者和管理员不受此策略的约束。

在网页密码库和 CLI 中，会向用户显示一条消息，以表明某个策略正在影响他们的选项。在其他客户端中，该选项将被简单地禁用：

{% embed url="https://bitwarden.com/assets/5E2871D2vZBzveBmVyv9lO/b89f979980566dda40928db1ce450507/2024-10-14_08-50-45.png?w=1015&fm=avif" %}
密码库导出已禁用
{% endembed %}

### 禁用免费 Bitwarden 家庭赞助 <a href="#remove-free-bitwarden-families-sponsorship" id="remove-free-bitwarden-families-sponsorship"></a>

启用**禁用免费 Bitwarden 家庭赞助**策略将禁止您的组织成员通过您的组织[兑换免费的家庭计划](../../plans-and-pricing/password-manager/families-for-enterprise.md)。

在该策略激活前已兑换赞助家庭组织的用户将继续获得其组织的赞助，直至当前账单周期结束。在下一个账单周期开始时，将通过该组织存储的付款方式收取费用。

### 激活自动填充 <a href="#activate-auto-fill" id="activate-auto-fill"></a>

启用**激活自动填充**策略将自动为组织的所有现有和新成员打开浏览器扩展上的[页面加载时自动填充](../../password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#on-page-load)功能。如果激活，成员将无法禁用页面加载时自动填充功能。

### 使用 SSO 自动登录 <a href="#automatic-login-with-sso" id="automatic-login-with-sso"></a>

启用**使用 SSO 自动登录**策略，将允许在访问身份提供程序提供的非 SSO App 时自动填充并提交登录表单。要启用此设置：

1、要启用**使用 SSO 自动登录**策略，请选中**启用**复选框，并输入**身份提供程序主机** URL。URL 应包含 `protocol://domain`。

{% embed url="https://bitwarden.com/assets/2qHW4T4CDwpQJmPK6oDDn8/e25f021aa609e6072ffa664ae757ea7f/2025-11-19_09-34-16.png?w=543&fm=avif" %}
为允许的应用程序自动登录用户
{% endembed %}

2、作为 IdP 的管理员，在终端用户控制面板上添加一个应用程序或 App 快捷方式，其中包含具有附加参数 `?autofill=1` 的目标 URL。

{% embed url="https://bitwarden.com/assets/33zjaF3nEYtBB3JaVjBGmS/ab61ee2d6551d5d5bab70319ca64951e/2024-09-24_10-39-55.png?w=538&fm=avif" %}
Microsoft App 示例
{% endembed %}

3、保存应用程序后，用户可以从 IdP 面板上选择应用程序，然后 Bitwarden 将自动填充并登录应用程序。

{% hint style="info" %}
**使用 SSO 自动登录**将根据用户当前在 Bitwarden 浏览器扩展上的活动账户自动填充数据。此外，自动填充的数据将是用户最近使用的与目标应用程序 URL 相关联的凭据。
{% endhint %}

### 阻止已声明域名的账户创建 <a href="#block-account-creation-for-claimed-domains" id="block-account-creation-for-claimed-domains"></a>

{% hint style="info" %}
在激活此策略之前，必须先[声明域名](claimed-domains/claimed-domains.md)。
{% endhint %}

启用**阻止已声明域名的账户创建**策略，可以阻止具有与您[已声明的域名](claimed-domains/claimed-domains.md)匹配的电子邮箱地址的人员在组织外部创建 Bitwarden 账户。启用此策略后，与您已声明的域名匹配的电子邮箱地址只能通过受邀加入您的组织的方式或[使用 SSO 进行 JIT 配置](../login-with-sso/jit-provisioning.md)的方式创建 Bitwarden 账户。

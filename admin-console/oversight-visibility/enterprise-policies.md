# 企业策略

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/policies/)
{% endhint %}

## 什么是企业策略？ <a href="#what-are-enterprise-policies" id="what-are-enterprise-policies"></a>

企业策略使企业能够对所有用户强制执行安全规则，例如强制使用两步登录。

企业策略可以由组织的**管理员**或**所有者**的用户来设置。

{% hint style="danger" %}
Bitwarden 强烈建议在邀请用户加入您的组织之前设置好企业策略。某些策略会在启用时删除不合要求的用户，而某些策略无法追溯执行。
{% endhint %}

## 设置企业策略 <a href="#setting-enterprise-policies" id="setting-enterprise-policies"></a>

可通过在管理控制台中，导航至**管理设置 → 策略**来设置策略：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2flohk6BsRKvazjztwvzsJ/4258307d845b33cd9f765388ca6bfea6/2024-12-03_14-24-58.png?_a=DAJCwlWIZAAB" %}
设置策略
{% endembed %}

## 可用的策略 <a href="#available-policies" id="available-policies"></a>

### 要求两步登录 <a href="#require-two-step-login" id="require-two-step-login"></a>

打开**要求两步登录**策略将要求成员使用任何两步登录方法访问其密码库。如果使用的是 SSO 或身份提供商的 2FA 功能，则无需启用此策略。即使是只接受了组织邀请的用户，也会执行此策略。

{% hint style="danger" %}
**不是所有者或管理员，且其账户未设置两步登录的组织成员，在激活此策略后将从组织中被移除。**&#x7531;于该策略而被移除的用户将收到电子邮件通知，并且必须重新邀请他们加入组织。更多信息：

* 现有用户在为他们的密码库启用两步登录之前，将无法接受邀请，包括成为所有者或管理员的邀请。
* 新用户将自动设置为基于电子邮箱的两步登录，但可以随时更改。
{% endhint %}

### 主密码要求 <a href="#master-password-requirements" id="master-password-requirements"></a>

打开**主密码要求**策略，将对用户的主密码强度执行一套可配置的最低要求。组织可以强制执行：

* 最小主密码复杂度
* 最小主密码长度
* 所需字符类型

密码的复杂度按照 0（弱）到 4（强）的比例计算。Bitwarden 使用 [zxcvbn 库](https://github.com/dropbox/zxcvbn)来计算密码复杂度。

使用**要求现有成员更改他们的密码**选项以要求现有的、不合规的组织成员（无论其角色如何）在下次登录时更新他们的主密码。通过组织邀请创建新账户的用户会被提示创建一个符合要求的主密码。

### 禁用 PIN 码解锁 <a href="#remove-unlock-with-pin" id="remove-unlock-with-pin"></a>

打开**禁用 PIN 码解锁**策略后，成员将无法在网页 App、浏览器扩展和桌面 App 上配置或使用 PIN 码解锁。该策略打开后适用于所有组织成员，包括管理员和所有者。

{% hint style="info" %}
计划在今后的版本中支持在移动 App 上执行这一策略。
{% endhint %}

在该策略实施前使用 PIN 码解锁的成员将在下次登录时执行该策略，也就是说，如果他们已经登录了会话，他们仍将在用户界面中看到该选项，并能使用 PIN 码解锁，直到他们注销或关闭客户端中的 PIN 码解锁选项。

### 账户恢复管理 <a href="#account-recovery-administration" id="account-recovery-administration"></a>

打开**账户恢复管理**策略将允许所有者和管理员使用[密码重置功能](../manage-members/account-recovery/about-account-recovery.md)来重置已注册用户的主密码。默认情况下，用户需要[自行注册密码重置](../manage-members/account-recovery/about-account-recovery.md#self-enroll-in-password-reset)，但也可以使用[自动注册](enterprise-policies.md#automatic-enrollment)选项，对受邀用户强制自动注册。

要在您的组织中使用[受信任设备 SSO](../login-with-sso/trusted-devices/about-trusted-devices.md)，您的组织必须开启账户恢复管理策略。

{% hint style="info" %}
在激活该策略之前，必须先启用**单一组织**策略。

同理，必须先禁用**账户恢复管理**策略，才能禁用**单一组织**策略。
{% endhint %}

#### 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

打开**自动注册**选项将在新用户[加入组织的邀请被接受后](../manage-members/user-management.md#accept)自动注册密码重置功能并阻止他们撤销。

{% hint style="info" %}
已经在组织中的用户不会被注册密码重置，而是需要[自行注册](../manage-members/account-recovery/about-account-recovery.md#self-enroll-in-password-reset)。
{% endhint %}

### 密码生成器 <a href="#password-generator" id="password-generator"></a>

打开**密码生成器**策略将对任何用户生成的密码强制执行一套可配置的最低要求。组织可以强制执行：

* 密码、密码短语、或用户偏好

**对于密码：**

* 最小密码长度
* 最少数字（0-9）数量
* 最少特殊字符（!@#$%^&\*）数量
* 所需字符类型

**对于密码短语：**

* 最少单词数
* 是否大写
* 是否包含数字

{% hint style="warning" %}
启用此策略后，现有的不符合要求的密码**不会**被更改，相关的项目也不会从组织中移除。启用此策略后，当更改或生成密码时，将强制要求符合此策略。

密码生成器界面上将显示一条横幅给用户，表明某个策略正在影响他们的生成器设置。
{% endhint %}

### 单一组织 <a href="#single-organization" id="single-organization"></a>

打开**单一组织**策略将限制组织内的非所有者/非管理员成员加入其他组织或创建其他组织。即使是只接受了组织邀请的用户，也可以执行此策略，所有者和管理员不受此策略的约束。

{% hint style="warning" %}
**启用此策略后，本组织中属于多个组织成员的用户将被从本组织中移除。**

由于此策略而被移除的用户将收到电子邮件通知，并且必须重新被邀请才能加入组织。除非用户将自己从所有其他组织中移除，否则他们将无法接受加入组织的邀请。
{% endhint %}

### 要求单点登陆验证 <a href="#require-single-sign-on-authentication" id="require-single-sign-on-authentication"></a>

打开**要求单点登录验证**策略将要求非所有者/非管理员用户使用 SSO 登录。如果是自托管，可以使用环境变量对所有者和管理员强制执行该策略。有关更多信息，请参阅 [SSO 登录的使用](../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)。所有者和管理员不受此策略的约束。

使用此策略的组织成员将无法使用密码登录。

{% hint style="info" %}
在激活此策略之前，必须先启用**单一组织**策略。

同理，必须先禁用**单点登录验证**策略，然后才能禁用**单一组织**策略。
{% endhint %}

### 强制组织数据所有权 <a href="#enforce-organization-data-ownership" id="enforce-organization-data-ownership"></a>

打开**强制组织数据所有权**策略将要求非所有者/非管理员用户将密码库项目保存到组织中，防止组织成员拥有密码库项目的所有权。

在**添加项目**界面上将向用户显示一条横幅，表明某个策略正在影响他们的所有权选项。

即使是只接受了组织邀请的用户，也会执行此策略，所有者和管理员不受此策略的约束。

{% hint style="info" %}
在实施本策略之前或加入本组织之前创建的密码库项目将保留在用户的个人密码库中。
{% endhint %}

### 禁用 Send <a href="#disable-send" id="disable-send"></a>

打开**禁用 Send** 策略将阻止非所有者/非管理员用户使用 [Bitwarden Send](../../bitwarden-send/about-send.md) 创建或编辑 Send。受此策略约束的用户仍然可以删除尚未达到[删除日期](../../bitwarden-send/send-lifespan.md)的现有 Send。所有者和管理员不受此策略的约束。

在 **Send** 视图中和打开任何现有的 Send 时，会向用户显示一个横幅，以表明某个策略限制他们只能删除 Send。

### Send 选项 <a href="#send-options" id="send-options"></a>

打开 **Send 选项**策略将允许所有者和管理员指定用于创建和编辑 Send 的选项。所有者和管理员不受此策略的约束。选项包括：

| 选项             | 描述                                                                                                                                         |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| 不允许用户隐藏其电子邮箱地址 | 启用该选项可以禁用[隐藏电子邮箱](../../bitwarden-send/send-privacy.md#hide-email)选项，这意味着所有[接收到的 Send](../../bitwarden-send/receive-a-send.md) 都将包含其发送者信息。 |

### 密码库超时 <a href="#vault-timeout" id="vault-timeout"></a>

设置**密码库超时**策略将允许您：

* 为**除所有者外**的所有成员实施最大[密码库超时](../../account/log-in-and-unlock/vault-timeout-options.md#vault-timeout)持续时间。此选项将超时限制应用于所有客户端应用程序（移动端、桌面端、浏览器扩展等）。
* 为**除所有者外**的所有成员设置[密码库超时](../../account/log-in-and-unlock/vault-timeout-options.md#vault-timeout-action)动作。此选项可以设置为**用户首选项**、在发生密码库超时时**锁定**或**注销**。\
  **注销**选项可用于比如在用户每次访问其密码库时提示用户使用 2FA，并通过定期清除用户机器上的本地数据来防止离线使用。

在密码库超时配置期间将向用户显示一条横幅，表明某个策略正在影响他们的选项。激活该策略后，用户将无法使用某些密码库超时选项，如浏**览器重启时**或**永不**。所有者和管理员不受此策略的约束。

{% hint style="info" %}
在激活此策略之前，必须启用**单一组织**策略。

因此，您必须先禁用**密码库超时**策略，然后才能禁用**单一组织**策略。
{% endhint %}

### 禁用个人密码库导出 <a href="#disable-personal-vault-export" id="disable-personal-vault-export"></a>

打开**禁用个人密码库导出**策略将禁止您组织的非所有者/非管理员成员[导出其私人密码库数据](../../import-export/export-vault-data.md#export-a-personal-vault)。所有者和管理员不受此策略的约束。

在网页密码库和 CLI 中，会向用户显示一条消息，以表明某个策略正在影响他们的选项。在其他客户端中，该选项将被简单地禁用：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5E2871D2vZBzveBmVyv9lO/b89f979980566dda40928db1ce450507/2024-10-14_08-50-45.png?_a=DAJCwlWIZAAB" %}
移除了密码库导出
{% endembed %}

### 禁用免费 Bitwarden 家庭赞助 <a href="#remove-free-bitwarden-families-sponsorship" id="remove-free-bitwarden-families-sponsorship"></a>

打开**禁用免费 Bitwarden 家庭赞助**策略将禁止您的组织成员通过您的组织[兑换免费的家庭计划](../../plans-and-pricing/password-manager/redeem-families-sponsorship.md)。

在该策略激活前已兑换赞助家庭组织的用户将继续获得其组织的赞助，直至当前账单周期结束。在下一个账单周期开始时，将通过该组织存储的付款方式收取费用。

### 激活自动填充 <a href="#activate-auto-fill" id="activate-auto-fill"></a>

打开**激活自动填充**策略将自动为组织的所有现有和新成员打开浏览器扩展上的[页面加载时自动填充](../../password-manager/autofill/autofill-from/autofill-from-browser-extensions.md#on-page-load)功能。如果激活，成员将无法禁用页面加载时自动填充功能。

### 为允许的应用程序自动登录用户 <a href="#automatically-log-in-users-for-allowed-applications" id="automatically-log-in-users-for-allowed-applications"></a>

打开**为允许的应用程序自动登录用户**策略，将允许在访问身份提供程序提供的非 SSO  App 时自动填充并提交登录表单。要启用此设置：

1、要启用**为允许的应用程序自动登录用户**策略，请选中**打开**复选框，并输入**身份提供程序主机** URL。URL 应包括 `protocol://domain`。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2qHW4T4CDwpQJmPK6oDDn8/4fe9fb9517db6ed1a09a72be3883f2ae/2024-08-27_11-21-32.png?_a=DAJCwlWIZAAB" %}
为允许的应用程序自动登录用户
{% endembed %}

2、作为 IdP 的管理员，在终端用户控制面板上添加一个应用程序或应用程序快捷方式，其中包含目标 URL，并添加参数 `?autofill=1`。 例如，假如使用 Microsoft Azure：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/33zjaF3nEYtBB3JaVjBGmS/ab61ee2d6551d5d5bab70319ca64951e/2024-09-24_10-39-55.png?_a=DAJCwlWIZAAB" %}
Microsoft 应用程序示例
{% endembed %}

3、保存应用程序后，用户可从 IdP 面板上选择应用程序，Bitwarden 将自动填充并登录应用程序。

{% hint style="info" %}
自动登录用户将根据用户当前在 Bitwarden 浏览器扩展上的活动账户自动填充数据。此外，自动填充的数据将是用户最近使用的与目标应用程序 URL 相关联的凭证。
{% endhint %}

### 禁用支付卡项目类型 <a href="#remove-card-item-type" id="remove-card-item-type"></a>

打开**禁用支付卡项目类型**策略将阻止成员创建或导入信用卡到组织和个人密码库。

作为多个组织成员的用户仍只能在允许使用支付卡的组织中使用支付卡，即使不同的组织已激活此策略。

现有支付卡将自动隐藏，但数据不会被删除，如果管理员禁用该策略，支付卡将重新出现。

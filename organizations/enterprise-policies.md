# 企业策略

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/policies/)
{% endhint %}

## 什么是企业策略？ <a href="#what-are-enterprise-policies" id="what-are-enterprise-policies"></a>

企业策略使企业能够对所有用户强制执行安全规则，例如强制使用两步登录。

企业策略可以由用户类型为**管理员**或**所有者**的用户来设置。

{% hint style="warning" %}
Bitwarden 强烈建议在邀请用户加入您的组织之前设置好企业策略。某些策略会在启用时删除不合要求的用户，而某些策略无法追溯执行。
{% endhint %}

## 设置企业策略 <a href="#setting-enterprise-policies" id="setting-enterprise-policies"></a>

在您的组织中，通过打开**管理**选项卡并从左侧菜单中选择**策略**来设置策略：

{% embed url="https://bitwarden.com/_gatsby/image/3ed737ae33882d52451effd692957b53/c108ed4ae804218975cdc02452f19206/Screen%20Shot%202023-07-17%20at%202.53.44%20PM.webp?eu=de8f04e7b0c8fa80096ea2d16170353fe63f01a9f80034d13961ecfb4efd9dd325f24c5d239d29b62a605f8b85e547b360c52e341dbcd388c1ed1ea7e864f95c538350b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af81796eb5eefd281781c903a643140e815c36ba2ef8eac13516bc9cb34ab9e7bda10cc4cee27f0216d9a233737049195aea7bb3f0b45574264a1319609bf137a439c9f2531e61215d4203f07a3bd73aaa285ec1fafea243dd7e1481d5d7712ed1&a=w%3D850%26h%3D406%26fm%3Dwebp%26q%3D75&cd=2023-07-17T18%3A54%3A02.234Z" %}
设置策略
{% endembed %}

## 可用的策略 <a href="#available-policies" id="available-policies"></a>

### 要求两步登录 <a href="#require-two-step-login" id="require-two-step-login"></a>

启用**两步登录**策略后将要求所有非所有者/非管理员用户使用任何两步登录方式来访问他们的密码库。如果您使用了 SSO 或身份提供商的 2FA 功能，则无需启用此策略。

{% hint style="warning" %}
**当您启用此策略后，组织内未启用两步登录的用户将被移除组织。**

由于此策略而被移除的用户将收到电子邮件通知，并且必须重新被邀请才能加入组织：

* 现有用户在为他们的密码库启用两步登录之前，将无法接受邀请。
* 新用户将被自动设置为电子邮件方式的两步登录，但可以随时更改。
{% endhint %}

### 主密码要求 <a href="#master-password-requirements" id="master-password-requirements"></a>

启用**主密码**策略将对用户的主密码强度强制执行一组可配置的最低要求。组织可以强制执行：

* 最小主密码复杂度
* 最小主密码长度
* 所需字符类型

密码的复杂度按照 0（弱）到 4（强）的比例计算。Bitwarden 使用 [zxcvbn 库](https://github.com/dropbox/zxcvbn)来计算密码复杂度。

使用**要求现有成员更改他们的密码**选项以要求现有的、不合规的组织成员在下次登录时更新他们的主密码。

### 账户恢复管理 <a href="#account-recovery-administration" id="account-recovery-administration"></a>

启用**主密码重置**策略将允许所有者和管理员使用[密码重置功能](admin-password-reset.md)来重置已注册用户的主密码。默认情况下，用户需要[自行注册密码重置](admin-password-reset.md#self-enroll-in-password-reset)，但是，要对受邀用户强制自动注册，可以使用[自动注册](enterprise-policies.md#automatic-enrollment)选项。

要在您的组织中使用受信任设备 SSO，必须开启账户恢复管理策略。

{% hint style="info" %}
在激活该策略之前，必须先启用**单一组织**策略。

同理，必须先禁用**账户恢复管理**策略，才能禁用**单一组织**策略。
{% endhint %}

#### 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

打开**自动注册**选项将在新用户[加入组织的邀请被接受后](user-management.md#accept)自动注册密码重置功能并阻止他们撤销。

{% hint style="info" %}
已经在组织中的用户不会被注册密码重置，而是需要[自行注册](admin-password-reset.md#self-enroll-in-password-reset)。
{% endhint %}

### 密码生成器 <a href="#password-generator" id="password-generator"></a>

启用**密码生成器**策略将对任何用户生成的密码强制执行一组可配置的最低要求。组织可以强制执行：

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

启用**单一组织**策略将限制组织内的非所有者/非管理员成员加入其他组织或创建其他组织。

{% hint style="warning" %}
**启用此策略后，本组织中属于多个组织成员的用户将被从本组织中移除。**

由于此策略而被移除的用户将收到电子邮件通知，并且必须重新被邀请才能加入组织。除非用户将自己从所有其他组织中移除，否则他们将无法接受加入组织的邀请。
{% endhint %}

### 要求单点登陆验证 <a href="#require-single-sign-on-authentication" id="require-single-sign-on-authentication"></a>

启用**要求单点登录验证**策略将要求非所有者/非管理员用户使用企业单点登录进行登录。有关更多信息，请参阅 [SSO 登录的使用](../login-with-sso/using-login-with-sso.md)。

{% hint style="info" %}
在激活此策略之前，必须先启用**单一组织**策略。

同理，必须先禁用**单点登录验证**策略，然后才能禁用**单一组织**策略。
{% endhint %}

### 移除个人密码库 <a href="#remove-individual-vault" id="remove-individual-vault"></a>

启用**移除个人密码库**策略将要求非所有者/非管理员用户通过禁用组织用户对密码库项目的个人所有权来将密码库项目保存到组织。

在添加项目界面上将向用户显示一条横幅，表明某个策略正在影响他们的所有权选项。

{% hint style="info" %}
在实施本策略之前或加入本组织之前创建的密码库项目将保留在用户的个人密码库中。
{% endhint %}

### 禁用 Send <a href="#disable-send" id="disable-send"></a>

启用**禁用 Send** 策略将阻止非所有者/非管理员用户使用 [Bitwarden Send](../bitwarden-send/about-send.md) 创建或编辑 Send。受此策略约束的用户仍然可以删除尚未达到[删除日期](../bitwarden-send/send-lifespan.md)的现有 Send。

在 Send 视图中和打开任何现有的 Send 时，会向用户显示一个横幅，以表明某个策略限制他们只能删除 Send。

### Send 选项 <a href="#send-options" id="send-options"></a>

启用 **Send 选项**策略将允许所有者和管理员指定用于创建和编辑 Send 的选项。所有者和管理员不受此政策的约束。选项包括：

| 选项             | 描述                                                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| 不允许用户隐藏其电子邮件地址 | 启用该选项可以禁用[隐藏电子邮件](../bitwarden-send/send-privacy.md#hide-email)选项，这意味着所有[接收到的 Send](../bitwarden-send/receive-a-send.md) 都将包含其发送者信息。 |

### 密码库超时 <a href="#vault-timeout" id="vault-timeout"></a>

设置**密码库超时**策略将允许您：

* 为组织的所有成员（所有者除外）实施最大[密码库超时](../your-vault/vault-timeout-options.md#vault-timeout)持续时间。此选项将超时限制应用于所有客户端应用程序（移动端、桌面端、浏览器扩展等）。
* 为组织的所有成员（所有者除外）设置[密码库超时](../your-vault/vault-timeout-options.md#vault-timeout-action)动作。此选项可以设置为用户首选项、在发生密码库超时时锁定或注销。\
  **注销**选项可用于比如在用户每次访问其密码库时提示用户使用 2FA，并通过定期清除用户机器上的本地数据来防止离线使用。

在密码库超时配置期间将向用户显示一条横幅，表明某个策略正在影响他们的选项。

{% hint style="info" %}
在激活此策略之前，必须启用**单一组织**策略。

因此，您必须先禁用**密码库超时**策略，然后才能禁用**单一组织**策略。
{% endhint %}

### 禁用个人密码库导出 <a href="#disable-personal-vault-export" id="disable-personal-vault-export"></a>

启用**禁用个人密码库导出**策略将禁止您组织的非所有者/非管理员成员[导出其私人密码库数据](../import-export/export-vault-data.md#export-a-personal-vault)。

在网页密码库和 CLI 中，会向用户显示一条消息，以表明某个策略正在影响他们的选项。在其他客户端中，该选项将被简单地禁用。

### 激活自动填充 <a href="#activate-auto-fill" id="activate-auto-fill"></a>

打开**激活自动填充**策略将自动为组织的所有现有和新成员打开浏览器扩展上的[页面加载时自动填充](../password-manager/auto-fill/auto-fill-basics/auto-fill-logins-in-browser-extensions.md#on-page-load)功能。如果愿意，成员也可以为其浏览器扩展关闭或修改页面加载的自动填充行为。

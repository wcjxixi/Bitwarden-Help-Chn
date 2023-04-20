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

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2flohk6BsRKvazjztwvzsJ/fd89ba8b2234956c4c50f69741ab3df3/policies.png?fm=webp&h=446&q=50&w=835" %}
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

{% hint style="warning" %}
启用此策略后，现有的不符合要求的用户**不会**强制要求更改其主密码，也不会从组织中将其移除。这些用户下次更改其主密码时，将强制要求符合此策略。
{% endhint %}

### 主密码重置 <a href="#master-password-reset" id="master-password-reset"></a>

启用**主密码重置**策略将允许所有者和管理员使用[密码重置功能](admin-password-reset.md)来重置已注册用户的主密码。默认情况下，用户需要[自行注册密码重置](admin-password-reset.md#self-enroll-in-password-reset)，但是，[自动注册](enterprise-policies.md#automatic-enrollment)选项可用于受邀用户的强制自动注册：

#### 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

启用**自动注册**选项将在新用户[加入组织的邀请被接受后](user-management.md#accept)自动注册新用户的密码重置功能并阻止他们撤销。

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

启用**单点登录验证**策略将要求非所有者/非管理员用户使用企业单点登录进行登录。有关更多信息，请参阅 [SSO 登录的使用](../login-with-sso/using-login-with-sso.md)。

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

启用**密码库超时**策略将为您组织的所有成员实施最大的密码库超时时间。此策略会将超时限制应用于所有客户端应用程序（移动端、桌面端、浏览器扩展等）。

在密码库超时配置期间将向用户显示一条横幅，表明某个策略正在影响他们的选项。

{% hint style="info" %}
在激活此策略之前，必须启用**单一组织**策略。

因此，您必须先禁用**密码库超时**策略，然后才能禁用**单一组织**策略。
{% endhint %}

### 禁用个人密码库导出 <a href="#disable-personal-vault-export" id="disable-personal-vault-export"></a>

启用**禁用个人密码库导出**策略将禁止您组织的非所有者/非管理员成员[导出其私人密码库数据](../import-export/export-vault-data.md#export-a-personal-vault)。

在网页密码库和 CLI 中，会向用户显示一条消息，以表明某个策略正在影响他们的选项。在其他客户端中，该选项将被简单地禁用。

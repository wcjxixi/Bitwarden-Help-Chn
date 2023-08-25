# =账户恢复

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery/)
{% endhint %}

{% hint style="info" %}
账户恢复适用于当前计划的**企业组织**。与 SSO 登录一样，账户恢复不适用于[经典 2019 企业组织](../../plans-and-pricing/updates-to-bitwarden-plans-2019-2020.md)计划。
{% endhint %}

## 什么是账户恢复？ <a href="#what-is-account-recovery" id="what-is-account-recovery"></a>

账户恢复允许[指定的管理员](account-recovery.md#permissions)恢复企业组织用户帐户并在员工忘记[主密码](../../your-vault/your-master-password.md)时恢复访问权限。通过[启用账户恢复策略](account-recovery.md#activate-account-recovery)为组织激活账户恢复。

个人用户必须注册（通过[自行注册](account-recovery.md#self-enroll-in-password-reset)或使用[自动注册策略选项](account-recovery.md#automatic-enrollment)）才有资格进行账户恢复，因为注册会触发密钥交换，以确保恢复的安全。

**账户恢复不会绕过两步登录或 SSO 登录。**如果为帐户启用了[两步登录方式](../../two-step-login/two-step-login-methods.md)，或者如果您的组织[要求 SSO 身份验证](../../organizations/enterprise-policies.md#single-sign-on-authentication)，您在密码重置后仍将需要使用该方式访问您的密码库。

### 加密 <a href="#encryption" id="encryption"></a>

{% hint style="info" %}
**2021-06-01：**账户恢复功能的发布为所有组织引入了一个全新的 RSA 公钥/私钥对。私钥在存储之前使用组织预先存在的对称密钥进一步加密。

此密钥对在创建新的组织时，在客户端生成并加密。或者对于已有的组织，使用以下方式生成并加密密钥对：

* 导航至**管理** → **人员**界面。
* 更新**设置** → **我的组织**界面上的任何内容。
* 从一种组织类型升级到另一种组织类型。
{% endhint %}

当组织的成员[注册](account-recovery.md#automatic-enrollment)管理员密码重置时，该用户的[加密密钥](../../security/account-encryption-key.md)将使用组织的公钥进行加密。然后将其作为**密码重置密钥**存储。

当执行恢复操作时：

1. 使用组织对称密钥解密组织私钥。
2. 使用已解密的组织私钥解密用户的**密码重置密钥**，从而得到用户的[加密密钥](../../security/account-encryption-key.md)。
3. 用户的加密密钥和主密码散列被替换为新的加密密钥和新的主密码散列，这些散列源自新的主密码。
4. 使用组织的公钥加密用户新的加密密钥，使用新的密钥替换之前的**密码重置密钥**。

任何人，包括执行重置的管理员，都**无法**看到旧的主密码。

### 权限 <a href="#permissions" id="permissions"></a>

管理员密码重置可由[所有者、管理员和允许的自定义用户](member-roles-and-permissions.md)执行。管理员密码重置使用分级权限结构来确定谁可以重置谁的主密码：

* 任何所有者、管理员或允许的自定义用户都可以重置**用户**、**经理**或**自定义用户**的主密码。
* 只有管​​理员或所有者可以重置**管理员**的主密码。
* 只有所有者可以重置其他**所有者**的主密码。

### 事件日志 <a href="#event-logging" id="event-logging"></a>

以下情况会记录[事件](../reporting/event-logs.md)：

* 主密码被重置。
* 用户注册管理员密码重置。
* 用户撤销管理员密码重置。

## 激活账户恢复 <a href="#activate-account-recovery" id="activate-account-recovery"></a>

要为您的企业组织激活主密码重置，请导航到组织的**管理**选项卡，从左侧菜单选择**策略**，然后启用[主密码重置策略](../../organizations/enterprise-policies.md#master-password-reset)：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2uJim3XlFdF89Z0Kkr62tV/6bfd3d883f6d1ae611aca281c810ac40/policies.png?fm=webp&h=446&q=50&w=835" %}

用户需要[自行注册](account-recovery.md#self-enroll-in-password-reset)或[自动注册](account-recovery.md#automatic-enrollment)密码重置，然后才能重置其主密码。

### 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

启用自动注册策略选项将在新用户[加入组织的邀请被接受后](../../organizations/user-management.md#accept)自动注册新用户的密码重置功能。并且会阻止他们[撤销](account-recovery.md#withdraw-enrollment)管理员密码重置。

已经在组织中的用户不会被注册密码重置，需要他们[自行注册](account-recovery.md#self-enroll-in-password-reset)。

{% hint style="success" %}
如果您为组织成员使用自动注册管理员密码重置，我们**强烈建议您通知他们这一功能**。很多 Bitwarden 组织用户在他们的个人密码库中存储私人凭据，应该让他们知道管理员密码重置将允许管理员访问他们的个人密码库。
{% endhint %}

### 自行注册 <a href="#self-enroll-in-password-reset" id="self-enroll-in-password-reset"></a>

要注册密码重置，请在[网页密码库](https://vault.bitwarden.com/)中导航至**设置** → **组织**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4ape19S5L7lf0tAAEyInGR/a2ec66d67ed6ac5813d9364b4a52d075/pwreset-enroll-gif.gif?fm=gif&h=542&q=50&w=1048" %}
注册密码重置
{% endembed %}

将鼠标悬停在您希望注册密码重置的组织上，选择 **⚙️**齿轮下拉菜单，然后选择**注册密码重置**。当您注册密码重置后，组织列表上将显示一个 🔑钥匙图标。如果您愿意，您可以在多个组织中注册管理员密码重置。

### 撤销注册 <a href="#withdraw-enrollment" id="withdraw-enrollment"></a>

注册后，您可以从用于注册的同一下拉菜单中**撤销**密码重置：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4GR176lad9pre4sZN3rA35/29f27ea072ac8c2c243e8241fe29a3cc/pwreset-withdraw.png?fm=webp&h=239&q=50&w=998" %}
撤销密码重置
{% endembed %}

已启用[自动注册](account-recovery.md#automatic-enrollment)策略选项的组织中的用户将**不允许撤销**管理员密码重置。此外，手动更改您的主密码或[轮换您的加密密钥](../../security/account-encryption-key.md)**不会**使您撤销管理员密码重置。

## 重置主密码 <a href="#reset-a-master-password" id="reset-a-master-password"></a>

{% hint style="info" %}
您必须是[所有者、管理员或允许的自定义用户](account-recovery.md#permissions)才能重置主密码。检查本文的[权限](account-recovery.md#permissions)章节以了解您可以重置谁的主密码。
{% endhint %}

要重置企业组织成员的主密码：

1、在[网页密码库](https://vault.bitwarden.com/)中，打开您的组织。

2、打开**管理**标签并导航到**人员**部分。

3、将鼠标悬停在要重置其主密码的用户上，选择 **⚙️**齿轮下拉菜单，然后选择 🔑重置密码：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/26oD8iqDY15SNJXCJlQE71/34ab2dbe79a6f52b58412d869e2afd02/pwreset-reset.png?fm=webp&h=420&q=50&w=835" %}
重置密码
{% endembed %}

4、在重置密码窗口中，为用户创建一个**新密码**。如果您的组织启用了[主密码策略](../../organizations/enterprise-policies.md#master-password)，您将需要创建一个满足实施要求的密码（例如，最少 8 个字符，包含数字）：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/28qKke9XJLj6nTZJjg4mK4/5a1138874c9aa45131b6c1022304eb1e/pwreset-newpw.png?fm=webp&h=502&q=50&w=510" %}
创建新的密码
{% endembed %}

复制新的主密码并使用安全的通讯方式联系用户，例如使用 [Bitwarden Send](../../bitwarden-send/create-a-send.md)。

5、选择**保存**以执行密码重置。这样做会将用户从当前会话中注销。某些客户端应用程序（比如移动应用程序）上的活动会话可能会保持活动长达一小时。

### 密码重置后 <a href="#after-a-password-reset" id="after-a-password-reset"></a>

当您的主密码被重置时，您将收到一封来自 Bitwarden 的电子邮件，通知您这一点。收到此电子邮件后，请联系您的组织管理员，通过诸如 [Bitwarden Send](../../bitwarden-send/create-a-send.md) 等安全渠道获取您的新主密码。

当您使用新的主密码重新获得对密码库的访问权限后，系统将提示您再次更新主密码：

{% embed url="https://bitwarden.com/help/images/organizations/pwreset-temporary.png" %}
更新您的主密码
{% endembed %}

因为主密码应该是**强大**且**易记**的，并且**只有您自己**知道，所以重置后您会被要求更新您的主密码。

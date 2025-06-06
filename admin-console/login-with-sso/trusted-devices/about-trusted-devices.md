# 关于受信任设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/about-trusted-devices/)
{% endhint %}

受信任设备 SSO 允许用户[使用 SSO 进行身份验证](../../../login-with-sso/about-login-with-sso.md)，并使用设备存储的加密密钥解密其密码库，而无需输入主密码。受信任设备必须在登录尝试前注册，或[通过几种不同的方法获得批准](../../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)。

受信任设备 SSO 可为企业终端用户提供零知识和端到端加密的无密码体验。这可以防止用户因忘记主密码而被锁定，让他们享受简化的登录体验。

## 开始使用受信任设备 <a href="#start-using-trusted-devices" id="start-using-trusted-devices"></a>

要开始使用受信任设备 SSO：

1. 为您的组织[设置受信任设备 SSO](setup-sso-with-trusted-devices.md)。
2. 向管理员提供有关[如何批准设备请求](approve-a-trusted-device.md)的信息。
3. 向最终用户提供有关[如何添加受信任设备](../../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)的信息。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

以下选项卡描述了不同的受信任设备程序中的加密过程和密钥交换：

{% tabs %}
{% tab title="入职" %}
当新用户加入组织时，会使用**组织公钥**对其账户加密密钥进行加密，从而创建**账户恢复密钥**（[了解更多](../../../organizations/admin-password-reset.md)）。账户恢复是启用受信任设备 SSO 的先决条件。

然后询问用户是否想要记住或信任此设备。当他们选择这样做时：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2o9o8L0JZMvWZYJvfKGMzj/b7cab59682862c8e782331ed6a2ef9d9/td-create.png?_a=DAJAUVWIZAAB" %}
创建受信任设备
{% endembed %}

1. 客户端生成新的**设备密钥**。该密钥永远不会离开客户端。
2. 客户端生成新的 RSA 密钥对：**设备私钥**和**设备公钥**。
3. 用户的账户加密密钥使用未加密的设备公钥进行加密，然后将结果值作为**公钥-已加密的用户密钥**发送到服务器。
4. **设备公钥**使用用户的账户加密密钥进行加密，然后将结果值作为**用户密钥-已加密的公钥**发送到服务器。
5. **设备私钥**使用第一个设备密钥进行加密，然后将结果值作为**设备密钥-已加密的私钥**发送到服务器。

最重要的是，当用户开始登录时，**公钥-已加密的用户密钥**和**设备密钥-已加密的私钥**将从服务器发送到客户端。

如果用户需要轮换其账户加密密钥，将使用**用户密钥-已加密的公钥**。
{% endtab %}

{% tab title="登录" %}
当用户在已受信任的设备上使用 SSO 进行身份验证时：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/61SSa6ITlRaICIUoCzEiVp/746cf3ba3005b4118d20319e894c47c7/td-use.png?_a=DAJAUVWIZAAB" %}
使用受信任设备
{% endembed %}

1. 用户的**公钥-已加密的用户密钥**（用于解密密码库数据的账户加密密钥的加密版本）从服务器发送到客户端。
2. 用户的**设备密钥-已加密的私钥**（解密**公钥-已加密的用户密钥**所需的未加密版本）从服务器发送到客户端。
3. 客户端使用**设备密钥**对**设备密钥-已加密的私钥**进行解密，**设备密钥**从未离开过客户端。
4. 现在未加密的**设备私钥**用于解密**公钥-已加密的用户密钥**，从而产生用户的账户加密密钥。
5. 用户的账户加密密钥解密密码库数据。
{% endtab %}

{% tab title="批准" %}
当用户使用 SSO 进行身份验证，并选择使用未受信任的设备（即**设备对称密钥**不存在于该设备上）解密其密码库时，他们需要选择一种方法来批准该设备，并选择信任该设备，以便将来无需进一步批准即可使用。接下来会发生什么取决于所选的选项：

* **从其他设备批准：**
  1. 触发[此处](../../../account/log-in-and-unlock/more-log-in-options/log-in-with-device.md#how-it-works)记录的流程后，客户端就获得并解密了账户加密密钥。
  2. 用户现在可以使用解密后的账户加密密钥解密其密码库数据。如果用户选择信任该设备，则会按照**入职**选项卡中的说明与客户端建立信任。
* **请求管理员批准：**
  1. 发起请求的客户端向 Bitwarden 数据库中的验证请求表 POST 一个请求，其中包括账户电子邮件地址、唯一的**身份验证请求公钥**ª 和访问代码。
  2. 管理员可在设备批准页面上[批准或拒绝此请求](approve-a-trusted-device.md)。
  3. 请求获得管理员批准后，被批准客户端会使用请求中包含的**身份验证请求公钥**对用户的账户加密密钥进行加密。
  4. 然后，被批准客户端将加密后的账户加密密钥 PUT 到验证请求记录，并标记为请求已完成。
  5. 发起请求的客户端 GET 到加密后的账户加密密钥，然后使用**身份验证请求私钥**ª 对它进行**本地**解密。
  6. 使用解密后的账户加密密钥，与客户端建立信任关系，详见**入职**选项卡。

ª - **身份验证请求公钥**和**私钥**是为每一个无密码登录请求生成的唯一密钥，其存在时间与请求的存在时间相同。未被批准的请求，请求将在 1 周后过期。

* **使用主密码批准：**
  1. 按照安全白皮书中「[身份验证和解密](../../../security/bitwarden-security-whitepaper.md#authentication-and-decryption)」部分的说明，获取并解密用户的账户加密密钥。
  2. 使用解密后的账户加密密钥，按照**入职**选项卡中的说明与客户建立信任。
{% endtab %}

{% tab title="密钥轮换" %}
{% hint style="info" %}
只有拥有主密码的用户才能轮换其[账户加密密钥](../../../security/encryption/encryption-key-rotation.md)。[了解更多](about-trusted-devices.md#impact-on-master-passwords)。
{% endhint %}

当用户轮换其[账户加密密钥](../../../security/encryption/encryption-key-rotation.md)时，正常轮换过程如下：

1. **用户密钥-已加密的公钥**从服务器发送到客户端，然后使用旧的账户加密密钥（又称**用户密钥**）对其解密，得到**设备公钥**。
2. 使用未加密的设备公钥对用户的新的账户加密密钥进行加密，然后将结果值作为新的**公钥-已加密的用户密钥**发送到服务器。
3. 使用用户的新的账户加密密钥对设备公钥进行加密，然后将结果值作为新的**用户密钥-已加密的公钥**发送到服务器。
4. 为此用户持久保存在服务器上的所有其他设备的受信任设备加密密钥都会被清除。这样，服务器上就只保留该单个设备所需的三个密钥（**公钥-已加密的用户密钥**、**用户密钥-已加密的公钥**和在此过程中未被更改的**设备密钥-已加密的私钥**）。

任何现在未受信任的客户端都必须通过**批准**选项卡中说明的方法之一重新建立信任。
{% endtab %}
{% endtabs %}

### 用于受信设备的密钥 <a href="#keys-used-for-trusted-devices" id="keys-used-for-trusted-devices"></a>

本表格提供了有关上述过程中所使用的每一种密钥的更多信息：

| 密钥          | 详细信息                                                      |
| ----------- | --------------------------------------------------------- |
| 设备密钥        | AES-256 CBC HMAC SHA-256，长度为 512 位（其中密钥 256 位，HMAC 256 位） |
| 设备私钥和设备公钥   | RSA-2048 OAEP SHA1，长度为 2048 位                             |
| 公钥-已加密的用户密钥 | RSA-2048 OAEP SHA1                                        |
| 用户密钥-已加密的公钥 | AES-256 CBC HMAC SHA-256                                  |
| 设备密钥-已加密的私钥 | AES-256 CBC HMAC SHA-256                                  |

### 对主密码的影响 <a href="#impact-on-master-passwords" id="impact-on-master-passwords"></a>

虽然使用受信任设备 SSO 可以消除对主密码的需求，但并非在所有情况下都能消除主密码本身：

* 如果用户是在受信任设备 SSO 激活**之前**入职的，或者如果他们从组织邀请中选择了**创建账户**，则他们的账户将保留其主密码。
* 如果用户是在受信任设备 SSO 激活**之后**入职的，并从组织邀请中选择**登录** → **企业 SSO** 进行 [JIT 配置](../../../login-with-sso/login-with-sso-faqs.md#q-how-does-login-with-sso-work-for-new-users-just-in-time)，则他们的账户将无需拥有主密码。如果您更改为主密码[成员解密选项](../../../login-with-sso/member-decryption-options.md)，只要这些用户仍然是组织的成员，系统就会在他们登录时提示创建一个主密码（[了解更多](setup-sso-with-trusted-devices.md)）。
* 如果使用账户恢复功能恢复了用户账户，就必须为其分配一个主密码。目前，有了主密码后，就无法将其从账户中移除，因此，为了避免出现这种结果，我们建议：(i) 指导用户将数据导出到备份中；(ii) 完全删除丢失的账户；(iii) 要求用户[使用受信任设备重新入职到您组织](../../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)；(iv) 用户完成这些后，指导他们导入备份。

{% hint style="danger" %}
对于那些因使用受信任设备 SSO 而没有主密码的账户，[将其从您的组织中移除](../../../organizations/user-management.md#offboard-users)或[撤销其访问权限](../../../organizations/user-management.md#revoke-access)将切断其对 Bitwarden 账户的所有访问权限，除非：

1. 您事先使用[账户恢复](../../../organizations/admin-password-reset.md)功能为其分配了主密码。
2. 用户在账户恢复后至少登录一次，以便完全完成账户恢复流程。

此外，除非在将用户从组织中删除之前执行上述步骤，否则用户将无法重新加入您的组织。在这种情况下，用户将需要[删除其账户](../../../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，并接收新的邀请以创建账户并加入您的组织。

撤销对组织的访问权限，但不将其从组织中移除，仍可让他们登录 Bitwarden 并**只能**访问其个人密码库。
{% endhint %}

### 对其它功能的影响 <a href="#impact-on-other-features" id="impact-on-other-features"></a>

根据您的客户端内存中是否有主密码哈希（由客户端应用程序最初被访问的方式决定），它可能会表现出以下行为变化：

| 功能       | 影响                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 验证       | <p>Bitwarden 客户端应用程序中有许多功能通常需要输入主密码才能使用，包括<a href="../../../import-export/export-vault-data.md">导出密码库数据</a>、更改<a href="../../../account/two-step-login/setup-guides/two-step-login-methods.md">两步登录设置</a>、检索 <a href="../../../password-manager/developer-tools/personal-api-key-for-cli-authentication.md">API 密钥</a>等。</p><p>如果用户不使用主密码访问客户端，<strong>所有这些功能</strong>都将使用基于电子邮件的 TOTP 验证来取代主密码确认。</p> |
| 密码库锁定/解锁 | <p>一般情况下，被锁定的密码库可以使用主密码解锁。如果用户不使用主密码访问客户端，则被锁定的客户端应用程序只能使用 <a href="../../../account/log-in-and-unlock/more-unlock-options/unlock-with-pin.md">PIN</a> 或<a href="../../../account/log-in-and-unlock/more-unlock-options/unlocking-with-biometrics.md">生物识别</a>解锁。</p><p>如果客户端应用程序既没有启用 PIN 也没有启用生物识别，则密码库将始终注销而不是锁定。解锁和登录<strong>始终</strong>需要互联网连接。</p>                                               |
| 主密码重新提示  | 如果用户不使用主密码解锁其密码库，则[主密码重新提示](../../../your-vault/vault-items.md#protect-individual-items)将被禁用。                                                                                                                                                                                                                                                                                                          |
| 更改电子邮箱地址 | [没有主密码](about-trusted-devices.md#impact-on-master-passwords)的用户将**无法**更改他们电子邮箱地址。                                                                                                                                                                                                                                                                                                                      |
| CLI      | [没有主密码](about-trusted-devices.md#impact-on-master-passwords)的用户将**无法**访问密码管理器 CLI。                                                                                                                                                                                                                                                                                                                     |

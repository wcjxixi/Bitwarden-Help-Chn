# JIT 配置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/jit-provisioning/)
{% endhint %}

使用 [SSO](about-sso.md) 的企业组织支持即时 (JIT) 配置成员。除 **SSO 指南**中记载的 SAML 或 OIDC 配置流程外，无需额外设置即可实现 JIT 功能。

## 推荐的 JIT 策略 <a href="#recommended-jit-strategy" id="recommended-jit-strategy"></a>

优化的 JIT 配置策略可以为您的成员提供最简单的注册流程。作为管理员，通过以下方式帮助您的成员快速轻松地加入：

* **务必**通过 [SCIM](../manage-members/scim/about-scim.md)、[目录连接器](../manage-members/directory-connector/about-directory-connector.md)或[手动](../manage-members/user-management.md#confirm)向成员发送电子邮件邀请。
  * 使用 SCIM 或目录连接器的额外优势是，可将[群组及群组成员资格](../manage-members/groups.md)同步到您的组织（即时配置本身不支持这一功能），自动将成员分配到群组中，以实现高效的[集合分配](../manage-shared-items/collections/assign-users-to-collections.md)。
* **不应**允许成员在被邀请加入组织之前预先创建 Bitwarden 账户。

{% hint style="success" %}
通过邀请发起的新账户 JIT 配置可以绕过管理员或成员通常需要执行的几个步骤（请参阅[**非标准注册**](jit-provisioning.md#non-standard-signup)）。该策略还可以确保由于[受信任设备](trusted-devices/about-trusted-devices.md)或 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 实施结果而不应拥有主密码的成员不会在其账户上设置主密码。
{% endhint %}

### 成员注册流程 <a href="#member-signup-process" id="member-signup-process"></a>

使用**推荐的 JIT 策略**配置成员只需要：

1. 点击组织邀请电子邮件中包含的**完成账户设置**按钮。
2. 出现提示时，使用其 SSO 凭据登录其 IdP。如果成员已与 IdP 建立了活动会话，则跳过此步骤。
3. 根据您的组织选择的[解密方式](sso-decryption-options.md)：
   * 如果使用**主密码解密**方式，请创建一个主密码。
   * 如果使用**受信任设备解密**方式，请选择是否记住该设备。

完成后，成员将被移动到`已接受`状态。届时，他们需要由管理员进行[确认](../manage-members/user-management.md#confirm)。

### 非标准注册 <a href="#non-standard-signup" id="non-standard-signup"></a>

在偏离**推荐的 JIT 策略**的情况下，成员的注册流程将有所不同：

{% tabs %}
{% tab title="未发送邀请" %}
在未向成员发送邀请的情况下，他们仍然可以相对容易地加入组织。请指示成员按照[这些说明](./)操作，除非他们需要使用已有的 Bitwarden 账户加入，在这种情况下，请参考**已有账户**选项卡。

{% hint style="success" %}
除非您的组织已经[声明了域名](../oversight-visibility/claimed-domains/claimed-domains.md) ，否则管理员需要向成员提供 SSO 标识符 。他们需要在注册过程中输入该标识符。
{% endhint %}
{% endtab %}

{% tab title="已有账户" %}
{% hint style="danger" %}
需要遵循此流程的成员（不同于采用[信任设备解密](trusted-devices/about-trusted-devices.md)机制的组织中遵循标准成员注册流程的成员）将在其账户上设置主密码。若组织要求成员不得设置主密码，请指导用户执行以下操作：

1. 从现有账户导出数据。
2. 删除现有账户。
3. 按照标准的**成员注册流程** ，通过即时配置 (JIT) 方式创建新 Bitwarden 账户。
4. 将数据从原有账户导入新账户。
{% endhint %}

如果成员需要使用现有的 Bitwarden 账户加入组织：

1. 管理员需向成员 Bitwarden 账户关联的电子邮箱发送邀请电子邮件。该成员必须通过电子邮件邀请才能加入您的组织。
2. 指导用户**接受邀请**，并在邀请电子邮件引导的登录界面上使用他们的主密码登录。即使激活了[要求单点登录身份验证](../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)策略，该成员在完成组织确认前仍无法使用 SSO 功能。
3. 确认后，成员即可使用 SSO 登录，如果[要求单点登录身份验证](../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)策略处于激活状态，系统将强制要求其通过 SSO 登录。
{% endtab %}
{% endtabs %}

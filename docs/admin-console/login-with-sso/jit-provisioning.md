# JIT 配置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/jit-provisioning/)
{% endhint %}

使用 SSO 的企业组织支持即时配置 (JIT) 成员。除 SSO 指南中记录的 SAML 或 OIDC 设置过程外，无需额外配置即可支持 JIT。

## 推荐的 JIT 策略

一个优化的即时配置策略可以为您的成员提供最简单的注册流程之一。作为管理员，通过以下方式帮助您的成员快速轻松地加入：

* **应**通过 [SCIM](https://bitwarden.com/help/about-scim/)、[ 目录连接器](https://bitwarden.com/help/directory-sync/)或[手动](https://bitwarden.com/help/managing-users/#confirm)向成员发送电子邮件邀请。
  * 使用 SCIM 或目录连接器的额外好处是，[ 组及其成员关系](https://bitwarden.com/help/about-groups/)可以同步到您的组织，而即时配置本身不支持这一功能，可以自动将成员分配到组中，以实现简化的[收集分配 ](https://bitwarden.com/help/assign-users-to-collections/)。
* **不应**允许成员在被邀请加入组织之前预先创建 Bitwarden 账户。

{% hint style="info" %}
由邀请发起的 JIT 新账户配置绕过了管理员或成员可能需要执行的几个步骤（参见<强>非标准注册 <强>）。这种策略还确保了由于<强>受信任设备<强>或<强>密钥连接器<强>实施结果而不应拥有主密码的成员不会在其账户上设置主密码。
{% endhint %}

### 成员注册流程

使用<强>推荐 JIT 策略<强>配置的成员只需要：

1. 选择组织邀请邮件中包含的**完成账户设置**按钮。
2. 当提示时，使用其 SSO 凭证登录其 IdP。如果他们与 IdP 有活动的会话，则跳过此步骤。
3. 根据您组织选择的[解密方法 ](https://bitwarden.com/help/sso-decryption-options/)：
   * 如果**主密码解密** ，则创建一个主密码。
   * 如果**受信任设备解密** ，请选择是否记住该设备。

完成后，成员将被移动到`已接受`状态。届时，他们需要由管理员进行[确认 ](https://bitwarden.com/help/managing-users/#confirm)。

### 非标准注册

在偏离**推荐 JIT 策略**的情况下，成员的注册过程将有所不同：

{% tabs %}
{% tab title="未发送邀请" %}
在未向成员发送邀请的情况下，组织仍然可以相对容易地加入。请指示成员遵循[这些说明 ](https://bitwarden.com/help/using-sso/)，除非他们需要使用已有的 Bitwarden 账户加入，在这种情况下，请参考**已有账户**选项卡。

{% hint style="success" %}
除非您的组织已经[注册了域名 ](https://bitwarden.com/help/claimed-domains/)，否则管理员需要向成员提供 [SSO 标识符 ](https://bitwarden.com/help/sso-faqs/#configuration)。他们需要在注册过程中输入该标识符。
{% endhint %}
{% endtab %}

{% tab title="已有账户" %}
{% hint style="danger" %}
需要遵循此流程的成员，与使用[可信设备解密](https://bitwarden.com/help/about-trusted-devices/)的组织遵循标准**成员注册流程**的成员不同，其账户将设置主密码。如果要求组织成员不设置主密码，请指示用户：

1. 从现有账户导出数据。
2. 删除现有账户。
3. 按照标准**成员注册流程** ，通过即时配置（JIT）方式创建一个新的 Bitwarden 账户。
4. 将数据从现有账户导入新账户。
{% endhint %}

如果成员需要使用现有的 Bitwarden 账户加入组织：

1. 作为管理员，向与成员 Bitwarden 账户关联的邮箱地址发送邀请邮件。除非通过邮件邀请，否则该成员无法加入您的组织。
2. 指导用户 **接受邀请** ，并在邀请邮件引导的登录屏幕上使用他们的主密码登录。即使激活了 [要求单点登录认证 ](https://bitwarden.com/help/policies/#require-single-sign-on-authentication)策略，该成员在确认加入组织之前也无法使用 SSO。
3. 确认后，成员可以使用 SSO 登录，如果[要求单点登录认证](https://bitwarden.com/help/policies/#require-single-sign-on-authentication)策略已激活，则必须这样做。
{% endtab %}
{% endtabs %}

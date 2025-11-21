# 关于 SSO 登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-sso/)
{% endhint %}

## 什么是 SSO 登录？ <a href="#what-is-login-with-sso" id="what-is-login-with-sso"></a>

SSO 登录是 Bitwarden 的单点登录解决方案。使用 SSO 登录，[企业组织](../organizations-overview.md#types-of-organizations)可以利用其现有的身份提供程序，通过 Bitwarden 使用 **SAMl 2.0** 或 **Open ID Connect (OIDC)** 协议对用户进行身份验证。

SSO 登录的独特之处在于它保留了我们的零知识加密模型。Bitwarden 没有人可以访问您的密码库数据，包括**您的身份提供程序**。这就是 SSO 登录将**身份验证和解密分离**的原因。在所有 SSO 登录的实施中，您的身份提供程序不能也不会访问解密密码库数据所需的解密密钥。

在大多数情况下，解密密钥是用户的[主密码](../../account/log-in-and-unlock/your-master-password.md)，他们全权负责，但是组织自托管 Bitwarden 可以使用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 作为解密密码库数据的替代方法。

{% hint style="info" %}
除非您使用的是受信任设备，否则 SSO 登录并不能取代登录时要求的主密码和电子邮箱。SSO 登录会利用您现有的身份提供程序 (IdP) 来验证您进入 Bitwarden 的身份，但您仍必须输入主密码和电子邮箱才能解密您的密码库数据。

不过，如果您使用的是受信任设备，设备存储的加密密钥将取代输入主密码来解密密码库数据。
{% endhint %}

使用单点登录 (SSO)，[企业组织](../organizations-overview.md#types-of-organizations)可以利用其现有的身份提供程序对 Bitwarden 的成员进行身份验证。企业组织 SSO 包括：

* [SAML 2.0](sso-guides/generic-saml.md) 和 [OIDC](sso-guides/generic-oidc.md) 配置选项，支持与各类身份提供程序的集成。
* 一项[企业策略](../oversight-visibility/enterprise-policies.md#single-sign-on-authentication)，可选择**要求**非管理员用户使用单点登录登录 Bitwarden。
* 一项[企业策略](../oversight-visibility/enterprise-policies.md#single-sign-on-authentication)，可选择允许从 IdP 启动的非 SSO App 更轻松地自动填充。
* 用于安全数据访问工作流的两个不同的[成员解密选项](sso-decryption-options.md)。
* 通过 SSO 即时 (JIT) 配置成员。





SSO 登录是一种灵活的解决方案，可以满足您的企业需求。SSO 登录包括：

* [SAML 2.0](sso-guides/generic-saml.md) 和 [OIDC](sso-guides/generic-oidc.md) 配置选项，支持与各类身份提供程序的集成。
* 一项[企业策略](../oversight-visibility/enterprise-policies.md#single-sign-on-authentication)，可选择要求非管理员用户使用单点登录登录 Bitwarden。
* 用于安全数据访问工作流的两个不同的[成员解密选项](sso-decryption-options.md)。
* 通过 SSO 进行「即时」的最终用户入职。
* 自动登录到 App 而无需使用来自您的身份提供程序仪表板中的 SSO。

{% hint style="success" %}
将 SSO 与 Bitwarden 结合使用保留了我们的零知识加密模型。 Bitwarden 的任何人均无法访问您的数据，同样，您的身份提供出现也不能访问您的数据。这就是 SSO 将身份验证和解密解耦。在所有实现中，您的身份提供出现不能也不会访问解密密码库数据所需的解密密钥。

虽然身份验证是通过 IdP 处理的，但数据的解密是由多种[解密方式](sso-decryption-options.md)之一控制的。
{% endhint %}

## 如何开始使用 SSO 登录？ <a href="#how-do-i-start-using-login-with-sso" id="how-do-i-start-using-login-with-sso"></a>

SSO 登录适用于所有[企业组织](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#enterprise-organizations)的客户 。如果您是 Bitwarden 的新手，我们很乐意通过我们的专用注册页面帮助您完成设置帐户和开始一个 7 天免费试用企业组织的过程：

{% embed url="https://bitwarden.com/go/start-enterprise-trial/" %}

拥有企业组织后，部署应包括以下的步骤：

1. 按照我们的 [SAML 2.0](sso-guides/generic-saml.md) 和 [OIDC](sso-guides/generic-oidc.md) 实施指南之一配置和部署使用主密码解密的 SSO 登录。
2. 使用主密码解密测试[最终用户的 SSO 登录体验](../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)。
3. （**如果自托管**）查看我们不同的[成员解密选项](sso-decryption-options.md)，以确定使用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 的方式是否适合您的组织。
4. （**如果自托管**）如果您对实施 Key Connector 感兴趣，请[联系我们](https://bitwarden.com/contact/)，我们将帮助您开始[部署 Key Connector](../../self-hosting/key-connector/deploy-key-connector.md)。
5. 培训您的组织成员如何[使用 SSO 登录](../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)。

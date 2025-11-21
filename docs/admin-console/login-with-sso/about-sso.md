# 关于 SSO

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-sso/)
{% endhint %}

通过单点登录 (SSO) 功能，[企业组织](../organizations-overview.md#types-of-organizations)可以利用现有身份提供程序 (IdP) 对成员进行 Bitwarden 身份验证。企业组织的 SSO 功能包括：

* 支持与多种身份提供程序集成的 [SAML 2.0](sso-guides/generic-saml.md) 和 [OIDC](sso-guides/generic-oidc.md) 配置选项。
* 一项[企业策略](../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)，可选择要求非管理成员使用 SSO 登录 Bitwarden。
* 一项[企业策略](../oversight-visibility/enterprise-policies.md#automatically-log-in-users-for-allowed-applications)，可选择允许更轻松地在从 IdP 启动的非 SSO App 中自动填充。
* 用于安全数据访问流程的多个不同的[成员解密选项](sso-decryption-options.md)。
* 通过 SSO 实现成员[即时 (JIT) 配置](jit-provisioning.md)。

{% hint style="success" %}
将 SSO 与 Bitwarden 结合使用保留了我们的零知识加密模型。Bitwarden 没有任何人可以访问您的数据，同样，您的身份提供程序也不能访问您的数据。这正是 SSO 将身份验证与解密操作分离的原理。在所有实现方案中，您的身份提供程序不能也不会访问解密密码库数据所需的解密密钥。

虽然身份验证是由您的 IdP 处理，但数据的解密由多种[解密方式](sso-decryption-options.md)之一进行控制。
{% endhint %}

{% embed url="https://bitwarden.com/assets/76IOpVRQv886zcUYIM2HF0/36300f14123231d0da18081adcc9962b/sso-workflow-3.png?w=856&fm=avif" %}
SSO 和主密码解密
{% endembed %}

如果您是 Bitwarden 的新手，请[开始 7 天企业版免费试用](../../plans-and-pricing/start-an-enterprise-trial-with-your-bitwarden-account.md)以开始测试 SSO。我们建议在测试 SSO 时执行以下步骤：

1. 使用您选择的 IdP 的 **SSO 指南**之一配置您的 SSO 集成。如果您的 IdP 未列出，您可以使用[通用 SAML](sso-guides/generic-saml.md) 或[通用 OIDC](sso-guides/generic-oidc.md) 指南。
2. 使用主密码解密测试[成员登录体验](./)。
3. 评估不同的[成员解密选项](sso-decryption-options.md)是否适合您的实现，如果适合，则开始配置该解密选项。
4. 根据实施的具体情况，向成员提供有关如何[使用 SSO 登录](./)的信息。

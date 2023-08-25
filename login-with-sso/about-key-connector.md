# 关于 Key Connector

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-key-connector/)
{% endhint %}

## 什么是 Key Connector？ <a href="#what-is-key-connector" id="what-is-key-connector"></a>

Key Connector（密钥连接器）是一个用于促进**客户管理的加密**的自托管应用程序，其允许企业组织向 Bitwarden 客户端提供加密密钥。Key Connector 在与现有服务相同的网络上作为 docker 容器运行，并且可以与 [SSO 登录](about-login-with-sso.md)一起使用为组织提供加密密钥，作为使用主密码进行密码库解密的一种替代（[了解更多](about-key-connector.md#why-use-key-connector)）。

Key Connector 需要连接到存储了已加密用户密钥的数据库和用于加密和解密已存储的用户密钥的 RSA 密钥对。Key Connector 可以使用各类数据库提供程序（例如 MSSQL、PostgreSQL、MySQL）和密钥对存储提供程序（例如 Hashicorp Vault、云 KMS 提供程序、本地 HSM 设备）来进行[配置](deploy-key-connector.md)，以满足您公司的基础架构要求。

{% embed url="https://bitwarden.com/help/images/sso/keyconnector/keyconnector-diagram-2.png" %}
Key Connector 架构
{% endembed %}

## 为什么要使用 Key Connector？ <a href="#why-use-key-connector" id="why-use-key-connector"></a>

**在利用主密码解密的实施方案中**，您的身份提供程序用于处理身份验证，同时密码库解密还需要成员的主密码。这种关注点分离是一个重要的步骤，用以确保只有组织成员可以访问用于解密组织敏感密码库数据所需的密钥。

**在利用 Key Connector 进行解密的实施中**，您的身份提供程序仍然用于处理身份验证，但密码库解密由 Key Connector 处理。通过访问加密的密钥数据库（_见上图_），Key Connector 在用户登录时为其提供解密密钥，而不再需要主密码。

我们经常把 Key Connector 的实施称为利用**客户管理的加密**，因为您的企业对 Key Connector 应用程序及其提供的密码库解密密钥的管理负有全部责任。对于准备部署和维护客户管理的加密环境的企业来说，Key Connector 有助于简化密码库的登录体验。

### 对主密码的影响 <a href="#impact-on-master-passwords" id="impact-on-master-passwords"></a>

由于 Key Connector 使用客户管理的解密密钥代替基于主密码的解密，因此组织成员将被**要求从他们的帐户中移除主密码**。移除后，所有密码库解密操作都将使用已存储的用户密钥进行。除了登录之外，这还会对离职和以及您应该注意的其他功能产生一些影响。

{% hint style="warning" %}
目前，无法为已移除了主密码的帐户重新创建主密码。

因此，组织所有者和管理员无法移除他们的主密码，并且即使使用 SSO 也必须继续使用他们的主密码。可以将已移除主密码的用户提升为所有者或管理员，但我们**强烈建议**您的组织始终至少有一个拥有主密码的所有者。
{% endhint %}

### 对组织成员的影响 <a href="#impact-on-organization-membership" id="impact-on-organization-membership"></a>

Key Connector 要求用户[移除他们的主密码](about-key-connector.md#impact-on-master-passwords)，改用使用公司拥有的加密密钥数据库来解密用户的密码库。由于无法为已移除主密码的帐户重新创建主密码，这意味着，一旦帐户使用 Key Connector 解密，就所有的意图和目的而言，都**属于组织所有**。

这些帐户**不能离开组织**，因为这样做他们将失去任何解密密码库数据的方法。同样，如果组织管理员从组织中移除帐户，该帐户将失去任何解密密码库数据的方法。

### 对其他功能的影响 <a href="#impact-on-other-features" id="impact-on-other-features"></a>

| 功能           | 影响                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **验证**       | <p>Bitwarden 客户端应用程序中有许多功能通常需要输入主密码才能使用，包括<a href="../import-export/export-vault-data.md">导出密码库数据</a>、更改<a href="../two-step-login/two-step-login-methods.md">两步登录</a>设置、检索 <a href="../password-manager/developer-tools/personal-api-key-for-cli-authentication.md">API 密钥</a>等。<br></p><p><strong>所有这些功能</strong>都将使用基于 TOTP 验证的电子邮件取代主密码验证。</p>                                                                                            |
| **密码库锁定/解锁** | <p>在一般情况下，可以使用主密码<a href="../your-vault/vault-timeout-options.md#vault-timeout-action">解锁锁定的密码库</a>。当您的组织使用 Key Connector 时，锁定的客户端应用程序只能使用 <a href="../your-vault/unlock-with-pin.md">PIN 码</a>或<a href="../your-vault/unlocking-with-biometrics.md">生物识别</a>解锁。<br></p><p>如果客户端应用程序既未启用 PIN 码也未启用生物识别，则密码库将始终注销而不是锁定。与解锁不同，登录<strong>总是</strong>需要互联网连接（<a href="../your-vault/vault-timeout-options.md#vault-timeout-action">了解更多</a>）。</p> |
| **主密码重新提示**  | 使用 Key Connector 后，对于因实施密钥连接器而移除了其主密码的任何用户，[主密码重新提示](../your-vault/vault-items.md#protect-individual-items)将被禁用。                                                                                                                                                                                                                                                                                                                              |
| **管理员密码重置**  | 使用 Key Connector 后，对于因实施密钥连接器而移除了其主密码的任何用户，[管理员密码重置](../admin-console/user-management/account-recovery.md)将被禁用。                                                                                                                                                                                                                                                                                                                               |
| **紧急访问**     | <p>使用 Key Connector 后，对于因实施密钥连接器而移除了其主密码的任何用户，紧急访问的<a href="../security/emergency-access.md#user-access">账户接管选项</a>将被禁用。<br><br>根据既定的紧急访问工作流程，受信任的紧急联系人仍可以<strong>查看</strong>授予人的个人密码库数据。</p>                                                                                                                                                                                                                                                 |

## 如何开始使用 Key Connector？ <a href="#how-do-i-start-using-key-connector" id="how-do-i-start-using-key-connector"></a>

要开始使用客户管理加密的 Key Connector，请查看以下要求：

{% hint style="warning" %}
加密密钥的管理非常敏感，**仅建议拥有可以安全支持部署和管理密钥服务器的团队和基础架构的企业使用**。
{% endhint %}

要使用 Key Connector，您必须：

* [拥有一个企业组织](../plans-and-pricing/password-manager/about-bitwarden-plans.md#enterprise-organizations)
* [拥有一个自托管的 Bitwarden 服务器](../self-hosting/)
* [拥有一个活跃的 SSO 实施](about-login-with-sso.md)
* [激活单一组织和单点登录策略](../organizations/enterprise-policies.md)

如果您的组织满足或能够满足这些要求，包括拥有可以支持密钥服务器管理的团队和基础设施，请[联系我们](https://bitwarden.com/contact)，我们将为您激活 Key Connector。

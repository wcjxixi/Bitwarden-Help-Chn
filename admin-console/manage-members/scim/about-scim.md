# 关于 SCIM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/about-scim/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置成员和群组。

Bitwarden 服务器提供了一个 SCIM 端点，该端点具有有效的 [SCIM API 密钥](about-scim.md#setting-up-scim)，将接受来自您的身份提供程序 (IdP) 的用户和群组的配置和取消配置请求。

{% hint style="info" %}
SCIM 集成适用于**团队组织和企业组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

Bitwarden 支持使用标准属性映射的 SCIM v2，并提供以下官方 SCIM 集成：

* [Azure 活动目录](microsoft-entra-id-scim-integration.md)
* [Okta](okta-scim-integration.md)
* [OneLogin](onelogin-scim-integration.md)
* [JumpCloud](jumpcloud-scim-integration.md)
* [Ping Identity](../../login-with-sso/implementation-guides/ping-identity-saml-implementation.md)

{% hint style="success" %}
除了上面列出的提供程序之外，Bitwarden 还提供与 Google Workspace 的测试版集成。[联系我们以了解更多信息](https://bitwarden.com/contact/)。
{% endhint %}

## 设置 SCIM <a href="#setting-up-scim" id="setting-up-scim"></a>

要设置 SCIM，您的 IdP 需要一个 SCIM URL 和 API 密钥来向 Bitwarden 服务器发出授权请求。这些值可以通过导航到管理控制台的**设置** → **SCIM 配置**获取：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sw1kuK7GuZ3dfQkkbs6rV/a4f4e18e561733297338e4ed44c6ed8c/2024-12-03_15-25-46.png?_a=DAJAUVWIZAAB" %}
SCIM 预配
{% endembed %}

{% hint style="success" %}
我们建议使用我们的专用指南之一来设置 Bitwarden 与 [Azure AD](microsoft-entra-id-scim-integration.md)、[Okta](okta-scim-integration.md)、[OneLogin](onelogin-scim-integration.md) 或 [JumpCloud](jumpcloud-scim-integration.md) 的 SCIM 集成。
{% endhint %}

### 属性要求 <a href="#required-attributes" id="required-attributes"></a>

Bitwarden 使用此处列出的标准 SCIM v2 属性名称，但每个 IdP 也可以使用在配置期间映射到 Bitwarden 的备用名称。

#### 用户属性 <a href="#user-attributes" id="user-attributes"></a>

对于每个用户，Bitwarden 将使用以下属性：

* 表明用户处于 `active` 状态的指示（**必填**）
* `email`ª 或 `userName`（**必填**）
* `displayName`
* `externalId`

ª - 由于 SCIM 允许用户将多个电子邮箱地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

#### 群组属性 <a href="#group-attributes" id="group-attributes"></a>

对于每个用户，Bitwarden 将使用以下属性：

* `displayName`（**必填**）
* `members`ª
* `externalId`

ª - `members` 是一个对象数组，每个对象代表该群组中的一个用户。

## 撤销和恢复访问权限 <a href="#revoking-and-restoring-access" id="revoking-and-restoring-access"></a>

使用 SCIM 在 Bitwarden 中配置用户后，您可以暂时撤销他们对您的组织及其密码库项目的访问权限。当用户在您的 IdP 中被暂停/停用时，他们对您组织的访问权限将被自动撤销。

{% hint style="success" %}
只有**所有者**可以撤销和恢复其他所有者的访问权限。
{% endhint %}

已撤销访问权限的用户列在组织的**成员**界面的**已撤销**选项卡中，并将：

* 无权访问任何组织密码库项目、集合等。
* 无法使用 [SSO 登录](../../../account/log-in-and-unlock/using-single-sign-on/using-login-with-sso.md)，或使用 [Organizational Duo](../../../account/two-step-login/setup-guides/two-step-login-via-duo.md) 进行两步登录。
* 不受您的组织[策略](../../manage-shared-items/enterprise-policies.md)的约束。
* 不占用许可席位。

{% hint style="danger" %}
对于那些因[使用受信任设备 SSO](../../login-with-sso/trusted-devices/about-trusted-devices.md) 而没有主密码的账户，[将其从您的组织中移除](../user-management.md#offboard-users)将切断其对 Bitwarden 账户的所有访问权限，除非：

1. 您事先使用[账户恢复](../account-recovery.md)功能为其分配了主密码。
2. 用户在账户恢复后至少登录一次，以便全部完成账户恢复工作流程。&#x20;

此外，除非在将用户从组织中删除之前采取上述步骤，否则用户将无法重新加入组织。在这种情况下，用户将被要求[删除其账户](../../../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，并将收到创建账户并加入组织的新邀请。

撤销对组织的访问权限，但不将其从组织中移除，仍允许其登录 Bitwarden 并**只能**访问其个人密码库。
{% endhint %}

了解有关[撤销](../user-management.md#revoke-access)和[恢复](../user-management.md#restore-access)访问权限的更多信息。

## SCIM 事件日志 <a href="#scim-events" id="scim-events"></a>

组织将捕获 SCIM 集成所执行操作的[事件日志](../../reporting/event-logs.md)，包括邀请用户和移除用户，以及创建或删除群组。SCIM 派生的事件将在**成员**列中注册 `SCIM`。

## 已有用户和群组 <a href="#pre-existing-users-and-groups" id="pre-existing-users-and-groups"></a>

在手动或使用目录连接器激活 SCIM 之前，具有用户和群组的组织应注意以下事项：

|       | ...已存在于 IdP 中                                                                  | ...不存在于 IdP 中                         |
| ----- | ------------------------------------------------------------------------------ | ------------------------------------- |
| 已有的用户 | <p>•不会重复</p><p>•不会被迫重新加入组织</p><p>•将根据 IdP 添加到相关群组</p><p>•不会从他们已经是其成员的组织中移除</p> | <p>•不会从组织中移除</p><p>•不会添加或移除群组成员身份</p> |
| 已有的群组 | <p>•不会重复</p><p>•将根据 IdP 添加成员</p><p>•不会移除现有成员</p>                               | <p>•不会从组织中移除</p><p>•不会添加或移除成员</p>     |

{% hint style="info" %}
如果您使用的是 Directory Connector，请确保在激活 SCIM 之前关闭同步。
{% endhint %}

## 更改 Bitwarden 电子邮箱地址 <a href="#changing-bitwarden-email-address" id="changing-bitwarden-email-address"></a>

隶属于使用 SCIM 的组织的用户可以在 Bitwarden 及其组织的相关 IdP 中更改电子邮箱地址。要更改 SCIM 组织中的 Bitwarden 电子邮箱地址，请执行以下操作：

1. 通过导航到设**置** → **我的账户**在 Bitwarden 中更改电子邮箱地址（更多信息请参阅[这里](../../../your-vault/general-faqs.md#q-how-do-i-change-my-email-address)）。
2. 在 Bitwarden 上更改电子邮箱地址后，更新 IdP 或 AD 客户端上的用户值。这可以是 `externalid` 或相应的值，取决于企业对 IdP 的选择。
3. 重新同步 IdP 或 AD 客户端，以实现更改。

{% hint style="info" %}
如果在更新 Bitwarden 电子邮箱之前，用户电子邮箱地址已在 IdP 或 AD 上更新并同步，则更新后的电子邮箱将被视为新的用户。
{% endhint %}

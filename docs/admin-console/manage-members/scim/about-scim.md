# =关于 SCIM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/about-scim/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置成员和群组。

Bitwarden 服务器提供了一个 SCIM 端点，该端点具有有效的 [SCIM API 密钥](about-scim.md#setting-up-scim)，将接受来自您的身份提供程序 (IdP) 的用户和群组的配置和取消配置请求。

{% hint style="info" %}
SCIM 集成适用于**团队版组织和企业版组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用[目录同步](../directory-connector/about-directory-connector.md)作为替代的配置方式。
{% endhint %}

Bitwarden 支持使用标准属性映射的 SCIM v2，并提供以下官方 SCIM 集成：

* [Azure 活动目录](microsoft-entra-id-scim-integration.md)
* [Okta](okta-scim-integration.md)
* [OneLogin](onelogin-scim-integration.md)
* [JumpCloud](jumpcloud-scim-integration.md)
* [Ping Identity](../../login-with-sso/sso-guides/ping-identity-saml-implementation.md)

{% hint style="success" %}
除了上面列出的提供程序之外，Bitwarden 还提供与 Google Workspace 的测试版集成。[联系我们以了解更多信息](https://bitwarden.com/contact/)。
{% endhint %}

## 设置 SCIM <a href="#setting-up-scim" id="setting-up-scim"></a>

要设置 SCIM，您的 IdP 需要一个 SCIM URL 和 API 密钥来向 Bitwarden 服务器发出授权请求。这些值可以通过导航到管理控制台的**设置** → **SCIM 配置**获取：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sw1kuK7GuZ3dfQkkbs6rV/a4f4e18e561733297338e4ed44c6ed8c/2024-12-03_15-25-46.png?_a=DAJAUVWIZAAB" %}
SCIM 预配
{% endembed %}

{% hint style="success" %}
以下部分涵盖了用于配置 SCIM 的通用信息，但 Bitwarden 建议使用以下集成文档之一：

* [JumpCloud](jumpcloud-scim-integration.md)
* [Microsoft Entra ID](microsoft-entra-id-scim-integration.md)
* [Okta](okta-scim-integration.md)
* [OneLogin](onelogin-scim-integration.md)
* [Ping Identity](ping-identity-scim-integration.md)
{% endhint %}

### 属性要求 <a href="#required-attributes" id="required-attributes"></a>

Bitwarden 使用此处列出的标准 SCIM v2 属性名称，但每个 IdP 也可以使用在配置期间映射到 Bitwarden 的备用名称。

#### 用户属性 <a href="#user-attributes" id="user-attributes"></a>

对于每个用户，Bitwarden 将使用以下属性：

* 表明用户处于 `active` 状态的指示（**必填**）
* `email`ª 或 `userName`（**必填**）
* `displayName`
* `externalId`

{% hint style="info" %}
ª - 由于 SCIM 允许用户将多个电子邮箱地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。
{% endhint %}

#### 群组属性 <a href="#group-attributes" id="group-attributes"></a>

对于每个用户，Bitwarden 将使用以下属性：

* `displayName`（**必填**）
* `members`ª
* `externalId`

{% hint style="info" %}
ª - `members` 是一个对象数组，每个对象代表该群组中的一个用户。**必须使用群组配置才能将已同步用户分配到群组**，但是 SCIM API 不能用于查询群组中的成员。要查询群组成员资格，请使用[公共 API](https://bitwarden.com/help/api/)。
{% endhint %}

## SCIM 事件日志 <a href="#scim-events" id="scim-events"></a>

组织将捕获 SCIM 集成所执行操作的[事件日志](../../oversight-visibility/event-logging/event-logs.md)，包括邀请用户和移除用户，以及创建或删除群组。SCIM 派生的事件将在**成员**列中注册 `SCIM`。

## 现有对象更新 <a href="#updates-to-existing-objects" id="updates-to-existing-objects"></a>

以下章节将说明当 IdP 发生变更时，SCIM 配置会将哪些更改同步到组织的成员和群组：

### 成员状态 <a href="#member-status" id="member-status"></a>

当用户在您的 IdP 中被暂时挂起或停用（而非直接移除）时，其对您组织的访问权限将[自动撤销](../revoke-remove/temporarily-revoke-access.md)。被撤销访问权限的用户将显示在组织**成员**界面的**已撤销**标签页中，并且将：

* 无法访问任何组织密码库项目和集合
* 无法[使用 SSO 登录](../../login-with-sso/)或[组织级 Duo](../../../account/two-step-login/setup-two-step-login/two-step-login-via-duo.md) 双重验证登录
* 不受组织[策略](../../oversight-visibility/enterprise-policies.md)的约束
* 不占用许可证席位

{% hint style="danger" %}
对于那些使用[受信任设备 SSO](../../login-with-sso/trusted-devices/) 而没有主密码的成员账户：

* [从您的组织中移除它们](../revoke-remove/permanently-remove-access.md)将切断它们对 Bitwarden 账户的所有访问权限，除非该账户此前通过[账户恢复](../account-recovery/about-account-recovery.md)功能设置过主密码，且在移除前至少使用该主密码登录过一次。

除非在用户被从组织中移除**之前**采取了上述步骤，否则用户将无法重新加入您的组织。如果没有采取上述步骤，每个被移除的用户都必须[删除自己的账户](../../../plans-and-pricing/delete-an-account-or-organization.md#delete-your-personal-account)，然后重新获得邀请才能创建账户和加入组织。

* [撤销对组织的访问权限](../revoke-remove/temporarily-revoke-access.md)，但不会从组织中移除他们，他们仍然可以登录 Bitwarden 并**仅可以**访问他们的个人密码库。
{% endhint %}

### 成员电子邮箱地址 <a href="#member-email-address" id="member-email-address"></a>

SCIM 配置的用户可以在 Bitwarden 及其组织的相关 IdP 中更改电子邮箱地址。要更改 SCIM 组织中的 Bitwarden 电子邮箱地址，请执行以下操作：

1. 通过导航到**设置** → **我的账户**在 Bitwarden 中更改电子邮箱地址（[了解更多](../../../password-manager/more/password-manager-faqs.md#q-how-do-i-change-my-email-address)）。
2. 在 Bitwarden 上更改电子邮箱地址后，更新 IdP 或 AD 客户端上的用户值。这可以是 `externalid` 或相应的值，取决于组织对 IdP 的选择。
3. 重新同步 IdP 或 AD 客户端，以实现更改。

{% hint style="info" %}
如果在更新 Bitwarden 电子邮箱之前，用户电子邮箱地址已在 IdP 或 AD 上更新并同步过，则更新后的电子邮箱将被视为新的用户。
{% endhint %}

### 成员显示名称 <a href="#member-display-name" id="member-display-name"></a>

### 成员外部 ID <a href="#member-external-id" id="member-external-id"></a>

## SCIM 实施前的对象更新 <a href="#updates-to-pre-scim-objects" id="updates-to-pre-scim-objects"></a>

### SCIM 实施前加入的成员 <a href="#members-added-prior-to-scim" id="members-added-prior-to-scim"></a>

### SCIM 实施前创建的群组 <a href="#groups-created-prior-to-scim" id="groups-created-prior-to-scim"></a>


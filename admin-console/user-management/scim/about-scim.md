# 关于 SCIM

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/about-scim/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置成员和群组。

Bitwarden 服务器提供了一个 SCIM 端点，该端点具有有效的 [SCIM API 密钥](about-scim.md#setting-up-scim)，将接受来自您的身份提供程序 (IdP) 的用户和群组的配置和取消配置请求。

{% hint style="info" %}
SCIM 集成适用于**企业组织**。团队组织或未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用[目录连接器](../directory-connector/directory-connector-cli.md)作为替代的预配方式。
{% endhint %}

Bitwarden 支持使用标准属性映射的 SCIM v2，并提供以下官方 SCIM 集成：

* [Azure 活动目录](azure-ad-scim-integration.md)
* [Okta](okta-scim-integration.md)
* [OneLogin](onelogin-scim-integration.md)
* [JumpCloud](jumpcloud-scim-integration.md)

{% hint style="success" %}
除了上面列出的提供程序之外，Bitwarden 还提供与 Google Workspace 的测试版集成。[联系我们以了解更多信息](https://bitwarden.com/contact/)。
{% endhint %}

## 设置 SCIM <a href="#setting-up-scim" id="setting-up-scim"></a>

要设置 SCIM，您的 IdP 需要一个 SCIM URL 和 API 密钥来向 Bitwarden 服务器发出授权请求。这些值可从您组织的**管理** → **SCIM 配置**页面获取：

{% embed url="https://bitwarden.com/_gatsby/image/c70bf678c406888fdf350cedde0490ed/684599a3378fc51acd1d29f150dcb312/scim1.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6sw1kuK7GuZ3dfQkkbs6rV%2F11680a14a2c77af699e8c5a9d86394c6%2Fscim1.png&a=w%3D850%26h%3D473%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A07%3A34.818Z" %}
SCIM 预配
{% endembed %}

{% hint style="success" %}
我们建议使用我们的专用指南之一来设置 Bitwarden 与 [Azure AD](azure-ad-scim-integration.md)、[Okta](okta-scim-integration.md)、[OneLogin](onelogin-scim-integration.md) 或 [JumpCloud](jumpcloud-scim-integration.md) 的 SCIM 集成。
{% endhint %}

### 属性要求 <a href="#required-attributes" id="required-attributes"></a>

Bitwarden 使用此处列出的标准 SCIM v2 属性名称，但每个 IdP 也可以使用在配置期间映射到 Bitwarden 的备用名称。

#### 用户属性 <a href="#user-attributes" id="user-attributes"></a>

对于每个用户，Bitwarden 将使用以下属性：

* 表明用户处于 `active` 状态的指示（**必填**）
* `email`ª 或 `userName`（**必填**）
* `externalId`

ª -由于 SCIM 允许用户将多个电子邮件地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

#### 群组属性 <a href="#group-attributes" id="group-attributes"></a>

对于每个用户，Bitwarden 将使用以下属性：

* `displayName`（**必填**）
* `members`ª
* `externalId`

ª -`members` 是一个对象数组，每个对象代表该群组中的一个用户。

## 撤销和恢复访问权限 <a href="#revoking-and-restoring-access" id="revoking-and-restoring-access"></a>

使用 SCIM 在 Bitwarden 中配置用户后，您可以暂时撤销他们对您的组织及其密码库项目的访问权限。当用户在您的 IdP 中被暂停/停用时，他们对您组织的访问权限将被自动撤销。

{% hint style="success" %}
只有**所有者**可以撤销和恢复其他所有者的访问权限。
{% endhint %}

已撤销访问权限的用户列在**管理** → **人员**界面的**已撤销**选项卡中，并将：

* 无权访问任何组织密码库项目、集合等。
* 无法使用 [SSO 登录](../../../my-account/log-in-and-unlock/using-login-with-sso.md)，或使用 [Organizational Duo](../../../my-account/two-step-login/setup-guides/two-step-login-via-duo.md) 进行两步登录。
* 不受您的组织[策略](../../organization-basics/enterprise-policies.md)的约束。
* 不占用许可席位。

了解有关[撤销](../user-management.md#revoke-access)和[恢复](../user-management.md#restore-access)访问权限的更多信息。

## SCIM 事件日志 <a href="#scim-events" id="scim-events"></a>

组织将捕获 SCIM 集成所采取操作的[事件日志](../../organization-basics/event-logs.md)，包括邀请用户和移除用户，以及创建或删除群组。SCIM 派生的事件将从 `Unknown` 注册：

{% embed url="https://bitwarden.com/_gatsby/image/1512d8c4b2ab04b9daa67ceaa1f9398e/01d16ab8f9d51e1d20cf8ba0379e35df/Screen%20Shot%202022-07-25%20at%2010.41.51%20AM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F5y4TtUhrANOCKo5dHWgZ7z%2F55b95f8df86ef257620412a14e4a2012%2FScreen_Shot_2022-07-25_at_10.41.51_AM.png&a=w%3D626%26h%3D192%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A07%3A41.268Z" %}
SCIM 事件日志
{% endembed %}

## 迁移到 SCIM <a href="#migrating-to-scim" id="migrating-to-scim"></a>

在手动或使用目录连接器激活 SCIM 之前，具有用户和群组的组织应注意以下事项：

|       | .**..已存在于 IdP 中的**                                                             | **...不存在于 IdP 中的**                    |
| ----- | ------------------------------------------------------------------------------ | ------------------------------------- |
| 已有的用户 | <p>•不会重复</p><p>•不会被迫重新加入组织</p><p>•将根据 IdP 添加到相关群组</p><p>•不会从他们已经是其成员的组织中移除</p> | <p>•不会从组织中移除</p><p>•不会添加或移除群组成员身份</p> |
| 已有的群组 | <p>•不会重复</p><p>•将根据 IdP 添加成员</p><p>•不会移除现有成员</p>                               | <p>•不会从组织中移除</p><p>•不会添加或移除成员</p>     |

{% hint style="info" %}
如果您使用的是目录连接器，请确保在激活 SCIM 之前关闭同步。
{% endhint %}

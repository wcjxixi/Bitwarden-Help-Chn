# Microsoft Entra ID SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/microsoft-entra-id-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**团队版组织和企业版组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

本文将帮助您配置与 Azure 的 SCIM 集成。配置过程需要同时使用 Bitwarden 网页密码库和 Azure 门户。在进行操作时，我们建议您同时准备好这两者，并按照文档中的顺序步骤完成操作。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../../../self-hosting/deploy-and-configure/optional-features/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开 Admin Console，然后导航至**设置** → **SCIM 配置**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6sw1kuK7GuZ3dfQkkbs6rV/a4f4e18e561733297338e4ed44c6ed8c/2024-12-03_15-25-46.png?w=1197&#x26;fm=avif" alt=""><figcaption><p>SCIM 配置</p></figcaption></figure></div>

选中**启用 SCIM** 复选框，并记录下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中，您将需要使用这两个值。

## 创建企业应用程序 <a href="#create-an-enterprise-application" id="create-an-enterprise-application"></a>

{% hint style="success" %}
如果您已将此 IdP 用于 SSO 登录，请打开现有的企业应用程序并[跳至此步骤](microsoft-entra-id-scim-integration.md#enable-provisioning)。否则，继续本部分以创建一个新的应用程序。
{% endhint %}

在 Azure 门户中，导航到 **Microsoft Entra ID**，然后从导航菜单中选择 **Enterprise applications**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/69h0vJlyvkF5J6tsKfQ7jd/4994ed3200bdce4b5faea87e1ac2de83/Enterprise_application.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>企业应用程序</p></figcaption></figure></div>

选择 **➕New application** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7f6vbFmJRpfwDXbjHNKp1i/c314ef0bcbb68306858fa0f76da1e369/new_application.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>创建新的应用程序</p></figcaption></figure></div>

在浏览 **Microsoft Entra ID** 图库界面，选择 **➕Create your own application** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6oF8nrPsl7riqg3jWFDk7N/5cf08062f5656e0aee44ea627a2071c5/Create_your_own_application.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>创建您自己的应用程序</p></figcaption></figure></div>

在 Create your own application 界面，为应用程序指定一个专用于 Bitwarden 的名称，然后选择 **Create** 按钮。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2fCSl3wr0PPuTYBk9zisXd/0e8754a3163b6560d832306b4b88bb1b/create_entra_app.png?w=1134&#x26;fm=avif" alt=""><figcaption><p>创建 Entra ID 应用程序</p></figcaption></figure></div>

### 启用配置 <a href="#enable-provisioning" id="enable-provisioning"></a>

从导航中选择 **Provisioning**，然后完成以下步骤：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3FNghuESyQaW6EB4WfANSy/f0a1ef6cae75ccc9412e5f0e1396b5f1/Select_Provisioning.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>选择 Provisioning</p></figcaption></figure></div>

1. 选择 **➕New configuration** 按钮。
2. 在 **Select authentication method** 下拉菜单中，选择 **Bearer authentication**。
3. 在 **Tenant URL** 字段中输入您的 SCIM URL（[了解更多](microsoft-entra-id-scim-integration.md#enable-scim)）。
4. 在 **Secret Token** 字段中输入您的 SCIM API 密钥（[了解更多](microsoft-entra-id-scim-integration.md#enable-scim)）。
5. 选择 **Test Connection** 按钮。
6. 如果您的连接测试成功，请选择 **Save** 按钮。

### 映射 <a href="#mappings" id="mappings"></a>

此界面在为企业应用程序进行初始设置时，或通过导航到企业应用程序时可用。在左侧菜单的 **Manage** 部分下选择 **Provisioning**，然后在顶部选择 **Edit Provisioning**。

Bitwarden 使用标准的 SCIM v2 属性名称，尽管这些名称可能与 Microsoft Entra ID 属性名称不一致。默认映射将正常工作，但您可以根据需要使用此部分进行更改。

#### 用户映射 <a href="#user-mapping" id="user-mapping"></a>

如果您希望目录中的用户对象与 Bitwarden 同步，您可以启用或禁用 **Provision Microsoft Entra ID Users**。默认情况下启用此功能。如果您希望根据下表进行更改，请选择 **Provision Microsoft Entra ID Users** 链接以自定义用户对象发送给 Bitwarden 的属性：

| Bitwarden 属性                                               | 默认 AAD 属性                                                     |
| ---------------------------------------------------------- | ------------------------------------------------------------- |
| `active`                                                   | `Switch([IsSoftDeleted], , "False", "True", "True", "False")` |
| `emails`<mark style="color:red;">**ª**</mark> 或 `userName` | `mail` 或 `userPrincipalName`                                  |
| `displayName`                                              | `displayName`                                                 |
| `externalId`                                               | `mailNickname`                                                |

<mark style="color:red;">**ª**</mark> - 由于 SCIM 允许用户拥有多个电子邮箱地址（以对象数组形式表示），Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

#### 使用对象标识符的用户映射 <a href="#user-mapping-with-object-identifiers" id="user-mapping-with-object-identifiers"></a>

如果用户映射优先考虑使用 Entra `objectId` 而非其他属性进行映射，可能会获得更好的性能。以这种方式映射可以保持与 Bitwarden 账户的连接，即使对应的 Entra ID 账户的电子邮箱地址发生变化，例如在姓名变更的情况下。要实现这一点，请对您的用户映射方案进行以下更改：

* 将 `externalId` 映射到 `objectId` 而不是 `mailNickname` 。
* 对于 `externalId` 到 `objectId` 的映射，将 **Match objects using this attribute** 设置为 Yes。
* 对于 `externalId` 到 `objectId` 的映射，将 **Matching precedence** 设置为 1。
* 对于 `userName`（**customerappsso 属性**）到 `userPrincipalName` 或 `mail`（**Microsoft Entra ID 属性**）的映射，将 **Matching precedence** 设置为 2。

{% hint style="danger" %}
如果在用户已通过 SCIM 同步到 Bitwarden 后实施此映射策略，请注意，这些已同步的用户将不会拥有由 Entra ID 对象 ID 设置的外部 ID。对于这些用户，请使用[公共 API](../../bitwarden-public-api.md) 的 `/public/members/{id}` 端点来设置其外部 ID。
{% endhint %}

#### 群组映射 <a href="#group-mapping" id="group-mapping"></a>

如果您希望目录中的群组对象与 Bitwarden 同步，则可以启用或禁用 **Provision Microsoft Entra ID Groups**。此选项默认处于启用状态。如果您想根据下表进行更改，请选择 **Provision Microsoft Entra ID Groups** 链接，以自定义群组对象发送至 Bitwarden 的属性：

| Bitwarden 属性  | 默认 AAD 属性     |
| ------------- | ------------- |
| `displayName` | `displayName` |
| `members`     | `members`     |
| `externalId`  | `objectId`    |

### 设置 <a href="#settings" id="settings"></a>

在 **Settings** 下拉菜单下，选择：

* 发生故障时是否发送电子邮件通知，如果是，发送到哪个地址（推荐）。
* 是 **sync only assigned users and groups** 还是 **sync all users and groups**。此设置根据您的映射配置进行修改。例如，如果禁用群组映射，添加到企业应用程序的群组将仅同步属于该群组成员的用户对象，而不是在 Bitwarden 本身中创建群组。如果您选择 sync all users and groups，请跳过下一步，因为根据您的映射设置，您的整个目录将被同步。

## 分配用户和群组 <a href="#assign-users-and-groups" id="assign-users-and-groups"></a>

如果您已从 Provisioning Settings 中选择了 **sync only assigned users and groups** ，请完成此步骤。从导航中选择 **Users and Groups**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5xXgCDxrB4wVlZmfsKmi2L/cad020d84786fa009a6636b01ce5d918/remove-name-2.png?w=1338&#x26;fm=avif" alt=""><figcaption><p>企业应用程序中的用户和群组</p></figcaption></figure></div>

选择 **➕Add user/group** 以在用户或群组级别分配对 SCIM 应用程序的访问权限。以下部分说明在 Azure 中修改用户和群组将如何影响其在 Bitwarden 中的对应项：

### 用户 <a href="#users" id="users"></a>

如果在您的映射中已启用 **Provision Microsoft Entra ID Users**，则会执行以下操作：

* 当在 Azure 中分配新用户后，该用户将被邀请加入您的 Bitwarden 组织。
* 当在 Azure 中分配已经是组织成员的用户时，Bitwarden 用户将通过其 `UserName` 值链接到 Azure 用户。
  * 以这种方式链接的用户仍然受此列表中的其他工作流程的约束，但是 Bitwarden 在 `DisplayName` 和 `externalId/mailnickname` 之类的值不会自动更改。
* 当通过 Azure 中的 `accountEnabled` 属性禁用分配的用户时，该用户对组织的访问权限将被撤销。
* 当分配的用户在 Azure 中被「软」删除时，该用户对组织的访问权限将被撤销。
  * 当用户在 Azure 中被永久删除时，该用户将从组织中被移除。
* 从 Azure 中的企业应用程序中移除已分配的用户后，该用户对组织的访问权限将被撤销。
* 当分配的用户从 Azure 中的群组中被移除时，该用户也会从 Bitwarden 中的该群组中被移除，但仍是组织的成员。

### 群组 <a href="#groups" id="groups"></a>

如果在您的映射中已启用 **Provision Microsoft Entra ID Groups**，则会执行以下操作：

* 当在 Azure 中分配新的群组时，该组将在 Bitwarden 中被创建。
  * 已经是 Bitwarden 组织成员的群组成员将被添加到该群组中。
  * 尚未成为 Bitwarden 组织成员的群组成员会被邀请加入。
* 当在 Azure 中分配已经存在于 Bitwarden 组织中的群组时，Bitwarden 群组将通过 `DisplayName` 和 `externalID/ObjectID` 值链接到 Azure。
  * 以这种方式链接的群组将使他们的成员从 Azure 同步。
* 当群组在 Azure 中重命名时，只要建立初始同步，它就会在 Bitwarden 进行更新。
  * 当群组在 Bitwarden 中重命名时，它将更改回其在 Azure 中的名称。请始终在 Azure 端更改群组名称。

## 开始配置 <a href="#start-provisioning" id="start-provisioning"></a>

应用程序完全配置好后，通过选择企业应用程序 **Provisioning** 页面上的 **Start provisioning** 按钮以开始配置：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1oJcKq2shIBPxySuKjaZLV/61bbe111c6e1a140698103ae00874d14/Start_provisioning_.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>开始配置</p></figcaption></figure></div>

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

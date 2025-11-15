# Microsoft Entra ID SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/microsoft-entra-id-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**团队组织和企业组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

本文将帮助您配置与 Azure 的 SCIM 集成。配置涉及同时使用 Bitwarden 网页密码库和 Azure 门户。在进行配置时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../../../self-hosting/deploy-and-configure/optional-features/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开管理控制台并导航至**设置** → **SCIM 配置**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sw1kuK7GuZ3dfQkkbs6rV/a4f4e18e561733297338e4ed44c6ed8c/2024-12-03_15-25-46.png?_a=DAJAUVWIZAAB" %}
SCIM 配置
{% endembed %}

选中**启用 SCIM** 复选框并记下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中您将需要使用这两个值。

## 创建企业应用程序 <a href="#create-an-enterprise-application" id="create-an-enterprise-application"></a>

{% hint style="success" %}
如果您的 SSO 登录已在使用此 IdP，请打开现有的企业应用程序并[跳至此步骤](microsoft-entra-id-scim-integration.md#enable-provisioning)。否则，继续本部分以创建一个新的应用程序。
{% endhint %}

在 Azure 门户中，导航到 **Microsoft Entra ID** 并从导航菜单中选择 **Enterprise applications**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/69h0vJlyvkF5J6tsKfQ7jd/4994ed3200bdce4b5faea87e1ac2de83/Enterprise_application.png?_a=DAJAUVWIZAAB" %}
企业应用程序
{% endembed %}

选择 **🞤 New application** 按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7f6vbFmJRpfwDXbjHNKp1i/c314ef0bcbb68306858fa0f76da1e369/new_application.png?_a=DAJAUVWIZAAB" %}
创建新的应用程序
{% endembed %}

在浏览 **Microsoft Entra ID** 图库界面，选择 **🞤Create your own application** 按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6oF8nrPsl7riqg3jWFDk7N/5cf08062f5656e0aee44ea627a2071c5/Create_your_own_application.png?_a=DAJAUVWIZAAB" %}
创建您自己的应用程序
{% endembed %}

在 Create your own application 界面，为应用程序指定一个专用于 Bitwarden 的特定名称，然后选择 **Create** 按钮。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2fCSl3wr0PPuTYBk9zisXd/0e8754a3163b6560d832306b4b88bb1b/create_entra_app.png?_a=DAJAUVWIZAAB" %}
创建 Entra ID 应用程序
{% endembed %}

### 启用配置 <a href="#enable-provisioning" id="enable-provisioning"></a>

从导航中选择 **Provisioning** 并完成以下步骤：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3FNghuESyQaW6EB4WfANSy/f0a1ef6cae75ccc9412e5f0e1396b5f1/Select_Provisioning.png?_a=DAJAUVWIZAAB" %}
选择 Provisioning
{% endembed %}

1. 选择 **Get started** 按钮。
2. 从 **Provisioning Mode** 下拉菜单中选择 **Automatic**。
3. 在 **Tenant URL** 字段中输入您的 SCIM URL（[了解更多](microsoft-entra-id-scim-integration.md#enable-scim)）。
4. 在 **Secret Token** 字段中输入您的 SCIM API 密钥（[了解更多](microsoft-entra-id-scim-integration.md#enable-scim)）。
5. 选择 **Test Connection** 按钮。
6. 如果您的连接测试成功，请选择 **Save** 按钮。

### 映射 <a href="#mappings" id="mappings"></a>

此界面在为企业应用程序进行初始设置时，或通过导航到企业应用程序时可用，然后在左侧菜单的 **Manage** 部分下选择 **Provisioning**，然后在顶部选择 **Edit Provisioning**。

Bitwarden 使用标准的 SCIM v2 属性名称，尽管这些名称可能与 Microsoft Entra ID 属性名称不一致。默认映射将正常工作，但您可以根据需要使用此部分进行更改。

#### 用户映射 <a href="#user-mapping" id="user-mapping"></a>

如果您希望目录中的用户对象与 Bitwarden 同步，您可以启用或禁用 **Provision Microsoft Entra ID Users**。默认情况下启用此功能。如果您希望根据下表进行更改，请选择 **Provision Microsoft Entra ID Users** 链接以自定义用户对象发送给 Bitwarden 的属性：

| Bitwarden 属性           | 默认 AAD 属性                                                     |
| ---------------------- | ------------------------------------------------------------- |
| `active`               | `Switch([IsSoftDeleted], , "False", "True", "True", "False")` |
| `emails`ª 或 `userName` | `mail` 或 `userPrincipalName`                                  |
| `displayName`          | `displayName`                                                 |
| `externalId`           | `mailNickname`                                                |

ª - 由于 SCIM 允许用户将多个电子邮件地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

#### 群组映射 <a href="#group-mapping" id="group-mapping"></a>

如果您希望目录中的群组对象与 Bitwarden 同步，则可以启用或禁用 **Provision Microsoft Entra ID Groups**。默认情况下启用此选项。如果您想根据下表进行更改，请选择 **Provision Microsoft Entra ID Groups** 链接以自定义群组对象发送给 Bitwarden 的属性：

| Bitwarden 属性  | 默认 AAD 属性     |
| ------------- | ------------- |
| `displayName` | `displayName` |
| `members`     | `members`     |
| `externalId`  | `objectId`    |

### 设置 <a href="#settings" id="settings"></a>

在 **Settings** 下拉菜单下，选择：

* 发生故障时是否发送电子邮件通知，如果是，发送到哪个地址（推荐）。
* 是 **sync only assigned users and groups** 还是 **sync all users and groups**。如果您选择 sync all users and groups。此设置根据您的映射配置进行修改。例如，如果禁用群组映射，添加到企业应用程序的群组将仅同步属于该群组成员的用户对象，而不是在 Bitwarden 本身中创建群组。如果您选择同步所有用户和群组，请跳过下一步，因为您的整个目录将被同步，具体取决于您的映射设置。

## 分配用户和群组 <a href="#assign-users-and-groups" id="assign-users-and-groups"></a>

如果您已从 Provisioning Settings 中选择了 **sync only assigned users and groups** ，请完成此步骤。从导航中选择 **Users and Groups**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5xXgCDxrB4wVlZmfsKmi2L/cad020d84786fa009a6636b01ce5d918/remove-name-2.png?_a=DAJAUVWIZAAB" %}
企业应用程序中的用户和群组
{% endembed %}

选择 **🞤 Add user/group** 以在用户或群组级别分配对 SCIM 应用程序的访问权限。当 SCIM 配置开始时，此处添加的用户和群组将被邀请到 Bitwarden。

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

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1oJcKq2shIBPxySuKjaZLV/61bbe111c6e1a140698103ae00874d14/Start_provisioning_.png?_a=DAJAUVWIZAAB" %}
开始配置
{% endembed %}

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

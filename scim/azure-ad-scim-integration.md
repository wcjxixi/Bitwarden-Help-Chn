# Azure AD SCIM 集成

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/azure-ad-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**企业组织**。团队组织或未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用[目录连接器](../directory-connector/directory-connector-cli.md)作为替代的预配方式。
{% endhint %}

本文将帮助您配置与 Azure 的 SCIM 集成。配置涉及同时使用 Bitwarden 网页密码库和 Azure 门户。在进行配置时，我们建议您准备好这两样东西，并按照文档规定的顺序完成这些步骤。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**如果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开您组织的**管理** → **SCIM 配置**页面：

{% embed url="https://bitwarden.com/_gatsby/image/c70bf678c406888fdf350cedde0490ed/684599a3378fc51acd1d29f150dcb312/scim1.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6sw1kuK7GuZ3dfQkkbs6rV%2F11680a14a2c77af699e8c5a9d86394c6%2Fscim1.png&a=w%3D850%26h%3D473%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A07%3A34.818Z" %}
SCIM 配置
{% endembed %}

选中**启用 SCIM** 复选框并记下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中您将需要使用这两个值。

## 创建一个企业应用程序 <a href="#create-an-enterprise-application" id="create-an-enterprise-application"></a>

{% hint style="success" %}
如果您的 SSO 登录已在使用此 IdP，请打开现有的企业应用程序并[跳至此步骤](azure-ad-scim-integration.md#enable-provisioning)。否则，继续本部分以创建一个新的应用程序。
{% endhint %}

在 Azure 门户中，导航到 **Azure Active Directory** 并从导航菜单中选择 **Enterprise applications**：

{% embed url="https://bitwarden.com/_gatsby/image/a3ea338dc5947c2a95f26c305c4b9352/9dfed6e43dcce5bd724dfb6bf4af0789/az-create.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F69h0vJlyvkF5J6tsKfQ7jd%2F1a6cd30a127f597a3f5b53121bc60adc%2Faz-create.png&a=w%3D850%26h%3D505%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A15%3A40.338Z" %}
企业应用程序
{% endembed %}

选择 **🞤 New application** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/a2a30911de21c7466f362b044a158253/b8257e323ee5953820291453e1197a99/az-newapp.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F7f6vbFmJRpfwDXbjHNKp1i%2F1245c6faab19cd3ea78bc547a98e9fcf%2Faz-newapp.png&a=w%3D850%26h%3D325%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A15%3A41.345Z" %}
创建新的应用程序
{% endembed %}

在 Browse Azure AD Gallery 界面，选择 **🞤 Create your own application** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/47c6b9623fdc9b02f0c2ae24d4ac6260/8edca8a5097cc14b22b9d9515be0f778/az-newapp2.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6oF8nrPsl7riqg3jWFDk7N%2F37af1c6f11f95c4822058b6a7da5e067%2Faz-newapp2.png&a=w%3D850%26h%3D261%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A15%3A40.323Z" %}
创建您自己的应用程序
{% endembed %}

在 Create your own application 界面，为应用程序指定一个专用于 Bitwarden 的特定名称，然后选择 **Create** 按钮。

### 启用配置 <a href="#enable-provisioning" id="enable-provisioning"></a>

从导航中选择 **Provisioning** 并完成以下步骤：

{% embed url="https://bitwarden.com/_gatsby/image/45de67039b59e16664f65193db4c4566/8d943395ffe484f455bc1202070f88cc/remove-name-1.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F3FNghuESyQaW6EB4WfANSy%2Fc1ccebd8e1516745ab23d5fe06f24848%2Fremove-name-1.png&a=w%3D850%26h%3D353%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A04%3A00.526Z" %}
选择 Provisioning
{% endembed %}

1. 选择 **Get started** 按钮。
2. 从 **Provisioning Mode** 下拉菜单中选择 **Automatic**。
3. 在 **Tenant URL** 字段中输入您的 SCIM URL（[了解更多](azure-ad-scim-integration.md#enable-scim)）。
4. 在 **Secret Token** 字段中输入您的 SCIM API 密钥（[了解更多](azure-ad-scim-integration.md#enable-scim)）。
5. 选择 **Test Connection** 按钮。
6. 如果您的连接测试成功，请选择 **Save** 按钮。

### 映射 <a href="#mappings" id="mappings"></a>

Bitwarden 使用标准的 SCIM v2 属性名称，尽管这些名称可能与 Azure AD 属性名称不一致。默认映射将起作用，但您可以根据需要使用此部分进行更改。Bitwarden 将为用户和群组使用以下属性：

#### 用户映射 <a href="#user-mapping" id="user-mapping"></a>

| **Bitwarden 属性**       | **默认的 Azure AD 属性**                                           |
| ---------------------- | ------------------------------------------------------------- |
| `active`               | `Switch([IsSoftDeleted], , "False", "True", "True", "False")` |
| `emails`ª 或 `userName` | `mail` 或 `userPrincipalName`                                  |
| `displayName`          | `displayName`                                                 |
| `externalId`           | `mailNickname`                                                |

ª -由于 SCIM 允许用户将多个电子邮件地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

#### 群组映射 <a href="#group-mapping" id="group-mapping"></a>

| **Bitwarden 属性** | **默认的 Azure AD 属性** |
| ---------------- | ------------------- |
| `displayName`    | `displayName`       |
| `members`        | `members`           |
| `externalId`     | `objectId`          |

### 设置 <a href="#settings" id="settings"></a>

在 **Settings** 下拉菜单下，选择：

* 发生故障时是否发送电子邮件通知，如果是，发送到哪个地址（_推荐_）。
* 是 **sync only assigned users and groups** 还是 **sync all users and groups**。如果您选择 sync all users and groups，请跳过[下一步](azure-ad-scim-integration.md#assign-users-and-groups)。

## 分配用户和群组 <a href="#assign-users-and-groups" id="assign-users-and-groups"></a>

如果您已从 Provisioning Settings 中选择了 **sync only assigned users and groups** ，请完成此步骤。从导航中选择 **Users and Groups**：

{% embed url="https://bitwarden.com/_gatsby/image/3e5f95eafc8fec1bb757335c60d8eae4/d33acae33b34c8fc08ff98b0ae7cfe76/remove-name-2.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F5xXgCDxrB4wVlZmfsKmi2L%2Fcad020d84786fa009a6636b01ce5d918%2Fremove-name-2.png&a=w%3D850%26h%3D366%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A04%3A00.564Z" %}
企业应用程序中的用户和群组
{% endembed %}

选择 **🞤 Add user/group** 以在用户或群组级别分配对 SCIM 应用程序的访问权限。当 SCIM 配置开始时，此处添加的用户和群组将被邀请到 Bitwarden。

## 开始配置 <a href="#start-provisioning" id="start-provisioning"></a>

应用程序完全配置好后，通过选择企业应用程序 **Provisioning** 页面上的 **Start provisioning** 按钮以开始配置：

{% embed url="https://bitwarden.com/_gatsby/image/3f714e8a4ae9122eda6f3711852ccb99/3e916238451826c0bba161671c3bca44/Screen%20Shot%202022-07-19%20at%209.59.02%20AM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F1oJcKq2shIBPxySuKjaZLV%2F73014a5ae82de2b9780fdde79f770365%2FScreen_Shot_2022-07-19_at_9.59.02_AM.png&a=w%3D850%26h%3D354%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A04%3A00.536Z" %}
开始配置
{% endembed %}

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../organizations/user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../organizations/user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

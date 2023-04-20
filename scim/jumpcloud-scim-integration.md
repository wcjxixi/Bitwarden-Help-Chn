# JumpCloud SCIM 集成

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/jumpcloud-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**企业组织**。团队组织或未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用[目录连接器](../directory-connector/directory-connector-cli.md)作为替代的预配方式。
{% endhint %}

本文将帮助您配置与 JumpCloud 的 SCIM 集成。配置涉及同时使用 Bitwarden 网页密码库和 JumpCloud 门户。在进行配置时，我们建议您准备好这两样东西，并按照文档规定的顺序完成这些步骤。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**如果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../self-hosting/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开您组织的**管理** → **SCIM 配置**页面：

{% embed url="https://bitwarden.com/_gatsby/image/c70bf678c406888fdf350cedde0490ed/684599a3378fc51acd1d29f150dcb312/scim1.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6sw1kuK7GuZ3dfQkkbs6rV%2F11680a14a2c77af699e8c5a9d86394c6%2Fscim1.png&a=w%3D850%26h%3D473%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A07%3A34.818Z" %}
SCIM 配置
{% endembed %}

选中**启用 SCIM** 复选框并记下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中您将需要使用这两个值。

## 创建一个 JumpCloud 应用程序 <a href="#create-a-jumpcloud-app" id="create-a-jumpcloud-app"></a>

{% hint style="success" %}
如果您的 SSO 登录已在使用此 IdP，请打开现有的企业应用程序并[跳至此步骤](jumpcloud-scim-integration.md#enable-provisioning)。否则，继续本部分以创建一个新的应用程序。
{% endhint %}

在 JumpCloud 门户中，从菜单中选择 SSO，然后选择 **🞤Add** 图标：

{% embed url="https://bitwarden.com/_gatsby/image/d41b15622a230aa8d3186ed0546c753b/77be0e56c4162ea7e3505661ca3ca127/jc-addapp.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F4NL4Co6MKF71IDGMBDISyp%2F456a246be2bb037ad0d989d50049646e%2Fjc-addapp.png&a=w%3D850%26h%3D423%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A15%3A37.311Z" %}
添加 JumpCloud 应用程序
{% endembed %}

在搜索框中输入 `Bitwarden` 然后选择 **Configure** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/5daf3d796baeb30fbb21ae5cf0876808/09f6ad118a199851f5e075fe0ad67ee5/jc-bw.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F2pFRcBTjlIjBhMbqlKMhxb%2Fb80b23ecfd660d5c314028297c606879%2Fjc-bw.png&a=w%3D685%26h%3D229%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A15%3A38.342Z" %}
配置 Bitwarden
{% endembed %}

### 常规信息 <a href="#general-info" id="general-info"></a>

在 **General Info** 选项卡中，为应用程序指定一个专用于 Bitwarden 的名称。

### SSO

如果您计划使用 JumpCloud 进行单点登录，请选择 **SSO** 选项卡并按照[这些说明](../login-with-sso/implementation-guides/jumpcloud-saml-implementation.md)设置 SSO。完成后，或者如果您现在要跳过 SSO，请选择 **active** 按钮并完成确认模式。

### 身份管理 <a href="#identity-management" id="identity-management"></a>

重新打开应用程序并导航到 **Identity Management** 选项卡。在此界面上，配置以下信息：

| **字段**          | **描述**                                                              |
| --------------- | ------------------------------------------------------------------- |
| API Type        | 选择 **SCIM API**。                                                    |
| SCIM Version    | 选择 **SCIM 2.0**。                                                    |
| Base URL        | 输入 SCIM URL（[了解更多](jumpcloud-scim-integration.md#enable-scim)）。     |
| Token Key       | 输入 SCIM API Key（[了解更多](jumpcloud-scim-integration.md#enable-scim)）。 |
| Test User Email | 输入一个 JumpCloud 可用于测试集成的电子邮件地址。                                      |

配置完这些字段后，选择 **Test Connection** 按钮。测试成功返回后，选择 **Activate**。

在离开此页面之前，打开 **Enable management of User Groups and Group Membership in this application** 选项并选择 **Save**。

### 用户群组 <a href="#user-groups" id="user-groups"></a>

在 **User Groups** 选项卡中，选择您要在 Bitwarden 中配置的群组。选择 **Save** 按钮后，将立即开始根据此规范进行配置。

{% embed url="https://bitwarden.com/_gatsby/image/1df6e76778b520e9eaad168fb408156d/6f538a9c78d3291a2b016b95a58f5c7f/Screen%20Shot%202022-07-19%20at%2012.01.57%20PM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F55RivcAbqDxw0CZ18jpg4J%2F3f894e05b1448cd0ad5e6383a4ce0422%2FScreen_Shot_2022-07-19_at_12.01.57_PM.png&a=w%3D850%26h%3D391%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A04%3A00.558Z" %}
选择用户群组
{% endembed %}

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../organizations/user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../organizations/user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

## 附录 <a href="#appendix" id="appendix"></a>

### 用户属性映射 <a href="#user-attribute-mapping" id="user-attribute-mapping"></a>

itwarden 使用标准的 SCIM v2 属性名称，但这些名称可能与 JumpCloud 属性名称不同。Bitwarden 将为每个用户使用以下属性：

| **Bitwarden 属性** | **JumpCloud 默认属性**               |
| ---------------- | -------------------------------- |
| `active`         | `!suspended && !passwordExpired` |
| `emails`ª        | `email`                          |
| `displayName`    | `displayName`                    |

ª -由于 SCIM 允许用户将多个电子邮件地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

### 群组属性映射 <a href="#group-attribute-mapping" id="group-attribute-mapping"></a>

Bitwarden 将为每个群组使用以下属性：

| **Bitwarden 属性** | **JumpCloud 默认属性** |
| ---------------- | ------------------ |
| `displayName`    | `displayName`      |
| `members`ª       | `members`          |

ª -成员资格作为对象数组发送到 Bitwarden，每个对象代表一个用户，该用户是该群组的成员。

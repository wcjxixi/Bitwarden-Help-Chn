# Okta SCIM 集成

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/okta-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**企业组织**。团队组织或未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用[目录连接器](../directory-connector/directory-connector-cli.md)作为替代的预配方式。
{% endhint %}

本文将帮助您配置与 Okta 的 SCIM 集成。配置涉及同时使用 Bitwarden 网页密码库和 Okta 管理员门户。在进行配置时，我们建议您准备好这两样东西，并按照文档规定的顺序完成这些步骤。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**如果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开您组织的**管理** → **SCIM 配置**页面：

{% embed url="https://bitwarden.com/_gatsby/image/c70bf678c406888fdf350cedde0490ed/684599a3378fc51acd1d29f150dcb312/scim1.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6sw1kuK7GuZ3dfQkkbs6rV%2F11680a14a2c77af699e8c5a9d86394c6%2Fscim1.png&a=w%3D850%26h%3D473%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A07%3A34.818Z" %}
SCIM 配置
{% endembed %}

选中**启用 SCIM** 复选框并记下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中您将需要使用这两个值。

## 创建一个应用程序集成 <a href="#create-an-app-integration" id="create-an-app-integration"></a>

{% hint style="success" %}
如果您的 SSO 登录已在使用此 IdP，请打开现有的企业应用程序并[跳至此步骤](okta-scim-integration.md#enable-provisioning)。否则，继续本部分以创建一个新的应用程序。
{% endhint %}

在 Okta 管理员门户中，从导航中选择 **Applications** → **Applications**。在 Application 界面，选择 **Create App Integration** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/0b7e51992e0f6d7fefd273f76ef32bdf/520f908a5350182f3069b47fbf6ad3a6/Screen%20Shot%202022-07-18%20at%2010.32.31%20AM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2FnBs4O5osFzxI0QCfQLpxx%2F18aaaf550c8bb2b5a01bc70ddee3ebdb%2FScreen_Shot_2022-07-18_at_10.32.31_AM.png&a=w%3D850%26h%3D390%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A08%3A30.503Z" %}
创建应用程序集成
{% endembed %}

在 Create a new app integration 对话框中，选择 **SAML 2.0** 选项然后选择 **Next**：

{% embed url="https://bitwarden.com/_gatsby/image/24f248dceb8356538ff2e69689c9c7f2/e03d1bca1829049d73c51c6f66c17858/Screen%20Shot%202022-07-19%20at%201.13.29%20PM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F4I8U9GJFm2w25scodW6aHu%2Ffba55a2b20e931dcc9df4be6e689279f%2FScreen_Shot_2022-07-19_at_1.13.29_PM.png&a=w%3D850%26h%3D503%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A08%3A35.641Z" %}
应用程序类型设置
{% endembed %}

### 通用设置 <a href="#general-settings" id="general-settings"></a>

在 **General Settings** 选项卡上，为应用程序指定一个专用于 Bitwarden 的特定名称，然后选择 **Next**。

### 配置 SAML <a href="#configure-saml" id="configure-saml"></a>

按照[这些说明](../../login-with-sso/implementation-guides/okta-saml-implementation.md#configure-saml)完成 **Configure SAML** 选项卡的配置。如果您不使用 SSO，尽管需要完成集成，但不会使用这些字段。

配置完成后，选择 **Next** 按钮进入 **Feedback** 界面然后选择 **Finish**。

## 设置配置 <a href="#setup-provisioning" id="setup-provisioning"></a>

在您的应用集成的 **General** 选项卡上，选择 **App Settings** 旁边的 **Edit** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/1562169ef0c364edd00a4b69c74a0ded/e3c97f431c846f897b92cb064dca9c1e/Screen%20Shot%202022-07-19%20at%2012.27.01%20PM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F2ZcE0BQq8HbQg47MyvXQpZ%2F49ddef22f27980be759887c6aa945d75%2FScreen_Shot_2022-07-19_at_12.27.01_PM.png&a=w%3D850%26h%3D446%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A08%3A43.433Z" %}
编辑应用程序设置
{% endembed %}

在 **Provisioning** 部分中，选择 **SCIM** 然后选择t **Save**。

### 配置设置 <a href="#provisioning-settings" id="provisioning-settings"></a>

打开启用后将出现的 **Provisioning** 选项卡，然后选择 **SCIM Connection** 旁边的 **Edit** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/473dc5232e2aa73de20340b2eea94015/bfaf2ee43fc6e23b7ee18143d9808acf/Screen%20Shot%202022-07-19%20at%2012.29.45%20PM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F1vyUChnKJS2WM2V6u0gMGS%2Fba743e0965341678978c3a56464d0a90%2FScreen_Shot_2022-07-19_at_12.29.45_PM.png&a=w%3D850%26h%3D507%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A08%3A49.184Z" %}
编辑 SCIM 连接
{% endembed %}

在此页面上，配置以下内容：

| **字段**                            | **描述**                                                          |
| --------------------------------- | --------------------------------------------------------------- |
| SCIM connector base URL           | 输入您的 SCIM URL（[了解更多](okta-scim-integration.md#enable-scim)）。    |
| Unique identifier field for users | 输入 `email`。                                                     |
| Supported provisioning actions    | 至少启用 **Push New Users** 和 **Push Groups**.                      |
| Authentication Mode               | 选择 **HTTP Header**.                                             |
| Authorization                     | 输入您的 SCIM API 密钥（[了解更多](okta-scim-integration.md#enable-scim)）。 |

完成这些字段的配置后，选择 **Save**。

### 设置配置动作 <a href="#set-provisioning-actions" id="set-provisioning-actions"></a>

在 **Provisioning** → **To App** 界面上，选择 **Edit** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/8a6c50e4d8b547e95b8d0c872fc084df/2dc4dbb17173b0a1b7e9ebd5824ff2c9/Screen%20Shot%202022-07-20%20at%204.10.05%20PM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F7HbSzaHxTZ8iddtJ3p0ATj%2F896fae907584a2dc95ddfb8db0bfe228%2FScreen_Shot_2022-07-20_at_4.10.05_PM.png&a=w%3D850%26h%3D682%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A04%3A00.552Z" %}
配置到应用程序
{% endembed %}

至少启用 **Create Users** 和 **Deactivate Users**。完成后选择 **Save**。

## 指派 <a href="#assignments" id="assignments"></a>

打开 **Assignments** 选项卡然后使用指派下拉菜单将人员或群组指派给应用程序。已指派的用户和群组将自动发出邀请。根据您的工作流程，您可能需要使用 **Push Groups** 选项卡以在群组被指派后后触发群组配置。

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

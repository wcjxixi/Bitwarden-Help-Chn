# JumpCloud SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/jumpcloud-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**团队版组织和企业版组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

本文将帮助您配置与 JumpCloud 的 SCIM 集成。配置过程需要同时使用 Bitwarden 网页密码库和 JumpCloud 门户。在进行操作时，我们建议您同时准备好这两者，并按照文档中的顺序步骤完成操作。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../../../self-hosting/deploy-and-configure/optional-features/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开 Admin Console，然后导航至**设置** → **SCIM 配置**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6sw1kuK7GuZ3dfQkkbs6rV/e665df6992fb880114fcef82e4e4c07c/SCIM_provisioning_URL_and_API_key.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>SCIM 配置</p></figcaption></figure></div>

选中**启用 SCIM** 复选框，并记录下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中，您将需要使用这两个值。

## 创建 JumpCloud App <a href="#create-a-jumpcloud-app" id="create-a-jumpcloud-app"></a>

{% hint style="success" %}
如果您已将此 IdP 用于 SSO 登录，请打开现有的应用程序并[跳至此步骤](jumpcloud-scim-integration.md#enable-provisioning)。否则，继续本部分以创建一个新的应用程序。
{% endhint %}

在 JumpCloud 门户中，从菜单中选择 **Applications**，然后选择 **Get Started** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/63S5F953fjQN6V4xYKZR3h/d2f5eff68f3c5f4fb7f7b25c71c6dc7d/Create-Bitwarden-App.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>创建 JumpCloud Bitwarden App</p></figcaption></figure></div>

在搜索框中输入 `Bitwarden`，然后选择 **Configure** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2pFRcBTjlIjBhMbqlKMhxb/fc85babc5dfa8b90b6edf028bb347a52/Configure_Bitwarden.png?w=1146&#x26;fm=avif" alt=""><figcaption><p>配置 JumpCloud Bitwarden</p></figcaption></figure></div>

### 常规信息 <a href="#general-info" id="general-info"></a>

在 **General Info** 选项卡中，为应用程序指定一个专用于 Bitwarden 的名称。

### SSO

如果您计划使用 JumpCloud 进行单点登录，请选择 **SSO** 选项卡然后按照[这些说明](../../login-with-sso/sso-guides/jumpcloud-saml-implementation.md)设置 SSO。完成后，或者如果您现在要跳过 SSO，请选择 **active** 按钮并完成确认模式。

### 身份管理 <a href="#identity-management" id="identity-management"></a>

重新打开应用程序并导航到 **Identity Management** 选项卡。展开 **Configuration Settings** 框并输入以下信息：

| 字段        | 描述                                                                  |
| --------- | ------------------------------------------------------------------- |
| Base URL  | 输入 SCIM URL（[了解更多](jumpcloud-scim-integration.md#enable-scim)）。     |
| Token Key | 输入 SCIM API Key（[了解更多](jumpcloud-scim-integration.md#enable-scim)）。 |

配置完这些字段后，选择 **Activate** 按钮。测试成功后，选择 **Save**。

### 用户群组 <a href="#user-groups" id="user-groups"></a>

在 **User Groups** 选项卡中，选择您要在 Bitwarden 中配置的群组。选择 **Save** 按钮后，将立即开始根据此规范进行配置。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/55RivcAbqDxw0CZ18jpg4J/3f894e05b1448cd0ad5e6383a4ce0422/Screen_Shot_2022-07-19_at_12.01.57_PM.png?w=1196&#x26;fm=avif" alt=""><figcaption><p>选择用户群组</p></figcaption></figure></div>

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

## 附录 <a href="#appendix" id="appendix"></a>

### 用户属性映射 <a href="#user-attribute-mapping" id="user-attribute-mapping"></a>

Bitwarden 使用标准的 SCIM v2 属性名称，但这些名称可能与 JumpCloud 属性名称不同。Bitwarden 将为每位用户使用以下属性：

| Bitwarden 属性                                  | JumpCloud 默认属性                   |
| --------------------------------------------- | -------------------------------- |
| `active`                                      | `!suspended && !passwordExpired` |
| `emails`<mark style="color:red;">**ª**</mark> | `email`                          |
| `displayName`                                 | `displayName`                    |

<mark style="color:red;">**ª**</mark> - 由于 SCIM 允许用户拥有多个电子邮箱地址（以对象数组形式表示），Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

### 群组属性映射 <a href="#group-attribute-mapping" id="group-attribute-mapping"></a>

Bitwarden 将为每个群组使用以下属性：

| Bitwarden 属性                                   | JumpCloud 默认属性 |
| ---------------------------------------------- | -------------- |
| `displayName`                                  | `displayName`  |
| `members`<mark style="color:red;">**ª**</mark> | `members`      |

<mark style="color:red;">**ª**</mark> - 成员资格作为对象数组发送到 Bitwarden，每个对象代表该群组中的一名成员用户。

# Okta SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/okta-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**团队组织和企业组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

本文将帮助您配置与 Okta 的 SCIM 集成。配置涉及同时使用 Bitwarden 网页密码库和 Okta 管理员门户。在进行配置时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

## 支持的功能 <a href="#supported-features" id="supported-features"></a>

该集成支持以下配置功能：

* **推送用户**：Okta 中分配给 Bitwarden 的用户会被添加为 Bitwarden 中的用户。
* **停用用户**：当用户在 Okta 中停用时，他们也会在 Bitwarden 中停用。
* **推送群组**：可以将 Okta 中的群组及其用户推送到 Bitwarden。

{% hint style="info" %}
请注意，Bitwarden 不支持更改已配置的用户电子邮箱地址。Bitwarden 也不支持更改用户的电子邮箱地址类型，或使用 `primary` 以外的类型。为电子邮箱和用户名输入的值应该相同。[了解更多](about-scim.md#required-attributes)。
{% endhint %}

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../self-hosting/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开管理控制台并导航至**设置** → **SCIM 配置**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sw1kuK7GuZ3dfQkkbs6rV/a4f4e18e561733297338e4ed44c6ed8c/2024-12-03_15-25-46.png?_a=DAJAUVWIZAAB" %}
SCIM 配置
{% endembed %}

选中**启用 SCIM** 复选框并记下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中您将需要使用这两个值。

## 添加 Bitwarden App <a href="#add-the-bitwarden-app" id="add-the-bitwarden-app"></a>

在 Okta 管理门户中，从导航中选择 **Applications** → **Applications**。在 Application 界面，选择 **Browse App Catalog** 按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/nBs4O5osFzxI0QCfQLpxx/c8232cb95494901d8c04e38efc1b3662/Screen_Shot_2022-08-29_at_11.43.30_AM.png?_a=DAJAUVWIZAAB" %}
Browse App Catalog
{% endembed %}

在搜索栏中输入 `Bitwarden` 然后并选择 **Bitwarden**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4I8U9GJFm2w25scodW6aHu/cff940398de8ba4e363b706a2fe98d9f/today1.png?_a=DAJAUVWIZAAB" %}
Bitwarden Okta App
{% endembed %}

选择 **Add Integration** 按钮继续配置。

### 通用设置 <a href="#general-settings" id="general-settings"></a>

在 **General Settings** 选项卡上，为应用程序指定一个专用于 Bitwarden 的特定名称，勾选 **Do not display application icon to users** 和 **Do not display application icon in Okta Mobile App** 选项，然后选择 **Done**。

## 设置配置 <a href="#setup-provisioning" id="setup-provisioning"></a>

### 配置设置 <a href="#provisioning-settings" id="provisioning-settings"></a>

打开 **Provisioning** 选项卡然后选择 **Configure API Integration** 按钮。

选择后，Okta 会列出几个选项供您配置：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1vyUChnKJS2WM2V6u0gMGS/826c7a34f32cc9dc3b864a969d1b00c5/Screen_Shot_2023-02-06_at_1.39.09_PM.png?_a=DAJAUVWIZAAB" %}
配置 API 集成
{% endembed %}

1. 选中 **Enable API Integration** 复选框。
2. 在 **Base URL** 字段中，输入您的 SCIM URL。该 URL 可在 SCIM Provisioning 界面找到（[了解更多](okta-scim-integration.md#enable-scim)）。
3. 在 **API Token** 字段中，输入你的 SCIM API 密钥（[了解更多](okta-scim-integration.md#enable-scim)）。

完成后，使用 **Test API Credentials** 按钮测试配置。如果测试通过，请选择 **Save** 按钮。

### 设置配置动作 <a href="#set-provisioning-actions" id="set-provisioning-actions"></a>

在 **Provisioning** → **To App** 界面上，选择 **Edit** 按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7HbSzaHxTZ8iddtJ3p0ATj/b24242f237309de4d51e1f7c943d7903/today3.png?_a=DAJAUVWIZAAB" %}
配置到应用程序
{% endembed %}

至少启用 **Create Users** 和 **Deactivate Users**。完成后选择 **Save**。

## 指派 <a href="#assignments" id="assignments"></a>

打开 **Assignments** 选项卡然后使用指派下拉菜单将人员或群组指派给应用程序。已指派的用户和群组将自动发出邀请。根据您的工作流程，您可能需要使用 **Push Groups** 选项卡以在群组被指派后后触发群组配置。

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../organizations/user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../organizations/user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

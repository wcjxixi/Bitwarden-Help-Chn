# Okta SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/okta-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**团队版组织和企业版组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

本文将帮助您配置与 Okta 的 SCIM 集成。配置过程需要同时使用 Bitwarden 网页密码库和 Okta 管理员门户。在进行操作时，我们建议您同时准备好这两者，并按照文档中的顺序步骤完成操作。

## 支持的功能 <a href="#supported-features" id="supported-features"></a>

该集成支持以下配置功能：

* **推送用户**：Okta 中分配给 Bitwarden 的用户将被添加为 Bitwarden 的用户。
* **停用用户**：处于停用状态的用户将无法再访问其分配的 App。在 Okta 中停用的用户会将其 Bitwarden 状态更改为已撤销。
* **删除用户**：Okta 中删除的用户将在 Bitwarden 组织中移至已撤销状态。

{% hint style="info" %}
在 Okta 中选择暂停用户状态**不会**导致其在 Bitwarden 中变为已撤销状态。
{% endhint %}

* **推送群组**：Okta 中的群组及其用户可推送至 Bitwarden。

{% hint style="info" %}
请注意，Bitwarden 不支持更改已配置的用户电子邮箱地址。Bitwarden 也不支持更改用户的电子邮箱地址类型，或使用 `primary` 以外的类型。为电子邮箱和用户名输入的值应该相同。[了解更多](about-scim.md#required-attributes)。
{% endhint %}

## 在 Bitwarden 中启用 SCIM <a href="#enable-scim-in-bitwarden" id="enable-scim-in-bitwarden"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../../../self-hosting/deploy-and-configure/optional-features/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成：

1、打开 Admin Console，导航至**设置** → **SCIM 配置**。

2、选中**启用 SCIM**。

3、选择**保存**。

4、您的 **SCIM URL** 和 **SCIM API 密钥**将显示出来。在后面的步骤中，您需要输入到 Okta 中。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6sw1kuK7GuZ3dfQkkbs6rV/e665df6992fb880114fcef82e4e4c07c/SCIM_provisioning_URL_and_API_key.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>SCIM 配置</p></figcaption></figure></div>

## 将 Bitwarden App 添加到 Okta <a href="#add-the-bitwarden-app-to-okta" id="add-the-bitwarden-app-to-okta"></a>

要在 Okta 中添加 Bitwarden：

1、在 Okta 管理门户中，导航至 **Applications** → **Applications**。

2、选择 **Browse App Catalog**。

3、在搜索栏中输入 `Bitwarden`，然后选择 **Bitwarden**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7DjlcFofhaHLVKyy2TId7c/86dc82876b88ba717ecfb107b192e7c7/Browse_app_catalog_for_Bitwarden_.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>Browse App Catalog</p></figcaption></figure></div>

4、选择 **Add Integration**，这将打开 Bitwarden 应用程序的常规设置。

5、在 **Application label** 中输入唯一的、Bitwarden 专用的名称。

6、勾选 **Do not display application icon to users**。

7、选择 **Done**。

## 在 Okta 中设置配置 <a href="#set-up-provisioning-in-okta" id="set-up-provisioning-in-okta"></a>

要设置配置，必须按照此处显示的顺序完成以下步骤。

### 连接您的 Bitwarden 组织&#xD; <a href="#connect-your-bitwarden-organization" id="connect-your-bitwarden-organization"></a>

要将 Okta 与 Bitwarden 连接：

1、还是在 Okta 中的 Bitwarden App 配置页面上，选择 **Provisioning**。

2、选择 **Configure API Integration**。

3、勾选 **Enable API Integration**。

4、输入您之前在 Bitwarden Admin Console 的**设置** → **SCIM 配置**中找到的详细信息：

* 在 **Base URL** 字段中，输入来自 Bitwarden 的 **SCIM URL**。
* 在 **API Token** 字段中，输入来自 Bitwarden 的 **SCIM API 密钥**。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5GMQfUOLdpOaKhNxDf88D6/86617a7ee28f2fc5d2e6d646652406a1/Enter_Bitwarden_SCIM_URL_and_API_key.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>输入 Bitwarden SCIM URL 和 API 密钥</p></figcaption></figure></div>

5、选择 **Test API Credentials**。如果您看到类似「Bitwarden was verified successfully!」之类的确认消息，表示您的连接可以正常工作了。

6、选择 **Save**。

### 设置配置动作 <a href="#set-provisioning-actions" id="set-provisioning-actions"></a>

要允许特定的配置动作：

1、还是在  **Provisioning** 选项卡中，选择 **To App**。

2、选择 **Edit**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2xFykuY8l8QtAp8ZfvrwQB/f7e98ede27e13479d54aa04f1a8fec18/Provisioning_to_app.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>配置到 App</p></figcaption></figure></div>

3、勾选 **Create Users** 和 **Deactivate Users**。

4、选择 **Save**。

5、（可选）自定义 **Bitwarden Attribute Mappings**。

## 设置指派 <a href="#set-assignments" id="set-assignments"></a>

打开 **Assignments** 选项卡，然后使用 Assign 下拉菜单将人员或群组指派给应用程序。已指派的用户和群组将自动发出邀请。根据您的工作流程，您可能需要在群组被指派后使用 **Push Groups** 选项卡来触发群组配置。

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

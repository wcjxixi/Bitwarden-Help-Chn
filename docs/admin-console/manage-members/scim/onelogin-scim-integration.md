# OneLogin SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/onelogin-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**团队版组织和企业版组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

本文将帮助您配置与 OneLogin 的 SCIM 集成。配置过程需要同时使用 Bitwarden 网页密码库和 OneLogin 管理员门户。在进行操作时，我们建议您同时准备好这两者，并按照文档中的顺序步骤完成操作。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../../../self-hosting/deploy-and-configure/optional-features/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开 Admin Console，然后导航至**设置** → **SCIM 配置**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6sw1kuK7GuZ3dfQkkbs6rV/e665df6992fb880114fcef82e4e4c07c/SCIM_provisioning_URL_and_API_key.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>SCIM 配置</p></figcaption></figure></div>

选中**启用 SCIM** 复选框，并记录下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中，您将需要使用这两个值。

## 创建 OneLogin App <a href="#create-a-onelogin-app" id="create-a-onelogin-app"></a>

在 OneLogin 门户中，导航到 **Applications** 界面，然后选择 **Add App** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/37OSt7e5j969j9ikvH8buI/3bf9fa6b57a45b357a9d2bc012d8a6af/ol-addapp.png?w=1071&#x26;fm=avif" alt=""><figcaption><p>添加应用程序</p></figcaption></figure></div>

在搜索栏中，输入 `SCIM`，然后选择 **SCIM Provisioner with SAML (SCIM v2 Enterprise)** App：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1nhhqAjka2eRfzl0cG00re/009afae8e9a056db414523aaf99392b2/remove-name-3.png?w=1359&#x26;fm=avif" alt=""><figcaption><p>SCIM Provisioner App</p></figcaption></figure></div>

为应用程序指定一个专用于 Bitwarden 的 **Display Name**，然后选择 **Save** 按钮。

### 配置 <a href="#configuration" id="configuration"></a>

从左侧导航中选择 **Configuration**，然后配置以下信息，其中一些信息需要从 Bitwarden 的 Single Sign-On 和 SCIM Provisioning 界面中获取。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2AeNYZyjrTZSU8CHupIXjY/d8e0475924f924fceebc9a6e4a2331b7/remove-name-4.png?w=1359&#x26;fm=avif" alt=""><figcaption><p>SCIM App 配置</p></figcaption></figure></div>

#### 应用程序详情 <a href="#application-details" id="application-details"></a>

即使您不打算使用单点登录，OneLogin 也会要求您填写 **SAML Audience URL** 和 **SAML Consumer URL** 字段。[了解在这些字段中应输入什么内容](onelogin-scim-integration.md#configuration)。

#### API 连接 <a href="#api-connection" id="api-connection"></a>

在 **API Connection** 部分输入以下值：

| Application 设置    | 描述                                                                     |
| ----------------- | ---------------------------------------------------------------------- |
| SCIM Base URL     | 将此字段设置为 SCIM URL（[了解更多](onelogin-scim-integration.md#enable-scim)）。    |
| SCIM Bearer Token | 将此字段设置为 SCIM API 密钥（[了解更多](onelogin-scim-integration.md#enable-scim)）。 |

配置好这些字段后，选择 **Save**。

### 访问权限 <a href="#access" id="access"></a>

从左侧导航中选择 **Access**。在 **Roles** 部分，将应用程序访问权限指派给您希望在 Bitwarden 中配置的所有角色。在您的 Bitwarden 组织中，每个角色都被视为一个群组，指派给任何角色的用户都将包含在每个群组中，即使他们被分配了多个角色。

### 规则 <a href="#rules" id="rules"></a>

创建一个将 OneLogin 角色映射到 Bitwarden 群组的规则：

1、从左侧导航中选择 **Rules**。

2、选择 Add Rule 按钮，打开 **New mapping** 对话框：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/42I8sAk9GBypUCDFxWbb4V/3c34b07f12bc62fb85270bf91881f582/Screen_Shot_2022-07-21_at_12.14.25_PM.png?w=991&#x26;fm=avif" alt=""><figcaption><p>角色/群组映射</p></figcaption></figure></div>

3、为规则起一个 **Name**，例如 Create Groups from Rules。

4、将 **Conditions** 留空。

5、在 **Actions** 部分：

1. 从第一个下拉菜单中选择 **Set Groups in \<application\_name>**。
2. 选择 **Map from OneLogin** 选项。
3. 从「For each」下拉菜单中选择 **role**。
4. 在「with value that matches」字段中输入 `.*` 以将所有角色映射到群组，或输入特定角色名称。

6、选择 **Save** 按钮以完成规则的创建。

### 测试连接 <a href="#test-connection" id="test-connection"></a>

从左侧导航中选择 **Configuration**，然后选择 **API Status** 下方的 **Enable** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6JJ9yBJshFhR7BgxXBg83K/74cc06192465100b109c6f94cc9ae680/remove-name-6.png?w=1222&#x26;fm=avif" alt=""><figcaption><p>测试 API 连接</p></figcaption></figure></div>

此测试**不会**开始配置，但如果应用程序成功从 Bitwarden 获得响应，则会向 Bitwarden 发出 GET 请求并显示 **Enabled**。

### 启用配置 <a href="#enable-provisioning" id="enable-provisioning"></a>

从左侧导航中选择 **Provisioning**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/YMC1HjBpeKREdb3lJNHqb/1abdcbb216848efb62795c921edc05b5/image.png?w=1372&#x26;fm=avif" alt=""><figcaption><p>配置设置</p></figcaption></figure></div>

在此界面上：

1. 选中 **Enable provisioning** 复选框。
2. 在 **When users are deleted in OneLogin...** 下拉菜单中，选择 **Delete**。
3. 在 **When user accounts are suspended in OneLogin...** 下拉菜单中，选择 **Suspend**。

完成后，选择 **Save** 以触发配置。

### 指定群组以进行配置 <a href="#designate-groups-to-provision" id="designate-groups-to-provision"></a>

从左侧导航中选择 **Parameters**。从表中选择 **Groups**，启用 **Include in User Provisioning** 复选框，然后选择 **Save** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2h03FR4hdjbrxWuUojzzGb/c004d00d53e780b98429453f20591125/remove-name-5.png?w=908&#x26;fm=avif" alt=""><figcaption><p><strong>Include in User Provisioning</strong></p></figcaption></figure></div>

### 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

## 附录 <a href="#appendix" id="appendix"></a>

### 用户属性 <a href="#user-attributes" id="user-attributes"></a>

Bitwarden 和 OneLogin 的 SCIM Provisioner with SAML (SCIM v2 Enterprise) 应用程序都使用标准的 SCIM v2 属性名称。Bitwarden 将使用以下属性：

* `active`
* `emails`<mark style="color:red;">**ª**</mark> 或 `userName`
* `displayName`
* `externalId`

<mark style="color:red;">**ª**</mark> - 由于 SCIM 允许用户拥有多个电子邮箱地址（以对象数组形式表示），Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

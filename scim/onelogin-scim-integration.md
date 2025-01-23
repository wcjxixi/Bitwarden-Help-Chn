# OneLogin SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/onelogin-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 用于在您的 Bitwarden 组织中自动配置和取消配置成员和群组。

{% hint style="info" %}
SCIM 集成适用于**企业组织**。团队组织或未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用[目录连接器](../directory-connector/directory-connector-cli.md)作为替代的预配方式。
{% endhint %}

本文将帮助您配置与 OneLogin 的 SCIM 集成。配置涉及同时使用 Bitwarden 网页密码库和 OneLogin 管理员门户。在进行配置时，我们建议您准备好这两样东西，并按照文档规定的顺序完成这些步骤。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../self-hosting/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开您组织的**管理** → **SCIM 配置**页面：

{% embed url="https://bitwarden.com/_gatsby/image/c70bf678c406888fdf350cedde0490ed/684599a3378fc51acd1d29f150dcb312/scim1.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6sw1kuK7GuZ3dfQkkbs6rV%2F11680a14a2c77af699e8c5a9d86394c6%2Fscim1.png&a=w%3D850%26h%3D473%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A07%3A34.818Z" %}
SCIM 配置
{% endembed %}

选中**启用 SCIM** 复选框并记下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中您将需要使用这两个值。

## 创建一个 OneLogin 应用程序 <a href="#create-a-onelogin-app" id="create-a-onelogin-app"></a>

{% hint style="success" %}
如果您的 SSO 登录已在使用此 IdP，请打开现有的企业应用程序并[跳至此步骤](onelogin-scim-integration.md#enable-provisioning)。否则，继续本部分以创建一个新的应用程序。
{% endhint %}

在 OneLogin 门户中，导航到 **Applications** 页面然后选择 **Add App** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/6718cb95cc3db83c5cc5b3538334263e/61a5b8ab41fe70535ba29946bf7a94f9/ol-addapp.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F37OSt7e5j969j9ikvH8buI%2F3bf9fa6b57a45b357a9d2bc012d8a6af%2Fol-addapp.png&a=w%3D850%26h%3D232%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A21%3A01.206Z" %}
添加应用程序
{% endembed %}

在搜索栏中，输入 `SCIM` 然后选择 **SCIM Provisioner with SAML (SCIM v2 Enterprise)** 应用程序：

{% embed url="https://bitwarden.com/_gatsby/image/09edf35733c2257b7bcc7b510d9cad95/02be0a0a1922d2ed743e4c57a532c5a9/remove-name-3.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F1nhhqAjka2eRfzl0cG00re%2F009afae8e9a056db414523aaf99392b2%2Fremove-name-3.png&a=w%3D850%26h%3D413%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A09%3A31.682Z" %}
SCIM Provisioner App
{% endembed %}

为您的应用程序指定一个专用于 Bitwarden 的 **Display Name**，然后选择 **Save** 按钮。

### 配置 <a href="#configuration" id="configuration"></a>

从左侧导航中选择 **Configuration** 并配置以下信息，其中一些信息需要从 Bitwarden 的 Single Sign-On 和 SCIM Provisioning 界面中检索获取。

{% embed url="https://bitwarden.com/_gatsby/image/50650ef6a221a0e25a53d09351173d4b/02be0a0a1922d2ed743e4c57a532c5a9/remove-name-4.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F2AeNYZyjrTZSU8CHupIXjY%2Fd8e0475924f924fceebc9a6e4a2331b7%2Fremove-name-4.png&a=w%3D850%26h%3D413%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A09%3A37.127Z" %}
SCIM App 配置
{% endembed %}

#### 应用程序详情 <a href="#application-details" id="application-details"></a>

即使您不打算使用单点登录，OneLogin 也会要求您填写 **SAML Audience URL** 和 **SAML Consumer URL** 字段。了解在这些字段中应输入的内容。

#### API 连接 <a href="#api-connection" id="api-connection"></a>

在 **API Connection** 部分输入以下值：

| **应用程序设置**        | **描述**                                                                 |
| ----------------- | ---------------------------------------------------------------------- |
| SCIM Base URL     | 将此字段设置为 SCIM URL（[了解更多](onelogin-scim-integration.md#enable-scim)）。    |
| SCIM Bearer Token | 将此字段设置为 SCIM API 密钥（[了解更多](onelogin-scim-integration.md#enable-scim)）。 |

配置好这些字段后，选择 **Save**。

### 访问权限 <a href="#access" id="access"></a>

从左侧导航中选择 **Access**。在 **Roles** 部分，将应用程序访问权限指派给您希望在 Bitwarden 中配置的所有角色。在您的 Bitwarden 组织中，每个角色都被视为一个群组，指派给任何角色的用户都将包含在每个群组中，包括为他们指派了多个角色。

### 参数 <a href="#parameters" id="parameters"></a>

从左侧导航中选择 **Parameters**。从表中选择 **Groups**，启用 **Include in User Provisioning** 复选框，然后选择 **Save** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/3913633bd7259d11b26a246138fb97af/45bc29c1c677ef2ff5d81ed57c62c8a5/remove-name-5.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F2h03FR4hdjbrxWuUojzzGb%2Fc004d00d53e780b98429453f20591125%2Fremove-name-5.png&a=w%3D850%26h%3D635%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A09%3A49.888Z" %}
Include Groups in User Provisioning
{% endembed %}

### 规则 <a href="#rules" id="rules"></a>

创建一个将 OneLogin 角色映射到 Bitwarden 群组的规则：

1、从左侧导航中选择 **Rules**。

2、选择 Add Rule 按钮以打开 **New mapping** 对话框：

{% embed url="https://bitwarden.com/_gatsby/image/7df36defa112affd41465dad64f46655/f63ed8d925ef638f7b72a6d1c792d1cc/Screen%20Shot%202022-07-21%20at%2012.14.25%20PM.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F42I8sAk9GBypUCDFxWbb4V%2F3c34b07f12bc62fb85270bf91881f582%2FScreen_Shot_2022-07-21_at_12.14.25_PM.png&a=w%3D850%26h%3D667%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A10%3A00.073Z" %}
角色/群组映射
{% endembed %}

3、为规则起一个 **Name**，例如 Create Groups from Rules。

4、将 **Conditions** 留空。

5、在 **Actions** 部分：

1. 从第一个下拉列表中选择 **Set Groups in \<application\_name>**。
2. 选择 **Map from OneLogin** 选项。
3. 从「For each」下拉列表中选择 **role**。
4. 在「with value that matches」字段中输入 `.*` 以将所有角色映射到群组，或输入特定角色名称。

6、选择 **Save** 按钮以完成规则的创建。

### 测试连接 <a href="#test-connection" id="test-connection"></a>

从左侧导航中选择 **Configuration**，然后选择 **API Status** 下的 **Enable** 按钮：

{% embed url="https://bitwarden.com/_gatsby/image/9992f616aae079c6d4167dc18795092d/677523f231b8875aefb0adec246eee6c/remove-name-6.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F6JJ9yBJshFhR7BgxXBg83K%2F74cc06192465100b109c6f94cc9ae680%2Fremove-name-6.png&a=w%3D850%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A10%3A08.963Z" %}
测试 API 连接
{% endembed %}

此测试**不会**开始配置，但如果应用程序成功从 Bitwarden 获得响应，则会向 Bitwarden 发出 GET 请求并显示 **Enabled**。

### 启用配置 <a href="#enable-provisioning" id="enable-provisioning"></a>

从左侧导航中选择 **Provisioning**：

{% embed url="https://bitwarden.com/_gatsby/image/00872f7434d6cb81872f84474687dcfd/d00e17d052b4c6dd60eede4bd3a48bdf/image.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2FYMC1HjBpeKREdb3lJNHqb%2F1abdcbb216848efb62795c921edc05b5%2Fimage.png&a=w%3D850%26h%3D500%26fm%3Dwebp%26q%3D75&cd=2022-08-12T12%3A04%3A00.545Z" %}
配置设置
{% endembed %}

在此界面上：

1. 选中 **Enable provisioning** 复选框。
2. 在 **When users are deleted in OneLogin...** 下拉列表中，选择 **Delete**。
3. 在 **When user accounts are suspended in OneLogin...** 下拉菜单中，选择 **Suspend**。

完成后，选择 **Save** 以触发配置。

## 完成用户入职 <a href="#finish-user-onboarding" id="finish-user-onboarding"></a>

现在您的用户已配置完毕，他们将收到加入组织的邀请。指导您的用户[接受邀请](../organizations/user-management.md#accept)，并在接受邀请后，[确认他们加入组织](../organizations/user-management.md#confirm)。

{% hint style="info" %}
邀请 → 接受 → 确认工作流程有利于解密密钥的握手，以允许用户安全地访问组织密码库数据。
{% endhint %}

## 附录 <a href="#appendix" id="appendix"></a>

### 用户属性 <a href="#user-attributes" id="user-attributes"></a>

Bitwarden 和 OneLogin 的 SCIM Provisioner with SAML (SCIM v2 Enterprise) 应用程序都使用标准的 SCIM v2 属性名称。Bitwarden 将使用以下属性：

* `active`
* `emails`ª 或 `userName`
* `displayName`
* `externalId`

ª -由于 SCIM 允许用户将多个电子邮件地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

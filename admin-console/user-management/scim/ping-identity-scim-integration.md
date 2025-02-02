# Ping Identity SCIM 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ping-identity-scim-integration/)
{% endhint %}

跨域身份管理系统 (SCIM) 可用于自动配置和取消配置 Bitwarden 组织中的成员和群组。

{% hint style="info" %}
SCIM 集成适用于**团队组织和企业组织**。未使用与 SCIM 兼容的身份提供程序的客户可以考虑使用 [Directory Connector](../../../directory-connector/directory-connector-cli.md) 作为替代的配置方式。
{% endhint %}

本文将帮助您配置 Ping Identity SCIM 集成。配置涉及同时使用 Bitwarden 网页密码库和 Ping Identity 管理员控制面板。在进行配置时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

## 启用 SCIM <a href="#enable-scim" id="enable-scim"></a>

{% hint style="info" %}
**您是自托管 Bitwarden 吗？**&#x5982;果是，请在继续操作之前完成[这些步骤为您的服务器启用 SCIM](../../../self-hosting/self-hosting-scim.md)。
{% endhint %}

要开始您的 SCIM 集成，请打开管理控制台并导航至**设置** → **SCIM 配置**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6sw1kuK7GuZ3dfQkkbs6rV/a4f4e18e561733297338e4ed44c6ed8c/2024-12-03_15-25-46.png?_a=DAJAUVWIZAAB" %}
SCIM 配置
{% endembed %}

选中**启用 SCIM** 复选框并记下您的 **SCIM URL** 和 **SCIM API 密钥**。在后面的步骤中您将需要使用这两个值。

## 创建 SCIM App <a href="#create-a-scim-app" id="create-a-scim-app"></a>

1、导航至配置 ✚**New Connection**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7rehLEEEAvNwsBHGKqDwln/babec3f81595ead3253285229fe0e653/2024-10-09_11-29-32.png?_a=DAJAUVWIZAAB" %}
Ping Identity **New Connection**
{% endembed %}

2、在创建新连接窗口中，为 **Identity Store** 选择 **Select** 选项。

3、在 **Identity Store** 中，在搜索框中输入 SCIM，然后选择 **SCIM Outbound**。完成此步骤后，选择 **Next**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1FYhcQpQbuh78ypyLxi2Jn/9081de91a419870aad37dded7c5db080/2024-10-09_11-35-23.png?_a=DAJAUVWIZAAB" %}
SCIM 连接
{% endembed %}

4、为 SCIM 连接输入名称和描述。

5、接下来，您需要输入 **SCIM BASE URL**。复制 Bitwarden 管理控制台中启用 SCIM 页面上的  **SCIM URL** 值并粘贴到该字段中。

6、使用 **Authentication Method** 下拉菜单，选择 **OAuth 2 Bearer Token**。此时会出现一个名为 **Oauth Access Token** 的字段，请将 Bitwarden 管理控制台中的 **SCIM API key** 值粘贴到该字段中。&#x20;

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7uGtHe2xM6QxJnqs5LNycl/6408a86d4332001ab1dac5f99c222887/2024-10-09_12-06-25.png?_a=DAJAUVWIZAAB" %}
Ping Identity SCIM 连接测试
{% endembed %}

7、设置完成后，您可以选择 **Test Connection**。如果成功，请选择 **Next**。

8、在 **Configure Preferences** 页面，选择所需的首选项和操作。

{% hint style="info" %}
如果用户不符合 Ping Identity 上设置的筛选标准，将移除操作设置为 `Disable` 将导致 Bitwarden 用户被移至 `Revoked` 状态。恢复标准将使用户恢复到 `previous state`。

如果移除操作设置为 `Delete`，同样的操作将取[消配置用户](../../../organizations/user-management.md#offboard-users)。
{% endhint %}

9、完成后选择 **Save**。 选择新创建的连接，使用切换键启用连接。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1GpO1UTspVLzLh0SwRgKuf/4669f4225cca00108f4f0a8700c38e2e/2024-10-09_14-13-24.png?_a=DAJAUVWIZAAB" %}
启用 Ping Identity 连接
{% endembed %}

## 创建规则 <a href="#create-a-rule" id="create-a-rule"></a>

在同步用户群组和目录之前，需要一个规则将用户群组同步到 Bitwarden SCIM。

1、返回 **Provisioning** 界面。

2、选择 **Rules** 选项卡，然后选择 ✚**New Rule**。

3、为规则输入一个特定于应用程序的名称，然后选择 **Create Rule**。

4、在 Configuration 选项卡中编辑新规则。选择 **Bitwarden SCIM connection**，然后 **Save**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3eKZXwtiFdQqhlUNRSm6jr/167c28c624cf7f9ceb7dc563d58c64f4/2024-10-09_14-11-35.png?_a=DAJAUVWIZAAB" %}
Ping Identity 规则
{% endembed %}

5、选择 Configuration 选项卡然后添加一个 **✏️User Filter**。

更多信息，请参阅 [Ping Identity 文档](https://docs.pingidentity.com/pingone/integrations/p1_add_provisioning_filter.html)。完成后选择 **Save**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1dgfaEYambvyHm7J4WBASe/9b2245b92629e61341856c8cb197be2f/2024-10-09_14-32-31.png?_a=DAJAUVWIZAAB" %}
Ping Identity 用户筛选器
{% endembed %}

6、使用切换键启用规则。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/73Y4cHkTeLtxtuqB3xIrOR/6faf11b60a278eab11f5c83d52035b57/2024-10-09_14-37-44.png?_a=DAJAUVWIZAAB" %}
Ping Identity 新增规则
{% endembed %}

## 配置群组 <a href="#provision-groups" id="provision-groups"></a>

1、要分配群组，请返回 Provisioning 界面，然后选择规则 **≡Edit Group Provisioning**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/10ztwQpTzsxZoi0vh83no6/f976a4f57d1fbe60b1f616f6114ce635/2024-10-09_15-11-57.png?_a=DAJAUVWIZAAB" %}
编辑 **Group Provisioning**
{% endembed %}

2、选择要配置的一个或多个组，然后选择 Save。保存后，目录将触发同步。

## 附录 <a href="#appendix" id="appendix"></a>

### 必要属性 <a href="#required-attributes" id="required-attributes"></a>

Bitwarden 和 Ping Identity **SCIM Provisioner with SAML (SCIM v2 Enterprise)** 应用程序都使用标准 SCIM v2 属性名称。Bitwarden 将使用以下属性：

#### 用户属性 <a href="#user-attributes" id="user-attributes"></a>

* `active`
* `emails`ª 或 `userName`
* `displayName`
* `externalId`

ª - 由于 SCIM 允许用户将多个电子邮箱地址表示为对象数组，因此 Bitwarden 将使用包含 `"primary": true` 的对象的 `value`。

#### 群组属性 <a href="#group-attributes" id="group-attributes"></a>

* `displayName`（**必填**）
* `members`ª
* `externalId`

ª - `members` 是一个对象数组，每个对象代表该群组中的一个用户。

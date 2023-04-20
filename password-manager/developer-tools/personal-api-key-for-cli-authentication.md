# 用于 CLI 验证的个人 API 密钥

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/personal-api-key/)
{% endhint %}

您的 Bitwarden 个人 API 密钥可以作为一种验证进入命令行界面（CLI）的方式。

{% hint style="info" %}
个人 API 密钥与用于访问 [Bitwarden 公共 API](../../organizations/bitwarden-public-api.md) 或[目录连接器](../../directory-connector/about-directory-connector.md)的[组织 API 密钥](../../organizations/bitwarden-public-api.md#authentication)是**不同的**。个人 API 密钥的 `client_id` 格式为 `"user.clientId"`，而组织 API 密钥的 `client_id` 格式为 `"organization.ClientId"`。
{% endhint %}

## 获取您的个人 API 密钥 <a href="#get-your-personal-api-key" id="get-your-personal-api-key"></a>

使用以下步骤来获取您的 API 密码：

1、在[网页密码库](https://vault.bitwarden.com/)中，选择配置文件图标然后从下拉列表中选择**帐户设置**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/74BqYDU6qE9evz6wEz8K7Y/773eec1c0b00e00db4dedd3456e9a3f9/Screen_Shot_2022-05-13_at_10.34.10_AM.png?fm=webp&h=226&q=50&w=773" %}
账户设置
{% endembed %}

2、从帐户设置菜单中，选择**安全**页面然后选择**密钥**选项卡：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3IHpaOpEB5a13TF3B3RqqB/2d3f5e721eda8aa02210c4b476fc9434/Screen_Shot_2022-05-18_at_9.17.41_AM.png?fm=webp&h=594&q=50&w=787" %}
密钥选项卡
{% endembed %}

3、选择**查看 API 密钥**按钮后将提示您输入主密码。

输入正确的主密码后，将为你提供以下内容：

* `client_id: "user.clientId"` （这个值对于你的账户是唯一的，并且不会改变）
* `client_secret: "clientSecret"` （这个值是唯一的，但可以被轮换）
* `scope: "api"` （这个值固定为 `"api"`）
* `grant_type: "client_credentials"` （这个值固定为`"client_credentials"`）

### 轮换您的 API 密钥 <a href="#rotate-your-api-key" id="rotate-your-api-key"></a>

选择**轮换 API 密钥**按钮来轮换您的个人 API 密钥。轮换您的密钥将只会更改您的 `client_secret` 的值。

轮换您的密钥将使您之前的密钥和所有使用该密钥的活动会话失效。

## 使用您的 API 密钥验证 <a href="#authenticate-using-your-api-key" id="authenticate-using-your-api-key"></a>

使用个人 API 密钥登录 CLI **建议用于自动化工作流程或对外部应用程序提供访问的场景**。要使用 API 密钥登录：

```shell
bw login --apikey
```

这将提示您输入获您的个人 `client_id` 和 `client_secret` 来进行验证。使用这些值对您的会话进行身份验证后，您就可以使用 `unlock` 命令了（[了解更多](password-manager-cli.md#unlock)）。

### 使用 API 密钥环境变量 <a href="#using-api-key-environment-variables" id="using-api-key-environment-variables"></a>

在使用 Bitwarden CLI 完成自动化工作的场景中，您可以保存环境变量以避免在身份验证时需要手动介入。

| 环境变量名称           | 要求的值            |
| ---------------- | --------------- |
| BW\_CLIENTID     | `client_id`     |
| BW\_CLIENTSECRET | `client_secret` |

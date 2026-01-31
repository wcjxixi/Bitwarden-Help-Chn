# 通过 API 密钥进行 CLI 验证

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/personal-api-key/)
{% endhint %}

您的 Bitwarden 个人 API 密钥可用作命令行界面 (CLI) 的验证方法。

{% hint style="info" %}
个人 API 密钥与[组织 API 密钥](../../../admin-console/bitwarden-public-api.md#authentication)是**不同的，**&#x7EC4;织 API 密钥用于访问 [Bitwarden 公共 API](../../../admin-console/bitwarden-public-api.md) 或[目录连接器](../../../admin-console/manage-members/directory-connector/about-directory-connector.md)。个人 API 密钥的 `client_id` 格式为 `"user.clientId"`，而组织 API 密钥的 `client_id` 格式为 `"organization.ClientId"`。
{% endhint %}

## 获取个人 API 密钥 <a href="#get-your-personal-api-key" id="get-your-personal-api-key"></a>

要获取您的个人 API 密钥：

1、在网页 App 中，导航到**设置** → **安全** → **密钥**：

{% embed url="https://bitwarden.com/assets/3IHpaOpEB5a13TF3B3RqqB/fab175095404a90d9d372542745bb9bb/Keys_settings.png?w=1200&fm=avif" %}
密钥设置
{% endembed %}

3、选择**查看 API 密钥**按钮然后输入主密码以验证访问权限。输入后，您将看到以下内容：

* `client_id: "user.clientId"` （这个值对于你的账户是唯一的，并且不会改变）
* `client_secret: "clientSecret"` （这个值是唯一的，但可以被轮换）
* `scope: "api"` （这个值固定为 `"api"`）
* `grant_type: "client_credentials"` （这个值固定为`"client_credentials"`）

### 轮换 API 密钥 <a href="#rotate-your-api-key" id="rotate-your-api-key"></a>

选择**轮换 API 密钥**按钮来轮换您的个人 API 密钥。轮换您的密钥将只会更改您的 `client_secret` 的值。

轮换您的密钥将使您之前的密钥和所有使用该密钥的活动会话失效。

## 使用 API 密钥验证身份 <a href="#authenticate-using-your-api-key" id="authenticate-using-your-api-key"></a>

使用个人 API 密钥进行 CLI 身份验证适用于自动化工作流程、提供对外部应用程序的访问权限，或者当您的账户使用 CLI 不支持的双重身份验证方法（FIDO2 或 Duo）时。以下命令将提示您输入您的个人 `client_id` 和 `client_secret`：

```shellscript
bw login --apikey
```

虽然有些命令不需要解密您的数据即可执行，但大多数 CLI 命令，需要您首先使用 `unlock` 命令（[了解更多](password-manager-cli.md#unlock)）对数据进行解密才能使用，除非您是使用 Key Connector 的组织成员。您的 API 密钥不能替代您的主密码。

### 使用 API 密钥环境变量 <a href="#using-api-key-environment-variables" id="using-api-key-environment-variables"></a>

在使用 Bitwarden CLI 完成自动化工作的场景中，您可以保存环境变量以避免在身份验证时需要手动介入。

| 环境变量名称           | 要求的值            |
| ---------------- | --------------- |
| BW\_CLIENTID     | `client_id`     |
| BW\_CLIENTSECRET | `client_secret` |

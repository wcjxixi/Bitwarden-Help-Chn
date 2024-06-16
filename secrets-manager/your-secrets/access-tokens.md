# 访问令牌

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/access-tokens/)
{% endhint %}

访问令牌是促进[机器账户](machine-accounts.md)访问和解密存储在 Secrets Manager 中的[机密](secrets.md)的对象。访问令牌颁发给特定的机器账户，并将赋予应用它们的任何机器仅能访问**与该机器账户相关联的机密**的能力。

## 创建访问令牌 <a href="#create-an-access-token" id="create-an-access-token"></a>

访问令牌永远不会存储在 Bitwarden 数据库中并且无法检索，因此在生成访问令牌时请注意将其存储在安全的地方。要创建访问令牌：

1、从导航中选择**机器账户**。

2、选择要为其创建访问令牌的机器账户，然后打开**访问令牌**选项卡：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6EINDaXiPQp9qQcO6q1zt5/40e157b6e8385572f58e817d49100c7a/Screenshot_2024-04-09_at_10.40.41_AM.png?_a=BAJFJtWIB" %}
创建访问令牌
{% endembed %}

3、选择**创建访问令牌**按钮。

4、在「创建访问令牌」窗口中，提供以下信息：

* 令牌的**名称**。
* 令牌的**到期**时间。默认为 `从不`。

5、完成令牌配置后，选择**创建访问令牌**按钮。

6、将出现一个显示访问令牌的窗口。关闭此窗口之前请将您的令牌复制到安全的地方，因为您的令牌**不会被存储并且以后无法获取**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3QfpdSQai2hFrWGdGSlQRN/8453d5425eba62421e443b4b7a677f7a/Screenshot_2024-04-09_at_10.41.34_AM.png?_a=BAJFJtWIB" %}
访问令牌示例
{% endembed %}

此访问令牌是身份验证工具，通过它您可以编写机密注入脚本到您的机器和应用程序中。

## 使用访问令牌 <a href="#use-an-access-token" id="use-an-access-token"></a>

访问令牌用于 [Secrets Manager CLI](../developer-tools/secrets-manager-cli.md) 的身份验证。您创建了访问令牌并将其值保存在安全的地方后，就可以通过 CLI 来使用它验证机密检索命令，以注入您的应用程序或基础设施。它可以：

*   将访问令牌导出到主机上的 `BWS_ACCESS_TOKEN` 环境变量。如下所示的 CLI 命令将自动检查具有该密钥的变量以进行身份​​验证：

    ```batch
    bws get secret fc3a93f4-2a16-445b-b0c4-aeaf0102f0ffText C
    ```
*   在脚本中使用 `-access-token` 选项 `get` 和注入机密，例如包含以下行的内容：

    ```batch
    ...
    export DB_PW=$(bws get secret fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff --access-token 0.48c78342-1635-48a6-accd-afbe01336365.C0tMmQqHnAp1h0gL8bngprlPOYutt0:B3h5D+YgLvFiQhWkIq6Bow== | .jq '.value')
    ...
    docker run -d database ... -env DB_PW=$DB_PW ... mysql:latest
    ```
* 使用我们专用的 [GitHub Actions 集成](../integrations/github-actions.md)将访问令牌保存为存储库机密，以便在您的工作流文件中使用。

## 吊销访问令牌 <a href="#revoke-an-access-token" id="revoke-an-access-token"></a>

您可以随时吊销访问令牌。**吊销令牌将破坏当前使用它的任何机器检索和解密机密的能力**。要吊销令牌：

1、从导航中选择**机器账户**，然后打开**访问令牌**选项卡。

2、对于要撤销的访问令牌，使用 (**≡**) 选项菜单选择**吊销访问令牌**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1rujDBqHJ6lYy26kqmTZw4/e280c0f28b2b2377e8d9c4f07b7f6f5e/Screenshot_2024-04-10_at_9.51.37_AM.png?_a=BAJFJtWIB" %}
吊销访问令牌
{% endembed %}

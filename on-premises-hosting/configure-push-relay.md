# 配置推送中继

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/configure-push-relay/)
{% endhint %}

默认情况下，您的自托管 Bitwarden 服务器配置为与 Bitwarden 的推送中继服务（`https://push.bitwarden.com`）进行通信。您可以选择使用自己的推送中继服务来配置服务器或完全禁用推送中继。

{% hint style="warning" %}
禁用推送中继将阻止移动应用程序[自动同步](../your-vault/syncing-your-vault.md#what-is-vault-syncing)，但用户仍然可以[手动同步](../your-vault/syncing-your-vault.md#what-is-vault-syncing-1)他们的密码库。
{% endhint %}

## 更改推送中继服务 <a href="#change-push-relay-service" id="change-push-relay-service"></a>

要使用您自己的推送中继服务配置服务器：

1. 打开 `./bwdata/docker/global.env`。
2. 在 `globalSettings__pushRelayBaseUri=` 中指定您的推送中继服务的 URI。
3. 运行 `./bitwarden.sh restart` 以应用您的更改。

## 禁用推送中继 <a href="#disable-push-relay" id="disable-push-relay"></a>

要为服务器禁用推送中继：

1. 打开 `./bwdata/config.yml`。
2. 将 `push_notifications: true` 属性更改为 `false`。
3. 运行 `./bitwarden.sh rebuild` 以应用您的更改。

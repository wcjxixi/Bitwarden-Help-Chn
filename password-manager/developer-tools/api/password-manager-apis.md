# Password Manager API

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/bitwarden-apis/)
{% endhint %}

Bitwarden 目前提供两种具有不同功能和用例的 API：

## 公共 API <a href="#public-api" id="public-api"></a>

Bitwarden 公共 API 为组织提供了一套用于管理成员、集合、群组、事件日志和策略的工具。

公共 API 是一个 RESTful API，具有可预测的面向资源的 URL，接受 JSON 编码的请求正文，返回 JSON 编码的响应，并使用标准的 HTTP 响应代码、身份验证和动词。

了解有关 [Bitwarden 公共 API](../../../organizations/bitwarden-public-api.md) 的更多信息或查看 [API 规范](https://bitwarden.com/help/api/)文档。

## 密码库管理 API <a href="#vault-management-api" id="vault-management-api"></a>

密码库管理 API 为 Bitwarden 用户提供了一套用于管理密码库项目的工具，包括那些由组织拥有的项目，前提是您必须拥有相应的权限。

密码库管理 API 以 RESTful API 调用的形式执行 Bitwarden CLI 可以执行的大多数操作。使用密码库管理 API 需要使用 CLI 中的 `serve` 命令来启动本地 Express 网络服务器，以便从该服务器发出请求。

{% hint style="info" %}
密码库管理 API 接受 JSON 请求体并返回 JSON 响应，包括标准 HTTP 响应代码。
{% endhint %}

了解有关 [serve 命令](../cli/password-manager-cli.md#serve)的更多信息或查看 [API 规范](https://bitwarden.com/help/vault-management-api/)文档。

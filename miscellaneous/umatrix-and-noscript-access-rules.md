# uMatrix 和 NoScript 访问规则

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/blocker-access-rule/)
{% endhint %}

默认情况下，[uMatrix 扩展](https://github.com/gorhill/uMatrix)和 [NoScript 扩展](https://noscript.net/)可能会阻止 Bitwarden Firefox 扩展访问 Bitwarden API 服务器。如果不添加适当的规则将 Bitwarden API 服务器列入白名单，登录以及其他 API 操作将失败。

## uMatrix

需要以下 [uMatrix 规则](https://github.com/gorhill/uMatrix/wiki/Rules-syntax)：

```
dc8ef5f6-eb0d-4c87-9e9f-0cf803f619e8.moz-extension-scheme bitwarden.com xhr allow
```

{% hint style="info" %}
&#x20;上述规则中的 UUID（`dc8ef5f6-eb0d-4c87-9e9f-0cf803f619e8`）对于您的安装是不一样的。访问`about:debugging#/runtime/this-firefox`页面（从 Firefox 的地址栏导航）以找到属于您的 Bitwarden 扩展的 UUID。
{% endhint %}

## NoScript

需要在 NoScript 中将以下域名列入白名单： `bitwarden.com`

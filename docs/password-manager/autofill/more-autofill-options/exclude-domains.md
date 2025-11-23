# 对指定网站屏蔽自动保存

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/exclude-domains/)
{% endhint %}

Bitwarden 浏览器扩展可配置为排除指定站点，使其不触发[自动保存通知](../autofill-from/autosave-from-browser-extensions.md)。当某个域名位于**排除域名**列表中时，Bitwarden 不会发出任何可用的通知，包括保存新的登录、更新现有登录、保存或使用通行密钥：

{% embed url="https://bitwarden.com/assets/4vsurEuH5deik26BWn4n1p/b14619e64cd8cd9c1cd4aa2d9f2fe88a/2025-05-20_16-17-25.png?w=1007&fm=avif&q=80" %}
询问添加登录
{% endembed %}

要配置排除域名，请导航到 **️设置** → **通知** → **排除域名**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/qUGIVQR379ac3R2dXdoy8/06b4dec0b9e02911903052789c44723c/2024-12-03_11-00-24.png?_a=DAJCwlWIZAAB" %}
排除域名配置
{% endembed %}

域名排除不会注册「完整」的 URL，只会注册域名组件。例如 `https://github.com/bitwarden/browser` 在保存时将解析为 `github.com`，这意味着浏览器扩展将明确不为 Github 提示保存凭证。

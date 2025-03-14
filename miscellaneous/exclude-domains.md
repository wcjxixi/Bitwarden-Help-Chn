# 排除域名

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/exclude-domains/)
{% endhint %}

Bitwarden 浏览器扩展可以配置排除特定域名（即明确不为其提示保存密码）。当某个域名位于**排除域名**列表中时，Bitwarden 不会弹出提示记住输入的密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7GnwQ6UKY6er7PpCWj6xn0/3c4804ffe63521cc5c48394d0f9624d6/2024-12-02_14-08-47.png?_a=DAJCwlWIZAAB" %}
添加登录
{% endembed %}

当某个域名被列入排除域列表时，Bitwarden 浏览器扩展也不会发出[通行密钥提示](../password-manager/vault-basics/storing-passkeys.md)。

要配置排除域名，请打开 **⚙️设置**选项卡，然后选择**通知**，再选择**排除域名**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/qUGIVQR379ac3R2dXdoy8/06b4dec0b9e02911903052789c44723c/2024-12-03_11-00-24.png?_a=DAJCwlWIZAAB" %}
排除域名配置
{% endembed %}

域名排除不会注册「完整」的 URL，只会注册域名组件。例如 `https://github.com/bitwarden/browser` 在保存时将解析为 `github.com`，这意味着浏览器扩展将明确不为 Github 提示保存凭证。

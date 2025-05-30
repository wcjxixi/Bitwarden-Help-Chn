# 自动填充基本验证提示

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/basic-auth-autofill/)
{% endhint %}

像下图这样的登录提示，被称为「基本」或「原生」验证提示，**如果只有 1 个具有**[**匹配 URI**](../troubleshoot-autofill/forming-uris-for-autofill.md) **的登录项目**，Bitwarden 浏览器扩展将自动填充。您也可以使用浏览器扩展的 **⮫启动**按钮来自动打开并登录基本的受自治保护的资源。

默认情况下，基本验证提示的自动填充将使用[主机](../troubleshoot-autofill/forming-uris-for-autofill.md#host) URI 匹配检测选项，这样自动填充的限制性更强。可以通过设置相关密码库项目的[匹配检测选项](../troubleshoot-autofill/forming-uris-for-autofill.md)来更改。

如果发现多个登录项目有匹配的 URI，浏览器扩展将无法自动填充您的凭据，您需要手动复制/粘贴您的用户名和密码来登录。

如果只有一个有匹配 URI 的登录项目，则凭据将在后台自动填充，并且不会显示验证提示。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6rUtQ8FzPTPuKM0sXZ4iyc/3fc116ce5eba8bc70f8dbebfac0eafa6/basic-auth-prompt.png?fm=webp&h=368&q=50&w=1192" %}
基本验证提示
{% endembed %}

{% hint style="info" %}
由于基本验证提示的设计方式，自动填充必须是非交互式的。这意味着您不能使用**密码库**视图、上下文菜单或键盘快捷键在基本验证提示上进行自动填充。
{% endhint %}

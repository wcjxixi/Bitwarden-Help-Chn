# 从浏览器扩展自动保存

{% hint style="success" %}
询问更新现有登录对应的[官方文档地址](https://bitwarden.com/help/autosave-from-browser-extensions/)
{% endhint %}

Bitwarden 浏览器扩展提供一系列内置的浏览器通知，可将您的解密数据与您在登录、注册和类似网页表单中输入的数据进行比较。其中包括：

* 保存或使用通行密钥的通知。
* 添加未检测到的登录的通知。
* 更新现有登录的通知。

这些通知默认为激活状态，但可以通过浏览器扩展的**设置** → **通知**菜单将其关闭。

{% hint style="success" %}
您还可以从**设置** → **通知** → **排除域名**菜单中阻止指定网站以触发自动保存通知。了解[对指定网站屏蔽自动保存](../more-autofill-options/exclude-domains.md)。
{% endhint %}

## 询问保存和使用通行密钥 <a href="#ask-to-save-and-use-passkeys" id="ask-to-save-and-use-passkeys"></a>

当 Bitwarden 检测到您正在为某个网站创建新的通行密钥，或提示您使用已保存在 Bitwarden 中的通行密钥登录时，Bitwarden 将会提示您：

{% embed url="https://bitwarden.com/assets/5KeuUZox5shd0zDMxPHKXn/1aab35dfceed0ed9cdb17b143be9a890/2024-10-29_11-39-33.png?w=961&fm=avif&q=80" %}
使用通行密钥登录
{% endembed %}

更多信息请参阅[自动填充通行密钥](../more-autofill-options/autofill-passkeys.md)。

## 询问添加登录 <a href="#ask-to-add-login" id="ask-to-add-login"></a>

当 Bitwarden 检测到您为一个未存储在 Bitwarden 中的页面输入了登录信息时，Bitwarden 将会提示您将这些凭据保存到 Bitwarden 中：

{% embed url="https://bitwarden.com/assets/4vsurEuH5deik26BWn4n1p/b14619e64cd8cd9c1cd4aa2d9f2fe88a/2025-05-20_16-17-25.png?w=1007&fm=avif&q=80" %}
询问添加登录
{% endembed %}

从该通知中，您可以选择是将其存储在个人项目（即**我的密码库**）中，还是存储在某个组织中。在保存之前，您还可以使用编辑 **✏️**按钮对项目进行编辑。

## 询问更新现有登录 <a href="#ask-to-update-existing-login" id="ask-to-update-existing-login"></a>

当 Bitwarden 检测到您在 Bitwarden 中已保存的项目的表单上输入的登录信息与您保存的信息不一致时，例如，如果您最近在某个网站上更新了密码，但没有在 Bitwarden 中更新，Bitwarden 将会提示您在 Bitwarden 中更新您的凭据：

{% embed url="https://bitwarden.com/assets/3nn8Vz526Il3onWPHMUUAi/90fd3af3616b60c2961064a56205d525/2025-05-20_16-19-00.png?w=1007&fm=avif&q=80" %}

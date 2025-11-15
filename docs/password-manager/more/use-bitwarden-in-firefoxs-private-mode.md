# 在 Firefox 隐私窗口中使用 Bitwarden

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/private-mode/)
{% endhint %}

## 允许隐私窗口 <a href="#allow-private-windows" id="allow-private-windows"></a>

要允许浏览器扩展在 Firefox 隐私窗口中运行：

1. 在浏览器中导航到 `about:addons`，然后从扩展列表中选择 Bitwarden。
2. 在**详细信息**选项卡上，向下滚动到**在隐私窗口中运行**并切换为**允许**。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1tdckgSp5yF97cp3Jk1nsw/41ae31a8c39b067edefb09a6236d9302/Screen_Shot_2022-03-10_at_11.56.20_AM.png?fm=webp&h=474&q=50&w=916" %}
在隐私窗口中启用扩展
{% endembed %}

## ~~隐私窗口的限制~~ <a href="#limitations-in-private-windows" id="limitations-in-private-windows"></a>

~~虽然浏览器扩展在 Firefox 隐私窗口中可以展示全部功能，但需要考虑一些限制：~~

* ~~使用~~[~~上下文菜单~~](../autofill/autofill-from/autofill-from-browser-extensions.md#using-the-context-menu)~~和~~[~~键盘快捷键~~](../autofill/autofill-from/autofill-from-browser-extensions.md#using-keyboard-shortcuts)~~自动填充要求在非隐私窗口中才能解锁密码库。~~
* ~~每次浏览器扩展关闭时，您的密码库都会被锁定，除非您将密码库超时设置为**从不**。或者，您可以将浏览器扩展作为侧边栏以绕过此限制。~~
* ~~仅当未选中**在浏览器重新启动时使用主密码锁定**选项时，PIN 解锁才有效。~~
* [~~徽章图标~~](../autofill/autofill-from/autofill-from-browser-extensions.md)~~不会更新以显示密码库的状态（_已锁&#x5B9A;_&#x6216;_已解锁_）。~~

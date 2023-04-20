# 键盘快捷键

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/keyboard-shortcuts/)
{% endhint %}

## 浏览器扩展快捷键 <a href="#browser-extension-shortcuts" id="browser-extension-shortcuts"></a>

某些浏览器，包括 Microsoft Edge，可能会将以下组合键用做其他的默认快捷键。在这些情况下，您需要配置浏览器快捷的键。对于基于 Chromium 的浏览器（Chrome、Edge、Vivaldi、Brave 等），这可以通过 `chrome://extensions/shortcuts`、`edge://extensions/shortcuts` 等完成。对于 Firefox，使用[此文](https://support.mozilla.org/zh-CN/kb/%E7%AE%A1%E7%90%86Firefox%E7%9A%84%E6%89%A9%E5%B1%95%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F)来帮助您管理扩展程序快捷键。

{% hint style="info" %}
Microsoft Edge 的自动填充要求是最新的基于 Chromium 的版本。
{% endhint %}

* Ctrl/CMD + Shift + Y → 激活扩展
* Ctrl/CMD + Shift + L → 自动填充，再次按下可在匹配的登录名之间循环
* Ctrl/CMD + Shift + 9 → 生成密码并复制到剪贴板
* Ctrl/CMD + Shift + N → 锁定扩展

{% hint style="success" %}
如果一个登录使用 [Bitwarden TOTP 验证器](../../your-vault/totp.md)，使用 `Cmd/Ctrl + Shift + L` 会在自动填充后自动将您的 TOTP 复制到剪贴板。您所要做的就是 `Cmd/Ctrl + V` 粘贴！
{% endhint %}

## 桌面应用程序快捷键 <a href="#desktop-application-shortcuts" id="desktop-application-shortcuts"></a>

**通用：**

* Ctrl/CMD + , → 首选项
* Ctrl/CMD + L → 立即锁定
* Ctrl/CMD + Q → 退出

**文件：**

* Ctrl/CMD + N → 添加新的登录

**编辑：**

* Ctrl/CMD + Z → 撤销
* Ctrl/CMD + Y → 重做
* Ctrl/CMD + X → C剪切
* Ctrl/CMD + C → 复制
* Ctrl/CMD + V → 黏贴
* Ctrl/CMD + A → 全选
* Ctrl/CMD + U → 复制用户名
* Ctrl/CMD + P → 复制密码
* Ctrl/CMD + T → 复制 TOTP

**查看：**

* Ctrl/CMD + F → 搜索密码库
* Ctrl/CMD + G → 密码生成器
* Ctrl/CMD + = → 放大
* Ctrl/CMD + - → 缩小
* Ctrl/CMD + 0 → 重置缩放
* F11 → 全屏
* Ctrl/CMD + Shift + R → 重新加载
* F12 → 开发者选项

**窗口：**

* Ctrl/CMD + M → 最小化
* Ctrl/CMD + Shift + M → 发送到托盘/隐藏到菜单栏
* Ctrl/CMD + Shift + T → 总在最前
* Ctrl/CMD + W → 关闭窗口

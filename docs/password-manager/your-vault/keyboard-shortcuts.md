# 键盘快捷键

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/keyboard-shortcuts/)
{% endhint %}

键盘快捷键能加速完成 Bitwarden 中的常用操作，例如自动填充登录信息和保存新项目。它们可以帮助您更高效地进行导航，并为使用鼠标提供了一种重要的替代方案。

## 浏览器扩展快捷键 <a href="#browser-extension-shortcuts" id="browser-extension-shortcuts"></a>

这些快捷键允许您使用键盘操作 Bitwarden 浏览器扩展。如果快捷键不起作用，您可能需要更新浏览器的快捷键设置。

### 通用 <a href="#general" id="general"></a>

| 作用          | 按键                         |
| ----------- | -------------------------- |
| 激活扩展        | `Ctrl/Cmd` + `Shift` + `Y` |
| 生成密码并复制到剪贴板 | `Ctrl/Cmd` + `Shift` + `9` |
| 锁定密码库       | `Ctrl/Cmd` + `Shift` + `N` |

### 自动填充 <a href="#autofill" id="autofill"></a>

您可以[使用键盘快捷键自动填充凭据](../autofill/autofill-from/autofill-from-browser-extensions.md#keyboard-shortcuts)至网站。当用户名和密码字段在同一页面上并列出现时，或在分步登录流程中分别出现时，自动填充快捷键均可生效。

| 作用               | 按键                                                                                                       |
| ---------------- | -------------------------------------------------------------------------------------------------------- |
| 自动填充当前网站上次使用的登录。 | <p><code>Ctrl/Cmd</code> + <code>Shift</code> + <code>L</code></p><p>再次按下可在匹配的登录之间循环。</p>                |
| 自动填充上次使用的支付卡。    | [创建键盘快捷键](../autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-keyboard-shortcuts)。 |
| 自动填充上次使用的身份。     | [创建键盘快捷键](../autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-keyboard-shortcuts)。 |

{% hint style="success" %}
如果登录使用 [Bitwarden 身份验证器](security-tools/totp.md)生成的 TOTP，并且您使用自动填充快捷键，则 TOTP 会在自动填充后自动复制到剪贴板。按下 `Cmd/Ctrl` + `V` 以粘贴 TOTP。
{% endhint %}

### 自定义浏览器扩展快捷键 <a href="#customize-browser-extension-shortcuts" id="customize-browser-extension-shortcuts"></a>

部分浏览器（包括 Microsoft Edge 和 Safari）使用的默认快捷键与 Bitwarden 的快捷键存在冲突。要解决此问题，请调整浏览器的默认快捷键，使 Bitwarden 的快捷键能够正常工作。具体步骤因浏览器而异：

* **基于 Chromium 的浏览器（包括 Chrome、Edge、Vivaldi、Brave）**：前往浏览器设置页面，例如 `chrome://extensions/shortcuts` 或 `edge://extensions/shortcuts`，更改存在冲突的快捷键或应用新的快捷键。
* **Safari**：更新 [Mac 键盘快捷键](https://support.apple.com/zh-cn/guide/mac-help/mchlp2271/mac)。您可能需要为显示/隐藏侧边栏重新分配快捷键，以确保[自动填充快捷键](keyboard-shortcuts.md#autofill)正常工作。
* **Firefox**：更新[扩展的快捷键设置](https://support.mozilla.org/zh-CN/kb/%E7%AE%A1%E7%90%86Firefox%E7%9A%84%E6%89%A9%E5%B1%95%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F)。

## 桌面应用程序快捷键 <a href="#desktop-application-shortcuts" id="desktop-application-shortcuts"></a>

**通用：**

* `Ctrl/CMD + ,` → 首选项
* `Ctrl/CMD + L` → 立即锁定
* `Ctrl/CMD + Q` → 退出

**文件：**

* `Ctrl/CMD + N` → 添加新的登录

**编辑：**

* `Ctrl/CMD + Z` → 撤销
* `Ctrl/CMD + Y` → 重做
* `Ctrl/CMD + X` → 剪切
* `Ctrl/CMD + C` → 复制
* `Ctrl/CMD + V` → 黏贴
* `Ctrl/CMD + A` → 全选
* `Ctrl/CMD + U` → 复制用户名
* `Ctrl/CMD + P` → 复制密码
* `Ctrl/CMD + T` → 复制 TOTP

**查看：**

* `Ctrl/CMD + F` → 搜索密码库
* `Ctrl/CMD + G` → 密码生成器
* `Ctrl/CMD + =` → 放大
* `Ctrl/CMD + -` → 缩小
* `Ctrl/CMD + 0` → 重置缩放
* `F11` → 全屏
* `Ctrl/CMD + Shift + R` → 重新加载
* `F12` → 开发者选项

**窗口：**

* `Ctrl/CMD + M` → 最小化
* `Ctrl/CMD + Shift + M` → 发送到托盘/隐藏到菜单栏
* `Ctrl/CMD + Shift + T` → 总在最前
* `Ctrl/CMD + W` → 关闭窗口

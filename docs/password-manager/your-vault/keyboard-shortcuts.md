# 键盘快捷键

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/keyboard-shortcuts/)
{% endhint %}

键盘快捷键能加速完成 Bitwarden 中的常用操作，例如[自动填充](../autofill/autofill-from/autofill-from-browser-extensions.md)登录信息和保存新项目。它们可以帮助您更高效地进行导航，并为使用鼠标提供了一种重要的替代方案。

## 浏览器扩展快捷键 <a href="#browser-extension-shortcuts" id="browser-extension-shortcuts"></a>

这些快捷键允许您使用键盘操作 Bitwarden 浏览器扩展。如果快捷键不起作用，您可能需要[更新浏览器的快捷键设置](keyboard-shortcuts.md#customize-browser-extension-shortcuts)。

### 通用 <a href="#general" id="general"></a>

| 作用          | 按键                         |
| ----------- | -------------------------- |
| 激活扩展        | `Ctrl/Cmd` + `Shift` + `Y` |
| 生成密码并复制到剪贴板 | `Ctrl/Cmd` + `Shift` + `9` |
| 锁定密码库       | `Ctrl/Cmd` + `Shift` + `N` |

### 自动填充 <a href="#autofill" id="autofill"></a>

您可以[使用键盘快捷键自动填充凭据](../autofill/autofill-from/autofill-from-browser-extensions.md#keyboard-shortcuts)至网站。当用户名和密码字段在同一页面上并列出现时，或在分步登录流程中分别出现时，自动填充快捷键均可生效。

| 作用              | 按键                                                                                                       |
| --------------- | -------------------------------------------------------------------------------------------------------- |
| 自动填充当前网站上次使用的登录 | <p><code>Ctrl/Cmd</code> + <code>Shift</code> + <code>L</code></p><p>再次按下可在匹配的登录之间循环</p>                 |
| 自动填充上次使用的支付卡    | [创建键盘快捷键](../autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-keyboard-shortcuts)。 |
| 自动填充上次使用的身份     | [创建键盘快捷键](../autofill/more-autofill-options/auto-fill-cards-and-identities.md#using-keyboard-shortcuts)。 |

{% hint style="success" %}
如果登录使用 [Bitwarden 身份验证器](security-tools/totp.md)生成的 TOTP，并且您使用自动填充快捷键，则 TOTP 会在自动填充后自动复制到剪贴板。按下 `Cmd/Ctrl` + `V` 以粘贴 TOTP。
{% endhint %}

### 自定义浏览器扩展快捷键 <a href="#customize-browser-extension-shortcuts" id="customize-browser-extension-shortcuts"></a>

部分浏览器（包括 Microsoft Edge 和 Safari）使用的默认快捷键与 Bitwarden 的快捷键存在冲突。要解决此问题，请调整浏览器的默认快捷键，使 Bitwarden 的快捷键能够正常工作。具体步骤因浏览器而异：

* **基于 Chromium 的浏览器（包括 Chrome、Edge、Vivaldi、Brave）**：前往浏览器设置页面，例如 `chrome://extensions/shortcuts` 或 `edge://extensions/shortcuts`，更改存在冲突的快捷键或应用新的快捷键。
* **Safari**：更新 [Mac 键盘快捷键](https://support.apple.com/zh-cn/guide/mac-help/mchlp2271/mac)。您可能需要为显示/隐藏侧边栏重新分配快捷键，以确保[自动填充快捷键](keyboard-shortcuts.md#autofill)正常工作。
* **Firefox**：更新[扩展的快捷键设置](https://support.mozilla.org/zh-CN/kb/%E7%AE%A1%E7%90%86Firefox%E7%9A%84%E6%89%A9%E5%B1%95%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F)。

## 桌面 App 快捷键 <a href="#desktop-app-shortcuts" id="desktop-app-shortcuts"></a>

### 通用 <a href="#general" id="general"></a>

| 作用                                              | 按键                         |
| ----------------------------------------------- | -------------------------- |
| 锁定密码库                                           | `Ctrl/Cmd` + `L`           |
| 打开 Bitwarden 首选项                                | `Ctrl/Cmd` + `,`           |
| 重新加载 Bitwarden 桌面 App                           | `Ctrl/Cmd` + `Shift` + `R` |
| 退出 Bitwarden 桌面 App                             | `Ctrl/Cmd` + `Q`           |
| 将光标置于密码库的搜索框中                                   | `Ctrl/Cmd` + `F`           |
| 打开 [Bitwarden 生成器](security-tools/generator.md) | `Ctrl/Cmd` + `G`           |

### 编辑项目 <a href="#edit-items" id="edit-items"></a>

| 作用               | 按键               |
| ---------------- | ---------------- |
| 添加新的登录           | `Ctrl/Cmd` + `N` |
| 编辑项目时撤销上一个操作     | `Ctrl/Cmd` + `Z` |
| 重做编辑中的项目的最后一个操作  | `Ctrl/Cmd` + `Y` |
| 选择当前活动字段或项目的所有文本 | `Ctrl/Cmd` + `A` |
| 剪切并复制选中的文本       | `Ctrl/Cmd` + `X` |
| 复制选中的文本          | `Ctrl/Cmd` + `C` |
| 粘贴最后复制的文本        | `Ctrl/Cmd` + `V` |
| 复制已打开项目的用户名      | `Ctrl/Cmd` + `U` |
| 复制已打开项目的密码       | `Ctrl/Cmd` + `P` |
| 复制已打开项目的 TOTP    | `Ctrl/Cmd` + `T` |

### 调整显示 <a href="#adjust-display" id="adjust-display"></a>

| 作用      |                                                                                    |
| ------- | ---------------------------------------------------------------------------------- |
| 放大      | `Ctrl/Cmd` + `=`                                                                   |
| 缩小      | `Ctrl/Cmd` + `-`                                                                   |
| 重置缩放级别  | `Ctrl/Cmd` + `0`                                                                   |
| 进入全屏模式  | <p>Windows 和 Linux：<code>F11</code></p><p>Mac：<code>Fn</code> + <code>F</code></p> |
| 打开开发者模式 | Windows 和 Linux：`F12`                                                              |

### 控制窗口 <a href="#control-window" id="control-window"></a>

| 作用                        |                                                                                    |
| ------------------------- | ---------------------------------------------------------------------------------- |
| 最小化 Bitwarden 桌面 App      | `Ctrl/Cmd` + `M`                                                                   |
| 将 Bitwarden 桌面 App 隐藏到托盘  | `Ctrl/Cmd` + `Shift` + `M`                                                         |
| 始终将 Bitwarden 桌面 App 置于顶层 | <p><code>Ctrl/Cmd</code> + <code>Shift</code> + <code>T</code></p><p>再次按下可撤消操作</p> |
| 关闭 Bitwarden 桌面 App 窗口    | `Ctrl/Cmd` + `W`                                                                   |

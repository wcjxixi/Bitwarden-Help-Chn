# 填充辅助

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/fill-assist/)
{% endhint %}

通过提供人工编写并审核的指令，帮助浏览器扩展确定如何自动填充凭据，填充辅助功能**提高了 Bitwarden 精选的网站上的自动填充的准确性**，这些网站是已知的会广泛导致用户自动填充问题的网站。

通常，网站之所以会导致自动填充问题，是因为它们在登录或创建账户表单的代码中偏离了广泛采用的规范。填充辅助功能通过让 Bitwarden 识别行为异常的网站，并为浏览器扩展在这些网站上如何自动填充创建自定义指令，从而解决了这一问题。

## 启用填充辅助 <a href="#turn-on-fill-assist" id="turn-on-fill-assist"></a>

可通过**设置** → **自动填充**菜单为 Bitwarden 浏览器扩展启用填充辅助，适用于 2026.6.0 及以上版本的所有用户。

{% hint style="info" %}
无需任何额外操作！启用后，您将在收录于精选列表的网站上体验到更出色的自动填充性能。本文后续部分将详细说明填充辅助的工作原理。
{% endhint %}

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

填充辅助由 Bitwarden [Map the Web](https://github.com/bitwarden/map-the-web/) 项目提供支持，是专为解决自动填充问题而构建的多种工具之一。它通过用人工编写并审核的指令替代默认的自动填充逻辑，来指导自动填充在其支持的任意网站上应如何运作。我们来详细解析一下：

* **支持的网站**：填充辅助仅在您浏览的网站被收录于 [Map the Web](https://github.com/bitwarden/map-the-web/) 时才会介入；通常，这些网站是广泛被报告会导致 Bitwarden 用户出现自动填充问题的网站。
* **替代默认逻辑**：当在支持的网站上自动填充时，填充辅助会指示浏览器扩展忽略其通常使用的启发式规则，转而采用更具针对性的替代方案。
* **人工编写的指令**：填充辅助使用一份由人工编写和审核的 CSS 选择器映射表，来描述 Bitwarden 应在填充辅助网站上的哪些位置自动填充哪些凭据。

这些映射表可在 [Map the Web](https://github.com/bitwarden/map-the-web/) 项目中找到，浏览器扩展客户端会在每次同步或每 6 小时获取一次，以保持与最新填充辅助指令同步。因此，有两个关键点需要注意：

* **数据隐私**：获取后，浏览器扩展会将该文件本地存储，因此，当自动填充操作使用填充辅助时，**无需也绝不会向 Bitwarden 发送任何数据**。
* **独立于客户端发布**：由于浏览器扩展会定期获取最新的映射，您无需等待客户端发布，新的或更新的指令即可生效。

### 报告问题 <a href="#report-an-issue" id="report-an-issue"></a>

另请注意，由于填充辅助指令针对表单上的特定 CSS 选择器，当网站维护者进行更改时，这些指令可能会失效。我们鼓励所有用户继续[报告自动填充问题](https://docs.google.com/forms/d/e/1FAIpQLSfkxh1w6vK8fLYwAbAAEVhvhMAJwfFNDtYtPUVk1y5WTHvJmQ/viewform)，因为部分报告可能适合更新或添加填充辅助指令。

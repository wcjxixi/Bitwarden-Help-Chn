# 与 Bitwarden 支持排除移动端故障

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/flight-recorder/)
{% endhint %}

在 Bitwarden 移动 App 上，您可以激活**飞行记录器**来捕获额外的日志活动，以便对意外行为进行故障排除。这在您与 Bitwarden 支持合作时尤其有用。

飞行记录器是一个轻量级的临时事件记录器，它捕获最近的 App 活动，例如用户交互和关键系统事件等。这些信息由您控制，它仅存储在您的设备上，如果您愿意，可以将其导出以与 Bitwarden 支持团队分享。飞行记录器**不会**记录敏感信息，例如您的主密码或密码库数据等。

## 使用飞行记录器 <a href="#using-flight-recorder" id="using-flight-recorder"></a>

{% hint style="success" %}
在与 Bitwarden 支持合作时，如果您遇到难以复现的问题，或者遇到了崩溃或意外行为，可能会要求您激活飞行记录器。
{% endhint %}

飞行记录器默认未激活。要激活飞行记录器：

1. 在 Bitwarden 移动 App 中，点击**设置** → **关于**。
2. 向下滚动然后点击**飞行记录器**。
3. 检查您要报告给支持的问题所涉及的任务或工作流程。

{% hint style="info" %}
飞行记录器仅存储一段最近的活动窗口，因此 Bitwarden 建议在激活飞行记录器后立即尝试重现您遇到的问题。
{% endhint %}

飞行记录器捕获到您遇到的问题后：

1. 通过从同一菜单将**飞行记录器**切换为关闭以停止记录。
2. 点击**设置** → **关于** → **查看已记录的日志**以下载您的日志文件。每个日志文件都将对您可用，直到您删除它或自创建之日起 30 天后到期。
3. 在以后与 Bitwarden 支持沟通时，请将日志文件包含在您关于意外 App 行为、问题或潜在错误的讨论主题中。

## 飞行记录器捕获的数据 <a href="#data-captured-by-flight-recorder" id="data-captured-by-flight-recorder"></a>

Bitwarden 优先考虑您的安全。飞行记录器被设计为：

* 日志仅存储在您的设备上，永远不会自动传输。
* 日志只能由您启动、停止或共享。
* 日志不包含敏感的用户数据，如主密码或密码库数据。

飞行记录器被激活期间，可能会捕获以下数据：

| 分类         | 数据                                    |
| ---------- | ------------------------------------- |
| 用户事件       | 屏幕导航和导航时间戳，按键点击和用户交互，进入和退出模态、表单或重叠。   |
| App & 构建信息 | Bitwarden App 版本、构建类型、设备平台、设备型号、OS 版本 |
| 崩溃 & 异常报告  | 异常信息、异常类型、异常特有的元数据、堆栈跟踪               |
| 飞行记录器元数据   | 记录会话开始时间、记录会话持续时间、日志文件大小              |

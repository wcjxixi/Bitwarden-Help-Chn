# 提供商事件日志

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/provider-events/)
{% endhint %}

## 什么是事件日志？ <a href="#what-are-event-logs" id="what-are-event-logs"></a>

事件日志是您的提供商中发生的事件的时间戳记录。提供商的事件日志只能由[提供商管理员](provider-users.md)从提供商门户的**管理**选项卡中访问：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/78qTc5NI4nFDbpxWMDjwJz/b4098e38a47a542e60bbbe573841bfed/provider-events.png?fm=webp&h=440&q=50&w=774" %}
提供商事件日志
{% endembed %}

选择**导出**按钮将创建一个位于指定日期范围内所有事件的 `.csv` 文件：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1BYgVWThvhR5CWpNKBTuOT/a6b7b03285534c47feee2fca4dfb824b/provider-events-export.png?fm=webp&h=214&q=50&w=774" %}
导出事件日志
{% endembed %}

### 事件 <a href="#events" id="events"></a>

事件日志记录了提供商的几种不同类型的事件。事件日志界面捕获事件的**时间戳**、包含应用程序类型和 IP（通过将鼠标悬停在 🌎地球图标上访问）的客户端应用程序信息、连接到事件的**用户**以及**事件**描述。提供商事件包括：

* 已邀请用户的 _user-identifier（用户标识符）_
* 已确认用户的 _user-identifier（用户标识符）_
* 已编辑用户的 _user-identifier（用户标识符）_
* 已移除用户的 _user-identifier（用户标识符）_
* 已访问的组织密码库的 _organization-identifier（组织标识符）_
* 已创建组织的 _organization-identifier（组织标识符）_（[在提供商中创建新组织](start-a-client-organization.md#create-a-client-organization)时触发）
* 已添加组织的 _organization-identifier（组织标识符）_（[将现有组织添加到提供商](providers-faqs.md#q-im-already-providing-bitwarden-as-a-service-for-my-clients-what-do-i-need-to-do-to-move-to-the-provider-portal)时触发）
* 已删除组织的 _organization-identifier（组织标识符）_

{% hint style="success" %}
提供商事件当前不会汇总为每一个[客户组织](provider-portal-overview.md#client-organizations)记录的事件。提供商用户可以从客户组织的密码库访问组织事件日志。[了解更多](../organizations/event-logs.md)。
{% endhint %}

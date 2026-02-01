# Rapid7 SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/rapid7-siem/)
{% endhint %}

Rapid7 是一个安全平台，提供多种分析漏洞和威胁数据的方法，例如安全信息和事件管理 (SIEM)。通过 Rapid7 团队开发的 Rapid7 Bitwarden 集成，企业可以使用 Rapid7 InsightConnect 软件上的 Bitwarden App 监控 Bitwarden 组织和[事件](../event-logging/event-logs.md)活动。

{% hint style="info" %}
InsightConnect 上的 Bitwarden 插件适用于云用户和 Insight Orchestrator 用户。本指南将演示云设置。有关 Insight Orchestrator 的更多信息，请参阅 [Rapid7 文档](https://docs.rapid7.com/insightconnect/orchestrator/)。
{% endhint %}

## 设置 <a href="#setup" id="setup"></a>

### 创建 Rapid7 账户 <a href="#create-rapid7-account" id="create-rapid7-account"></a>

首先，您需要一个能够访问 InsightConnect 的 Rapid7 账户。在 Rapid7 [网站](https://www.rapid7.com/)上创建一个账户。

### 下载 Bitwarden 插件 <a href="#download-the-bitwarden-plugin" id="download-the-bitwarden-plugin"></a>

1、访问 InsightConnect 仪表板。

2、在导航菜单上，选择 **SETTINGS** → **Plugins & Tools**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1dr9pERHfn4fdumb0QbJfy/f2aebdf026bb1d9ab470855980e40388/settings.png?_a=DAJAUVWIZAAB" %}
Rapid7 插件
{% endembed %}

3、在扩展目录中搜索 **Bitwarden** 并安装此插件。

4、返回您的扩展库并选择 Bitwarden 插件，点击 ✚ **Create Connection**。保持此连接窗口打开，需要来自 Bitwarden 网页密码库的信息才能完成下一步。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4iHermwAq1WYzraF6pnoK6/a3a841ef3c806242783236c034a80f25/new_connection.png?_a=DAJAUVWIZAAB" %}
新建 Bitwarden 连接
{% endembed %}

5、在新选项卡或窗口中，访问 Bitwarden 组织的**客户端 ID** 和**客户端密钥。**&#x767B;录 Bitwarden 网页 App 然后使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/919a2c332ed6a53707f80ac3f734e0a8/2024-06-04_10-13-18.png?_a=DAJAUVWIZAAB" %}
产品切换器
{% endembed %}

6、导航到组织的**设置** → **组织信息**界面，然后选择**查看 API 密钥**按钮。系统将要求您重新输入主密码以访问您的 API 密钥信息。

{% embed url="https://bitwarden.com/assets/6gHjAyqgeqDj6UPT6agsBK/3a614e043cb3836a41bd68f226835e53/2024-12-04_09-51-07.png?w=1175&fm=avif" %}
组织 API 信息
{% endembed %}

7、复制 `client_id` 和 `client_secret` 值。返回创建云连接窗口：

1. 将 `client_id` 值粘贴到 **Client ID** 字段中。
2. 将 `client_secret` 值粘贴到 **Client Secret** 字段中。要访问此字段，请从 **Select Credential** 下拉菜单中选择 **Add Credential**。将 `client_secret` 值粘贴到 **Client Secret** 字段中。填写您希望包含在连接中的任何其他名称和描述值。

8、输入这些值后，选择 **Save & Test Connection**。Rapid7 将运行连接测试并指示设置是否成功。

{% hint style="info" %}
您的组织 API 密钥信息属于敏感数据。请勿在非安全位置共享这些值。
{% endhint %}

## 创建工作流 <a href="#create-a-workflow" id="create-a-workflow"></a>

要开始使用 Rapid7 监控数据，请创建 InsightConnect 工作流。本指南将演示创建云工作流，然后测试该工作流。

1、在主导航上，选择 **WORKFLOWS**。

2、在此界面右上角，选择 **Add Workflow** 开始。

3、将出现一个窗口，显示用于创建工作流的不同选项。对于本示例，选择 **Start From Scratch**。高级用户可以选择浏览现有模板。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5jTVduSflnf6c5aHYGbv0h/fd139b270cf7e8af6bdf97ce477fdf96/2024-08-20_11-08-03.png?_a=DAJAUVWIZAAB" %}
添加工作流
{% endembed %}

4、在「创建新工作流」窗口中，填写以下必填字段：

1. **Workflow Name：**&#x4E3A;工作流创建一个名称，例如 **Bitwarden Logs** 。
2. **Time Savings：**&#x6B64;工作流将节省的时间。
3. **Optional：**&#x6839;据需要包括工作流程的摘要和标签。

5、完成后选择 **Create**。

### 创建工作流触发器 <a href="#create-workflow-trigger" id="create-workflow-trigger"></a>

1、单击工作流编辑器中的新触发器。在选择触发器窗口中，选择您想要用于启动工作流的触发器，例如 **API Trigger**。填写以下必填字段：

1. **Name：**&#x4E3A;新触发器提供一个名称。
2. **Variable：**&#x9009;择变量，例如 `Event` 。
3. **Data Type:：**&#x9009;择 **String**。
4. **Optional：**&#x8F93;入触发器描述以记录有关触发器的使用情况。

2、完成设置后选择 **Close**。

### 添加工作流步骤 <a href="#add-a-workflow-step" id="add-a-workflow-step"></a>

1、在工作流编辑器上，选择 ✚加号图标以添加新步骤。

{% embed url="https://bitwarden.com/assets/6B6GApClPXwr3yypKZJ5N0/38a6edc616bd3f23e3ee07ef4f9dfaeb/2024-08-20_12-26-54.png?w=262&fm=avif" %}

2、选择 ✚**Action** 以添加新操作。从插件列表中选择 **Bitwarden** 。

3、在选择操作界面，选择要监控的操作。对于此示例，我们将选择 **List Events** 。做出选择后，选择 **Continue**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/jYba6MvQBxtEd81fzUlca/521681306f9cf8d174487589b683ca7c/2024-08-20_12-32-15.png?_a=DAJAUVWIZAAB" %}
List Events 操作
{% endembed %}

4、选择要运行的 **Cloud** 选项。在连接下拉列表中，选择我们之前在指南中建立的 Bitwarden 连接。完成后选择 **Continue**。

5、在配置详情界面上，根据您的设置要求填写可选字段，例如 **Start Date**。

6、自定义步骤详情后，选择 **Save Step**。

{% hint style="info" %}
Rapid7 允许创建多个操作并将其链接在一起。您可以通过其他 Bitwarden 操作重复此步骤以报告更多信息。[在此处](https://extensions.rapid7.com/extension/bitwarden)查看 Bitwarden 集成操作的完整列表。
{% endhint %}

### 测试工作流 <a href="#test-workflow" id="test-workflow"></a>

1、返回工作流编辑器然后选择 **Test** 以尝试工作流。将出现「测试工作流」窗口。选择窗口底部的 **Test Workflow** 来运行该流程。

2、这可能需要一些时间。完成后，将出现「作业详细信息」窗口，其中包含工作流的结果：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1jgRIiIjIjnPRqn82afwSt/300c593b6221f854deff10f7c85b27d2/Events.png?_a=DAJAUVWIZAAB" %}
Rapid7 事件输出
{% endembed %}

### 启用工作流 <a href="#enable-workflow" id="enable-workflow"></a>

1、要启用工作流，请从主导航中选择 **WORKFLOWS**。

2、使用切换选项激活工作流：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6u6JvyiCi3RMkBKgYovZxO/18b513d4e19eefa54045a3ba6ac83a7f/2024-08-20_12-53-54.png?_a=DAJAUVWIZAAB" %}
启用工作流
{% endembed %}

3、激活后，将根据工作流中建立的触发器设置生成报告。通过选择导航上的**作业**来查看这些报告。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/74bmUmBX6LQlNTDeHDYgkm/f10055bdb9c2c791e8c75b9b996ecb84/2024-08-29_11-04-36.png?_a=DAJAUVWIZAAB" %}
查看 Rapid7 作业
{% endembed %}

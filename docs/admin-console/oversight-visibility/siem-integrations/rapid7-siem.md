# Rapid7 SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/rapid7-siem/)
{% endhint %}

Rapid7 是一个安全平台，提供多种分析漏洞和威胁数据的方法，例如安全信息与事件管理 (SIEM)。通过 Rapid7 团队开发的 Rapid7 Bitwarden 集成，组织可以使用 Rapid7 InsightConnect 软件上的 Bitwarden App 来监控 Bitwarden 组织和[事件](../event-logging/event-logs.md)活动。

{% hint style="info" %}
InsightConnect 上的 Bitwarden 插件适用于云端用户和 Insight Orchestrator 用户。本指南将演示云端设置。有关 Insight Orchestrator 的更多信息，请参阅 [Rapid7 文档](https://docs.rapid7.com/insightconnect/orchestrator/)。
{% endhint %}

## 设置 <a href="#setup" id="setup"></a>

### 创建 Rapid7 账户 <a href="#create-rapid7-account" id="create-rapid7-account"></a>

首先，您需要拥有一个能够访问 InsightConnect 的 Rapid7 账户。在 Rapid7 [网站](https://www.rapid7.com/)上创建一个账户。

### 下载 Bitwarden 插件 <a href="#download-the-bitwarden-plugin" id="download-the-bitwarden-plugin"></a>

1、访问 InsightConnect 仪表板。

2、在导航菜单上，选择 **SETTINGS** → **Plugins & Tools**。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1dr9pERHfn4fdumb0QbJfy/f2aebdf026bb1d9ab470855980e40388/settings.png?w=428&#x26;fm=avif" alt=""><figcaption><p>Rapid7 插件</p></figcaption></figure></div>

3、在扩展目录中搜索 **Bitwarden** 并安装此插件。

4、返回您的扩展库，选择 Bitwarden 插件，然后点击 ✚ **Create Connection**。保持此连接窗口打开，需要来自 Bitwarden 网页密码库的信息才能完成下一步。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4iHermwAq1WYzraF6pnoK6/a3a841ef3c806242783236c034a80f25/new_connection.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>新建 Bitwarden 连接</p></figcaption></figure></div>

5、在新标签页或窗口中，获取 您的 Bitwarden 组织的**客户端 ID** 和**客户端密钥。**&#x767B;录 Bitwarden 网页 App ，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

6、导航到组织的**设置** → **组织信息**界面，然后选择**查看 API 密钥**按钮。将要求您重新输入主密码，以访问您的 API 密钥信息。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6gHjAyqgeqDj6UPT6agsBK/3a614e043cb3836a41bd68f226835e53/2024-12-04_09-51-07.png?w=1175&#x26;fm=avif" alt=""><figcaption><p>组织 API 信息</p></figcaption></figure></div>

7、复制 `client_id` 和 `client_secret` 值。返回创建云连接的窗口：

1. 将 `client_id` 值粘贴到 **Client ID** 字段中。
2. 将 `client_secret` 值粘贴到 **Client Secret** 字段中。要访问此字段，请从 **Select Credential** 下拉菜单中选择 **Add Credential**。将 `client_secret` 值粘贴到 **Client Secret** 字段中。填写您希望在连接中包含的任何其他名称和描述值。

8、输入这些值后，选择 **Save & Test Connection**。Rapid7 将运行连接测试并指示设置是否成功。

{% hint style="info" %}
您的组织 API 密钥信息是敏感数据。不要在不安全的位置分享这些值。
{% endhint %}

## 创建工作流 <a href="#create-a-workflow" id="create-a-workflow"></a>

要开始使用 Rapid7 监控数据，请创建一个 InsightConnect 工作流。本指南将演示创建云工作流，然后测试该工作流。

1、在主导航上，选择 **WORKFLOWS**。

2、在此界面右上角，选择 **Add Workflow** 以开始。

3、将出现一个窗口，显示用于创建工作流的不同选项。对于本示例，选择 **Start From Scratch**。高级用户可以选择浏览现有模板。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5jTVduSflnf6c5aHYGbv0h/fd139b270cf7e8af6bdf97ce477fdf96/2024-08-20_11-08-03.png?w=733&#x26;fm=avif" alt=""><figcaption><p>添加工作流</p></figcaption></figure></div>

4、在「创建新工作流」窗口中，填写以下必填字段：

1. **Workflow Name**：为工作流创建一个名称，例如 **Bitwarden Logs** 。
2. **Time Savings**：此工作流将节省的时间。
3. **Optional**：根据需要为工作流添加摘要和标签。

5、完成后选择 **Create**。

### 创建工作流触发器 <a href="#create-workflow-trigger" id="create-workflow-trigger"></a>

1、单击工作流编辑器中的新触发器。在「选择触发器」窗口中，选择您想要用于启动工作流的触发器，例如 **API Trigger**。填写以下必填字段：

1. **Name**：为新触发器提供一个名称。
2. **Variable**：选择变量，例如 `Event` 。
3. **Data Type**：选择 **String**。
4. **Optional：**&#x8F93;入触发器描述以记录有关触发器的使用情况。

2、完成设置后选择 **Close**。

### 添加工作流步骤 <a href="#add-a-workflow-step" id="add-a-workflow-step"></a>

1、在工作流编辑器上，选择 ✚加号图标以添加新步骤。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6B6GApClPXwr3yypKZJ5N0/38a6edc616bd3f23e3ee07ef4f9dfaeb/2024-08-20_12-26-54.png?w=262&#x26;fm=avif" alt=""><figcaption><p>添加步骤</p></figcaption></figure></div>

2、选择 ✚**Action** 以添加新操作。从插件列表中选择 **Bitwarden** 。

3、在选择操作界面，选择要监控的操作。对于此示例，我们将选择 **List Events** 。完成选择后，选择 **Continue**。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/jYba6MvQBxtEd81fzUlca/521681306f9cf8d174487589b683ca7c/2024-08-20_12-32-15.png?w=499&#x26;fm=avif" alt=""><figcaption><p>列出事件操作</p></figcaption></figure></div>

4、选择要运行的 **Cloud** 选项。在连接下拉菜单中，选择我们在指南中先前建立的 Bitwarden 连接。完成后选择 **Continue**。

5、在「配置详细信息」界面上，根据您的设置要求填写可选字段，例如 **Start Date**。

6、自定义步骤详细信息后，选择 **Save Step**。

{% hint style="info" %}
Rapid7 允许创建多个操作并将其链接在一起。您可以通过其他 Bitwarden 操作重复此步骤以报告更多信息。[在此处](https://extensions.rapid7.com/extension/bitwarden)查看 Bitwarden 集成操作的完整列表。
{% endhint %}

### 测试工作流 <a href="#test-workflow" id="test-workflow"></a>

1、返回工作流编辑器，然后选择 **Test** 以尝试运行工作流。将出现「测试工作流」窗口。选择窗口底部的 **Test Workflow** 来运行该流程。

2、这可能需要一些时间。完成后，将出现「作业详细信息」窗口，其中包含工作流的结果：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1jgRIiIjIjnPRqn82afwSt/300c593b6221f854deff10f7c85b27d2/Events.png?w=842&#x26;fm=avif" alt=""><figcaption><p>Rapid7 事件输出</p></figcaption></figure></div>

### 启用工作流 <a href="#enable-workflow" id="enable-workflow"></a>

1、要启用工作流，请从主导航中选择 **WORKFLOWS**。

2、使用切换选项激活工作流：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6u6JvyiCi3RMkBKgYovZxO/18b513d4e19eefa54045a3ba6ac83a7f/2024-08-20_12-53-54.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>启用工作流</p></figcaption></figure></div>

3、激活后，将根据工作流中建立的触发器设置生成报告。通过选择导航上的**作业**来查看这些报告。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/74bmUmBX6LQlNTDeHDYgkm/f10055bdb9c2c791e8c75b9b996ecb84/2024-08-29_11-04-36.png?w=1268&#x26;fm=avif" alt=""><figcaption><p>查看 Rapid7 作业</p></figcaption></figure></div>

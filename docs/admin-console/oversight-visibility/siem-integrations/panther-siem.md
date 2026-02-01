# Panther SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/panther-siem/)
{% endhint %}

Panther 是一个安全信息和事件管理 (SIEM) 平台，可与 Bitwarden 组织一起使用。组织用户可以使用 Panther 监控系统上的 Bitwarden App 监控[事件](../event-logging/event-logs.md)活动。

## 设置 <a href="#setup" id="setup"></a>

### 创建一个 Panther 账户 <a href="#create-a-panther-account" id="create-a-panther-account"></a>

首先，您需要一个 Panther 账户和仪表板。在他们的[网站](https://panther.com/)上创建一个 Panther 账户。

### 初始化 Panther Bitwarden 日志源 <a href="#initialize-panther-bitwarden-log-source" id="initialize-panther-bitwarden-log-source"></a>

1、访问 Panther 仪表板。

2、在菜单上，打开 **Configure** 下拉列表然后选择 **Log Sources**。

{% embed url="https://bitwarden.com/assets/2ZE57tHcy87V0qBKbUykRO/c0bf68f1da74c896562f87a85950138c/Panther_Log_sources.png?w=289&fm=avif" %}
Panther 日志源
{% endembed %}

3、选择 **Onboard your logs**。

{% embed url="https://bitwarden.com/assets/4mefTa7wGIZ6Kc62Mf9oNu/ab043ca54203609664765bcc0132158d/Panther_integration_marketplace.png?w=1028&fm=avif" %}

4、在目录中搜索 **Bitwarden**。

{% embed url="https://bitwarden.com/assets/3sSNvUFqgN8dwEWrfe0UFM/f9c1473e113c9851c506720992dfef2a/bitwarden_app.png?w=1167&fm=avif" %}
Bitwarden 日志集成
{% endembed %}

5、单击 **Bitwarden** 集成然后选择 **Start Setup**。

### 连接您的 Bitwarden 组织 <a href="#connect-your-bitwarden-organization" id="connect-your-bitwarden-organization"></a>

选择 **Start Setup** 后，您将被引导至配置界面。

{% hint style="info" %}
Panther SIEM 服务仅适用于 Bitwarden 云托管组织。
{% endhint %}

1、输入集成的名称，然后选择 **Setup**。

2、接下来，您必须访问您的 Bitwarden 组织的**客户端 ID** 和**客户端密钥**。保持此界面打开，在另一个选项卡上，登录 Bitwarden 网页 App 然后使用产品切换器打开管理控制台：

{% embed url="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&fm=avif" %}
产品切换器
{% endembed %}

3、导航到组织的**设置** → **组织信息**界面，然后选择**查看 API 密钥**按钮。将要求您重新输入主密码，以访问 API 密钥信息。

{% embed url="https://bitwarden.com/assets/6gHjAyqgeqDj6UPT6agsBK/3a614e043cb3836a41bd68f226835e53/2024-12-04_09-51-07.png?w=1175&fm=avif" %}
组织 API 信息
{% endembed %}

4、将 `client_id` 和 `client_secret` 值复制并粘贴到 Bitwarden 应用程序设置页面上各自的位置。输入信息后，再次选择 **Setup** 以继续。

5、Panther 将对集成进行测试。成功完成测试后，您将可以选择调整偏好。按下 **View Log Source** 完成设置。

{% hint style="info" %}
在 Bitwarden 应用程序设置完成后，Panther 可能需要长达 10 分钟的时间来提取数据。
{% endhint %}

### 开始监控数据 <a href="#start-monitoring-data" id="start-monitoring-data"></a>

1、要开始监控数据，请转到主仪表板然后选择 **🔍Investigate** 和 **Data Explorer**。

2、在 **Data Explorer**（数据资源管理器）页面上，从下拉菜单中选择 `panther_logs.public` 数据库。确保 `bitwarden_events` 也可见。

{% embed url="https://bitwarden.com/assets/3mrpsXxhYXiPHr5bAt2Dfk/9316f68edd7191180174869d37264752/data_explorer.png?w=1200&fm=avif" %}
Panther Data Explorer
{% endembed %}

3、完成所有必需的选择后，选择 **Run Query**。

您也可以 **Save as** 以便下次使用此查询。

4、屏幕底部将生成 Bitwarden 事件列表。

{% embed url="https://bitwarden.com/assets/3iyy9chBYenrpJ5hCwVKOd/385e7d5348621b7c58649f0632f198b2/Panther_event_logs.png?w=1200&fm=avif" %}
Panther  事件日志
{% endembed %}

5、通过选择 **View JSON**，可以以 JSON 格式展开和查看事件。

{% embed url="https://bitwarden.com/assets/1wHDe1snFJ4NB1G13VBUBC/71def83a275e8bf25e25488b872a02f0/Header_object.png?w=700&fm=avif" %}
Panther JSON 对象
{% endembed %}

有关 Bitwarden 组织活动的更多信息，请参阅[此处](../event-logging/event-logs.md#organization-events)。有关针对特定查询的其他选项，请参阅 [Panther Data Explorer](https://docs.panther.com/search/data-explorer) 文档以获取更多信息。

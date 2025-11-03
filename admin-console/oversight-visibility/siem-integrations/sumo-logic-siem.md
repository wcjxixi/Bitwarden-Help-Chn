# Sumo Logic SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/sumo-logic-siem/)
{% endhint %}

Sumo Logic 是一个能够提供您的 Bitwarden 组织用户和密码库活动可视化的解决方案。Sumo Logic Bitwarden 集成允许用户监控重要的组织活动，例如登录、失败的两步验证、主密码重置以及解密密钥迁移等。

## 设置 <a href="#setup" id="setup"></a>

### 创建 Sumo Logic 账户 <a href="#create-a-sumo-logic-account" id="create-a-sumo-logic-account"></a>

首先，[创建 Sumo Logic 账户](https://www.sumologic.com/)，或登录具有创建和管理应用程序权限的现有 Sump Logic 账户。

### 下载 Bitwarden App <a href="#download-the-bitwarden-app" id="download-the-bitwarden-app"></a>

1、从 Sumo Logic 仪表盘，导航至 **App Catalog** 然后搜索 Bitwarden。选择 **Install App**。

{% embed url="https://bitwarden.com/assets/4leelRzp6369eVXg5By339/98cf6c075ba033e16db9643fbd56752d/install_app.png?w=1200&fm=avif" %}
安装 Bitwarden App
{% endembed %}

2、接下来，在 **Set Up Collection** 界面上选择 **Create a new Collector**。

{% embed url="https://bitwarden.com/assets/1TAkWsPHx42qxhZsvZ22B5/c7e9172538573359379e20242b0245cb/Create_a_collector.png?w=1200&fm=avif" %}
创建收集器
{% endembed %}

3、输入 **Collector Name**、**Timezone**和可选的 **Metadata**。完成后，选择 **Next**。

4、在 **Configure Source** 界面上，提供应用程序的 **Name**，例如 Bitwarden Event Logs。

{% embed url="https://bitwarden.com/assets/vxxfTbKUTU3RMYeEp1alQ/254010cbb93438d191f53f3d9374db5e/configure_application_connection.png?w=1200&fm=avif" %}
配置应用程序连接
{% endembed %}

5、保持此界面打开，然后在新选项卡中打开 Bitwarden 组织的网页密码库。

### 连接您的 Bitwarden 组织 <a href="#connect-your-bitwarden-organization" id="connect-your-bitwarden-organization"></a>

此时，您需要返回 Bitwarden 网页密码库以获取 **Client ID** 和 **Client Secret** 的值。

1、要访问 Bitwarden 组织的 `client_id` 和 `client_secret`，请登录 Bitwarden 网页 App 然后使用产品切换器打开管理控制台：

{% embed url="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&fm=avif" %}
产品切换器
{% endembed %}

2、导航到您组织的**设置** → **组织信息**界面，然后选择**查看 API 密钥**按钮。您将被要求重新输入主密码以访问您的 API 密钥信息。

{% embed url="https://bitwarden.com/assets/6gHjAyqgeqDj6UPT6agsBK/3a614e043cb3836a41bd68f226835e53/2024-12-04_09-51-07.png?w=1175&fm=avif" %}
组织 API 信息
{% endembed %}

3、将 `client_id` 和 `client_secret` 的值复制然后粘贴到 Sumo Logic 的 **Configure Source** 界面上对应的位置。

4、完成后，选择 **Next**。

## 为 Bitwarden App 创建监控器 <a href="#create-a-monitor-for-bitwarden-app" id="create-a-monitor-for-bitwarden-app"></a>

Sumo Logic Bitwarden App 包含预配置的监控器，可主动检测数据导出、账户盗用以及策略违规等威胁。监控器提供自动化警报机制，在满足条件时将通知您。

1、返回 **App Catalog**，搜索然后选择 Bitwarden App。

2、若 App 已安装，请导航至 **What's Included** 选项卡。

{% embed url="https://bitwarden.com/assets/5nV8JAS5NiEVMtKxfx1T3Y/051a93edcc7b722fa052d5b31bc9cdcc/create_monitors.png?w=1200&fm=avif" %}
创建监控器
{% endembed %}

3、在 **Monitors** 部分中，为您要使用的预配置的监控器选择 **Create**。Sumo Logic 提供了三个预配置的监控器：

* 来自受限制的地理位置的事件
* 导出了组织密码库
* 组织禁用了 SSO

4、在 New Monitor 设置界面，设置所需监视器的 **Trigger Conditions**、**Alert Grouping** 和 **Trigger Types**。

{% embed url="https://bitwarden.com/assets/3llf1rkTKRkY4zE2Gl34ry/8d2d7684a904f68189af1a6b0a6b6e5f/setup_monitor.png?w=1022&fm=avif" %}
设置监控器
{% endembed %}

5、配置监控器后，选择 **Save**。

### 开始监控数据 <a href="#start-monitoring-data" id="start-monitoring-data"></a>

完成 App 设置后，您可打开 Sumo Logic 仪表盘然后开始监控数据。在 Sumo Logic 中选择 **Dashboards**，然后打开 **Bitwarden - Security** 仪表盘。该安全仪表盘可直观展示从 Bitwarden 事件日志中收集的数据。Bitwarden 事件日志的完整列表可在[此处](../event-logging/event-logs.md)查阅。

{% embed url="https://bitwarden.com/assets/7a6Ycqv8GmyvGo5rvJCcdZ/6de5baa070fa2879ba22f9434b7da403/2025-10-17_12-01-21.png?w=1200&fm=avif" %}
Sumo Logic Bitwarden 仪表盘
{% endembed %}

### 时间范围 <a href="#timeframe" id="timeframe"></a>

您可以使用位于仪表盘右上角的工具栏筛选仪表盘结果。选择 **🕘**以按时间范围进行筛选：

{% embed url="https://bitwarden.com/assets/4fytpjiAfdudPjMGlKPB6o/3a42bf4bb20a5a435b49e177142ca910/2025-10-22_11-17-47.png?w=1200&fm=avif" %}

### 示例查询 <a href="#sample-query" id="sample-query"></a>

您可以在 Sumo Logic 仪表盘上查询 Bitwarden 事件日志。Bitwarden 事件以 JSON 格式传输。示例事件查询如下所示：

{% embed url="https://bitwarden.com/assets/5FwpAond1iIaPuSdcJdZ0e/279796d62964ec284b81a5a1e59e6ba6/sample_query.png?w=1200&fm=avif" %}
Sumo Logic 简单查询
{% endembed %}

示例查询结构：

```
_sourceCategory=source-category-1 
| json "actingUserName", "date", "object", "type", "typeName", "ipAddress","deviceName","actingUserEmail" as user_name, date, object, event_code, event_name, ip, device_name, user_email
| lookup event_name from source on event_code=event_code
| lookup latitude, longitude,country_name, country_code from geo://location on ip = ip
```

要了解更多有关 Sumo Logic 高级查询的信息，请参阅 [Sumo Logic Query Language documentation](https://www.sumologic.com/help/docs/search/search-query-language/)。

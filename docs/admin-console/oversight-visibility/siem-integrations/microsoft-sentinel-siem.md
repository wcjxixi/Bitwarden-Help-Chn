# Microsoft Sentinel SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/microsoft-sentinel-siem/)
{% endhint %}

Microsoft Sentinel 是一个安全信息和事件管理 (SIEM) 平台，可用于监控 Bitwarden 组织。企业可使用 Microsoft Sentinel 上的 Bitwarden Event Logs App 监控[事件](../event-logging/event-logs.md)活动。

## 设置 <a href="#setup" id="setup"></a>

要设置 Bitwarden 集成，需要一个可访问 Microsoft Sentinel 工作区的活动 Azure 账户。此外，还需要 Bitwarden [API 密钥](../../bitwarden-public-api.md#authentication)，该密钥只能由[组织所有者](../../manage-members/member-roles.md)获取。

## 将 Bitwarden App 安装到您的 Microsoft Sentinel 仪表盘 <a href="#install-the-bitwarden-app-to-your-microsoft-sentinel-dashboard" id="install-the-bitwarden-app-to-your-microsoft-sentinel-dashboard"></a>

Bitwarden Event Logs App 位于 [Microsoft Azure Marketplace](https://azuremarketplace.microsoft.com/zh-cn/marketplace/apps/8bit-solutions-llc.bitwarden-sentinel-integration?tab=Overview)。要将新的应用程序添加到您的工作区，请执行以下操作：

1、从下拉菜单中选择 Bitwarden Event Logs 计划，然后选择**创建**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7mrbZU5XylvwS9muqfXOM7/5f1216a644693655e970e66deb7dfbc2/2024-10-08_16-20-06.png?_a=DAJCwlWIZAAB" %}
Bitwarden 事件日志市场 App
{% endembed %}

2、填写必填字段，然后选择工作区，这将将监控 Bitwarden 组织数据。

3、完成后，选择**审核 + 创建**。

## 连接您的 Bitwarden 组织 <a href="#connect-your-bitwarden-organization" id="connect-your-bitwarden-organization"></a>

将 Bitwarden Event Logs App 添加到 Microsoft Sentinel 工作区后，您就可以使用 Bitwarden API 密钥连接您的 Bitwarden 组织了。

1、返回**数据连接器**界面然后选择 Bitwarden Event Logs App。选择**打开连接器页面**。如果 Bitwarden Event Logs App 不可见，您可能需要选择 **⟳刷新**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7CoeRtrpz1i7JbbF6Tm91e/a6e46ad19099681aa4b93cfc6fb9ed69/2024-10-08_12-45-04.png?_a=DAJCwlWIZAAB" %}
Microsoft Sentinel Bitwarden 事件日志 App
{% endembed %}

2、保持该界面打开，在另一个标签页上登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

3、导航到组织的**设置** → **组织信息**界面，然后选择**查看 API 密钥**按钮。系统会要求您重新输入主密码，以访问 API 密钥信息。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6gHjAyqgeqDj6UPT6agsBK/3a614e043cb3836a41bd68f226835e53/2024-12-04_09-51-07.png?_a=DAJCwlWIZAAB" %}
组织 API 信息
{% endembed %}

4、返回 Microsoft Sentinel 选项卡。在配**置**页面上，填写以下字段：

| 字段                     | 值                                                                                                                                                                                                                                                               |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bitwarden Identity URL | <p>对于 Bitwarden 云用户，默认的 URL 为 <code>https://identity.bitwarden.com</code> 或 <code>https://identity.bitwarden.eu</code>。</p><p>对于自托管 Bitwarden 用户，请输入您的自托管 URL。例如 <code>https://&#x3C;self-hosted-url>/identity</code>。确保 URL 尾部不包含任何尾随的正斜杠「<code>/</code>」。</p> |
| Bitwarden API URL      | <p>对于 Bitwarden 云用户，默认的 URL 为 <code>https://api.bitwarden.com</code> or <code>https://api.bitwarden.eu</code>。</p><p>对于自托管 Bitwarden 用户，请输入您的自托管 URL。例如 <code>https://&#x3C;self-hosted-url>/api</code>。确保 URL 尾部不包含任何尾随的正斜杠「<code>/</code>」。</p>               |
| Client ID              | 输入从 Bitwarden 组织 API 密钥窗口获取的 `client_id` 的值。                                                                                                                                                                                                                    |
| Client Secret          | 输入从 Bitwarden 组织 API 密钥窗口获取的  `client_secret` 的值。                                                                                                                                                                                                               |

5、完成必填字段后，选择**连接**。

{% hint style="info" %}
您的组织 API 密钥信息属于敏感数据。请勿在非安全位置共享这些值。
{% endhint %}

## 开始监控事件日志 <a href="#start-monitoring-event-logs" id="start-monitoring-event-logs"></a>

{% hint style="info" %}
Microsoft Sentinel 上的 Bitwarden Event Logs App 目前不提供历史事件数据。此外，在 Microsoft Sentinel 中显示第一批事件可能需要长达 1 个小时。
{% endhint %}

可使用 `BitwardenEventLogs` 查询功能在 Microsoft Sentinel 中查看 Bitwarden 组织事件日志。

1、从 Microsoft Sentinel 选择**日志**。将创建新查询选项卡。在左侧导航栏中，选择**功能** → **工作区功能** → **BitwardenEventLogs**。

2、在运行查询之前，可以选择时间范围并为查询添加特定参数。要执行查询，请选择**运行**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/38MLy3Ieg9nf3YH4s50R1K/d4b9f6df7e1e5e42bbe84a2bbaf5afa5/image_480-1.png?_a=DAJCwlWIZAAB" %}
Microsoft Sentinel 查询
{% endembed %}

可以保存查询，以备将来使用。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/B1P94UrwYOysKWh28oHJp/f6ab59d7f240b0519922fba9d0723598/image__1_.png?_a=DAJCwlWIZAAB" %}
Microsoft Sentinel 查询结果
{% endembed %}

### 使用 Workbook 监控 <a href="#monitor-using-workbooks" id="monitor-using-workbooks"></a>

Workbook 可用于查看事件日志和可视化数据。此外，Bitwarden 事件日志 Workbook 中还包含模板，用于预配置可用数据概览。

要访问 Workbook，请从导航中选择 **Workbook**，然后选择**模板**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4eh5nlRZ1TCptqg8Q8Yz3T/55e09959de52e396a69f17f5509fdccd/workbooks.png?_a=DAJCwlWIZAAB" %}
Workbook 模板
{% endembed %}

Bitwarden Event Logs App 默认包含三个模板。选择其中一个模板并选择**查看模板**即可开始监控数据：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2UfrEiMzlyVJcJ7P9Exaub/9e0664475aa6b357b5a3710e6ac268b8/included_templates.png?_a=DAJCwlWIZAAB" %}
包含的模板
{% endembed %}

仪表盘包括可视化数据：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3Wf1N2jRun1kROxJnjGrMy/ebe3cb8fddff817e8a00b1f2666a3f0e/BitwardenEventLogsAuthenticationWhite1.png?_a=DAJCwlWIZAAB" %}
Microsoft Sentinel 仪表盘视图
{% endembed %}

继续滚动概览页面，查看更多事件日志数据：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6wGNTITmTwvrzJXIJSZxJA/500b34ddb453cb63036a995e3c3db5d0/BitwardenEventLogsAuthenticationWhite2.png?_a=DAJCwlWIZAAB" %}
Bitwarden 事件日志视图
{% endembed %}

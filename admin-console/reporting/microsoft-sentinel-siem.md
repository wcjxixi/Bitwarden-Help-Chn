# =Microsoft Sentinel SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/microsoft-sentinel-siem/)
{% endhint %}

Microsoft Sentinel 是一个安全信息和事件管理 (SIEM) 平台，可用于监控 Bitwarden 组织。企业可使用 Microsoft Sentinel 上的 Bitwarden Event Logs App 监控事件活动。

## 设置 <a href="#setup" id="setup"></a>

要设置 Bitwarden 集成，需要一个可访问 Microsoft Sentinel 工作区的活动 Azure 账户。此外，还需要 Bitwarden API 密钥，该密钥只能由组织所有者获取。

## 将 Bitwarden App 安装到您的 Microsoft Sentinel 仪表盘 <a href="#install-the-bitwarden-app-to-your-microsoft-sentinel-dashboard" id="install-the-bitwarden-app-to-your-microsoft-sentinel-dashboard"></a>

Bitwarden Event Logs App位 pA于 Microsoft Azure Marketplace。要将新应用程序添加到工作区，请执行以下操作

1、从下拉菜单中选择 Bitwarden Event Logs 计划，然后选择创建。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7mrbZU5XylvwS9muqfXOM7/5f1216a644693655e970e66deb7dfbc2/2024-10-08_16-20-06.png?_a=DAJCwlWIZAAB" %}
Bitwarden 事件日志市场 App
{% endembed %}

2、填写必填字段，并选择将监控 Bitwarden 组织数据的工作区。

3、完成后，选择 "审核+创建"。

## 连接您的 Bitwarden 组织 <a href="#connect-your-bitwarden-organization" id="connect-your-bitwarden-organization"></a>

将 Bitwarden Event Logs 应用程序添加到 Microsoft Sentinel 工作区后，您就可以使用 Bitwarden API 密钥连接您的 Bitwarden 组织了。

1、返回数据连接器屏幕并选择 Bitwarden Event Logs 应用程序。 选择打开连接器页面。 如果 Bitwarden Event Logs 应用程序不可见，您可能需要选择  Refresh。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7CoeRtrpz1i7JbbF6Tm91e/a6e46ad19099681aa4b93cfc6fb9ed69/2024-10-08_12-45-04.png?_a=DAJCwlWIZAAB" %}
Microsoft Sentinel Bitwarden 事件日志 App
{% endembed %}

2、保持该界面打开，在另一个标签页上登录 Bitwarden Web 应用程序，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

3、导航到组织的 "设置"→"组织信息 "屏幕，然后选择 "查看 API 密钥 "按钮。系统会要求您重新输入主密码，以访问 API 密钥信息。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6gHjAyqgeqDj6UPT6agsBK/3a614e043cb3836a41bd68f226835e53/2024-12-04_09-51-07.png?_a=DAJCwlWIZAAB" %}
组织 api 信息
{% endembed %}

4、返回 Microsoft Sentinel 选项卡。在 "配置 "页面上，填写以下字段：

| 字段                     | 值                                                                                                                                                                                                                                                                                                                                                                                                     |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bitwarden Identity URL | <p>For Bitwarden cloud users, the default URL will be <code>https://identity.bitwarden.com</code> or <code>https://identity.bitwarden.eu</code>.</p><p>For self-hosted Bitwarden users, input your self-hosted URL. For example, <code>https://&#x3C;self-hosted-url>/identity</code>. Be sure that the URL does not include any trailing forward slashes at the end of the URL "<code>/</code>".</p> |
| Bitwarden API URL      | <p>For Bitwarden cloud users, the default URL will be <code>https://api.bitwarden.com</code> or <code>https://api.bitwarden.eu</code>.</p><p>For self-hosted Bitwarden users, input your self-hosted URL. For example, <code>https://&#x3C;self-hosted-url>/api</code>. Be sure that the URL does not include any trailing forward slashes at the end of the URL "<code>/</code>".</p>                |
| Client ID              | Input the value for `client_id` from the Bitwarden organization API key window.                                                                                                                                                                                                                                                                                                                       |
| Client Secret          | Input the value for `client_secret` from the Bitwarden organization API key window.                                                                                                                                                                                                                                                                                                                   |

5、完成必填字段后，选择 "连接"。

{% hint style="info" %}
您的组织 API 密钥信息属于敏感数据。 请勿在非安全位置共享这些值。
{% endhint %}

## 开始监控事件日志 <a href="#start-monitoring-event-logs" id="start-monitoring-event-logs"></a>

### 使用工作簿监控 <a href="#monitor-using-workbooks" id="monitor-using-workbooks"></a>

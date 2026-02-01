# Elastic SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/elastic-siem/)
{% endhint %}

Elastic 是一种可提供搜索和可观察性选项的解决方案，用于监控您的 Bitwarden 组织。通过与 Elastic Bitwarden 的集成，Elastic Agent 提供了监控 `collection`、`event`、`group` 和 `policy` 信息的功能。

## 设置 <a href="#setup" id="setup"></a>

### 创建 Elastic 账户 <a href="#create-a-elastic-account" id="create-a-elastic-account"></a>

首先，[创建一个 Elastic 账户](https://www.elastic.co/)。要通过 Elastic 的云托管服务（推荐）或内部部署服务设置仪表板以监控数据，需要执行此步骤。

### 添加 Bitwarden 集成 <a href="#add-bitwarden-integration" id="add-bitwarden-integration"></a>

监控数据需要使用 Elastic Search 和 Kibana 来可视化数据。

1、在 Elastic 主界面上，向下滚动然后找到 **Add Integrations**。

{% embed url="https://bitwarden.com/assets/3Ka8ZepztzAq9YiGJO7pSM/879c6c6719eac019f4eb53f5383b3e92/2023-09-08_10-15-52.png?w=1200&fm=avif" %}
添加 Elastic 集成
{% endembed %}

2、进入集成目录后，在搜索字段中输入 **Bitwarden** 然后选择 Bitwarden。

{% embed url="https://bitwarden.com/assets/5mlMtswqip5Fbc9Z3u6zFX/1d202883452499e85a852fb9ac01e70a/2023-09-08_10-21-12.png?w=1200&fm=avif" %}
Bitwarden Elastic 集成
{% endembed %}

3、选择 **Add Bitwarden** 按钮以安装此集成。

4、如果这是您第一次运行 Elastic 集成，则需要安装 Elastic Agent。在以下界面上，选择 **Install Elastic Agent** 然后按照安装说明进行操作。

{% embed url="https://bitwarden.com/assets/2v3y1bfqiFdk2H9aLElJ26/f86ba44de90afcc37e38c06233ad0f70/2023-09-08_10-24-05.png?w=1200&fm=avif" %}
安装 Elastic 代理
{% endembed %}

5、要运行 Bitwarden 集成，需要使用 Elastic Agent 来维护集成数据。安装完成后，Elastic 会检测安装是否成功。成功设置代理后，选择 **Add the integration**。

{% embed url="https://bitwarden.com/assets/25pXseQDpZp8jly8kFKIub/22257e4116e67f12647a2e33071ba37f/2023-11-07_11-55-35.png?w=1200&fm=avif" %}
Elastic 设置
{% endembed %}

### 将集成连接到 Bitwarden <a href="#connect-integration-to-bitwarden" id="connect-integration-to-bitwarden"></a>

添加 Bitwarden 集成后，您将进入设置界面配置此集成。在此步骤中，您需要访问组织的 API 信息。保持该界面打开，在另一个标签页上登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

导航到组织的**设置** → **组织信息**界面，然后选择**查看 API 密钥**按钮。系统会要求您重新输入主密码，以访问 API 密钥信息。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6gHjAyqgeqDj6UPT6agsBK/3a614e043cb3836a41bd68f226835e53/2024-12-04_09-51-07.png?_a=DAJCwlWIZAAB" %}
组织 API 信息
{% endembed %}

在相应字段中输入以下信息：

| Elastic 字段    | 值                                                                                                                                                         |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| URL           | <p>对于 Bitwarden 云用户，默认 URL 为 <code>https://api.bitwarden.com</code>。</p><p></p><p>对于自托管 Bitwarden 用户，请输入您的自托管 URL。确保 URL 末尾不包含任何尾部正斜杠「<code>/</code>」</p> |
| Client ID     | 输入从 Bitwarden 组织 API 密钥窗口获取的 `client_id` 值。                                                                                                               |
| Client Secret | 输入从 Bitwarden 组织 API 密钥窗口获取的 `client_secret` 值。                                                                                                           |

{% hint style="info" %}
您的组织 API 密钥信息是敏感数据。不要在不安全的位置共享这些值。
{% endhint %}

完成必填字段后，继续向下滚动页面以应用所需的数据收集设置。完成后选择 **Confirm incoming data**。

{% hint style="info" %}
此时可使用其他高级选项进行配置。上面突出显示了添加 Bitwarden 集成所需的最少字段。要在以后访问集成以编辑设置，请转至菜单然后选择 **Integrations** → **Installed integrations** → **Bitwarden** → **Integration policies**。
{% endhint %}

如果所有数据输入正确，Elastic 将确认传入的数据并提供传入数据的预览。选择 **View assets** 以监控您的数据。

### 开始监控数据 <a href="#start-monitoring-data" id="start-monitoring-data"></a>

设置完成后，您就可以开始查看您的 Bitwarden 组织数据了。选择任何一个 Bitwarden 仪表板来监控与仪表板相关的数据。以下是每个仪表板监控数据的简要概述：

| 日志                                     | 描述                                                          |
| -------------------------------------- | ----------------------------------------------------------- |
| \[Logs Bitwarden] Policy               | 查看组织的策略变更，如启用、禁用或更新组织策略。                                    |
| \[Logs Bitwarden] Group and Collection | 监控与组织相关的群组和集合的记录事件。                                         |
| \[Logs Bitwarden] Event                | 监控组织事件日志。[此处](../event-logging/event-logs.md)了解有关事件日志的更多信息。 |

### 了解仪表板 <a href="#understanding-the-dashboards" id="understanding-the-dashboards"></a>

#### 查询 <a href="#queries" id="queries"></a>

Elastic 数据监控利用 Kibana 查询语言 (KQL) 来筛选数据。要了解有关查询和搜索的更多信息，请参阅 [Elastic 查询文档](https://www.elastic.co/guide/en/kibana/current/kuery-query.html)。

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

## 为 Bitwarden App 创建监控器 <a href="#create-a-monitor-for-bitwarden-app" id="create-a-monitor-for-bitwarden-app"></a>

### 开始监控数据 <a href="#start-monitoring-data" id="start-monitoring-data"></a>

### 时间范围 <a href="#timeframe" id="timeframe"></a>

### 示例查询 <a href="#sample-query" id="sample-query"></a>


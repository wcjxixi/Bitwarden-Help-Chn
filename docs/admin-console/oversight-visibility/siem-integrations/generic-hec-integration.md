# =通用 HEC 集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/generic-hec-integration/)
{% endhint %}

## 要求 <a href="#requirements" id="requirements"></a>

要设置 HTTP 摄取，您必须：

* 拥有 Bitwarden 团队版或企业版组织。
* 拥有符合 HTTP 摄取规范的平台账户并已完成设置。
* 拥有 Bitwarden 和您所选事件日志监控平台的管理访问权限。

## 设置 <a href="#setup" id="setup"></a>

将 Bitwarden 与 HTTP 摄取集成，需要在这两个平台上执行设置过程。

### 在您的 SIEM 平台中设置 HEC <a href="#set-up-hec-in-your-siem-platform" id="set-up-hec-in-your-siem-platform"></a>

### 从 Bitwarden 连接 <a href="#connect-from-bitwarden" id="connect-from-bitwarden"></a>

拥有 **HTTP Event Collector URL** 和 **HTTP Event Collector Token** 后，请在 Bitwarden 组织中提供这些信息以完成设置：

1、登录 Bitwarden 网页 App 并打开 **Admin Console**。

2、在 **Admin Console** 中，转到**集成** → **事件管理。**

3、找到**通用 HEC** 卡片并选择**连接**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4u1j0QHvTP0ffQr4xe8tw3/ab6fdac6e2fcd069bc78b803252174e9/HEC-card.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>通用 HEC 连接</p></figcaption></figure></div>

4、输入您的 **HTTP Event Collector URL** 和 **HTTP Event Collector Token**。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/D3QjBI9mp9H5YFQzctIx6/418d0ec7622d4fef644bdd056730c60c/2026-07-28_08-31-53.png?w=658&#x26;fm=avif" alt=""><figcaption><p>设置 HEC</p></figcaption></figure></div>

| 字段                             | 描述                                                                                                         |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| **HTTP Event Collector URL**   | 您的 SIEM 或日志记录平台提供的用于通过 HTTP 接收事件数据的端点 URL，包括端口（如果需要）（例如 `https://<your-hec-endpoint>/services/collector`）。 |
| **HTTP Event Collector Token** | 您的 SIEM 或日志记录平台为此集成生成的身份验证令牌或 API 密钥。Bitwarden 将在每个授权连接的请求中包含此令牌。                                          |

## 附加资源 <a href="#additional-resources" id="additional-resources"></a>

* 了解更多有关 [Bitwarden 会显示哪些事件](../event-logging/event-logs.md)的信息。
* 了解[非原生 SIEM 集成](non-native-siem.md)。

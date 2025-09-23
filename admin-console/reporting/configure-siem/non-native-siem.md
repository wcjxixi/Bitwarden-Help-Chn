# 非原生 SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/non-native-siem/)
{% endhint %}

Bitwarden 提供全面的事件日志记录功能，能够与安全信息和事件管理 (SIEM) 平台集成，而不仅仅是提供官方集成的解决方案。本文将指导您如何将 Bitwarden 与这些 SIEM 解决方案集成，例如流行的 Datadog 等平台。

## 要求 <a href="#requirements" id="requirements"></a>

要将 Bitwarden 与您的 SIEM 平台集成，您需要：

* Bitwarden 团队或企业计划（需要事件日志记录和 API 访问权限）。
* 通过管理员、所有者或自定义角色访问您的 Bitwarden 组织的管理权限。
* 了解您的 SIEM 平台可用的数据摄取方法。

## 数据访问 <a href="#data-access" id="data-access"></a>

Bitwarden 提供了多种访问与您的 SIEM 监控相关的数据的方法，允许您的平台在摄取信息方面具有灵活性：

### 公共 API 访问 <a href="#public-api-access" id="public-api-access"></a>

**（推荐）**&#x42;itwarden 公共 API 通过 `/events` 端点提供对事件日志的程序化访问。该 API 返回 JSON 格式的事件数据，可以被大多数现代 SIEM 平台消费，并且可用于访问更多的组织数据，而不仅限于事件数据，包括通过 `/members` 端点访问成员信息，通过 `/groups` 端点访问群组数据，以及通过 `/collections` 端点访问集合数据。[了解有关 API 的更多信息](../../../organizations/bitwarden-public-api.md)。

### CLI 数据提取 <a href="#cli-data-extraction" id="cli-data-extraction"></a>

Password Manager CLI 可用于提取可能为 API 提供的事件分析提供有用上下文的其他数据，例如使用 `list` 命令获取与从 API 访问的成员、群组或集合 ID 相关的项目数据。[了解有关 Password Manager CLI 的更多信息](../../../password-manager/developer-tools/cli/password-manager-cli.md)。

### 事件导出 <a href="#event-exports" id="event-exports"></a>

对于偏好基于文件摄取的 SIEM 平台，Bitwarden 允许手动以 .csv 格式导出事件日志。这种方法适用于批量处理场景和历史数据分析。[了解有关导出事件日志的更多信息](../event-logs.md#export-events)。

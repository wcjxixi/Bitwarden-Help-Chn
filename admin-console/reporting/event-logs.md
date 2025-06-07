# 事件日志

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/event-logs/)
{% endhint %}

事件日志是团队或企业组织内发生的事件的时间戳记录。要访问事件日志：

1、登录到 Bitwarden 网页 App 然后使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、从导航中选择**报告** → **事件日志**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2s5YQ3tIUHHI0UpTVXmUsJ/f0dfaf1d5b4f2cafa070238f435cdd8e/2024-12-04_09-48-02.png?_a=DAJCwlWIZAAB" %}
事件日志
{% endembed %}

事件日志可以从 [Bitwarden 公共 API](../../organizations/bitwarden-public-api.md) 的 `/events` 端点访问和导出，并无限期保留，但每次只能查看 367 天的数据（由范围选择器决定）。

Bitwarden 客户端和服务器都会捕获事件，其中大多数事件发生在客户端。服务器事件捕获是瞬时的，处理速度也很快，而客户端则每 60 秒向服务器推送一次事件数据，因此您可能会观察到最近事件的报告有轻微延迟。此外，客户端事件数据是通过 API 调用进行通信的，并且会重试，直到成功为止。因此，如果客户端无法与 API 通信，或者被修改为不发送事件，就无法接收并处理这些事件。

## 检查事件 <a href="#inspect-events" id="inspect-events"></a>

在网页 App 的**事件日志**视图中，选择粉红色的资源标识符（例如 `1e685004`）将做两件事：

1. 打开一个对话框，其中包含与该资源关联的事件列表。例如，选择一个项目的标识符将打开该项目被编辑、被查看等的时间列表，包括哪个成员执行的每个操作。
2. 导航到您访问资源的视图。例如，从**事件日志**中选择成员的标识符将带您进入**成员**视图并自动将列表筛选为该成员。

## 事件列表 <a href="#events-list" id="events-list"></a>

事件日志记录了超过 60 种不同类型的事件。事件日志界面捕捉事件的**时间戳**，包括应用程序的类型和 IP （通过悬停在 **🌎**地球图标上访问）等客户端 App 信息、连接到事件的**用户**、以及**事件**的描述。

{% hint style="info" %}
每一个**事件**都使用类型代码（`1000`、`1001` 等）关联，以标识事件所捕获的操作。[Bitwarden 公共 API](../../organizations/bitwarden-public-api.md) 使用类型代码来标识被事件所记录的操作。
{% endhint %}

下面列出了所有事件类型及其相应的类型代码：

### 用户事件 <a href="#user-events" id="user-events"></a>

* Logged In. (`1000`)
* Changed account password. (`1001`)
* Enabled/updated two-step login. (`1002`)
* Disabled two-step login. (`1003`)
* Recovered account from two-step login. (`1004`)
* Login attempted failed with incorrect password. (`1005`)
* Login attempt failed with incorrect two-step login. (`1006`)
* User Exported their personal Vault items. (`1007`)
* User updated a password issued through [account recovery](../../organizations/admin-password-reset.md). (`1008`)
* User migrated their decryption key with [Key Connector](../../self-hosting/key-connector/about-key-connector.md). (`1009`)
* User requested [device approval](../login-with-sso/trusted-devices/approve-a-trusted-device.md). (`1010`)

### 项目事件 <a href="#item-events" id="item-events"></a>

* Created item _item-identifier_. (`1100`)
* Edited item _item-identifier_. (`1101`)
* Permanently Deleted item _item-identifier_. (`1102`)
* Created attachment for item _item-identifier_. (`1103`)
* Deleted attachment for item _item-identifier_. (`1104`)
* Moved item _item-identifier_ to an organization. (`1105`)
* Edited collections for item _item-identifier_ (`1106`)
* Viewed item _item-identifier_. (`1107`)
* Viewed password for item _item-identifier_. (`1108`)
* Viewed hidden field for item _item-identifier_. (`1109`)
* Viewed security code for item _item-identifier_. (`1110`)
* Copied password for item _item-identifier_. (`1111`)
* Copied hidden field for item _item-identifier_. (`1112`)
* Copied security code for item _item-identifier_. (`1113`)
* Autofilled item _item-identifier_. (`1114`)
* Sent item _item-identifier_ to trash. (`1115`)
* Restored item _item-identifier_. (`1116`)
* Viewed Card Number for item _item-identifier_. (`1117`)

### 集合事件 <a href="#collection-events" id="collection-events"></a>

* Created collection _collection-identifier_. (`1300`)
* Edited collection _collection-identifier_. (`1301`)
* Deleted collection _collection-identifier_. (`1302`)

### 群组事件 <a href="#group-events" id="group-events"></a>

* Created group _group-identifier_. (`1400`)
* Edited group _group-identifier_. (`1401`)
* Deleted group _group-identifier_. (`1402`)

### 组织事件 <a href="#organization-events" id="organization-events"></a>

* Invited user _user-identifier_. (`1500`)
* Confirmed user _user-identifier_. (`1501`)
* Edited user _user-identifier_. (`1502`)
* Removed user _user-identifier_. (`1503`)
* Edited groups for user _user-identifier_. (`1504`)
* Unlinked SSO. (`1505`)
* _user-identifier_ enrolled in Master Password Reset. (`1506`)
* _user-identifier_ withdrew from Master Password Reset. (`1507`)
* Master Password was reset for _user-identifier_. (`1508`)
* Reset SSO link for user _user-identifier_. (`1509`)
* _user-identifer_ logged in using SSO for the first time. (`1510`)
* Revoked organization access for _user-identifier_ (`1511`)
* Restores organization access for _user-identifier_ (`1512`)
* Edited organization settings. (`1600`)
* Purged organization vault. (`1601`)
* Exported organization vault. (`1602`)
* Organization Vault access by a managing [Provider](../../provider-portal/provider-portal-overview.md). (`1603`)
* Organization enabled SSO. (`1604`)
* Organization disabled SSO. (`1605`)
* Organization enabled Key Connector. (`1606`)
* Organization disabled Key Connector. (`1607`)
* Families Sponsorships synced. (`1608`)
* Updated a Policy. (`1700`)
* Added domain _domain-name_. (`2000`)
* Removed domain _domain-name_. (`2001`)
* _Domain-name_ verified. (`2002`)
* _Domain-name_ not verified. (`2003`)

### Secrets Manager 事件 <a href="#secrets-manager-events" id="secrets-manager-events"></a>

Secrets Manager 事件可从组织密码库的**报告**选项卡和[服务账户事件日志页面](../../secrets-manager/your-secrets/machine-accounts.md#machine-account-events)获取。捕获以下 Secrets Manager 事件：

* Accessed secret _secret-identifier_. (`2100`)

### 提供商事件 <a href="#provider-events" id="provider-events"></a>

当[管理提供商](../../provider-portal/provider-portal-overview.md)的成员触发上述任何事件时，**用户**栏将记录提供商的名称。此外，每当管理提供商的成员访问您的组织密码库时，专用于提供商的事件也将被记录：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4e95ZWDt6ZBPfina42MZhP/d4653c6aebb2bcff6186e6d49415da61/2024-12-05_09-47-18.png?_a=DAJCwlWIZAAB" %}
提供商访问事件
{% endembed %}

## 导出事件 <a href="#export-events" id="export-events"></a>

导出事件日志将创建一个包含指定日期范围内所有事件的 `.csv` 文件：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/QL3nTOsAOsCPQtQTONOEw/53652d49e4bf8eaa67c972c1b55c12fc/2024-12-04_09-48-02.png?_a=DAJCwlWIZAAB" %}
导出事件日志
{% endembed %}

示例：

```
message,appIcon,appName,userId,userName,userEmail,date,ip,type
Logged in.,fa-globe,Web Vault - Chrome,1234abcd-56de-78ef-91gh-abcdef123456,Alice,alice@bitwarden.com,2021-06-14T14:22:23.331751Z,111.11.111.111,User_LoggedIn
Invited user zyxw9876.,fa-globe,Unknown,1234abcd-56de-78ef-91gh-abcdef123456,Alice,alice@bitwarden.com,2021-06-14T14:14:44.7566667Z,111.11.111.111,OrganizationUser_Invited
Edited organization settings.,fa-globe,Web Vault - Chrome,9876dcba-65ed-87fe-19hg-654321fedcba,Bob,bob@bitwarden.com,2021-06-07T17:57:08.1866667Z,222.22.222.222,Organization_Updated
```

## API 响应 <a href="#api-responses" id="api-responses"></a>

从 [Bitwarden 公共 API](../../organizations/bitwarden-public-api.md) 的 `/events` 端点访问事件日志将返回 JSON 响应，例如下面这样：

```bash
{
  "object": "list",
  "data": [
    {
      "object": "event",
      "type": 1000,
      "itemId": "string",
      "collectionId": "string",
      "groupId": "string",
      "policyId": "string",
      "memberId": "string",
      "actingUserId": "string",
      "date": "2020-11-04T15:01:21.698Z",
      "device": 0,
      "ipAddress": "xxx.xx.xxx.x"
    }
  ],
  "continuationToken": "string"
}
```

## SIEM 和外部系统集成 <a href="#siem-and-external-systems-integrations" id="siem-and-external-systems-integrations"></a>

> **\[译者注]**：[SIEM](https://en.wikipedia.org/wiki/Security_information_and_event_management)（Security Information and Event Management，安全信息与事件管理）是一种综合性的网络安全解决方案，用于实时收集、分析、关联和响应来自企业IT基础设施中的安全事件和日志数据。其核心目标是通过集中化监控和智能分析，帮助组织检测威胁、调查安全事件并满足合规要求。
>
> 常见的 SIEM 工具有：
>
> * 商业产品：Splunk Enterprise Security、IBM QRadar、Microsoft Sentinel、LogRhythm 等
> * 开源/免费方案：Elastic Stack、OSSIM、Wazuh 等

当将数据从 Bitwarden 导出到其他系统时，可以使用 API​​ 和 CLI 的组合数据来收集数据。

例如，Bitwarden RESTful API 围绕组织结构收集数据。

* GET /public/members：返回成员、ID 和分配的群组 ID
* GET /public/groups：返回所有群组、ID、分配的集合及其权限
* GET /public/collections：返回所有集合及其分配的群组

获得每个成员、群组和集合的唯一 ID 之后，您现在就可以使用 CLI 工具通过 CLI 命令 `bw-list` 来收集信息，该命令以 JSON 格式检索以下项目：

* 组织成员
* 项目
* 集合
* 群组

在收集这些数据后，您可以将行连接到它们唯一的 ID 上，以建立对您的 Bitwarden 组织所有部分的参考。有关 Bitwarden CLI 使用的更多信息，请参阅 [Bitwarden 命令行工具 (CLI)](../../password-manager/developer-tools/password-manager-cli.md)。

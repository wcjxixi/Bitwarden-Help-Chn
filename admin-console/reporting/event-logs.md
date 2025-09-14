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

* 登录了。(`1000`)
* 修改了账户密码。(`1001`)
* 启用/更新了两步登录。(`1002`)
* 禁用了两步登录。(`1003`)
* 从两步登录中恢复了账户。(`1004`)
* 登录尝试因密码错误而失败。(`1005`)
* 登录尝试因两步登录错误而失败。(`1006`)
* 用户导出了他们个人的密码库项目。(`1007`)
* 用户通过[账户恢复](../../organizations/admin-password-reset.md)更新了密码。(`1008`)
* 用户使用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 迁移了他们的解密密钥。(`1009`)
* 用户请求了[设备批准](../login-with-sso/trusted-devices/approve-a-trusted-device.md) 。(`1010`)

### 项目事件 <a href="#item-events" id="item-events"></a>

* 创建了项目 _item-identifier_。(`1100`)
* 编辑了项目 _item-identifier_。(`1101`)
* 永久删除了项目 _item-identifier_。(`1102`)
* 为项目 _item-identifier_ 创建了附件。(`1103`)
* 为项目 _item-identifier_ 删除了附件。(`1104`)
* 将项目 _item-identifier_ 移动至组织。(`1105`)
* 编辑了项目 _item-identifier_ 的集合。(`1106`)
* 查看了项目 _item-identifier_。(`1107`)
* 查看了项目 _item-identifier_ 的密码。(`1108`)
* 查看了项目 _item-identifier_ 的隐藏字段。(`1109`)
* 查看了项目 _item-identifier_ 的安全码。(`1110`)
* 复制了项目 _item-identifier_ 的密码。(`1111`)
* 复制了项目 _item-identifier_ 的隐藏字段。(`1112`）
* 复制了项目 _item-identifier_ 的安全码。(`1113`）
* 自动填充了项目 _item-identifier_。(`1114`）
* 将项目 _item-identifier_ 移至回收站。(`1115`)
* 恢复了项目 _item-identifier_。(`1116`)
* 查看了项目 _item-identifier_ 的卡号。(`1117`)

### 集合事件 <a href="#collection-events" id="collection-events"></a>

* 创建了集合 _collection-identifier_。(`1300`)
* 编辑了集合 _collection-identifier_。(`1301`)
* 删除了集合 _collection-identifier_。(`1302`)

### 群组事件 <a href="#group-events" id="group-events"></a>

* 创建了群组 _group-identifier_。(`1400`)
* 编辑了群组 _group-identifier_。(`1401`)
* 删除了群组 _group-identifier_。(`1402`)

### 组织事件 <a href="#organization-events" id="organization-events"></a>

* 邀请了用户 _user-identifier_。(`1500`)
* 确认了用户 _user-identifier_。(`1501`)
* 编辑了用户 _user-identifier_。(`1502`)
* 删除了用户 _user-identifier_。(`1503`)
* 编辑了用户 _user-identifier_ 的群组。(`1504`)
* 为用户 _user-identifier_ 取消链接 SSO 。(`1505`)
* 用户 _user-identifier_ 加入了账户恢复。(`1506`)
* 用户 _user-identifier_ 退出了账户恢复。(`1507`)
* 用户 _user-identifier_ 重置了主密码。(`1508`)
* 重置了用户 _user-identifier_ 的 SSO 链接。(`1509`)
* 用户 _user-identifier_ 首次使用 SSO 登录。(`1510`)
* 撤销了用户 _user-identifier_ 的组织访问权限。(`1511`)
* 恢复了用户 _user-identifier_ 的组织访问权限。(`1512`)
* 批准了用户 _user-identifier_ 的设备。(`1513`)
* 拒绝了用户 _user-identifier_ 的设备。(`1514`)
* 所有者/管理员删除了用户 _user-identifier_ 的账户。(`1515`)
* 用户 _user-identifier_ 离开了组织。(`1516`)
* 编辑了组织设置。(`1600`)
* 清除了组织密码库。(`1601`)
* 导出了组织密码库。(`1602`)
* 管理[提供商](../../provider-portal/provider-portal-overview.md)访问了组织密码库。(`1603`)
* 组织启用了 SSO。(`1604`)
* 组织禁用了 SSO。(`1605`)
* 组织启用了 Key Connector。(`1606`)
* 组织禁用了 Key Connector。(`1607`)
* 家庭赞助同步完成。(`1608`)
* 修改了集合管理设置。(`1609`)
* 修改了策略 _policy-identifier_。(`1700`)
* 添加了域名 _domain-name_。(`2000`)
* 移除了域名 _domain-name_。(`2001`)
* 域名 &#x64;_&#x6F;main-name_ 已验证。(`2002`)
* 域名 _domain-name_ 未验证。(`2003`)

### Secrets Manager 事件 <a href="#secrets-manager-events" id="secrets-manager-events"></a>

Secrets Manager 事件可从组织密码库的**报告**选项卡和[服务账户事件日志页面](../../secrets-manager/your-secrets/machine-accounts.md#machine-account-events)获取。捕获以下 Secrets Manager 事件：

* 访问了标识符为 _secret-identifier_ 的机密。(`2100`)
* 编辑了标识符为 _secret-identifier_ 的机密。(`2101`)
* 删除了标识符为 _secret-identifier_ 的机密。(`2102`)
* 创建了标识符为 _secret-identifier_ 的新机密。(`2103`)
* 访问了标识符为 _project-identifier_ 的工程。(`2200`)
* 创建了标识符为 _project-identifier_ 的新工程。(`2201`)
* 编辑了标识符为 _project-identifier_ 的工程。(`2202`)
* 删除了标识符为 _project-identifier_ 的工程。(`2203`)

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

Bitwarden 提供了一套与安全信息和事件管理 (SIEM) 平台的全面集成，以利用事件日志：

* [Elastic SIEM](configure-siem/elastic-siem.md)
* [Microsoft Sentinel SIEM](configure-siem/microsoft-sentinel-siem.md)
* [Panther SIEM](configure-siem/panther-siem.md)
* [Rapid7 SIEM](configure-siem/rapid7-siem.md)
* [Splunk SIEM](configure-siem/splunk-siem.md)

Bitwarden 还提供了多种数据访问方法，这些数据可能与 SIEM 平台相关，但目前还没有特定的集成。有关配置上面未列出的 SIEM 的帮助，请参阅[非原生 SIEM](configure-siem/non-native-siem.md)。

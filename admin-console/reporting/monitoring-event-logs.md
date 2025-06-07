# =监控事件日志

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/monitoring-event-logs/)
{% endhint %}

通过与 SIEM（安全信息与事件管理）系统集成的事件监控功能，您能有效监督组织活动以维持最佳安全实践并确保合规性。以下章节重点介绍多项监控参考指标，这些指标将增强您对 Bitwarden 解决方案的可观测性，包括洞察用户在密码库中的操作行为，并提供自动化告警目标的示例。

这些事件选自 Bitwarden 事件日志。通过针对关键业务事件配置实时告警与时段累积告警策略，您将能根据自身独特的安全态势，对组织使用 Bitwarden 的情况进行全面审计。

## 理解日志 <a href="#understanding-logs" id="understanding-logs"></a>

多种 SIEM 平台与 Bitwarden 集成，用于审查日常保险库使用的关键信息。

{% embed url="https://bitwarden.com/assets/1wHDe1snFJ4NB1G13VBUBC/31248544d432c33c18f56e7fb6800e0a/Panther_JSON_Object.png?w=644&fm=avif&q=80" %}
Panther JSON 对象
{% endembed %}

SIEM 事件监控平台将提供需要监控的特定字段，以维持高标准的安全性：

| 值                 | 描述                                                                                                                                            |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `actingUserEmail` | 执行操作的用户邮箱。                                                                                                                                    |
| `actingUserId`    | 执行操作的用户唯一 ID。                                                                                                                                 |
| `actingUserName`  | 执行操作的用户名称。                                                                                                                                    |
| `collectionId`    | 组织集合 ID。                                                                                                                                      |
| `device`          | 设备的数值 ID。精确映射可以在这里找到[这里 ](https://github.com/bitwarden/server/blob/d50ad97e6eeb733af9c069a949939b0567ba936d/src/Core/Enums/DeviceType.cs#L4)。 |
| `ipAddress`       | 执行事件的 IP 地址。                                                                                                                                  |
| `itemId`          | 组织保险库的项目（密码、安全笔记等）。                                                                                                                           |
| `policyId`        | 组织策略更新。查看组织事件 [此处 ](https://bitwarden.com/help/event-logs/#organization-events)。                                                              |

## 关注趋势 <a href="#concerning-trends" id="concerning-trends"></a>

追踪 Bitwarden 使用趋势可以识别可疑活动或潜在安全威胁：

### 登录尝试失败率异常 <a href="#abnormal-rate-of-failed-login-attempts" id="abnormal-rate-of-failed-login-attempts"></a>

* 登录失败尝试
  * `1005` 使用错误密码登录失败
  * `1006` 使用错误的双因素登录尝试失败
* Failed Login attempts
  * `1005` Login attempt failed with incorrect password
  * `1006` Login attempt failed with incorrect two step login.

### 查看敏感或隐藏字段的异常频率 <a href="#abnormal-rate-of-viewing-sensitive-or-hidden-fields" id="abnormal-rate-of-viewing-sensitive-or-hidden-fields"></a>

* 查看项目
  * `1107` 查看项目 `item-identifier`
  * `1108` 查看了项目 `item-identifier` 的密码
  * `1109` 查看了项目 `item-identifier` 的隐藏字段
  * `1110` 查看了项目 `item-identifier` 的安全码
* 复制项目字段
  * `1111` 复制了项目 `item-identifier` 的密码
  * `1112` 复制了项目 `item-identifier` 的安全代码
* Viewing item
  * `1107` Viewed item `item-identifier`
  * `1108` Viewed password for item `item-identifier`
  * `1109` Viewed hidden field for item `item-identifier`
  * `1110` Viewed security code for item `item-identifier`
* Copying item fields
  * `1111` Copied password for item `item-identifier`
  * `1112` Copied security code for item `item-identifier`

## 使用趋势 <a href="#usage-trends" id="usage-trends"></a>

监控使用趋势以识别使用 Bitwarden 并保持安全实践的用户：

### 监控用户频率 <a href="#monitor-user-frequency" id="monitor-user-frequency"></a>

* 保险库使用情况
  * `1000` 登录
  * `1010` 用户请求 [设备批准](https://bitwarden.com/help/approve-a-trusted-device/)
* Vault usage
  * `1000` Logged in
  * `1010` User requested [device approval](https://bitwarden.com/help/approve-a-trusted-device/)

## 关键的密码库操作 <a href="#critical-vault-actions" id="critical-vault-actions"></a>

### 超级用户活动 <a href="#super-user-activities" id="super-user-activities"></a>

* 个人账户活动
  * `1000` 登录
  * `1001` 已更改账户密码
  * `1002` 启用/更新了双重验证登录
  * `1003` 禁用了双重验证登录
  * `1007` 用户导出了他们个人的保险箱项目
  * `1603` 管理员通过[提供者](https://bitwarden.com/help/providers/)访问了组织保险箱
* 组织活动
  * `1500` 邀请用户 `user-identifier`
  * `1501` 确认用户 `user-identifier`
  * `1502` 编辑用户 `user-identifier`
  * `1504` 编辑用户的组 `user-identifier`
  * `1511` 为用户 `user-identifier` 撤销了组织访问权限
  * `1512` 为 `user-identifier` 恢复了组织访问权限
  * `1513` 为 `user-identifier` 批准了设备
  * `1600` 编辑组织设置
  * `1609` 修改集合管理设置
  * `1700` 修改策略 `policy-identifier`
  * `2001` 移除域名 `domain-name`
* 导出组织保险库信息
  * `1602` 导出的组织保险库
* Individual account activity
  * `1000` Logged in
  * `1001` Changed account password
  * `1002` Enabled/updated two-step login
  * `1003` Disabled two-step login
  * `1007` User exported their individual vault items
  * `1603` Organization vault access by a managing [provider](https://bitwarden.com/help/providers/)
* Organization activities
  * `1500` Invited user `user-identifier`
  * `1501` Confirmed user `user-identifier`
  * `1502` Edited user `user-identifier`
  * `1504` Edited groups for user `user-identifier`
  * `1511` Revoked organization access for user `user-identifier`
  * `1512` Restored organization access for `user-identifier`
  * `1513` Approved device for `user-identifier`
  * `1600` Edited organization settings
  * `1609` Modified collection management setting
  * `1700` Modified policy `policy-identifier`
  * `2001` Removed domain `domain-name`
* Exporting organization vault information
  * `1602` Exported organization vault

### 关键的项目活动 <a href="#critical-item-activities" id="critical-item-activities"></a>

* 已识别为关键项的变更
  * `1101` 编辑项目 `item-identifier`
  * `1105` 将项目 `item-identifier` 移至组织
  * `1106` 编辑了项目 `item-identifier` 的收藏集
  * `1107` 查看项目 `item-identifier`
  * `1108` 查看了项目 `item-identifier` 的密码
  * `1109` 查看了项目 `item-identifier` 的隐藏字段
  * `1110` 查看了项目 `item-identifier` 的安全码
  * `1111` 复制了项目 `item-identifier` 的密码
  * `1112` 复制了项目的隐藏字段 `item-identifier`
  * `1113` 复制了项目 `item-identifier` 的安全码
  * `1114` 自动填充了项目 `item-identifier`
  * `1117` 查看了项目 `item-identifier` 的卡片数量
* Changes made to items that have been identified to be critical
  * `1101` Edited item `item-identifier`
  * `1105` Moved item `item-identifier` to an organization
  * `1106` Edited collections for item `item-identifier`
  * `1107` Viewed item `item-identifier`
  * `1108` Viewed password for item `item-identifier`
  * `1109` Viewed hidden field for item `item-identifier`
  * `1110` Viewed security code for item `item-identifier`
  * `1111` Copied password for item `item-identifier`
  * `1112` Copied hidden field for item `item-identifier`
  * `1113` Copied security code for item `item-identifier`
  * `1114` Autofilled item `item-identifier`
  * `1117` Viewed card number for item `item-identifier`


# =来自 Bitwarden 服务器的电子邮件

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/list-of-emails/)
{% endhint %}

本文描述了从 `no-reply@bitwarden.com` 或 `no-reply@bitwarden.eu` 自动发送给组织成员（包括所有者、管理员和最终用户）以及个人用户的电子邮件。

本文中的电子邮件按接收人和重要程度排列。**在组织环境中，某封电子邮件是否被视为紧要电子邮件可能取决于您的组织的独特部署或要求。**

## 组织电子邮件 <a href="#organization-emails" id="organization-emails"></a>

### 紧要的管理电子邮件 <a href="#https-bitwarden.com-help-list-of-emails-critical-administrative-emails" id="https-bitwarden.com-help-list-of-emails-critical-administrative-emails"></a>

以下电子邮件用于提醒 Bitwarden 组织的所有者和管理员有关其组织的紧要的变更或操作项目：

| 主题                     | 变量                        | 描述                                                                                                                  |
| ---------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| 您的订阅即将续订               | n/a                       | 当组织订阅[即将到期](../../plans-and-pricing/organization-renewal.md)时，组织的计费电子邮箱会收到此电子邮件。                                    |
| {Organization} 席位数量已增加 | {Organization} = 您组织的显示名称 | 当组织[席位数量自动扩展](../../organizations/user-management.md#user-seats)时，所有所有者会收到此电子邮件。                                    |
| {Organization} 席位已达上限  | {Organization} = 您组织的显示名称 | 当组织成员数量达到他们的[席位限制](../../organizations/user-management.md#set-a-seat-limit)时，所有所有者会收到此电子邮件。                         |
| 域名未声明                  | n/a                       | 当组织[尝试声明新域名未成功](../../admin-console/login-with-sso/claimed-domains.md)时，所有所有者和管理员会收到此电子邮件。                          |
| 需要采取行动：{User} 需要确认     | {User} = 用户的电子邮箱地址        | 当用户[等待确认加入组织](../../organizations/user-management.md#confirm)时，所有所有者和管理员会收到此电子邮件。                                   |
| 审核新设备的 SSO 登录请求        | n/a                       | 当用户等待[受信任设备被批准](../../admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md)时，所有所有者和管理员会收到此电子邮件。 |
| 请求删除您的组织               | n/a                       | <p>如果向 Bitwarden 支持团队请求删除其组织，其所有者会收到此电子邮件。</p><p>此电子邮件只会发送给已与 Bitwarden 支持团队确认可以启动组织删除的有效所有者。</p>                   |

### 紧要的成员电子邮件 <a href="#critical-member-emails" id="critical-member-emails"></a>

以下电子邮件用于提醒 Bitwarden 组织成员（所有角色）有关其账户的紧要的变更或操作项目：

| 主题                                  | 变量                        | 描述                                                                                                                                                                             |
| ----------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 加入 {Organization}                   | {Organization} = 您组织的显示名称 | 当其被邀请加入组织时，用户会收到此电子邮件。                                                                                                                                                         |
| 您已被从 {Organization} 中移除             | {Organization} = 您组织的显示名称 | 当其因违反[要求两步登录](../../organizations/enterprise-policies.md#require-two-step-login)或[单一组织](../../organizations/enterprise-policies.md#single-organization)策略而被撤销访问权限时，用户会收到此电子邮件。 |
| 您的管理员已发起账户恢复                        | n/a                       | 当管理员[对其账户发起了账户恢复](../../organizations/admin-password-reset.md#recover-an-account)时，用户会收到此电子邮件。                                                                                 |
| 登录请求已批准                             | n/a                       | 当其[受信任设备的登录请求被管理员批准](../../admin-console/login-with-sso/trusted-devices/approve-a-trusted-device.md)时，用户会收到此电子邮件。                                                              |
| 您的 Bitwarden 账户已被 {Organization} 声明 | {Organization} = 您组织的显示名称 | 当其[账户被他们所属的组织声明](../../admin-console/user-management/claimed-accounts.md)时，用户将收到此电子邮件。                                                                                         |

### 紧要的 Secrets Manager 电子邮件 <a href="#critical-secrets-manager-emails" id="critical-secrets-manager-emails"></a>

以下的电子邮件用于提醒 Bitwarden 组织的所有者有关其 Secrets Manager 使用情况的紧要的变更或操作项目：

| 主题                                      | 变量                        | 描述                                                                                                                                                             |
| --------------------------------------- | ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| {Organization} Secrets Manager 席位已达上限   | {Organization} = 您组织的显示名称 | 当组织中[分配给 Secrets Manager 的用户数量达到席位限制](../../secrets-manager/get-started/secrets-manager-quick-start.md#user-seats-and-service-account-scaling)时，所有所有者会收到此电子邮件。 |
| {Organization} Secrets Manager 机器账户已达上限 | {Organization} = 您组织的显示名称 | 当组织中创建的[机器账户数量达到机器账户限制](../../secrets-manager/get-started/secrets-manager-quick-start.md#user-seats-and-service-account-scaling)时，所有所有者会收到此电子邮件。               |

### 非紧要的组织电子邮件 <a href="#non-critical-organization-emails" id="non-critical-organization-emails"></a>

以下的电子邮件用于提醒 Bitwarden 组织成员（所有角色）有关其账户或组织的非紧要的变更或操作项目：

| 主题                     | 变量                        | 描述                                            |
| ---------------------- | ------------------------- | --------------------------------------------- |
| 您已被确认加入 {Organization} | {Organization} = 您组织的显示名称 | 当其组织访问权限被确认时，用户会收到此电子邮件。                      |
| 请求访问 Secrets Manager   | n/a                       | 当有用户请求访问 Secrets Manager 时，管理员或所有者会收到此电子邮件。   |
| 接受您的免费家庭订阅             | n/a                       | 当组织的成员被邀请创建一个赞助的家庭组织时，用户会收到此电子邮件。             |
| 成功！已接受家庭订阅             | n/a                       | 当其已兑换创建赞助的家庭组织的邀请时，用户会收到此电子邮件。                |
| 您的家庭赞助已被移除             | n/a                       | 当其已手动移除家庭组织的赞助时，用户会收到此电子邮件。                   |
| 移除免费 Bitwarden 家庭计划    | n/a                       | 当家庭组织的赞助被管理员移除时（通常是通过激活了某个策略后被移除），用户会收到此电子邮件。 |

## 提供商 & 业务单位电子邮件 <a href="#provider-and-business-unit-emails" id="provider-and-business-unit-emails"></a>

以下的电子邮件用于提醒提供商和业务单元管理员有关其提供商或业务单元的任何变更或操作项目：

| 主题                              | 变量                                   | 描述                                             |
| ------------------------------- | ------------------------------------ | ---------------------------------------------- |
| 创建提供商                           | n/a                                  | 当其被注册用于创建提供商时，提供商管理员会收到此电子邮件。                  |
| 设置业务单元                          | n/a                                  | 当其被注册用于创建业务单元时，业务单元管理员会收到此电子邮件。                |
| 加入 {Provider/Business Unit}     | {Provider/Business Unit} = 您提供商的显示名称 | 当其被邀请加入提供商或业务单元时，用户会收到此电子邮件。                   |
| 您已确认加入 {Provider/Business Unit} | {Provider/Business Unit} = 您提供商的显示名称 | 当其对提供商或业务单元的访问权限被确认时，用户会收到此电子邮件。               |
| 您已被移除 {Provider/Business Unit}  | {Provider/Business Unit} = 您提供商的显示名称 | 当其对提供商或业务单元的访问权限被移除时，用户会收到此电子邮件。               |
| 更新您的计费信息                        | n/a                                  | 当其组织从提供商管理中被移除，并且必须添加一个付款方式时，客户组织的所有者会收到此电子邮件。 |
| 请求删除您的提供商                       | n/a                                  | 当其向 Bitwarden 支持团队请求删除其组织时，所有者会收到此电子邮件。        |

## 自托管电子邮件 <a href="#self-hosting-emails" id="self-hosting-emails"></a>

以下的电子邮件用于提醒管理员有关其自托管 Bitwarden 部署的更改或与服务器相关的操作项目：

| 主题          | 变量  | 描述                                           |
| ----------- | --- | -------------------------------------------- |
| 许可证过期       | n/a | 当自托管服务器的许可证文件已过期并且超过了 60 天的宽限期时，所有者会收到此电子邮件。 |
| \[管理员] 继续登录 | n/a | 当登录系统管理员门户时，管理员收到此电子邮件。                      |

## 通用的电子邮件 <a href="#widely-applicable-emails" id="widely-applicable-emails"></a>

以下的电子邮件用于提醒 Bitwarden 用户（包括所有角色的组织成员和个人用户）有关其账户的变更或操作项目：

| 主题               | 变量                                            | 描述                                          |
| ---------------- | --------------------------------------------- | ------------------------------------------- |
| 验证您的电子邮箱         | n/a                                           | 在独立创建账户期间，用户会收到此电子邮件。                       |
| 您的电子邮箱变更         | n/a                                           | 当其发起更改账户电子邮箱地址的请求时，用户会收到此电子邮件。              |
| 您的主密码提示          | n/a                                           | 当其在登录期间请求了主密码提示时，用户会收到此电子邮件。                |
| 主密码已更改           | n/a                                           | 当其主密码被更改时，用户收到会此电子邮件。                       |
| 您的 Bitwarden 验证码 | n/a                                           | 当其登录时，如果他们需要输入基于电子邮件的两步登录或验证新设备，用户会收到此电子邮件。 |
| 从新设备 {Device} 登录 | {Device} = 设备类型，例如「Chrome 扩展」、「Windows」或「iOS」 | 当其从新的设备登录其账户时，用户会收到此电子邮件。                   |
| 检测到失败的登录尝试       | n/a                                           | 当其多次尝试登录其 Bitwarden 账户失败时，用户会收到此电子邮件。       |
| 从 {IP} 恢复了 2FA   | {IP} = IP 地址。                                 | 当其使用两步登录恢复代码停用了 2FA 时，用户会收到此电子邮件。           |
| 删除您的账户           | n/a                                           | 当其请求删除其账户时，用户会收到此电子邮件。                      |
| 支付失败             | n/a                                           | 当其订阅关联的付款方式在续费失败时，用户会收到此电子邮件。               |
| 账户信用支付处理完成       | n/a                                           | 当其账户信用额度用于订阅续费时，用户会收到此电子邮件。                 |
| 欢迎使用 Bitwarden！  | n/a                                           | 当其创建了一个新的 Bitwarden 账户时，用户会收到此电子邮件。         |
| 紧急访问联系人邀请        | n/a                                           | 当其被邀请成为另一位用户的紧急联系人时，用户会收到此电子邮件。             |
| 接受了紧急访问          | n/a                                           | 当另一位用户已接受邀请成为其紧急联系人时，用户会收到此电子邮件。            |
| 您已被确认为紧急访问联系人    | n/a                                           | 当其被确认成为另一位用户的紧急联系人时，用户会收到此电子邮件。             |
| 紧急访问已发起          | n/a                                           | 当某个紧急联系人请求访问其账户时，用户会收到此电子邮件。                |
| 紧急访问已批准          | n/a                                           | 当其紧急访问他人账户的请求被批准时，用户会收到此电子邮件。               |
| 紧急访问被拒绝          | n/a                                           | 当其紧急访问他人账户的请求被拒绝时，用户会收到此电子邮件。               |
| 待处理的紧急访问请求       | n/a                                           | 当其发起的紧急访问请求在一定时间后仍未处理时，用户会收到此电子邮件。          |
| 紧急访问已授权          | n/a                                           | 当其账户被授权成为紧急联系人时，用户会收到此电子邮件。                 |

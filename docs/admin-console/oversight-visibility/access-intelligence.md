# =Access Intelligence

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/access-intelligence/)
{% endhint %}

企业组织可以使用 Access Intelligence 来识别并优先处理由其成员存储在 Bitwarden 组织内的、存在风险凭据的应用程序。通过此报告，您可以选择关键应用程序，并通知组织成员需要对存在风险的密码采取措施。

Access Intelligence 为管理员提供了便捷的集中式可见性，以了解哪些凭据存在风险 ，但它不会授予管理员原本无法访问的密码的直接访问权限。

{% hint style="info" %}
Access Intelligence 不允许管理员查看非组织所有者的项目。为确保全面了解所有潜在的存在风险的凭据，Bitwarden 建议激活强制组织数据所有权策略，以便所有数据都归组织所有。
{% endhint %}

## 运行报告 <a href="#run-the-report" id="run-the-report"></a>

随着应用程序在您组织中的不断演变和变化，本报告的内容也将随之改变。Access Intelligence 必须被视为一项持续性的工作，至关重要。要更新报告，请注意**数据最后更新**时间戳，并选择**运行报告**按钮。

{% embed url="https://bitwarden.com/assets/6ooDvXBHM0ehpTD2XWpQGK/1358401b192cae48f3c27f2fc1ed1c8f/riskinsights4.png?w=1092&fm=avif" %}
运行 Access Intelligence 报告
{% endembed %}

## 活动 <a href="#activity" id="activity"></a>

Access Intelligence 报告的**活动**选项卡提供了关键数据点和任务的摘要。虽然活动选项卡能一目了然地提供这些信息，但您应该熟悉**所有应用程序**和**关键应用程序**选项卡，以便更好地理解这里展示的内容：

{% embed url="https://bitwarden.com/assets/4ors4hBI2rwbW0zvjb2W0U/437e05ac30f7245ee676ba9204b52c84/riskinsights1.png?w=1092&fm=avif" %}
访问 Access Intelligence 活动选项卡
{% endembed %}

* **密码更改进度** ：已发送密码更改请求的完成百分比。
* **高风险成员** ：有权访问高风险项目的成员数量，这些项目属于关键应用。
* **关键应用** ：目前处于高风险状态的关键应用比例。
* **需要审核的应用** ：自报告上次运行以来，成员添加的新应用数量。

### 确定风险 <a href="#determining-risk" id="determining-risk"></a>

如果密码强度不足、已泄露或在组织内重复使用，则该密码被视为**存在风险** 。此分析使用与弱密码报告 、 已泄露密码报告和重复使用密码报告中相同的工具进行。与手动运行报告一样，Access Intelligence 进行的分析是在本地完成的，以保护零知识并维护您的数据完整性和匿名性。

## 所有应用程序 <a href="#all-applications" id="all-applications"></a>

《Access Intelligence》报告列出了您 Bitwarden 组织中保存的所有应用程序。每个应用程序代表一组所有具有与给定网络服务匹配的 URI 的项目（例如，“Atlassian”应用程序可能包含 26 个“总密码”，表示有 26 个项目包含用于登录 Atlassian 的凭证），并包含：

|           |                         |
| --------- | ----------------------- |
| 列         | 描述                      |
| **应用程序**  | 该应用程序的名称，处于风险中 。        |
| **风险密码**  | 与该应用程序相关联且处于风险中的密码数量。   |
| **总密码数**  | 与应用程序关联的密码总数。           |
| **有风险成员** | 有权访问与应用程序关联的有风险密码的成员数量。 |
| **总成员数**  | 可以访问该应用程序的成员总数。         |

{% hint style="info" %}
通过列出所有组织成员拥有凭证的应用程序，Access Intelligence 还可以帮助管理员检测未经授权的应用程序使用情况，以及那些可以通过 IdP 迁移到单点登录（SSO）身份验证的应用程序。
{% endhint %}

### 标记关键应用程序 <a href="#marking-critical-applications" id="marking-critical-applications"></a>

{% hint style="success" %}
区分 **关键应用** 和 **所有应用** 是确保组织成员能够迅速处理最重要应用的重要工具。

Access Intelligence 的一项重要功能是向成员发送通知，告知他们需要处理一个关键的高风险密码。通过分批次发送这些通知，有助于防止成员因警报疲劳而导致的修复延迟。
{% endhint %}

被标记为**关键**的应用是指那些将向组织成员发送通知，告知他们需要处理高风险密码的应用。要标记应用为关键，请勾选一个或多个复选框，然后选择**将应用标记为关键**按钮：

{% embed url="https://bitwarden.com/assets/77hdEeJiKWpHd8BoHYbnCx/a63f1756ac6ac188116279c320fcd4be/riskinsights2.png?w=1092&fm=avif" %}
标记一个关键应用
{% endembed %}

## 关键应用程序 <a href="#critical-applications" id="critical-applications"></a>

使用 Access Intelligence，管理员可以预先评估他们希望优先处理哪些应用程序。报告可以从组织内存储凭证的**所有应用程序**缩小范围，仅限于他们选择作为当前**需要立即处理的关键应用程序** 。

### 要求更改密码 <a href="#requesting-password-changes" id="requesting-password-changes"></a>

请求修改密码将会向有权访问关键应用的组织成员发送通知，告知他们需要处理有风险密码。成员将通过电子邮件收件箱和已登录的 Bitwarden 浏览器扩展中的横幅接收通知。

{% hint style="success" %}
在发送您的第一个密码更改请求之前，或作为员工 Bitwarden 培训的一部分，我们建议：

* 告知成员这些邮件是合法的，不应被忽略。
* 向成员提供关于如何处理密码更改请求的说明。
{% endhint %}

要请求更改所有当前标记为[关键](https://bitwarden.com/help/access-intelligence/#marking-critical-applications)的应用程序的密码，请导航至**关键应用程序**视图，并选择**请求密码更改** ：

{% embed url="https://bitwarden.com/assets/6wQ3EUzMFkzRIkA2FHgnlY/abac6f520da4c9f509a9c17a783f36a9/riskinsights3.png?w=1092&fm=avif" %}
请求修改密码
{% endembed %}

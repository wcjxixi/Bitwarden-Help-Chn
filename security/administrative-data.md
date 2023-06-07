# 管理数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/administrative-data/)
{% endhint %}

用户提供的个人信息与您的账户创建、Bitwarden 服务和支持的使用以及 Bitwarden 服务的支付相关联。Bitwarden 使用管理数据向您提供 Bitwarden 服务。只要您是 Bitwarden 的客户，我们就会根据法律要求保留管理数据。如果您终止与 Bitwarden 的关系，我们将根据我们的数据保留政策删除您的个人信息。

{% hint style="success" %}
我们鼓励您查看我们的[隐私政策](https://bitwarden.com/privacy)页面以了解更多信息。
{% endhint %}

Bitwarden **不会记录用户活动或例如 IP 地址、身份验证、访问或使用等访问信息**。与用户活动相关的信息仅可通过[事件日志](../admin-console/reporting/event-logs.md)提供给团队或企业组织。如上所述，Bitwarden 使用一些数据为您提供 Bitwarden 服务，这些数据包括：

### 个人信息 <a href="#personal-information" id="personal-information"></a>

* 您的电子邮件地址（用于电子邮件验证、账户管理以及您与 Bitwarden 之间的交流）
  * 电子邮件地址是否经过验证
* 您的名字（_仅如果在创建账户时有提供_）
* **Bitwarden 生成**的特定于设备的 GUID（有时称为_设备 ID_，用于在新设备登录到密码库时向您发出警告）

### 计费/订阅 <a href="#billing-subscription" id="billing-subscription"></a>

* 高级订阅状态和续费日期
* 账单历史
* 记录的付款方式的最后 4 位数字、卡类型和到期日期
  * 任何现有的帐户信用额度

### 组织信息 <a href="#organization-information" id="organization-information"></a>

* 组织名称
  * 组织的企业名称（可用时）
* 组织类型和计划信息，包括：
  * 组织可用的功能
  * 续费周期
  * 席位数量
* 组织的账单电子邮件地址
* 组织所有者和管理员的电子邮件地址

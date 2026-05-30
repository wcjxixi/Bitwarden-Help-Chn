# 提供商计费

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/provider-billing/)
{% endhint %}

{% hint style="info" %}
**如果您的提供商是在 2024 年 8 月 1 日之前建立的**，则每个客户组织当前均使用在[客户组织创建](start-a-client-organization.md)期间注册的付款方式单独计费。客户组织所有者（即**不是**提供商成员​​的所有者）将能够查看计费信息。

已有的提供商将从 2024 年 10 月开始转入新的计费系统。
{% endhint %}

当您注册成为提供商时，您需要指定两个单独的最低席位数量：**最低团队席位**和**最低企业席位**。这些数量是您每月需支付的固定最低费用。

创建客户组织并配置其用户时，只要还有剩余未分配的席位，就会从您指定的席位数中提取客户用户席位，无需支付额外的月费。例如，如果您注册了 50 个企业席位，并且有 1 个企业客户组织使用了 25 个席位，则您可以向该组织或任何企业客户组织添加额外的 25 个企业席位，无需支付额外的月费。

可以随时向客户组织添加超过您指定的最低席位数量的席位，这将：

* 在管理客户组织的席位数量或创建新客户组织时，会列为**已购买的附加席位**。
* 自动添加到您的在下一个计费周期的账单中。

{% hint style="info" %}
作为提供商，您必须按照下一章节所述主动管理客户组织的席位数量。由提供商管理的客户组织在达到分配的席位总数后不会自动添加用户席位，因此请定期检查，以确保客户分配的席位数量满足其需求。
{% endhint %}

## 管理席位 <a href="#manage-seats" id="manage-seats"></a>

要在客户组织中添加或删除席位，请使用 **≡** 选项菜单然后选择**管理订阅**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5azlW7UdPa9zT23P9Iou6B/13bc3905d44745494afac3f847d87ff2/2024-12-05_16-14-43.png?w=1031&#x26;fm=avif" alt=""><figcaption><p>添加客户组织席位</p></figcaption></figure></div>

如果您向客户组织**添加**席位**超出了**指定的团队版最低席位或企业版最低席位，则将在您的下一次账单中按比例收取相应费用。

如果您从客户组织中**移除**席位，从而**回落至**指定的团队版最低席位或企业版最低席位，则超出最低席位的附加席位的配置费用将在下一个计费周期自动从您的账单中扣除。

## 查看计费信息 <a href="#view-billing-information" id="view-billing-information"></a>

{% hint style="success" %}
只有提供商管理员才能查看其客户组织的计费信息。客户组织的所有者在 Admin Console 中导航到其**计费** → **订阅**界面时，将显示以下内容：

<img src="../../.gitbook/assets/Managed client billing.png" alt="" data-size="original">
{% endhint %}

### 订阅 <a href="#subscription" id="subscription"></a>

从**计费** → **订阅**页面，您可以查看您正在支付的团队版和企业版席位总数、每个席位的费率以及下次收费的日期。

### 计费历史记录 <a href="#billing-history" id="billing-history"></a>

从**计费** → **计费历史记录**页面，您可以下载每个计费周期的 PDF 账单以及包含已分配席位的按客户划分的 .csv 文件。

## 更多信息 <a href="#more-information" id="more-information"></a>

### 合作伙伴计划 <a href="#partner-program" id="partner-program"></a>

Bitwarden 对任何团队版和企业版组织（包括为经销商或 MSP 员工创建的任何团队版和企业版组织）中管理的累积席位提供 MSP 激励措施。如需了解有关 MSP 计划的更多信息，请[联系](https://bitwarden.com/contact/)销售人员。

### 客户支持 <a href="#customer-support" id="customer-support"></a>

所有 MSP 都会获得我们 24/7 客户支持团队的优先支持。[联系我们](https://bitwarden.com/contact/)获取支持。

# 查看 & 更新计费详细信息

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/update-billing-info/)
{% endhint %}

计费信息**只能从 Bitwarden 网页 App** 更新。取决于您是更新[个人账户计费信息](update-your-billing-information.md#update-billing-for-individual-premium-subscriptions)还是更新[组织计费信息](update-your-billing-information.md#update-billing-for-organizations)，此步骤会有所不同。

不确定您使用的是哪个方案吗？对于个人用户，检查**设置** → **订阅**页面。如果您拥有管理控制台的访问权限，那么您就是某个组织的所有者或管理员。作为[所有者](../admin-console/manage-members/member-roles.md#default-roles)，您可以前往**计费** → **订阅**页面找您的方案。

{% hint style="info" %}
个人版订阅和组织版订阅是分开计费的，因此更新其中一个不会自动更改另一个。例如，如果您拥有一个高级版账户并隶属于一个家庭版组织，更新您的高级版订阅的[付款方式](payment-methods.md)不会影响组织的计费。
{% endhint %}

## 更新个人高级版订阅的计费信息 <a href="#update-billing-for-individual-premium-subscriptions" id="update-billing-for-individual-premium-subscriptions"></a>

要查看您的个人订阅的计费信息；

1、从 Bitwarden 网页 App 中，前往**设置** → **订阅**：

2、选择**付款详细信息**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1VADjEEgyXqp4RxGTJE5pn/be179fbba8bb435accfb26c1f0c75ea3/Premium_payment_method.png?w=1264&#x26;fm=avif" alt=""><figcaption><p>个人版订阅付款详细信息</p></figcaption></figure></div>

3、在此页面上，您可以查看或选择：

* **更改付款方式**，以编辑在您的订阅续费时自动扣款的[付款方式](payment-methods.md)。
* **添加信用额度**，以通过 PayPal 或 Bitcoin 来购买[账户信用额度](payment-methods.md#account-credit)。可用的信用额度将自动用于抵扣您的下一笔付款。

选择**订阅**选项卡，了解更多关于您的下次扣款信息、添加[附件](../password-manager/your-vault/vault-items/file-attachments.md)存储空间或[取消订阅](cancel-a-subscription.md#cancel-a-personal-subscription)。前往**计费历史**选项卡，查看过往交易记录以及下载[账单](invoices-and-receipts.md)。

{% hint style="danger" %}
如果我们无法处理您的[续费](password-manager/premium-renewal.md)，您的订阅将降级为免费版方案。要解决此问题，请更新您的付款方式或直接支付未支付的[账单](invoices-and-receipts.md#review-invoices)。如果您的账户仍然无法恢复为付费版订阅，请[联系我们](https://bitwarden.com/contact/)。
{% endhint %}

## 更新组织计费信息 <a href="#update-billing-for-organizations" id="update-billing-for-organizations"></a>

只有[所有者](../admin-console/manage-members/member-roles.md#default-roles)才能查看或更新组织的计费信息。登录 Bitwarden 网页 App，然后打开管理控制台。从导航中选择**计费**，可以找到组织的大部分计费详细信息。

{% hint style="success" %}
至少指定一名额外的所有者，以便在当前所有者不可用时保持对计费和订阅详细信息的访问权限。
{% endhint %}

### 付款方式和计费地址 <a href="#payment-method-and-billing-address" id="payment-method-and-billing-address"></a>

要访问您的组织的计费详细信息：

1、从 Bitwarden 网页 App 中，打开管理控制台。

2、前往**计费** → **付款详细信息**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1ueaSUjVlMBXtjHroCB4Kw/2ba89898e32b100674d749499dd5a647/Payment_details_for_organizations.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>组织的付款详细信息</p></figcaption></figure></div>

3、在此页面上，您可以查看或选择：

* **更改付款方式**，编辑在您的订阅续费时自动扣款的[付款方式](payment-methods.md)。
* **编辑计费地址**，更改与您的订阅关联的计费地址，包括适用的[增值税 (VAT) 或商品和服务税 (GST) 号码](tax-calculation.md#vat)。
* **添加信用额度**，通过 PayPal 或 Bitcoin 来购买[账户信用额度](payment-methods.md#account-credit)。可用的信用额度将用于自动抵扣您的下一笔付款。

{% hint style="danger" %}
如果我们无法处理您的[组织续费](organization-renewal.md)，您的订阅将降级为免费版方案。要解决此问题，请更新您的付款方式或直接支付未支付的[账单](invoices-and-receipts.md#review-invoices)。如果您的账户仍然无法恢复为付费版订阅，请[联系我们](https://bitwarden.com/contact/)。
{% endhint %}

### 订阅席位 <a href="#subscription-seats" id="subscription-seats"></a>

前往**计费** → **订阅**以管理您组织的[订阅席位](manage-subscription-seats-in-your-organization.md#manually-add-or-remove-seats)。从这里，您可以调整付费席位的数量或为 Password Manager 和 Secrets Manager [设置席位限制](manage-subscription-seats-in-your-organization.md#set-a-seat-limit)。

### 计费电子邮箱 <a href="#billing-email" id="billing-email"></a>

存档的计费电子邮箱会发送有关您的订阅的重要通知，例如即将到来的续费提醒或未支付的账单。要编辑计费电子邮箱：

1、从 Bitwarden 网页 App 中，打开管理控制台。

2、前往**设置** → **组织信息**。

3、在**计费电子邮箱**中输入正确的地址：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3htbOdK0AbMMEfQgKhB3qd/68136527561739f8819e28e02d3c9bdb/Edit_billing_email.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>编辑计费电子邮箱</p></figcaption></figure></div>

4、选择**保存**。

{% hint style="success" %}
您组织的计费电子邮箱的持有人可以[联系我们](https://bitwarden.com/contact/)获取计费协助，包括：

* 向订阅中添加或移除信用卡。
* 更改组织的计费电子邮箱。
* 咨询存档的账单和计费信息。
* 在月度与年度计费周期之间切换（如果适用于您的组织）。
* 请求方案升级、降级、取消或订阅席位调整。

他们仅凭借持有的该电子邮箱地址，**无法**请求[组织删除](delete-an-account-or-organization.md#delete-an-organization)，也无法获取当前组织所有者的身份，或者请求将任何用户的角色提升为所有者。
{% endhint %}

### 组织名称 <a href="#organization-name" id="organization-name"></a>

组织的名称会打印在发票上，并在整个 Bitwarden App 中可见。要更改您的组织名称：

1、从 Bitwarden 网页 App 中，打开管理控制台。

2、前往**设置** → **组织信息**。

3、在**组织名称**中输入正确的名称：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2dsI9GDfEb4c7Uu9mk5XfS/358d7939989b8bb86abde23b62b8c758/Edit_organization_name.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>编辑组织名称</p></figcaption></figure></div>

4、选择**保存**。

### 取消订阅 <a href="#cancel-subscription" id="cancel-subscription"></a>

只有所有者可以[取消组织的订阅续订](cancel-a-subscription.md#cancel-an-organization-subscription)。

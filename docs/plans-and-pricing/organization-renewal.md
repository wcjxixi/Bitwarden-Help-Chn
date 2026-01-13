# 组织续费

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/organization-renewal/)
{% endhint %}

组织订阅按年或按月自动续订。组织所有者可以通过从网页 App 管理控制台导航到组织的**计费** → **订阅**界面，查看续订日期：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7MT9lfZZDTOQOBmnrLGceN/1ac8c615153e35250d15ce3921148cfe/2024-12-04_10-33-12.png?_a=DAJCwlWIZAAB" %}
组织订阅视图
{% endembed %}

随着续订日期的临近，Bitwarden 建议您通过导航至组织**计费** → **付款方式**来验证您的付款方式。如需更新付款方式，请参阅[更新计费信息](update-your-billing-information.md#update-billing-information-for-organizations)。

{% hint style="danger" %}
如果我们无法处理您的付款方式，或者您取消了您的订阅，您的组织将被禁用。Bitwarden  Cloud 客户，在您的[许可证](../self-hosting/licensing-on-premise.md#organization-license)到期和您的组织被禁用之间有七天的宽限期，对于**自托管客户**，则有 60 天的宽限期。无论哪种情况，被禁用的组织将导致以下结果：

**组织拥有的密码库项目**

[所有者](../admin-console/manage-members/member-roles.md)将保留对[已共享密码库项目](../password-manager/organization-members/sharing.md)的访问权限，但所有其他用户将无法访问这些项目。组织密码库项目和现有[集合](../admin-console/manage-shared-items/collections/about-collections.md)**不会被删除**。

**组织用户**

用户和现有的[群组](../admin-console/manage-members/groups.md)**不会从组织中移除**。[重新启用](organization-renewal.md#re-enabling-a-disabled-organization)您的组织后，用户无需执行任何操作。
{% endhint %}

## 重新启用已禁用的组织 <a href="#re-enabling-a-disabled-organization" id="re-enabling-a-disabled-organization"></a>

如果您的云托管组织被禁用，在管理控制台**计费** → **订阅**页面上支付未支付的账单后，将自动恢复服务。

如果您遇到任何问题，请使用主题 **Disabled Subscription Organization** [联系我们](https://bitwarden.com/contact/)。Bitwarden 团队将手动重新启用您的组织，并与应收账款团队合作提供进一步的计费协助。

如果您的自托管组织被禁用，请从您的云托管 Bitwarden 组织密码库下载新的许可证文件。下载后，打开您的自托管网页密码库，然后在管理控制台**计费** → **订阅**页面更新许可证。

# 组织续费

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/organization-renewal/)
{% endhint %}

组织订阅按年或按月自动续费。组织[所有者](../../admin-console/manage-members/member-roles.md#default-roles)可以从网页 App Admin Console，导航到组织的**计费** → **订阅**页面来查看续费日期：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7MT9lfZZDTOQOBmnrLGceN/1ac8c615153e35250d15ce3921148cfe/2024-12-04_10-33-12.png?w=1175&#x26;fm=avif" alt=""><figcaption><p>组织订阅</p></figcaption></figure></div>

当您的续费日期临近时，Bitwarden 建议您前往**计费** → **付款方式**来确认您的付款方式是否为最新。了解如何[更新您的计费信息](../update-your-billing-information.md)。

{% hint style="warning" %}
如果我们无法处理您的付款方式，或者您取消了订阅，您的组织将被停用。Bitwarden 云端客户在[许可证](../../self-hosting/licensing-on-premise.md#organization-license)到期后有 7 天的宽限期，在此期间组织不会被停用。对于**自托管客户** ，宽限期为 60 天。无论哪种情况，组织被停用都会导致以下情况：

#### 组织拥有的密码库项目 <a href="#organization-owned-vault-items" id="organization-owned-vault-items"></a>

[所有者](../../admin-console/manage-members/member-roles.md)将继续拥有对[共享密码库项目](../../password-manager/organization-members/sharing.md)的访问权限，但所有其他用户将失去对这些项目的访问权限。组织密码库项目和现有[集合](../../admin-console/manage-shared-items/collections/about-collections.md)**不会被删除**。

#### 组织成员 <a href="#organization-members" id="organization-members"></a>

成员和现有[群组](../../admin-console/manage-members/groups.md)**不会从组织中移除**。组织被[重新启用](organization-renewal.md#re-enabling-a-disabled-organization)后，成员无需采取任何行动。
{% endhint %}

## 重新启用停用的组织 <a href="#re-enabling-a-disabled-organization" id="re-enabling-a-disabled-organization"></a>

如果您的云端托管组织被停用，在 Admin Console 的**计费** → **订阅**页面支付未结账单后，即可自动恢复服务。

如果您遇到任何问题，请以主题 **Disabled Subscription Organization** [联系我们](https://bitwarden.com/contact/)。Bitwarden 团队将手动重新启用您的组织，并与应收账款团队合作，为您提供进一步的计费协助。

如果您的自托管组织已被停用，请从云端托管的 Bitwarden 组织密码库下载新的许可证文件。下载后，打开您的自托管网页密码库，然后在管理控制台的**计费** → **订阅**页面上[更新许可证](../../self-hosting/licensing-on-premise.md#shou-dong-geng-xin)。

# 组织续费

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/organization-renewal/)
{% endhint %}

组织订阅基于年或月自动续订。您可以从[网页密码库](https://vault.bitwarden.com/)通过导航到组织**设置** → **订阅**，来检查您的续订日期。

随着您的续订日期的临近，Bitwarden 建议您通过导航到组织**设置** → **计费**来验证付款方式。有关更新您的付款方式的帮助，请参阅[更新您的计费信息](update-your-billing-information.md)。

{% hint style="warning" %}
如果我们无法处理您的付款方式，或者您取消了您的订阅，您的组织将被禁用。对于**自托管客户**，在您的[许可证](../self-hosting/licensing-for-paid-features.md#organization-license)到期和您的组织被禁用之间有 2 个月的宽限期。在任一情况下，被禁用的组织将导致以下结果：

**组织拥有的密码库项目**

[所有者](../admin-console/user-management/member-roles-and-permissions.md)将保留对[已共享密码库项目](../organizations/sharing.md)的访问权限，但所有其他用户将无法访问这些项目。组织密码库项目和现有[集合](../organizations/collections.md)**不会被删除**。

**组织用户**

用户和现有的[群组](../organizations/groups.md)**不会从组织中移除**。[重新启用](organization-renewal.md#re-enabling-a-disabled-organization)您的组织后，用户无需执行任何操作。
{% endhint %}

## 重新启用已禁用的组织 <a href="#re-enabling-a-disabled-organization" id="re-enabling-a-disabled-organization"></a>

如果您的云托管组织被禁用，请使用主题 **Disabled Organization** [联系我们](https://bitwarden.com/contact/)。 Bitwarden 团队将手动重新启用您的组织，并与应收账款团队合作以获得任何进一步的计费帮助。

如果您的自托管组织被禁用，请从您的云托管 Bitwarden 组织密码库下载新的许可证文件。下载后，打开您的自托管网页密码库并从组织**设置** → **订阅**页面更新许可证：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6BMl40XY4F6eYF22Ztngwu/5e445c5410c7ea4cca4322d11f820c2c/update-license.png?fm=webp&h=1296&q=50&w=2040" %}
更新您的自托管许可证
{% endembed %}

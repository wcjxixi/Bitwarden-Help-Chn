# 将项目转移到组织

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/transfer-ownership/)
{% endhint %}

您的组织激活[集中化组织所有权](../../admin-console/oversight-visibility/enterprise-policies.md#centralize-organization-ownership)策略后，您可能会在 Bitwarden 浏览器扩展中被要求将您的项目转移到组织。通过此策略，您的组织要求所有项目都归组织拥有，以确保安全性和合规性。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1rhoCL30l2gE2FAPxmfbU4/4edb33dbe95f231924d6b69571eb8df4/2026-04-08_16-42-27.png?w=945&#x26;fm=avif" alt=""><figcaption><p>将项目转移到组织</p></figcaption></figure></div>

如果您被提示转移项目，您拥有两个选择：

* **接受转移**：接受以将您的项目转移到组织，这将把您的项目从「**我的密码库**」移动到一个名为「**我的项目**」的新位置。与集合不同，「[我的项目](my-items.md)」是您用来存储不需要与其他成员共享的项目的地方。转移完成后：
  * 已转移的项目可以在「**我的项目**」中找到，它们仅直接与您共享，但组织可见并被组织拥有。
  * 您应该开始在「**我的项目**」中保存不需要共享的新项目，因为您的旧的「**我的密码库**」位置将不再可用。
* **拒绝并退出**：如果您需要在转移之前将个人项目移出您的密码库，您可以拒绝将项目转移到组织，**但您将立即失去组织共享的项目的访问权限，以及任何活跃的组织功能**。如果您决定这样做，推荐的工作流程如下：
  1. [导出您的项目](../import-and-export/export-vault-data.md)，然后从已下载的文件中移除可能属于组织的项目。
  2. 将整理好的文件（应仅包含您的个人项目）导入到个人 Bitwarden 账户。
  3. 在您的组织账户中，删除您转移到个人账户的项目，以防止它们被转移到组织。
  4. 联系组织管理员以获取对已恢复组织的访问权限，这次请**接受转移**。
  5. 删除已下载的导出文件。

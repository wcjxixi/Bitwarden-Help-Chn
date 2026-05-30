# 自动确认

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/automatic-confirmation/)
{% endhint %}

默认情况下，被邀请加入 Bitwarden 组织的用户在接受邀请后，必须[由管理员进行确认](user-management.md#confirm)。「确认」是完成三步入职流程的关键步骤，该流程旨在促进组织及其成员之间端到端加密的项目共享。

如果不想让管理员手动确认每个加入组织的用户，企业组织可以选择设置用户自动确认。

要有资格使用自动确认功能：

* **由您的 Bitwarden 团队添加**：要获得此自动化功能的访问权限，Bitwarden 支持团队需要将其添加到您的组织中。第一步是[联系我们](https://bitwarden.com/contact/)。
* **单一组织策略将扩展到所有角色**：[单一组织策略](../oversight-visibility/enterprise-policies.md#single-organization)必须启用，并且所有成员（包括通常不受该策略约束的所有者和管理员）都必须遵守该策略。
* **没有紧急访问**：为了降低使用自动确认的风险，将移除您组织中所有成员的紧急访问。使用紧急访问的成员将收到一封邮件通知其已被停用。
* **没有配置提供商账户**：[提供商](../../provider-portal/provider-portal-overview.md)的成员可能不是您组织中已配置的成员。提供商仍然可以管理您的组织，但其成员不能占用您组织的席位。
* **接受潜在的安全风险**：自动确认可能会对您组织的数据构成安全风险。在使用自动确认之前，请确保您已阅读[本文中概述的风险](automatic-confirmation.md#potential-security-risks)并接受它们。

激活后，自动确认是由已解锁的浏览器扩展（属于具有**管理用户**权限的[所有者、管理员和自定义角色成员](member-roles.md)）执行的后台进程。通过下面的章节了解如何激活自动确认。

{% hint style="info" %}
当为组织启用了或停用了自动确认、每一位管理员启用了或停用了自动确认，以及某位成员被自动确认时，都会记录[事件](../oversight-visibility/event-logging/event-logs.md)。
{% endhint %}

## 启用自动确认 <a href="#turn-on-automatic-confirmation" id="turn-on-automatic-confirmation"></a>

要启用新成员的自动确认，您必须在组织层面以及您希望执行该流程的每个 Bitwarden 客户端上将其启用。

### 对于组织 <a href="#for-the-organization" id="for-the-organization"></a>

要为您的组织启用自动确认，请确保您已满足上述资格要求。当您联系了您的 Bitwarden 团队后，组织所有者将在下次登录时收到一个激活面板。

当 Bitwarden 为您的组织添加了该功能后，您还可以从 Admin Console 中的**设置** → **策略**菜单，通过[策略](../oversight-visibility/enterprise-policies.md#automatic-user-confirmation)来激活自动确认。无论哪种方式，选择**继续**即可为组织启用自动确认：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1ggo2uyCvldAlJcOxAmGdv/eabe1eb2c5a82731268d6b3486fbc3d5/2026-02-05_10-43-27.png?w=1134&#x26;fm=avif" alt=""><figcaption><p>新用户自动确认</p></figcaption></figure></div>

### 对于每位管理员 <a href="#for-each-administrator" id="for-each-administrator"></a>

为组织启用后，具有**管理用户**权限的每一位[所有者、管理员和自定义角色成员](member-roles.md)将**在浏览器扩展**中收到一个激活面板，邀请他们为该客户端启用自动确认。

关闭了此对话框的管理员可以从浏览器扩展的**设置** → **管理员**菜单中启用或停用自动确认。无论哪种方式，选择**启用**以开始自动确认：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/18MR4NrPqPFWRW7W5oqFzW/40422afa9db8a695213a80944d427589/2026-02-05_11-02-16.png?w=867&#x26;fm=avif" alt=""><figcaption><p>启用自动确认</p></figcaption></figure></div>

为了让成员能够自动确认，至少需要由一位[所有者、管理员或相关自定义角色成员](member-roles.md)启用此功能。自动确认进程会在每一个选择启用此功能的已解锁的浏览器扩展客户端的后台运行。

## 潜在的安全风险 <a href="#potential-security-risks" id="potential-security-risks"></a>

在启用自动确认之前，**确保您了解使用此功能可能带来的潜在风险**。

解密您组织的数据需要用户完成一个三步（邀请 → 接受 → 确认）的入职流程，以[促进加密密钥的安全共享](../../security/bitwarden-security-whitepaper.md#sharing-data-between-users)并维护端到端加密环境。在此流程中，手动确认充当最后一道保护措施，确保只有有意访问组织数据的成员才能访问；如果未经授权的人员或恶意攻击者接受了邀请，他们会在确认步骤中被捕获并拒绝，以防止未经授权的访问。

对 Bitwarden 服务器（无论是自托管还是云托管）使用的数据库具有不受限制的访问权限的攻击者，可以伪造加入您组织的邀请并接受它。由于自动确认在运行中，管理员无法通过人工干预来发现并拒绝此类攻击者的访问。

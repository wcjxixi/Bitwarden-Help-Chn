# 提供商用户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/provider-users/)
{% endhint %}

## 入职提供商用户 <a href="#onboard-provider-users" id="onboard-provider-users"></a>

为确保您的客户组织的安全管理，Bitwarden 采用 3 步流程来入职新的提供商成员​​，[邀请](provider-users.md#invite) → [接受](provider-users.md#accept) → [确认](provider-users.md#confirm)。

### 邀请 <a href="#invite" id="invite"></a>

要邀请用户加入您的提供商：

1、登录到 Bitwarden，然后使用产品切换器打开提供商门户：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4xn04Sj9u8n73TPxZUWi5f/dac0d56f47a05e2d8b28754e997a1391/2025-02-25_15-16-00.png?w=1080&#x26;fm=avif" alt=""><figcaption><p>产品切换器 - 提供商门户</p></figcaption></figure></div>

2、打开**管理** → **成员**视图，然后选择 <i class="fa-plus">:plus:</i>**邀请用户**按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6E5GA111xdiHHkA0gb5LtG/5e5b5fddb5911e1b2ed468c1d49134ad/2024-12-05_09-27-45.png?w=1031&#x26;fm=avif" alt=""><figcaption><p>邀请提供商用户</p></figcaption></figure></div>

3、在邀请用户面板上：

* 输入新用户用来接收邀请的**电子邮箱**地址。您可以通过逗号分隔电子邮箱地址，一次最多添加 20 个成员。
* 选择要应用于这批用户的**用户类型**。[用户类型](provider-users.md#provider-user-types)将决定这些用户对提供商的访问权限。这**两种用户类型**都能够完全管理任何[客户组织](start-a-client-organization.md)。

4、单击**保存**以邀请这些指定的用户加入提供商。

{% hint style="info" %}
**邀请将在 5 天后过期**，届时需要重新邀请用户。通过选择每个用户然后使用 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i>选项菜单以**重新发送邀请**来批量重新邀请用户：

<img src="https://bitwarden.com/assets/6Sx6YxDzCYoaw7qFGgMvvv/77c341b80fd47aa6865821c30a887a8c/2024-12-05_09-34-07.png?w=1031&#x26;fm=avif" alt="" data-size="original">
{% endhint %}

### 接受 <a href="#accept" id="accept"></a>

受邀用户将收到一封来自 Bitwaden 的电子邮件，邀请他们加入提供商。单击电子邮件中的链接将打开 Bitwarden 邀请窗口。使用现有的 Bitwarden 账户**登录**或**创建账户**以接受邀请：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1DlzjKAmxR82fsAMFqIBwB/ed0e704ccdea7785609b562e79310e0b/provider-accept-invite.png?w=344&#x26;fm=avif" alt=""><figcaption><p>电子邮件邀请</p></figcaption></figure></div>

### 确认 <a href="#confirm" id="confirm"></a>

要确认已接受加入您的提供商的邀请：

1、在提供商门户中，导航到**管理** → **成员**视图。

2、选中任何 `已接受` 的用户，然后使用 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i>选项菜单来 <i class="fa-check">:check:</i>**确认所选**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/IxUeScxNYYmI4y8jceC5v/ebdf3fa89abbd69fbb028e0cff8c99aa/2024-12-05_09-29-04.png?w=1031&#x26;fm=avif" alt=""><figcaption><p>确认已邀请的提供商用户</p></figcaption></figure></div>

3、在出现的面板上，验证新用户的[指纹短语](../security/encryption/account-fingerprint-phrase.md)与他们在**设置** → **我的账户**界面中找到的指纹短语是否匹配。每个指纹短语对其账户都是唯一的，这确保了在安全添加用户时多了一层最终监督。如果它们匹配，请选择**确认**。

## 离职提供商用户 <a href="#deprovision-users" id="deprovision-users"></a>

要从提供商移除用户：

1、在提供商门户中，导航到**管理** → **成员**视图。

2、选择您要从提供商中移除的用户，然后使用 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i>选项菜单来 <i class="fa-xmark">:xmark:</i>**移除**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/DC18TP9xNK1V8768meTDT/bfedb940285677f78e408294aadf5e0f/2024-12-05_09-36-46.png?w=1031&#x26;fm=avif" alt=""><figcaption><p>移除提供商用户</p></figcaption></figure></div>

## 提供商用户类型 <a href="#provider-user-types" id="provider-user-types"></a>

{% hint style="success" icon="lightbulb" %}
**正在管理客户组织的用户？**&#x62E5;有一套独立于提供商用户类型的[成员角色和访问控制](../admin-console/manage-members/member-roles.md)。
{% endhint %}

Bitwarden 提供商用户可以被授予两种用户类型之一，以管理他们对提供商的访问权限。**这两种用户类型都能够完全管理任何客户组织**。Bitwarden 强烈建议您为故障转移目的配置第二个提供商管理员角色。

您可以在[邀请](provider-users.md#invite)提供商用户时或随时从提供商门户中的**管理** → **成员**界面设置用户的类型。用户类型包括：

| 角色     | 描述                                                                                                                                                                                                                                                                                                                                        |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 服务用户   | <p>服务用户可以访问和管理所有<a href="start-a-client-organization.md">客户组织</a>，包括：</p><ul><li>创建或删除集合</li><li>将用户和用户组分配给集合</li><li>将用户分配到用户群组</li><li>创建或删除用户群组</li><li>邀请并确认新用户</li><li>管理企业策略</li><li>查看事件日志</li><li>导出组织密码库数据</li><li>管理密码重置</li><li>在<a href="provider-billing.md#about-provider-billing">提供商可用的总席位</a>范围内，为客户端组织添加或移除席位</li></ul> |
| 提供商管理员 | <p>提供商管理员管理提供商和所有客户组织的所有方面。提供商管理员可以执行上述所有操作，以及：</p><ul><li>创建新的客户组织</li><li>邀请并确认新的服务用户和提供商管理员</li><li>查看提供商事件日志</li><li>编辑提供商设置</li><li>管理计费、订阅和<a href="provider-billing.md">提供商可用的总席位</a></li></ul>                                                                                                                                    |

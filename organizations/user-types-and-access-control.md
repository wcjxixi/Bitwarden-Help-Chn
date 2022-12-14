# 用户类型和访问控制

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/user-types-access-control/)
{% endhint %}

Bitwarden 组织中的用户可以被授予各种用户类型和访问控制，以管理他们的权限和访问。当[邀请用户到您的组织](user-management.md)时，您可以设置用户类型和访问控制，或者在任何时候从您的组织的**管理** → **人员**界面进行设置：

{% embed url="https://bitwarden.com/help/images/organizations/user-types-access-control.png" %}
编辑用户类型和访问控制
{% endembed %}

## 用户类型 <a href="#user-types" id="user-types"></a>

用户类型决定了一个用户在您的组织内将拥有的权限。用户类型并不决定[他们可以访问哪些集合](user-types-and-access-control.md#access-control)，而是决定他们在您的组织的资源和工具范围内**可以获取哪些操作**。选项包括：

| 用户类型 | 权限                                                                                                                                                                       |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 用户   | <p>访问指定集合中的共享项目</p><p>从分配的集合中添加、编辑或删除项目（除非<strong>只读</strong>）</p>                                                                                                       |
| 经理   | <p>上述所有的权限，</p><p>+将用户分配给集合</p><p>+将用户群组分配给集合</p><p>+创建或删除集合</p>                                                                                                         |
| 管理员  | <p>上述所有的权限，</p><p>+将用户分配给用户群组</p><p>+创建或删除用户群组</p><p>+邀请并确认新用户</p><p>+管理企业策略</p><p>+查看事件日志</p><p>+导出组织密码库数据</p><p>+管理密码重置</p><p><strong>管理员用户自动拥有所有集合的访问权限。</strong></p> |
| 所有者  | <p>上述所有的权限，</p><p>+管理计费、订阅和集成</p><p><strong>所有者用户自动拥有所有集合的访问权限。</strong></p>                                                                                             |
| 自定义  | 允许逐个用户地对用户权限进行粒度控制，请参阅[自定义角色](user-types-and-access-control.md#custom-role)。                                                                                             |

{% hint style="info" %}
**仅所有者**可以创建新的所有者，或分配所有者类型到一个现有的用户。为了进行故障转移，Bitwarden 建议创建多个所有者用户。
{% endhint %}

### 自定义角色 <a href="#custom-role" id="custom-role"></a>

为用户选择**自定义**角色可以逐个用户地精细控制权限。自定义角色的用户拥有经理和管理员功能的配置选择能力，包括：

* 管理已分配的集合（提供以下 2 个选项）
  * 编辑已分配的集合
  * 删除已分配的集合
* 访问事件日志
* 访问导入/导出
* 访问报告
* 管理所有集合（提供以下 3 个选项）
  * 创建新的集合
  * 编辑任何集合
  * 删除任何集合
* 管理群组
* 管理 SSO
* 管理策略
* 管理用户
* 管理密码重置

{% hint style="success" %}
例如，自定义角色允许创建只能管理 SSO 配置和访问相关凭证的用户。这种情况下，此场景可做如下所示设置：

<img src="../.gitbook/assets/image (1).png" alt="" data-size="original">
{% endhint %}

## 访问控制 <a href="#access-control" id="access-control"></a>

访问控制决定了对集合的访问权限，以及每个单独集合内部的权限：

![配置访问控制选项](../.gitbook/assets/collection-access-control.png)

{% hint style="info" %}
回顾一下，[管理员和所有者](user-types-and-access-control.md#user-types)可以自动获得访问所有集合的权限。对于其他用户类型，配置访问控制将决定哪些集合可以在他们的个人密码库和客户端应用程序（浏览器扩展、移动端等等）中随时访问。管理员和所有者仍然能够从组织密码库中访问「未分配」的集合。
{% endhint %}

| 访问控制               | 描述                                                                     |
| ------------------ | ---------------------------------------------------------------------- |
| **此用户可以访问和修改所有项目** | <p>授予用户对所有集合的访问权限，以及修改其中存储的密码库项目的能力。</p><p></p><p>选择此选项将折叠集合选择部分。</p>  |
| **此用户只能访问选定的集合**   | <p>仅授予用户对选定集合的访问权限，以及对每一个集合的粒度访问控制权限。</p><p></p><p>选择此选项将展开集合选择部分。</p> |

### 粒度访问控制 <a href="#granular-access-control" id="granular-access-control"></a>

如果您选择了**此用户只能访问选定的集合**，请选择要为其提供访问权限的集合。对于每一个集合，您还可以配置以下选项：

| 选项       | 描述                                                                                                                                                                         |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **隐藏密码** | <p>防止用户查看或复制所有密码、TOTP 种子以及隐藏的自定义字段。启用<strong>隐藏密码</strong>的用户只能通过自动填充使用集合中的项目。</p><p></p><p><strong>隐藏密码</strong>可防止轻松复制​​和粘贴隐藏的项目，但它并不能完全阻止用户访问此信息。像对待任何共享凭证一样对待隐藏密码。</p> |
| **只读**   | 防止用户添加、编辑或删除集合中的项目。具有**只读**访问权限的用户仍然可以查看和使用所有密码、TOTP 种子以及隐藏的自定义字段。                                                                                                         |

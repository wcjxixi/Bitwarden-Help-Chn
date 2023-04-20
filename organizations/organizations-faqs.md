# 组织常见问题

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/org-faqs/)
{% endhint %}

本文包含了关于**组织**的常见问答（FAQ）。

有关**组织**的更多高级信息，请参阅以下文章：

* [关于组织](organizations.md)
* [关于集合](collections.md)
* [关于群组](groups.md)

## 组织通用 <a href="#organizations-general" id="organizations-general"></a>

### 问：组织和高级会员之间有什么区别？ <a href="#q-whats-the-difference-between-organizations-and-premium" id="q-whats-the-difference-between-organizations-and-premium"></a>

**答：**组织支持从组织到组织用户的安全共享。

高级个人计划可解锁高级密码安全和管理功能，包括高级 2FA 选项、Bitwarden 验证器（TOTP）、加密文件附件等。高级个人计划不包括安全数据共享。

付费组织（家庭、团队或企业）自动为组织中已注册的每个用户提供高级功能（高级 2FA 选项、Bitwarden 验证器等）。

## 组织管理 <a href="#organization-administration" id="organization-administration"></a>

### 问：组织的所有者不再在公司任职，可以创建新的所有者吗？ <a href="#q-my-organizations-owner-is-no-longer-with-the-company-can-a-new-owner-be-created" id="q-my-organizations-owner-is-no-longer-with-the-company-can-a-new-owner-be-created"></a>

**答：**只有组织的所有者才能创建新的所有者或将所有者分配给现有用户。为了进行故障转移，Bitwarden 建议创建多个所有者用户。如果您的唯一所有者离开了公司，请[与我们联系](https://bitwarden.com/contact)。

### 问：我已邀请用户，但他们看不到共享的项目，我该怎么办？ <a href="#q-i-have-invited-users-but-they-cannot-see-shared-items-what-do-i-do" id="q-i-have-invited-users-but-they-cannot-see-shared-items-what-do-i-do"></a>

**答：**被邀请的用户会收到一封邮件，询问他们加入本组织。首先，确保他们已经接受了邀请。如果他们接受了邀请，管理员或所有者应导航到**管理** → **人员**，将鼠标悬停在该用户上，打开齿轮下拉菜单，然后选择**确认**。

### 问：我的组织可以审计哪些事件？ <a href="#q-what-events-are-auditing-for-my-organization" id="q-what-events-are-auditing-for-my-organization"></a>

**答：**有关 Bitwarden 事件日志中包含的内容的完整列表，请参阅[事件日志](event-logs.md)。

### 问：我可以防止用户自我注册到我的组织吗？ <a href="#q-can-i-prevent-users-from-self-registering-into-my-organization" id="q-can-i-prevent-users-from-self-registering-into-my-organization"></a>

如果你是自托管，请[配置环境变量](../self-hosting/configure-environment-variables.md) `globalSettings__disableUserRegistration=` 为 `true`，以防止用户通过注册页面注册账户。配置后，组织管理员或所有者必须邀请用户才能在自托管的实例上注册账户。

### 问：如何更改组织名称？ <a href="#q-how-do-i-change-the-name-of-my-organization" id="q-how-do-i-change-the-name-of-my-organization"></a>

**答：**要更改组织名称：

1. 在[网页密码库](https://vault.bitwarden.com/)中，打开您的组织。
2. 导航到组织的 **⚙️设置**页面。
3. 编辑**组织名称**字段然后选择**保存**按钮。

**如果您是自托管**，您还需要：

1. 导航到 **⚙️设置 → 订阅**页面。
2. 选择**下载许可证**按钮来下载更新了组织名称的许可证。
3. [上传新的许可证](../self-hosting/licensing-for-paid-features.md#organization-license)到您的自托管服务器。

### 问：如何升级我的免费组织？ <a href="#q-how-do-i-upgrade-my-free-organization" id="q-how-do-i-upgrade-my-free-organization"></a>

**答：**如果您想升级到付费组织以解锁[许多附加功能](../plans-and-pricing/about-bitwarden-plans.md)，请导航到您的组织**设置** → **订阅**视图，然后选择**升级计划**按钮：

{% embed url="https://bitwarden.com/help/images/plans-and-pricing/upgrade-org.png" %}
升级您的组织
{% endembed %}

## 组织共享 <a href="#sharing-with-an-organization" id="sharing-with-an-organization"></a>

### 问：如何「取消共享」组织中的项目？ <a href="#q-how-do-i-unshare-an-item-from-my-organization" id="q-how-do-i-unshare-an-item-from-my-organization"></a>

**答：**要取消共享一个项目：

1. 导航到您的组织密码库，并从您要克隆的项目的齿轮下拉菜单中选择**克隆**，将项目克隆到您的个人密码库。只有用户类型为**管理员**或更高级别的用户才能通过更改**所有权**设置将项目克隆到他们的个人密码库。
2. 从同一齿轮下拉菜单中选择**删除**，从组织密码库中删除该项目。

或者，您也可以通过将项目移动到具有更高访问控制限制的其他集合来取消共享项目。

### 问：如何向组织用户隐藏密码？ <a href="#q-how-do-i-hide-a-password-from-my-organizations-users" id="q-how-do-i-hide-a-password-from-my-organizations-users"></a>

**答：**在添加新用户或编辑现有用户时，使用**访问控制**部分中的**隐藏密码**选项，以对他们隐藏指定集合的密码和隐藏字段。有关更多信息，请参阅[访问控制](../admin-console/user-management/member-roles-and-permissions.md)。

### 问：我离开后，移动到组织的项目是否会被保留？ <a href="#q-does-an-item-i-share-with-the-organization-stay-after-i-leave" id="q-does-an-item-i-share-with-the-organization-stay-after-i-leave"></a>

答：是的！当用户与组织共享项目时，组织将获得该项目的所有权。即使用户离开组织或删除其帐户，该项目仍将保留在组织密码库中。

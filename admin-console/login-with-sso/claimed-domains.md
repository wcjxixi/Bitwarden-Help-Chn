# 声明域名

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/domain-verification/)
{% endhint %}

> **\[译者注]**：从版本 2025.3.0 开始，之前的「域名验证」(Domain verification) 已改名为「声明域名」(Claimed domains)

企业客户可以声明其组织所拥有的域名（如 `mycompany.com`）的所有权。

声明域名支持以下功能：

* **声明成员账户**：当您声明一个域名时，任何拥有与此域名匹配的电子邮箱地址（如 `jdoe@mycompany.com`）的组织成员账户也将被您的组织声明。被声明的成员账户在功能上归组织所有，会限制用户进行某些账户操作，并允许管理员直接删除账户，包括删除该用户的个人密码库，而不是仅将其从组织中移除。[了解更多](../user-management/claimed-accounts.md)。
* **为成员提供更便捷的 SSO**：当您声明一个域名时，任何拥有与域名匹配的电子邮箱地址（如 `jdoe@mycompany.com`）的组织成员账户都将在 SSO 过程中自动绕过要求他们输入 [SSO 标识符](../../login-with-sso/using-login-with-sso.md#get-your-organization-identifier)的步骤。
* **自动验证成员电子邮箱**：当您声明一个域名时，任何组织成员账户，只要其电子邮箱地址与域名（如 jdoe@mycompany.com）匹配，在入职时就会[自动验证其电子邮箱](../../your-vault/general-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)。

域名可以通过有效且对 Bitwarden 唯一的 DNS TXT 记录来声明。

## 声明域名 <a href="#claim-a-domain" id="claim-a-domain"></a>

要声明某个域名，Bitwarden 必须确认以下信息：

* 没有其他组织验证该域名。
* 您的组织拥有此域名的所有权。

Bitwarden 将使用 DNS TXT 记录来验证域名声明。该 DNS TXT 记录必须始终保持激活状态并可用，因为 Bitwarden 将不断对其进行检查。

要声明域名：

1、登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**设置** → **声明域名**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6WJAs5AXufz8zSiVjEp5aA/8d9f4576f877ce74d6553430801070a9/2025-01-14_09-56-53.png?_a=DAJCwlWIZAAB" %}
声明域名
{% endembed %}

3、在**声明域名**界面，您将看到一个活动域名的列表，以及状态检查和选项。如果您没有活动域名，请选择**新增域名**。

{% hint style="success" %}
如果是首次声明域名，[单一组织策略](../../organizations/enterprise-policies.md#single-organization)将在声明工作流程中自动激活。如果您在 2025.3.0 版本发布之前已经声明了一个域名，则无需遵守此要求。
{% endhint %}

4、在弹出窗口中，输入**域名名称**。

{% hint style="info" %}
确保文本条目的格式中**不要**包含 `https://` 或 `www.`。
{% endhint %}

5、复制 **DNS TXT 记录**然后将其添加到您的域名中。

6、选择**声明域名**。

## 管理您的域名 <a href="#managing-domains" id="managing-domains"></a>

您可以从**声明域名**页面管理和查看您的域名的状态。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1sgIhVJzsRce0VyNIvH1ze/9646e4b0d433efa53f5d1b29a43134df/image.png?_a=DAJCwlWIZAAB" %}
已验证的域名
{% endembed %}

如果要编辑或删除域名，请选择域名或位于域名右侧的 **≡** 菜单。

**≡** 菜单提供了用于复制 DNS TXT 记录的附加选项，以及在新域名设置期间自动验证不成功时手动验证域名的选项。

域名具有 `UNVERIFIED` 或 `VERIFIED`（未验证或已验证）两种状态。

{% hint style="danger" %}
Bitwarden 将在前 72 小时内尝试声明域名 3 次。如果该域名在第 3 次尝试后的 7 天内仍未通过验证，该域名将从您的组织中被移除。
{% endhint %}

域名设置活动将记录在组织事件日志中。要查看事件，请在管理控制台中导航到**报告** → **事件日志**。

## 域名被声明后 <a href="#once-your-domain-is-claimed" id="once-your-domain-is-claimed"></a>

您的域名被声明和验证后，您的组织就可以获得以下访问权限：

### 声明成员账户 <a href="#claimed-member-accounts" id="claimed-member-accounts"></a>

当您声明一个域名时，任何拥有与此域名匹配的电子邮箱地址（如 `jdoe@mycompany.com`）的组织成员账户也将被您的组织声明。被声明的成员账户在功能上归组织所有，这会导致账户的工作方式发生一些关键性的变化：

#### 删除组织管理的账户 <a href="#org-managed-account-deletion" id="org-managed-account-deletion"></a>

组织管理员可以直接删除已声明的成员账户，而不是只将他们从组织中移除。所有者和管理员可以在管理控制台的**成员**页面上使用 **≡**&#x83DC;单删除已声明的账户：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6HUnGTfMstF4IasZcKBfdi/0d2dbd328ba4a006611576e7d91c70df/2025-01-14_10-45-56.png?_a=DAJCwlWIZAAB" %}
删除已声明的账户
{% endembed %}

如果组织成员没有已声明的账户，则可将其从组织中**移除**。

{% hint style="info" %}
Directory Connector 和 SCIM 无法删除已声明账户，只有管理员和所有者可以通过网页 App 管理控制台执行此操作。
{% endhint %}

#### 限制账户操作 <a href="#restricted-access-to-account-actions" id="restricted-access-to-account-actions"></a>

成员账户用户将受到以下限制：

* 将他们的账户电子邮箱地址更改为其他域名（成员仍可更改电子邮箱地址中的用户名部分）。
* 离开组织。
* 清空他们的密码库。
* 删除他们的账户。

### 为成员提供更便捷的 SSO <a href="#easier-sso-for-members" id="easier-sso-for-members"></a>

当您声明一个域名时，任何拥有与域名匹配的电子邮箱地址（如 `jdoe@mycompany.com`）的组织成员账户都将在 SSO 过程中自动绕过要求他们输入 [SSO 标识符](../../login-with-sso/using-login-with-sso.md#get-your-organization-identifier)的步骤。

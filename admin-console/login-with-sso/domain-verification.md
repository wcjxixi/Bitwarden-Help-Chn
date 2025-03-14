# 域名验证

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/domain-verification/)
{% endhint %}

企业客户可以验证其组织的域名所有权（例如 `mycompany.com`）。域名验证将允许组织声明一个域名，支持自动 SSO 操作等功能，从而更轻松、更快速地登录。可以使用有效且对 Bitwarden 唯一的 DNS TXT 记录来验证域名。

域名的所有权得到验证后，具有该域名（例如 `@mycompany.com`）的用户将能够绕过 SSO 登录步骤，该步骤需要在登录期间输入 [SSO 标识符](../../login-with-sso/using-login-with-sso.md#get-your-organization-identifier)。此外，已验证域名的组织成员将在入职时[自动验证他们的电子邮箱](../../your-vault/general-faqs.md#q-what-features-are-unlocked-when-i-verify-my-email)。

## 验证域名 <a href="#verify-a-domain" id="verify-a-domain"></a>

为了验证域名所有权，Bitwarden 必须验证：

* 没有其他组织声明或验证该域名。
* 您的组织拥有域名的所有权。

为了验证域名的所有权，Bitwarden 将使用 DNS TXT 记录。该 DNS TXT 记录必须始终保持激活状态并可用，因为 Bitwarden 将不断对其进行检查。

要验证域名：

1、登录 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**设置** → **域名验证**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6WJAs5AXufz8zSiVjEp5aA/8d9f4576f877ce74d6553430801070a9/2025-01-14_09-56-53.png?_a=DAJCwlWIZAAB" %}
声明域名
{% endembed %}

3、在**域名验证**界面，您将看到一个活动域名的列表，以及状态检查和选项。如果您没有活动域名，请选择**新增域名**。

4、在弹出窗口中，输入**域名名称**。

{% hint style="info" %}
确保文本条目的格式中**不要**包含 `https://` 或 `www.`。
{% endhint %}

5、复制 **DNS TXT 记录**然后将其添加到您的域名。

6、选择**验证域名**。

## 管理域名 <a href="#managing-domains" id="managing-domains"></a>

您可以从**域名验证**页面管理和查看域名的状态。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1sgIhVJzsRce0VyNIvH1ze/9646e4b0d433efa53f5d1b29a43134df/image.png?_a=DAJCwlWIZAAB" %}
已验证的域名
{% endembed %}

如果要编辑或删除域名，请选择域名或位于域名右侧的 **≡** 菜单。

**≡** 菜单提供了用于复制 DNS TXT 记录的附加选项，以及在新域名设置期间自动验证不成功时手动验证域名的选项。

域名具有 `UNVERIFIED` 或 `VERIFIED`（未验证或已验证）两种状态。

{% hint style="danger" %}
Bitwarden 将在前 72 小时内尝试验证域名 3 次。如果该域名在第 3 次尝试后的 7 天内仍未通过验证，该域名将从您的组织中被移除。
{% endhint %}

域名设置活动将记录在组织事件日志中。要查看事件，请在管理控制台中导航到**报告** → **事件日志**。

## 登录 <a href="#login" id="login"></a>

现在您的域名已被您的组织验证了，您可以在没有 SSO 标识符的情况下登录：

1. 在您首选的 Bitwarden 客户端上打开登录页面。
2. 输入包含已验证域名的电子邮箱（例如 `@mydomain.com`），然后选择**继续**。
3. 选择**企业单点登录**。
4. 您将被重定向到您的身份提供商页面，从这里，使用您的 SSO 凭据完成登录过程。

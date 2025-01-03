# 域名验证

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/domain-verification/)
{% endhint %}

企业客户可以验证其组织的域名所有权（例如 `mycompany.com`）。域名验证将允许组织声明一个域名，支持自动 SSO 操作等功能，从而更轻松、更快速地登录。可以使用有效且对 Bitwarden 唯一的 DNS TXT 记录来验证域名。

域名的所有权得到验证后，具有该域名（例如 `@mycompany.com`）的用户将能够绕过 SSO 登录步骤，该步骤需要在登录期间输入 [SSO 标识符](../../login-with-sso/using-login-with-sso.md#get-your-organization-identifier)。

{% hint style="info" %}
域名验证适用于具有企业计划的组织。这不包括 Enterprise 2019。如果您有任何计划问题或想要升级您的计划，请联系 [Bitwarden 支持](https://bitwarden.com/contact/)。
{% endhint %}

## 验证域名 <a href="#verify-a-domain" id="verify-a-domain"></a>

为了验证域名所有权，Bitwarden 必须验证：

* 没有其他组织声明或验证该域名。
* 您的组织拥有域名的所有权。

为了验证域名的所有权，Bitwarden 将使用 DNS TXT 记录。要验证域名：

1、访问网页密码库并转到**组织**选项卡。

2、在您的组织中，选择**设置**选项卡，然后从左侧菜单中选择**域名验证**：

{% embed url="https://bitwarden.com/_gatsby/image/6016d2529b9b899fd73de565844ba44c/164894a27797d23a9f34e030d32cd12c/Screen%20Shot%202023-03-06%20at%203.02.57%20PM%20(2).webp?eu=8a8c50e4e6ccfe875b3ca9d26070356be96b03aff95637d03f30eda74efb9c8177a01a0474c37fe57f3a53dbd7e045bf31c47e6748ef82d994b94cf2be60ac5b018b5fe961b47003572ec6afb6fd53453c951c51a684c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bbdf7a4425debbfd85ab9ace6e36a94fabd5847458a822a762418185ebb28eda2e455223c29400861c7a65bc032c4b03c48322a5b5951f178598317ae396fac87a3fe19b6787be3abd431739bc3a8efbc5ec32968e7cd39ac85541a7362c311c2a23ba985&a=w%3D750%26h%3D468%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.865Z" %}
域验证
{% endembed %}

3、在**域名验证**界面，您将看到一个活动域名的列表，以及状态检查和选项。如果您没有活动域名，请选择**新增域名**。

4、在弹出窗口中，输入域名名称。

{% hint style="info" %}
确保文本条目的格式中不要包含 `https://` 或 `www.`。
{% endhint %}

5、复制 **DNS TXT 记录**然后将其添加到您的域名。

6、选择**验证域名**。

## 管理域名 <a href="#managing-domains" id="managing-domains"></a>

您可以从**域名验证**页面管理和查看域名的状态。

{% embed url="https://bitwarden.com/_gatsby/image/fbfc1bda67dd3c0210f1a9caa12417b2/54ade9a6c6415cf1fa6fa65c81c336c6/Screenshot%202023-03-07%20at%209.58.39%20AM%20copy.webp?eu=dd8d51b2e49bfc835b69f4866021623bb36955fdfe0037d56932edfb1afbcdd421a5180175937ab52b6808ded1b34bee63c77d6311bfd8d391ba4afcb961f809018409bd67b770045b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b92f2695d22086681417a94b24fc02f2eea77566ef84e500ebe6eafd5cc8cfe02d5543d9a56770744d175feb79b2a5e102716f7d400a67cab03b9423c3e3625f397c1a3001f76539cd55f87131c48baae532d0647ee9b6ca381ff7bec1d3b25ae53436b998&a=w%3D762%26h%3D146%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.638Z" %}
已验证的域
{% endembed %}

如果要编辑或删除域名，请选择域名或位于域名右侧的 **≡** 菜单。

**≡** 菜单提供了用于复制 DNS TXT 记录的附加选项，以及在新域名设置期间自动验证不成功时手动验证域名的选项。

域名具有 `UNVERIFIED` 或 `VERIFIED`（未验证或已验证）的状态。

{% hint style="info" %}
Bitwarden 将在前 72 小时内尝试验证域名 3 次。如果该域名在第 3 次尝试后的 7 天内仍未通过验证，该域名将从您的组织中被移除。
{% endhint %}

域名设置活动将记录在组织事件日志中。要查看事件：

1. 打开您的组织。
2. 选择**报告**选项卡，然后选择左侧菜单中的**事件日志**。

## 登录 <a href="#login" id="login"></a>

您的域名已被您的组织声明，现在您可以在没有 SSO 标识符的情况下登录：

1. 在您首选的 Bitwarden 客户端上打开登录页面。
2. 输入包含已声明域名的电子邮箱（例如 `@mydomain.com`），然后选择**继续**。
3. 选择**企业单点登录**。
4. 您将被重定向到您的身份提供商页面，从这里，使用您的 SSO 凭据完成登录过程。

# SSO 登录的使用

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/using-sso/)
{% endhint %}

作为 Bitwarden 的最终用户，在您[使用 SSO 登录](using-login-with-sso.md#login-using-sso)之前，您需要拥有您的[组织标识符](using-login-with-sso.md#get-your-organization-identifier)：

{% hint style="success" %}
根据您组织的设置方式，您可能还需要[将您的帐户链接到 SSO](using-login-with-sso.md#link-your-account)。如果您**已经拥有作为组织成员的 Bitwarden 帐户**，或者**您的组织不要求您使用 SSO**，则通常需要这样做。
{% endhint %}

## 获取组织标识符 <a href="#get-your-organization-identifier" id="get-your-organization-identifier"></a>

每一个 Bitwarden 组织都有一个专门用于 SSO 登录的唯一标识符。您将需要这个值才能登录，因此请询问您的经理或 Bitwarden 管理员[以获取它](saml-2.0-configuration.md#step-1-set-an-organization-identifier)。

## 使用 SSO 登录 <a href="#login-using-sso" id="login-using-sso"></a>

使用 SSO 登录所需的步骤将略有不同，具体取决于您的组织是否使用 [Key Connector](about-key-connector.md)：

{% tabs %}
{% tab title="SSO 登录 & 主密码" %}
### SSO 登录 & 主密码 <a href="#login-with-sso-and-master-password" id="login-with-sso-and-master-password"></a>

要使用 SSO 和您的主密码登录：

1、打开您的 Bitwarden 网页密码库，然后选择**企业单点登录（SSO）**按钮：

![企业 Single Sign-On 按钮](https://images.ctfassets.net/7rncvj1f8mw7/3TjmG99YArRXpsaBHH77Mt/0e4be9262c1a51be449880390ddd19f5/sso-button-lg.png)

2、输入您的**企业标识符**然后选择**登录**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2wjMPE63ZAOzLm1QOxIott/6ef80387d381bc016df9ab0181ec57f5/org-id-input.png?fm=webp&h=236&q=50&w=417" %}
组织标识符字段
{% endembed %}

{% hint style="success" %}
我们建议将此页面添加为书签，并将您的组织标识符作为查询字符串包含在内，这样您就不必每次都输入它了，比如： `https://vault.bitwarden.com/#/sso?identifier=YOUR-ORG-ID` 或 `https://your.domain.com/#/sso?identifier=YOUR-ORG-ID`。
{% endhint %}

3、现在您已经使用 SSO 登录验证了您的身份，系统将提示您为新帐户创建[主密码](../your-vault/your-master-password.md)，或者如果您已经拥有 Bitwarden 帐户，输入您的[主密码](../your-vault/your-master-password.md)以**解密**您的密码库。

{% hint style="info" %}
**为什么仍然需要我的主密码？**

所有密码库数据，包括[由您组织共享](../organizations/sharing.md)的凭据，Bitwarden **仅**以加密形式保存他们。这意味着为了使用任何这些凭据，**您**需要一种方法来解密该数据（我们不能）。

您的主密码是该解密密钥的来源。即使您使用 SSO 向 Bitwarden 进行身份验证（证明您的身份），您仍然必须使用该解密密钥（您的主密码）来解密密码库数据。
{% endhint %}
{% endtab %}

{% tab title="SSO 登录 & Key Connector" %}
### SSO 登录 & Key Connector <a href="#login-with-sso-and-key-connector" id="login-with-sso-and-key-connector"></a>

要使用 SSO 和 Key Connector 登录：

1、打开您的 Bitwarden 网页密码库，然后选择**企业单点登录（SSO）**按钮：

![企业 Single Sign-On 按钮](https://images.ctfassets.net/7rncvj1f8mw7/3TjmG99YArRXpsaBHH77Mt/0e4be9262c1a51be449880390ddd19f5/sso-button-lg.png)

2、输入您的**企业标识符**然后选择**登录**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2wjMPE63ZAOzLm1QOxIott/6ef80387d381bc016df9ab0181ec57f5/org-id-input.png?fm=webp&h=236&q=50&w=417" %}
组织标识符字段
{% endembed %}

{% hint style="success" %}
我们建议将此页面添加为书签，并将您的组织标识符作为查询字符串包含在内，这样您就不必每次都输入它了，比如： `https://vault.bitwarden.com/#/sso?identifier=YOUR-ORG-ID` 或 `https://your.domain.com/#/sso?identifier=YOUR-ORG-ID`。
{% endhint %}

3、根据您的帐户状态，您可能需要在首次使用 SSO 和 Key Connector 登录时输入或创建一个主密码。这样做将从您的帐户中删除主密码。

{% hint style="success" %}
我们鼓励您阅读[本文](about-key-connector.md#impact-on-master-passwords)和[本文](about-key-connector.md#impact-on-organization-membership)，以充分了解从您的帐户中移除主密码的含义。您也可以选择**离开此组织**，但是，这将移除对组织所拥有的密码库项目和集合以及单点登录的访问权限。
{% endhint %}

4、如果您使用[两步登录](../two-step-login/two-step-login-methods.md)，请使用您的辅助设备进行身份验证。

{% hint style="info" %}
如果您使用 SSO 登录，则不建议使用电子邮件方式的两步登录，因为使用多个方法会导致错误。可以考虑改为设置[免费的验证器应用程序方式的两步登录](../two-step-login/setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

## 链接您的账户 <a href="#link-your-account" id="link-your-account"></a>

如果您已经拥有属于组织成员的 Bitwarden 帐户，或者您的组织不要求您使用 SSO，则您只需要将您的帐户链接到 SSO：

1、打开网页密码库，导航到**设置**选项卡然后打开您的**组织**。

2、将鼠标悬停在所需的组织上，然后选择 ⚙️齿轮下拉菜单。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/cv0DGhcgyEbQEn4MvdJp5/c0823395fe1a70e5341f9decae3d56d9/sso-link-button-overlay.png?fm=webp&h=386&q=50&w=922" %}
链接 SSO 到网页密码库
{% endembed %}

3、从下拉菜单选择 **链接 SSO**。

链接后，您应该能够像上面记录的那样[使用 SSO 登录](using-login-with-sso.md#login-using-sso)了。

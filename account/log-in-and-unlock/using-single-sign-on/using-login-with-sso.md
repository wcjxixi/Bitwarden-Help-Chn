# 使用 SSO 登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/using-sso/)
{% endhint %}

作为 Bitwarden 的最终用户，在您[使用 SSO 登录](using-login-with-sso.md#login-using-sso)之前，您需要获取组织 [SSO 标识符](using-login-with-sso.md#get-your-organization-identifier)：

{% hint style="success" %}
根据您组织的设置方式，您可能还需要[将您的账户链接到 SSO](using-login-with-sso.md#link-your-account)。如果您**已经拥有作为组织成员的 Bitwarden 账户**，或者**您的组织不要求您使用 SSO**，则通常需要这样做。
{% endhint %}

## 获取组织标识符 <a href="#get-your-organization-identifier" id="get-your-organization-identifier"></a>

每一个 Bitwarden 组织都有一个专门用于 SSO 登录的唯一标识符。您将需要这个值才能登录，因此请询问您的经理或 Bitwarden 管理员[以获取它](../../../login-with-sso/saml-2.0-configuration.md#step-1-set-an-organization-identifier)。

{% hint style="info" %}
企业客户可以验证其组织的域名所有权（例如 `mycompany.com`）。如果您的登录电子邮箱与您组织的已验证域名（例如 `mycompany.com`）相匹配，则在使用 SSO 登录时无需输入 SSO 标识符。

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7xZNW8JqRBbT9BAkTzMIfE/9588c393ada5dee74cca9278e97004c1/Screenshot_2023-03-24_at_9.33.11_AM__2_.png?_a=DAJCwlWIZAAB" alt="" data-size="original">

要了解有关域验证的更多信息，请参阅[这里](../../../admin-console/login-with-sso/claimed-domains.md)。
{% endhint %}

## 使用 SSO 加入组织 <a href="#join-an-organization-using-sso" id="join-an-organization-using-sso"></a>

使用 SSO 加入组织所需的步骤会略有不同，具体取决于您是否收到电子邮件邀请以及您是否已经拥有与要加入 Bitwarden 的电子邮箱地址相关联的 Bitwarden 账户：

{% tabs %}
{% tab title="我已被邀请" %}
如果您的收件箱中已收到加入该组织的电子邮件邀请，请根据您是否已经有一个使用该电子邮箱地址的 Bitwarden 账户，执行以下步骤之一：

## 我已经有 Bitwarden 账户 <a href="#i-already-have-a-bitwarden-account" id="i-already-have-a-bitwarden-account"></a>

如果邀请已发送到已链接到 Bitwarden 账户并且与 IdP 提供的电子邮箱地址匹配的电子邮箱，请按照以下步骤加入组织：

1. 单击电子邮件邀请中的**加入组织**按钮。
2. 在 Bitwarden 邀请页面上，选择**登录**。输入您的电子邮箱地址，然后输入主密码，然后再次选择**登录**。
3. 成功登录后，页面顶部会出现一个绿色横幅，表明您的组织邀请已被接受。在您继续之前，组织管理员需要向组织确认您。
4. 确认后，您将能够通过再次登录 Bitwarden 来访问该组织，这次使用**企业单点登录**选项。

## 我还没有 Bitwarden 账户 <a href="#i-dont-have-a-bitwarden-account" id="i-dont-have-a-bitwarden-account"></a>

如果邀请发送到尚未链接到 Bitwarden 账户的电子邮箱，请按照以下步骤操作：

1. 单击电子邮件邀请中的**加入组织**按钮。
   1. 如果您的组织没有启用**要求 SSO 身份验证**策略，系统会提示您在登录 IdP 之前创建一个新的 Bitwarden 账户。
   2. 如果已启用**要求 SSO 身份验证**，请继续执行步骤 2。
2. 在邀请页面上选择**登录**，选择**登录**。组织的 SSO 标识符将在此界面预先填入（如果您的电子邮箱与组织的已验证域名相匹配，您将绕过此步骤）。
3. 登录到您的 IdP。登录后，您将被重定向到一个页面，在这里您可以为新账户创建一个主密码。
4. 为账户创建主密码。在您继续操作前，组织管理员需要确认您已加入组织。在管理员确认之前，您可能需要使用主密码登录。
5. 确认后，您就可以使用**企业单点登录**选项或主密码登录 Bitwarden 访问该组织了。

尝试登录时，如果您收到错误消息 `<email> has been invited to the organization, please accept invitation.`（\<email> 已被邀请加入该组织，请接受邀请。）。说明已有一个 Bitwarden 账户与此电子邮箱相关联。请按照上面的**我已经有 Bitwarden 账户**的说明进行操作。
{% endtab %}

{% tab title="我未被邀请" %}
如果您的收件箱中还没有收到加入该组织的电子邮件邀请，请根据您是否已经有一个使用该电子邮箱地址的 Bitwarden 账户，执行以下步骤之一：

## 我已经有 Bitwarden 账户 <a href="#i-already-have-a-bitwarden-account" id="i-already-have-a-bitwarden-account"></a>

您将无法使用此账户加入使用 SSO 的组织。联系您的组织管理员以请求邀请。

## 我还没有 Bitwarden 账户 <a href="#i-dont-have-a-bitwarden-account" id="i-dont-have-a-bitwarden-account"></a>

如果您在没有邀请且没有预先存在 Bitwarden 账户的情况下加入组织，请按照以下说明操作：

1. 在 Bitwarden 登录页面上输入您的电子邮箱。在下一页上，选择**企业单点登录**按钮。
2. 输入您的 **SSO 标识符**然后选择**登录**（如果您的电子邮箱与组织的已验证域名相匹配，您将绕过此步骤）。
3. 登录您的 IdP。完成后，您将被重定向到一个页面，您可以在其中为新账户创建主密码。
4. 为账户创建一个主密码。在您继续之前，组织管理员需要向组织确认您。
5. 确认后，您将能够通过使用**企业单点登录**选项登录到 Bitwarden 来访问该组织。
{% endtab %}
{% endtabs %}

## 使用 SSO 登录 <a href="#login-using-sso" id="login-using-sso"></a>

使用 SSO 登录所需的步骤将略有不同，具体取决于您的组织是否使用 [Key Connector](../../../login-with-sso/about-key-connector.md)：

{% tabs %}
{% tab title="SSO 登录 & 主密码" %}
要使用 SSO 和您的主密码登录：

1、打开 Bitwarden App，输入与您的电子邮箱地址，然后选择**使用单点登录**。如果您还没有 Bitwarden 账户电子邮箱，可以输入您的公司电子邮箱。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3XPDLW9GBkA4TIk1j6EAXq/153e77e3b278808b3d05cc13a4fc80f9/login.png?_a=DAJCwlWIZAAB" %}
输入您的电子邮箱地址
{% endembed %}

2、输入您的 **SSO 标识符**然后选择**登录**：

{% hint style="success" %}
并非每个人都需要完成这一步，您的组织可能已将登录程序设置为不需要！ 如果您没有看到此界面，请进入下一步。
{% endhint %}

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5sNF8v7r2HsyLQm8gd6xBC/0925fe8383a4324c359932ed77bcf96f/sso.png?_a=DAJCwlWIZAAB" %}
SSO 标识符界面
{% endembed %}

{% hint style="success" %}
如果您必须完成 SSO 标识符步骤，我们建议将此页面添加为书签，并将您的组织标识符作为查询字符串包含在内，这样您就不必每次都输入组织标识符了，比如： `https://vault.bitwarden.com/#/sso?identifier=my-organization's-identifier` 或 `https://your.domain.com/#/sso?identifier=my-organization's-identifier`。
{% endhint %}

3、现在您将被重定向到你的 IdP（例如 Microsoft Azure、Duo、OneLogin 等）。输入你的 SSO 凭据，像往常一样登录。

4、使用 SSO 进行身份验证后，系统会提示您**输入主密码**以解密密码库，如果您的账户是新的账户，则需要**创建**[**主密码**](../your-master-password.md)。

{% hint style="info" %}
**为什么仍然需要我的主密码？**

所有密码库数据，包括[由您组织共享](../../../organizations/sharing.md)的凭据，Bitwarden **仅**以加密形式保存他们。这意味着为了使用任何这些凭据，**您**需要一种方法来解密该数据（我们不能）。

您的主密码是该解密密钥的来源。即使您使用 SSO 向 Bitwarden 进行身份验证（证明您的身份），您仍然必须使用该解密密钥（您的主密码）来解密密码库数据。
{% endhint %}

5、如果您使用[两步登录](../../two-step-login/setup-guides/two-step-login-methods.md)，请使用您的辅助设备进行身份验证。

{% hint style="danger" %}
如果您使用 [SSO 登录](using-login-with-sso.md)，则不建议使用电子邮箱方式的两步登录，因为使用多种方式会导致错误。考虑改为[免费的验证器方式的两步登录](../../two-step-login/setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}
{% endtab %}

{% tab title="SSO 登录 & 受信任设备" %}
要使用 SSO 和受信任设备登录：

1、打开 Bitwarden App，输入与您的电子邮箱地址，然后选择**使用单点登录**。如果您还没有 Bitwarden 账户电子邮箱，可以输入您的公司电子邮箱。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3XPDLW9GBkA4TIk1j6EAXq/153e77e3b278808b3d05cc13a4fc80f9/login.png?_a=DAJCwlWIZAAB" %}
输入您的电子邮箱地址
{% endembed %}

2、输入您的 **SSO 标识符**然后选择**登录**：

{% hint style="success" %}
并非每个人都需要完成这一步，您的组织可能已将登录程序设置为不需要！ 如果您没有看到此界面，请进入下一步。
{% endhint %}

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5sNF8v7r2HsyLQm8gd6xBC/0925fe8383a4324c359932ed77bcf96f/sso.png?_a=DAJCwlWIZAAB" %}
SSO 标识符界面
{% endembed %}

{% hint style="success" %}
如果您必须完成 SSO 标识符步骤，我们建议将此页面添加为书签，并将您的组织标识符作为查询字符串包含在内，这样您就不必每次都输入组织标识符了，比如： `https://vault.bitwarden.com/#/sso?identifier=my-organization's-identifier` 或 `https://your.domain.com/#/sso?identifier=my-organization's-identifier`。
{% endhint %}

3、现在您将被重定向到你的 IdP（例如 Microsoft Azure、Duo、OneLogin 等）。输入你的 SSO 凭据，像往常一样登录。

4、使用 SSO 进行身份验证后，系统会提示您选择与登录设备建立信任的选项（[了解更多选项信息](add-a-trusted-device.md)）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1zrsBanU5CNhFnDHAXazwP/45aebda6d73fefcb0c47bea1fe254d3d/2024-10-09_16-02-23.png?_a=DAJCwlWIZAAB" %}
建立信任的选项
{% endembed %}

{% hint style="info" %}
如果您是第一次登录，您可以将此 App 指定为受信任设备，而不必请求使用上述方法之一。
{% endhint %}

5、如果您使用[两步登录](../../two-step-login/setup-guides/two-step-login-methods.md)，请使用您的辅助设备进行身份验证。

{% hint style="danger" %}
如果您使用 [SSO 登录](using-login-with-sso.md)，则不建议使用电子邮箱方式的两步登录，因为使用多种方式会导致错误。考虑改为[免费的验证器方式的两步登录](../../two-step-login/setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}
{% endtab %}

{% tab title="SSO 登录 & Key Connector" %}
要使用 SSO 和 Key Connector 登录：

1、打开 Bitwarden App，输入与您的电子邮箱地址，然后选择**使用单点登录**。如果您还没有 Bitwarden 账户电子邮箱，可以输入您的公司电子邮箱。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3XPDLW9GBkA4TIk1j6EAXq/153e77e3b278808b3d05cc13a4fc80f9/login.png?_a=DAJCwlWIZAAB" %}
输入您的电子邮箱地址
{% endembed %}

2、输入您的 **SSO 标识符**然后选择**登录**：

{% hint style="success" %}
并非每个人都需要完成这一步，您的组织可能已将登录程序设置为不需要！ 如果您没有看到此界面，请进入下一步。
{% endhint %}

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5sNF8v7r2HsyLQm8gd6xBC/0925fe8383a4324c359932ed77bcf96f/sso.png?_a=DAJCwlWIZAAB" %}
SSO 标识符界面
{% endembed %}

{% hint style="success" %}
如果您必须完成 SSO 标识符步骤，我们建议将此页面添加为书签，并将您的组织标识符作为查询字符串包含在内，这样您就不必每次都输入组织标识符了，比如： `https://vault.bitwarden.com/#/sso?identifier=my-organization's-identifier` 或 `https://your.domain.com/#/sso?identifier=my-organization's-identifier`。
{% endhint %}

3、现在您将被重定向到你的 IdP（例如 Microsoft Azure、Duo、OneLogin 等）。输入你的 SSO 凭据，像往常一样登录。

4、根据您的账户状态，您可能需要在首次使用 SSO 和 Key Connector 登录时输入或创建主密码。这样做将从您的账户中移除主密码。

{% hint style="info" %}
我们希望您阅读[这里](../../../login-with-sso/about-key-connector.md#impact-on-master-passwords)和[这里](../../../login-with-sso/about-key-connector.md#impact-on-organization-membership)，以充分了解从您的账户中删除主密码意味着什么。您可以选择**离开组织**，但这将取消对组织拥有的密码库项目和集合以及单点登录的访问权限。
{% endhint %}

5、如果您使用[两步登录](../../two-step-login/setup-guides/two-step-login-methods.md)，请使用您的辅助设备进行身份验证。

{% hint style="danger" %}
如果您使用 [SSO 登录](using-login-with-sso.md)，则不建议使用电子邮箱方式的两步登录，因为使用多种方式会导致错误。考虑改为[免费的验证器方式的两步登录](../../two-step-login/setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

## 链接您的账户 <a href="#link-your-account" id="link-your-account"></a>

如果您已经拥有属于组织成员的 Bitwarden 账户，或者您的组织不要求您使用 SSO，则您只需要将您的账户链接到 SSO：

1、打开网页 App，选择组织旁边的 **≡选项**菜单。

2、从下拉菜单选择**链接 SSO**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/cv0DGhcgyEbQEn4MvdJp5/fefb4158c09be8cf9804ed5579c2d7dc/Screenshot_2024-02-26_at_2.07.03_PM.png?_a=DAJCwlWIZAAB" %}
链接 SSO
{% endembed %}

链接后，您应该能够像上面记录的那样[使用 SSO 登录](using-login-with-sso.md#login-using-sso)了。

{% hint style="info" %}
链接成功后，可以从同一菜单中**取消链接 SSO**。这通常在以下情况下有用：IdP（如谷歌、Azure）或 Bitwarden 中的电子邮箱地址发生变化，导致 SSO 停止工作；IdP 身份链接到错误的 Bitwarden 账户，必须先破坏现有链接才能建立正确的链接。
{% endhint %}

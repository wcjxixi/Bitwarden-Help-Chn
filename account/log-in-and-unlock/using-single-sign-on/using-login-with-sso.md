# 使用 SSO 登录

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/using-sso/)
{% endhint %}

如果您是某个企业组织的成员，您可能会被要求或被允许使用单点登录登录到 Bitwarden，类似于登录其他工作相关的应用程序的方式：

1、打开 Bitwarden App，输入您的电子邮箱地址，然后选择**使用单点登录**：

{% embed url="https://bitwarden.com/assets/3XPDLW9GBkA4TIk1j6EAXq/37d89e28b4d913e7a5031ff1c06fc783/2025-10-13_10-39-36.png?w=938&fm=avif" %}
使用单点登录按钮
{% endembed %}

2、您的组织**可能**会要求您输入 **SSO 标识符**。若看到以下界面，请输入您组织的 SSO 标识符；若不清楚该信息，请联系经理或管理员协助获取。

{% embed url="https://bitwarden.com/assets/5sNF8v7r2HsyLQm8gd6xBC/ac61e5e2bb0c733b3498536be584db9a/2025-10-13_10-46-01.png?w=958&fm=avif" %}
SSO 标识符界面
{% endembed %}

{% hint style="success" %}
**组织成员**：请将 URL 中包含标识符的页面（例如 `https://vault.bitwarden.com/#/sso?my-identifier`）添加为书签，这样您就不必在每次登录时输入它。

**组织管理员**：如果您的成员拥有与域名匹配的电子邮件地址，设置[声明域名](../../../admin-console/login-with-sso/claimed-domains.md)将自动跳过此步骤。
{% endhint %}

3、当您被重定向至 IdP（例如 Microsoft Azure、Duo 或 OneLogin）后，请输入您的 SSO 凭据进行登录，操作方式与其他应用程序相同。通常，在此阶段，您的 IdP 会要求您完成 2FA。

4、后续操作取决于您的组织选择的解密选项：

{% tabs %}
{% tab title="主密码" %}
输入您的主密码，或者，如果您的账户是新账户，请创建主密码以完成登录：

{% embed url="https://bitwarden.com/assets/TJ0nUZ4zs7l38aOQz5WLl/6b95624ef2271198f6fc6447b77d63c1/2025-10-13_12-57-15.png?w=958&fm=avif" %}
使用主密码解密
{% endembed %}

{% hint style="success" %}
**为什么仍然需要我的主密码？**

所有密码库数据，包括[由您组织共享](../../../password-manager/organization-members/sharing.md)的凭据，Bitwarden **仅**以加密形式保存他们。这意味着为了使用任何这些凭据，**您**需要一种方法来解密该数据（我们不能）。

您的主密码是该解密密钥的来源。即使您使用 SSO 向 Bitwarden 进行身份验证（证明您的身份），您仍然必须使用该解密密钥（在这种情况下是您的主密码）来解密密码库数据。
{% endhint %}
{% endtab %}

{% tab title="受信任设备" %}
选择一个[与您登录的设备建立信任](add-a-trusted-device.md)的选项，以完成登录：

{% embed url="https://bitwarden.com/assets/1zrsBanU5CNhFnDHAXazwP/c94f8bfb5066cb79381676570bd87aa1/2025-10-13_13-06-26.png?w=958&fm=avif" %}
建立信任的选项
{% endembed %}

{% hint style="success" %}
如果这是您第一次登录，您将被允许自动将此 App 指定为受信任设备，而不是被要求使用上述方法之一：

<img src="https://bitwarden.com/assets/6iahsCNPUcIT51P2oZIUQ1/f6dbb4364d96d80c69c3ec84176e7971/2025-10-13_13-03-59.png?w=958&#x26;fm=avif" alt="" data-size="original">
{% endhint %}
{% endtab %}

{% tab title="Key Connector" %}
如果您的组织使用 Key Connector，您很可能可以跳到下一步。如果您的账户是在推出 Key Connector 之前创建的，则可能需要输入主密码。这样做将从您的账户中移除主密码。

{% hint style="info" %}
我们鼓励您阅读有关 Key Connector 的信息，以了解从您的账户中[移除主密码的影响](../../../self-hosting/key-connector/about-key-connector.md#impact-on-master-passwords)。
{% endhint %}
{% endtab %}
{% endtabs %}

5、最后，可能会要求您使用您在 Bitwarden 中设置的选项完成两步登录。如果您的 IdP 要求，您通常不需要使用 Bitwarden 两步登录（**步骤 3**）。

# SSO 登录的使用

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/using-sso/)
{% endhint %}

作为 Bitwarden 的最终用户，在您[使用 SSO 登录](using-login-with-sso.md#login-using-sso)之前，您需要获取组织 [SSO 标识符](using-login-with-sso.md#get-your-organization-identifier)：

{% hint style="success" %}
根据您组织的设置方式，您可能还需要[将您的账户链接到 SSO](using-login-with-sso.md#link-your-account)。如果您**已经拥有作为组织成员的 Bitwarden 帐户**，或者**您的组织不要求您使用 SSO**，则通常需要这样做。
{% endhint %}

## 获取组织标识符 <a href="#get-your-organization-identifier" id="get-your-organization-identifier"></a>

每一个 Bitwarden 组织都有一个专门用于 SSO 登录的唯一标识符。您将需要这个值才能登录，因此请询问您的经理或 Bitwarden 管理员[以获取它](saml-2.0-configuration.md#step-1-set-an-organization-identifier)。

{% hint style="info" %}
企业客户可以验证其组织的域名所有权（例如 `mycompany.com`）。如果您的登录电子邮件与您组织的已验证域名（例如 `mycompany.com`）相匹配，则在使用 SSO 登录时无需输入 SSO 标识符。

要了解有关域验证的更多信息，请参阅[这里](../admin-console/login-with-sso/domain-verification.md)。
{% endhint %}

## 使用 SSO 加入组织 <a href="#join-an-organization-using-sso" id="join-an-organization-using-sso"></a>

使用 SSO 加入组织所需的步骤会略有不同，具体取决于您是否收到电子邮件邀请以及您是否已经拥有与要加入 Bitwarden 的电子邮件地址相关联的 Bitwarden 账户：

{% tabs %}
{% tab title="我已被邀请" %}
如果您的收件箱中有加入该组织的电子邮件邀请，请根据您是否已经有一个使用该电子邮件地址的 Bitwarden 账户，执行以下步骤之一：

## 我已经有 Bitwarden 账户 <a href="#i-already-have-a-bitwarden-account" id="i-already-have-a-bitwarden-account"></a>

如果邀请已发送到已链接到 Bitwarden 账户并且与 IdP 提供的电子邮件地址匹配的电子邮件，请按照以下步骤加入组织：

1. 单击电子邮件邀请中的**加入组织**按钮。
2. 在 Bitwarden 邀请页面上，选择**登录**。输入您的电子邮件地址，然后输入主密码，然后再次选择**登录**。
3. 成功登录后，页面顶部会出现一个绿色横幅，表明您的组织邀请已被接受。在您继续之前，组织管理员需要向组织确认您。
4. 确认后，您将能够通过再次登录 Bitwarden 来访问该组织，这次使用企业单点登录选项。

## 我还没有 Bitwarden 账户 <a href="#i-dont-have-a-bitwarden-account" id="i-dont-have-a-bitwarden-account"></a>

如果邀请发送到尚未链接到 Bitwarden 账户的电子邮件，请按照以下步骤操作：

1. 单击电子邮件邀请中的**加入组织**按钮。
2. 在邀请页面上选择**登录**，然后输入您的电子邮件地址。在下一页上，选择**企业单点登录**按钮。
3. 输入您的 **SSO 标识符**然后选择**登录**（如果您的电子邮件与组织的已验证域匹配，您将绕过此步骤）。
4. 登录您的 IdP。完成后，您将被重定向到一个页面，您可以在其中为新账户创建主密码。
5. 为账户创建一个主密码。在您继续之前，组织管理员需要向组织确认您。
6. 确认后，您将能够通过使用企业单点登录选项登录到 Bitwarden 来访问该组织。

尝试登录时，如果您收到错误消息 `<email> has been invited to the organization, please accept invitation.`（\<email> 已被邀请加入该组织，请接受邀请。）。说明已有一个 Bitwarden 账户与此电子邮件相关联。请按照上面的**我已经有 Bitwarden 账户**的说明进行操作。
{% endtab %}

{% tab title="我未被邀请" %}
如果您的收件箱中还没有加入该组织的电子邮件邀请，请根据您是否已经有一个使用该电子邮件地址的 Bitwarden 账户，执行以下步骤之一：

## 我已经有 Bitwarden 账户 <a href="#i-already-have-a-bitwarden-account" id="i-already-have-a-bitwarden-account"></a>

您将无法使用此账户加入使用 SSO 的组织。联系您的组织管理员以请求邀请。

## 我还没有 Bitwarden 账户 <a href="#i-dont-have-a-bitwarden-account" id="i-dont-have-a-bitwarden-account"></a>

如果您在没有邀请且没有预先存在的 Bitwarden 账户的情况下加入组织，请按照以下说明操作：

1. 在 Bitwarden 登录页面上输入您的电子邮件。在下一页上，选择**企业单点登录**按钮。
2. 输入您的 **SSO 标识符**然后选择**登录**（如果您的电子邮件与组织的已验证域匹配，您将绕过此步骤）。
3. 登录您的 IdP。完成后，您将被重定向到一个页面，您可以在其中为新账户创建主密码。
4. 为账户创建一个主密码。在您继续之前，组织管理员需要向组织确认您。
5. 确认后，您将能够通过使用**企业单点登录**选项登录到 Bitwarden 来访问该组织。
{% endtab %}
{% endtabs %}

## 使用 SSO 登录 <a href="#login-using-sso" id="login-using-sso"></a>

使用 SSO 登录所需的步骤将略有不同，具体取决于您的组织是否使用 [Key Connector](about-key-connector.md)：

{% tabs %}
{% tab title="SSO 登录 & 主密码" %}
### SSO 登录 & 主密码 <a href="#login-with-sso-and-master-password" id="login-with-sso-and-master-password"></a>

要使用 SSO 和您的主密码登录：

1、打开您的 Bitwarden 网页密码库，然后输入您的 Bitwarden 电子邮件并选择**继续**。如果您还没有 Bitwarden 帐户电子邮件，您可以输入您的公司电子邮件。

{% embed url="https://bitwarden.com/_gatsby/image/2cabcf38f4a4b36d40891d1876e39315/0c3e98384836d57b216b7aaf24bdd37a/Screen%20Shot%202022-11-17%20at%2010.56.00%20AM%20(2).webp?eu=dddd58e3eac8a9d55e6da88439753560b23f01abaf5133823a32e3fb4dfc988726f54f5126922eb7786008dbd5b143bb65927d641fe9d7d3c1bd4ef4ef3cab5a52845cbf63b2780f552b95fce6f3011361cf4e50abdb8c4ce32e78cbfaeaea214e055f35fb3eeed0afea6020f39d7167aea9a16c3b91ed22e14456098c1f6eff0cdbe4a2541799bceb6eeb8297f208979a925c6f01c4f73170761e1d0aeb2ae8a0b601756f7c415b619ba95acf61c3b23d156071595a1c9434788500a503529bbbbfce5fd97879fca9c82c7181acffc4821bac3473e1d127a9ed4a076162ae7cb3fc25a0&a=w%3D386%26h%3D231%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.775Z" %}
电子邮件地址
{% endembed %}

2、选择**企业单点登录**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/22e1f6a4d3c65d6851495ec8339952d7/42621eea3ec67a0562af8715e5f23b8a/Screen%20Shot%202022-11-02%20at%2010.51.48%20AM.webp?eu=8c8754e3b6c1a8d20f6ca2d13c21326bb33d57abac0535d33564e0ae1ea8978470a64801249279b724380cddd0b441b231c4796910bcd588c6bd4bf2b864af0b01d058bc63b621065322c0fab8f503443b93180da8d7cb0da36e73ddb3b7e2214b591b7afe2bbbd5b9aa3f3cf4c76f71e0a9b9773893fc2da30c0d109d4932bf31ffd3c06d4baad1b75db1b5a8f3089b94ba6a005fd881617e0f19400fb929b9d9c75b06392f01394a87ce47956495b56e4a68200c5f04f763388553f86f32c4e5fca40ede7c78e9a1c0337599a0fdc2b84ff24515bf9063c6803b780c10ad12b0bc79988320690f8134ff9452b60b6a443d9c5cd773&a=w%3D380%26h%3D287%26fm%3Dwebp%26q%3D75&cd=2022-11-29T13%3A10%3A06.710Z" %}
企业单点登录和主密码
{% endembed %}

3、输入您的 **SSO 标识符**然后选择**登录**（已验证域名的组织将跳过此步骤）：

{% embed url="https://bitwarden.com/_gatsby/image/12226573eecd59868314f6427076a94f/23efaf500c33ba0a60fd687eefc9a497/Screen%20Shot%202022-11-07%20at%203.31.39%20PM%20(2).webp?eu=dddf57efb5c0a8865a3af186697b653ae76c50adf80736d83c64b6a71eac988077f01c0028c62fb32b6953d6dbe517ef6fcf71374ce7d3dac5be4ef0e264ac0a018108bf35e724555023c6ace6f40c1d2c825a1bab9cd751fe3c2581a6ade4344f015f68fd3efb9fb2fc717bb7c17161aceca7786d9fec7fff171d2abd1037fb26b9e89d7a628f93b848bbe0a6db7ad29fb17e0f468aa16477724a1d5cee2ab8f4b152743821125b3198ae0bc46391b1237f32610b0a5d9804628f11946e31c1e6e6a05cc47a7c8ef98d5e7398c0af9eee13c34a0b88a025c69c7b2459&a=w%3D413%26h%3D330%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.828Z" %}
SSO 标识符
{% endembed %}

{% hint style="success" %}
我们建议将此页面添加为书签，并将您的组织标识符作为查询字符串包含在内，这样您就不必每次都输入它了，比如： `https://vault.bitwarden.com/#/sso?identifier=YOUR-ORG-ID` 或 `https://your.domain.com/#/sso?identifier=YOUR-ORG-ID`。
{% endhint %}

4、现在您已经使用 SSO 登录验证了您的身份，系统将提示您为新帐户**创建**[主密码](../your-vault/your-master-password.md)，或者如果您已经拥有 Bitwarden 账户，输入您的主密码以解密您的密码库。

{% hint style="info" %}
**为什么仍然需要我的主密码？**

所有密码库数据，包括[由您组织共享](../organizations/sharing.md)的凭据，Bitwarden **仅**以加密形式保存他们。这意味着为了使用任何这些凭据，**您**需要一种方法来解密该数据（我们不能）。

您的主密码是该解密密钥的来源。即使您使用 SSO 向 Bitwarden 进行身份验证（证明您的身份），您仍然必须使用该解密密钥（您的主密码）来解密密码库数据。
{% endhint %}

5、如果您使用两步登录，请使用您的辅助设备进行身份验证。

{% hint style="danger" %}
如果您使用 [SSO 登录](using-login-with-sso.md)，则不建议通过电子邮件进行两步登录，因为使用多种方式会导致错误。考虑改为[免费的验证器方式的两步登录](../two-step-login/setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}
{% endtab %}

{% tab title="SSO 登录 & Key Connector" %}
### SSO 登录 & Key Connector <a href="#login-with-sso-and-key-connector" id="login-with-sso-and-key-connector"></a>

要使用 SSO 和 Key Connector 登录：

1、打开您的 Bitwarden 网页密码库，然后输入您的 Bitwarden 电子邮件并选择**继续**。如果您还没有 Bitwarden 账户电子邮件，您可以输入您的公司电子邮件。

{% embed url="https://bitwarden.com/_gatsby/image/2cabcf38f4a4b36d40891d1876e39315/0c3e98384836d57b216b7aaf24bdd37a/Screen%20Shot%202022-11-17%20at%2010.56.00%20AM%20(2).webp?eu=dddd58e3eac8a9d55e6da88439753560b23f01abaf5133823a32e3fb4dfc988726f54f5126922eb7786008dbd5b143bb65927d641fe9d7d3c1bd4ef4ef3cab5a52845cbf63b2780f552b95fce6f3011361cf4e50abdb8c4ce32e78cbfaeaea214e055f35fb3eeed0afea6020f39d7167aea9a16c3b91ed22e14456098c1f6eff0cdbe4a2541799bceb6eeb8297f208979a925c6f01c4f73170761e1d0aeb2ae8a0b601756f7c415b619ba95acf61c3b23d156071595a1c9434788500a503529bbbbfce5fd97879fca9c82c7181acffc4821bac3473e1d127a9ed4a076162ae7cb3fc25a0&a=w%3D386%26h%3D231%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.775Z" %}
电子邮件地址
{% endembed %}

2、选择**企业单点登录**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/22e1f6a4d3c65d6851495ec8339952d7/42621eea3ec67a0562af8715e5f23b8a/Screen%20Shot%202022-11-02%20at%2010.51.48%20AM.webp?eu=8c8754e3b6c1a8d20f6ca2d13c21326bb33d57abac0535d33564e0ae1ea8978470a64801249279b724380cddd0b441b231c4796910bcd588c6bd4bf2b864af0b01d058bc63b621065322c0fab8f503443b93180da8d7cb0da36e73ddb3b7e2214b591b7afe2bbbd5b9aa3f3cf4c76f71e0a9b9773893fc2da30c0d109d4932bf31ffd3c06d4baad1b75db1b5a8f3089b94ba6a005fd881617e0f19400fb929b9d9c75b06392f01394a87ce47956495b56e4a68200c5f04f763388553f86f32c4e5fca40ede7c78e9a1c0337599a0fdc2b84ff24515bf9063c6803b780c10ad12b0bc79988320690f8134ff9452b60b6a443d9c5cd773&a=w%3D380%26h%3D287%26fm%3Dwebp%26q%3D75&cd=2022-11-29T13%3A10%3A06.710Z" %}
企业单点登录和主密码
{% endembed %}

3、输入您的 **SSO 标识符**然后选择**登录**（已验证域名的组织将跳过此步骤）：

{% embed url="https://bitwarden.com/_gatsby/image/12226573eecd59868314f6427076a94f/23efaf500c33ba0a60fd687eefc9a497/Screen%20Shot%202022-11-07%20at%203.31.39%20PM%20(2).webp?eu=dddf57efb5c0a8865a3af186697b653ae76c50adf80736d83c64b6a71eac988077f01c0028c62fb32b6953d6dbe517ef6fcf71374ce7d3dac5be4ef0e264ac0a018108bf35e724555023c6ace6f40c1d2c825a1bab9cd751fe3c2581a6ade4344f015f68fd3efb9fb2fc717bb7c17161aceca7786d9fec7fff171d2abd1037fb26b9e89d7a628f93b848bbe0a6db7ad29fb17e0f468aa16477724a1d5cee2ab8f4b152743821125b3198ae0bc46391b1237f32610b0a5d9804628f11946e31c1e6e6a05cc47a7c8ef98d5e7398c0af9eee13c34a0b88a025c69c7b2459&a=w%3D413%26h%3D330%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.828Z" %}
SSO 标识符
{% endembed %}

{% hint style="success" %}
我们建议将此页面添加为书签，并将您的组织标识符作为查询字符串包含在内，这样您就不必每次都输入它了，比如： `https://vault.bitwarden.com/#/sso?identifier=YOUR-ORG-ID` 或 `https://your.domain.com/#/sso?identifier=YOUR-ORG-ID`。
{% endhint %}

4、根据您的账户状态，您可能需要在首次使用 SSO 和 Key Connector 登录时输入或创建主密码。这样做将从您的账户中移除主密码。

{% hint style="info" %}
我们希望您阅读[这里](about-key-connector.md#impact-on-master-passwords)和[这里](about-key-connector.md#impact-on-organization-membership)，以充分了解从您的账户中删除主密码意味着什么。您可以选择**离开组织**，但这将取消对组织拥有的密码库项目和集合以及单点登录的访问权限。
{% endhint %}

5、如果您使用两步登录，请使用您的辅助设备进行身份验证。

{% hint style="danger" %}
如果您使用 [SSO 登录](using-login-with-sso.md)，则不建议使用电子邮件方式的两步登录，因为使用多种方式会导致错误。考虑考虑改为[免费的验证器应用程序方式的两步登录](../two-step-login/setup-guides/two-step-login-via-authenticator.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

## 链接您的账户 <a href="#link-your-account" id="link-your-account"></a>

如果您已经拥有属于组织成员的 Bitwarden 账户，或者您的组织不要求您使用 SSO，则您只需要将您的账户链接到 SSO：

1、打开网页密码库，选择组织旁边的 **≡选项**菜单。

2、从下拉菜单选择 **链接 SSO**。

{% embed url="https://bitwarden.com/_gatsby/image/b596746782d2d29ae1d422819d3c0c71/2ea02158370812fd9f80da64d3b4d1e7/Screen%20Shot%202022-05-17%20at%2010.25.46%20AM.webp?eu=8b8805e3b7cafa850d3aa48a39776361e53d02afaa043ed56c64edfc4cf9cf8770a71e00289178e22c6a588c86e04bb9349278331ce6858bc6b44ba7bc63a30e5bd75be862b679055722c5f9b1a6054368c7195ea48a9c0fa6382481e3bae1221308586fe839b29ef3f06835e7d66c2cb9f2f07f2681fe3ca30c00018f0776be3ae8d6843248e693f718f0b5a8a97dbac4b47a4e358992407c7331590c976dbebae657736d21445e3cc6a850ce6296b06a4867205f5852f3366cd504f83e33c5b1e4c20e9b2f2ebfc7aa692fc2acac80ef18b12a73face20c6d37f150f0db211a8a27ff1bd157b10c174ad&a=w%3D806%26h%3D483%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.572Z" %}
在网页密码库中链接 SSO
{% endembed %}

链接后，您应该能够像上面记录的那样[使用 SSO 登录](using-login-with-sso.md#login-using-sso)了。

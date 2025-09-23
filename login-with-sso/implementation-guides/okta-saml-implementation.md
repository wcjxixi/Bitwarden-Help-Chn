# Okta SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-okta/)
{% endhint %}

本文是**专门针对** **Okta** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页 App 和 Okta 管理门户中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

{% hint style="success" %}
**已经是 SSO 专家？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/3tQfArvZQ1vigzlnjdBxr1/41449d881bd3292eed3046cf457495f1/saml-okta-sample.zip)
{% endhint %}

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJAUVWIZAAB" %}
产品切换器
{% endembed %}

打开组织的**设置** → **单点登录**界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?_a=DAJAUVWIZAAB" %}
SAML 2.0 配置
{% endembed %}

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个，然后从**类型**下拉菜单中选择 **SAML**。保持此界面打开，以方便参考。

如果愿意，您可以在此阶段关闭**设置专属的 SP 实体 ID** 选项。这样做会从 SP 实体 ID 值中移除组织 ID，但大多数情况下都建议打开该选项。

{% hint style="success" %}
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 和 [Key Connector](../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建 Okta 应用程序 <a href="#create-an-okta-app" id="create-an-okta-app"></a>

在 Okta 管理门户中，从导航中选择 **Applications** → **Applications**。在应用程序界面，选择 **Add Application** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5LhfdUFyWSsqzStUzjcvN0/970d6c398de09ad3219baa331b16263f/okta-addapp.png?fm=webp&h=615&q=50&w=923" %}
添加应用程序
{% endembed %}

选择 **Create New App** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/78TXGiETmELRygBMuVWhm5/7ce41e8bde463b8f966afcc5d8c7ef43/okta-createapp.png?fm=webp&h=257&q=50&w=920" %}
创建新应用程序
{% endembed %}

在 Create a New Application Integration 对话框中，从 **Platform** 下拉列表中选择 **Web** 然后选择 **SAML 2.0** 单选按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4I8U9GJFm2w25scodW6aHu/1017c3f27948c6fde116b4783d343a91/okta-apptype.png?fm=webp&h=539&q=50&w=734" %}
应用程序类型设置
{% endembed %}

选择 **Create** 按钮以继续进行配置。

### 常规设置 <a href="#general-settings" id="general-settings"></a>

在 **General Settings** 界面，为应用程序指定一个唯一的、专用于 Bitwarden 的名称，然后选择 **Next**。

### 配置 SAML <a href="#configure-saml" id="configure-saml"></a>

在 **Configure SAML** 界面，配置以下字段：

| 字段                          | 描述                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Single sign on URL          | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>Assertion Consumer Service (ACS) URL</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2/your-org-id/Acs</code>。对于自托管实例，这由您<a href="../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain/sso/saml2/your-org-id/Acs</code>。</p> |
| Audience URI (SP Entity ID) | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>SP Entity ID</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2</code>。对于自托管实例，这由您<a href="../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2</code>。</p>                                                     |
| Name ID format              | 选择在 SAML 声明中使用的 [SAML NameID format](https://docs.oracle.com/cd/E19316-01/820-3886/ggwbz/index.html)。默认为 **Unspecified**。                                                                                                                                                                                                                                                                |
| Application username        | 选择用户用于登录 Bitwarden 的 Okta 属性。                                                                                                                                                                                                                                                                                                                                                            |

### 高级设置 <a href="#advanced-settings" id="advanced-settings"></a>

选择 **Show Advanced Settings** 链接并配置以下字段：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4VOeKsTeXHPsipA0SoDgHb/d19693e16cb98ab475cb1873bf5641d7/okta-advsettings.png?fm=webp&h=159&q=50&w=626" %}
高级设置
{% endembed %}

| 字段                  | 描述                                                                                 |
| ------------------- | ---------------------------------------------------------------------------------- |
| Response            | SAML 响应是否由 Okta 签名。                                                                |
| Assertion Signature | SAML 声明是否由 Okta 签名。                                                                |
| Signature Algorithm | 用于对响应和/或声明进行签名的签名算法，具体取决于设置为 **Signed** 的算法。默认为 `rsa-sha256`。                      |
| Digest Algorithm    | 用于对响应和/或声明进行签名的摘要算法，具体取决于设置为 **Signed** 的算法。此字段必须与已选择的 **Signature Algorithm** 匹配。 |

### 属性声明 <a href="#attribute-statements" id="attribute-statements"></a>

在 **Attribute Statements** 部分，构建以下 SP → IdP 属性映射：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/VJZ2ZJtqdCdnzxG4xf4G8/b9fce227ebf1ba72e3598875e1f6f7aa/okta-attr.png?fm=webp&h=417&q=50&w=617" %}
属性声明
{% endembed %}

配置完成后，选择 **Next** 按钮进入 **Feedback** 界面然后选择 **Finish**。

### 获取 IdP 值 <a href="#get-idp-values" id="get-idp-values"></a>

应用程序创建后，选择应用程序的 **Sign On** 选项卡，然后选择 **View Setup Instructions** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/ec14rKiQG4rowDgxg3MPg/593450634299f3798fc25c8e37308464/okta-ssosettings.png?fm=webp&h=895&q=50&w=958" %}
获取 IdP 的值
{% endembed %}

保留此页面以备将来使用，或复制 **Identity Provider Single Sign-On URL** 和 **Identity Provider Issuer** 并下载 **X.509 Certificate**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4SRYsrAZjCPhksikeAOnBp/f975c57912f6c1a8c5d5d6002d23bd38/okta-values.png?fm=webp&h=388&q=50&w=909" %}
IdP 值
{% endembed %}

### 分配 <a href="#assignments" id="assignments"></a>

导航到 **Assignments** 选项卡然后选择 **Assign** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4KcjFuFnHFMnQda4NbKTGh/731a0c635efde1f3333ed6afd58d994e/okta-assign.png?fm=webp&h=799&q=50&w=959" %}
分配群组
{% endembed %}

您可以使用 **Assign to People** 选项逐个用户地分配对应用程序的访问权限，或使用 **Assign to Groups** 选项来批量分配。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已经在 Okta 管理门户中配置了所需的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据在 Okta 管理门户[设置期间](okta-saml-implementation.md#create-an-okta-app)所选择的选项配置以下字段：

| 字段                                 | 描述                                                                                                        |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | 将其设置为[在 Okta 中指定的](okta-saml-implementation.md#configure-saml) NameID 格式。否则，请保留为 **Unspecified**。         |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                                |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                                         |
| Minimum Incoming Signing Algorithm | 将其设置为[在 Okta 中指定的](okta-saml-implementation.md#configure-saml) 签名算法。                                      |
| Want Assertions Signed             | 如果您[在 Okta 中](okta-saml-implementation.md#advanced-settings)将 Assertion Signature 字段设置为 **Signed**，请选中此框。 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 Okta 管理门户以获取应用程序的值：

| 字段                                        | 描述                                                                                                                                                                                                                  |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | 输入您的 **Identity Provider Issuer**，这可以从 Okta 的 [**Sign On** 设置](okta-saml-implementation.md#get-idp-values)界面选择 **View Setup Instructions** 按钮来获取。                                                                   |
| Binding Type                              | 设置为 **Redirect**。Okta 目前不支持 HTTP POST。                                                                                                                                                                              |
| Single Sign On Service URL                | 输入您的  **Identity Provider Single Sign-On URL**，这可以从 Okta 的 [**Sign On** 设置](okta-saml-implementation.md#get-idp-values)界面获取。                                                                                        |
| Single Log Out Service URL                | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。但是您可以根据需要预先配置它。                                                                                                                                                                   |
| Artifact Resolution Service URL           | 对于 Okta 实现，您可以将此字段留空。                                                                                                                                                                                               |
| X509 Public Certificate                   | <p>黏贴<a href="okta-saml-implementation.md#get-idp-values">已下载的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 选择[在 Okta 应用程序配置期间](okta-saml-implementation.md#advanced-settings)选择的签名算法。如果您没有更改签名算法，请将其保留为默认 (`rsa-sha256`)。                                                                                                      |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                |
| Disable Outbound Logout Requests          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                  |
| Want Authentication Requests Signed       | Okta 是否要求 SAML 请求被签名。                                                                                                                                                                                               |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../admin-console/manage-shared-items/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**企业单点登录**按钮来进行测试：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BdlHeogd42LEoG06qROyQ/cab8e66d8745059e73c02739d9d2d744/2024-12-02_10-28-02.png?_a=DAJAUVWIZAAB" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 Okta 的登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3Rh2Bg17sCE57xJsUKfqwN/4342c56fa656be94ef90dd620251a868/okta-login.png?fm=webp&h=620&q=50&w=427" %}
Okta 登录界面
{% endembed %}

使用您的 Okta 凭据进行身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

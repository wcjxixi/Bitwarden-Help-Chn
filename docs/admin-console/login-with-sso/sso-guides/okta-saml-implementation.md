# Okta SAML

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-okta/)
{% endhint %}

本文是**专门针对** **Okta** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](generic-saml.md)。

配置需要在 Bitwarden 网页 App 和 Okta 管理门户中同时进行。操作过程中，我们建议同时打开这两个界面，并按照文档记录的步骤顺序完成操作。

{% hint style="success" %}
**已经是 SSO 专家了吗？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️** [下载示例](https://bitwarden.com/assets/3tQfArvZQ1vigzlnjdBxr1/364da08e7280662e743b6f6b75eb225f/saml-okta.zip.zip)
{% endhint %}

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden [网页 App](https://bitwarden.com/help/getting-started-webvault/)，然后使用产品切换器打开管理控制台：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

打开组织的**设置** → **单点登录**界面：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?w=1036&#x26;fm=avif" alt=""><figcaption><p>SAML 2.0 配置</p></figcaption></figure></div>

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个，然后从**类型**下拉菜单中选择 **SAML**。保持此界面打开，以方便参考。

如果愿意，您可以在此阶段关闭**设置唯一的 SP 实体 ID** 选项。这样做会从 SP 实体 ID 值中移除组织 ID，但大多数情况下都建议打开该选项。

{% hint style="success" %}
还可以选择使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建 Okta 应用程序 <a href="#create-an-okta-app" id="create-an-okta-app"></a>

接下来，创建一个新的 Okta 应用程序：

1、在 Okta 管理门户中，转到 **Applications** → **Applications**。

2、选择 **Create App Integration**。

3、选择 **SAML 2.0**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6QTVpxi659XVt11Azdtoz/38f8eb0cb2d003de0bba59bf4a6fa3be/Create_new_app_for_SAML_2.0.png?w=935&#x26;fm=avif" alt=""><figcaption><p>创建新的 SAML 2.0 应用程序</p></figcaption></figure></div>

4、选择 Next，这将打开应用程序的通用配置。

5、在  **App name** 中输入一个唯一的、专用于 Bitwarden 的名称。

6、选择 **Next**。

### 配置 SAML <a href="#configure-saml" id="configure-saml"></a>

在 **Configure SAML** 界面，配置以下字段：

| 字段                          | 描述                                                                                                                                            |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Single sign on URL          | <p>将此字段设置为预先生成的<strong>断言消费者服务 (ACS) URL</strong>。<br></p><p>此自动生成的值可以从组织的<strong>设置</strong> → 单<strong>点登录</strong>界面复制，并且会根据您的设置而有所不同。</p> |
| Audience URI (SP Entity ID) | <p>将此字段设置为预先生成的 <strong>SP 实体 ID</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并且会根据您的设置而有所不同。</p>            |
| Name ID format              | 选择在 SAML 断言中使用的 [SAML NameID format](https://docs.oracle.com/cd/E19316-01/820-3886/ggwbz/index.html)。默认为 **Unspecified**。                     |
| Application username        | 选择用户用于登录 Bitwarden 的 Okta 属性，通常为 **Email**。                                                                                                   |

### 高级设置 <a href="#advanced-settings" id="advanced-settings"></a>

接下来，选择 **Show Advanced Settings**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7vxaIVnLCCTyb55hOpkctS/13481c873198fca937f2c92045bbc8c3/Show_Advanced_Settings.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>显示高级设置</p></figcaption></figure></div>

| 字段                  | 描述                                                                                 |
| ------------------- | ---------------------------------------------------------------------------------- |
| Response            | SAML 响应是否由 Okta 签名。                                                                |
| Assertion Signature | SAML 断言是否由 Okta 签名。                                                                |
| Signature Algorithm | 用于对响应和/或断言进行签名的签名算法，具体取决于设置为 **Signed** 的算法。默认为 `rsa-sha256`。                      |
| Digest Algorithm    | 用于对响应和/或断言进行签名的摘要算法，具体取决于设置为 **Signed** 的算法。此字段必须与已选择的 **Signature Algorithm** 匹配。 |

### 属性声明 <a href="#attribute-statements" id="attribute-statements"></a>

要在新的 Bitwarden 应用程序中定义属性声明：

1、转到 **Sign On** 选项卡。

2、在 **Attribute statements** 部分中，选择 **Show legacy configuration**。

3、选择 **Edit**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6zV8VlsjIKhynmkq6p1xpW/a85a7d67ba233cfeeb569c5861d0203b/Create_attribute_statements.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>创建属性声明</p></figcaption></figure></div>

4、默认情况下，下面会出现一行来用于构建属性声明。选择 **Add Another** 两次，以便您可以构建以下这三个 SP → IdP 属性映射。最后选择 **Save**：

| 名称        | 名称格式        | 值              |
| --------- | ----------- | -------------- |
| email     | Unspecified | user.email     |
| firstname | Unspecified | user.firstName |
| lastname  | Unspecified | user.lastName  |

### 获取 IdP 值 <a href="#get-idp-values" id="get-idp-values"></a>

还是在 **Sign On** 选项卡上，选择右侧的 **View Setup Instructions**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/20AjFNFk4VoBt2HrDtB9Zt/86bb2b1181f09d03b1ac7ac05844c46e/View_SAML_setup_instructions.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>查看 SAML 设置说明</p></figcaption></figure></div>

保留此页面以供[后面步骤](okta-saml-implementation.md#identity-provider-configuration)使用，或复制 **Identity Provider Single Sign-On URL** 和 **Identity Provider Issuer** 并下载 **X.509 Certificate**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3oc8QKbmtLzkZctLDxCCes/356c439aca47a5d0bca3c14ce0126ab2/IdP_values_.png?w=1106&#x26;fm=avif" alt=""><figcaption><p>IdP 值</p></figcaption></figure></div>

### 分配 <a href="#assignments" id="assignments"></a>

导航到 **Assignments** 选项卡然后选择 **Assign** 按钮：返回 Okta 中的 Bitwarden 应用程序配置，然后转到 **Assignments**。选择 **Assign**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1XoCbTbrAZV37R3wBTHgVl/0030e828cc635e1a70a719c94885f5ac/Assign_to_People_or_Groups.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>分配到人员或群组</p></figcaption></figure></div>

您可以使用 **Assign to People** 选项逐个用户地分配对应用程序的访问权限，或使用 **Assign to Groups** 选项来批量分配。

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已经在 Okta 管理门户中配置好了您所需要的一切。请返回 Bitwarden 网页 App 完成配置。

单点登录界面将配置分为两个部分：

* &#x20;**SAML 服务提供程序配置**将决定 SAML 请求的格式。
* &#x20;**SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据在 Okta 管理门户的[应用程序创建期间](okta-saml-implementation.md#create-an-okta-app)所选择的选项配置以下字段：

| 字段                                 | 描述                                                                                                        |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Name ID Format                     | 将其设置为[在 Okta 中指定的](okta-saml-implementation.md#configure-saml) NameID 格式。否则，请保留为 **Unspecified**。         |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                                |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                                         |
| Minimum Incoming Signing Algorithm | 将其设置为[在 Okta 中指定的](okta-saml-implementation.md#configure-saml) 签名算法。                                      |
| Want Assertions Signed             | 如果您[在 Okta 中](okta-saml-implementation.md#advanced-settings)将 Assertion Signature 字段设置为 **Signed**，请选中此框。 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。                |

完成服务提供程序配置部分后，**保存**您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要您返回 Okta 管理门户以获取这些值：

| 字段                                  | 描述                                                                                                                                                                                                                           |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                           | 输入您的 **Identity Provider Issuer**，这可以从 Okta 的 [**Sign On** 设置](okta-saml-implementation.md#get-idp-values)界面选择 **View Setup Instructions** 按钮来获取。                                                                            |
| Binding Type                        | 设置为 **Redirect**。Okta 目前不支持 HTTP POST。                                                                                                                                                                                       |
| Single Sign On Service URL          | 输入您的  **Identity Provider Single Sign-On URL**，这可以从 Okta 的 [**Sign On** 设置](okta-saml-implementation.md#get-idp-values)界面获取。                                                                                                 |
| Single Log Out Service URL          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。但是您可以根据需要预先配置它。                                                                                                                                                                            |
| X509 Public Certificate             | <p>黏贴<a href="okta-saml-implementation.md#get-idp-values">已下载的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>证书值区分大小写，多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm          | 选择[在 Okta 应用程序配置期间](okta-saml-implementation.md#advanced-settings)选择的签名算法。如果您没有更改签名算法，请将其保留为默认 (`rsa-sha256`)。                                                                                                               |
| Disable Outbound Logout Requests    | SSO 登录当前还**不支持** SLO。                                                                                                                                                                                                        |
| Want Authentication Requests Signed | Okta 是否要求 SAML 请求被签名。                                                                                                                                                                                                        |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**保存**您的工作。

{% hint style="success" %}
您可以通过激活[单点登录身份验证策略](../../oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication)来要求用户使用 SSO 登录。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，然后选择**使用单点登录**按钮进行测试：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3BdlHeogd42LEoG06qROyQ/c68021df4bf45d72e9d37b1fbf5a6040/login.png?w=517&#x26;fm=avif" alt=""><figcaption><p>登录选项界面</p></figcaption></figure></div>

输入[已配置的组织标识符](okta-saml-implementation.md#open-sso-in-the-web-app)，然后选择**继续**。如果您的实施已成功配置，您将被重定向到 Okta 的登录界面：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3Rh2Bg17sCE57xJsUKfqwN/8f6e1d8555c9e1b60d2e145d0f0bb565/Log_in_with_Okta.png?w=500&#x26;fm=avif" alt=""><figcaption><p>Okta 登录</p></figcaption></figure></div>

使用您的 Okta 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="success" %}
Bitwarden 不支持未经请求的响应，因此从您的 IdP 发起登录将导致错误。SSO 登录流程必须从 Bitwarden 发起。Okta 管理员可以创建一个 [Okta Bookmark App](https://support.okta.com/help/s/article/How-do-you-create-a-bookmark-app?language=en_US)，该应用程序将直接链接到 Bitwarden 网页密码库的登录页面。

1. 作为管理员，导航至主导航栏上的 **Applications** 下拉菜单，然后选择 **Applications**。
2. 单击 **Browse App Catalog**。
3. 搜索 **Bookmark App** 然后单击 **Add Integration**。
4. 将以下设置添加到应用程序：
   1. 为应用程序提供一个名称，例如 **Bitwarden Login**。
   2. 在 **URL** 字段中，提供 Bitwarden 客户端的 URL，例如 `https://vault.bitwarden.com/#/login` 或 `your-self-hostedURL.com`。
5. 选择 **Done** 然后返回到应用程序仪表板，然后编辑新创建的应用程序。
6. 将人员和群组分配给应用程序。您还可以为应用程序分配一个用于最终用户识别的 Logo。Bitwarden Logo 可以从[此处](https://github.com/bitwarden/brand/tree/master)获取。

完成此过程后，分配的人员和群组将在其 Okta 仪表板上拥有一个 Bitwarden 书签应用程序，该应用程序将他们直接链接到 Bitwarden 网页密码库的登录页面。
{% endhint %}

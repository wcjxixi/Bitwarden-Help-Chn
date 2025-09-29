# AWS SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-aws/)
{% endhint %}

本文是**专门针对 AWS** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页 App 和 AWS 控制台中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

{% hint style="success" %}
**已经是 SSO 专家？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/K4Z8ny0RzKkHKIJlZ4hh1/76a6643237e3bb45dee6913d2b29a9c4/saml-aws-sample.zip)
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

## 创建 AWS SSO 应用程序 <a href="#create-an-aws-sso-application" id="create-an-aws-sso-application"></a>

在 AWS 控制台中，导航到 **AWS SSO**，从导航中选择 **Applications**，然后选择 **Add a new application** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/62rVtvK7sT2nzJTRkunmCe/f81a48dc09cf26e25421e17bfd26d343/aws-newapp.png?fm=webp&h=398&q=50&w=1113" %}
添加新的应用
{% endembed %}

在搜索栏下方，选择 **Add a custom SAML 2.0 application** 选项：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/46dB0jiUsLRWJmzsvGkom2/b51811ee1b0f0da5983bbdb4f37027d9/aws-newapp2.png?fm=webp&h=332&q=50&w=898" %}
添加自定义 SAML 应用
{% endembed %}

### 详情 <a href="#details" id="details"></a>

为此应用程序提供一个唯一的、专用于 Bitwarden 的 **Display Name**。

### AWS SSO 元数据 <a href="#aws-sso-metadata" id="aws-sso-metadata"></a>

您需要此部分中的信息，以进行后续的配置步骤。复制 **AWS SSO sign-in URL** 和 **AWS SSO issuer URL**，然后下载 **AWS SSO certificate**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3Bw1LUH9z4rcYhMW705GLg/6a3dda29baac8451740be8d39e553c37/aws-values.png?fm=webp&h=342&q=50&w=885" %}
AWS SSO 元数据
{% endembed %}

### 应用程序属性 <a href="#application-properties" id="application-properties"></a>

在 **Application start URL** 字段中，指定用户将从其访问 Bitwarden 的登录 URL。对于托管云的客户，此地址始终为 `https://vault.bitwarden.com/#/sso`。对于自托管实例，这取决于您[配置的服务器 URL](../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain)，例如为 `https://your.domain/#/sso`。

### 应用程序元数据 <a href="#application-metadata" id="application-metadata"></a>

在应用程序元数据部分中，选择此选项以手动输入元数据的值：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3pa6K0UVEXEpjR7BQmeZzv/1b4eec5d43c1c3c6a1813e74e2d2eca5/aws-metadata.png?fm=webp&h=239&q=50&w=1029" %}
输入元数据值
{% endembed %}

配置以下字段：

| 字段                        | 描述                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Application ACS URL       | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>Assertion Consumer Service (ACS) URL</strong>。</p><p></p><p>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2/your-org-id/Acs</code>。对于自托管实例，这由您<a href="../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2/your-org-id/Acs</code>。</p> |
| Application SAML audience | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>SP Entity ID</strong>。</p><p></p><p>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2</code>。对于自托管实例，这由您<a href="../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2</code>。</p>                                                         |

完成后，选择 **Save changes**。

### 属性映射 <a href="#attribute-mappings" id="attribute-mappings"></a>

导航到 **Attribute mappings** 选项卡然后配置如下映射：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5UQnkRhZglhfpsxgQMFEgK/9bf44344e254a5d188e65d707397057b/aws-attr.png?fm=webp&h=533&q=50&w=1265" %}
属性映射
{% endembed %}

| 应用程序中的用户属性 | 映射到 AWS SSO 中的此字符串值或用户属性 | 格式           |
| ---------- | ------------------------ | ------------ |
| Subject    | `${user:email}`          | emailAddress |
| email      | `${user:email}`          | emailAddress |

### 分配用户 <a href="#assigned-users" id="assigned-users"></a>

导航到 **Assigned users** 选项卡并选择 **Assign users** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5IRbGNxLqP4W1Ym703pkV3/3fe10a03861961740865509f6c06e542/aws-assign.png?fm=webp&h=391&q=50&w=1265" %}
分配用户
{% endembed %}

您可以单独或按群组将用户分配给应用程序。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，你已经在 AWS 控制台范围内配置好了你所需要的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。



### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

服务提供程序配置应该已完成​​，但您可以选择编辑以下任何字段：

| 字段                                 | 描述                                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------------------ |
| Name ID Format                     | 将其设为 **Email Address**。                                                                    |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                 |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                          |
| Minimum Incoming Signing Algorithm | 默认，AWS SSO 将使用 SHA-256 签名。除非您进行了更改，否则请从下拉列表中选择 `sha256`。                                   |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名。                                                                 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。 |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 AWS 控制台以获取应用程序的值：

| 字段                                        | 描述                                                                                                                                                                                                                   |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | 输入从 AWS 控制台的 [AWS SSO metadata](https://bitwarden.com/help/article/saml-aws/#aws-sso-metadata) 部分获取到的 **AWS SSO issuer URL**。                                                                                        |
| Binding Type                              | 设置为 **HTTP POST** 或 **Redirect**。                                                                                                                                                                                    |
| Single Sign On Service URL                | 输入从 AWS 控制台的 [AWS SSO metadata](https://bitwarden.com/help/article/saml-aws/#aws-sso-metadata) 部分获取到的 **AWS SSO sign-in URL**。                                                                                       |
| Single Log Out Service URL                | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发，但是您可以将其预先配置为 **AWS SSO sign-out URL**，从 AWS 控制台的 [AWS SSO metadata](https://bitwarden.com/help/article/saml-aws/#aws-sso-metadata) 部分获取。                                            |
| Artifact Resolution Service URL           | 对于 AWS 实施，您可以将此字段保留为空。                                                                                                                                                                                               |
| X509 Public Certificate                   | <p>黏贴<a href="aws-saml-implementation.md#aws-sso-metadata">已下载的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 默认，AWS SSO 将使用 SHA-256 签名。除非您进行了更改，否则请从下拉列表中选择 `sha256`。                                                                                                                                                             |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                 |
| Disable Outbound Logout Requests          | SSO 登录当前**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                    |
| Want Authentication Requests Signed       | AWS SSO 是否要求 SAML 请求被签名。                                                                                                                                                                                             |

{% hint style="info" %}
填写 X509 证书时，请注意到期日期。必须续签证书，以防止向 SSO 最终用户提供的服务中断。如果证书已过期，管理员和所有者账户将始终可以使用电子邮箱地址和主密码登录。
{% endhint %}

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../admin-console/oversight-visibility/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 或 [https://vault.bitwarden.eu](https://vault.bitwarden.eu/)，输入您的电子邮箱地址，选择**继续**，然后选择**企业单点登录**按钮来进行测试：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3BdlHeogd42LEoG06qROyQ/cab8e66d8745059e73c02739d9d2d744/2024-12-02_10-28-02.png?_a=DAJAUVWIZAAB" %}
登录选项界面
{% endembed %}

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 IAM Identity Center 登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4zu0GVni1vyxMB0TayruvF/923cfdd3b641eb877bdf425e13d0ee5e/aws-login.png?fm=webp&h=544&q=50&w=375" %}
AWS 登录界面
{% endembed %}

使用您的 IAM Identity Center 凭据进行身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持非请求响应，因此从您的 IdP 发起登录会导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

# Google SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-google/)
{% endhint %}

本文是**专门针对** **Google Workspace** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页 App 和 Google Workspace 控制台中同时进行。在您继续进行操作时，我们建议您准备好这两样东西，并按照文档中的顺序完成这些步骤。

{% hint style="success" %}
**已经是 SSO 专家？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/2qc3QwfnmHhjJ5RCwL5hQN/aedad77e918df194f3033a34a141fcec/saml-google-sample.zip)
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
您可以选择性使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md) 和 [Key Connector](../about-key-connector.md)。
{% endhint %}

## 创建 SAML 应用程序 <a href="#create-a-saml-app" id="create-a-saml-app"></a>

在 Google Workspace 管理控制台中，从导航中选择 **Apps → Web and mobile apps**，在 Web and mobile apps 界面，选择 **Add App → Add custom SAML app**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/C9jyVEQXkiBxRwU82ix0U/c9cda4568d3a7f43170e4b3ef0aebab4/g-addapp.png?fm=webp&h=572&q=50&w=1065" %}
创建 SAML 应用程序
{% endembed %}

### 应用程序详细信息 <a href="#app-details" id="app-details"></a>

在应用程序详细信息界面，为应用程序指定一个唯一的专用于 Bitwarden 的名称，然后选择 **Continue** 按钮。

### Google 身份提供程序详细信息 <a href="#google-identity-provider-details" id="google-identity-provider-details"></a>

在 Google 身份提供程序详细信息界面，复制 **SSO URL**、**Entity ID** 和 **Certificate** 以[供后续步骤使用](google-saml-implementation.md#identity-provider-configuration)：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6YxeYEY4VdrJNYO0zYkPqd/bbe5b99b54570ef14f7a4ff5a1bcb7a6/g-details.png?fm=webp&h=1094&q=50&w=1091" %}
IdP 详细信息
{% endembed %}

完成后选择 **Continue**。

### 服务提供程序详细信息 <a href="#service-provider-details" id="service-provider-details"></a>

在服务提供程序详细信息界面，配置以下字段：

| 字段              | 描述                                                                                                                                                                                                                                                                                                                                                                                            |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ACS URL         | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>Assertion Consumer Service (ACS) URL</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2/your-org-id/Acs</code>。对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain/sso/saml2/your-org-id/Acs</code>。</p> |
| Entity ID       | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>SP Entity ID</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2</code>。对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2</code>。</p>                                                     |
| Start URL       | <p>可选。将此字段设置为用户访问 Bitwarden 的登录 URL。<br><br>对于云托管客户，其始终为 <code>https://vault.bitwarden.com/#/sso</code>。对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/#/sso</code>。</p>                                                                                     |
| Signed response | 如果您希望 Workspace 签名 SAML 响应，请选中此框。如果未选中，Workspace 将仅签名 SAML 声明。                                                                                                                                                                                                                                                                                                                                |
| Name ID format  | 将此字段设置为 **Persistent**（持久）。                                                                                                                                                                                                                                                                                                                                                                   |
| Name ID         | 选择 Workspace 用户属性，以填充 NameID。                                                                                                                                                                                                                                                                                                                                                                 |

完成后选择 **Continue**。

### 属性映射 <a href="#attribute-mapping" id="attribute-mapping"></a>

在属性映射界面，选择 **Add Mapping** 按钮并构建如下的映射：

| Google Directory 属性 | 应用程序属性 |
| ------------------- | ------ |
| Primary email       | email  |

选择 **Finish**。

### 开启应用程序 <a href="#turn-on-the-app" id="turn-on-the-app"></a>

默认，Workspace SAML 应用程序将 **OFF for everyone**（对所有人关闭）。打开 SAML 应用程序的 User Access（用户访问权限）部分，并根据您的需要，设置为 **ON for everyone**（对所有人开启）或对特定群组开启：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1cFjmvCmDIAMy6zy4e9x0a/03a1613a1186da2f014c40add256047e/g-activate.png?fm=webp&h=339&q=50&w=1431" %}
用户访问权限
{% endembed %}

**Save** 您的更改。

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已经在 Google Workspace 管理控制台中配置了所需的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据在 Workspace 管理控制台[设置期间](google-saml-implementation.md#service-provider-details)所选择的选项配置以下字段：

| 字段                                 | 描述                                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------------------ |
| Name ID Format                     | 将此字段设置为在 Workplace 中[所选择的 NameID 格式](duo-saml-implementation.md#saml-response)。            |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                 |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                          |
| Minimum Incoming Signing Algorithm | Bitwarden 在 SAML 响应中接受的最小签名算法。默认，Workplace 使用 SHA-256 进行签名。请从下拉列表中选择 `sha-256`。            |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 声明被签名。默认，Workspace SAML 应用程序将签名 SAML 声明，因此请选中此框。                       |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。 |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 Workplace 管理控制台以获取应用程序的值：

| 字段                                        | 描述                                                                                                                                                                                                                                      |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 | 将此字段设置为 Workplace 的 **Entity ID**，这可以从 [Google 身份提供程序详细信息部分](google-saml-implementation.md#google-identity-provider-details)或使用 **Download Metadata** 按钮来获取。                                                                            |
| Binding Type                              | 将此字段设置为 **HTTP POST** 或 **Redirect**。                                                                                                                                                                                                   |
| Single Sign On Service URL                | 将此字段设置为 Workplace 的 **SSO URL**，这可以从 [Google 身份提供程序详细信息部分](google-saml-implementation.md#google-identity-provider-details)或使用 **Download Metadata** 按钮来获取。                                                                              |
| Single Log Out Service URL                | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发，但是您可以根据需要预先配置它。                                                                                                                                                                                       |
| Artifact Resolution Service URL           | 对于 Workplace SAML 实现，将此字段留空。                                                                                                                                                                                                            |
| X509 Public Certificate                   | <p>黏贴<a href="google-saml-implementation.md#google-identity-provider-details">已获取的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 默认，Google Workspace 将使用 RSA SHA-256 进行签名。从下拉列表中选择 `sha-256`。                                                                                                                                                                            |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                                    |
| Disable Outbound Logout Requests          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                                      |
| Want Authentication Requests Signed       | Google Workspace 是否要求 SAML 请求被签名。                                                                                                                                                                                                       |

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 Google Workspace 的登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1hJ5ERnbj5UA7QriG0UPTb/95f36b9cb7573b1a966fe1331bf02fcd/g-login.png?fm=webp&h=524&q=50&w=484" %}
Google 登录界面
{% endembed %}

使用您的 Workspace 凭据进行身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

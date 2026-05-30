# AWS SAML

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-aws/)
{% endhint %}

本文是**专门针对 AWS IAM Identity Center** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](generic-saml.md)。

配置需要在 Bitwarden 网页 App 和 AWS 控制台中同时进行。操作过程中，我们建议同时打开这两个界面，并按照文档记录的步骤顺序完成操作。

{% hint style="success" %}
**已经是 SSO 专家了吗？**&#x8DF3;过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️** [下载示例](https://bitwarden.com/assets/6cXYk5OomUl81vXSdCBSb9/07061904608edcc18c168f9ac109f4cb/saml-aws-sample.zip)
{% endhint %}

## 在网页 App 中打开 SSO <a href="#open-sso-in-the-web-app" id="open-sso-in-the-web-app"></a>

登录到 Bitwarden [网页 App](https://bitwarden.com/help/getting-started-webvault/)，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

打开组织的**设置** → **单点登录**界面：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/20720mRAluo6crSdTiYJrn/1175889d7f6ab42fe7614f34cdd1dcdd/2024-12-04_09-41-15.png?w=1036&#x26;fm=avif" alt=""><figcaption><p>SAML 2.0 配置</p></figcaption></figure></div>

如果还没有为您的组织创建唯一的 **SSO 标识符**，请创建一个，然后从**类型**下拉菜单中选择 **SAML**。保持此界面打开，以方便参考。

如果愿意，您可以在此阶段关闭**设置唯一的 SP 实体 ID** 选项。这样做会从 SP 实体 ID 值中移除组织 ID，但大多数情况下都建议打开该选项。

{% hint style="success" %}
还可以选择使用**成员解密选项**。了解如何开始使用[受信任设备 SSO](../trusted-devices/about-trusted-devices.md) 或 [Key Connector](../../../self-hosting/key-connector/about-key-connector.md)。
{% endhint %}

## 创建应用程序 <a href="#create-an-application" id="create-an-application"></a>

在 AWS 控制台中，导航到 **AWS Identity Center**，从导航中选择 **Application assignments** → **Applications**，然后选择 **Add application** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/62rVtvK7sT2nzJTRkunmCe/1e1c14bd974785c0accce5f16b0f2ec0/IAMIDENTITY1.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>添加新应用程序</p></figcaption></figure></div>

在 Select application type 界面，选择 **I have an application I want to set up** 和 **SAML 2.0**。

### 配置应用程序 <a href="#configure-application" id="configure-application"></a>

在 Configure application 界面：

1、为应用程序指定一个唯一的、Bitwarden 专用的 **Display name**。

2、复制 **IAM Identity Center sign-in URL** 和 **IAM Identity Center issuer URL**，然后下载 **IAM Identity Center Certificate**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3Bw1LUH9z4rcYhMW705GLg/105b6b1eafbf1a1170d20ecd1ad1d800/IAMIDENTITY5.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>IAM 身份中心元数据</p></figcaption></figure></div>

3、在 **Application start URL** 字段中，指定用户访问 Bitwarden 的登录 URL。对于云托管客户，始终为 `https://vault.bitwarden.com/#/sso` 或 `https://vault.bitwarden.eu/#/sso`。对于自托管实例，这由您[已配置的服务器 URL](../../../self-hosting/deploy-and-configure/docker/linux-standard-deployment.md#configure-your-domain) 决定，例如 `https://your.domain/#/sso`：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/40VWgLzi5iccMIS9on3YkV/c12f4989b3aac0f93b3bfb6540e6e728/IAMIDENTITY6.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>IAM 身份中心应用程序属性</p></figcaption></figure></div>

4、在 Application metadata 部分中，选择 **Manually type your metadata values** 选项：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3pa6K0UVEXEpjR7BQmeZzv/da5b1f5f1141e8f05088251d00c3fd35/IAMIDENTITY6_copy.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>输入元数据值</p></figcaption></figure></div>

在该部分中，配置以下字段：

| 字段                        | 描述                                                                                                                                                              |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Application ACS URL       | <p>将此字段设置为从 Bitwarden SSO 配置界面中预先生成的<strong>断言消费者服务 (ACS) URL</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并且会根据您的设置而有所不同。</p> |
| Application SAML audience | <p>将此字段设置为从 Bitwarden SSO 配置界面中预先生成的 <strong>SP 实体 ID</strong>。<br><br>此自动生成的值可以从组织的<strong>设置</strong> → <strong>单点登录</strong>界面复制，并且会根据您的设置而有所不同。</p>         |

配置完成后，选择 **Submit**。

### 属性映射 <a href="#attribute-mappings" id="attribute-mappings"></a>

创建应用程序后，从 **Application assignments** → **Applications** 界面再次打开它。使用 **Actions** 下拉菜单 **Edit attribute mappings**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5UQnkRhZglhfpsxgQMFEgK/b71db32cd454b59f22b6dae143332982/IAMIDENTITY7.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>编辑属性映射</p></figcaption></figure></div>

配置以下映射然后 **Save changes**：

| 应用程序中的用户属性 | 映射到 IAM Identity Center 中的此字符串值或用户属性 | 格式           |
| ---------- | ------------------------------------ | ------------ |
| Subject    | `${user:email}`                      | emailAddress |
| email      | `${user:email}`                      | emailAddress |

### 分配用户 <a href="#assigned-users" id="assigned-users"></a>

在您的应用程序中，向下滚动到 Assigned users and groups 部分，然后选择 **Assign users and groups** 按钮：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5IRbGNxLqP4W1Ym703pkV3/31697ee57260a7136dae65ddf19209d9/IAMIDENTITY9.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>分配用户和群组</p></figcaption></figure></div>

将用户和群组分配给应用程序。

## 返回网页 App <a href="#back-to-the-web-app" id="back-to-the-web-app"></a>

至此，您已经在 AWS 控制台范围内配置好了您所需要的一切。请返回 Bitwarden 网页 App 完成配置。

单点登录界面将配置分为两个部分：

* &#x20;**SAML 服务提供程序配置**将决定 SAML 请求的格式。
* &#x20;**SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

服务提供程序配置应该已完成​​，但您可以选择编辑以下任何字段：

| 字段                                 | 描述                                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------------------ |
| Name ID Format                     | 将其设为 **Email Address**。                                                                    |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                 |
| Signing Behavior                   | SAML 请求是否/何时将被签名。                                                                          |
| Minimum Incoming Signing Algorithm | 默认，IAM Identity Center 将使用 SHA-256 签名。除非您进行了更改，否则请从下拉菜单中选择 `sha256`。                       |
| Want Assertions Signed             | Bitwarden 是否要求 SAML 断言被签名。                                                                 |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。 |

完成服务提供程序配置部分后，**保存**您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 AWS 控制台以获取应用程序的值：

| 字段                                  | 描述                                                                                                                                                                  |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                           | 输入从 AWS 控制台中您的应用程序的 IAM Identity Center metadata 部分获取到的 IAM Identity Center **issuer URL**。该字段区分大小写。                                                                |
| Binding Type                        | 设置为 **HTTP POST** 或 **Redirect**。                                                                                                                                   |
| Single Sign On Service URL          | 输入从 AWS 控制台中您的应用程序的 IAM Identity Center metadata 部分获取到的 IAM Identity Center **sign-in URL**。                                                                        |
| Single Log Out Service URL          | SSO 登录当前**不支持** SLO。该选项计划未来开发，但是您可以将其预先配置为从 AWS 控制台中您的应用程序的 IAM Identity Center metadata 部分获取到的 IAM Identity Center **sign-out URL**。                               |
| X509 Public Certificate             | <p>黏贴已下载的证书，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>证书值区分大小写，多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm          | 默认，IAM Identity Center 将使用 SHA-256 签名。除非您进行了更改，否则请从下拉菜单中选择 `sha256`。                                                                                                |
| Disable Outbound Logout Requests    | SSO 登录当前**不支持** SLO。该选项计划未来开发。                                                                                                                                      |
| Want Authentication Requests Signed | IAM Identity Center 是否要求 SAML 请求被签名。                                                                                                                                |

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

输入[已配置的组织标识符](aws-saml-implementation.md#open-sso-in-the-web-app)，然后选择**登录**。如果您的实施已成功配置，您将被重定向到 IAM Identity Center 登录界面:

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4zu0GVni1vyxMB0TayruvF/923cfdd3b641eb877bdf425e13d0ee5e/aws-login.png?w=375&#x26;fm=avif" alt=""><figcaption><p>AWS 登录界面</p></figcaption></figure></div>

使用您的 IAM Identity Center 凭据进行身份验证后，输入您的 Bitwarden 主密码以解密您的密码库！

{% hint style="info" %}
Bitwarden 不支持未经请求的响应，因此从您的 IdP 发起登录将导致错误。SSO 登录流程必须从 Bitwarden 发起。
{% endhint %}

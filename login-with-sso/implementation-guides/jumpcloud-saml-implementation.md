# JumpCloud SAML 实施

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/saml-jumpcloud/)
{% endhint %}

本文是**专门针对** **JumpCloud** 用于配置 SAML 2.0 方式的 SSO 登录的帮助。有关其他 IdP 方式配置 SSO 登录的帮助，请参阅 [SAML 2.0 配置](../saml-2.0-configuration.md)。

配置需要在 Bitwarden 网页密码库和 JumpCloud 门户网站中同时进行。在您继续进行操作时，我们建议您随时准备好并按照记录的顺序完成步骤。

{% hint style="success" %}
**已经是 SSO 专家？**跳过本文中的说明，然后下载示例配置，将里面的屏幕截图与您自己的配置进行比较。

**⬇️**[下载示例](https://assets.ctfassets.net/7rncvj1f8mw7/2jY7iejfs0KgdWBnwhGMHF/4bdd393ef26aac504ac2dd5b38cd283f/saml-jumpcloud-sample.zip)
{% endhint %}

## 打开业务门户 <a href="#open-the-business-portal" id="open-the-business-portal"></a>

## 在网页密码库中打开 SSO <a href="#open-sso-in-the-web-vault" id="open-sso-in-the-web-vault"></a>

如果你是直接从 [SAML 2.0 配置](../saml-2.0-configuration.md)过来的，你应该[已经创建了一个组织 ID](../saml-2.0-configuration.md#step-1-set-an-organization-identifier) 并打开了 SSO 配置界面。如果你没有，请参考那篇文章，为 SSO 创建一个组织 ID。

导航到您组织的**管理** → **单点登录**界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/20720mRAluo6crSdTiYJrn/62165bae24b421d4b8bbbdf601a18468/sso-saml1.png?fm=webp&h=652&q=50&w=822" %}
SAML 2.0 配置
{% endembed %}

你不需要编辑此界面上的任何内容，但要保持打开以方便引用。

{% hint style="success" %}
如果您是自托管 Bitwarden，您可以选择性使用**成员解密选项**。此功能默认情况下被禁用，因此现在继续使用**主密码**解密，并了解如何在配置完成并成功运行后开始使用 [Key Connector](../about-key-connector.md)。
{% endhint %}

## 创建 JumpCloud SAML 应用程序 <a href="#create-a-jumpcloud-saml-app" id="create-a-jumpcloud-saml-app"></a>

在 JumpCloud 门户网站中，从菜单中选择 **SSO** 并选择 **🞤Add** 图标：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4NL4Co6MKF71IDGMBDISyp/456a246be2bb037ad0d989d50049646e/jc-addapp.png?fm=webp&h=535&q=50&w=1076" %}
添加 JumpCloud 应用程序
{% endembed %}

在搜索框中输入 `Bitwarden` 并选择 **configure** 按钮：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2pFRcBTjlIjBhMbqlKMhxb/b80b23ecfd660d5c314028297c606879/jc-bw.png?fm=webp&h=229&q=50&w=685" %}
配置 Bitwarden
{% endembed %}

{% hint style="success" %}
如果您更喜欢 SAML，或者想要更多地控制 NameID 格式和签名算法等内容，请改为创建 **Custom SAML App**。
{% endhint %}

### 基本信息 <a href="#general-info" id="general-info"></a>

在 **General Info** 部分，配置以下信息：

| 字段            | 描述                          |
| ------------- | --------------------------- |
| Display Label | 为应用程序指定一个专用于 Bitwarden 的名称。 |

### 单点登录（SSO）配置 <a href="#single-sign-on-configuration" id="single-sign-on-configuration"></a>

在 **Single Sign-On Configuration** 部分，配置以下信息：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3GvG8DHkn0P1KYvNcrq2sc/d914a529cd0feacf67e833502fabac6c/jc-config.png?fm=webp&h=416&q=50&w=1090" %}
单点登录配置
{% endembed %}

| 字段            | 描述                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IdP Entity ID | 将此字段设置为唯一的、专用于 Bitwarden 的值，例如 `bitwardensso_yourcompany`.                                                                                                                                                                                                                                                                                                                                        |
| SP Entity ID  | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>SP Entity ID</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2</code>。对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2</code>。</p>                                                         |
| ACS URL       | <p>将此字段设置为从 Bitwarden SSO 配置界面预先生成的 <strong>Assertion Consumer Service (ACS) URL</strong>。<br><br>对于云托管客户，其始终为 <code>https://sso.bitwarden.com/saml2/your-org-id/Acs</code>。对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/sso/saml2/your-org-id/Acs</code>。</p> |

#### 仅对于自定义 SAML 应用程序 <a href="#custom-saml-app-only" id="custom-saml-app-only"></a>

如果您创建了自定义 SAML 应用程序，您还需要配置以下 **Single Sign-On Configuration** 字段：

| 字段                        | 描述                                                                                                                                                                                                                                                                                                     |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SAMLSubject NameID        | 指定将在 SAML 响应中作为 NameID 发送的 JumpCloud 属性。                                                                                                                                                                                                                                                               |
| SAMLSubject NameID Format | 指定在 SAML 响应中发送的 NameID 的格式。                                                                                                                                                                                                                                                                            |
| Signature Algoritm        | 选择用于签名 SAML 声明或响应的算法。                                                                                                                                                                                                                                                                                  |
| Sign Assertion            | 默认，JumpCloud 将对 SAML 响应进行签名。选中此框以签名 SAML 声明。                                                                                                                                                                                                                                                           |
| Login URL                 | <p>指定用户通过 SSO 登录 Bitwarden 的 URL。<br><br>对于云托管客户，其始终为 <code>https://vault.bitwarden.com/#/sso</code>。对于自托管实例，这由您<a href="../../self-hosting/install-and-deploy-guides/docker/linux-standard-deployment.md#configure-your-domain">配置的服务器 URL</a> 决定，例如为 <code>https://your.domain.com/#/sso</code>。</p> |

### 属性 <a href="#attributes" id="attributes"></a>

在 **Single Sign-On Configuration** → **Attributes** 部分，构建以下 SP → IdP 属性映射。如果您在 JumpCloud 中选择了 Bitwarden App，则这些应该已经构建：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5vRaXPal1HJsXhJZX8MdTL/b7c71fb6d4156d104f0f2b826f78a247/jc-attr.png?fm=webp&h=428&q=50&w=573" %}
属性映射
{% endembed %}

完成后，选择 **activate** 按钮。

### 下载证书 <a href="#download-the-certificate" id="download-the-certificate"></a>

应用程序激活后，再次使用 **SSO** 菜单选项打开已创建的 Bitwarden 应用程序。选择 **IDP Certificate** 下拉菜单并 **Download certificate**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6Y2DUGlm3LxBK6Ws44SjRg/a032010b5c0df73cccf7418892c9c00f/jc-cert.png?fm=webp&h=484&q=50&w=1416" %}
下载证书
{% endembed %}

### 绑定用户群组 <a href="#bind-users-groups" id="bind-users-groups"></a>

在 JumpCloud 门户网站中，从菜单中选择 **User Groups**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3nIOyl4xedMgTRTNobFqwG/35151b1af8594d15fd9d69531c5e4e04/jc-groups.png?fm=webp&h=452&q=50&w=1346" %}
用户群组
{% endembed %}

创建一个专用于 Bitwarden 的用户群组，或打开所有用户默认用户群组。在任一情况下，选择 **Applications** 选项卡并对该用户群组创建的 Bitwarden SSO 应用程序开启访问权限：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7BUUQUi79zmEy8xm64qwog/7d5537c45423a87f92485e7b6cad5d5e/jc-group-app.png?fm=webp&h=390&q=50&w=945" %}
绑定应用程序权限
{% endembed %}

{% hint style="success" %}
或者，您可以直接从 **SSO** → **Bitwarden Application** 界面绑定对用户群组的访问。
{% endhint %}

## 回到网页密码库 <a href="#back-to-the-web-vault" id="back-to-the-web-vault"></a>

至此，您已经在 JumpCloud 门户网站中配置了所需的一切。回到 Bitwarden 网页密码库来完成配置。

单点登录界面将配置分为两个部分：

* **SAML 服务提供程序配置**将决定 SAML 请求的格式。
* **SAML 身份提供程序配置**将决定用于 SAML 响应的预期格式。

### 服务提供程序配置 <a href="#service-provider-configuration" id="service-provider-configuration"></a>

根据在 JumpCloud 门户网站[设置期间](jumpcloud-saml-implementation.md#create-a-jumpcloud-saml-app)所选择的选项配置以下字段：

| 字段                                 | 描述                                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------------------ |
| Name ID Format                     | 如果您创建了自定义 SAML 应用程序，请将其设置为指定的 SAMLSubject NameID 格式内容。否则，请保留为 **Unspecified**。             |
| Outbound Signing Algorithm         | Bitwarden 用于签名 SAML 请求的算法。                                                                 |
| Signing Behavior                   | SAML 请求是否/何时将被签名。默认，JumpCloud 不要求对请求进行签名。                                                  |
| Minimum Incoming Signing Algorithm | 如果您创建了自定义 SAML 应用程序，请将其设置为您选择的签名算法。否则，保留为 `rsa-sha256`。                                    |
| Want Assertions Signed             | 如果您创建了自定义 SAML 应用程序，并且您在 JumpCloud 中设置了 **Sign Assertion** 选项，请选中此框。否则，保留为未选中。             |
| Validate Certificates              | 通过受信任的 CA 使用来自 IdP 的受信任和有效证书时，请选中此框。除非在 Bitwarden SSO 登录 docker 镜像中配置了适当的信任链，否则自签名证书可能会失败。 |

完成服务提供程序配置部分后，**Save**（保存）您的工作。

### 身份提供程序配置 <a href="#identity-provider-configuration" id="identity-provider-configuration"></a>

身份提供程序配置通常需要你返回 JumpCloud 门户网站以获取应用程序的值：

| 字段                                        | 描述                                                                                                                                                                                                                                 |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                 |  输入您的 JumpCloud **IdP Entity ID**，这可以从 JumpCloud [单点登录（SSO）配置部分](jumpcloud-saml-implementation.md#single-sign-on-configuration)来获取。                                                                                                |
| Binding Type                              | 设置为 **Redirect**。                                                                                                                                                                                                                  |
| Single Sign On Service URL                | 输入您的 JumpCloud **IdP URL**，这可以从 JumpCloud [单点登录（SSO）配置部分](jumpcloud-saml-implementation.md#single-sign-on-configuration)来获取。                                                                                                       |
| Single Log Out Service URL                | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                                 |
| Artifact Resolution Service URL           | 对于 JumpCloud 实现，您可以将此字段留空。                                                                                                                                                                                                         |
| X509 Public Certificate                   | <p>黏贴<a href="jumpcloud-saml-implementation.md#download-the-certificate">已获取的证书</a>，移除 <code>-----BEGIN CERTIFICATE-----</code>  和 <code>-----END CERTIFICATE-----</code>。<br><br>多余的空格、回车符和其他多余的字符<strong>将导致证书验证失败</strong>。</p> |
| Outbound Signing Algorithm                | 如果您创建了自定义 SAML 应用程序，请将其设置为您选择的签名算法。否则，保留为 `rsa-sha256`。                                                                                                                                                                            |
| Allow Unsolicited Authentication Response | SSO 登录当前**不支持**未经请求（由 IdP 发起）的 SAML 声明。该选项计划用于将来的开发。                                                                                                                                                                               |
| Disable Outbound Logout Requests          | SSO 登录当前还**不支持** SLO。该选项计划用于将来的开发。                                                                                                                                                                                                 |
| Want Authentication Requests Signed       | JumpCloud 是否要求 SAML 请求被签名。                                                                                                                                                                                                         |

完成身份提供程序配置部分后，**Save**（保存）您的工作。

{% hint style="success" %}
您可以通过激活单点登录身份验证策略来要求用户使用 SSO 登录。请注意，这需要先激活单一组织政策。[了解更多](../../organizations/enterprise-policies.md)。
{% endhint %}

## 测试配置 <a href="#test-the-configuration" id="test-the-configuration"></a>

配置完成后，通过导航到 [https://vault.bitwarden.com](https://vault.bitwarden.com) 并选择 **Enterprise Single Sign-On** 按钮来进行测试：

![企业 Single Sign-On 按钮](https://raw.githubusercontent.com/bitwarden/help/master/images/sso/sso-button-lg.png)

输入[已配置的组织标识符](../saml-2.0-configuration.md#step-1-enabling-login-with-sso)，然后选择 **Log In**。如果您的实施已成功配置，您将被重定向到 JumpCloud 的登录界面：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/678vDfFuKfH8FBZkhJdt5J/df1e8bad4f88f013ca194d9c9c82fccc/jc-login.png?fm=webp&h=522&q=50&w=486" %}
JumpCloud 登录界面
{% endembed %}

使用您的 JumpCloud 凭据进行身份验证后，输入您的 Bitwarden 主密码来解密您的密码库！

# SSO 解密选项

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/sso-decryption-options/)
{% endhint %}

SSO 登录的独特之处在于它保留了我们的零知识加密模型。Bitwarden 的任何人都没有您的密码库数据的访问权限，同样，**您的身份提供程序也没有**。这就是为什么 SSO 登录**将身份验证和解密分开**的原因。在所有 SSO 登录的实施中，您的身份提供程序不能也不会访问解密密码库数据所需的解密密钥。

**成员解密选项**用于确定在使用 SSO 登录处理身份验证的情况下将使用哪一种解密密钥来解密密码库数据。选项包括：

* **主密码**：通过身份验证后，组织成员将使用他们的[主密码](../../account/log-in-and-unlock/your-master-password.md)解密密码库数据。
* **受信任设备**： 允许用户使用 SSO 进行身份验证，并使用设备存储的加密密钥解密其密码库，而无需输入主密码。[了解更多](trusted-devices/about-trusted-devices.md)。
* **Key Connector**：链接 SSO 登录到您的自托管解密密钥服务器。使用此选项，组织成员无需使用其主密码来解密密码库数据。相反，[Key Connector](../../self-hosting/key-connector/about-key-connector.md) 将获取安全地存储在您拥有和管理的数据库中的解密密钥。

{% hint style="success" %}
由于存储解密密钥的敏感性，**Key Connector** 选项默认被禁用，目前仅可用于组织自托管 Bitwarden。

如果您对使用 Key Connector 感兴趣，请查看[关于 Key Connector](../../self-hosting/key-connector/about-key-connector.md) 和[部署 Key Connector](../../self-hosting/key-connector/deploy-key-connector.md) 文章并[联系我们](https://bitwarden.com/contact/)，以便我们安排时间以帮助您开始。
{% endhint %}

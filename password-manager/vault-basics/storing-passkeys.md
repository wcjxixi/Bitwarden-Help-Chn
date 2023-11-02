# =通行密钥

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/storing-passkeys/)
{% endhint %}

通行密钥可以通过 Bitwarden 密码管理器密码库存储和使用。使用 Bitwarden 浏览器扩展，用户可以登录自己喜欢的具有通行密钥登录功能的应用程序和网站。通行密钥是一种安全、无密码的替代方案，可供用户跨设备登录各种服务。

通行密钥根据 [FIDO 联盟](https://fidoalliance.org/overview/)制定的标准开发，允许用户保护其账户安全，并绕过标准密码身份验证带来的漏洞，如网络钓鱼。存储的通行密钥受到 Bitwarden 可信的端到端加密技术的保护。

## 什么是通行密钥？ <a href="#what-are-passkeys" id="what-are-passkeys"></a>

通行密钥是密码的替代品，可以让用户在不同设备上快速、方便、安全地登录网站和应用程序。更确切地说，"通行密钥 "是一个对消费者友好的术语，指的是一种可发现的 FIDO 凭证，它可以通过同步实现跨设备的安全无密码登录，或作为设备绑定通行密钥专用于单个硬件。

可以通过多种方法执行通行密钥验证：

* PIN
* 图案
* 密码
* 生物识别

根据您使用的设备和网站的不同，验证用于登录的通行密钥的选项也不同。有些用户可能会选择使用指纹验证，而有些用户则更喜欢熟悉的传统密码。

{% embed url="https://bitwarden.com/_gatsby/image/a8c5e7df5f115f4729299db21fe5d09d/c52224c8458622ef9ded640e5f63acee/unlock%20prompt.webp?eu=d9db59efebcffc84096ca5d06b76336ae96e02fff6503ed83830b7fb4af99f8570f01f5320907ab2286c5cd686b142b36f9579344cbcd68cc5bf19a7b830a20001865ded6fb17106547f91fbe2fd0741629e5e1ce1c0c217bc342f85b2e6f46e4a144a7aeb39edc5afb76b31f49c2870b4e5e0746494a325a715415083602b9533eccf8c5674a6b7fa1c8d929fdc7fbbfaf82c51418ffa322177451a59b97feef0b755243c2d495a3cc9ad5fc062c7e46e157e6600035ca43c559017a4317187fabbff0a&a=w%3D446%26h%3D353%26fm%3Dwebp%26q%3D75&cd=2023-11-01T12%3A58%3A48.103Z" %}
通行密钥操作系统提示
{% endembed %}

{% hint style="info" %}
密码可用于保护账户或用于验证通行密钥。在这两种情况下，密码的使用会有所不同。

* 当使用密码来验证通行密钥时，密码的目的是允许访问存储在设备上的私钥。
* 传统的密码验证用于访问存储在数据库中的账户信息。这是标准的用户名和密码登录流程。
{% endhint %}

通行密钥通过 Bitwarden 浏览器扩展进行存储和调用。这意味着可发现和不可发现的通行密钥都可以存储在 Bitwarden 中，并用于登录具有通行密钥功能的网站。

## 通行密钥存储 <a href="#passkey-storage" id="passkey-storage"></a>

### 创建新的通行密钥 <a href="#create-a-new-passkey" id="create-a-new-passkey"></a>

### 使用 Bitwarden 中存储的通行密钥登录网站 <a href="#sign-in-to-a-website-using-a-passkey-stored-in-bitwarden" id="sign-in-to-a-website-using-a-passkey-stored-in-bitwarden"></a>

## 通行密钥管理常见问题 <a href="#passkey-management-faq" id="passkey-management-faq"></a>

### 问：如果我没有主密码（受信任设备 SSO 或 Key Connector 用户），可以使用通行密钥吗？ <a href="#q-can-passkeys-be-used-if-i-do-not-have-a-master-password-sso-with-trusted-devices-or-key-connector" id="q-can-passkeys-be-used-if-i-do-not-have-a-master-password-sso-with-trusted-devices-or-key-connector"></a>

### 问：如果克隆密码库项目，是否会包含通行密钥？ <a href="#q-will-passkeys-be-included-if-you-clone-a-vault-item" id="q-will-passkeys-be-included-if-you-clone-a-vault-item"></a>

### 问：Bitwarden 导入和导出中是否包含存储的通行密钥？ <a href="#q-are-stored-passkeys-included-in-bitwarden-imports-and-exports" id="q-are-stored-passkeys-included-in-bitwarden-imports-and-exports"></a>

### 问：我可以在移动应用程序中存储通行密钥吗？ <a href="#q-can-i-store-passkeys-in-the-mobile-app" id="q-can-i-store-passkeys-in-the-mobile-app"></a>


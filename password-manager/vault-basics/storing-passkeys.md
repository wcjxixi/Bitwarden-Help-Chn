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

{% hint style="info" %}
保存和使用通行密钥是 Bitwarden 浏览器扩展的一项功能。其他 Bitwarden 客户端可用于查看已保存的通行密钥。
{% endhint %}

在 Bitwarden 密码库中，新字段现在将显示已存储的通行密钥。新的通行密钥保存后，可以从任意 Bitwarden 密码库查看该项目，该项目位于**通行密钥**字段中。

{% embed url="https://bitwarden.com/_gatsby/image/b5b3c6f21636107b8d055eaab91ce07b/d4b781c8bd57cc67014033106ffbc097/Passkey%20vault%20item.webp?eu=d78653b7e2caa8d4596aa18a397a666de53851fdac0563863963b6a949fa99d271fb4a03739c2ee528690f8ad7e747e965c37c661eead4d9c9bb4aa7ee66f95d01800cb866bb7353572c92afb1f653433ac01850a58a9a08f03e2687b1b4b3701c06142aac72ee89e4ad3762badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec3741281a7e18a84cf8e1f25b776e77390c3c97ed1fba7ec7e43b1c68765c0e52a464688450ae3e37c5e5f3f70b8a7b28e6aac8317183cab1e0bc59ef7123aea061f8c7673e6154e846f0a23ba985&a=w%3D800%26h%3D689%26fm%3Dwebp%26q%3D75&cd=2023-11-01T12%3A58%3A48.096Z" %}
通行密钥密码库项目
{% endembed %}

通行密钥字段不可编辑，该字段包含通行密钥的创建日期。

### 创建新的通行密钥 <a href="#create-a-new-passkey" id="create-a-new-passkey"></a>

在网站或应用程序上创建新的通行密钥时，Bitwarden 会提示您将此通行密钥存储在 Bitwarden 浏览器扩展中。

{% embed url="https://bitwarden.com/_gatsby/image/baf274466805ed1f10a19ef0af5a3cb6/bc05b959dd23600af6c51d12975aaa30/save%20passkey%20for%20login.webp?eu=d6df06b7b5ccafd2073af4d76e73686ab16a5efaf75232d16937b2f946fb968623f74f5024932ce42e6b5bdfd6b143ef66977e671de9d188c9be1ffcef33fb5b59db1eaa27f07a184e7299afe7a0455b3b824c09e2c09d4ce0732c81a1acb03247035a71a92cb0dcabae2a67ebd926789cc1f42f3bb8fc1fe2115837ae4903831aa4c18b3648eacab21ce9eeeaa009c8c8b42905458dfa347476181a0ee579b8a6b01b32686f1534759fec1b9c34dfd96a43234c020054ae3924900bac&a=w%3D850%26h%3D558%26fm%3Dwebp%26q%3D75&cd=2023-11-01T12%3A58%3A48.099Z" %}
保存通行密钥
{% endembed %}

{% hint style="info" %}
如果您不希望将通行密钥存储在 Bitwarden 密码库中，请选择**使用浏览器**。
{% endhint %}

如果该服务已存在一个通行密钥，浏览器扩展程序会通知您，并允许您通过选择 **➕** 图标以保存新的通行密钥，或覆盖现有的通行密钥。

{% hint style="info" %}
每个登录项目只能保存一个通行密钥。如果一个凭证保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

{% embed url="https://bitwarden.com/_gatsby/image/5112b24fae2615d9768475b703a6a1fb/f638faaddf60cc80a8a587f7c9b0af65/save%20or%20overwrite.webp?eu=8bda57e7e1cbff8f0e68a38b60206138b26b53a9f90463836f66ecf91ca897d077f11e5d72c029e52f6d5bdad3e844b864947d351cecd48b95bd4ef5ec31a20807850eec33e67851512397a8b6f155176fc3490ea2d0ca08a1652385e6b1b22610024d7dfa7fb883eafc3235e3832636bee7a2286f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32b9d2ec6d2b73611b3e438dc60e8326e9d547566055074004f334338303f23a3192e7ada05fd17e7db3fcce607082c5af86ed18a57e75e2d064f8c46e15514fc34cebe939b0903d425b9f6aa4c2&a=w%3D850%26h%3D554%26fm%3Dwebp%26q%3D75&cd=2023-11-01T12%3A58%3A48.092Z" %}
保存新的或覆盖通行密钥
{% endembed %}

要覆盖现有的通行密钥：

1. 从您选择的网站或服务开始创建一个新的通行密钥。
2. 选择您想要存储新通行密钥的现有登录项目，然后选择**保存通行密钥**。

在这里测试一下 [https://demo.yubico.com/playground](https://demo.yubico.com/playground)。

{% hint style="info" %}
无法在密码库项目视图中编辑通行密钥字段。如果需要同一网站的额外的通行密钥，请保存一个与新的通行密钥相关联的新登录项目。
{% endhint %}

### 使用 Bitwarden 中存储的通行密钥登录网站 <a href="#sign-in-to-a-website-using-a-passkey-stored-in-bitwarden" id="sign-in-to-a-website-using-a-passkey-stored-in-bitwarden"></a>

## 通行密钥管理常见问题 <a href="#passkey-management-faq" id="passkey-management-faq"></a>

### 问：如果我没有主密码（受信任设备 SSO 或 Key Connector 用户），可以使用通行密钥吗？ <a href="#q-can-passkeys-be-used-if-i-do-not-have-a-master-password-sso-with-trusted-devices-or-key-connector" id="q-can-passkeys-be-used-if-i-do-not-have-a-master-password-sso-with-trusted-devices-or-key-connector"></a>

### 问：如果克隆密码库项目，是否会包含通行密钥？ <a href="#q-will-passkeys-be-included-if-you-clone-a-vault-item" id="q-will-passkeys-be-included-if-you-clone-a-vault-item"></a>

### 问：Bitwarden 导入和导出中是否包含存储的通行密钥？ <a href="#q-are-stored-passkeys-included-in-bitwarden-imports-and-exports" id="q-are-stored-passkeys-included-in-bitwarden-imports-and-exports"></a>

### 问：我可以在移动应用程序中存储通行密钥吗？ <a href="#q-can-i-store-passkeys-in-the-mobile-app" id="q-can-i-store-passkeys-in-the-mobile-app"></a>


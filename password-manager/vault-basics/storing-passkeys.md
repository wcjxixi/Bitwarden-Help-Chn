# 存储通行密钥

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/storing-passkeys/)
{% endhint %}

可以通过 Bitwarden 密码管理器密码库存储和使用通行密钥。使用 Bitwarden 浏览器扩展，用户可以登录自己喜欢的具有通行密钥登录功能的应用程序和网站。通行密钥是一种安全、无密码的替代方案，可供用户跨设备登录各种服务。

通行密钥根据 [FIDO 联盟](https://fidoalliance.org/overview/)制定的标准开发，允许用户保护其账户安全，并绕过标准密码身份验证带来的漏洞（如网络钓鱼）。存储的通行密钥受到 Bitwarden 可信的端到端加密技术的保护。

## 什么是通行密钥？ <a href="#what-are-passkeys" id="what-are-passkeys"></a>

通行密钥是密码的替代品，可以让用户在不同设备上快速、方便、安全地登录网站和应用程序。更确切地说，「通行密钥」是一个对消费者友好的术语，指的是一种可发现的 FIDO 凭证，它可以通过同步实现跨设备的安全无密码登录，或作为设备绑定通行密钥专用于单个硬件。

当您保存或访问应用程序和服务时，应用程序和服务可以请求使用 PIN、密码、图案或生物识别因素验证使用它们创建的通行密钥。Bitwarden Password Manager 将在未来版本中添加对 PIN、密码和生物识别验证的支持。有关通行密钥的更多信息，请参阅[通行密钥常见问题](passkeys-faq.md)。

### 通行密钥的类型 <a href="#types-of-passkeys" id="types-of-passkeys"></a>

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

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/e_vectorize/q_auto/f_svg/v1/ctf/7rncvj1f8mw7/3kj9zFGb1nJgW236SUaBON/ace40f6c363a533381be89f5ca579a07/Screenshot_2024-03-06_at_1.01.15_PM.png?_a=BATAUVAA0" alt=""><figcaption><p>保存通行密钥</p></figcaption></figure>

{% hint style="info" %}
如果您不希望将通行密钥存储在 Bitwarden 密码库中，请选择**使用浏览器**。
{% endhint %}

如果该服务已存在一个通行密钥，浏览器扩展程序会通知您，并允许您通过选择 **➕** 图标以保存新的通行密钥，或覆盖现有的通行密钥。

{% hint style="info" %}
每个登录项目只能保存一个通行密钥。如果一个凭证保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/e_vectorize/q_auto/f_svg/v1/ctf/7rncvj1f8mw7/2GnYjzxkUFsYftwOSKz1Fi/7cf67ddcbf93581f57c97218b9553e4f/Screenshot_2024-03-06_at_1.02.00_PM.png?_a=BATAUVAA0" alt=""><figcaption><p>为现有登录保存通行密钥</p></figcaption></figure>

要覆盖现有的通行密钥：

1. 从您选择的网站或服务开始创建一个新的通行密钥。
2. 选择您想要存储新通行密钥的现有登录项目，然后选择**保存通行密钥**。

在这里测试一下 [https://demo.yubico.com/playground](https://demo.yubico.com/playground)。

{% hint style="info" %}
无法在密码库项目视图中编辑通行密钥字段。如果同一网站需要额外的通行密钥，请保存一个与新的通行密钥相关联的新的登录项目。
{% endhint %}

### 使用 Bitwarden 中存储的通行密钥登录网站 <a href="#sign-in-to-a-website-using-a-passkey-stored-in-bitwarden" id="sign-in-to-a-website-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的通行密钥，请在网站上启动通行密钥登录。您的系统将提示通行密钥登录。Bitwarden 启用后，Bitwarden 浏览器扩展将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项。

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5KeuUZox5shd0zDMxPHKXn/1c49a0c70ad63cabad33cfd213417e14/Screenshot_2024-03-06_at_1.02.35_PM.png?_a=BAJFJtWIB" alt=""><figcaption><p>使用通行密钥登录</p></figcaption></figure>

相关通行密钥将显示在 Bitwarden 对话框中。选择您要使用的通行密钥并按**确认**。

{% hint style="info" %}
如果此登录项目启用了主密码重新提示，您将需要重新输入主密码才能访问通行密钥。
{% endhint %}

## 关闭通行密钥提示 <a href="#turn-off-passkey-prompt" id="turn-off-passkey-prompt"></a>

如果您不想使用 Bitwarden 浏览器扩展程序提示您保存和使用特定站点的通行密钥，您可以设置[排除域名](../../miscellaneous/exclude-domains.md)。您还可以通过以下方式完全关闭提示：

1. 导航至 **⚙️设置**选项卡。
2. 选择**选项**。
3. 取消选中**询问保存和使用通行密钥**选项。

## 通行密钥管理常见问题 <a href="#passkey-management-faq" id="passkey-management-faq"></a>

以下常见问题与 Bitwarden 通行密钥存储有关。有关通行密钥的一般信息，请参阅[通行密钥常见问题](passkeys-faq.md)。

### 问：如果[克隆](../../your-vault/vault-items.md#clone)密码库项目，是否会包含通行密钥？ <a href="#q-will-passkeys-be-included-if-you-clone-a-vault-item" id="q-will-passkeys-be-included-if-you-clone-a-vault-item"></a>

**答：**完成克隆操作时，Bitwarden 不会复制通行密钥。

### 问：Bitwarden 导入和导出中是否包含存储的通行密钥？ <a href="#q-are-stored-passkeys-included-in-bitwarden-imports-and-exports" id="q-are-stored-passkeys-included-in-bitwarden-imports-and-exports"></a>

**答：**后期版本中将包含通行密钥导入和导出。

### 问：我可以在移动应用程序中存储通行密钥吗？ <a href="#q-can-i-store-passkeys-in-the-mobile-app" id="q-can-i-store-passkeys-in-the-mobile-app"></a>

**答：**计划在后期版本中提供对移动应用程序的通行密钥支持。


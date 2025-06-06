# 自动填充通行密钥

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/storing-passkeys/)
{% endhint %}

可以通过 Bitwarden Password Manager 存储和使用通行密钥。使用 Bitwarden 浏览器扩展和移动 App，用户可以登录自己喜欢的具有通行密钥登录功能的 App 和网站。通行密钥是一种安全、无密码的替代方案，可供用户跨设备登录各种服务。

{% hint style="info" %}
在 iOS 上，存储和使用通行密钥要求版本 17.0 或更高版本。[了解更多](../autofill-from/autofill-from-ios.md)。

在 Android 上，存储和使用通行密钥要求 14.0 或更高版本。可能需要额外的设置步骤。[了解更多](../autofill-from/autofill-from-android.md)。
{% endhint %}

通行密钥根据 [FIDO 联盟](https://fidoalliance.org/overview/)制定的标准开发，允许用户保护其账户安全，并绕过标准密码身份验证带来的漏洞（如网络钓鱼）。存储的通行密钥受到 Bitwarden 可信的端到端加密技术的保护。

## 什么是通行密钥？ <a href="#what-are-passkeys" id="what-are-passkeys"></a>

通行密钥是密码的替代品，可以让用户在不同设备上快速、方便、安全地登录网站和 App。更确切地说，「通行密钥」是一个对消费者友好的术语，指的是一种可发现的 FIDO 凭证，它可以通过同步实现跨设备的安全无密码登录，或作为设备绑定通行密钥专用于单个硬件。

App 和服务可以要求在保存或访问用它们创建的通行密钥时使用 PIN、密码、图案或生物识别因素进行验证。有关通行密钥的更多信息，请参阅[通行密钥 FAQ](../../../miscellaneous/passkeys-faq.md)。

### 通行密钥的类型 <a href="#types-of-passkeys" id="types-of-passkeys"></a>

通行密钥通过 Bitwarden 浏览器扩展和移动 App 进行存储和调用。这意味着，可被发现的通行密钥和不可被发现的 FIDO2 凭据都可以存储在 Bitwarden 中，并用于登录具有通行密钥功能的网站。

## 使用 Bitwarden 通行密钥 <a href="#using-passkeys-with-bitwarden" id="using-passkeys-with-bitwarden"></a>

{% hint style="info" %}
保存和使用通行密钥是 Bitwarden 浏览器扩展和移动 App 的一项功能。其他 Bitwarden 客户端可用于查看已保存的通行密钥。

* 在 iOS 上，存储和使用通行密钥要求版本 17.0 或更高版本。[了解更多](../autofill-from/autofill-from-ios.md)。
* 在 Android 上，存储和使用通行密钥要求 14.0 或更高版本。可能需要额外的设置步骤。[了解更多](../autofill-from/autofill-from-android.md)。
{% endhint %}

{% tabs %}
{% tab title="浏览器扩展" %}
{% hint style="info" %}
如果某个域名位于[**排除域名**](exclude-domains.md)列表中，Bitwarden 浏览器扩展就不会发出通行密钥提示。
{% endhint %}

### 询问保存和使用通行密钥 <a href="#ask-to-save-and-use-passkeys" id="ask-to-save-and-use-passkeys"></a>

要使用下述功能，请确保打开浏览器扩展**设置** → **通知**菜单中的**询问保存和使用通行密钥**选项。

如果您不希望在某些特定站点上使用 Bitwarden 通行密钥，您可以设置[排除域名](exclude-domains.md)。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，Bitwarden 会提示您存储此通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3kj9zFGb1nJgW236SUaBON/4a6fc1892506164f37586fa4a4fc9aa2/2024-10-29_11-33-21.png?_a=DAJCwlWIZAAB" %}
保存通行密钥
{% endembed %}

{% hint style="info" %}
如果您不希望将通行密钥存储在 Bitwarden 中，请选择**使用您的设备或硬件钥匙**。
{% endhint %}

如果该服务已存在一个通行密钥，Bitwarden 将允许您通过选择 **➕** 图标以创建一个新的项目来保存新的通行密钥，或覆盖现有的通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2GnYjzxkUFsYftwOSKz1Fi/e065e2784cd4b1eb21470fdfd64a35e9/2024-10-29_11-37-38.png?_a=DAJCwlWIZAAB" %}
为现有登录保存通行密钥
{% endembed %}

{% hint style="info" %}
每个登录项目只能保存一个通行密钥。如果一个凭据保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用存储在 Bitwarden 中的通行密钥，请在网站上发起通行密钥登录。当**询问保存和使用通行密钥**选项打开时，浏览器扩展将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

{% hint style="success" %}
[内嵌自动填充菜单](../autofill-from/autofill-from-browser-extensions.md#inline-auto-fill-menu)也可用于轻松使用通行密钥进行身份验证。
{% endhint %}

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5KeuUZox5shd0zDMxPHKXn/1aab35dfceed0ed9cdb17b143be9a890/2024-10-29_11-39-33.png?_a=DAJCwlWIZAAB" %}
使用通行密钥登录
{% endembed %}

选择您想要使用的通行密钥。

{% hint style="info" %}
如果您不希望将通行密钥存储在 Bitwarden 中或已创建的通行密钥未存储在 Bitwarden 中，请选择**使用您的设备或硬件密钥**。
{% endhint %}
{% endtab %}

{% tab title="iOS" %}
### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

要使用下述功能，请打开 iOS **设置** App 然后导航至**密码** → **密码选项**。打开以下选项：

* 打开**自动填充密码和通行密钥**。
* 在**密码和通行密钥来源：** 列表中打开 **Bitwarden**。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，iOS 应用程序将提示您存储此通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6rccoaRtUBbEnUjQxfSTNi/d033196df75950bae5bd7a20e8a7edd2/passkey-ios-1__1_.png?_a=BAJFJtWIB" %}
创建通行密钥
{% endembed %}

选择**继续**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**其他选项**，或者选择**其他登录选项**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

如果该服务已存在一个通行密钥，Bitwarden 将允许您通过选择 **➕** 图标以创建一个新的项目来保存新的通行密钥，或覆盖现有的通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6L5s6XBFjvaaEiDZ68m00Q/a130745c2276068fd0be066a47a34684/passkey-ios-2__1_.png?_a=BAJFJtWIB" %}
保存或覆盖通行密钥
{% endembed %}

不能为同一用户名和服务保存重复的通行密钥。如果您希望使用用户名和服务保存新的通行密钥，可以编辑或覆盖现有密码。

{% hint style="info" %}
每个登录项目只能保存一个通行密钥。如果一个凭证保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的密钥，请在网站上启动密钥登录。移动 App 将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/b6fY5o4CBxhW4ZjDIpanR/56ffdbf1ff93b7387be273bc7df15e6b/passkey-ios-3__1_.png?_a=BAJFJtWIB" %}
使用通行密钥登录
{% endembed %}

选择**继续**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**其他选项**，或者选择**其他登录选项**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}
{% endtab %}

{% tab title="Android" %}
### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

将 Bitwarden 应用程序更新到最新版本后，转到**设置** → **自动填充**然后点击**通行密钥管理**以访问 Android 设置，将 Bitwarden 配置为您的通行密钥提供程序。

{% hint style="danger" %}
要将 Bitwarden 激活为您的首选通行密钥提供程序，可能需要：

* 对于 Chrome 用户：
  * 导航至 `chrome://flags`，然后在 **Android 通行密钥凭据管理**下选择**启用第三方通行密钥提供程序**。如果未显示此选项，您的浏览器可能需要更新。
* 更新到最新版本后，禁用并重新启用 Bitwarden 作为自动填充提供程序。
* 更改上述设置后重新启动您的手机。
* 删除存储在 Google Password Manager 中的任何通行密钥，因为 Android 会优先选择该提供程序（确保不要删除任何会导致账户被锁定的重要的通行密钥）。

&#x20;另请注意，Android 不允许 Bitwarden 等第三方通行密钥提供程序支持基于通行密钥的 2FA（也称为「不可发现的凭据」）。

此外，虽然支持网络浏览器通行密钥，但对 App 的支持很快就会在未来的版本中推出。
{% endhint %}

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，Android 应用程序将提示您存储此通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4mBZ6s599BKxzn86CDwBhH/e2a313ab3dc263cd93f5da24e7cad778/passkey-android-1__1_.png?_a=BAJFJtWIB" %}
创建通行密钥
{% endembed %}

选择**创建**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**以另一种方式保存**，或者选择**更多已保存的登录**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}

如果该服务已存在一个通行密钥，Bitwarden 将允许您通过选择 **➕** 图标以创建一个新的项目来保存新的通行密钥，或覆盖现有的通行密钥：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/m8rHHqT8hmuEY7wB9WKld/573de4ef230d2d9cdbdcd94574b55168/passkey-android-2__1_.png?_a=BAJFJtWIB" %}
保存或覆盖通行密钥
{% endembed %}

{% hint style="info" %}
每个登录项目只能保存一个通行密钥。如果一个凭证保存在多个地方，例如作为两个登录项目分别保存在个人密码库和组织密码库中，则每个登录项目都可以保存不同的通行密钥。
{% endhint %}

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的密钥，请在网站上启动密钥登录。移动 App 将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2COiWur13OpX1QZ7Fy0tbR/65e2b4d39e2387fdcb0ba380ab52fa04/passkey-android-3__1_.png?_a=BAJFJtWIB" %}
使用通行密钥登录
{% endembed %}

选择**登录**以使用您的通行密钥登录。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**以另一种方式保存**，或者选择**更多已保存的登录**以使用未存储在 Bitwarden 中的通行密钥登录。
{% endhint %}
{% endtab %}
{% endtabs %}

## 查看 Bitwarden 中的通行密钥 <a href="#viewing-passkeys-in-bitwarden" id="viewing-passkeys-in-bitwarden"></a>

通行密钥保存后，可以从任何 Bitwarden App 查看它，其位于**通行密钥**字段中：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2SofQpuQstpo6gnIg9irwM/5ad0255aa61813dd55a6d4081e7c234d/2024-12-02_16-07-56.png?_a=DAJCwlWIZAAB" %}
您的密码库中的通行密钥
{% endembed %}

{% hint style="info" %}
如果此登录项目启用了主密码重新提示，您需要重新输入主密码才能访问此通行密钥。
{% endhint %}

### 删除通行密钥 <a href="#deleting-passkeys" id="deleting-passkeys"></a>

要从密码库项目中删除通行密钥：

1、从 Password Manager 网页 App、浏览器扩展或桌面 App 打开项目的**编辑**界面。

2、选择**通行密钥**字段的 ⛔删除图标。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/448nZ5ybyis0nUEwWsq6kt/8442776aca2a73eec13d30ce25b08f9a/2024-12-02_16-08-55.png?_a=DAJCwlWIZAAB" %}
删除通行密钥
{% endembed %}

## 通行密钥管理 FAQ <a href="#passkey-management-faq" id="passkey-management-faq"></a>

以下 FAQ 与 Bitwarden 通行密钥存储有关。有关通行密钥的一般信息，请参阅[通行密钥 FAQ](../../../miscellaneous/passkeys-faq.md)。

### 问：如果[克隆](../../../your-vault/vault-items.md#clone)密码库项目，是否会包含通行密钥？ <a href="#q-will-passkeys-be-included-if-you-clone-a-vault-item" id="q-will-passkeys-be-included-if-you-clone-a-vault-item"></a>

**答：**&#x5B8C;成克隆操作时，Bitwarden 不会复制通行密钥。

### 问：Bitwarden 导入和导出中是否包含存储的通行密钥？ <a href="#q-are-stored-passkeys-included-in-bitwarden-imports-and-exports" id="q-are-stored-passkeys-included-in-bitwarden-imports-and-exports"></a>

**答：**&#x901A;行密钥包含在 Bitwarden 的 .json 导出中。我们计划在未来的版本中提供将通行密钥转移到其他通行密钥提供程序或从其他通行密钥提供程序处转移通行密钥的功能。

### 问：我可以在移动 App 中存储通行密钥吗？ <a href="#q-can-i-store-passkeys-in-the-mobile-app" id="q-can-i-store-passkeys-in-the-mobile-app"></a>

**答：**&#x8BA1;划在后期版本中提供对移动应用程序的通行密钥支持。移动 App 通行密钥支持适用于 iOS（[了解更多](../autofill-from/autofill-from-ios.md)）和 Android（[了解更多](../autofill-from/autofill-from-android.md)）。


# 自动填充通行密钥

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/storing-passkeys/)
{% endhint %}

{% hint style="info" %}
Bitwarden 提供三种通行密钥功能：

* 从 Bitwarden 密码库为其他服务[保存和自动填充通行密钥](autofill-passkeys.md)
* [使用通行密钥登录和解锁](autofill-passkeys.md#log-in-and-unlock-with-your-passkey)您的 Bitwarden 账户 <mark style="color:red;">**ª**</mark>
* 使用[通行密钥 2FA](../../../account/two-step-login/setup-two-step-login/two-step-login-via-fido.md) 保护您的 Bitwarden 账户 <mark style="color:red;">**ª**</mark>

<mark style="color:red;">**ª**</mark> - 某些身份验证器，尤其是 Windows Hello，不允许您使用通行密钥进行登录和 2FA。
{% endhint %}

通行密钥是传统密码的安全替代方案，让您无需输入密码即可登录 App 和网站。根据 [FIDO 联盟](https://fidoalliance.org/overview/)制定的标准开发，绕过了标准密码可能存在的漏洞（如网络钓鱼）。

通行密钥保存在您的 Bitwarden 密码库中，并使用浏览器扩展或移动 App 在您日常使用的 App 和网站上自动填充它们。存储的通行密钥受 Bitwarden 可信赖的端到端加密保护。

## 什么是通行密钥？ <a href="#what-are-passkeys" id="what-are-passkeys"></a>

通行密钥是密码的替代方案，可以让用户在不同设备上快速、方便、安全地登录网站和 App。通行密钥指的是一种可发现的 FIDO 凭证，它可以通过同步实现跨设备的安全无密码登录，或作为设备绑定通行密钥专用于单个硬件。

App 和服务可以要求在保存或访问用它们创建的通行密钥时使用 PIN、密码、图案或生物识别因素进行验证。

### 通行密钥的类型 <a href="#types-of-passkeys" id="types-of-passkeys"></a>

通行密钥通过 Bitwarden 浏览器扩展和移动 App 进行存储和调用。可被发现的通行密钥和不可被发现的 FIDO2 凭据都可以存储在 Bitwarden 中，并用于登录具有通行密钥功能的网站。

## 使用 Bitwarden 保存和自动填充通行密钥 <a href="#using-passkeys-with-bitwarden" id="using-passkeys-with-bitwarden"></a>

{% tabs %}
{% tab title="浏览器扩展" %}
{% hint style="info" %}
浏览器扩展不会为[**排除域名**](exclude-domains.md)列表中的任何域名提供保存或使用通行密钥的选项。
{% endhint %}

### 允许浏览器扩展使用通行密钥 <a href="#allow-passkeys-with-the-browser-extension" id="allow-passkeys-with-the-browser-extension"></a>

首先打开浏览器扩展，然后进入**设置** → **通知**，确认**询问保存和使用通行密钥**选项已勾选。

如果您不希望在某些特定站点上使用 Bitwarden 通行密钥，您可以设置[排除域名](exclude-domains.md)。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，Bitwarden 会提示您存储此通行密钥：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3kj9zFGb1nJgW236SUaBON/4a6fc1892506164f37586fa4a4fc9aa2/2024-10-29_11-33-21.png?w=961&#x26;fm=avif" alt=""><figcaption><p>保存通行密钥</p></figcaption></figure></div>

{% hint style="info" %}
如果您不希望将通行密钥存储在 Bitwarden 中，请选择**使用您的设备或硬件密钥**。
{% endhint %}

每个登录项目只能保存一个通行密钥。如果某项服务已存在通行密钥，可覆盖现有通行密钥，或选择 <i class="fa-plus">:plus:</i> 添加图标来创建新的登录项目以存储额外的通行密钥：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2GnYjzxkUFsYftwOSKz1Fi/e065e2784cd4b1eb21470fdfd64a35e9/2024-10-29_11-37-38.png?w=961&#x26;fm=avif" alt=""><figcaption><p>为现有登录保存通行密钥</p></figcaption></figure></div>

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

首先，确认**询问保存和使用通行密钥**选项已开启。然后在网站上发起通行密钥登录。从弹出的窗口中选择已保存的通行密钥：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5KeuUZox5shd0zDMxPHKXn/1aab35dfceed0ed9cdb17b143be9a890/2024-10-29_11-39-33.png?w=961&#x26;fm=avif" alt=""><figcaption><p>使用通行密钥登录</p></figcaption></figure></div>

或者，也可以使用[内嵌自动填充菜单](../autofill-from/autofill-from-browser-extensions.md#inline-auto-fill-menu)通过通行密钥进行身份验证。

{% hint style="info" %}
如果您之前选择了**使用您的设备或硬件密钥**，Bitwarden 将不会提供输入或保存通行密钥的选项。如果您误点了此选项或改变了主意，请将该网站从[屏蔽的域名](blocking-autofill.md)中移除。下次您访问该服务的登录页面时，Bitwarden 会询问是否保存您的通行密钥。
{% endhint %}
{% endtab %}

{% tab title="iOS" %}
您可以在 iOS 17.0+ 版本中通过 Bitwarden 保存和使用通行密钥。

### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

要允许 Bitwarden 在 iOS 中存储和使用通行密钥：

1. 打开 iOS **设置** App。
2. 前往**密码** → **查看自动填充设置。**
3. 点击**自动填充密码和通行密钥**。此时将显示可存储通行密钥的 App 列表。
4. 点击 **Bitwarden**。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，iOS App 将提示您存储此通行密钥：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6rccoaRtUBbEnUjQxfSTNi/d033196df75950bae5bd7a20e8a7edd2/passkey-ios-1__1_.png?w=500&#x26;fm=avif" alt=""><figcaption><p>创建通行密钥</p></figcaption></figure></div>

选择**继续**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**其他选项**。
{% endhint %}

每个登录项目只能保存一个通行密钥。如果某项服务已存在通行密钥，可覆盖现有通行密钥，或选择 <i class="fa-plus">:plus:</i> 添加图标来创建新的登录项目以存储额外的通行密钥：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6L5s6XBFjvaaEiDZ68m00Q/a130745c2276068fd0be066a47a34684/passkey-ios-2__1_.png?w=500&#x26;fm=avif" alt=""><figcaption><p>保存或覆盖通行密钥</p></figcaption></figure></div>

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的通行密钥，请在网站上发起通行密钥登录。移动 App 将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/b6fY5o4CBxhW4ZjDIpanR/56ffdbf1ff93b7387be273bc7df15e6b/passkey-ios-3__1_.png?w=500&#x26;fm=avif" alt=""><figcaption><p>使用通行密钥登录</p></figcaption></figure></div>

选择**继续**。

{% hint style="info" %}
如果您更倾向于使用未存储在 Bitwarden 中的通行密钥登录，请选择**其他登录选项**。
{% endhint %}
{% endtab %}

{% tab title="Android" %}
您可以在 Android 14.0+ 版本中通过 Bitwarden 保存和使用通行密钥。

{% hint style="info" %}
在 Android 中，Bitwarden 存储的通行密钥只能用作主要的登录凭据。Android 不允许像 Bitwarden 这样的第三方通行密钥提供程序支持基于通行密钥的 2FA，也称为「不可发现凭据」。
{% endhint %}

### 设置 Bitwarden 以使用通行密钥 <a href="#setup-bitwarden-for-use-with-passkeys" id="setup-bitwarden-for-use-with-passkeys"></a>

要允许 Bitwarden 在 Android 中存储和使用通行密钥：

1. 打开 Bitwarden App。
2. 前往**设置** → **自动填充。**
3. 点击**通行密钥管理**。
4. 点击**继续**。
5. 这将打开您设备的设置 App。将 Bitwarden 配置为您的通行密钥提供程序。

### 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

在网站或 App 上创建新的通行密钥时，Bitwarden Android App 将提示您存储此通行密钥：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4mBZ6s599BKxzn86CDwBhH/e2a313ab3dc263cd93f5da24e7cad778/passkey-android-1__1_.png?w=500&#x26;fm=avif" alt=""><figcaption><p>创建通行密钥</p></figcaption></figure></div>

选择**创建**。

{% hint style="info" %}
如果您不想将此通行密钥存储在 Bitwarden 中，请选择**以另一种方式保存**。
{% endhint %}

每个登录项目只能保存一个通行密钥。如果某项服务已存在通行密钥，可覆盖现有通行密钥，或选择 <i class="fa-plus">:plus:</i> 添加图标来创建新的登录项目以存储额外的通行密钥：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/m8rHHqT8hmuEY7wB9WKld/573de4ef230d2d9cdbdcd94574b55168/passkey-android-2__1_.png?w=500&#x26;fm=avif" alt=""><figcaption><p>保存或覆盖通行密钥</p></figcaption></figure></div>

### 使用存储在 Bitwarden 中的通行密钥登录 <a href="#sign-in-using-a-passkey-stored-in-bitwarden" id="sign-in-using-a-passkey-stored-in-bitwarden"></a>

要使用 Bitwarden 中存储的通行密钥，请在网站上发起通行密钥登录。移动 App 将提供使用存储在 Bitwarden 密码库中的通行密钥登录的选项：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2COiWur13OpX1QZ7Fy0tbR/65e2b4d39e2387fdcb0ba380ab52fa04/passkey-android-3__1_.png?w=500&#x26;fm=avif" alt=""><figcaption><p>使用通行密钥登录</p></figcaption></figure></div>

选择**登录**以使用您的通行密钥登录。

{% hint style="info" %}
如果您更倾向于使用未存储在 Bitwarden 中的通行密钥登录，请选择**更多已保存的登录**。
{% endhint %}
{% endtab %}
{% endtabs %}

## 查看 Bitwarden 中的通行密钥 <a href="#viewing-passkeys-in-bitwarden" id="viewing-passkeys-in-bitwarden"></a>

通行密钥保存后，可以从任何 Bitwarden App 查看它，其位于**通行密钥**字段中：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2SofQpuQstpo6gnIg9irwM/5ad0255aa61813dd55a6d4081e7c234d/2024-12-02_16-07-56.png?w=1205&#x26;fm=avif" alt=""><figcaption><p>您的密码库中的通行密钥</p></figcaption></figure></div>

{% hint style="info" %}
如果此登录项目启用了主密码二次验证，您需要重新输入主密码才能访问此通行密钥。
{% endhint %}

### 删除通行密钥 <a href="#deleting-passkeys" id="deleting-passkeys"></a>

要从密码库项目中删除通行密钥：

1、从 Password Manager 网页 App、浏览器扩展或桌面 App 打开项目的**编辑**界面。

2、选择**通行密钥**字段的 <i class="fa-circle-minus">:circle-minus:</i>删除图标。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/448nZ5ybyis0nUEwWsq6kt/8442776aca2a73eec13d30ce25b08f9a/2024-12-02_16-08-55.png?w=694&#x26;fm=avif" alt=""><figcaption><p>删除通行密钥</p></figcaption></figure></div>

### 导出和导入通行密钥 <a href="#export-and-import-passkeys" id="export-and-import-passkeys"></a>

通行密钥包含在 Bitwarden 生成的 [JSON 导出](../../import-and-export/export-vault-data.md)文件中，导出后即可[导入到 Bitwarden 账户](../../import-and-export/import-data.md)中。

# 用于自动填充的 URI 的结构

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/uri-match-detection/)
{% endhint %}

在登录项目中包含统一资源标识符 (URI) 以使用自动填充，然后选择 ⮫**启动**图标直接从您的密码库打开网站或 App。URI 是一串字符，用于标识网站地址 (URL)、服务器 IP 地址、[移动 App 包 ID](forming-uris-for-autofill.md#uris-for-mobile-apps) 等。

## 将 URI 保存到登录项目 <a href="#save-uris-in-login-items" id="save-uris-in-login-items"></a>

当您创建或编辑登录项目时，请将其输入到**网站 (URI)** 字段中。当浏览器扩展自动保存新登录时，会自动填充网站的 URI。

您可以将多个 URI 添加到单个登录项目。要重新排序，请在网页 App 或浏览器扩展中编辑项目，然后将 URI 拖放到您的首选顺序中：

{% embed url="https://bitwarden.com/assets/aDbOEJ6x8G44gkDYcuHJ6/dfef7ac49894805dd0e1e718452e6a60/2025-03-25_09-45-56.png?w=967&fm=avif&q=80" %}
网页 App 中登录项目的 URI 字段
{% endembed %}

### 将 URI 保存到现有登录项目 <a href="#save-uri-to-existing-login-item" id="save-uri-to-existing-login-item"></a>

您可以使用浏览器扩展来自动填充与您尝试登录的网站没有匹配 URI 的登录项目。

1、打开浏览器扩展并找到您要填充的登录项目。该项目可以被搜索，或位于**所有项目**列表中。选择 **≡**&#x83DC;单然后选择**自动填充**。确认自动填充界面将显示在浏览器中。此界面将显示保存到登录项目的所有 URI，以及您当前所在网站的 URI。

{% embed url="https://bitwarden.com/assets/67h2UzB5cit1oVpEKTUcVs/dfeadfd6749961b76fb9746a36cc9085/2025-12-04_09-37-06.png?w=1200&fm=avif" %}

2、选择您想要执行的操作。

### URI 方案格式 <a href="#format-uri-schemes" id="format-uri-schemes"></a>

格式良好的 URI 在开头应包含一个方案，例如 `https://` 方案用来安全地引用网站地址。如果未指定方案，则假定为 `http://`。

方案包括：

* `http://` 或 `https://` 引用网站地址（例如：`https://www.github.com`）
* `androidapp://` 引用 Android App 的包 ID 或名称（例如：`androidapp://com.instagram.android`）

### 查找移动 App URI <a href="#find-uris-for-mobile-apps" id="find-uris-for-mobile-apps"></a>

获取 iOS 和 Android 设备上安装的 App 的 URI 可能比较麻烦。以下是在 iOS 和 Android App 上获取 URI 的一些提示：

{% tabs %}
{% tab title="iOS" %}
在 iOS 上，查找原生应用程序 URI 的最简单方法是：

1. 在 App 的登录界面，点击 **🔑密码**打开 Bitwarden。
2. 打开 Bitwarden 后，选择屏幕右上角的 ✚图标。
3. URI 将自动包含到新的密码库项目中（如果 App 允许），可以将其复制并粘贴到任何现有的登录项目中。
{% endtab %}

{% tab title="Android" %}
{% hint style="danger" %}
在 Android 上，Password Manager 使用包名称（例如 `com.google.android.gm`）在已安装的应用程序中自动填充。对于已安装的应用程序，请务必**仅安装并自动填充来自受信任来源**（例如 Google Play Store 或 F-Droid）**的应用程序**，

对于 Google Play Store 或 F-Droid 等外部​​来源，Android 不强制包名称的唯一性。这意味着恶意开发人员可以创建和分发旨在获取使用与官方知名应用程序相同的包名称（例如 `com.google.android.gm`）的凭据的应用程序。此类申请将通过自动填充提供，但您可以通过以下方式保护自己：

* 仅安装来自受信任来源的应用程序，例如 Google Play Store 或 F-Droid。
* 仅将凭据自动填充到官方版本的应用程序中。
{% endhint %}

在 Android 上，查找原生应用程序 URI 的最简单方法是：

1. 访问 Google Play 商店中的 App 页面。
2. 找到分享按钮并将链接复制到剪贴板。
3.  将复制的链接粘贴到可以阅读的地方。此链接看起来像这样：

    `https://play.google.com/store/apps/details?id=com.instagram.android`，`id=` 之后的值就是您的 URI，在本示例中为 `com.instagram.android`。
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Android 版本 13 及更高版本支持启动应用程序。
{% endhint %}

## 设置匹配检测 <a href="#match-detection-options" id="match-detection-options"></a>

您可以微调 Bitwarden 将您保存的 URI 与您当前使用的网站或 App 进行比较的方式，确保在合适的时间将您的凭据建议为自动填充。有多种[匹配检测选项](forming-uris-for-autofill.md#match-detection-options-1)可供选择。

### 默认匹配检测 <a href="#default-match-detection" id="default-match-detection"></a>

所有新登录项目的默认 URI 匹配方式是[**基础域名**](forming-uris-for-autofill.md#base-domain)。要更改您的账户的默认匹配检测：

1. 转到 **⚙️设置**。
2. 选择**自动填充**。
3. 从**默认 URI 匹配检测**下拉菜单中选择您的首选方式。

{% hint style="info" %}
如果**默认 URI 匹配检测**选项不存在，则是因为您的组织所有者或管理员已选择了[您的组织的默认匹配](../../../admin-console/oversight-visibility/enterprise-policies.md#default-uri-match-detection)。
{% endhint %}

### 按项目的匹配检测 <a href="#match-detection-by-item" id="match-detection-by-item"></a>

您还可以为各个项目更改匹配检测。在登录项目的**网站 (URI)** 字段中，选择 **⚙️设置**图标以选择匹配检测方式。这将覆盖您账户的默认匹配检测选项。

## 匹配检测选项 <a href="#match-detection-options" id="match-detection-options"></a>

分配给登录项目的每一个 URI 都有一个关联的匹配检测选项。该选项决定了 Bitwarden 何时将此登录作为自动填充，这通常是通过与具体的组成部分的匹配来确定的。下图对 URI 的组成部分进行了分解：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2J7AdBKH3DLQwoyGhNAWJA/7fcfdc4cf80202d9c90a1350a75542e2/urlgraphic.png?fm=webp&h=150&q=50&w=930" %}
URI 示意图
{% endembed %}

{% hint style="info" %}
由于 Android API 提供的自动填充服务的限制，Android Password Manager 客户端当前无法基于**端口**或**路径**来匹配 URI。
{% endhint %}

### 基础域名 <a href="#base-domain" id="base-domain"></a>

选择**基础域名**，当 URI 的顶级域名 (`.com`) 和二级域名 (`google`) 与检测到的资源相匹配时，Bitwarden 将弹出提示提供自动填充。实施基础域名匹配可与任何国家/地区代码顶级域名（例如 `.it` 或 `.co.uk`）配合使用。对于使用唯一域名（例如不同国家/地区）的站点，请创建其他基本域名条目。

例如，URI 为 `https://google.com`，使用基础域名匹配检测：

| URL                           | 自动填充？  |
| ----------------------------- | ------ |
| `http://google.com`           | **✔︎** |
| `https://accounts.google.com` | **✔︎** |
| `https://google.net`          | **✘**  |
| `http://yahoo.com`            | **✘**  |

{% hint style="info" %}
带有本地 TLD（例如 `http://mysite.local` 或 `https://mysite.lan`）或单术语主机名（例如 `http://localdevice`）URI 的用于自动填充的登录项目，将无法使用基础域名检测。我们建议使用[主机匹配](forming-uris-for-autofill.md#host)。
{% endhint %}

> **\[译者注]**：本地 TLD、单术语主机名，通常用于本地环境，而不是互联网上的公开服务。因此，Bitwarden 等工具无法对它们进行基础域名检测。
>
> * **本地 TLD (local TLD)**：TLD 是域名中最后一部分，即顶级域名，例如 `.com`、`.org` 等。本地 TLD 是指用于本地网络或开发环境的特殊顶级域名，例如 `.local`、`.lan` ，它不是互联网上公开注册的域名，而是专门为本地环境设计的，通常用于开发、测试或内部网络。
> * **单术语主机名 (Single-Term Hostname)**：主机名是域名的一部分，用于标识网络中的特定设备或服务。单术语主机名是指没有域名层级结构的简单主机名，例如 `http://localdevice`，这是一个非常简单的地址，仅包含主机名 (`localdevice`)，没有域名后缀 (如 `.com` 或 `.local`)。这种形式的主机名通常用于本地网络中的设备，例如路由器、打印机或其他本地服务。

### 主机 <a href="#host" id="host"></a>

{% hint style="info" %}
由于 Android API 提供的自动填充服务的限制，Android Password Manager 客户端当前无法基于**端口**或**路径**来匹配 URI。
{% endhint %}

选择**主机**，当主机名和端口（若指定了）与检测到的资源相匹配时，Bitwarden 将弹出提示以提供自动填充。

例如，URI 为 `https://sub.domain.com:4000`，使用主机匹配检测：

| URL                                     | 自动填充？  |
| --------------------------------------- | ------ |
| `http://sub.domain.com:4000`            | **✔︎** |
| `https://sub.domain.com:4000/page.html` | **✔︎** |
| `https://domain.com`                    | **✘**  |
| `https://sub.domain.com`                | **✘**  |
| `https://sub2.sub.domain.com:4000`      | **✘**  |
| `https://sub.domain.com:5000`           | **✘**  |

{% hint style="danger" %}
在使用[基于键盘的建议](../autofill-from/autofill-from-ios.md#keyboard-auto-fill)时，iOS 将始终使用基础域匹配自动填充建议。登录时打开 Bitwarden App，将允许您手动选择适当的 App 进行自动填充。
{% endhint %}

### 开始于 <a href="#starts-with" id="starts-with"></a>

选择**开始于**，当检测到的资源以登录项目的 URI 值开头（无论后面跟什么）时，Bitwarden 将弹出提示以提供自动填充。

例如，URI 为 `https://sub.domain.com/path/`，使用开始于匹配检测：

| URL                                                  | 自动填充？  |
| ---------------------------------------------------- | ------ |
| `https://sub.domain.com/path/`                       | **✔︎** |
| `https://sub.domain.com/path/page.html`              | **✔︎** |
| `https://sub.domain.com`                             | **✘**  |
| `https://sub.domain.com:4000/path/page.html`（被端口阻断了） | **✘**  |
| `https://sub.domain.com/path`（缺少斜杠）                  | **✘**  |

### 正则表达式 <a href="#regular-expression" id="regular-expression"></a>

{% hint style="danger" %}
正则表达式是一个高级选项，如果使用不正确，可能会非常危险。如果您完全不知道自己在做什么，则不应使用此选项。
{% endhint %}

选择**正则表达式**，当检测到的资源与一个指定的[正则表达式](https://zh.wikipedia.org/wiki/%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F)相匹配时，Bitwarden 将弹出提示以提供自动填充。正则表达式始终不区分大小写。

#### 不安全的示例 <a href="#unsafe-example" id="unsafe-example"></a>

URI 为 `^https://.*google\.com$`，使用正则表达式匹配检测：

| URL                                       | 自动填充？  |
| ----------------------------------------- | ------ |
| `https://google.com`                      | **✔︎** |
| `https://sub.google.com`                  | **✔︎** |
| `https://malicious-site.com?q=google.com` | **✔︎** |
| `http://google.com`                       | **✘**  |
| `https://yahoo.com`                       | **✘**  |

这可能比预期的要匹配得更多。考虑避免使用句号 (`.`)，除非转义 (`\`)，否则会匹配任意字符。

#### 安全的示例 <a href="#safe-example" id="safe-example"></a>

URI 为 `^https://[a-z]+\.wikipedia\.org/w/index\.php`，使用正则表达式匹配检测：

| URL                                                                               | 自动填充？  |
| --------------------------------------------------------------------------------- | ------ |
| `https://en.wikipedia.org/w/index.php?title=Special:UserLogin&returnto=Bitwarden` | **✔︎** |
| `https://pl.wikipedia.org/w/index.php?title=Specjalna:Zaloguj&returnto=Bitwarden` | **✔︎** |
| `https://en.wikipedia.org/w/index.php`                                            | **✔︎** |
| `https://malicious-site.com`                                                      | **✘**  |
| `https://en.wikipedia.org/wiki/Bitwarden`                                         | **✘**  |

### 精确 <a href="#exact" id="exact"></a>

选择**精确**，当登录项目的 URI 值与检测到的资源精确匹配时，Bitwarden 将弹出提示以提供自动填充。

例如，URI 为 `https://www.google.com/page.html`，使用精确匹配检测：

| URL                                          | 自动填充？  |
| -------------------------------------------- | ------ |
| `https://www.google.com/page.html`           | **✔︎** |
| `http://www.google.com/page.html`            | **✘**  |
| `https://www.google.com/page.html?query=123` | **✘**  |
| `https://www.google.com`                     | **✘**  |

{% hint style="success" %}
如表中所示，您可以使用精确匹配检测将自动填充限制为仅 `https://` 网站上。请注意，无论是否使用精确匹配，浏览器扩展都会在自动填充 HTTP 网站之前向用户发出警告，因为根据该项目保存的 URI，HTTPS 是预期的。
{% endhint %}

### 从不 <a href="#never" id="never"></a>

选择**从不**，Bitwarden 将从不为登录项目弹出以提供自动填充。

## 等效域名 <a href="#equivalent-domains" id="equivalent-domains"></a>

可以在网页密码库的**账户设置** → **域名规则**页面设置等效域名，这样就可以链接域名，以便于自动填充。例如，将 `turbotax.com` 和 `intuit.com` 设置为等效域名，意味着，将 `turbotax.com` 作为 URI 保存的密码库项目也将在 `intuit.com` 上提供自动填充。

Bitwarden 维护一个经过审核的主要网站的默认等效域名列表，例如 `apple.com` 和 `icloud.com`，以改善您的自动填填充体验。您可以将鼠标悬停在任何给定的等效域名上，然后使用 **⚙️**选项菜单选择 **✘排除**，以禁用该等效域名。

{% hint style="success" %}
对于使用[精确匹配检测](forming-uris-for-autofill.md#exact)的项目，等效域名将被忽略。例如，一个保存的 URI 为 `apple.com` 并设置为**精确**的项目，将不会为 `icloud.com` 提供自动填充，即使 `icloud.com` 是默认的等效域名。
{% endhint %}

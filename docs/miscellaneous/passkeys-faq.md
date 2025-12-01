# 通行密钥 FAQ

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/resources/passkeys-faq/)
{% endhint %}

> 这是 Bitwarden 资源库的一篇文章，我把它放在帮助中心，以便于理解什么是通行密钥 (Passkey)。

## 通行密钥概览 <a href="#passkey-overview" id="passkey-overview"></a>

### 什么是通行密钥以及它的工作原理？ <a href="#what-is-a-passkey-and-how-does-it-work" id="what-is-a-passkey-and-how-does-it-work"></a>

通行密钥是一种身份验证形式，可让您快速创建和登录账户，而无需使用安全性较低的密码。这种一步到位的安全登录方法取代了传统的身份验证方法以及双因素身份验证 (2FA) 过程。更妙的是，有了通行密钥，您再也不会创建弱密码了，因为您再也不需要创建密码了。

### 通行密钥会取代物理硬件钥匙（例如 YubiKey）吗？ <a href="#do-passkeys-replace-physical-yubikeys" id="do-passkeys-replace-physical-yubikeys"></a>

现代化的 YubiKey 可以作为一种通行密钥的形式。具体来说，它们就是所谓的安全密钥或「设备绑定的通行密钥」- 密钥本身保存在小型设备上，并且从不同步或备份。这可能会使它们比同步通行密钥更难使用，但在某些情况下可能更有用。

### 通行密钥与无密码相同吗？ <a href="#are-passkeys-the-same-as-passwordless" id="are-passkeys-the-same-as-passwordless"></a>

是的。由于通行密钥不需要密码，因此它们被视为无密码的身份验证方法。请注意，通行密钥通常比其他更容易被网络钓鱼的无密码身份验证方式更安全。

### 使用通行密钥的最佳方式是什么？ <a href="#whats-the-best-way-to-use-passkeys" id="whats-the-best-way-to-use-passkeys"></a>

通行密钥的使用比您想象的要简单得多。在您注册新账户时，您无需创建传统的用户名和密码（以及注册额外的两步登录），而是创建一个单一的通行密钥。如果通行密钥要求用户验证，该通行密钥可以与设备上的生物识别（如指纹扫描仪）结合使用。因此，当您登录账户时，只需通过生物识别验证即可进入。生物识别只会在您的设备上本地使用，绝不会发送到网站。

### 设置通行密钥的流程是怎样的？当我将来访问某个网站或应用程序时，该流程会发生怎样的变化？ <a href="#what-is-the-process-to-set-up-a-passkey-how-does-that-process-change-when-i-go-to-a-site-or-app-in-t" id="what-is-the-process-to-set-up-a-passkey-how-does-that-process-change-when-i-go-to-a-site-or-app-in-t"></a>

当以前使用传统用户名/密码的网站或应用程序支持通行密钥时，通常只需单击按钮即可创建您的第一个通行密钥。该过程就像解锁您的设备一样简单。在后台，当您创建通行密钥时，它将生成一对加密密钥。第一个是公钥，存储在您为其创建账户的网站上。第二个是私钥，存储在您的设备或 Bitwarden 密码库中。这对密钥对在您的设备上受到生物指纹或面部扫描的保护。

### 设置通行密钥时需要哪些信息？ <a href="#what-information-is-required-when-setting-up-a-passkey" id="what-information-is-required-when-setting-up-a-passkey"></a>

当您为站点创建通行密钥时，您必须首先使用现有的用户名和密码登录。然后，服务器将向您的浏览器推送一个请求，要求您提供特定的加密信息。然后，您必须使用诸如生物识别（指纹扫描仪或面部解锁）或您的设备 PIN 码来批准该请求。验证成功后，您的设备将生成密钥对，并将公钥发送到该站点。这就是您在设置通行密钥时需要提供的所有信息。

### 我的通行密钥存储在哪里？ <a href="#where-are-my-passkeys-stored" id="where-are-my-passkeys-stored"></a>

公钥存储在网站上，私钥存储在您的设备或您的通行密钥提供程序中，例如您的 Bitwarden 密码库。

## 通行密钥安全 <a href="#passkey-security" id="passkey-security"></a>

### 从安全角度来看，密码和通行密钥有何不同？ <a href="#from-a-security-perspective-how-do-passwords-and-passkeys-compare" id="from-a-security-perspective-how-do-passwords-and-passkeys-compare"></a>

通行密钥比传统的用户名/密码身份验证方法更安全，原因有很多。首先，您将无法使用易于破解的密码，例如「password」。此外，通行密钥中内置了 2FA，某人访问您账户的唯一方法是同时拥有私钥和您的生物识别登录信息或设备 PIN 码。

### 我的通行密钥需要 2FA 吗？ <a href="#do-i-need-2fa-with-my-passkey" id="do-i-need-2fa-with-my-passkey"></a>

不需要，因为 2FA 内置在登录过程中提供的网站的通行密钥中。每个网站都可能选择包含额外的登录步骤，但大多数网站都没有。

### 我的通行密钥会被破解吗？ <a href="#can-my-passkey-be-hacked" id="can-my-passkey-be-hacked"></a>

没有什么是 100% 万无一失的。然而，破解通行密钥需要付出相当大的努力，不仅要获得对存储私钥的设备的访问权限，还要侵入你的设备，例如重新创建您的生物识别登录信息（指纹或面部）或设备 PIN 码。因此，通行密钥比传统方法安全得多。

### 如果我丢失了手机怎么办？如何在没有密码之类的方式来验证自己身份的情况下恢复我的通行密钥？ <a href="#what-happens-if-i-lose-my-phone-how-do-i-recover-my-passkey-with-nothing-like-a-password-to-identify" id="what-happens-if-i-lose-my-phone-how-do-i-recover-my-passkey-with-nothing-like-a-password-to-identify"></a>

通行密钥通常能够在您的设备之间同步，但并非所有平台都支持这一点。Bitwarden 允许您将通行密钥存储在您的密码库中，该密码库已备份并在您的所有设备之间同步。如果您因某种原因丢失了通行密钥，大多数网站都应该有恢复选项，以便您可以为您的账户创建一个新的通行密钥。当然，这要根据每个网站的具体情况而定。

### 如果我的设备被盗怎么办？窃贼可以通过这种方式获取通行密钥吗？ <a href="#what-happens-if-my-device-is-stolen-can-a-thief-gain-access-to-passkeys-in-that-way" id="what-happens-if-my-device-is-stolen-can-a-thief-gain-access-to-passkeys-in-that-way"></a>

窃贼要想在设备上成功使用密码，唯一方法是他们也可以解锁您的设备，从而有效地获取对您的数据的完全访问权限。然而，每次使用通行密钥通常都需要用户验证，例如生物识别或重新输入设备密码，因此在解锁后窃取您的设备是远远不够的。

## 在 Bitwarden 中使用通行密钥 <a href="#using-passkeys-with-bitwarden" id="using-passkeys-with-bitwarden"></a>

### 谷歌最近宣布支持通行密钥。Bitwarden 宣布的事情和这个是一样的吗？ <a href="#google-recently-announced-passkey-support.-is-this-the-same-thing-that-bitwarden-is-announcing" id="google-recently-announced-passkey-support.-is-this-the-same-thing-that-bitwarden-is-announcing"></a>

部分一样。Google 宣布已为其 Workspaces 账户添加了通行密钥验证支持，这意味着用户可以使用通行密钥而不是常规密码登录其 Google Workspace。同样，Bitwarden 用户也可以用通行密钥代替主密码访问自己的 Bitwarden 账户。

Bitwarden 还宣布，用户将能够保存、存储以及管理与他们在密码库中使用的网站和应用程序相关联的已注册通行密钥。因此，Google 现在可以在账户中使用通行密钥，而 Bitwarden 也可以在密码库中存储通行密钥。

### 无论使用何种浏览器，我都要使用相同的通行密钥吗？还是每个网站要根据浏览器或设备使用不同的通行密钥？ <a href="#do-i-use-the-same-passkey-regardless-of-the-browser-im-on-or-will-each-site-require-a-different-pass" id="do-i-use-the-same-passkey-regardless-of-the-browser-im-on-or-will-each-site-require-a-different-pass"></a>

如果您使用 Bitwarden 来存储您的通行密钥，并且浏览器支持 Bitwarden 扩展（以及通行密钥的底层技术），您就可以使用相同的通行密钥访问您的账户，而无需创建新的通行密钥。如果您不将通行密钥存储在 Bitwarden 中，这将取决于浏览器与您的设备操作系统（通行密钥的存储位置）的集成程度。

### 支持通行密钥的网站有哪些？ <a href="#what-are-some-examples-of-sites-that-support-passkeys" id="what-are-some-examples-of-sites-that-support-passkeys"></a>

目前支持通行密钥的网站越来越多，包括 Best Buy、Cloudflare、eBay、Google、Kayak、PayPal 和 GitHub。[GitHub](https://github.com/passwordless/passkeys-index/blob/main/passkey-index.md) 上有一个来自社区的支持通行密钥的网站索引。

### 如何在 Bitwarden 中使用通行密钥？我还需要主密码吗？ <a href="#how-will-i-use-passkeys-with-bitwarden-do-i-still-need-a-master-password" id="how-will-i-use-passkeys-with-bitwarden-do-i-still-need-a-master-password"></a>

到 2023 年秋季，用户将可以使用通行密钥访问自己的账户，而无需主密码。用户还可以在自己的密码库中存储和保护他们的通行密钥。

### 通行密钥可以跨平台使用吗？如果不能，根据使用的平台使用不同的通行密钥是否有任何问题？ <a href="#can-passkeys-be-used-across-platforms-if-not-are-there-any-issues-with-having-different-passkeys-dep" id="can-passkeys-be-used-across-platforms-if-not-are-there-any-issues-with-having-different-passkeys-dep"></a>

最初，通行密钥只能在创建通行密钥的设备上使用。接下来，同步通行密钥将通过支持存储通行密钥的密码管理器（如 Bitwarden）跨设备存储和管理。

### 如果我采用它，我是否会被锁定为只能使用通行密钥？ <a href="#will-i-be-locked-into-using-passkeys-if-i-adopt-it" id="will-i-be-locked-into-using-passkeys-if-i-adopt-it"></a>

这取决于网站或账户。有些网站可能只提供通行密钥身份验证，而其他网站可能还会提供传统的用户名/密码身份验证、用户名/密码/2FA 身份验证。

### 可以与其他受信任的个人共享通行密钥吗？ <a href="#can-passkeys-be-shared-with-other-trusted-individuals" id="can-passkeys-be-shared-with-other-trusted-individuals"></a>

这取决于平台。包括 Bitwarden 在内的一些平台将允许与受信任的个人共享通行密钥。

### 如果我在使用通行密钥时遇到困难，是否有支持服务，例如与代表实时聊天？ <a href="#is-there-support-such-as-a-live-chat-representative-to-speak-with-if-im-having-trouble-with-my-passk" id="is-there-support-such-as-a-live-chat-representative-to-speak-with-if-im-having-trouble-with-my-passk"></a>

这将取决于网站。如果网站支持通行密钥身份验证，并且他们提供支持服务，他们将能够回答您有关该特定网站的通行密钥身份验证的问题。

### 如果我不想再使用我的通行密钥了，我可以将其移除吗？ <a href="#if-i-no-longer-want-to-use-my-passkey-can-i-remove-it" id="if-i-no-longer-want-to-use-my-passkey-can-i-remove-it"></a>

可以。执行此操作的方式与移除设备上的密码是一样的。

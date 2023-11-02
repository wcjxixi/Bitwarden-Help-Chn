# =\*通行密钥常见问题

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/resources/passkeys-faq/)
{% endhint %}

> 这是 Bitwarden 资源库的一篇文章，我把它放在帮助中心的「通行密钥」旁边，以便于理解什么是通行密钥 (Passkey)。

### 什么是通行密钥以及它是如何工作的？ <a href="#what-is-a-passkey-and-how-does-it-work" id="what-is-a-passkey-and-how-does-it-work"></a>

通行密钥是一种身份验证形式，可让您快速创建和登录账户，而无需使用安全性较低的密码。这种一步到位的安全登录方法取代了传统的身份验证方法以及双因素身份验证 (2FA) 过程。更妙的是，有了通行密钥，您再也不会创建弱密码了，因为您再也不需要创建密码了。

{% embed url="https://bitwarden.com/_gatsby/file/b071a13b1731fd9fdf7fd29584e73955/infographic-passkeys-large.gif?eu=8cdb04efb6c9f4d20f61a4d26877626cb66d01fdfe5337d66b31e3a84efc9cd32cf71850739579b0256d59d880e611bc6e9770324cef838f92ed1cf0e83dad5a53d052bf64b67204547ec4f6b7a4551768974951a4d0c10fa43f2385e3b7e6231e011a7ea97bb0d7eaf83f3cf4c76f71e0a9b9773893fc2da30c0d109d4932bf31ffd3c06d4baad1b75db1b5a8f3089b94ba6a005fdc886a797714672ebb49b8c5d5570e6641162070cfeb47cf67c3e5681b622b0b5601a1316ed154aa696091e4a8f555dd2c2ab5fece3671999af0d6b24dee7b36bf9674b4c26a394d56f95aeea127a690335310d673ac" %}

### 通行密钥可以取代物理 Yubikey 吗？ <a href="#do-passkeys-replace-physical-yubikeys" id="do-passkeys-replace-physical-yubikeys"></a>

现代化的 Yubikey 可以作为一种通行密钥的形式。具体来说，它们就是所谓的安全密钥或「设备绑定的通行密钥」- 密钥本身保存在小型设备上，并且从不同步或备份。这可能会使它们比同步通行密钥更难使用，但在某些情况下可能更有用。

### 使用通行密钥的最佳方式是什么？ <a href="#whats-the-best-way-to-use-passkeys" id="whats-the-best-way-to-use-passkeys"></a>

通行密钥的使用比您想象的要简单得多。在您注册新账户时，您无需创建传统的用户名和密码（以及注册额外的两步登录），而是创建一个单一的通行密钥。如果通行密钥要求用户验证，该通行密钥可以与设备上的生物识别（如指纹扫描仪）结合使用。因此，当您登录账户时，只需通过生物识别验证即可进入。生物识别只会在您的设备上本地使用，绝不会发送到网站。

### 设置通行密钥的流程是怎样的？当我将来访问某个网站或应用程序时，该流程会发生怎样的变化？ <a href="#what-is-the-process-to-set-up-a-passkey-how-does-that-process-change-when-i-go-to-a-site-or-app-in-t" id="what-is-the-process-to-set-up-a-passkey-how-does-that-process-change-when-i-go-to-a-site-or-app-in-t"></a>

当以前使用传统用户名/密码的网站或应用程序支持通行密钥时，通常只需单击按钮即可创建您的第一个通行密钥。该过程就像解锁您的设备一样简单。在后台，当您创建通行密钥时，它将生成一对加密密钥。第一个是公钥，存储在您为其创建账户的网站上。第二个是私钥，存储在您的设备或 Bitwarden 密码库中。这对密钥对在您的设备上受到生物指纹或面部扫描的保护。

### 设置通行密钥时需要哪些信息？ <a href="#what-information-is-required-when-setting-up-a-passkey" id="what-information-is-required-when-setting-up-a-passkey"></a>

当您为站点创建通行密钥时，您必须首先使用现有的用户名和密码登录。然后，服务器将向您的浏览器推送一个请求，要求您提供特定的加密信息。然后，您必须使用诸如生物识别（指纹扫描仪或面部解锁）或您的设备 PIN 码来批准该请求。验证成功后，您的设备将生成密钥对，并将公钥发送到该站点。这就是您在设置通行密钥时需要提供的所有信息。

### 我的通行密钥存储在哪里？ <a href="#where-are-my-passkeys-stored" id="where-are-my-passkeys-stored"></a>

公钥存储在网站上，私钥存储在您的设备或您的通行密钥提供商中，例如您的 Bitwarden 密码库。

### 如果我丢失了手机怎么办？如何在没有密码之类的方式来验证自己身份的情况下恢复我的通行密钥？ <a href="#what-happens-if-i-lose-my-phone-how-do-i-recover-my-passkey-with-nothing-like-a-password-to-identify" id="what-happens-if-i-lose-my-phone-how-do-i-recover-my-passkey-with-nothing-like-a-password-to-identify"></a>

通行密钥通常能够在您的设备之间同步，但并非所有平台都支持这一点。Bitwarden 允许您将密钥存储在您的密码库中，该密码库已备份并在您的所有设备之间同步。如果您因某种原因丢失了通行密钥，大多数网站都应该有恢复选项，以便您可以为您的账户创建一个新的通行密钥。当然，这要根据每个网站的具体情况而定。

### 如果我的设备被盗怎么办？小偷可以通过这种方式获取通行密钥吗？ <a href="#what-happens-if-my-device-is-stolen-can-a-thief-gain-access-to-passkeys-in-that-way" id="what-happens-if-my-device-is-stolen-can-a-thief-gain-access-to-passkeys-in-that-way"></a>

窃贼要想在设备上成功使用密码，唯一方法是他们也可以解锁您的设备，从而有效地获取对您的数据的完全访问权限。然而，每次使用通行密钥通常都需要用户验证，例如生物识别或重新输入设备密码，因此在解锁后窃取您的设备是远远不够的。

### 从安全角度来看，密码和通行密钥有何不同？ <a href="#from-a-security-perspective-how-do-passwords-and-passkeys-compare" id="from-a-security-perspective-how-do-passwords-and-passkeys-compare"></a>

### 我的通行密钥需要 2FA 吗？ <a href="#do-i-need-2fa-with-my-passkey" id="do-i-need-2fa-with-my-passkey"></a>

### 我的通行密钥会被破解吗？ <a href="#can-my-passkey-be-hacked" id="can-my-passkey-be-hacked"></a>

### 谷歌最近宣布支持通行密钥。这和 Bitwarden 宣布的事情是一样的吗？ <a href="#google-recently-announced-passkey-support.-is-this-the-same-thing-that-bitwarden-is-announcing" id="google-recently-announced-passkey-support.-is-this-the-same-thing-that-bitwarden-is-announcing"></a>

### 无论我使用什么浏览器，我是否都使用相同的通行密钥？还是取决于浏览器或设备，每个站点都需要不同的通行密钥？ <a href="#do-i-use-the-same-passkey-regardless-of-the-browser-im-on-or-will-each-site-require-a-different-pass" id="do-i-use-the-same-passkey-regardless-of-the-browser-im-on-or-will-each-site-require-a-different-pass"></a>

### 支持通行密钥的有哪些网站？ <a href="#what-are-some-examples-of-sites-that-support-passkeys" id="what-are-some-examples-of-sites-that-support-passkeys"></a>

### 通行密钥与无密码相同吗？ <a href="#are-passkeys-the-same-as-passwordless" id="are-passkeys-the-same-as-passwordless"></a>

### 我将如何在 Bitwarden 中使用通行密钥？我还需要主密码吗？ <a href="#how-will-i-use-passkeys-with-bitwarden-do-i-still-need-a-master-password" id="how-will-i-use-passkeys-with-bitwarden-do-i-still-need-a-master-password"></a>

### 通行密钥可以跨平台使用吗？如果没不能，根据使用的平台使用不同的通行密钥是否有任何问题？ <a href="#can-passkeys-be-used-across-platforms-if-not-are-there-any-issues-with-having-different-passkeys-dep" id="can-passkeys-be-used-across-platforms-if-not-are-there-any-issues-with-having-different-passkeys-dep"></a>

### 如果我采用它，我是否会被锁定为只能使用通行密钥？ <a href="#will-i-be-locked-into-using-passkeys-if-i-adopt-it" id="will-i-be-locked-into-using-passkeys-if-i-adopt-it"></a>

### 可以与其他受信任的个人共享通行密钥吗？ <a href="#can-passkeys-be-shared-with-other-trusted-individuals" id="can-passkeys-be-shared-with-other-trusted-individuals"></a>

### 是否支持，例如当我在使用通行密钥遇到问题时可以与实时聊天代表交谈？ <a href="#is-there-support-such-as-a-live-chat-representative-to-speak-with-if-im-having-trouble-with-my-passk" id="is-there-support-such-as-a-live-chat-representative-to-speak-with-if-im-having-trouble-with-my-passk"></a>

### 如果我不想再使用我的通行密钥，我可以将其移除吗？ <a href="#if-i-no-longer-want-to-use-my-passkey-can-i-remove-it" id="if-i-no-longer-want-to-use-my-passkey-can-i-remove-it"></a>

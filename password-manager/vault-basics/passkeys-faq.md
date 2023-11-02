# =\*通行密钥常见问题

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/resources/passkeys-faq/)
{% endhint %}

> 这是 Bitwarden 资源库的一篇文章，我把它放在帮助中心的「通行密钥」旁边，以便于阅读以及理解什么是通行密钥 (Passkey)。

### 什么是通行密钥以及它是如何工作的？ <a href="#what-is-a-passkey-and-how-does-it-work" id="what-is-a-passkey-and-how-does-it-work"></a>

通行密钥是一种身份验证形式，可让您快速创建和登录账户，而无需使用安全性较低的密码。这种一步到位的安全登录方法取代了传统的身份验证方法以及双因素身份验证 (2FA) 过程。更妙的是，有了通行密钥，您再也不会创建弱密码了，因为您再也不需要创建密码了。

{% embed url="https://bitwarden.com/_gatsby/file/b071a13b1731fd9fdf7fd29584e73955/infographic-passkeys-large.gif?eu=8cdb04efb6c9f4d20f61a4d26877626cb66d01fdfe5337d66b31e3a84efc9cd32cf71850739579b0256d59d880e611bc6e9770324cef838f92ed1cf0e83dad5a53d052bf64b67204547ec4f6b7a4551768974951a4d0c10fa43f2385e3b7e6231e011a7ea97bb0d7eaf83f3cf4c76f71e0a9b9773893fc2da30c0d109d4932bf31ffd3c06d4baad1b75db1b5a8f3089b94ba6a005fdc886a797714672ebb49b8c5d5570e6641162070cfeb47cf67c3e5681b622b0b5601a1316ed154aa696091e4a8f555dd2c2ab5fece3671999af0d6b24dee7b36bf9674b4c26a394d56f95aeea127a690335310d673ac" %}

### 通行密钥可以取代物理 Yubikey 吗？ <a href="#do-passkeys-replace-physical-yubikeys" id="do-passkeys-replace-physical-yubikeys"></a>

### 使用通行密钥的最佳方式是什么？ <a href="#whats-the-best-way-to-use-passkeys" id="whats-the-best-way-to-use-passkeys"></a>

### 设置通行密钥的流程是怎样的？当我将来访问某个网站或应用程序时，该流程会发生怎样的变化？ <a href="#what-is-the-process-to-set-up-a-passkey-how-does-that-process-change-when-i-go-to-a-site-or-app-in-t" id="what-is-the-process-to-set-up-a-passkey-how-does-that-process-change-when-i-go-to-a-site-or-app-in-t"></a>

### 设置通行密钥时需要哪些信息？ <a href="#what-information-is-required-when-setting-up-a-passkey" id="what-information-is-required-when-setting-up-a-passkey"></a>

### 我的通行密钥存储在哪里？ <a href="#where-are-my-passkeys-stored" id="where-are-my-passkeys-stored"></a>

### 如果我丢失了手机怎么办？如何在没有密码之类的方式来验证自己身份的情况下恢复我的通行密钥？ <a href="#what-happens-if-i-lose-my-phone-how-do-i-recover-my-passkey-with-nothing-like-a-password-to-identify" id="what-happens-if-i-lose-my-phone-how-do-i-recover-my-passkey-with-nothing-like-a-password-to-identify"></a>

### 如果我的设备被盗怎么办？小偷可以通过这种方式获取通行密钥吗？ <a href="#what-happens-if-my-device-is-stolen-can-a-thief-gain-access-to-passkeys-in-that-way" id="what-happens-if-my-device-is-stolen-can-a-thief-gain-access-to-passkeys-in-that-way"></a>

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

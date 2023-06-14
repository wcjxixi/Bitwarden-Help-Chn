# 账户加密密钥

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/account-encryption-key/)
{% endhint %}

每个 Bitwarden 账户都有一个根据[加密](encryption.md)中定义的方法，从您的主密码派生出来的加密密钥。该加密密钥用于加密所有密码库数据。

## 轮换您的加密密钥 <a href="#rotate-your-encryption-key" id="rotate-your-encryption-key"></a>

{% hint style="warning" %}
**轮换加密密钥是潜在的危险操作。**请通读本章节，以了解这样做的全部后果。
{% endhint %}

轮换账户的加密密钥会生成一个新的加密密钥，用于重新加密所有密码库数据。如果您的帐户已被盗用，并且有人获得了您的加密密钥，则您应该考虑轮换您的加密密钥。

轮换之后，您应该迅速采取以下措施以防止数据丢失或损坏：

### 注销客户端应用程序 <a href="#log-out-of-client-applications" id="log-out-of-client-applications"></a>

轮换加密密钥后，您**必须立即**注销 Bitwarden 客户端应用程序（桌面应用程序、浏览器扩展、移动应用程序等）上的任何已登录会话。以这种方式注销客户端应用程序将关闭使用「陈旧」（轮换前）加密密钥的会话。然后，像往常一样重新登录将使用新的加密密钥。

**在使用「陈旧」加密密钥的会话中进行更改将导致数据损坏，使您的数据无法恢复。**

### 重新创建账户的加密导出 <a href="#re-create-any-account-backup-exports" id="re-create-any-account-backup-exports"></a>

如果您使用[加密导出](../import-export/encrypted-exports.md)来存储长期的安全备份，您应该立即使用新的加密密钥重新创建密码库数据的加密导出。

加密导出使用您的加密密钥来加密**以及解密**您的密码库数据，这意味着，经过轮换的加密密钥将无法解密使用「陈旧」（轮换前）的密钥创建的导出。

### 如何轮换您的加密密钥 <a href="#how-to-rotate-your-encryption-key" id="how-to-rotate-your-encryption-key"></a>

完成以下步骤以轮换您账户的加密密钥：

1、在您的[网页密码库](https://vault.bitwarden.com/)中，选择配置文件图标然后从下拉列表中选择**账户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?eu=89df52e3eacfa8860f3aa5806c233360e56e5fa3f8573e823d67e3fd4ff9ca8171fb1f0024932bb97a6153d8dbe010bc31932b651ee6d6dfc8ba1af3e337fc5a008453ea6eb3700e022991f8b5fc00143cc11309abdb8c4ce32e78cbfaeaea214e055f35fb3eeed0afea6020f39d7167aea9a16c3b91ed22e14456098c1f6efb60c9d1b7477be88fc516baa0a4af4eb8d6ef560029c4f4322122194c59be2de9a5b25171397d125f619bfb0cc46593b06915302008561c9434788500a503529bbbbfce5fd97879fca8cc2c7185acffc4821bac3475e3d126a9ed4a07104df244&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A24%3A03.707Z" %}
账户设置
{% endembed %}

2、从「账户设置」菜单中，选择**安全**页面和**主密码**选项卡。

3、输入您的**当前主密码**并输入和确认**新主密码**。

{% hint style="success" %}
如果您不想更改您的主密码而只想轮换您的帐户加密密钥，您可以在**新的**字段中输入您当前的主密码以防止其更改。
{% endhint %}

4、勾选**同时轮换我的帐户的加密密钥**复选框并接受弹出的对话框。

5、选择**更改主密码**按钮。

> \[**译者注**]：更改您的主密码或更改加密密钥设置（KDF）时，均不会主动轮换账户的加密密钥。仅在更改您的主密码时勾选**同时轮换账户的加密密钥**才会更改您账户的加密密钥。

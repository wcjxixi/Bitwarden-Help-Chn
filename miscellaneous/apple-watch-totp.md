# Apple Watch 上的 Bitwarden(Beta)

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/apple-watch-totp/)
{% endhint %}

{% hint style="info" %}
Apple Watch 上的 Bitwarden 目前处于测试阶段。通过 TestFlight 访问 Apple Watch beta 和 Bitwarden TOTP 功能的介绍位于[此处](https://community.bitwarden.com/t/join-the-beta-program/39185)。
{% endhint %}

我们的 Bitwarden [身份验证器功能](../your-vault/totp.md)现在可以在 Apple Watch 上使用。Bitwarden 高级会员或付费组织的成员现在将有一个额外的选项来访问基于时间的一次性密码 (TOTP) 代码。Apple Watch Bitwarden 将显示存储有种子的密码库项目的 TOTP 代码，以便在登录受 TOTP 保护的帐户时更容易访问。

{% hint style="info" %}
TOTP 验证码的生成要求高级会员或付费组织（家庭、团队或企业）成员资格。
{% endhint %}

## 设置 <a href="#setup" id="setup"></a>

1、您的 iOS 移动设备上安装了 Bitwarden 应用程序。

2、检查你的 Apple Watch，Bitwarden 应该会自动安装在你的手表上。如果您没有在您的 Apple Watch上看到 Bitwarden ，您可以在 Apple Watch 上手动安装 Bitwarden。

<figure><img src="https://bitwarden.com/_gatsby/image/b6f7d94a6452bc4f16f01085f1f47fa6/98d117dfd0bf59ba7c486b1153f63922/Screen%20Shot%202022-12-02%20at%203.53.40%20PM%20(2).webp?eu=da8704e7b799afd50a60a9846976693db16956f9af5632863b36e6a949fe96d423fb105075c67fb72d685cdbd5e510bd6f977d6218bbd3dec0e91fa7bf66ac59528a53bb67b77203592ac7f8b3f0014d3b921a0aa182cb08a3697082b6b6b47218514e2aa872ee84bffb6332b3837c37b9e4ac762186eb3bea0d410d964926a927a5c39a654fad8de55bacf8b0fc4dd29ba573540681f2632a2a0b1847eb6ddccfcf5618794c3539449ba81fa707edc44d620b3c0b0d00f7633cd150f23e36c4e0a8a35dde7f7ae1face37728fc7a9d5ec1ea87e69849c65fcd765156d55f357c2be7bf5d079070c9c2af8fa1df66c062b4581028d244fb94530e305ebff07cd7f&#x26;a=w%3D341%26h%3D44%26fm%3Dwebp%26q%3D75&#x26;cd=2022-12-15T16%3A26%3A30.241Z" alt=""><figcaption><p>Apple Watch Bitwarden 应用程序</p></figcaption></figure>

3、在 iPhone 移动应用程序上访问您的 Bitwarden 帐户，然后选择 **⚙️设置**选项卡。

4、向下滚动到**帐户**部分，然后选择**连接 Apple Watch**。选择后，在弹出窗口中确认设置已**打开**。

{% embed url="https://bitwarden.com/_gatsby/image/4a26aa0373818bb2ff54a2c346982d15/f5b6038be667bf26e31fd0251d966032/Screen%20Shot%202022-12-01%20at%202.59.13%20PM%20(2).webp?eu=8a8d04b4b59df4d30a60a4d03c736160b33706fdaf5834d86b63b7a74aae9e8276a51a0171c07fb22d6f5f8f87b645be6190703548e983db91b419a6ec30ad0055d55bee6ee1240e547fc5f9b3f701456bcf4e5af2d5ce0da43e26d6b3b3b77018051a2bac7feb86e6f17120f0c0252df5effb7f3297e866b3560805885b24b827a5ce8b7701e98cee4ca9bcefff0190dbe0320444d2aa345532107c2a986fdcc1f770124f56170052d1ab0bc4689fe5341b352a570903a1363b8450a96e36c6e2f9a95cdd7d29b3fac12e13d581fbd5b375cf7229a3a025a98039670f0fb113acd32ab3bd66180b8834fb9623d27e6a5a42ed02c97a77&a=w%3D371%26h%3D811%26fm%3Dwebp%26q%3D75&cd=2022-12-15T16%3A26%3A35.965Z" %}
连接 Apple Watch
{% endembed %}

5、启动后，手表将开始与 Bitwarden 同步。

当您注销帐户或切换到其他帐户时，Apple Watch 将擦除当前数据。在您的 iOS 移动设备上重新登录 Bitwarden 帐户时，将再次进行同步。

{% hint style="info" %}
在移动应用程序中关闭 Bitwarden Apple Watch 连接将删除 Apple Watch 上的 Bitwarden 应用程序的所有数据并禁用与其的通信。
{% endhint %}

## 启用 TOTP <a href="#enabling-totp" id="enabling-totp"></a>

如果您还不熟悉为密码库项目启用 TOTP 代码，请参阅[此处](../your-vault/totp.md#generate-totp-codes)。如果没有项目有 TOTP 设置，Apple Watch 将显示此界面：

{% embed url="https://bitwarden.com/_gatsby/image/2c163459af91a8f1a87de37115c7a60b/d0f4df0500e5dc50450e8938358ab234/2fa.webp?eu=8b8601e4b0cef9d55b3ef4863a77676ce26d01afaf0037853e31eca819aac8d476f11156739029b128385288d3b145bc67952d331bee838cc0ed1bf7eb32a20b578758bf65e67654032cc4f6e4f3054760c01000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41a798918d8eede3a4fb79dd418b6e4eed25abbc9bc5518468af33320224c1c51ec2ebea2e351703178120863c8af0b916997bf684e6125415d55a6797a8e02&a=w%3D250%26h%3D282%26fm%3Dwebp%26q%3D75&cd=2022-12-15T16%3A26%3A46.274Z" %}
Apple Watch 添加 2FA 界面
{% endembed %}

## 使用 Apple Watch 访问 TOTP 代码 <a href="#sing-the-apple-watch-to-access-totp-codes" id="sing-the-apple-watch-to-access-totp-codes"></a>

1、请输入您的已启用的手表 PIN 码解锁您的 Apple Watch。

2、在 Apple Watch 上选择 Bitwarden。

{% embed url="https://bitwarden.com/_gatsby/image/4ad40e9182d7290977aa20938ec7b35c/c8053ebda78f979dc2146670cfedd890/Screen%20Shot%202022-12-12%20at%205.06.28%20PM.webp?eu=dddd52b4e3cdfad2076fa38a3e75656ee33a54acaa5764d06e31b7aa46ab9f872da7100721c37eb6783d088ad1b211b861c52d661eee85dac7ee1af6ea3ca80b5bd75dee32b176550422c4afb1f154103cc54c09f582ce0da9353690a5f0bd6f0609417aff2ffb9fbfed6335f3c07a76a9a8f87b21ddac3abe41180eca4e79a123bc8fd97759b7aab56c8780eff34a94d6bd74612484a0425f681d4d0cbe7beeace352746d78420934c9ae5a92609ee73c4a34775b5655f46432cf36a82e6496ba94c205863e14e3a8cb336d87c1b381ef75fd6e19e2d127af9c3972616dd10dede22c&a=w%3D550%26h%3D312%26fm%3Dwebp%26q%3D75&cd=2022-12-15T16%3A26%3A51.832Z" %}
Apple Watch 应用程序选择界面
{% endembed %}

3、密码库将与您 iOS 移动设备上的活动 Bitwarden 帐户同步。可以在密码库页面的顶部看到当前的帐户。

{% embed url="https://bitwarden.com/_gatsby/image/1f9768d6d9cc911090452db6232d395d/b608eb7d3e1a7601b983ba99d80d41fd/vault%20view.webp?eu=d6d805e1b59eaf820a3af5816924643fe8385fabfb5163846c66e6a848fa9b8270f21b0371c72ee57a3f5fde87e210bd62947b611be6d9d993ea4dfde230f80c05d60eee34b272045b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b9281fb5f10687413b02915a14a718e1d8895140b4aec400efb7e7fb5cc998b3280640d3f2337076194b0ee978e8a2b456753d7b485c32c6b01e9624caf2535a3876194143a930&a=w%3D250%26h%3D283%26fm%3Dwebp%26q%3D75&cd=2022-12-15T16%3A26%3A57.034Z" %}
Apple Watch 密码库界面
{% endembed %}

4、选择您想要访问的密码库项目。TOTP 代码和计时器将显示在 Apple Watch 屏幕上。

{% embed url="https://bitwarden.com/_gatsby/image/6b332f0561be156c376ebc5de8b2caf7/4c94250e66de9d196b819662c7b27e31/totp%20bevel%20copy.webp?eu=d78755b7e399ae875a3df18468726361b63d05a3a8053fd63f35e6a846a9cc8471f3185024c02fb62a615ed681e14beb64c22d341ae8d8da92bf1aa5e835a9005a8a0ee966e67100567a97fcbaad420128851047beda9559f43831cab6f7e1215a13496feb64e6d4a8b63226eed06968ebe0ae7322c5b47c956c2b0bab4322bb21c9928a4c4ceebbc86bb2be8cb65c9bcdb12f5249d9f43d20764e4e0eef2fb2a2e701703c2c485230c6a95d963289f26358214c0c0a45a23b55830abb252f83baac&a=w%3D250%26h%3D284%26fm%3Dwebp%26q%3D75&cd=2022-12-15T16%3A27%3A03.676Z" %}
Apple Watch TOTP 界面
{% endembed %}

## Apple Watch 上的 Bitwarden 的安全性 <a href="#bitwarden-on-the-apple-watch-security" id="bitwarden-on-the-apple-watch-security"></a>

Bitwarden 的零知识加密与 Apple 的 WatchConnectivity 和 Secure Enclave 一起工作，将保留 iPhone 和 Apple Watch 之间的零知识和安全通信。可以采取几个步骤来提高您的帐户和设备的安全性：

* 设置安全密码以防止在 Apple Watch 上对 Bitwarden 进行不必要的访问。只有 Apple Watch 解锁后，才可以查看设备上的信息。
* 在 Apple Watch 上启用手腕检测，以便设备从用户手腕上取下后自动锁定。

请参阅 [Apple 的 watchOS 安全文档](https://support.apple.com/zh-cn/guide/security/secc7d85209d/web)以了解更多信息。

# Apple Watch 上的 Bitwarden

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/apple-watch-totp/)
{% endhint %}

我们的 Password Manager 的[集成验证器功能](../your-vault/security-tools/totp.md)现在可以在 Apple Watch 上使用。Bitwarden 高级会员或付费组织的成员现在将有一个额外的选项来访问基于时间的一次性密码 (TOTP) 代码。Apple Watch Bitwarden 将显示存储有种子的密码库项目的 TOTP 代码，以便在登录受 TOTP 保护的账户时更容易访问。

{% hint style="info" %}
TOTP 验证码的生成要求 Bitwarden 高级会员或付费组织（家庭、团队或企业）的高级成员资格。[此处](../../plans-and-pricing/password-manager/about-bitwarden-plans.md#compare-personal-plans)详细了解每种计划的详细信息。

Families 2019 不再向该计划的用户提供个人高级会员资格。[此处](../../plans-and-pricing/updates-to-bitwarden-plans-2019-2020.md)了解此计划的变更情况。
{% endhint %}

## 设置 <a href="#setup" id="setup"></a>

1、您的 iOS 移动设备上安装了 Bitwarden App。

2、检查你的 Apple Watch，Bitwarden 应该会自动安装在您的手表上。如果没有在您的 Apple Watch上看到 Bitwarden ，请在 Apple Watch 上手动安装 Bitwarden。

<div align="left"><figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6pWZMbYpUERAe7wPVKBANZ/eb3046159b774c207510b762947e144d/Screen_Shot_2022-12-02_at_3.53.40_PM__2_.png?_a=DAJCwlWIZAAB" alt=""><figcaption><p>Apple Watch Bitwarden App</p></figcaption></figure></div>

3、在 iPhone 移动 App 上访问您的 Bitwarden 账户，然后选择 **⚙️设置**选项卡。

4、选择**其他**选项然后打开**连接到 Watch**。选择后，在弹出窗口中确认设置已**打开**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/349i1GulSBErWTuDSFOgkW/25a10a9b2a8584fb074c205236311fc8/2025-01-22_10-10-42.png?_a=DAJCwlWIZAAB" %}
连接到 Apple Watch
{% endembed %}

5、启动后，手表将开始与 Bitwarden 同步。

当您注销账户或切换到其他账户时，Apple Watch 将擦除当前数据。在您的 iOS 移动设备上重新登录 Bitwarden 账户时，将再次进行同步。

{% hint style="info" %}
在移动 App 中关闭 Bitwarden Apple Watch 连接将删除 Apple Watch 上 Bitwarden App 的所有数据并禁止与其通信。
{% endhint %}

## 启用 TOTP <a href="#enabling-totp" id="enabling-totp"></a>

如果您还不熟悉为密码库项目启用 TOTP 代码，请参阅[此处](../your-vault/security-tools/totp.md#generate-totp-codes)。如果没有项目有 TOTP 设置，Apple Watch 将显示此界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/28ELSN09aicT7i20KcFekH/6a062e0391357ae18abcf60cf819db06/2fa.png?_a=DAJCwlWIZAAB" %}
Apple Watch 添加 2FA 界面
{% endembed %}

## 使用 Apple Watch 访问 TOTP 代码 <a href="#sing-the-apple-watch-to-access-totp-codes" id="sing-the-apple-watch-to-access-totp-codes"></a>

1、如果已启用手表 PIN 码，请输入手表 PIN 码解锁 Apple Watch。

2、在 Apple Watch 上选择 Bitwarden。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7twiT5CXV1jsizjiVTocGM/abdcfe9af5da2b1712e18a0fed59f338/Screen_Shot_2022-12-12_at_5.06.28_PM.png?_a=DAJCwlWIZAAB" %}
Apple Watch App 选择界面
{% endembed %}

3、密码库将与您 iOS 移动设备上的活动 Bitwarden 账户同步。可以在密码库页面的顶部看到当前的账户。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6JGjNWcUfjrUkLjxgRnjPD/0a9be44d510816b1edf4ec76b44b8778/vault_view.png?_a=DAJCwlWIZAAB" %}
Apple Watch 密码库界面
{% endembed %}

4、选择您想要访问的密码库项目。TOTP 代码和计时器将显示在 Apple Watch 屏幕上。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4ENEoPkcwuB2dOb0EHDmhR/efaf2e9278212af2297e5155895865ac/totp_bevel_copy.png?_a=DAJCwlWIZAAB" %}
Apple Watch TOTP 界面
{% endembed %}

## Apple Watch 上的 Bitwarden 的安全性 <a href="#bitwarden-on-the-apple-watch-security" id="bitwarden-on-the-apple-watch-security"></a>

Bitwarden 的零知识加密与 Apple 的 WatchConnectivity 和 Secure Enclave 一起工作，将保留 iPhone 和 Apple Watch 之间的零知识和安全通信。可以采取几个步骤来提高您的账户和设备的安全性：

* 设置安全密码以防止在 Apple Watch 上对 Bitwarden 进行不必要的访问。只有 Apple Watch 解锁后，才可以查看设备上的信息。
* 在 Apple Watch 上启用手腕检测，以便设备从用户手腕上取下后自动锁定。

{% hint style="danger" %}
如果启用了使用 iPhone 解锁设置，解锁连接的 iPhone 将自动解锁您的 Apple Watch（如果设备在附近）。这可能会暴露 Apple Watch 上的 Bitwarden 信息。
{% endhint %}

请参阅 [Apple 的 watchOS 安全文档](https://support.apple.com/zh-cn/guide/security/secc7d85209d/web)以了解更多信息。

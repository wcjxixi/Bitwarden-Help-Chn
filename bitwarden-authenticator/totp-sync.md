# 同步验证码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/totp-sync/)
{% endhint %}

> **\[译者注]**：Bitwarden Password Manager iOS 和 Android 以及 Bitwarden Authenticator 支持验证码同步功能。

如果您同时使用 Bitwarden Authenticator 和 Bitwarden Password Manager，您可以在两者之间无缝同步验证码。

{% embed url="https://bitwarden.com/assets/1DcAOWrPp1qDkIILFUu1f9/59504e02563a5a6faac1635b7e2b843f/2025-05-21_10-33-42.png?w=779&fm=avif&q=80" %}
在 Bitwarden Authenticator（左）和 Password Manager（右）之间同步
{% endembed %}

可以按照您希望的那样双向同步，这意味着：

* 您可以从所有 Password Manager 账户同步代码到 Authenticator，或者只从您特别选择的那几个账户同步。
* 您可以轻松地将本地验证码复制到 Password Manager，或仅通过 Authenticator 访问。

## 设置同步 <a href="#set-up-sync" id="set-up-sync"></a>

要设置 TOTP 同步：

1、确保您的设备上已同时安装了 Bitwarden Authenticator 和 Bitwarden Password Manager，并在 Password Manager 中登录了您想要同步的账户。

2、在 Password Manager 中，导航至**设置** → **账户安全**，然后打开**允许验证器同步**选项。

3、在 Authenticator 中，确认 Password Manager 中存储的任何代码都列在您的 Bitwarden 账户标题下，而不是在**本地代码**下。

设置完成后，同步将自动进行，这意味着：

* 您无需手动刷新 Authenticator 来获取 Password Manager 中最近添加或更新的验证码。
* 您无需手动解锁 Password Manager 来获取 Authenticator 中所需数据的访问权限。更多关于如何实现这一点的内容将在下一节中介绍。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

{% tabs %}
{% tab title="Android" %}
1. 当 Password Manager 中的**允许验证器同步**选项被激活时：
   1. Password Manager 客户端生成一个**全局对称密钥**，然后通过 Android 接口定义语言 (AIDL) 与 Authenticator 共享。
   2. 您现有的**账户加密密钥**将本地持久化存储，这将允许在 TOTP 同步需要时使用它来解密 Password Manager 项目数据。
2. 只要**允许验证器同步**选项被激活，当打开 Authenticator 时：
   1. 通过 AIDL 向 Password Manager 发起请求。
   2. Password Manager 在响应请求时，使用持久化的**账户加密密钥**临时解密您的项目数据，并使用**全局对称密钥**重新加密这些数据。
   3. 一部分重新加密的数据，特别是验证器密钥、显示名称和用户名，通过 AIDL 发送到 Authenticator。任何敏感数据都不会未经加密通过 AIDL 传输。
3. Authenticator 接收您重新加密的验证器密钥、显示名称和用户名，并使用共享的**全局对称密钥**解密这些数据。

{% hint style="success" %}
AIDL 是一种进程间通信 (IPC) 抽象，它允许 Authenticator 和 Password Manager 安全地连接，而设备中的任何其他组件都无法访问交换的信息。
{% endhint %}
{% endtab %}

{% tab title="iOS" %}
1. 当 Password Manager 中的**允许验证器同步**选项被激活时：
   1. Password Manager 客户端生成一个**全局对称密钥**，然后写入由 Password Manager 和 Authenticator 共享的钥匙串。
   2. 部分项目数据，包括验证器密钥、显示名称和用户名，使用**全局对称密钥**加密，然后写入 App Group（App 组）的共享容器。
2. 只要**允许验证器同步**选项被激活，当打开 Authenticator 时：
   1. Authenticator 从共享的钥匙串中获取**全局对称密钥**。
   2. Authenticator 从 App Group 中获取加密的 Authenticator 密钥、显示名称和用户名。
3. Authenticator 使用**全局对称密钥**在本地解密您的 Authenticator 密钥、显示名称和用户名。

{% hint style="success" %}
**钥匙串**使用访问权限组来允许在同一开发者制作的 App 之间安全地本地共享加密密钥或其他数据。

**App Groups** 使用称为共享容器的安全本地存储位置，以允许同一开发者制作的 App 访问共享数据和某些进程间通信 (IPC)。
{% endhint %}

任何时候，如果您停用了**允许验证器同步**选项或完全注销了 Password Manager：

* 之前存储在 App Group 中的已加密的验证器密钥、显示名称和用户名将被删除。
* 仅当所有用户停用同步或注销时，**全局对称密钥**也将被删除。

> **\[译者注]**：App Group 是 Apple 提供的允许同一开发者账号下的多个 App 或 Extension 共享数据（如登录状态）的机制。它通过提供一个共享的容器（Shared Container），使得不同的 App 或 Extension 可以访问同一份数据，从而突破 iOS 沙盒（Sandbox）的限制，实现跨 App 数据共享。
{% endtab %}
{% endtabs %}

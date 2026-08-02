# 同步验证码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/totp-sync/)
{% endhint %}

将 Authenticator 与 Password Manager 连接以同步您的验证码。激活后，Bitwarden App 将与您添加或编辑的任何代码（本地代码除外）保持同步。这可以帮助您从任一 App 快速查找和使用 TOTP：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1DcAOWrPp1qDkIILFUu1f9/59504e02563a5a6faac1635b7e2b843f/2025-05-21_10-33-42.png?w=779&#x26;fm=avif" alt=""><figcaption><p>在 Bitwarden Authenticator（左）和 Password Manager（右）之间同步</p></figcaption></figure></div>

如果您有多个 Password Manager 账户，您可以选择要与 Authenticator 同步的账户。同样，存储在 Authenticator 中的本地代码可以保持独立，也可以将它们移动到 Password Manager 以便从两个 App 进行访问。

{% hint style="info" %}
如果您希望仅将验证码保存在一个 Bitwarden App 中，请不要同步您的账户。这有两种选择：

* **仅从 Bitwarden 密码库访问代码**：使用 [Password Manager 集成的身份验证器](../password-manager/your-vault/security-tools/totp.md)保存 TOTP，并且不要启用 Bitwarden 账户的**允许验证器同步** App 设置。这意味着该特定 Bitwarden 账户中保存的任何代码都不会在 Authenticator 中显示。
* **仅从 Authenticator App 访问代码**：首次将代码添加到 Authenticator 时，选择**保存到此处**以将其添加为本地代码。这些代码未连接到您的 Bitwarden 账户，因此无法在您的 Bitwarden 密码库中的任何位置找到它们。
{% endhint %}

## 设置同步 <a href="#set-up-sync" id="set-up-sync"></a>

已保存在 Bitwarden 密码库登录项目中的代码可以[与 Authenticator 同步](totp-sync.md#sync-codes-saved-in-your-bitwarden-vault)。如果您有本地代码（即仅保存在您的设备上并通过 Authenticator 访问的 TOTP），请首先[将代码复制到您的密码库](totp-sync.md#move-and-sync-local-codes-to-your-bitwarden-vault)。代码位于您的密码库中后，它们就会像其他 TOTP 一样同步。

### 同步保存在 Bitwarden 密码库中的代码 <a href="#sync-codes-saved-in-your-bitwarden-vault" id="sync-codes-saved-in-your-bitwarden-vault"></a>

要使用此功能，您必须拥有 iOS 或 Android 12+。要在两个 Bitwarden App 之间同步 TOTP：

1. 确保您的设备上安装了 [Bitwarden Authenticator](https://bitwarden.com/download/#bitwarden-authenticator) 和 [Bitwarden Password Manager](https://bitwarden.com/download/#mobile-applications)。
2. 在 Password Manager 中，登录要与 Authenticator 同步的账户。
3. 点击 <i class="fa-gear-complex">:gear-complex:</i>**设置**图标。
4. 点击**账户安全**。
5. 启用**允许验证器同步**。
6. （可选）要同步其他 Password Manager 账户，请为每个账户重复步骤 2-5。您需要为每个账户单独切换设置，这样您才能准确选择与 Authenticator 同步的账户。
7. Authenticator 将代码分为两组：本地代码和从 Password Manager 同步的代码。请确认您的 Password Manager TOTP 代码是否显示在 Authenticator 中您的账户电子邮箱标题下。

### 将本地代码移动并同步到 Bitwarden 密码库 <a href="#move-and-sync-local-codes-to-your-bitwarden-vault" id="move-and-sync-local-codes-to-your-bitwarden-vault"></a>

您可以手动将本地代码复制到您的 Bitwarden 密码库，以便从两个 App 进行访问。要将本地代码复制并移动到 Password Manager：

1. 在 Bitwarden Authenticator 中，长按该代码。
2. 点击**复制到 Bitwarden 密码库**。
3. 这将打开 Password Manager 并搜索匹配的登录项目。
   * 如果找到匹配的登录项目，点击该登录项目。编辑或输入任何其他详细信息，然后在完成后点击 <i class="fa-circle-check">:circle-check:</i>**检查图标**。
   * 如果未找到匹配的登录项目，点击 <i class="fa-plus">:plus:</i>**新增项目**。编辑或输入任何其他详细信息，然后在完成后点击 <i class="fa-circle-check">:circle-check:</i>**检查图标**。

## 同步工作原理 <a href="#how-syncing-works" id="how-syncing-works"></a>

尽管各个平台的核心密钥交换工作流程是相同的，但用于实现 Password Manager 和 Authenticator 之间同步的安全存储和通信方法则因 Android 或 iOS 而异：

{% tabs %}
{% tab title="Android" %}
当 Password Manager 中的**允许验证器同步**被激活时：

1. Password Manager 客户端生成一个**全局对称密钥**，然后通过 Android 接口定义语言 (AIDL) 与 Authenticator 共享。
2. 您现有的**账户加密密钥**将本地持久化存储，这将允许在 TOTP 同步需要时使用它来解密 Password Manager 项目数据。

{% hint style="success" %}
AIDL 是一种进程间通信 (IPC) 抽象，它允许 Authenticator 和 Password Manager 安全地连接，而设备中的任何其他组件都无法访问交换的信息。
{% endhint %}

当您打开 Authenticator 并且**允许验证器同步**被激活时：

1. 通过 AIDL 向 Password Manager 发起请求。
2. Password Manager 在响应请求时，使用持久化的**账户加密密钥**临时解密您的项目数据，然后使用**全局对称密钥**重新加密这些数据。
3. Password Manager 将重新加密的身份验证器密钥、显示名称和用户名，通过 AIDL 发送到 Authenticator。任何敏感数据都不会未经加密通过 AIDL 传输。
4. Authenticator 接收您重新加密的身份验证器密钥、显示名称和用户名，然后使用共享的**全局对称密钥**解密这些数据。

> **\[译者注]**：AIDL（Android Interface Definition Language，Android 接口定义语言）是 Android 系统用于实现进程间通信 (IPC) 的一种机制。它允许在不同 App 之间进行数据交换和方法调用，使得不同进程能够安全有效地共享数据和功能。﻿
{% endtab %}

{% tab title="iOS" %}
当 Password Manager 中的**允许验证器同步**被激活时：

1. Password Manager 客户端生成一个**全局对称密钥**，然后写入由 Password Manager 和 Authenticator 共享的钥匙串。
2. 使用**全局对称密钥**加密保存在您的密码库项目中的身份验证器密钥、显示名称和用户名，然后存储到 App Group（App 组）的共享容器中。

{% hint style="success" %}
**钥匙串**使用访问权限组来允许在同一开发者制作的 App 之间安全地本地共享加密密钥或其他数据。

**App Groups** 使用称为共享容器的安全本地存储位置，以允许同一开发者制作的 App 访问共享数据和某些进程间通信 (IPC)。
{% endhint %}

当您打开 Authenticator 并且**允许验证器同步**被激活时：

1. Authenticator 从共享的钥匙串中获取**全局对称密钥**。
2. Authenticator 从 App Group 中获取加密的身份验证器密钥、显示名称和用户名。
3. Authenticator 使用**全局对称密钥**在本地解密身份验证器密钥、显示名称和用户名。

当您停用**允许验证器同步**或完全注销 Bitwarden Password Manager 时，存储在 App Group 中的加密数据（验证器密钥、显示名称和用户名）将被删除。如果所有关联的 Bitwarden 账户停用**允许验证器同步**或注销，则**全局对称密钥**也会被删除。

> **\[译者注]**：App Group 是 Apple 提供的允许同一开发者账号下的多个 App 或 Extension 共享数据（如登录状态）的机制。它通过提供一个共享的容器 (Shared Container)，使得不同的 App 或 Extension 可以访问同一份数据，从而突破 iOS 沙盒 (Sandbox) 的限制，实现跨 App 数据共享。
{% endtab %}
{% endtabs %}

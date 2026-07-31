# 关于 SSH

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/about-ssh/)
{% endhint %}

Bitwarden SSH 代理是桌面 App 的一项功能，允许您在所有机器上存储、管理和使用 SSH 密钥。桌面 App 可作为操作系统原生 SSH 代理的替代方案，使用密码库而非本地文件系统进行加密密钥存储。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

SSH 代理启用后，Bitwarden 桌面 App 会暴露一个本地套接字，供您的 SSH 客户端与之通信。诸如 `ssh` 、`git` 工具，以及其他依赖 SSH 的应用程序会将签名请求发送给 Bitwarden 代理，而非系统原生代理。Bitwarden 使用您密码库中存储的密钥来处理这些请求，并根据您已配置的设置来提示您验证访问权限。

该代理支持以下操作：

* **列出密钥**
* **请求签名**
* **代理转发**

## 存储 SSH 密钥 <a href="#storing-an-ssh-key" id="storing-an-ssh-key"></a>

SSH 密钥项目是一种跨 Bitwarden 桌面 App、网页 App、浏览器扩展和移动 App 支持的密码库项目类型。密钥可以通过桌面 App、网页 App 和浏览器扩展生成或导入。

每个 SSH 密钥项目存储以下字段：

| 字段   | 描述                   |
| ---- | -------------------- |
| 密钥名称 | 密钥的显示名称              |
| 私钥   | 用于身份验证的敏感的密钥内容。      |
| 公钥   | 与服务器或服务共享的密钥的一部分     |
| 指纹   | 从公钥派生的短标识符，用于验证签名提交。 |

SSH 密钥项目支持与其他密码库项目相同的 Bitwarden 功能，包括[文件夹](../../your-vault/vault-navigation/folders.md)、[收藏](../../your-vault/vault-navigation/favorites.md)、[主密码二次验证](../../your-vault/vault-items/vault-items.md#protect-individual-items)、笔记、[克隆项目](../../your-vault/vault-items/vault-items.md#clone)、[附件](../../your-vault/vault-items/file-attachments.md)和[自定义字段](../../your-vault/vault-items/custom-fields.md)等。

## 创建新的 SSH 密钥 <a href="#create-new-ssh-key" id="create-new-ssh-key"></a>

要创建新的 SSH 密钥：

1、选择**新建**按钮，然后选择 **SSH 密钥**作为项目类型。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1XYC3HwXOTMAPvyW1GS3Mk/82a46735327f9085d9380fbb8053b161/new_ssh_key-curent_ui.png?w=1187&#x26;fm=avif" alt=""><figcaption><p>在桌面端创建新的 SSH 密钥</p></figcaption></figure></div>

2、填写诸如**名称**等其余详细信息，完成后选择 **💾保存**图标。

{% hint style="info" %}
目前，Bitwarden 只能生成 `ED25519` 类型的 SSH 密钥。
{% endhint %}

## 编辑密钥 <a href="#edit-a-key" id="edit-a-key"></a>

要编辑现有的 SSH 密钥，请在您的密码库中找到它然后选择**编辑**。可编辑的字段包括密钥名称、文件夹、所有者和自定义字段。密钥本身内容在创建后无法修改。

### 组织 SSH 密钥 <a href="#organization-ssh-keys" id="organization-ssh-keys"></a>

SSH 密钥可以创建并存储在组织集合中。具有适当权限的组织成员可以创建、管理和访问组织拥有的 SSH 密钥。解更多有关[集合权限](../../../admin-console/manage-shared-items/collections/collection-permissions.md)的信息。

要将新的共享 SSH 密钥添加到组织密码库：

1、在桌面或网页 App 的密码库视图中，选择 **✚新增**按钮，然后选择 **SSH 密钥**。

{% hint style="success" %}
组织[所有者、管理员和某些自定义用户](../../../admin-console/manage-members/member-roles.md)也可以直接从 Admin Console 执行此步骤，以跳过此过程中的某些步骤。
{% endhint %}

2、使用**所有者**下拉列表，选择您希望该项目所属的组织。

3、使用**集合**下拉列表，选择要与其共享此项目的集合。

{% hint style="info" %}
通常，使用 SSH 密钥的资源可以支持每用户密钥。我们建议在向组织共享 SSH 密钥之前，先了解 SSH 密钥的最佳实践。
{% endhint %}

## 将密钥导入 Bitwarden <a href="#import-key-to-bitwarden" id="import-key-to-bitwarden"></a>

Bitwarden 桌面 App 支持 SSH 密钥导入功能。使用 Bitwarden 桌面 App：

1、选择**新增**按钮，然后选择 **SSH 密钥**作为项目类型。

2、复制您想要导入到 Bitwarden 的现有 SSH 密钥。

* 复制时，请包含密钥的头部和尾部，例如 `-----BEGIN OPENSSH PRIVATE KEY-----` 和 `-----END OPENSSH PRIVATE KEY-----` 。

3、使用**从剪贴板导入密钥**图标。这将自动将 SSH 密钥粘贴到 Bitwarden 中。

* 目前，导入的密钥必须是 **OpenSSH** 或 **PKCS#8** 格式。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5QTvyu39h3o0azkjU26P3t/c4987845f91b73efadaa8165f25b4524/Import.png?w=594&#x26;fm=avif" alt=""><figcaption><p>导入 SSH 密钥</p></figcaption></figure></div>

{% hint style="info" %}
目前，还不兼容从 Putty 导入的 SSH 密钥。
{% endhint %}

## 支持的密钥类型 <a href="#supported-key-types" id="supported-key-types"></a>

SSH 代理支持以下密钥类型：

* Ed25519
* RSA（SHA-256 和 SHA-512）

## 代理限制 <a href="#agent-limitations" id="agent-limitations"></a>

Bitwarden SSH 代理目前不支持以下操作。

### 不支持通过 ssh-add 管理密钥 <a href="#no-ssh-add-key-management" id="no-ssh-add-key-management"></a>

可供您的代理使用的密钥取决于存储在您密码库中的内容。无法通过 `ssh-add <key>` 等命令添加、删除或以编程方式限制这些密钥，也无法在 `~/.ssh/config` 中进行配置。

### 不支持按请求选择密钥 <a href="#no-per-request-key-selection" id="no-per-request-key-selection"></a>

当收到签名请求时，代理会依次尝试您密码库中的每个密钥，直到其中一个成功。目前没有机制可以指定某个主机应使用哪个密钥。即使您的密码库中包含正确的密钥，拥有多个密钥也可能导致身份验证失败。作为一种解决方法，您可以在 SSH 配置文件中使用 `IdentityFile` 指令指定要使用的密钥。

### 不支持 PuTTYgen 密钥 <a href="#puttygen-keys-not-supported" id="puttygen-keys-not-supported"></a>

目前无法将 PuTTYgen 密钥导入 Bitwarden。

### 多个账户 <a href="#multiple-accounts" id="multiple-accounts"></a>

当桌面 App 中加载了多个账户，并且启用了 SSH 代理时：

* 每个账户登录时，该账户的密钥都会被加载。
* 切换账户时，当前活动账户的密钥会被加载。在解锁第二个账户之前，第一个账户的密钥仍然处于活动状态。
* 注销某个账户后，如果还有其他已登录账户可用，代理会切换为使用剩余已登录账户的密钥。

**启用 SSH 代理**设置是所有账户共享的全局设置。如果您在一个账户下启用了该代理，然后切换到另一个账户，则会应用上一个活动账户中的该设置。

### 与原生 SSH 代理共存 <a href="#co-existing-with-a-native-ssh-agent" id="co-existing-with-a-native-ssh-agent"></a>

如果您在安装 Bitwarden 的同时也安装了原生 SSH 代理，并在本地存储了一些密钥，那么当 Bitwarden 代理不可用或返回失败时，您的 SSH 客户端可能会默认使用原生代理。如果您的授权设置设为**从不**或**记住直到密码库锁定**，则不会有任何 UI 交互来指示究竟是哪个代理处理了该请求。

如果您需要将密钥同时存储在本地和 Bitwarden SSH 代理中，请考虑将其放在非标准位置，而不是 `~/.ssh/` ，以降低意外回退的可能性。

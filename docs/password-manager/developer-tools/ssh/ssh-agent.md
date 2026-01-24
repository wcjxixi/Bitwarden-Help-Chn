# SSH 代理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ssh-agent/)
{% endhint %}

Bitwarden SSH 代理可以安全地加密和存储您的 SSH（安全 Shell）密钥，以用于以下目的：

* 验证服务器身份
* 签署 Git 提交
* 与基于 SSH 的服务进行交互

Bitwarden SSH 代理将您的密钥组织并保护在一个安全的位置。SSH 密钥可以通过桌面 App、网页 App、浏览器扩展和移动 App 访问。SSH 密钥可以通过桌面 App、网页 App 和浏览器扩展生成。

{% hint style="info" %}
SSH 代理需要 2025.1.2 或更新版本。

~~**macOS**：~~

~~macOS 商店构建版本目前暂不支持 SSH 代理，~~[~~.dmg 下载~~](https://bitwarden.com/download/)~~可用于获得 SSH 代理支持。~~

~~**Linux**：~~

~~Flatpak 版本目前暂不支持 SSH 代理，~~[~~Snap 下载~~](https://bitwarden.com/download/#downloads-desktop)~~可用于获得 SSH 代理支持。~~
{% endhint %}

## SSH 密钥存储 <a href="#storing-an-ssh-key" id="storing-an-ssh-key"></a>

您可以在 Bitwarden 桌面 App 中创建并保存新的 SSH 密钥。Bitwarden 存储的 SSH 密钥将包含以下内容：

| 字段   | 描述                                                                    |
| ---- | --------------------------------------------------------------------- |
| 密钥名称 | 您的 SSH 密钥的名称                                                          |
| 私钥   | 私钥是敏感数据，服务器将使用它来帮助建立安全连接。私钥数据应谨慎处理并保持安全。用户可以使用 Bitwarden 生成一个安全且唯一的私钥 |
| 公钥   | 与您要连接的服务器共享的密钥的一部分                                                    |
| 指纹   | 从公钥生成的短唯一字符串，用于识别。例如，可以使用指纹验证 SSH 签名的 Git 提交                          |

存储在 Bitwarden 密码管理器中的 SSH 密钥可以访问 Bitwarden 功能，例如[文件夹](../../your-vault/vault-navigation/folders.md)、[收藏](../../your-vault/vault-navigation/favorites.md)、[主密码重新提示](../../your-vault/vault-items/vault-items.md#protect-individual-items)、笔记、[克隆项目](../../your-vault/vault-items/vault-items.md#clone)、[附件](../../your-vault/vault-items/file-attachments.md)和[自定义字段](../../your-vault/vault-items/custom-fields.md)等。

## 创建新的 SSH 密钥 <a href="#create-new-ssh-key" id="create-new-ssh-key"></a>

您可以通过 Bitwarden 桌面 App、网页 App 或浏览器扩展创建新的 SSH 密钥。创建后，存储在 Bitwarden 中的 SSH 密钥可以通过桌面 App、网页 App、浏览器扩展和移动 App 访问。

1、选择**新建**按钮然后选择 **SSH 密钥**作为项目类型。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1XYC3HwXOTMAPvyW1GS3Mk/4689e814ffe356b6bc262713d7b27668/New_SSH_key.png?_a=DAJCwlWIZAAB" %}
在桌面客户端创建新的 SSH 密钥
{% endembed %}

{% hint style="info" %}
目前，Bitwarden 只能生成 `ED25519` 类型的 SSH 密钥。
{% endhint %}

2、填写诸如**名称**等其余详细信息，完成后选择 **💾保存**图标。

### 组织 SSH 密钥 <a href="#organization-ssh-keys" id="organization-ssh-keys"></a>

可以创建 SSH 密钥并将其存储在组织集合中。具有适当权限的组织成员可以创建、管理和访问组织拥有的 SSH 密钥。在[此处](../../../admin-console/manage-shared-items/collections/collection-permissions.md)了解更多有关集合权限的信息。

要将新的共享 SSH 密钥添加到组织密码库：

1、在桌面或网页 App 的密码库视图中，选择 **✚新增**按钮，然后选择 **SSH 密钥**。

{% hint style="success" %}
组织[所有者、管理员和某些自定义用户](../../../admin-console/manage-members/member-roles.md)也可以直接从管理控制台执行此步骤，以跳过此过程中的一些步骤。
{% endhint %}

2、使用**所有者**下拉列表，选择您希望该项目所属的组织。

3、使用**集合**下拉列表，选择要与其共享此项目的集合。

{% embed url="https://bitwarden.com/assets/1YnrhzwCw78KuFsArEioOO/e0d099972f5887f58fc7d09b95bf278f/organization_ssh_key.png?w=750&fm=avif" %}
组织共享的 SSH 密钥
{% endembed %}

{% hint style="info" %}
通常，使用 SSH 密钥的资源可以支持每用户密钥。我们建议在向组织共享 SSH 密钥之前查看 SSH 密钥最佳实践。
{% endhint %}

### 编辑现有密钥 <a href="#edit-existing-keys" id="edit-existing-keys"></a>

SSH 密钥保存到 Bitwarden 密钥库中后，您可以对某些关键字段，例如名称、所有者、文件夹和自定义字段进行编辑：

{% tabs %}
{% tab title="桌面端" %}
要在 Bitwarden 桌面 App 上编辑 SSH 密钥：

1、打开 Bitwarden 桌面 App 然后导航至 **SSH 密钥**。

2、找到要编辑的 SSH 密钥，然后选择 **✏️编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7wKQygR79OFJP1Nk1c3V3D/4b697f7068083c34da9ba0aed7e33fe8/desktop_edit.png?_a=DAJCwlWIZAAB" %}
桌面端编辑 SSH 项目
{% endembed %}

3、完成所需更改后，选择 **💾保存**。
{% endtab %}

{% tab title="网页 App" %}
要在 Bitwarden 网页 App 上编辑 SSH 密钥：

1、打开 Bitwarden 网页 App 然后导航至 **SSH 密钥**。

2、定位并选择要编辑的 SSH 密钥。屏幕上将出现一个对话框，然后选择**编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/oAvkQjLxtG1yCFAddNMtJ/40a8a4b0ed6bc95ff0f2db99949da330/edit_web.png?_a=DAJCwlWIZAAB" %}
网页 App 编辑 SSH 项目
{% endembed %}

3、完成所需更改后，选择**保存**。
{% endtab %}

{% tab title="移动端" %}
要在 Bitwarden 移动 App 上编辑 SSH 密钥：

1、打开 Bitwarden 移动 App 然后导航至 **SSH 密钥**。

2、定位要编辑的 SSH 密钥，然后选择**编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/65alCgNCYUdRpxoIwMocLr/5bd62fa5cbdc9b6f38becc978541ab87/IMG_1973.jpeg?_a=DAJCwlWIZAAB" %}
iOS 上选择编辑 SSH 密钥
{% endembed %}

3、完成所需更改后，选择**保存**。
{% endtab %}

{% tab title="浏览器扩展" %}
要在 Bitwarden 浏览器扩展上编辑 SSH 密钥：

1、打开 Bitwarden 浏览器扩展然后导航至 **SSH 密钥**。

2、定位并选择要编辑的 SSH 密钥。屏幕上将出现一个对话框，然后选择**编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5DVs8Vi3dJOQsFxbAUElw8/63aa4e007078e646029421e350904be8/2025-02-12_17-02-38.png?_a=DAJCwlWIZAAB" %}
浏览器扩展上编辑 SSH
{% endembed %}

3、完成所需更改后，选择**保存**。
{% endtab %}
{% endtabs %}

## 将密钥导入 Bitwarden <a href="#import-key-to-bitwarden" id="import-key-to-bitwarden"></a>

现有的 SSH 密钥可通过桌面客户端导入 Bitwarden。

1、选择**新增**按钮然后选择 **SSH 密钥**作为项目类型。

2、复制您想要导入到 Bitwarden 的现有 SSH 密钥。

2、使用**从剪贴板导入密钥**图标。这将自动将 SSH 密钥粘贴到 Bitwarden 中。

* 导入的密钥必须是 **OpenSSH** 或 **PKCS#8** 格式。

{% embed url="https://bitwarden.com/assets/5QTvyu39h3o0azkjU26P3t/9c2203a723f91c6a9b34c848bd0cb300/imported_key_ui.png?w=563&fm=avif&q=80" %}
在桌面客户端上导入 SSH 密钥
{% endembed %}

{% hint style="info" %}
此外，目前还不兼容从 Putty 导入的 SSH 密钥。
{% endhint %}

## 配置 Bitwarden SSH 代理 <a href="#configure-bitwarden-ssh-agent" id="configure-bitwarden-ssh-agent"></a>

要将 Bitwarden 用作您的主要 SSH 代理，您需要配置 SSH 客户端，以与 Bitwarden 进行身份验证。

{% tabs %}
{% tab title="Windows" %}
要在 Windows 上启用 Bitwarden SSH 代理，必须禁用 Windows 机器上的 OpenSSH 服务。要禁用 OpenSSH：

1、在 Windows 机器上，导航至**服务** → **OpenSSH Authentication Agent**。可使用 Windows 搜索栏查找服务。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/77fTJpxIBH5ikJYQW1KFL7/0c6fa3b9f68f7a85569ad6ede489979e/openSSH_agent.png?_a=DAJAUVWIZAAB" %}
Windows 服务面板
{% endembed %}

2、打开 OpenSSH Authentication Agent 属性窗口后，将**启动类型**设置设为**禁用**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6Ghl3WkroGhoyy4fUMDbCg/800780f201fff9d6dc2de3d6577587ac/Screenshot_2024-12-04_142322.png?_a=DAJAUVWIZAAB" %}
禁用 OpenSSH 窗口
{% endembed %}

3、调整设置后，选择**应用**，然后选择**确定**。
{% endtab %}

{% tab title="macOS" %}
### macOS 商店 <a href="#macos-store" id="macos-store"></a>

要在 macOS 商店下载上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。下面的示例演示了如何执行此操作（将 `<user>` 替换为您的用户名）：

```bash
export SSH_AUTH_SOCK=/Users/<user>/Library/Containers/com.bitwarden.desktop/Data/.bitwarden-ssh-agent.sock
```

### .dmg 下载 <a href="#dmg-download" id="dmg-download"></a>

要在 macOS .dmg 下载上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。下面的示例演示了如何执行此操作（将 `<user>` 替换为您的用户名）：

```bash
export SSH_AUTH_SOCK=/Users/<user>/.bitwarden-ssh-agent.sock
```

2、或者，配置 SSH\_AUTH\_SOCKET：

```bash
launchctl setenv "SSH_AUTH_SOCKET" "/Users/<user>/.bitwarden-ssh-agent.sock"
```
{% endtab %}

{% tab title="Linux" %}
要在 Linux 上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。下面的示例演示了如何执行此操作（将 `<user>` 替换为您的用户名）：

```bash
export SSH_AUTH_SOCK=/home/<user>/.bitwarden-ssh-agent.sock
```

### Shell 配置 <a href="#shell-configuration" id="shell-configuration"></a>

1、访问您的 `.bashrc` 或 `.zshrc` 文件：

```bash
nano ~/.bashrc
nano ~/.zshrc
```

2、在 `.bashrc` 或 `.zshrc` 文件中设置环境变量：

```bash
export SSH_AUTH_SOCK=/home/<user>/.bitwarden-ssh-agent.sock
```

### Snap 和 Flatpak <a href="#snap-and-flatpak" id="snap-and-flatpak"></a>

要在 Snap 和 Flatpak 安装上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。下面的示例演示了如何执行此操作（将 `<user>` 替换为您的用户名）：

```bash
# Snap
export SSH_AUTH_SOCK=/home/<user>/snap/bitwarden/current/.bitwarden-ssh-agent.sock

# Flatpak
export SSH_AUTH_SOCK=/home/<user>/.var/app/com.bitwarden.desktop/data/.bitwarden-ssh-agent.sock`
```
{% endtab %}
{% endtabs %}

## 启用 SSH 代理 <a href="#enable-ssh-agent" id="enable-ssh-agent"></a>

要在 Bitwarden 桌面 App 上启用 SSH 代理，请导航至**设置**然后选中**启用 SSH 代理**。

{% embed url="https://bitwarden.com/assets/7Fx7AnfIPXmiJpHq1lFhTx/4591ef1b514df8fe1d51c30dc5ffd4d5/2025-05-20_16-06-21.png?w=992&fm=avif&q=80" %}
在桌面客户端上启用 SSH 存储
{% endembed %}

启用 SSH 代理后，还可以调整**使用 SSH 代理时要求身份验证**设置。该设置将决定 Bitwarden 何时要求验证对 SSH 密钥的访问权限：

{% embed url="https://bitwarden.com/assets/7M0oE4BXZWiTpub3Vqwfpp/803eabf2073b2035266469c6c2d4ead8/2025-05-22_09-00-17.png?w=450&fm=avif&q=80" %}

* 总是
* 从不
* 记住直到密码库被锁定

默认情况下将选择**始终**。

## 测试 SSH 密钥 <a href="#testing-ssh-keys" id="testing-ssh-keys"></a>

为 Bitwarden 配置好 SSH 代理后，我们就可以通过请求 SSH 列表来测试设置：

```bash
ssh-add -L
```

这将返回保存在 Bitwarden 桌面客户端中的 SSH 密钥列表。

{% hint style="info" %}
访问 SSH 密钥时，Bitwarden 的行为会根据客户端的锁定或解锁状态而有所不同：

* **已锁定的密码库**：如果您的 Bitwarden 密码库处于锁定状态，Bitwarden 会自动提示您解锁密码库以获取 SSH 密钥。
* **已解锁的密码库**：如果桌面密码库已解锁，系统将提示您确认 SSH 密钥的使用。
{% endhint %}

### 使用 SSH 密钥验证 Git <a href="#use-ssh-key-to-authenticate-with-git" id="use-ssh-key-to-authenticate-with-git"></a>

SSH 可用于 Git 身份验证。Bitwarden SSH 代理能为你的 Git 工作流增添安全性和易用性。在本示例中，Bitwarden SSH 代理将用于验证 GitHub。

1、在 GitHub 账户上，通过导航至**设置** → **SSH 和 GPG 密钥**，然后选择**新建 SSH 密钥**，来设置 SSH 密钥。

2、在添加新 SSH 密钥界面，添加**名称**，选择**密钥类型**，选择**验证密钥**。将 Bitwarden 密码库中的**公钥**复制并粘贴到 GitHub 上的**密钥**字段。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1bZWyhzPtdpdhoDM6GNYdz/3c326b32d15d134ff7532a57041ceff4/2025-02-12_11-26-35.png?_a=DAJCwlWIZAAB" %}
创建新的 GitHub 密钥
{% endembed %}

3、完成所有字段后，选择**添加 SSH 密钥**以保存密钥。在保存密钥之前，GitHub 会要求您验证 GitHub 账户。

4、在终端测试 GitHub SSH 密钥，假如您使用的是 macOS：

```bash
ssh git@github.com
```

5、如果成功，Bitwarden 会提示您验证访问请求。选择**授权**以确认。如果成功，您将收到一条验证身份验证尝试的消息：

```
Hi <USER>! You've successfully authenticated, but GitHub does not provide shell access.
```

## 使用 Git 存储库进行身份验证 <a href="#authenticate-with-git-repositories" id="authenticate-with-git-repositories"></a>

使用 Bitwarden SSH 代理签署 SSH Git 提交。在使用 Bitwarden SSH 代理签署 Git 提交之前，系统需要满足以下条件：

* Git 2.34 或更新版本。使用以下命令检查 Git 版本：

```bash
git --version
```

* OpenSSH 8.8 或更新版本。用以下命令检查版本：

```bash
ssh -V
```

* 成功启用了 SSH 代理的 Bitwarden 桌面客户端。

### 为 SSH 签名配置 Git <a href="#configure-git-for-ssh-signing" id="configure-git-for-ssh-signing"></a>

配置 Git 环境以将签名指向 SSH 密钥。为此，您可以设置全局变量或在您的 `.gitconfig` 文件中建立相关说明。

#### 设置全局变量 <a href="#set-global-variables" id="set-global-variables"></a>

要使用 `--global` 变量配置 Git 设置：

1、设置 Git 使用 SSH 签名：

```bash
git config --global gpg.format ssh
```

2、为用于签名的密钥指定 SSH 密钥。要使用 Bitwarden SSH 代理，请将 `<YOUR_PUBLIC_KEY>` 替换为从 Bitwarden 密码库中保存的 SSH 密钥中复制的公钥。

```bash
git config --global user.signingkey "<YOUR_PUBLIC_KEY>"
```

#### 设置 `.gitconfig` 文件 <a href="#set-.gitconfig-file" id="set-.gitconfig-file"></a>

要使用 `.gitconfig` 文件配置 Git：

1、使用您喜欢的文本编辑器访问 `.gitconfig`：

```bash
nano ~/.gitconfig
```

2、添加以下配置：

```bash
[gpg]
        format = ssh
[user]
        signingkey = "<YOUR_PUBLIC_KEY>"
        name = <USER_NAME>
        email = <USER_EMAIL>
[commit]
        gpgsign = true
```

{% hint style="info" %}
对于 Windows 用户：

1、将 `core.sshCommand` 变量添加到 Git 配置中，以使用 Microsoft OpenSSH：

```bash
git config --global core.sshCommand "C:/Windows/System32/OpenSSH/ssh.exe"
```

或者，在 `.gitconfig` 文件中设置变量：

```bash
[core]
  sshCommand = C:/Windows/System32/OpenSSH/ssh.exe
```

2、接下来，可能需要设置 `gpg.ssh.program` 参数：

```bash
git config gpg.ssh.program "C:/Windows/System32/OpenSSH/ssh-keygen.exe"
```
{% endhint %}

### 签署 Git 提交 <a href="#sign-git-commits" id="sign-git-commits"></a>

使用 SSH 对 Git 进行身份验证，能为您的工作流增添安全性和易用性。同样，存储在 Bitwarden 中的 SSH 密钥也可用于使用 SSH 协议签署和验证 Git 提交。在本示例中，我们将使用 Bitwarden SSH 代理签署 Git 提交到 GitHub。

1、在 GitHub 账户上，通过导航至**设置** → **SSH 和 GPG 密钥**，然后选择**新建 SSH 密钥**，来设置 SSH 签名密钥。

2、在添加新 SSH 密钥界面，添加**名称**并选择**密钥类型**，选择 `Signing Key`。将 Bitwarden 密钥库中的**公钥**复制并粘贴到 GitHub 上的**密钥**字段中。

3、使用以下命令将 git 配置为使用 `allowedSignersFile`：

```shellscript
git config --global gpg.ssh.allowedSigners "$HOME/.ssh/allowedSigners"
```

4、将您的公钥添加到 allowedSignersFile 中：

```shellscript
# Create allowedSigners file
touch ~/.ssh/allowedSigners

# Add your public key pair you wish to trust
 User1@Bitwarden.com ssh-ed25519 <Your_Public_Key>
```

5、使用 SSH 密钥以 SSH 方式克隆您的存储库：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/76Snkd9TQMrVMmegeJRqK/21836de7c7500b9ebdabaeb1d17b9659/2025-02-12_17-16-13.png?_a=DAJCwlWIZAAB" %}
SSH 克隆
{% endembed %}

```bash
git clone git@github.com:<USER>/<repository>.git
```

6、使用终端或您喜欢的文本编辑器创建 Git 提交：

```bash
git commit -m "This commit is signed using SSH"
```

7、Bitwarden 将提示您对此密钥的使用进行授权：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/0aGz4U3YpB63EHRWVU2YY/6664aea9ab6649911947cac667549e7f/signing_key_approve.png?_a=DAJCwlWIZAAB" %}
使用客户端授权 SSH
{% endembed %}

8、授权后，将初始化 SSH 密钥以批准提交。现在您可以推送提交：

```bash
git push
```

9、通过导航到 GitHub commits 以验证您在 Github 上的提交：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1PR4Sss3Pvf3anlau5AlgC/ecfdb02b50fb83f59a21ebc7ed550042/2025-02-12_14-51-41.png?_a=DAJCwlWIZAAB" %}

## SSH 代理转发 <a href="#ssh-agent-forwarding" id="ssh-agent-forwarding"></a>

SSH 代理转发允许您访问的远程服务器使用您的密钥向其他服务器进行身份验证，而不会将您的私钥暴露在密码库之外。您登录的服务器可以请求您的本地 Bitwarden 实例对远程服务器进行身份验证。在本例中，我们将演示在服务器之间传输一个文件：

1、首先，通过导航至**设置**然后**启用 SSH 代理**，确保已在 Bitwarden 桌面 App 上启用 SSH 代理：

{% embed url="https://bitwarden.com/assets/7Fx7AnfIPXmiJpHq1lFhTx/4591ef1b514df8fe1d51c30dc5ffd4d5/2025-05-20_16-06-21.png?w=992&fm=avif" %}
在桌面客户端上启用 SSH 存储
{% endembed %}

2、创建新的 SSH 密钥或导入现有的 SSH 密钥到 Bitwarden 桌面 App。

3、打开与要发送文件的服务器的连接，激活代理转发：

```bash
ssh -A <Hostname>
```

4、向服务器发送一个文件：

```bash
rsync -avzP ./TEST.txt <USER>@<Hostname>:/home/<USER>/test.txt
```

5、Bitwarden 会提示您批准此 SSH 密钥得访问权限。将显示 SSH 密钥已被请求并用于完成文件传输。

{% embed url="https://bitwarden.com/assets/26n37qx0HKJ47ZdAzP2UFw/611025ed1513d6441acc4fecf547e12e/395218105-683d4ead-1f7e-46b3-8799-7591a74952af.png?w=750&fm=avif&q=80" %}
确认 SSH 代理转发
{% endembed %}

# SSH 代理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ssh-agent/)
{% endhint %}

Bitwarden SSH 代理可以安全地加密和存储您的 SSH（安全 Shell）密钥，以用于以下目的：

* 验证服务器身份
* 签署 Git 提交
* 与基于 SSH 的服务进行交互

Bitwarden SSH 代理将您的密钥组织并保护在一个安全的位置。SSH 密钥可以通过桌面 App、网页 App、浏览器扩展和移动 App 访问。SSH 密钥可以通过桌面 App、网页 App和浏览器扩展生成。

{% hint style="info" %}
**macOS**：

macOS 商店构建版本目前暂不支持 SSH 代理，[.dmg 下载](https://bitwarden.com/download/)可用于获得 SSH 代理支持。

**Linux**：

Flatpak 版本目前暂不支持 SSH 代理，[Snap 下载](https://bitwarden.com/download/#downloads-desktop)可用于获得 SSH 代理支持。
{% endhint %}

## SSH 密钥存储 <a href="#storing-an-ssh-key" id="storing-an-ssh-key"></a>

您可以在 Bitwarden 桌面 App 中创建并保存新的 SSH 密钥。Bitwarden 存储的 SSH 密钥将包含以下内容：

| 字段   | 描述                                                                    |
| ---- | --------------------------------------------------------------------- |
| 密钥名称 | 您的 SSH 密钥的名称                                                          |
| 私钥   | 私钥是敏感数据，服务器将使用它来帮助建立安全连接。私钥数据应谨慎处理并保持安全。用户可以使用 Bitwarden 生成一个安全且唯一的私钥 |
| 公钥   | 与您要连接的服务器共享的密钥的一部分                                                    |
| 指纹   | 从公钥生成的短唯一字符串，用于识别。例如，可以使用指纹验证 SSH 签名的 Git 提交                          |

存储在 Bitwarden 密码管理器中的 SSH 密钥可以使用 Bitwarden 的功能，例如[文件夹](../../your-vault/folders.md)、[收藏](../../your-vault/favorites.md)、[主密码重新提示](../../your-vault/vault-items.md#protect-individual-items)、笔记、[克隆项目](../../your-vault/vault-items.md#clone)、[附件](../../your-vault/file-attachments.md)和[自定义字段](../../your-vault/custom-fields.md)。

## 创建新的 SSH 密钥 <a href="#create-new-ssh-key" id="create-new-ssh-key"></a>

您可以通过 Bitwarden 桌面 App、网页 App或浏览器扩展创建新的 SSH 密钥。创建后，存储在 Bitwarden 中的 SSH 密钥可以通过桌面 App、网页 App、浏览器扩展和移动 App 访问。

1、点击**新建**按钮并选择 **SSH 密钥**作为项目类型。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1XYC3HwXOTMAPvyW1GS3Mk/89c7ee8a5127ad1295fc3074ce3339bb/2024-11-08_15-08-44.png?_a=DAJCwlWIZAAB" %}
在桌面客户端创建新的 SSH 密钥
{% endembed %}

{% hint style="info" %}
目前，Bitwarden 只能生成 `ED25519` 类型的 SSH 密钥。
{% endhint %}

2、填写诸如**名称**等其余详细信息，完成后选择 **💾保存**图标。

### 组织 SSH 密钥 <a href="#organization-ssh-keys" id="organization-ssh-keys"></a>

组织拥有的 SSH 密钥不能在 SSH 代理中使用。个人组织用户可以创建 SSH 密钥并将其存储在个人密码库中用于身份验证。不建议共享 SSH 凭据。

### 编辑现有密钥 <a href="#edit-existing-keys" id="edit-existing-keys"></a>

SSH 密钥保存到 Bitwarden 密钥库中后，您可以对它们进行编辑：

{% tabs %}
{% tab title="桌面端" %}
要在 Bitwarden 桌面 App 上编辑 SSH 密钥：

1、打开 Bitwarden 桌面 App 然后导航至 **SSH 密钥**。

2、找到要编辑的 SSH 密钥，然后选择 **✏️编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7wKQygR79OFJP1Nk1c3V3D/8b4f5620b35ad79951b55a3153843753/edit.png?_a=DAJAUVWIZAAB" %}
桌面端编辑 SSH 项目
{% endembed %}

3、完成所需更改后，选择 **💾保存**。
{% endtab %}

{% tab title="网页 App" %}
要在 Bitwarden 网页 App 上编辑 SSH 密钥：

1、打开 Bitwarden 网页 App 然后导航至 **SSH 密钥**。

2、定位并选择要编辑的 SSH 密钥。屏幕上将出现一个对话框，然后选择**编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/oAvkQjLxtG1yCFAddNMtJ/e75bf0f6314df1b30e691a78665f0efa/2024-12-05_10-43-25.png?_a=DAJAUVWIZAAB" %}
网页 App 编辑 SSH 项目
{% endembed %}

3、完成所需更改后，选择**保存**。
{% endtab %}

{% tab title="移动端" %}
要在 Bitwarden 移动 App 上编辑 SSH 密钥：

1、打开 Bitwarden 移动 App 然后导航至 **SSH 密钥**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6jJtth7lywypuSBqYZlzm1/45d9642e8d01698f8201d3960467f5ab/IMG_1900.jpg?_a=DAJAUVWIZAAB" %}
移动端 SSH 密钥密码库
{% endembed %}

2、定位要编辑的 SSH 密钥，然后选择**编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/65alCgNCYUdRpxoIwMocLr/8c43526942a90f89b0c3547059ea5148/IMG_1903.jpg?_a=DAJAUVWIZAAB" %}
iOS 上选择编辑 SSH 密钥
{% endembed %}

3、完成所需更改后，选择**保存**。
{% endtab %}

{% tab title="浏览器扩展" %}
要在 Bitwarden 浏览器扩展上编辑 SSH 密钥：

1、打开 Bitwarden 浏览器扩展然后导航至 **SSH 密钥**。

2、定位并选择要编辑的 SSH 密钥。屏幕上将出现一个对话框，然后选择**编辑**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5DVs8Vi3dJOQsFxbAUElw8/bf4126ae5575fdd5f04ad298a38e57d9/2025-01-15_12-17-04.png?_a=DAJAUVWIZAAB" %}
浏览器扩展上编辑 SSH
{% endembed %}

3、完成所需更改后，选择**保存**。
{% endtab %}
{% endtabs %}

## 将密钥导入 Bitwarden <a href="#import-key-to-bitwarden" id="import-key-to-bitwarden"></a>

现有的 SSH 密钥可以导入 Bitwarden。

1、从导航菜单中选择 **🔑SSH 密钥**。

2、复制要导入到 Bitwarden 的现有 SSH 密钥。使用**从剪贴板导入密钥**选项。这将自动将 SSH 密钥粘贴到 Bitwarden 中。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5QTvyu39h3o0azkjU26P3t/05f61ac4ebe4683844d0130d48c00a70/2024-11-08_16-02-04.png?_a=DAJAUVWIZAAB" %}
在桌面客户端上导入 SSH 密钥
{% endembed %}

{% hint style="info" %}
导入的密钥必须是 **OpenSSH** 或 **PKCS#8** 格式。

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

{% hint style="info" %}
如果服务列表中没有 OpenSSH Authentication Agent 选项，则无需禁用该服务。
{% endhint %}

4、要在 Git 中使用 SSH 代理，请将 Git 配置中的 `core.sshCommand` 变量配置为使用 Microsoft OpenSSH：

```bash
git config --global core.sshCommand "C:/Windows/System32/OpenSSH/ssh.exe"
```

5、这也可以使用您的 `gitconfig` 文件来设置：

```bash
[core]
  sshCommand = C:/Windows/System32/OpenSSH/ssh.exe
```
{% endtab %}

{% tab title="macOS" %}
要在 macOS 上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。下面的示例演示了如何在 macOS 上执行此操作（将 `<user>` 替换为您的用户名）：

```bash
export SSH_AUTH_SOCK=/Users/<user>/.bitwarden-ssh-agent.sock
```
{% endtab %}

{% tab title="Linux" %}
要在 Linux 上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。下面的示例演示了如何在 Linux 上执行此操作（将 `<user>` 替换为您的用户名）：

```bash
export SSH_AUTH_SOCK=/home/<user>/.bitwarden-ssh-agent.sock
```
{% endtab %}

{% tab title="Snap" %}
要在 snap 安装上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。下面的示例演示了如何在 snap 上执行此操作（将 `<user>` 替换为您的用户名）：

```bash
export SSH_AUTH_SOCK=/home/<user>/snap/bitwarden/current/.bitwarden-ssh-agent.sock
```
{% endtab %}
{% endtabs %}

## 启用 SSH 代理 <a href="#enable-ssh-agent" id="enable-ssh-agent"></a>

要在 Bitwarden 桌面 App 上启用 SSH 代理，请导航至**设置**然后**启用 SSH 代理**。

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7Fx7AnfIPXmiJpHq1lFhTx/db8dc33356f28b7c347dbe6f7af490fe/2024-12-09_09-09-08.png?_a=DAJAUVWIZAAB" alt=""><figcaption><p>在桌面客户端上启用 SSH 存储</p></figcaption></figure>

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

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4lrBnoOuS7qBO5Ql4V4QD9/872c38b4e3a2331aa60ed507a86426d5/2024-11-08_16-40-05.png?_a=DAJAUVWIZAAB" %}
创建新的 GitHub SSH 密钥
{% endembed %}

2、在添加新 SSH 密钥界面，添加**名称**，选择**密钥类型**，选择**验证密钥**。将 Bitwarden 密码库中的**公钥**复制并粘贴到 GitHub 上的**密钥**字段。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1bZWyhzPtdpdhoDM6GNYdz/3c59429b416a648550dbc07f960db41d/2024-11-08_16-53-44.png?_a=DAJAUVWIZAAB" %}
创建新的 GitHub 密钥
{% endembed %}

3、完成所有字段后，选择**添加 SSH 密钥**以保存密钥。在保存密钥之前，GitHub 会要求您验证 GitHub 账户。

4、在终端测试 GitHub SSH 密钥，假如您使用的是 macOS：

```bash
ssh git@github.com
```

5、如果成功，Bitwarden 会提示您验证访问请求。选择**授权**以确认。如果成功，您将收到一条验证身份验证尝试的消息：

```bash
Hi <USER>! You've successfully authenticated, but GitHub does not provide shell access.
```

## 使用 Git 仓库进行身份验证 <a href="#authenticate-with-git-repositories" id="authenticate-with-git-repositories"></a>

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

### 签署 Git 提交 <a href="#sign-git-commits" id="sign-git-commits"></a>

使用 SSH 对 Git 进行身份验证，能为您的工作流增添安全性和易用性。同样，存储在 Bitwarden 中的 SSH 密钥也可用于使用 SSH 协议签署和验证 Git 提交。在本示例中，我们将使用 Bitwarden SSH 代理签署 Git 提交到 GitHub。

1、在 GitHub 账户上，通过导航至**设置** → **SSH 和 GPG 密钥**，然后选择**新建 SSH 密钥**，来设置 SSH 签名密钥。

2、在添加新 SSH 密钥界面，添加**名称**并选择**密钥类型**，选择 `Signing Key`。将 Bitwarden 密钥库中的**公钥**复制并粘贴到 GitHub 上的**密钥**字段中。

3、使用 SSH 密钥以 SSH 方式克隆您的仓库：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/76Snkd9TQMrVMmegeJRqK/d072dc808665212512221d0f176c0b98/2024-11-19_12-09-07.png?_a=DAJAUVWIZAAB" %}
SSH 克隆
{% endembed %}

```bash
git clone git@github.com:<USER>/<repository>.git
```

4、使用终端或您喜欢的文本编辑器创建 Git 提交：

```bash
git commit -m "This commit is signed using SSH"
```

5、Bitwarden 将提示您授权密钥的使用：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/0aGz4U3YpB63EHRWVU2YY/fd1c54888857fc77e0f68b58549e5db7/2024-11-12_09-33-00.png?_a=DAJAUVWIZAAB" %}
使用客户端授权 SSH
{% endembed %}

6、授权后，将初始化 SSH 密钥以批准提交。现在您可以推送提交：

```bash
git push
```

7、通过导航到 GitHub commits 以验证您在 Github 上的提交：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1PR4Sss3Pvf3anlau5AlgC/cca4c1ec9936109d7434aa77f1afa7ce/2024-12-04_11-32-12.png?_a=DAJAUVWIZAAB" %}

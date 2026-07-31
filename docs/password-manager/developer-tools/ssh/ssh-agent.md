# SSH 代理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ssh-agent/)
{% endhint %}

Bitwarden Password Manager 桌面 App 可以作为 SSH 代理来安全地加密和存储您的 SSH（安全 Shell）密钥，以用于以下目的：

* 对服务进行身份验证
* 签署 Git 提交
* 与基于 SSH 的服务进行交互

有关代理的工作原理、支持的密钥类型、已知限制以及密码库行为的更多信息，请参阅[关于 SSH](about-ssh.md)。

## 启用 SSH 代理 <a href="#enable-ssh-agent" id="enable-ssh-agent"></a>

要在 Bitwarden 桌面 App 上启用 SSH 代理，请导航至**设置**然后选中**启用 SSH 代理**。然后，调整**使用 SSH 代理时要求身份验证**设置。该设置将决定 Bitwarden 何时要求验证对 SSH 密钥的访问权限：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7Fx7AnfIPXmiJpHq1lFhTx/d151287d040a69dcb52d36fc6a4593b9/Enable_SSH_agent_updated.png?w=651&#x26;fm=avif" alt=""><figcaption><p>在桌面客户端上启用 SSH 存储</p></figcaption></figure></div>

### 根据密码库状态的行为 <a href="#behavior-by-vault-state" id="behavior-by-vault-state"></a>

SSH 代理的行为会根据密码库的当前状态而有所不同。以下描述的是启用代理后单账户的行为。

<table><thead><tr><th width="183">密码库状态</th><th width="120">代理运行中</th><th width="111.99993896484375">列出请求</th><th>签署请求</th></tr></thead><tbody><tr><td>已注销</td><td>否</td><td></td><td></td></tr><tr><td>已锁定（初始解锁前）</td><td>是</td><td>支持</td><td>提示解锁密码库</td></tr><tr><td>已锁定（初始解锁后）</td><td>是</td><td>支持</td><td>提示解锁密码库，然后提示授权</td></tr><tr><td>已解锁</td><td>是</td><td>支持</td><td>支持</td></tr></tbody></table>

## 配置您的系统以使用 Bitwarden SSH 代理 <a href="#configure-your-system-to-use-bitwarden-ssh-agent" id="configure-your-system-to-use-bitwarden-ssh-agent"></a>

要将 Bitwarden 用作您的主要 SSH 代理，您需要配置 SSH 客户端，使其与 Bitwarden 进行通信以完成身份验证。在桌面 App 中启用代理后，请配置您的操作系统，将 SSH 请求路由到 Bitwarden：

{% tabs %}
{% tab title="Windows" %}
要在 Windows 上启用 Bitwarden SSH 代理，必须禁用 Windows 机器上的 OpenSSH 服务。要禁用 OpenSSH：

1、在 Windows 机器上，导航至**服务** → **OpenSSH Authentication Agent**。可使用 Windows 搜索栏查找服务。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/77fTJpxIBH5ikJYQW1KFL7/0c6fa3b9f68f7a85569ad6ede489979e/openSSH_agent.png?w=700&#x26;fm=avif" alt=""><figcaption><p>Windows 服务面板</p></figcaption></figure></div>

2、打开 OpenSSH Authentication Agent 属性窗口后，将**启动类型**设置设为**禁用**。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6Ghl3WkroGhoyy4fUMDbCg/800780f201fff9d6dc2de3d6577587ac/Screenshot_2024-12-04_142322.png?w=400&#x26;fm=avif" alt=""><figcaption><p>禁用 OpenSSH 窗口</p></figcaption></figure></div>

3、调整设置后，选择**应用**，然后选择**确定**。
{% endtab %}

{% tab title="macOS App Store" %}
要在 macOS 商店下载上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。在下面的示例中，将 `<user>` 替换为您的用户名：

```bash
export SSH_AUTH_SOCK=/Users/<user>/Library/Containers/com.bitwarden.desktop/Data/.bitwarden-ssh-agent.sock
```

2、要使此配置持久生效，请将 `export` 命令添加到您的 `~/.zhrc` 或 `~/.bashrc` 文件中。
{% endtab %}

{% tab title="macOS .dmg" %}
要在 macOS .dmg 下载上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。在下面的示例中，将 `<user>` 替换为您的用户名：

```bash
export SSH_AUTH_SOCK=/Users/<user>/.bitwarden-ssh-agent.sock
```

2、或者，配置 `SSH_AUTH_SOCKET`：

```bash
launchctl setenv "SSH_AUTH_SOCKET" "/Users/<user>/.bitwarden-ssh-agent.sock"
```

3、要使此配置持久生效，请将 `export` 命令添加到您的 `~/.zhrc` 或 `~/.bashrc` 文件中。

{% hint style="info" %}
使用 `launchctl` 命令后，您可能需要重启终端。
{% endhint %}
{% endtab %}

{% tab title="Linux" %}
要在 Linux 上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。在下面的示例中，将 `<user>` 替换为您的用户名：

```bash
export SSH_AUTH_SOCK=/home/<user>/.bitwarden-ssh-agent.sock
```

2、要使此配置持久生效，请将 `export` 命令添加到您的 `~/.zhrc` 或 `~/.bashrc` 文件中。
{% endtab %}

{% tab title="Snap 和 Flatpak" %}
要在 Snap 和 Flatpak 安装上启用 Bitwarden SSH 代理：

1、配置 `SSH_AUTH_SOCK` 变量，使其指向 Bitwarden SSH 代理套接字。在下面的示例中，将 `<user>` 替换为您的用户名：

```bash
# Snap
export SSH_AUTH_SOCK=/home/<user>/snap/bitwarden/current/.bitwarden-ssh-agent.sock

# Flatpak
export SSH_AUTH_SOCK=/home/<user>/.var/app/com.bitwarden.desktop/data/.bitwarden-ssh-agent.sock`
```
{% endtab %}
{% endtabs %}

## 测试 SSH 代理 <a href="#test-ssh-agent" id="test-ssh-agent"></a>

为 Bitwarden 配置好 SSH 代理后，我们可以通过请求 SSH 列表来测试设置：

```bash
ssh-add -L
```

## 场景与工作流程 <a href="#scenarios-and-workflows" id="scenarios-and-workflows"></a>

代理已启用且操作系统已配置完成后，您就可以在各种工具和工作流程中使用 Bitwarden SSH 密钥了。以下场景将为一系列常见设置和用例提供分步配置指南。

### 使用 SSH 通过 Git 进行身份验证 <a href="#use-ssh-to-authenticate-with-git" id="use-ssh-to-authenticate-with-git"></a>

SSH 可用于 Git 身份验证。Bitwarden SSH 代理能为您的 Git 工作流增添安全性和易用性。在本示例中，Bitwarden SSH 代理将用于向 GitHub 进行身份验证。

1、在您的 GitHub 账户上，通过导航至**设置** → **SSH 和 GPG 密钥**，然后选择**新建 SSH 密钥**，来设置一个 SSH 密钥。

2、在添加新 SSH 密钥界面，添加**名称**，选择**密钥类型**，选择 `Authentication Key`。将 Bitwarden 密码库中的**公钥**复制并粘贴到 GitHub 上的**密钥**字段。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1bZWyhzPtdpdhoDM6GNYdz/3c326b32d15d134ff7532a57041ceff4/2025-02-12_11-26-35.png?w=760&#x26;fm=avif" alt=""><figcaption><p>创建新的 GitHub 密钥</p></figcaption></figure></div>

3、完成所有字段后，选择**添加 SSH 密钥**以保存密钥。在保存密钥之前，GitHub 会要求您验证您的 GitHub 账户。

4、在终端测试 GitHub SSH 密钥，例如您使用的是 macOS：

```bash
ssh git@github.com
```

5、如果成功，Bitwarden 将提示您验证访问请求。选择**授权**以确认。如果成功，您将收到一条验证身份验证尝试的消息：

```
Hi <USER>! You've successfully authenticated, but GitHub does not provide shell access.
```

### 使用 Git 存储库进行身份验证 <a href="#authenticate-with-git-repositories" id="authenticate-with-git-repositories"></a>

使用 Bitwarden SSH 代理签署 SSH Git 提交。在使用 Bitwarden SSH 代理签署 Git 提交之前，系统需要满足以下条件：

* Git 2.34 或更新版本。使用以下命令检查 Git 版本：

```bash
git --version
```

* OpenSSH 8.8 或更新版本。用以下命令检查版本：

```bash
ssh -V
```

* 启用了 SSH 代理的 Bitwarden 桌面客户端。

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

3、启用自动提交签名。

```bash
git config --global commit.gpgsign true
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

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/76Snkd9TQMrVMmegeJRqK/21836de7c7500b9ebdabaeb1d17b9659/2025-02-12_17-16-13.png?w=420&#x26;fm=avif" alt=""><figcaption><p>SSH 克隆</p></figcaption></figure></div>

```bash
git clone git@github.com:<USER>/<repository>.git
```

6、使用终端或您喜欢的文本编辑器创建 Git 提交：

```bash
git commit -m "This commit is signed using SSH"
```

7、Bitwarden 将根据用户设置提示您对此密钥的使用进行授权。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/0aGz4U3YpB63EHRWVU2YY/d7e7883eb93065205226df80ffebde7c/github_auth_key.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>使用客户端授权 SSH</p></figcaption></figure></div>

8、授权后，将初始化 SSH 密钥以批准提交。现在您可以推送提交：

```bash
git push
```

9、通过导航到 GitHub commits 以验证您在 Github 上的提交。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1PR4Sss3Pvf3anlau5AlgC/ecfdb02b50fb83f59a21ebc7ed550042/2025-02-12_14-51-41.png?w=565&#x26;fm=avif" alt=""><figcaption><p>在 GitHub 中验证您的提交</p></figcaption></figure></div>

## SSH 代理转发 <a href="#ssh-agent-forwarding" id="ssh-agent-forwarding"></a>

SSH 代理转发允许您访问的远程服务器使用您的密钥向其他服务器进行身份验证，而不会将您的私钥暴露在密码库之外。您登录的服务器可以请求您的本地 Bitwarden 实例对远程服务器进行身份验证。在本例中，我们将演示在服务器之间传输一个文件：

1、创建新的 SSH 密钥或导入现有的 SSH 密钥到 Bitwarden 桌面 App。

2、打开与要发送文件的服务器的连接，激活代理转发：

```bash
ssh -A <Hostname>
```

3、向服务器发送一个文件：

```bash
rsync -avzP ./TEST.txt <USER>@<Hostname>:/home/<USER>/test.txt
```

4、Bitwarden 将提示您批准此 SSH 密钥的访问权限。将显示 SSH 密钥已被请求并用于完成文件传输。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4TPhGUdynuGBHj1l4zmUcS/04aae27ee063080afc5fbd6183a354b3/Confirm_SSH_key_usage.webp?w=960&#x26;fm=avif" alt=""><figcaption><p>确认 SSH 代理转发</p></figcaption></figure></div>

## 故障排除 <a href="#troubleshooting" id="troubleshooting"></a>

以下部分包括用户在使用 SSH 代理时可能遇到的常见问题。

`Error connecting to agent: Connection refused`

* 代理未运行；请确认其已正确启用，然后检查 App 日志。

`ssh <action>` fails

* 尝试使用 `-vvv` 运行命令，然后捕获输出以在错误报告中分享。

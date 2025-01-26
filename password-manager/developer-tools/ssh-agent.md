# =SSH 代理

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ssh-agent/)
{% endhint %}

Bitwarden SSH 代理可以安全地加密和存储您的 SSH（安全 Shell）密钥，以用于以下目的：

* 验证服务器身份
* 签署 Git 提交
* 与基于 SSH 的服务进行交互

Bitwarden SSH 代理将您的密钥组织并保护在一个安全的位置。SSH 密钥可以通过桌面 App、网页 App、浏览器扩展和移动 App 访问。SSH 密钥可以通过桌面 App、网页 App和浏览器扩展生成。

{% hint style="info" %}
macOS 商店构建版本目前暂不支持 SSH 代理，但可以通过 [.dmg 下载](https://bitwarden.com/download/)获得 SSH 代理支持。
{% endhint %}

## SSH 密钥存储 <a href="#storing-an-ssh-key" id="storing-an-ssh-key"></a>

您可以在 Bitwarden 桌面 App 中创建并保存新的 SSH 密钥。Bitwarden 存储的 SSH 密钥将包含以下内容：

| 字段   | 描述                                                                    |
| ---- | --------------------------------------------------------------------- |
| 密钥名称 | 您的 SSH 密钥的名称                                                          |
| 私钥   | 私钥是敏感数据，服务器将使用它来帮助建立安全连接。私钥数据应谨慎处理并保持安全。用户可以使用 Bitwarden 生成一个安全且唯一的私钥 |
| 公钥   | 与您要连接的服务器共享的密钥的一部分                                                    |
| 指纹   | 从公钥生成的短唯一字符串，用于识别。例如，可以使用指纹验证 SSH 签名的 Git 提交                          |

存储在 Bitwarden 密码管理器中的 SSH 密钥可以使用 Bitwarden 的功能，例如文件夹、收藏、主密码重新提示、笔记、克隆项目、附件和自定义字段。

## 创建新的 SSH 密钥 <a href="#create-new-ssh-key" id="create-new-ssh-key"></a>

您可以通过 Bitwarden 桌面 App、网页 App或浏览器扩展创建新的 SSH 密钥。创建后，存储在 Bitwarden 中的 SSH 密钥可以通过桌面 App、网页 App、浏览器扩展和移动 App 访问。

1、点击**新建**按钮并选择 **SSH 密钥**作为项目类型。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7wKQygR79OFJP1Nk1c3V3D/8b4f5620b35ad79951b55a3153843753/edit.png?_a=DAJAUVWIZAA0" %}

{% hint style="info" %}
目前，Bitwarden 只能生成 `ED25519` 类型的 SSH 密钥。
{% endhint %}

2、填写诸如**名称**等其余详细信息，完成后选择 **💾保存**图标。

### 编辑现有密钥 <a href="#edit-existing-keys" id="edit-existing-keys"></a>

## 将密钥导入 Bitwarden <a href="#import-key-to-bitwarden" id="import-key-to-bitwarden"></a>

## 配置 Bitwarden SSH 代理 <a href="#configure-bitwarden-ssh-agent" id="configure-bitwarden-ssh-agent"></a>

## 启用 SSH 代理 <a href="#enable-ssh-agent" id="enable-ssh-agent"></a>

## 测试 SSH 密钥 <a href="#testing-ssh-keys" id="testing-ssh-keys"></a>

### 使用 SSH 密钥验证 Git <a href="#use-ssh-key-to-authenticate-with-git" id="use-ssh-key-to-authenticate-with-git"></a>

## 使用 Git 仓库验证 <a href="#authenticate-with-git-repositories" id="authenticate-with-git-repositories"></a>

### 为 SSH 签名配置 Git <a href="#configure-git-for-ssh-signing" id="configure-git-for-ssh-signing"></a>

#### 设置全局变量 <a href="#set-global-variables" id="set-global-variables"></a>

### 签署 Git 提交 <a href="#sign-git-commits" id="sign-git-commits"></a>


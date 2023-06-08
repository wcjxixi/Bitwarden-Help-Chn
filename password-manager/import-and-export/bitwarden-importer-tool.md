# Bitwarden 导入器工具

{% hint style="success" %}
描述对应的[官方文档地址](https://bitwarden.com/help/bitwarden-importer-tool/)
{% endhint %}

Bitwarden 导入器工具可以轻松地将您的密码和其他信息从其他服务转移到 Bitwarden。Bitwarden 导入器工具兼容：

* LastPass

{% hint style="info" %}
Bitwarden 导入器会将信息导入您的个人密码库。导入信息后，您可以将项目手动移动组织中用于共享。
{% endhint %}

## 下载 <a href="#download" id="download"></a>

首先，您可以从 [Github ](https://github.com/bitwarden/importer/releases)下载 Bitwarden 导入器工具。为您的系统选择最佳安装选项：

{% tabs %}
{% tab title="Windows" %}
为安装向导选择 `.msix` 选项。
{% endtab %}

{% tab title="macOS" %}
* 为安装向导选择 `.pkg` 选项。
* 仅为应用程序选择 `.zip` 选项。

{% hint style="info" %}
根据您的安全设置，MacOS 用户可能会收到阻止下载的警告。有关其他安全设置信息，请参阅 [Apple 文档](https://support.apple.com/guide/mac-help/open-a-mac-app-from-an-unidentified-developer-mh40616/mac)。
{% endhint %}
{% endtab %}
{% endtabs %}

## 设置 <a href="#setup" id="setup"></a>

安装后，打开 Bitwarden 导入器工具，查看一个窗口，你将在上面设置一些配置选项。有两种验证选项：

1. **使用您的电子邮件和主密码**：此选项适用于使用验证器应用程序、YubiKey 或电子邮件进行[两步登录](../../two-step-login/two-step-login-methods.md)的账户，或不使用两步登录的账户。
2. **使用您的 API 密钥**：无论您为账户使用哪种两步登录选项，此选项都有效。

| 字段                                                                               | 描述                                                                                                                                                                                    |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bitwarden Server URL                                                             | <p>这是您的 Bitwarden 实例的服务器 URL。</p><p>默认情况下，此值为 <code>https://bitwarden.com</code>。自托管用户将输入他们的自托管 URL。</p>                                                                              |
| Bitwarden Email                                                                  | <p>你用来登录 Bitwarden 的电子邮件地址。</p><p>如果你选择使用 API 密钥登录，则不需要。</p>                                                                                                                          |
| Bitwarden Master Password                                                        | 用于登录 Bitwarden 的[主密码](../../your-vault/your-master-password.md)。                                                                                                                      |
| Log in using API key instead                                                     | 使用您的个人 API 密钥登录，而不是使用 Bitwarden 电子邮件和主密码。                                                                                                                                             |
| Bitwarden API Key `client_id`                                                    | <p>您的密码库的个人 API 密钥的 <code>client_id</code>。该值位于<a href="https://vault.bitwarden.com/#/settings/security/security-keys">此处</a>。</p><p>除非选择<strong>使用 API 密钥登录</strong>，否则不会出现。</p>     |
| Bitwarden API Key `client_secret`                                                | <p>您的密码库的个人 API 密钥的 <code>client_secret</code>。此值位于<a href="https://vault.bitwarden.com/#/settings/security/security-keys">此处</a>。</p><p>除非选择<strong>使用 API 密钥登录</strong>，否则不会出现。</p> |
| My organization uses a SSO configuration that does not require a master password | 如果你是一个使用[客户管理加密的 SSO (Key Connector)](../../login-with-sso/about-key-connector.md) 组织的成员，请选择此选项。                                                                                      |
| Import from Service                                                              | 选择您要从中导入数据的服务。目前，仅支持 LastPass。                                                                                                                                                        |
| Service Email                                                                    | 输入您要从中导入数据的账户的登录电子邮件。                                                                                                                                                                 |
| Service Master Password                                                          | 输入您要从中导入数据的账户的登录主密码。                                                                                                                                                                  |
| Skip items from shared folders                                                   | 选择此选项可防止导入属于共享文件夹的数据。                                                                                                                                                                 |

为所有字段提供数据并准备好导入后，选择窗口底部的**导入**。

## 疑难解答 <a href="#troubleshooting" id="troubleshooting"></a>

如果导入不成功，请检查以下内容：

* 您的 Bitwarden 电子邮件和主密码或 API 密钥已输入且正确无误。
* 其他服务的电子邮件地址和主密码已输入且正确无误。
* 您使用的验证方法与您账户的两步登录方法兼容。
  * **使用您的电子邮件和主密码**：此选项适用于使用验证器应用程序、YubiKey 或电子邮件进行[两步登录](../../two-step-login/two-step-login-methods.md)的账户，或不使用两步登录的账户。
  * **使用您的 API 密钥**：无论您为账户使用哪种两步登录选项，此选项都有效。
* 检查您的电子邮件，您的服务提供商可能已经发送了一封关于需要批准的登录尝试的电子邮件。

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 有关手动导入数据的信息，请参阅[导入数据您的密码库](../../import-export/import-data-to-your-vault.md)或[导入数据到组织](../../import-export/import-data-to-an-organization.md)。
* 有关管理组织的信息，请参阅[组织](../../organizations/organizations.md)。

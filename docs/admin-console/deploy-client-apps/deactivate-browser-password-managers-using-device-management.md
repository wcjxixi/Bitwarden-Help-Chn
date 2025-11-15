# 使用设备管理停用浏览器密码管理器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/deactivate-browser-password-managers/)
{% endhint %}

本文将指导您如何使用组策略禁用各种网页浏览器的内置密码管理器。这些步骤将有助于防止公司登录信息被保存并同步到个人账户。您还可以考虑[将 Bitwarden 浏览器扩展部署到所有浏览器](deploy-browser-extensions/browserext-deploy.md)，以作为同一策略的一部分。

## 使用 Windows GPO 禁用 <a href="#disable-with-windows-gpo" id="disable-with-windows-gpo"></a>

{% tabs %}
{% tab title="Edge" %}
1、在您的托管 Windows 服务器上打开组策略管理编辑器。

2、[下载相应的 Edge 策略模板](https://www.microsoft.com/zh-cn/edge/business/download?form=MA13FJ)。

3、在组策略编辑器中，为 Edge 创建一个新的 GPO 并提供一个适当的名称。

4、选择所需的范围。

5、右键单击新的**组策略对象** → **编辑**。

6、在组策略管理编辑器上，转到**用户配置** → **策略** → **管理模板** → **Microsoft Edge**。

7、设置以下设置：

* 打开「」密码管理器和保护」，禁用**启用将密码保存到密码管理器**策略 。
* 禁用**启用地址自动填充**策略。
* 禁用**启用支付工具自动填充**策略。
* （可选）启用**禁用使用 Microsoft 同步服务同步数据**策略。

8、完成后，GPO **设置**应显示如下：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7JYNg4j0ETWUYqxvC1aA35/b2330512b7ccfd0c2371d14349f6f91d/image.png?_a=DAJCwlWIZAAB" %}
Edge 设置
{% endembed %}

9、确保 GPO 链接已启用。
{% endtab %}

{% tab title="Chrome" %}
1、在您的托管 Windows 服务器上打开组策略管理编辑器。

2、[下载相应的 Chrome 策略模板](https://support.google.com/chrome/a/answer/187202?hl)。

3、将 **ADMX** 文件 `policy_templates\windows\admx\chrome.admx` 和 `policy_templates\windows\admx\google.admx` 复制到 `C:\Windows\PolicyDefinitions`

4、将 **ADML** 文件 `policy_templates\windows\admx\en-us\chrome.adml` 和 `policy_templates\windows\admx\en-us\google.adml` 复制到 `C:\Windows\PolicyDefinitions\en-us`

5、在组策略编辑器中，为 Chrome 创建一个新的 GPO 并提供一个适当的名称。

6、选择所需的范围。

7、右键单击新的**组策略对象** → **编辑**。

8、在组策略管理编辑器上，转到**用户配置** → **策略** → **管理模板** → **Google** → **Google Chrome**。

9、设置以下设置：

* 在「密码管理器」下，禁用**启用将密码保存到密码管理器**策略 。
* 禁用**启用地址自动填充**策略。
* 禁用**启用信用卡自动填充**策略。

10、完成后，GPO **设置**应显示如下：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4g4UFkO53OhzFhZlnSPoKY/000e4a638d423783c6e1c94c10b13395/chrome_gpo.png?_a=DAJCwlWIZAAB" %}
Chrome 设置
{% endembed %}

11、确保 GPO 链接已启用。
{% endtab %}

{% tab title="Firefox" %}
1、在您的托管 Windows 服务器上打开组策略管理编辑器。

2、[下载最新的 Firefox 策略模板 .zip 文件](https://github.com/mozilla/policy-templates/releases)。

3、将 **ADMX** 文件 `policy_templates_v#.##\windows\firefox.admx` 和 `policy_templates_v#.##\windows\mozilla.admx` 复制到 `C:\Windows\PolicyDefinitions`

4、将 **ADML** 文件 `policy_templates_v#.##\windows\en-us\firefox.adml` 和 `policy_templates_v#.##\windows\en-us\mozilla.adml` 复制到 `C:\Windows\PolicyDefinitions\en-us`

5、在组策略编辑器中，为 Firefox 创建一个新的 GPO 并提供一个适当的名称。

6、选择所需的范围。

7、右键单击新的**组策略对象** → **编辑**。

8、在组策略管理编辑器上，转到**用户配置** → **策略** → **管理模板** → **Mozilla** → **Firefox**。

9、找到并编辑以下策略：

* 禁用**禁用 Firefox 账户**策略。
* 禁用**提供保存登录信息**策略。
* 禁用**提供保存登录信息（默认）**&#x7B56;略。
* 禁用**密码管理器**策略。

10、完成后，GPO **设置**应显示如下：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/75Do1uQgOThyyIfdXU3ti7/6f27e19aaf0917d779fe6e1035339d05/FireFox_Settings.png?_a=DAJCwlWIZAAB" %}
Firefox 设置
{% endembed %}

11、确保 GPO 链接已启用。
{% endtab %}
{% endtabs %}

### 如何检查是否生效？ <a href="#how-to-check-if-it-worked" id="how-to-check-if-it-worked"></a>

检查前面的步骤是否适用于您的设置：

{% tabs %}
{% tab title="Edge" %}
1、在用户计算机上，打开命令行并运行 `gpupdate /force`。

2、打开 Edge，然后单击三个点 **...** → **设置** → **密码**。

3、确保「提供保存密码」已关闭并由组织管理。

{% hint style="info" %}
自动登录仍会被选中，因为没有策略设置可将其关闭。

之前在 Edge 中保存的任何登录信息都不会被删除，尽管自动填充功能已禁用，但仍会继续显示给用户。在从 Edge 中删除任何已保存的登录信息之前，请务必指示用户[将任何已保存的登录信息导入 Bitwarden](../../password-manager/import-and-export/import-guides/import-data-from-chrome.md)。
{% endhint %}
{% endtab %}

{% tab title="Chrome" %}
1、在用户计算机上，打开命令行并运行 `gpupdate /force`。

2、打开 Chrome 浏览器，然后点击右上角的**个人资料图标**。确保用户未登录。

3、打开 Chrome 浏览器，然后点击三个点 **...** → **设置** → **密码**。确保「提供保存密码」已关闭并由组织管理。
{% endtab %}

{% tab title="Firefox" %}
1、在用户计算机上，打开命令行并运行 `gpupdate /force`。

2、打开 Firefox，然后从菜单栏中选择**登录和密码**。&#x20;

3、确保「已阻止页面」消息已显示。
{% endtab %}
{% endtabs %}

## 在 Linux 上禁用 <a href="#disable-on-linux" id="disable-on-linux"></a>

{% tabs %}
{% tab title="Chrome" %}
要通过组策略禁用 Chrome 密码管理器：

1、下载适用于 Linux 的 [Google Chrome .deb 或 .rpm](https://www.google.com/chrome/?platform=linux)。

2、下载 [Chrome 企业捆绑包](https://chromeenterprise.google/intl/zh_cn/download)。

3、解压缩企业捆绑包（`GoogleChromeEnterpriseBundle64.zip` 或 `GoogleChromeEnterpriseBundle32.zip`）并打开 `/Configuration` 文件夹。

4、创建 `master_preferences.json`（在 Chrome 91+ 中为 `initial_preferences.json`）的副本并将其重命名为 `managed_preferences.json`。

5、要禁用 Chrome 内置的密码管理器，请在 `managed_preferences.json` 的 `"policies": { }` 中添加以下内容：

```
{
  "PasswordManagerEnabled": false
}
```

6、如果以下目录还不存在，请创建：

```bash
mkdir /etc/opt/chrome/policies
mkdir /etc/opt/chrome/policies/managed
```

7、将 `managed_preferences.json` 移动到 `/etc/opt/chrome/policies/managed` 中。

8、由于需要将这些文件部署到用户的机器上，我们建议确保只有管理员才能在 `/managed` 目录中写入文件。

```bash
chmod -R 755 /etc/opt/chrome/policies
```

9、此外，我们建议管理员在文件中添加以下内容，以防止对文件本身进行修改：

```bash
chmod 644 /etc/opt/chrome/policies/managed/managed_preferences.json
```

10、使用您首选的软件发布或 MDM 工具，将以下内容部署到用户的计算机上：

* 谷歌浏览器
* `/etc/opt/chrome/policies/managed/managed_preferences.json`

{% hint style="success" %}
如需更多帮助，请参阅 Google 的 [Chrome 浏览器快速入门 (Linux)](https://support.google.com/chrome/a/answer/9025903?hl=en\&ref_topic=9025817\&sjid=18069515108639844992-NC) 指南。
{% endhint %}
{% endtab %}

{% tab title="Firefox" %}
要通过组策略禁用 Firefox 密码管理器：

1、下载适用于 Linux 的 [Firefox](https://www.mozilla.org/zh-CN/firefox/linux/)。

2、打开终端，然后导航至下载文件保存的目录。例如 `cd ~/Downloads`

3\. 提取下载文件的内容：

```bash
tar xjf firefox-*.tar.bz2
```

以下命令必须以 root 用户身份执行，或在命令前面加上 `sudo`。

4、将未压缩的 Firefox 文件夹移动到 `/opt`：

```bash
mv firefox /opt
```

5、创建一个指向 Firefox 可执行文件的符号链接：

```bash
ln -s /opt/firefox /usr/local/bin/firefox
```

6、下载桌面文件副本：

```bash
wget https://raw.githubusercontent.com/mozilla/sumo-kb/main/install-firefox-linux/firefox.desktop -P /usr/local/share/applications
```

7、要禁用 Firefox 内置的密码管理器，请将以下内容添加到 `policies.json` 的 `"policies": {}` 中：

```
{
 "PasswordManagerEnabled": false
}
```

8、如果以下目录还不存在，请创建：

```bash
mkdir /opt/firefox/distribution
```

9、使用以下命令修改目录：

```bash
chmod 755 /opt/firefox/distribution
```

10、此外，我们建议管理员在文件中添加以下内容，以防止对文件本身进行修改：

```bash
chmod 644 /opt/firefox/distribution/policies.json
```

11、使用您首选的软件分发或 MDM 工具，将以下内容部署到用户的计算机上：

* Firefox 浏览器
* `/distribution/policies.json`

{% hint style="success" %}
如需更多帮助，请参阅 Firefox 的 [policies.json 概述](https://support.mozilla.org/zh-CN/kb/%E5%9C%A8%20macOS%20%E4%B8%8A%E4%BD%BF%E7%94%A8%E9%85%8D%E7%BD%AE%E6%8F%8F%E8%BF%B0%E6%96%87%E4%BB%B6%E5%AE%9A%E5%88%B6%20Firefox)或 Github 上的 [Policies README](https://github.com/mozilla/policy-templates/blob/master/README.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

## 在 macOS 上禁用 <a href="#disable-on-macos" id="disable-on-macos"></a>

{% tabs %}
{% tab title="Chrome" %}
1、下载适用于 macOS 的 [Google Chrome .dmg 或 .pkg](https://chromeenterprise.google/intl/zh_cn/download/#mac-tab)。

2、下载 Chrome 企业版捆绑包。

3、解压缩企业版捆绑包（`GoogleChromeEnterpriseBundle64.zip` 或 `GoogleChromeEnterpriseBundle32.zip`）。

4、使用任何文本编辑器打开 `/Configuration/com.Google.Chrome.plist` 文件。

5、要禁用 Chrome 的内置密码管理器，请在 `com.Google.Chrome.plist` 中添加以下内容：

```
<key>PasswordManagerEnabled</key>
<false />
```

6、使用您选择的转换工具将 `com.Google.Chrome.plist` 文件转换为配置文件。

7、使用软件分发或 MDM 工具将 Chrome `.dmg` 或 `.pkg` 和配置文件部署到所有受管计算机。

{% hint style="success" %}
如需更多帮助，请参阅 Google 的 [Chrome 浏览器快速入门 (Mac)](https://support.google.com/chrome/a/answer/7550274?hl=zh-Hans\&sjid=18069515108639844992-NC) 指南。

有关其他信息，请参阅 Chrome 文档：[在 Mac 上设置 Chrome 浏览器](https://support.google.com/chrome/a/answer/7550274?hl=zh-Hans)。
{% endhint %}
{% endtab %}

{% tab title="Firefox" %}
1、下载并安装适用于 MacOS 的[企业版 Firefox](https://www.mozilla.org/zh-CN/firefox/enterprise/#download)。

2、在 `Firefox.app/Contents/Resources/` 中创建一个 `distribution` 目录。

3、在创建的 `/distribution` 目录中，创建一个新文件 `org.mozilla.firefox.plist`。

{% hint style="info" %}
使用 [Firefox .plist 模板](https://github.com/mozilla/policy-templates/blob/master/mac/org.mozilla.firefox.plist)和[策略 README](https://github.com/mozilla/policy-templates/blob/master/README.md) 作为参考。
{% endhint %}

4、要[禁用](https://github.com/mozilla/policy-templates/blob/master/README.md#passwordmanagerenabled) Firefox 内置密码管理器，请在 `org.mozilla.firefox.plist` 中添加以下内容：

```
<dict>
  <key>PasswordManagerEnabled</key>
  <false/>
</dict>
```

5、使用您选择的转换工具将 `org.mozilla.firefox.plist` 文件转换为配置文件。

6、使用软件分发或 MDM 工具将 Firefox `.dmg` 和配置文件部署到所有受管计算机。

{% hint style="success" %}
有关其他信息，请参阅 Firefox 文档：[在 macOS 上使用配置描述文件定制 Firefox](https://support.mozilla.org/zh-CN/kb/%E5%9C%A8%20macOS%20%E4%B8%8A%E4%BD%BF%E7%94%A8%E9%85%8D%E7%BD%AE%E6%8F%8F%E8%BF%B0%E6%96%87%E4%BB%B6%E5%AE%9A%E5%88%B6%20Firefox)。
{% endhint %}
{% endtab %}

{% tab title="Edge" %}
1、下载适用于 macOS 的 [Microsoft Edge .pkg](https://www.microsoft.com/zh-cn/edge/) 文件。

2、在终端中，使用以下命令为 Microsoft Edge 创建 `.plist` 文件：

```bash
/usr/bin/defaults write ~/Desktop/com.microsoft.Edge.plist RestoreOnStartup -int 1
```

3、使用以下命令将 `.plist` 从二进制转换为纯文本：

```bash
/usr/bin/plutil -convert xml1 ~/Desktop/com.microsoft.Edge.plist
```

4、要[禁用](https://learn.microsoft.com/zh-cn/deployedge/microsoft-edge-policies#passwordmanagerenabled) Edge 的内置密码管理器，请在 `com.microsoft.Edge.plist` 中添加以下内容：

```
<key>PasswordManagerEnabled</key>
<false/>
```

5、使用软件分发或 MDM 工具将 Edge `.pkg` 和配置文件部署到所有受管计算机。

{% hint style="success" %}
有关特定于 Jamf 的帮助，请参阅 Microsoft 文档：[使用 Jamf 在 macOS 上配置 Microsoft Edge 策略设置](https://learn.microsoft.com/zh-cn/deployedge/configure-microsoft-edge-on-mac-jamf)。

有关其他信息，请参阅 Microsoft 文档：[在 macOS 上配置 Microsoft Edge 策略](https://learn.microsoft.com/zh-cn/deployedge/configure-microsoft-edge-on-mac#configure-microsoft-edge-policies-on-macos)。
{% endhint %}
{% endtab %}
{% endtabs %}

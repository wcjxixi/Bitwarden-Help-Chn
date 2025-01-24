# =使用 GPO、Linux 策略和 .plist 文件部署浏览器扩展

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/browserext-deploy/)
{% endhint %}

在商业环境中操作 Bitwarden 时，管理员可能希望使用端点管理平台或组策略自动向用户部署 Bitwarden 浏览器扩展。

对于每种操作系统和浏览器，操作过程会有所不同：

## Windows

要将 Bitwarden 浏览器扩展部署到 Windows 上的浏览​​器，通常需要使用 Windows 组策略将 ADMX 策略模板作为目标托管计算机。每种浏览器的过程略有不同：

{% tabs %}
{% tab title="Chrome" %}
要在 Windows Google Chrome 上部署浏览器扩展：

1、下载并解压适用于 Windows 的 [Chrome Enterprise Bundle](https://chromeenterprise.google/browser/download/#windows-tab)。

2、从已解压缩的目录：

* 将 `\Configuration\admx\chrome.admx` 复制到 `C:\Windows\PolicyDefinitions`
* 将 `\Configuration\admx\en-US\chrome.adml` 复制到 `C:\Windows\PolicyDefinitions\en-US`

3、打开 Windows 组策略管理器并为 Bitwarden 浏览器扩展安装创建一个新的 GPO。

4、右键单击新 GPO 并选择**编辑...**，然后继续导航到**计算机配置** → **策略** → **管理模板** → **Google Chrome** → **扩展程序**。

5、在右侧的设置区域中，选择**配置强制安装的应用程序和扩展程序列表**。在对话框中，切换为**启用**选项。

6、选择**显示...** 按钮并添加以下内容：

```
nngceckbapebfimnlniiiahkandclblb;https://clients2.google.com/service/update2/crx
```

点击**确认**。

7、还是在 **…管理模板** → **Google Chrome** 中，从文件树中选择**密码管理器**。

8、在右侧的设置区域中，右键单击**启用将密码保存到密码管理器**并选择**编辑**。在对话框中，切换为**禁用**选项然后选择**确定**。

9、重复**步骤 8** 以**启用地址自动填充**和**启用信用卡自动填充**选项，这些选项位于 **…管理模板** → **Google Chrome** 的设置区域中。

10、将新配置的 GPO 应用到所需的范围。
{% endtab %}

{% tab title="Firefox" %}
要在 Windows Firefox 上部署浏览器扩展：

1、下载并解压 [Firefox ADMX 模板](https://github.com/mozilla/policy-templates/releases)文件。

2、从已解压缩的目录：

* 将 `\policy_templates_\windows\firefox.admx` 复制到 `C:\Windows\PolicyDefinitions`
* 将 `\policy_templates_<version>\windows\en-US\firefox.adml` 复制到 `C:\Windows\PolicyDefinitions\en-US`

3、打开 Windows 组策略管理器并为 Bitwarden 浏览器扩展安装创建一个新的 GPO。

4、右键单击新 GPO 并选择**编辑...**，然后继续导航到**计算机配置** → **策略** → **管理模板** → **Firefox** → **扩展程序**。

5、在右侧的设置区域中，选择要安装的扩展。在对话框中，切换为**启用**选项。

6、选择**显示..** 按钮并添加以下内容：

```
https://addons.mozilla.org/firefox/downloads/latest/bitwarden-password-manager/latest.xpi
```

点击**确定**。

7、返回文件树，选择 **Firefox**。在右侧的设置区域中，**编辑...**&#x5E76;禁用**提供保存登录信息**和**提供保存登录信息（默认）**&#x9009;项。

8、将新配置的 GPO 应用到所需的范围。
{% endtab %}

{% tab title="Edge" %}
在 Windows Edge 上部署浏览器扩展：

1、下载并解压缩 [Microsoft Edge 策略](https://www.microsoft.com/en-us/edge/business/download)文件。

2、从已解压缩的目录：

* 将 `\windows\admx\msedge.admx` 复制到 `C:\Windows\PolicyDefinitions`
* 将 `\windows\admx\en-US\msedge.adml` 复制到 `C:\Windows\PolicyDefinitions\en-US`

3、打开 Windows 组策略管理器并为 Bitwarden 浏览器扩展安装创建一个新的 GPO。

4、右键单击新 GPO 并选择**编辑...**，然后继续导航到**计算机配置** → **策略** → **管理模板** → **Microsoft Edge** → **扩展程序**。

5、在右侧的设置区域中，选择**控制静默安装的扩展程序**。在对话框中，切换为**启用**选项。

6、选择**显示..** 按钮并添加以下内容：

```
jbkfoedolllekgbhcbcoahefnbanhhlh;https://edge.microsoft.com/extensionwebstorebase/v1/crx
```

点击**确定**。

7、还是在 **...管理模板** → **Microsoft Edge**，从文件树中选择**密码管理器和保护**。

8、在右侧的设置区域中，右键单击**启用将密码保存到密码管理器**并选择**编辑**。在对话框中，切换为**禁用**选项然后选择**确定**。

9、重复**步骤 8** 以**启用地址自动填充**和**启用信用卡自动填充**选项，这些选项位于 **…管理模板** → **Microsoft Edge** 的设置区域中。

10、将新配置的 GPO 应用到所需的范围。
{% endtab %}
{% endtabs %}

## Linux

要将 Bitwarden 浏览器扩展部署到 Linux 上的浏览​​器，通常涉及使用 `.json` 文件来设置配置属性。每种浏览器的过程略有不同：

{% tabs %}
{% tab title="Chrome" %}
要在 Linux Google Chrome 上部署浏览器扩展：

1、下载适用于 Linux 的 [Google Chrome .deb 或 .rpm](https://www.google.com/chrome/?platform=linux)。

2、下载 [Chrome Enterprise Bundle](https://chromeenterprise.google/browser/download/#windows-tab)。

3、解压缩 Enterprise Bundle（`GoogleChromeEnterpriseBundle64.zip` 或 `GoogleChromeEnterpriseBundle32.zip`）并打开 `/Configuration` 文件夹。

4、创建 `master_preferences.json`（在 Chrome 91+ 中为 `initial_preferences.json`）副本并将其重命名为 `managed_preferences.json`。

5、将以下内容添加到 `managed_preferences.json`：

```yaml
{
  "policies:" {
  "ExtensionSettings": {
    "nngceckbapebfimnlniiiahkandclblb": {
      "installation_mode": "force_installed",
      "update_url":
         "https://clients2.google.com/service/update2/crx"
      }
    }
  }
}
```

在这个 JSON 对象中，`"nngceckbapebfimnlniiiahkandclblb"` 是 Bitwarden 浏览器扩展的应用程序标识符。类似地，`"https://clients2.google.com/service/update2/crx"` 示意 Chrome 让其使用 Chrome 网上应用商店检索已识别的应用程序。

{% hint style="info" %}
您也可以使用 [ExtensionInstallForcelist](https://chromeenterprise.google/policies/?policy=ExtensionInstallForcelist) 策略来配置强制性安装，但是 [ExtensionSettings](https://support.google.com/chrome/a/answer/7517525#getID\&zippy=%2Cset-custom-message-for-blocked-apps-and-extensions%2Cprevent-apps-and-extensions-from-altering-webpages) 方法将取代 ExtensionInstallForceList。
{% endhint %}

6、（**推荐**）要[禁用](https://chromeenterprise.google/policies/#PasswordManagerEnabled) Chrome 的内置密码管理器，请将以下内容添加到 `managed_preferences.json` 的 `"policies": { }` 内部：

```yaml
{
 "PasswordManagerEnabled": false
}
```

7、如果以下目录尚不存在，则创建以下目录：

```shell
mkdir /etc/opt/chrome/policies
mkdir /etc/opt/chrome/policies/managed
```

8、将 `managed_preferences.json` 移动到 `/etc/opt/chrome/policies/managed`。

9、由于您需要将这些文件部署到用户的机器上，我们建议确保只有管理员可以在 /managed 目录中写入文件：

```
// Some codechmod -w /etc/opt/chrome/policies/managed
```

10、使用您首选的软件分发或 MDM 工具，将以下内容部署到用户的机器上：

* Google Chrome 浏览器
* `/etc/opt/chrome/policies/managed/managed_preferences.json`

{% hint style="success" %}
如需更多帮助，请参阅 Google 的 [Chrome 浏览器快速入门 (Linux)](https://support.google.com/chrome/a/answer/9025926?hl=zh-Hans\&ref_topic=9025817) 指南。
{% endhint %}
{% endtab %}

{% tab title="Firefox" %}
要在 Linux Firefox 上部署浏览器扩展：

1、下载适用于 Linux 的 [Firefox](https://www.mozilla.org/en-US/firefox/all/#product-desktop-release)。

2、在 Firefox 安装目录中创建一个 `distribution` 目录。

3、在 `distrubition` 目录中，创建一个 `policies.json` 文件。

4、将以下内容添加到 `policies.json`：

```yaml
{
"policies": {
 "ExtensionSettings": {
   "446900e4-71c2-419f-a6a7-df9c091e268b": {
     "installation_mode": "force_installed",
     "install_url": "https://addons.mozilla.org/firefox/downloads/latest/bitwarden-password-manager/latest.xpi"
      }
    }
  }
}
```

在这个 JSON 对象中，`"446900e4-71c2-419f-a6a7-df9c091e268b"` 是 Bitwarden 浏览器扩展的扩展 ID。类似地，`"https://addons.mozilla.org/firefox/downloads/latest/bitwarden-password-manager/latest.xpi"` 示意 Firefox 让其使用扩展商店来检索扩展。

5、（**推荐**）要[禁用](https://github.com/mozilla/policy-templates/blob/master/README.md#passwordmanagerenabled) Firefox 的内置密码管理器，请将以下内容添加到 `managed_preferences.json` 的 `"policies": { }` 内部：

```yaml
{
 "PasswordManagerEnabled": false
}
```

6、使用您首选的软件分发或 MDM 工具，将以下内容部署到用户的机器上：

* Firefox 浏览器
* `/distribution/policies.json`

{% hint style="success" %}
如需更多帮助，请参阅 Firefox 的 [policies.json 概述](https://support.mozilla.org/en-US/kb/customizing-firefox-macos-using-configuration-prof)或 Github 上的[策略自述文件](https://github.com/mozilla/policy-templates/blob/master/README.md)。
{% endhint %}
{% endtab %}
{% endtabs %}

## macOS

要将 Bitwarden 浏览器扩展部署到 macOS 上的浏览​​器，通常涉及使用属性列表（`.plist`）文件。每种浏览器的过程略有不同：

{% tabs %}
{% tab title="Chrome" %}
要在 macOS Google Chrome 上部署浏览器扩展：

1、下载适用于 macOS 的 [Google Chrome .dmg 或 .pkg](https://chromeenterprise.google/browser/download/#mac-tab)。

2、下载 [Chrome Enterprise Bundle](https://chromeenterprise.google/browser/download/#windows-tab)。

3、解压缩 Enterprise Bundle（`GoogleChromeEnterpriseBundle64.zip` 或 `GoogleChromeEnterpriseBundle32.zip`）。

4、使用任何文本编辑器打开 `/Configuration/com.Google.Chrome.plist` 文件。

5、将以下内容添加到 `.plist` 文件中：

```yaml
<key>ExtensionSettings</key>
<dict>
  <key>nngceckbapebfimnlniiiahkandclblb</key>
  <dict>
    <key>installation_mode</key>
    <string>force_installed</string>
    <key>update_url</key>
    <string>https://clients2.google.com/service/update2/crx</string>
  </dict>
 </dict>
```

在此代码块中，`nngceckbapebfimnlniiiahkandclblb` 是 Bitwarden 浏览器扩展的应用程序标识符。类似地，`https://clients2.google.com/service/update2/crx` 示意 Chrome 让其使用 Chrome 网上应用商店检索已识别的应用程序。



{% hint style="info" %}
您也可以使用 [ExtensionInstallForcelist](https://chromeenterprise.google/policies/?policy=ExtensionInstallForcelist) 策略来配置强制性安装，但是 [ExtensionSettings](https://support.google.com/chrome/a/answer/7517525#getID\&zippy=%2Cset-custom-message-for-blocked-apps-and-extensions%2Cprevent-apps-and-extensions-from-altering-webpages) 方法将取代 ExtensionInstallForceList。
{% endhint %}

6、（**推荐**）要[禁用](https://chromeenterprise.google/policies/#PasswordManagerEnabled) Chrome 的内置密码管理器，请将以下内容添加到 `com.Google.Chrome.plist`：

```yaml
<key>PasswordManagerEnabled</key>
<false />
```

7、使用 [mcxToProfile](https://github.com/timsutton/mcxToProfile) 等转换工具将 `com.Google.Chrome.plist` 文件转换为配置文件。

8、使用您的软件分发或 MDM 工具将 Chrome `.dmg` 或 `.pkg` 和配置文件部署到所有托管计算机。

{% hint style="success" %}
如需更多帮助，请参阅 Google 的ya [Chrome 浏览器快速入门 (Mac)](https://support.google.com/chrome/a/answer/9020580?hl=zh-Hans\&ref_topic=7650028) 指南。
{% endhint %}
{% endtab %}

{% tab title="Firefox" %}
要在 macOS Firefox 上部署浏览器扩展：

1、下载并安装适用于 macOS 的[企业版 Firefox](https://www.mozilla.org/en-US/firefox/enterprise/#download)。

2、在 `Firefox.app/Contents/Resources/` 中创建一个 `distribution` 目录。

3、在已创建的 `/distribution` 目录中，创建一个新的 `org.mozilla.firefox.plist` 文件。

{% hint style="success" %}
使用 [Firefox .plist 模板](https://github.com/mozilla/policy-templates/blob/master/mac/org.mozilla.firefox.plist)和[策略自述文件](https://github.com/mozilla/policy-templates/blob/master/README.md)作为参考。
{% endhint %}

4、将以下内容添加到 `org.mozilla.firefox.plist`：

```yaml
<key>ExtensionSettings</key>
<dict>
   <key>446900e4-71c2-419f-a6a7-df9c091e268b</key>
   <dict>
     <key>installation_mode</key>
     <string>force_installed</string>
     <key>update_url</key>
     <string>https://addons.mozilla.org/firefox/downloads/latest/bitwarden-password-manager/latest.xpi</string>
   </dict>
 </dict>
```

在此代码块中，`446900e4-71c2-419f-a6a7-df9c091e268b` 是 Bitwarden 浏览器扩展的扩展 ID。同样，`https://addons.mozilla.org/firefox/downloads/latest/bitwarden-password-manager/latest.xpi` 示意 Firefox 让其使用扩展商店来检索应用程序。

5、（**推荐**）要[禁用](https://github.com/mozilla/policy-templates/blob/master/README.md#passwordmanagerenabled) Firefox 的内置密码管理器，请将以下内容添加到 `org.mozilla.firefox.plist`：

```yaml
<dict>
  <key>PasswordManagerEnabled</key>
  <false/>
</dict>
```

6、使用 [mcxToProfile](https://github.com/timsutton/mcxToProfile) 等转换工具将 `org.mozilla.firefox.plist` 文件转换为配置文件。

7、使用您的软件分发或 MDM 工具将 Firefox `.dmg` 和配置文件部署到所有托管计算机。
{% endtab %}

{% tab title="Edge" %}
要在 macOS Edge 上部署浏览器扩展：

1、下载适用于 macOS 的 [Microsoft Edge .pkg](https://www.microsoft.com/en-us/edge) 文件。

2、在终端中，使用以下命令为 Microsoft Edge 创建 `.plist` 文件：

```yaml
/usr/bin/defaults write ~/Desktop/com.microsoft.Edge.plist RestoreOnStartup -int 1
```

3、使用以下命令将 `.plist` 从二进制转换为纯文本：

```yaml
//usr/bin/plutil -convert xml1 ~/Desktop/com.microsoft.Edge.plist
```

4、打开 `com.microsoft.Edge.plist` 并添加以下内容：

```yaml
<key>ExtensionSettings</key>
<dict>
  <key>jbkfoedolllekgbhcbcoahefnbanhhlh</key>
  <dict>
    <key>installation_mode</key>
    <string>force_installed</string>
    <key>update_url</key>
    <string>https://edge.microsoft.com/extensionwebstorebase/v1/crx</string>
  </dict>
</dict>
```

在此代码块中，`jbkfoedolllekgbhcbcoahefnbanhhlh` 是 Bitwarden 浏览器扩展的应用程序标识符。同样，`https://edge.microsoft.com/extensionwebstorebase/v1/crx` 示意 Edge 让其使用 Edge 外接程序商店来检索已识别的应用程序。

{% hint style="info" %}
您也可以使用 [ExtensionInstallForceList](https://docs.microsoft.com/en-us/DeployEdge/microsoft-edge-policies#extensioninstallforcelist) 来配置强制性安装，但是 [ExtensionSettings](https://docs.microsoft.com/en-us/DeployEdge/microsoft-edge-policies#extensionsettings) 方法将取代 ExtensionInstallForceList。
{% endhint %}

5、（**推荐**）要[禁用](https://docs.microsoft.com/en-us/deployedge/microsoft-edge-policies#passwordmanagerenabled) Edge 的内置密码管理器，请将以下内容添加到 `com.microsoft.Edge.plist`：

```yaml
<key>PasswordManagerEnabled</key>
<false/>
```

6、使用 [mcxToProfile](https://github.com/timsutton/mcxToProfile) 等转换工具将 `com.microsoft.Edge.plist` 文件转换为配置文件。

7、使用您的软件分发或 MDM 工具将 Edge `.pkg` 和配置文件部署到所有托管计算机。

{% hint style="success" %}
有关**专用于 Jamf** 的帮助，请参阅 Microsoft 文档：[使用 Jamf 在 macOS 上配置 Microsoft Edge 策略设置](https://docs.microsoft.com/zh-cn/deployedge/configure-microsoft-edge-on-mac-jamf)。
{% endhint %}
{% endtab %}
{% endtabs %}

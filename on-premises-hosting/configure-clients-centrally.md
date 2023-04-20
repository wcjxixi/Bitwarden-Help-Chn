# 集中式配置客户端

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/configure-clients/)
{% endhint %}

在业务环境中操作自托管的 Bitwarden 服务器时，管理员可能希望在使用端点管理平台部署给用户之前，集中配置客户端应用程序设置（特别是服务器 URL）。

对于每一种客户端应用程序，操作过程会有所不同：

## 浏览器扩展 <a href="#browser-extensions" id="browser-extensions"></a>

### Chrome 和 Chromium <a href="#chrome-and-chromium" id="chrome-and-chromium"></a>

{% tabs %}
{% tab title="Linux" %}
要为 Linux 预配置环境 URL：

1、如果您的系统上尚不存在以下目录结构之一，请创建它们：

* 对于 Chrome：`/etc/opt/chrome/policies/managed/`
* 对于 Chromium：`/etc/opt/chromium/policies/managed/`

2、在 `managed` 文件夹中，创建一个包含以下内容的 bitwarden.json 文件：

```
{
  "3rdparty": {
  "extensions": {
  "nngceckbapebfimnlniiiahkandclblb": {
      "environment": {
        "base": "https://my.bitwarden.server.com"
        }
      }
    }
  }
}
```

扩展 ID (`nngceckbapebfimnlniiiahkandclblb`) 将根据您的安装方法而有所不同。您可以通过导航到浏览器的扩展程序菜单（例如 `chrome://extensions`）找到您的扩展程序 ID。

大多数安装只需要 `"base":` URL，但一些特殊设置，可能需要您单独为每一个服务输入 URL：

```
{
  "3rdparty": {
  "extensions": {
  "nngceckbapebfimnlniiiahkandclblb": {
      "environment": {
        "base": "https://my.bitwarden.server.com",
        "webVault": "https://my.bitwarden.server.com",
        "api": "https://my.bitwarden.server.com",
        "identity": "https://my.bitwarden.server.com",
        "icons": "https://my.bitwarden.server.com",
        "notifications": "https://my.bitwarden.server.com",
        "events": "https://my.bitwarden.server.com"
        }
      }
    }
  }
}
```

{% hint style="info" %}
如果您打算使用 Chrome 或 Chromium Web Store 版本的 Bitwarden，则可以在分发托管策略时按照[这些说明](../admin-console/more/deploy-browser-extension-to-managed-devices.md#linux)在终端用户计算机上强制安装 Bitwarden。您可以跳过重叠的步骤，例如创建所需的目录。
{% endhint %}

3、由于您需要将这些文件部署到用户的计算机上，我们建议确保只有管理员可以在 `/policies` 目录中写入文件。

4、使用您首选的软件分发或 MDM 工具，将以下内容部署到用户的计算机：

* Chrome 或基于 Chromium 的浏览器
* `/etc/opt/{chrome or chromium}/policies/managed/bitwarden.json`
{% endtab %}

{% tab title="Windows" %}
要为 Windows 预配置环境 URL：

1、打开 Windows 组策略管理器并创建一个新的组策略对象 (GPO) 或使用适用于终端用户的现有 GPO。

2、编辑 GPO 并导航到用**户配置** -> **首选项** -> **Windows 设置** -> **注册表**。

3、键单击文件树中的**注册表**，然后选择**新建** > **注册表项**。

4、创建具有以下属性的新注册表项：

* **操作**：更新
* **配置单元**：`HKEY_LOCAL_MACHINE`
* **注册表项路径**：`HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Google\Chrome\3rdparty\extensions<extension_id>\policy\environment`\
  `<extension_id>` 将根据您的安装方法而有所不同。您可以通过导航到浏览器的扩展程序菜单（例如 `chrome://extensions`）找到您的扩展程序 ID。
* **值名称**：`base`
* **值类型**：`REG_SZ`
* **数值数据**：您的服务器已配置的域名

5、配置项目后选择**确定**。

大多数安装只需要 `base` URL，但一些特殊设置，可能需要您单独为每一个服务输入 URL。如果您的设置需要这样做，请重复**步骤 4** 为以下各项创建一个新的注册表项：

* 值名称：`webVault`
* 值名称：`api`
* 值名称：`identity`
* 值名称：`icons`
* 值名称：`notifications`
* 值名称：`events`

{% hint style="info" %}
您还可以使用 GPO 强制安装浏览器扩展。[了解更多](../admin-console/more/deploy-browser-extension-to-managed-devices.md#windows)。
{% endhint %}
{% endtab %}

{% tab title="macOS" %}
要为 macOS 预配置环境 URL：

1、创建一个新文件 `com.google.chrome.extensions.<extension_id>.plist`。

`<extension_id>` 将根据您的安装方法而有所不同。您可以通过导航到浏览器的扩展程序菜单（例如 `chrome://extensions`）找到您的扩展程序 ID。

2、在已创建的 `.plist` 文件中，添加以下内容：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
	<dict>
		<key>environment</key>
		<dict>
			<key>base</key>
			<string>https://my.bitwarden.server.com</string>
		</dict>
	</dict>
</plist>
```

大多数安装只需要 `base <key>` 和 `<string>` 对，但一些特殊设置，可能需要您单独为每一个服务输入 URL：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
	<dict>
		<key>environment</key>
		<dict>
			<key>base</key>
			<string>https://my.bitwarden.server.com</string>
                        <key>webVault</key>
                        <string>https://my.bitwarden.server.com</string>
                        <key>api</key>
                        <string>https://my.bitwarden.server.com></string>
                        <key>identity</key>
                        <string>https://my.bitwarden.server.com</string>
                        <key>icons</key>
                        <string>https://my.bitwarden.server.com</string>
                        <key>notifications</key>
                        <string>https://my.bitwarden.server.com</string>
                        <key>events</key>
                        <string>https://my.bitwarden.server.com</string>
		</dict>
	</dict>
</plist>
```

3、将 `.plist` 文件转换为 `.mobileconfig` 配置文件。

{% hint style="info" %}
如果您打算使用 Chrome 或 Chromium Web Store 版本的 Bitwarden，你可以按照[这些说明](../admin-console/more/deploy-browser-extension-to-managed-devices.md#macos)，通过创建另一个可以在下一步分发的配置文件，将 Bitwarden 强制安装在终端用户计算机上。
{% endhint %}

4、使用您首选的软件分发或 MDM 工具，将以下内容部署到用户的计算机：

* Chrome 或基于Chromium 的浏览器
* `.mobileconfig` 配置文件
{% endtab %}
{% endtabs %}

### Firefox <a href="#firefox" id="firefox"></a>

{% tabs %}
{% tab title="Linux" %}
要为 Linux 预配置环境 URL：

1、创建目录 `/etc/firefox/policies`：

```
mkdir -p /etc/firefox/policies
```

2、由于您需要将此目录及其中的文件部署到用户的机器上，建议要确保旧管理员可以在 `/policies` 目录中写入文件：

```
chmod -R 755 /etc/firefox/policies
```

3、在 `/etc/firefox/policies` 中创建一个 `policies.json` 文件并添加以下内容：

```
{
 "policies": {
    "3rdparty": {
      "Extensions": {
        "{446900e4-71c2-419f-a6a7-df9c091e268b}": {
          "environment": {
            "base": "https://my.bitwarden.server.com"
          }
        }
      }
    }
  }
}
```

大多数安装只需要 `"base":` URL，但一些特殊设置，可能需要您单独为每一个服务输入 URL：

```
{
 "policies": {
    "3rdparty": {
      "Extensions": {
        "{446900e4-71c2-419f-a6a7-df9c091e268b}": {
          "environment": {
            "base": "https://my.bitwarden.server.com",
            "webVault": "https://my.bitwarden.server.com",
            "api": "https://my.bitwarden.server.com",
            "identity": "https://my.bitwarden.server.com",
            "icons": "https://my.bitwarden.server.com",
            "notifications": "https://my.bitwarden.server.com",
            "events": "https://my.bitwarden.server.com"
          }
        }
      }
    }
  }
}
```

4、使用您首选的软件分发或 MDM 工具，将 `/etc/firefox/policies/policies.json` 部署到用户的计算机。
{% endtab %}

{% tab title="Windows" %}
要为 Windows 预配置环境 URL：

1、创建目录 `C:\Program Files\Mozilla Firefox\distribution`。

2、在 `distribution` 文件夹中创建一个 `policy.json` 文件并添加以下内容：

```
{
 "policies": {
    "3rdparty": {
      "Extensions": {
        "{446900e4-71c2-419f-a6a7-df9c091e268b}": {
          "environment": {
            "base": "https://my.bitwarden.server.com"
          }
        }
      }
    }
  }
}
```

大多数安装只需要 `"base":` URL，但一些特殊设置，可能需要您单独为每一个服务输入 URL：

```
{
 "policies": {
    "3rdparty": {
      "Extensions": {
        "{446900e4-71c2-419f-a6a7-df9c091e268b}": {
          "environment": {
            "base": "https://my.bitwarden.server.com",
            "webVault": "https://my.bitwarden.server.com",
            "api": "https://my.bitwarden.server.com",
            "identity": "https://my.bitwarden.server.com",
            "icons": "https://my.bitwarden.server.com",
            "notifications": "https://my.bitwarden.server.com",
            "events": "https://my.bitwarden.server.com"
          }
        }
      }
    }
  }
}
```

3、使用现有或新的 GPO 将 `C:\Program Files\Mozilla Firefox\distribution\policies.json` 部署到您想要的范围内。当范围内的用户重新启动或首次启动 Firefox 时，将应用此环境 URL。
{% endtab %}

{% tab title="macOS" %}
要为 macOS 预配置环境 URL：

1、通过运行以下命令移除自动应用于 Firefox 的隔离属性：

```
xattr -r -d com.apple.quarantine /Applications/Firefox.app
```

2、创建目录 `/Applications/Firefox.app/Contents/Resources/distribution`。

3、在 `distribution` 文件夹中创建一个 `policy.json` 文件并添加以下内容：

```
{
 "policies": {
    "3rdparty": {
      "Extensions": {
        "{446900e4-71c2-419f-a6a7-df9c091e268b}": {
          "environment": {
            "base": "https://my.bitwarden.server.com"
          }
        }
      }
    }
  }
}
```

大多数安装只需要 `"base":` URL，但一些特殊设置，可能需要您单独为每一个服务输入 URL：

```
{
 "policies": {
    "3rdparty": {
      "Extensions": {
        "{446900e4-71c2-419f-a6a7-df9c091e268b}": {
          "environment": {
            "base": "https://my.bitwarden.server.com",
            "webVault": "https://my.bitwarden.server.com",
            "api": "https://my.bitwarden.server.com",
            "identity": "https://my.bitwarden.server.com",
            "icons": "https://my.bitwarden.server.com",
            "notifications": "https://my.bitwarden.server.com",
            "events": "https://my.bitwarden.server.com"
          }
        }
      }
    }
  }
}
```

4、使用您首选的软件分发或 MDM 工具，将 `/etc/firefox/policies/policies.json` 部署到用户的计算机。
{% endtab %}
{% endtabs %}

## 桌面应用程序 <a href="#desktop-apps" id="desktop-apps"></a>

要集中配置桌面应用程序进行部署，首先在某一个工作站上完成以下步骤：

1、安装桌面应用程序。如果您使用的是 Windows，请以管理员身份使用 `installer.exe /allusers /S` 静默安装 Bitwarden（请参阅 [NSIS 文档](https://nsis.sourceforge.io/Docs/Chapter4.html#silent)）。

2、导航到桌面应用程序的本地存储设置目录。此目录因您的操作系统而异（例如，Windows 上为 `%AppData%\Bitwarden`，macOS 上为 `~/Library/Application Support/Bitwarden`）。[查找您的目录](../security/storage.md)。

3、打开目录中的 `data.json` 文件。

4、编辑 `data.json` 以根据需要配置桌面应用程序。特别是，创建以下对象以使用您的自托管服务器 URL 配置应用程序：

```
}
 "environmentUrls": {
		     "base": "https://my.bitwarden.server.com",
		     "api": null,
		     "identity": null,
		     "webVault": null,
		     "icons": null,
		     "notifications": null,
		     "events": null,
		     "enterprise": null
	  }
}
```

5、按照您希望的方式配置后，使用您选择的端点管理解决方案（如 [Jamf](https://www.jamf.com/)）将预配置的桌面应用程序部署为模板。

## 移动应用程序 <a href="#mobile-apps" id="mobile-apps"></a>

大多数移动设备管理 (MDM) 或企业移动管理 (EMM) 解决方案允许管理员在部署之前以标准方式预配置应用程序。要预配置 Bitwarden 移动应用程序以使用您的自托管服务器 URL，请构建以下应用程序配置：

| 配置密钥                 | 值类型    | 配置值                                                |
| -------------------- | ------ | -------------------------------------------------- |
| `baseEnvironmentUrl` | string | 您的自托管服务器 URL，例如 `https://my.bitwarden.server.com`。 |

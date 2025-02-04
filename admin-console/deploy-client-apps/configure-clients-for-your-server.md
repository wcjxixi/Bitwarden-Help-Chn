# =为您的服务器配置客户端

{% hint style="success" %}
参阅[为您的服务器配置客户端](../../self-hosting/configure-clients-centrally.md)
{% endhint %}

> **\[译者注]**：
>
> * [MDM](https://zh.wikipedia.org/zh-cn/%E8%A1%8C%E5%8B%95%E8%A3%9D%E7%BD%AE%E7%AE%A1%E7%90%86)：Mobile Device Management（移动设备管理）。
> * [EMM](https://zh.wikipedia.org/wiki/%E4%BC%81%E6%A5%AD%E8%A1%8C%E5%8B%95%E7%AE%A1%E7%90%86)：Enterprise Mobility Management（企业移动管理）。

## 浏览器扩展 <a href="#browser-extensions" id="browser-extensions"></a>

### Chrome 和 Chromium <a href="#chrome-and-chromium" id="chrome-and-chromium"></a>

### Firefox

{% tabs %}
{% tab title="Linux" %}
要预配置 Linux 环境 URL：

1、创建目录 `/etc/firefox/policies`：

```bash
mkdir -p /etc/firefox/policies
```

2、由于需要将此目录及其中的文件部署到用户的机器上，我们建议确保旧管理员可以在 `/policies` 目录中写入文件：

```bash
chmod -R 755 /etc/firefox/policies
```

3、在 `/etc/firefox/policies` 中创建 `policies.json` 文件，并添加以下内容：

```bash
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

大多数安装只需要 `"base":` URL，但某些独特的设置可能要求您为每个服务单独输入 URL：

```bash
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

4、使用您首选的软件发布或 MDM 工具，将 `/etc/firefox/policies/policies.json` 部署到用户的机器上。
{% endtab %}

{% tab title="Windows" %}
要预配置 Windows 环境 URL：

1、打开 Windows 组策略管理器，创建一个新的组策略对象 (GPO)，或使用针对最终用户的现有 GPO。

2、编辑 GPO 然后导航至**用户配置** > **首选项** > **Windows 设置** > **注册表**。

3、右键单击文件树中的**注册表**，选择**新建** > **注册表项**。

4、创建具有以下属性的新的注册表项：

* **操作**：更新
* **Hive**：`HKEY_LOCAL_MACHINE`
* **键路径**：`KEY_LOCAL_MACHINE\SOFTWARE\Policies\Mozilla\Firefox\3rdparty\Extensions{446900e4-71c2-419f-a6a7-df9c091e268b}\environment`
* **值名称**：`base`
* **值类型**：`REG_SZ`
* **值数据**：您的服务器已配置的域名

{% hint style="info" %}
注册表键管理系统可能会从完整的键路径中省略掉 `HKEY_LOCAL_MACHINE/`。 `KEY_LOCAL_MACHINE` 是一个 Hive，如果系统有单独的 Hive 设置，则会省略该部分路径。
{% endhint %}

5、项目配置完成后，选择**确定**。

大多数安装只需要基础 URL，但某些独特的设置可能要求您为每个服务单独输入 URL。如果您的设置需要这样做，请重复步骤 4，为以下每个服务创建一个新的注册表项：

* 值名称：`webVault`
* 值名称：`api`
* 值名称：`identity`
* 值名称：`icons`
* 值名称：`notifications`
* 值名称：`events`
{% endtab %}

{% tab title="macOS" %}
要预配置 macOS 环境 URL：

1、运行以下命令，移除自动应用于 Firefox 的隔离属性：

```bash
xattr -r -d com.apple.quarantine /Applications/Firefox.app
```

2、创建 `/Applications/Firefox.app/Contents/Resources/distribution` 目录。

3、在 `distribution` 文件夹中创建 `policies.json` 文件，并添加以下内容：

```bash
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

大多数安装只需要 `"base":` URL，但某些独特的设置可能要求您为每个服务单独输入 URL：

```bash
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

4、使用您首选的软件发布或 MDM 工具，将 `/etc/firefox/policies/policies.json` 部署到用户的机器上。
{% endtab %}
{% endtabs %}

## 桌面 App <a href="#desktop-apps" id="desktop-apps"></a>

要集中配置用于部署的桌面 App，请首先在单个工作站上完成以下步骤：：

1、安装桌面 App。如果您使用的是 Windows 系统，请使用 `installer.exe /allusers /S` 以管理员身份静默安装 Bitwarden（请参阅 [NSIS 文档](https://nsis.sourceforge.io/Docs/Chapter4.html#silent)）。

> **\[译者注]**：[NSIS](https://zh.wikipedia.org/zh-cn/Nullsoft%E8%85%B3%E6%9C%AC%E5%AE%89%E8%A3%9D%E7%B3%BB%E7%B5%B1)：Nullsoft Scriptable Install System（Nullsoft 脚本安装系统）。是 Windows下，制作安装包的一种工具，也是现在非常流行的一种脚本语言。

2、导航到桌面 App 的本地存储设置。根据操作系统的不同，该目录也有所不同（例如，Windows 上是 `%AppData%\Bitwarden`，macOS 上是 `~/Library/Application Support/Bitwarden`）。[找到您的目录](../../security/storage.md)。

3、在目录中打开 `data.json` 文件。

4、编辑 `data.json` 以根据需要配置桌面 App。特别是创建以下对象，以便使用自托管服务器 URL 配置应用程序：

```bash
 "global_environment_environment": {
    "region": "Self-hosted",
    "urls": {
       "base": "self-host.com"
     }
  }
```

{% hint style="success" %}
使用 Bitwarden 云服务器的客户需要将 `"region":` 设置为 `"US"` 或 `"EU"` ，以连接到这些服务器。
{% endhint %}

5、按您想要的方式配置后，使用您选择的端点管理解决方案（例如 [Jamf](https://www.jamf.com/)）将预配置的桌面 App 作为模板进行部署。

{% hint style="info" %}
除了手动配置 `data.json` 文件，您还可以使用 Bitwarden 桌面 App 分配 `environmentUrls`。使用桌面 App 图形用户界面选择所需的区域，然后关闭 App 并找到 `data.json` 文件，以便复制环境变量信息。
{% endhint %}

如果用户遇到图形或性能问题，Bitwarden 包含可调整的以提高性能的设置。请参阅 [Password Manager FAQ](../../your-vault/general-faqs.md)。

## 移动 App <a href="#mobile-apps" id="mobile-apps"></a>

大多数移动设备管理 (MDM) 或企业移动管理 (EMM) 解决方案都允许管理员在部署前以标准方式预配置应用程序。要预配置 Bitwarden 移动 App 以使用自托管服务器 URL，请构建以下应用程序配置：

| 配置键                  | 值类型    | 配置值                                                 |
| -------------------- | ------ | --------------------------------------------------- |
| `baseEnvironmentUrl` | string | 您的自托管服务器 URL，例如  `https://my.bitwarden.server.com`。 |

## 网页 App <a href="#web-app" id="web-app"></a>

对于网页 App 的用户，Bitwarden 建议使用您的终端、组策略或移动设备管理工具设置一个书签或桌面快捷方式，指向相应的网页 App URL（例如 `https://vault.bitwarden.eu` 或您的自托管服务器）。

了解如何[使用 Google 管理控制台部署托管书签](https://support.google.com/chrome/a/answer/10265060?hl=zh-Hans)。

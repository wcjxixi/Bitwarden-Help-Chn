# 连接客户端到实例

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/change-client-environment/)
{% endhint %}

默认情况下，Bitwarden 客户端应用程序连接到 Bitwarden 托管的服务器。可以将客户端应用程序配置为连接到您的自托管 Bitwarden 实例。

{% tabs %}
{% tab title="浏览器扩展" %}
要将浏览器扩展连接到您的自托管实例：

1. 在登录或注册界面，选择**区域**下拉菜单然后选择**自托管**选项。
2. 在**服务器 URL** 字段中，输入以 `https://` 开头的您的实例的域名（例如， `https://bitwarden.example.com`）。
3. 选择**保存**按钮。

{% hint style="info" %}
具有独立设置的用户可以选择在**自定义环境**部分中单独指定每个服务的 URL。
{% endhint %}
{% endtab %}

{% tab title="移动应用程序" %}
要将移动应用程序连接到您的自托管实例：

1. 在登录或注册界面，选择**区域**下拉菜单然后选择**自托管**选项。
2. 在**服务器 URL** 字段中，输入以 `https://` 开头的您的实例的域名（例如， `https://bitwarden.example.com`）。
3. 选择**保存**按钮。

{% hint style="info" %}
具有独立设置的用户可以选择在**自定义环境**部分中单独指定每个服务的 URL。
{% endhint %}
{% endtab %}

{% tab title="桌面应用程序" %}
登录到您的桌面应用程序的每一个帐户都可以连接到不同的服务器。要将帐户连接到您的自托管服务器：

1. 在登录或注册界面，选择**区域**下拉菜单然后选择**自托管**选项。
2. 在**服务器 URL** 字段中，输入以 `https://` 开头的您的实例的域名（例如， `https://bitwarden.example.com`）。
3. 选择**保存**按钮。

{% hint style="info" %}
具有独立设置的用户可以选择在**自定义环境**部分中单独指定每个服务的 URL。
{% endhint %}
{% endtab %}

{% tab title="CLI" %}
要将 CLI 连接到您的自托管服务器：

* 使用 `bw logout` 命令注销。
* 使用如下命令将 CLI 连接到您的自托管服务器：

```bash
bw config server https://your.bw.domain.com
```

具有独立设置的用户可以使用以下命令单独指定每个服务的 URL：

```bash
bw config --web-vault <url>
bw config --api <url>
bw config --identity <url>
bw config --icons <url>
bw config --notifications <url>
bw config --events <url>
```
{% endtab %}
{% endtabs %}

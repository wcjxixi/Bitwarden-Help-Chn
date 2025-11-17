# 连接个人客户端

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/change-client-environment/)
{% endhint %}

默认情况下，Bitwarden 客户端连接到 Bitwarden 托管的服务器，但也可以将客户端应用程序配置为连接到您的自托管 Bitwarden 实例。

{% hint style="info" %}
如果您希望连接到 Bitwarden 托管的服务器，但您的客户端却试图连接到自托管的实例，请从**登录到**菜单中选择 **bitwarden.com** 或 **bitwarden.eu**。
{% endhint %}

{% tabs %}
{% tab title="浏览器扩展" %}
要将浏览器扩展连接到您的自托管实例：

1、在登录或注册界面，选择**登录到**下拉菜单然后选择**自托管**选项。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1Pq95ZZLLySxwjLr7eul5W/326732e7943499236adf16e6a16378b6/2024-12-04_10-05-14.png?_a=DAJCwlWIZAAB" %}
浏览器扩展自托管服务器选择
{% endembed %}

2、在**服务器 URL** 字段中，输入以 `https://` 开头的您的实例的域名（例如，`https://my.bitwarden.domain.com`）。

3、选择**保存**。

{% hint style="success" %}
具有独立设置的用户可以选择在**自定义环境**部分中单独指定每个服务的 URL。
{% endhint %}
{% endtab %}

{% tab title="移动 App" %}
要将移动 App 连接到您的自托管实例：

1、在登录或注册界面，选择**登录到**下拉菜单然后选择**自托管**选项。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/0mBtygWpIfx8MLtcPwxwD/0041c5a129a88b9fb5dd021a07a6da4e/2025-01-22_10-17-39.png?_a=DAJCwlWIZAAB" %}
移动端自托管服务器选择
{% endembed %}

2、在**服务器 URL** 字段中，输入以 `https://` 开头的您的实例的域名（例如，`https://my.bitwarden.domain.com`）。

3、选择**保存**。

{% hint style="success" %}
具有独立设置的用户可以选择在**自定义环境**部分中单独指定每个服务的 URL。
{% endhint %}
{% endtab %}

{% tab title="桌面 App" %}
登录到您的桌面 App 的[每一个账户](../../account/log-in-and-unlock/more-log-in-options/account-switching.md)都可以连接到不同的服务器。要将账户连接到您的自托管服务器：

1、在登录或注册界面，选择**登录到**下拉菜单然后选择**自托管**选项。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4KVc44Osl3K38W0dxdCl3M/53ad13b8f456e8d92594c29c54091bd0/desktop.png?_a=DAJCwlWIZAAB" %}
桌面端自托管服务器选择
{% endembed %}

2、在**服务器 URL** 字段中，输入以 `https://` 开头的您的实例的域名（例如，`https://my.bitwarden.domain.com`）。

3、选择**保存**。

{% hint style="success" %}
具有独立设置的用户可以选择在**自定义环境**部分中单独指定每个服务的 URL。
{% endhint %}
{% endtab %}

{% tab title="CLI" %}
要将 CLI 连接到您的自托管服务器：

1. 使用 `bw logout` 命令注销。
2. 使用如下命令将 CLI 连接到您的自托管服务器：

```bash
bw config server https://your.bw.domain.com
```

具有独立设置的用户可以使用以下命令单独指定每个服务的 URL：

```bash
bw config server --web-vault <url>
bw config server --api <url>
bw config server --identity <url>
bw config server --icons <url>
bw config server --notifications <url>
bw config server --events <url>
bw config server --key-connector <url>
```
{% endtab %}
{% endtabs %}

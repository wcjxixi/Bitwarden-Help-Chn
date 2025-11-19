# DuckDuckGo macOS 浏览器集成

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/duckduckgo-macos-browser-integration/)
{% endhint %}

{% hint style="success" %}
要将 DuckDuckGo macOS App 与 Bitwarden 集成，您需要从 [https://duckduckgo.com/mac](https://duckduckgo.com/mac) 下载 DuckDuckGo macOS 浏览器，而不是从 macOS App Store 下载。
{% endhint %}

Bitwarden 和 DuckDuckGo 合作在 DuckDuckGo macOS 浏览器中提供 Bitwarden 功能！在 DuckDuckGo 中使用登录表单时，该集成允许无缝自动填充、创建和更新 Bitwarden 密码库中的凭据：

{% embed url="https://bitwarden.com/assets/4bfRWX1qSH0NK9HG2bBDTb/bfe35d198efed114e64ef1b97d6f9508/ddg_macos.png?w=1200&fm=avif" %}
DuckDuckGo 中的 Bitwarden
{% endembed %}

该集成要求在您的计算机上安装 Bitwarden [桌面 App](../getting-started/getting-started-desktop.md) 并解锁，以便从 DuckDuckGo 访问密码库项目。

## 设置集成 <a href="#set-up-the-integration" id="set-up-the-integration"></a>

要设置 DuckDuckGo macOS 浏览器和 Bitwarden 之间的集成：

1. 打开 DuckDuckGo 的**设置**界面然后从菜单中选择**密码 & 自动填充**。
2. 在 Password Manager 部分，选择 **Bitwarden**。向导将帮助您完成集成的设置，但我们也将在这里概述剩余的步骤。
3. 如果您的计算机上尚未安装 Bitwarden 桌面 App，请安装它。
4. 打开 Bitwarden 桌面 App 然后登录或解锁您的密码库。
5. 从 macOS 菜单栏中选择 **Bitwarden** → **偏好设置**。
6. 滚动找到 **App 设置（所有账户）**&#x90E8;分。
7. 勾选**允许 DuckDuckGo 浏览器集成**。
8. 在 DuckDuckGo 中，当浏览器检测到 Bitwarden 准备就绪时，选择**连接**。
9. 在 Bitwarden 中，选择**是**以批准 DuckDuckGo 的连接请求。

{% hint style="success" %}
连接 Bitwarden 后，您可以返回 DuckDuckGo 中的**设置** → **自动填充**页面以查看集成的当前状态（例如，您是否需要解锁 Bitwarden 以自动填充、创建或更新凭据）。
{% endhint %}

## 使用集成要从 Bitwarden 自动填充凭据，请选择登录表单输入框。如果检测到凭证，它们将被提供用于自动填充：如果您使用的一组凭据未在 Bitwarden 中检测到或与存储在 Bitwarden 中的凭据不同，系统将提示您添加或更新： <a href="#use-the-integration" id="use-the-integration"></a>

{% tabs %}
{% tab title="添加或更新凭据" %}
{% embed url="https://bitwarden.com/_gatsby/image/fe626914d3df0a1e490c78770663441b/4a4c1f3813ae161604a5323aa7724e98/ddg_macos%20copy.webp?eu=d78703efb2cbf5d6066ef3d53a74693ae86b57a2f65035826b36b6ab4afbcc8e26a54b06299d2cb07a3a5cdd82e246be31c37d6948bcd28996ee4bf3ee3ca20c508a5cbd62e17200032891abb0a601146dc04c5fa084c900a46d7b82e4e0bd285d145c68a265a7d8b1f86231f39d7c76bce7e56d3086e866be471a4bcc5a2faf22e191883b43a9c9af1b86bbbdfb5e92cd8624053c83a93765052f170fed4fa4f3b500233e7c110f3398ab5fc660c5e03a4d62770f0c07f1333dd307f83a36c2fbaff50ab6272ab2f78a5e23d983e79ead44fb&a=w%3D850%26h%3D872%26fm%3Dwebp%26q%3D75&cd=2022-12-05T20%3A02%3A37.082Z" %}
DuckDuckGo 添加或更新
{% endembed %}
{% endtab %}
{% endtabs %}

# 服务器 & 客户端版本控制

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/versioning/)
{% endhint %}

目前，Bitwarden 客户端和服务器端版本使用 `yyyy.mm.r` 约定，例如，`2022.5.0` 表示 2022 年 (`2022.`) 年 5 月 (`5.`) 的基础版本 (`.0`)。如果后续发布修补程序，它们将变成 `2022.5.1`、`2022.5.2` 等。

月度最初的版本（以 `.0` 结尾的版本）由所有客户端和服务器端共用，（后续）当某些客户端和服务器端获得了修补程序（`.1`、`.2` 等），而其他还未获得时，版本号会有所偏差。

不过，情况并非总是如此。在 2022 年 5 月之前，客户端和服务器端各自具有不同的版本控制系统。如果您使用的是版本为 `1.xx.x` 或 `2.xx.x` 的客户端或服务器端，则您使用的是旧版本。

{% hint style="info" %}
当 Bitwarden 放弃对某个版本的支持时，整个发行版和所有以前的版本也将不再受到支持。
{% endhint %}

## 自托管服务器版本 <a href="#self-hosted-server-version" id="self-hosted-server-version"></a>

要查找自托管服务器的版本，请登录[系统管理员门户](../../self-hosting/system-administrator-portal.md)。**服务器**和 **Web** 的版本将列在仪表盘上。如果**已安装**的版本与**最新**版本不匹配，请[更新您的服务器](../../self-hosting/update-a-server.md)：

{% embed url="https://bitwarden.com/_gatsby/image/d8c90588021557c653dab55c0b5ab2e7/14462549b504432f8d9963b56575d8a5/Screen%20Shot%202022-09-30%20at%209.25.41%20AM.webp?eu=8ddf54e3e1cffbd65b3df1806a70686be33904aeff5662d06863b7a919a89ad777f1115222947eb32d3a5d8ad6b340be66c32d674bed848fc6b84cfde832aa0a02d55dbb63bb780f572ec0fde5a6041061c11000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41a02ad3fddcc8f60699a9de1669c8ea4fe68b8ee9f2b1813dff43173771e4c0be424edf6b652763a20130f36c9a95ec46991b43a1f3024413c50b5326f8e3a98346e878bf9a15fdb677be8b5ca311fd787c189f318a93472e6a056d49c7b2459&a=w%3D850%26h%3D334%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.196Z" %}
托管服务器版本
{% endembed %}

您也可以检查 `bitwarden.sh`/`bitwarden.ps1` 文件以查看已安装的版本。如果有更新的版本可用，运行 `updateself` 将更新这些文件，运行 `update` 将根据 `.sh`/`.ps1` 文件中列出的内容更新 Bitwarden 容器。

## 客户端版本 <a href="#client-version" id="client-version"></a>

要获取客户端应用程序的版本：

{% tabs %}
{% tab title="浏览器扩展" %}
导航到 **⚙️设置**选项卡然后选择**关于** → **关于 Bitwarden**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4EkEPm8QGo6KCPTCnn4Pg5/090ff5cd26b2fddeedcbddf9edf49e7a/2024-12-04_10-10-53.png?_a=DAJCwlWIZAAB" %}
浏览器扩展版本
{% endembed %}
{% endtab %}

{% tab title="桌面 App" %}
在 Windows 上，选择**帮助** → **关于 Bitwarden**。在 macOS 上，选择 **Bitwarden** → **关于 Bitwarden**：

{% embed url="https://bitwarden.com/_gatsby/image/339e0009c2297e447d679a237568d1b4/ad7506f4707c8d765b9747472e310983/Screen%20Shot%202022-09-29%20at%202.52.13%20PM.webp?eu=8e8c52efb59bfdd65969a8d66d70326be43604abf60430816c67b1a81ca19fd271f34d5022927eb72b60598dd7e816b860947c641be785df93bf4bf4ee60aa5c55d65fef67b62604522cc5adb0a055416bc24e09f58b9d01a06a7082b7e0b1261d571b7fae2be983baa06364b8d72d66beb1a47c6394fa79e7105f519d1f7ba420ffd09d3901f197ed4eb8b3adb75a89cab66e44159fb02b7c2208005faf73e8e3e805273174075c2ac8d827ad62f2d64741237d2c0d5cab664cb728910f6cdcecaaa95b8a7e7ee4ae9c627484c2a980bb1ca92f75ef9c21ac8b33290b0ea846b2df28b587315861e272a5d123b00307375d8215942629b6691be3059ae4458d29ff01464b2f80a24d&a=w%3D500%26h%3D482%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.189Z" %}
桌面 App 版本
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
导航到 **⚙️设置**选项卡然后选择**关于**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3zYXLGYrfsJZuGwlT7Vq3v/9db9b271b977e94468cdf04b8cab70f2/2025-01-22_10-19-54.png?_a=DAJCwlWIZAAB" %}
移动 App 版本
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
要将当前版本打印到控制台，请运行以下命令：

```batch
bw -v
```
{% endtab %}
{% endtabs %}

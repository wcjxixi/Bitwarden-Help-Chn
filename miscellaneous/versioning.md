# 版本控制

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/versioning/)
{% endhint %}

目前 Bitwarden 客户端和服务器端版本使用 `yyyy.mm.r` 约定，例如，`2022.5.0` 是 2022 年 (`2022.`) 年 5 月 (`5.`) 的基础版本 (`.0`)。如果后续发布修补程序，它们将变成 `2022.5.1`、`2022.5.2` 等。

月度最初的版本（以 `.0` 结尾的版本）由所有客户端和服务器端共用，（后续）当某些客户端和服务器端获得了修补程序（`.1`、`.2` 等），而其他还未获得时，版本号会有所偏差。

不过，情况并非总是如此。在 2022 年 5 月之前，客户端和服务器端各自具有不同的版本控制系统。如果您使用的是版本为 `1.xx.x` 或 `2.xx.x` 的客户端或服务器端，则您使用的是旧版本。

{% hint style="info" %}
当 Bitwarden 放弃对某个版本的支持时，整个发行版和所有以前的版本也将不再受到支持。
{% endhint %}

## 自托管服务器版本 <a href="#self-hosted-server-version" id="self-hosted-server-version"></a>

要查找自托管服务器的版本，请登录[系统管理员门户](../on-premises-hosting/system-administrator-portal.md)。**服务器**和 **Web** 的版本将列在仪表盘上。如果**已安装**的版本与**最新**版本不匹配，请[更新您的服务器](../on-premises-hosting/update-your-instance.md)：

{% embed url="https://bitwarden.com/_gatsby/image/d8c90588021557c653dab55c0b5ab2e7/14462549b504432f8d9963b56575d8a5/Screen%20Shot%202022-09-30%20at%209.25.41%20AM.webp?eu=8ddf54e3e1cffbd65b3df1806a70686be33904aeff5662d06863b7a919a89ad777f1115222947eb32d3a5d8ad6b340be66c32d674bed848fc6b84cfde832aa0a02d55dbb63bb780f572ec0fde5a6041061c11000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41a02ad3fddcc8f60699a9de1669c8ea4fe68b8ee9f2b1813dff43173771e4c0be424edf6b652763a20130f36c9a95ec46991b43a1f3024413c50b5326f8e3a98346e878bf9a15fdb677be8b5ca311fd787c189f318a93472e6a056d49c7b2459&a=w%3D850%26h%3D334%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.196Z" %}
托管服务器版本
{% endembed %}

您也可以检查 `bitwarden.sh`/`bitwarden.ps1` 文件以查看已安装的版本。如果有更新的版本可用，运行 `updateself` 将更新这些文件，运行 `update` 将根据 `.sh`/`.ps1` 文件中列出的内容更新 Bitwarden 容器。

## 客户端版本 <a href="#client-version" id="client-version"></a>

要获取客户端应用程序的版本：

{% tabs %}
{% tab title="浏览器扩展" %}
导航到 **⚙️设置**选项卡然后选择**关于**选项：

{% embed url="https://bitwarden.com/_gatsby/image/9f8d75cdc21b5b8a2341487d65b523e4/a325be3253f911beb131cb50326e0f7f/Screen%20Shot%202022-09-29%20at%2011.46.14%20AM.webp?eu=8d8c50b4e2cef8860b3ef5d66a26696de23b5fabfb5160823d61e6fd1af9988270a01904229073b878385c88dab545eb3590293511bcd2dec0e84ba0ec67a80856865dbc65e779045b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b9283ba5e210a2111e1ea17d23a132e1d79d6f1a8ec8d400eee2eca15f98c9e3250549d9a26477761a195ee92eb3a3e756713c7c470e639db03b9423c3e36273027b011b6cf56738d248fb652cc1ed94f019b67b7affaccf2f7182acdffdf35af27d&a=w%3D300%26h%3D480%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.166Z" %}
浏览器扩展版本
{% endembed %}
{% endtab %}

{% tab title="桌面应用程序" %}
在 Windows 上，选择**帮助** → **关于 Bitwarden**。在 macOS 上，选择 **Bitwarden** → **关于 Bitwarden**：

{% embed url="https://bitwarden.com/_gatsby/image/339e0009c2297e447d679a237568d1b4/ad7506f4707c8d765b9747472e310983/Screen%20Shot%202022-09-29%20at%202.52.13%20PM.webp?eu=8e8c52efb59bfdd65969a8d66d70326be43604abf60430816c67b1a81ca19fd271f34d5022927eb72b60598dd7e816b860947c641be785df93bf4bf4ee60aa5c55d65fef67b62604522cc5adb0a055416bc24e09f58b9d01a06a7082b7e0b1261d571b7fae2be983baa06364b8d72d66beb1a47c6394fa79e7105f519d1f7ba420ffd09d3901f197ed4eb8b3adb75a89cab66e44159fb02b7c2208005faf73e8e3e805273174075c2ac8d827ad62f2d64741237d2c0d5cab664cb728910f6cdcecaaa95b8a7e7ee4ae9c627484c2a980bb1ca92f75ef9c21ac8b33290b0ea846b2df28b587315861e272a5d123b00307375d8215942629b6691be3059ae4458d29ff01464b2f80a24d&a=w%3D500%26h%3D482%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.189Z" %}
桌面应用程序版本
{% endembed %}
{% endtab %}

{% tab title="移动应用程序" %}
导航到 **⚙️设置**选项卡然后选择**关于**选项：

{% embed url="https://bitwarden.com/_gatsby/image/a75173250dab1ed38165a14598c18b45/dddaa76341119efc8d6f69a7d208fc07/IMG_0527.webp?eu=d88b54b7e1cca9820e6af4813b73643ce13e54acab0064d73c67e4af47fe978527f31006249529e3256a59ddd6b144e860937e611ce9d4d893ef4cf4bf37a80151815ebf35b225045522ccaab1a307103cc3120ca5d1cb0ef63e26dcefebf33459131634b723e5d0bbfc767ae3c77963a9f5f36a26dcf52da40d5916954b37a665ed98837419f1cdfa76879a99c04b9bdf9d4742379caf5125110d1c1ef22bbea7b052753028445d669bf90ec737c4e034193327570900f26f6fd65cfc3f2eba998cce5ddc787cfff28966&a=w%3D222%26h%3D480%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.182Z" %}
移动应用程序版本
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
要将当前版本打印到控制台，请运行以下命令：
{% endtab %}
{% endtabs %}

# 屏蔽自动填充

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/blocking-uris/)
{% endhint %}

Bitwarden 浏览器扩展和 Android 移动 App 的用户可以明确阻止在某些域名或 URI 上自动填充：

{% tabs %}
{% tab title="浏览器扩展" %}
{% hint style="success" %}
指定为屏蔽的域名将被屏蔽自动填充、屏蔽通行密钥提示以及屏蔽保存或更新凭据提示。
{% endhint %}

要为浏览器扩展指定要屏蔽的域名：

1. 在 Bitwarden 浏览器扩展中，打开 **⚙️设置**选项卡。
2. 选择**自动填充**，然后滚动到屏幕底部并选择**屏蔽域名**。
3. 选择**添加域名**，然后指定要屏蔽的域名。
4. 选择**保存**。
{% endtab %}

{% tab title="Android" %}
{% hint style="info" %}
屏蔽自动填充 URI 仅适用于 **Android 8.0 (Oreo)** 或更高版本。
{% endhint %}

要指定 URI 以屏蔽 Android 的自动填充：

1、在 Bitwarden Android App 中，打开 **⚙️设置**标签页。

2、点击**自动填充**。

3、滚动到**屏蔽自动填充**字段，在输入框中输入 URI。使用逗号分隔的列表指定被屏蔽的 URI，示例：

```bash
https://instagram.com,androidapp://com.instagram.android,https://facebook.com
```

4、此界面没有**保存**按钮，因此只需按后退按钮或返回上一个界面即可保存您的结果。

## 获取 Android App URI <a href="#getting-android-app-uris" id="getting-android-app-uris"></a>

对于通过网络浏览器访问的网站，正确的 URI 是登录页面的 `https://..` 地址，例如 `https://instagram.com` 或 `https://instagram.com/accounts/login`。

**对于 Android App**，[URI 方案](../../auto-fill/using-uris.md#uri-schemes)总是以 `androidapp://` 作为开头，这与典型的网络浏览器 URI 有些不一样。例如：

* Instagram Android App 的 URI 为 `androidapp://com.instagram.android`。
* Reddit Android App 的 URI 为 `androidapp://com.reddit.frontpage`。
* Bitwarden Android App 的 URI 为 `androidapp://com.x8bit.bitwarden`。

{% hint style="success" %}
为 Android App 获取正确的 URI 的一种简单方法是访问 Google Play 商店中的 App 页面，点击分享按钮，然后将复制的链接粘贴到您方便阅读的地方。此链接看起来类似于 `https://play.google.com/store/apps/details?id=com.instagram.android`，`id=` 之后的值就是您的 URI，在本示例中为 `com.instagram.android`。

对于 iOS 用户，可以使用自动填充功能打开 Bitwarden 获取 App URI。打开 Bitwarden 后，选择屏幕右上角的 ✚图标。从这里复制新的密码库项目中包含的 URI。将此 URI 粘贴到此 App 的现有登录项目中。
{% endhint %}
{% endtab %}
{% endtabs %}

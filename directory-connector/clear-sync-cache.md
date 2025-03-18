# 清除同步缓存

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/clear-sync-cache/)
{% endhint %}

当同步更改到您的 Bitwarden 组织时，目录连接器将会保留本地缓存。此缓存允许目录连接器**仅在两个目录之间发送增量**（之前/之后）。

如果遇到同步错误或某一具体的目录更改未预期同步，您应该清除此缓存。清除缓存将允许在下一个同步操作期间进行完全同步。

要清除本地缓存：

{% tabs %}
{% tab title="桌面" %}
打开[目录连接器桌面 App](directory-connector-desktop-app.md)：

1. 导航到 **More** 标签页。
2. 在 **Other** 部分，选择 **Clear Sync Cache** 按钮。
{% endtab %}

{% tab title="CLI" %}
使用如下命令：

```shell
bwdc clear-cache
```
{% endtab %}
{% endtabs %}

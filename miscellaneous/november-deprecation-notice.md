# 11 月弃用通知

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/november-deprecation-notice/)
{% endhint %}

计划于 2022 年 11 月 16 日发布的下一个 Bitwarden (2022.11.0) 版本中，Bitwarden 服务器的 API 服务的两个端点将被弃用。被弃用的端点的功能将由身份验证服务中的端点接管。

曾被添加到服务器版本 1.46.0 中的端点，将由 2022.11.0 及更高版本的 Bitwarden 客户端作为新的端点使用。**这意味着运行 1.45.4 或更早版本的自托管服务器将与 2022.11.0 版本的客户端不兼容**。[了解如何检查您的服务器版本](../security/versioning.md)。

我们建议在 2022.11.0 发布之前[更新您的自托管服务器](../self-hosting/update-your-instance.md)。如果由于任何原因您无法更新，请[联系我们](https://bitwarden.com/contact/)。

{% hint style="info" %}
由于网页密码库与服务器打包在一起，即使您不更新服务器，网页密码库也将继续正常运行。
{% endhint %}

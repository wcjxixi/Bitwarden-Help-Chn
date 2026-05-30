# =管理设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/manage-devices/)
{% endhint %}

**设备**列表显示所有已登录您账户的 Bitwarden 客户端 App。对于每台设备，您可以查看客户端类型、上次活动时间以及首次登录您账户的时间。您还可以使用此列表批准或拒绝来[自其他设备的登录请求](../../../account/log-in-and-unlock/more-log-in-options/log-in-with-device.md#approve-a-log-in-request)或[设备信任请求](../../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)。

{% hint style="info" %}
**设备**是指您登录过的 Bitwarden App 的唯一安装实例。重新安装 App、清除 App 数据或清除 Cookie 可能会导致同一设备多次出现。
{% endhint %}

要查看**设备**列表：

* 在网页 App 中，导航至**设置** → **安全** → **设备**。
* 在浏览器扩展中，导航至**设置** → **账户安全** → **设备**。
* 在桌面 App 中，使用菜单栏导航至**账户** → **设备**。

在**设备**列表中，您会看到每一行对应一台设备，其包含以下内容：

| 列    | 描述                                                                                                                                                                                                                                                                                                                                                                                       |
| ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 设备   | 设备的类型，例如**移动端**或**扩展**，以及其操作系统或平台，例如 **iOS** 或 **Firefox**。                                                                                                                                                                                                                                                                                                                              |
| 最近活动 | <p>设备上次处于活动状态的时间范围，例如<strong>过去 14 天</strong>，或者：</p><p></p><p>- <strong>当前会话</strong>：表示您当前正在使用的设备。<br>- <strong>请求待处理</strong>：表示来自设备的<a href="../../../account/log-in-and-unlock/more-log-in-options/log-in-with-device.md#approve-a-log-in-request">登录请求</a>或<a href="../../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md">设备信任请求</a>。选择此设备以批准或拒绝请求。</p> |
| 首次登录 | 设备首次登录您的 Bitwarden 账户的日期和时间。                                                                                                                                                                                                                                                                                                                                                             |

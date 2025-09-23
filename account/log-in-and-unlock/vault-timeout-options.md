# 自动注销或锁定

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/vault-timeout/)
{% endhint %}

密码库超时选项决定了 Password Manager 是否会在指定的闲置时间后自动注销或锁定。要设置超时行为：

{% tabs %}
{% tab title="网页 App" %}
导航至**设置** → **偏好设置**以设置您的密码库超时时间和密码库超时动作。
{% endtab %}

{% tab title="浏览器扩展" %}
导航至**设置** → **账户安全**以设置您的密码库超时时间和密码库超时动作。
{% endtab %}

{% tab title="移动端" %}
导航至**设置** → **账户安全**以设置您的会话超时时间和密码库超时动作。
{% endtab %}

{% tab title="桌面端" %}
* 在 macOS 上，导航至 **Bitwarden** → **设置**以设置您的密码库超时时间和密码库超时动作。
* 在 Windows 和 Linux 上，导航至**文件** → **设置**以设置您的密码库超时时间和密码库超时动作。
{% endtab %}
{% endtabs %}

{% hint style="success" %}
如果您在 Bitwarden 桌面应用程序中登录了多个账户，超时时间和超时行为需根据每个账户分别设置。[了解更多](more-log-in-options/account-switching.md)。
{% endhint %}

在配置密码库超时设置时，您可以同时设置[超时时间](vault-timeout-options.md#vault-timeout)和[超时行为](vault-timeout-options.md#vault-timeout-action)。

## 密码库超时时间 <a href="#vault-timeout" id="vault-timeout"></a>

密码库超时时间规定了 Bitwarden 在超时之前的非活动状态的时长。「不活动」是由与 Bitwarden 交互后的时间确定的，而不是系统空闲时间。每一种应用程序都有标准选项（例如 1 分钟、15 分钟、1 小时）和自定义时间输入，以及特定于某些 App 的选项（例如在系统空闲时）。企业组织还可以实施[最大允许的超时时长](../../admin-console/manage-shared-items/enterprise-policies.md#vault-timeout)选项。

{% hint style="info" %}
在 Chromebook 上，无法完全关闭或重新启动浏览器。因此，使用**浏览器重启时**选项，只会在您重新启动设备时才会锁定扩展程序。

对于 Microsoft Edge 用户，关闭浏览器时不会重新启动浏览器。为了使 Bitwarden 密码库在浏览器重启时超时，必须禁用 Microsoft Edge 的两个设置：

* **启动增强**
* **在 Microsoft Edge 关闭后继续运行后台扩展和应用**
{% endhint %}

### 网页版和浏览器扩展超时 <a href="#web-and-browser-extension-timeouts" id="web-and-browser-extension-timeouts"></a>

由于网页 App 和浏览器扩展基于您的网页浏览器，因此需要考虑特殊的「超时」情况：

**1、如果您刷新浏览器** (`CMD/CTRL + R`)，您的网页 App 将被锁定。刷新不会影响浏览器扩展。

**2、如果您关闭浏览器标签页**，您将注销网页 App。关闭单个选项卡不会影响浏览器扩展。

**3、如果您关闭浏览器窗口**，您将同时注销网页 App 和浏览器扩展。

{% hint style="success" %}
默认情况下，**如果您关闭浏览器窗口**，浏览器扩展将要求您使用主密码登录或解锁，而不管您选择了哪种密码库超时操作。

您可以通过取消选中设置 PIN 码时显示的**浏览器重启时使用主密码锁定**选项，允许浏览器扩展在关闭浏览器窗口后使用 PIN 码解锁。
{% endhint %}

**4、如果您的设备设置了使用屏幕保护程序**，您的浏览器扩展将把激活屏幕保护程序理解为系统锁定，如果选择了**系统锁定时**选项，则会超时。

## 密码库超时动作 <a href="#vault-timeout-action" id="vault-timeout-action"></a>

此选项决定了 Bitwarden 在达到[密码库超时](vault-timeout-options.md#vault-timeout)[时间](vault-timeout-options.md#vault-timeout)后将执行的操作。选项包括：

* **锁定**（默认）\
  密码库锁定时将在设备上保留密码库数据，因此可以离线解锁您的密码库。您只需要输入[主密码](your-master-password.md)或 PIN 码，或使用生物识别，但不需要使用任何有效的两步登录方式。
* **注销**\
  注销密码库时将完全从设备中删除所有密码库数据。重新登录将需要重新验证您的身份，因此登录只能在在线时完成。您需要输入您的[主密码](your-master-password.md)和任何有效的[两步登录](../two-step-login/setup-guides/two-step-login-methods.md)方式。

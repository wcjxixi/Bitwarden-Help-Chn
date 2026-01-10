# 自动注销或锁定

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/vault-timeout/)
{% endhint %}

会话超时选项决定了在指定的闲置时间后，Password Manager 密码库是否会自动注销或锁定。配置密码库超时设置时，您可以设置超时时间和超时动作。

要设置超时行为：

{% tabs %}
{% tab title="网页 App" %}
导航至**设置** → **偏好设置**以选择您的会话超时时间和会话超时动作。
{% endtab %}

{% tab title="浏览器扩展" %}
导航至**设置** → **账户安全**以选择您的会话超时时间和会话超时动作。
{% endtab %}

{% tab title="移动 App" %}
导航至**设置** → **账户安全**以选择您的会话超时时间和会话超时动作。
{% endtab %}

{% tab title="桌面 App" %}
* 在 macOS 上，导航至 **Bitwarden** → **设置**以选择您的会话超时时间和会话超时动作。
* 在 Windows 和 Linux 上，导航至**文件** → **设置**以选择您的会话超时时间和会话超时动作。

{% hint style="info" %}
关闭桌面 App 将导致密码库锁定或注销，具体取决于您选择的超时动作。
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="success" %}
如果您在 Bitwarden App 中[登录了多个账户](more-log-in-options/account-switching.md)，超时时间和超时动作需根据每个账户分别设置。
{% endhint %}

## 密码库超时时间 <a href="#vault-timeout" id="vault-timeout"></a>

会话超时时间（也称为密码库超时时间）决定了 Bitwarden 在超时之前的非活动状态的时长。「不活动」是由与 Bitwarden 交互后的时间确定的，而不是系统空闲时间。

超时选项因 App 而异。如果您发现超时选项少于预期，并且您隶属于企业组织，则可能是企业组织启用了[会话超时策略](../../admin-console/oversight-visibility/enterprise-policies.md#session-timeout)。

{% tabs %}
{% tab title="网页 App" %}
选择 Bitwarden 会话何时超时：

* **经过的时间**：在您选择的时间间隔之后，例如 **5 分钟**或 **1 小时**
* **浏览器刷新时**：当您刷新打开 Bitwarden 的浏览器窗口时
* **自定义**：经过您输入的**小时**数量和**分钟**数量之后

{% hint style="info" %}
由于网页 App 和浏览器扩展基于您的网页浏览器，因此需要考虑特殊的「超时」情况：

* **如果您刷新浏览器** (`CMD/CTRL + R`)，您的网页 App 将被锁定。刷新不会影响浏览器扩展。
* **如果您关闭浏览器标签页**，您将从网页 App 中注销。关闭单个标签页不会影响浏览器扩展。
* **如果您关闭浏览器窗口**，您将从网页 App 中注销，以及您的浏览器扩展将超时。
  * 默认情况下，浏览器扩展将要求您使用主密码登录或解锁，而不管您选择了哪种密码库超时动作。
  * 要在关闭浏览器窗口后改为使用 PIN 码解锁，请在[设置 PIN 码](more-unlock-options/unlock-with-pin.md)时取消选中**浏览器重启时使用主密码锁定**选项。
{% endhint %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择 Bitwarden 会话何时超时。可用的选项可能因浏览器而异，可能包括：

* **立即**：当用户停止与 Bitwarden 交互时
* **经过的时间**：在您选择的时间间隔之后，例如 **5 分钟**或 **1 小时**
* **系统锁定时**：当设备锁定或屏幕保护程序激活时
* **浏览器重启时**：当您首次打开或重启打开 Bitwarden 的浏览器时

{% hint style="info" %}
某些浏览器将以不同方式对待“浏览器重新启动”选项：

* 在 Chromebook 上，无法完全关闭或重新启动浏览器。因此，使用**浏览器重启时**选项只会在您重新启动设备时才会锁定扩展程序。
* 在通过 snap 安装的 Firefox 浏览器中，关闭应用程序不会停止所有进程。因此，使用**浏览器重启时**选项只会在您重新启动设备时才会锁定扩展程序。
* 对于 Microsoft Edge 用户，关闭浏览器时不会重新启动浏览器。为了使 Bitwarden 密码库在浏览器重启时超时，必须禁用 Microsoft Edge 的两个设置：
  1. **启动增强**
  2. **在 Microsoft Edge 关闭后继续运行后台扩展和应用程序**
{% endhint %}

* **从不**：您的会话不会超时

{% hint style="danger" %}
**从不**超时选项会将未加密的加密密钥存储在您的设备上，这可能会影响安全性。为了确保您的数据安全，我们强烈建议您选择其他选项。
{% endhint %}

* **自定义**：经过您输入的**小时**数量和**分钟**数量之后

浏览器扩展在弹出时不会遵守您选择的超时设置。

{% hint style="info" %}
由于网页 App 和浏览器扩展基于您的网页浏览器，因此需要考虑特殊的「超时」情况：

* **如果您刷新浏览器** (`CMD/CTRL + R`)，您的网页 App 将被锁定。刷新不会影响浏览器扩展。
* **如果您关闭浏览器标签页**，您将从网页 App 中注销。关闭单个选项卡不会影响浏览器扩展。
* **如果您关闭浏览器窗口**，您将从网页 App 中注销，以及您的浏览器扩展将超时。
  * 默认情况下，浏览器扩展将要求您使用主密码登录或解锁，而不管您选择了哪种密码库超时动作。
  * 要在关闭浏览器窗口后改为使用 PIN 码解锁，请在[设置 PIN 码](more-unlock-options/unlock-with-pin.md)时取消选中**浏览器重启时使用主密码锁定**选项。
{% endhint %}
{% endtab %}

{% tab title="移动端" %}
选择 Bitwarden 会话何时超时：

* **立即**：当用户停止与 Bitwarden 交互时
* **经过的时间**：在您选择的时间间隔之后，例如 **5 分钟**或 **1 小时**
* **App 重启时**：：当您首次打开或重新启动 Bitwarden App 时
* **从不**：您的会话不会超时

{% hint style="danger" %}
**从不**超时选项会将未加密的加密密钥存储在您的设备上，这可能会影响安全性。为了确保您的数据安全，我们强烈建议您选择其他选项。
{% endhint %}

* **自定义**：经过您输入的**小时**数量和**分钟**数量之后
{% endtab %}

{% tab title="桌面端" %}
选择 Bitwarden 会话何时超时：

* **经过的时间**：在您选择的时间间隔之后，例如 **5 分钟**或 **1 小时**
* **系统空闲时**：当您的设备在设定的时间内处于非活动状态但尚未进入睡眠模式时
* **系统睡眠时**：当您的设备进入睡眠状态时
* **系统锁定时**：当您的设备锁定或屏幕保护程序激活时
* **重启时**：当您的设备首次打开或重新启动时
* **从不**：您的会话不会超时

{% hint style="danger" %}
**从不**超时选项会将未加密的加密密钥存储在您的设备上，这可能会影响安全性。为了确保您的数据安全，我们强烈建议您选择其他选项。
{% endhint %}

* **自定义**：经过您输入的**小时**数量和**分钟**数量之后
{% endtab %}
{% endtabs %}

## 会话超时动作 <a href="#session-timeout-action" id="session-timeout-action"></a>

此选项决定了 Bitwarden 在达到[会话超时](vault-timeout-options.md#vault-timeout)[时间](vault-timeout-options.md#vault-timeout)后将执行的操作。选项包括：

* **锁定**（默认）\
  密码库锁定时将在设备上保留密码库数据，因此可以离线解锁您的密码库。您只需要输入[主密码](your-master-password.md)或 PIN 码，或使用[生物识别](more-unlock-options/unlocking-with-biometrics.md)，但不需要使用任何有效的两步登录方式。
* **注销**\
  注销密码库时将完全从设备中删除所有密码库数据。重新登录将需要重新验证您的身份，因此登录只能在在线时完成。您需要输入您的[主密码](your-master-password.md)和任何有效的[两步登录](../two-step-login/setup-two-step-login/two-step-login-methods.md)方式。

### 受信任设备 <a href="#trusted-devices" id="trusted-devices"></a>

如果您使用[受信任设备](../../admin-console/login-with-sso/trusted-devices/about-trusted-devices.md)，则必须启用[生物识别](more-unlock-options/unlocking-with-biometrics.md)或 [PIN 码](more-unlock-options/unlock-with-pin.md)才能解锁您的密码库。如果未启用生物识别或 PIN 码，会话超时将始终为注销而不是锁定。

使用受信设备解锁和登录**始终**需要互联网连接。

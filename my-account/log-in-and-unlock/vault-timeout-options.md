# 密码库超时选项

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/vault-timeout/)
{% endhint %}

密码库超时决定了您的密码库在指定的不活动时间段后的行为方式。从**设置**中为每一种 Bitwarden 客户端程序单独配置超时选项。可以从各个 Bitwarden 应用程序的**设置**菜单中配置密码库超时。在配置密码库超时设置时，您可以同时设置[超时时间](vault-timeout-options.md#vault-timeout)和[超时行为](vault-timeout-options.md#vault-timeout-action)：

{% hint style="success" %}
如果您在 Bitwarden 桌面应用程序中登录了多个帐户，超时时间和超时行为需根据每个帐户分别设置。[了解更多](account-switching.md)。
{% endhint %}

## 密码库超时时间 <a href="#vault-timeout" id="vault-timeout"></a>

密码库超时时间规定了 Bitwarden 在超时之前的非活动状态的时长。「不活动」是由与 Bitwarden 交互后的时间确定的，而不是系统空闲时间。每一种应用程序都有标准选项（例如 1 分钟、15 分钟、1 小时）和自定义时间输入，以及特定于某些应用程序的选项（例如在系统空闲时）。企业组织还可以实施[最大允许的超时时长](../../admin-console/organization-basics/enterprise-policies.md#vault-timeout)选项。

{% hint style="info" %}
在 Chromebook 上，无法完全关闭或重新启动浏览器。因此，使用**浏览器重启时**选项，只会在您重新启动设备时才会锁定扩展程序。
{% endhint %}

### 网页版和浏览器扩展超时 <a href="#web-and-browser-extension-timeouts" id="web-and-browser-extension-timeouts"></a>

由于网页密码库和浏览器扩展取决于您的网页浏览器，因此需要考虑独特的「超时」情况：

1. **如果您刷新浏览器**（`CMD/CTRL + R`），您的网页密码库将被锁定。刷新不会影响浏览器扩展。
2. **如果关闭浏览器标签页**，您将注销网页密码库。关闭单个选项卡不会影响浏览器扩展。
3. **如果您退出浏览器**，您将同时注销网页密码库和浏览器扩展。

{% hint style="success" %}
如果您使用的是浏览器扩展，则可以通过启用**使用 PIN 解锁**选项并取消选中**浏览器重启后使用主密码锁定**复选框来绕过此问题。
{% endhint %}

## 密码库超时行为 <a href="#vault-timeout-action" id="vault-timeout-action"></a>

此选项决定了 Bitwarden 在达到[密码库超时](vault-timeout-options.md#vault-timeout)[时间](vault-timeout-options.md#vault-timeout)后将执行的操作。选项包括：

* **锁定**（_默认_）\
  密码库锁定时将在设备上保留密码库数据，因此可以离线解锁您的密码库。您只需要输入[主密码](your-master-password.md)来解密您的密码库数据，**而不需要**任何有效的两步登录方式。
* **注销**\
  注销密码库时将完全从设备中删除所有密码库数据。重新登录将需要重新验证您的身份，因此登录只能在在线时完成。您需要输入您的[主密码](your-master-password.md)和任何有效的[两步登录](../two-step-login/two-step-login-methods.md)方式。

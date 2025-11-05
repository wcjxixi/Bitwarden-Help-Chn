# 使用 PIN 码解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/unlock-with-pin/)
{% endhint %}

{% hint style="info" %}
如果您是企业组织的成员，[策略](../../../admin-console/oversight-visibility/enterprise-policies.md#remove-unlock-with-pin)可能会禁止您使用 PIN 码解锁。
{% endhint %}

Bitwarden 密码管理器移动 App、浏览器扩展和桌面 App 可以使用 PIN 码解锁。重要的是，**解锁**与**登录** Password Manager 是有区别的。

登录时，您仍需要使用指定的登录方式（例如[主密码](../your-master-password.md)或[受信任设备](../using-single-sign-on/add-a-trusted-device.md)）和任何有效的[两步登录方式](../../two-step-login/setup-guides/two-step-login-methods.md)。登录后，您可以自由使用 PIN 码来解锁 App。更多信息，请参阅[理解登录与解锁](../understand-log-in-vs-unlock.md)一文。

## 设置 PIN 码 <a href="#set-up-a-pin" id="set-up-a-pin"></a>

完成以下步骤即可使用 PIN 码解锁您的账户。如果您登录了多个账户，则需要为每个账户进行设置：

{% hint style="danger" %}
使用 PIN 码会降低保护应用程序的本地密码库数据库的加密级别。如果您担心设备的本地数据会受到攻击，您可能需要重新考虑使用 PIN 码是否方便。
{% endhint %}

{% tabs %}
{% tab title="浏览器扩展" %}
要为浏览器扩展设置 PIN 码：

1、打开**设置**标签，选择**账户安全**菜单，然后打开**使用 PIN 码解锁**选项：

{% embed url="https://bitwarden.com/assets/6EAFlGeRk9LfFh1GWgowor/0ea284d711e099cf04402ca06869d12a/2025-08-13_10-48-58.png?w=955&fm=avif" %}
切换使用 PIN 码解锁
{% endembed %}

2、出现提示时，在**设置 PIN 码**弹出窗口中输入您要使用的 PIN 码。PIN 码可以是任意字符（a-z、0-9、$、# 等）的组合。

{% hint style="success" %}
创建强 PIN 码：

* 如果您与他人共享您的设备，请避免使用容易猜到的数字，例如出生日期。
* 要求至少 4 个字符，但建议使用超过最低要求的字符数。
{% endhint %}

3、预先选中的**浏览器重启时使用主密码锁定**选项将要求在浏览器重新启动时输入主密码而不是 PIN 码。如果您希望能够在浏览器重新启动时使用 PIN 码解锁，请取消选中此选项。

{% hint style="info" %}
当如果您关闭了此选项，Bitwarden 应用程序在进入锁定状态时可能无法完全清除应用程序内存中的敏感数据。如果您担心设备的本地内存受到盗用，您应该保持此选项处于打开状态。
{% endhint %}

{% hint style="danger" %}
使用 PIN 码时，您将在 5 次尝试输入 PIN 码失败后自动注销。
{% endhint %}
{% endtab %}

{% tab title="移动端" %}
要为移动 App 设置 PIN 码：

1、在您的 Bitwarden App 中，打开**设置**标签，然后点击**使用 PIN 码解锁**选项：

{% embed url="https://bitwarden.com/assets/7s8JhXJwhOYgmDCuwqEcvd/1451d2e61244617f768f70474ff236a8/2025-01-21_15-07-55.png?w=715&fm=avif" %}
移动端使用 PIN 码解锁
{% endembed %}

2、出现提示时，在**设置 PIN 码**弹出窗口中输入您要使用的 PIN 码。PIN 码可以是任意字符（a-z、0-9、$、# 等）的组合。

{% hint style="success" %}
创建强 PIN 码：

* 如果您与他人共享您的设备，请避免使用容易猜到的数字，例如出生日期。
* 要求至少 4 个字符，但建议使用超过最低要求的字符数。
{% endhint %}

3、当询问您是否需要在 App 重新启动时使用生物识别或主密码解锁时：

* 如果您希望在 Password Manager 从关闭状态启动时要求非 PIN 码解锁方式，请选择**是**。
* 如果您希望在 Password Manager 从关闭状态启动时能够使用您的 PIN 码，请选择**否**。

{% hint style="danger" %}
使用 PIN 码时，您将在 5 次尝试输入 PIN 码失败后自动注销。
{% endhint %}
{% endtab %}

{% tab title="桌面端" %}
要为桌面 App 设置 PIN 码：

1、打开您的**设置**（WIndows 上为**文件** → **设置**，macOS 上为 **Bitwarden** → **设置**），然后滚动到**安全**部分。

2、打开**使用 PIN 码解锁**选项：

{% embed url="https://bitwarden.com/assets/78q1ueLazPoYxUVCqPDjCC/226c8d943453a74cb1910e3529f60d8c/2025-08-13_11-08-20.png?w=825&fm=avif" %}

3、出现提示时，在**设置 PIN 码**弹出窗口中输入您要使用的 PIN 码。PIN 码可以是任意字符（a-z、0-9、$、# 等）的组合。

{% hint style="success" %}
创建强 PIN 码：

* 如果您与他人共享您的设备，请避免使用容易猜到的数字，例如出生日期。
* 要求至少 4 个字符，但建议使用超过最低要求的字符数。
{% endhint %}

4、预先选中的**重启时使用主密码锁定**选项将要求在 App 重新启动时输入主密码而不是 PIN 码。如果您希望能够在 App 重新启动时使用 PIN 码解锁，请取消选中此选项。

{% hint style="info" %}
当如果您关闭了此选项，Bitwarden 应用程序在进入锁定状态时可能无法完全清除应用程序内存中的敏感数据。如果您担心设备的本地内存受到盗用，您应该保持此选项处于打开状态。
{% endhint %}

{% hint style="danger" %}
使用 PIN 码时，您将在 5 次尝试输入 PIN 码失败后自动注销。
{% endhint %}
{% endtab %}
{% endtabs %}

### &#x20;更改 PIN 码 <a href="#change-a-pin" id="change-a-pin"></a>

您可以随时通过关闭然后重新打开**使用 PIN 码解锁**选项来更改 PIN 码。请注意，执行此操作要求 Password Manager 已解锁。

### 注销后的 PIN 码 <a href="#pins-after-a-logout" id="pins-after-a-logout"></a>

当您在上述任何 Password Manager App 上注销账户时，您配置的 PIN 码和相关设置将被自动擦除。您可以在登录后重新激活 PIN 码解锁。

# 两步登录-Duo

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-duo/)
{% endhint %}

使用 Duo 的两步登录在[可用的两步登录方式](../two-step-login-methods.md)中是比较独特的，因为它可以为个人账户启用（与其他方式一样），对[团队和企业](../../organizations/organizations.md)组织来说，可以为整个组织启用。

## 设置 Duo <a href="#setup-duo" id="setup-duo"></a>

本文涵盖适用于**个人用户**、**组织用户**和**组织管理员**的 Duo 设置：

{% hint style="info" %}
Duo 为应用程序用户引入了[通用提示](https://duo.com/docs/universal-prompt-update-guide)。此时，Duo 管理员必须从其 Duo 管理面板激活该设置。Bitwarden 文档体现了激活通用提示的登录过程，2024 年 3 月 30 日后，这将成为 Duo 的默认行为。
{% endhint %}

{% tabs %}
{% tab title="个人用户" %}
### 获取 Duo 密钥 <a href="#retrieve-duo-keys" id="retrieve-duo-keys"></a>

您需要一个 Duo 账户户才能获取 Bitwarden 所需的一些信息以完成设置。[免费注册](https://signup.duo.com/)，或登录到现有的 [Duo Admin Panel](https://admin.duosecurity.com/login)。要配置 Duo：

1. 在左侧菜单中，导航至 **Applications**。
2. 选择 **Protect an Application** 按钮。
3. 在应用程序列表中查找或检索 **Bitwarden**，然后选择 **Protect** 按钮。您将被重定向到一个 Bitwarden 应用程序页面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/35CpllTrg8k1IIQrL4Jf5m/d62f04d003eb8e6f6d7ef1da2a9f7e9b/2024-03-01_11-42-32.png?_a=BAJFJtWIB" %}
Bitwarden 应用程序页面
{% endembed %}

记录下 **Integration key**、**Secret key** 和 **API hostname**。当您在 Bitwarden 中设置 Duo 时，需要参考这些值。

### 在 Bitwarden 中设置 Duo <a href="#setup-duo-in-bitwarden" id="setup-duo-in-bitwarden"></a>

{% hint style="warning" %}
**失去对两步登录设备的访问权限可能会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方法后，您应该立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。
{% endhint %}

要为个人用户启用 Duo 方式的两步登录：

1、登录 Bitwarden 网页密码库。

2、从导航栏选择**设置** → **安全** → **两步登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2BsKs83g4cmiCUwxf2ad83/d9382d5c81ce3a8f281028176c1f6f34/Screenshot_2024-02-27_at_8.54.54_AM.png?_a=BAJFJtWIB" %}
两步登录
{% endembed %}

4、定位到 **Duo** 选项然后选择**管理**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/60ca7a602b3ed2213b146b44932a6f8b/9cd93fc2542897e9860b9a4630f212f1/twostep-options-duooverlay.webp?eu=d88a58e3e0cbaa855d3df58b61716969b23656a8aa5164d7386decfe1bfb98d576a61007759d2eb024685b8b85e045bc31ce29611fe6d088c8bb1da5b933a90e5bd150b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af862b63bcfedf2e17c1f979bc5456308a6b0fa319e2f3c13219e69db819ecb3b8a10b999de42500148df03274244e195beb7beaf3b30078266d0704768afa18da3ed6f265433f60430b46a8387c8517a73d78dda4a5f6&a=w%3D754%26h%3D391%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A18%3A20.295Z" %}
选择管理按钮
{% endembed %}

将提示您输入主密码以继续。

4、输入从 Duo Admin Portal 中获得的以下值：

* **Client ID** 输入到 **Integration Key** 字段
* **Client Secret** 输入到 **Secret Key** 字段
* 输入 **API Hostname**

5、选择**启用**按钮。

一个绿色的 `已启用` 消息表明已为您的密码库成功启用了 Duo。通过选择**关闭**按钮并看到 **Duo** 选项上有一个绿色的复选标记（**✔️**）以再次检查。

我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，你应该注销所有的 Bitwarden 应用程序，以为每个应用程序立即激活两步登录。您最终会被自动注销。

{% hint style="info" %}
在气隙网络上运行的自托管实例可能需要额外的设置才能保持与 Duo 服务器的通信。
{% endhint %}

### 注册设备 <a href="#register-a-device" id="register-a-device"></a>

设置好 Duo 后，打开网页密码库。如果 Duo 是您[优先级最高的启用方式](../two-step-login-methods.md#using-multiple-methods)，您将在下次登录时被要求注册一个两步登录设备：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1PNSfz6l3pjpOUHYd7Dv8e/53c4c5186b28a361132d1bdf663caf5c/duo_indv.png?_a=BAJFJtWIB" %}

系统会要求您注册两步登录设备，按照屏幕上的提示将辅助设备配置为使用 Duo（例如，注册和发送 SMS 或发送推送通知的设备类型）。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5Mm1G5tjfPmzs5V8obaxl1/7f482a7643742c5adefed45630ad6f1f/register.png?_a=BAJFJtWIB" %}
Duo 2FA 设置
{% endembed %}

如果您尚未下载 Duo 移动应用程序，建议您下载：

* [下载 iOS 版](https://itunes.apple.com/us/app/duo-mobile/id422663827?mt=8)
* [下载 Android 版](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile)
{% endtab %}

{% tab title="组织用户" %}
### 注册设备 <a href="#register-a-device" id="register-a-device"></a>

您的组织管理员设置了 Duo 后，下次登录时，系统将提示您启动 Duo：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/44SjeVrDTuQPz52cBxGhCX/25d783c2b2a152f26a358d4d155e38d1/launch.png?_a=BAJFJtWIB" %}
启动 Duo
{% endembed %}

系统会要求您注册两步登录设备，按照屏幕上的提示将辅助设备配置为使用 Duo（例如，注册和发送 SMS 或发送推送通知的设备类型）。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5Mm1G5tjfPmzs5V8obaxl1/7f482a7643742c5adefed45630ad6f1f/register.png?_a=BAJFJtWIB" %}
Duo 2FA 设置
{% endembed %}

{% hint style="success" %}
如果 Duo 没有要求您注册设备，请尝试使用隐身或隐私浏览窗口登录。
{% endhint %}

如果您尚未下载 Duo 移动应用程序，建议您下载：

* [下载 iOS 版](https://itunes.apple.com/us/app/duo-mobile/id422663827?mt=8)
* [下载 Android 版](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile)
{% endtab %}

{% tab title="组织管理员" %}
为一个组织启用 Duo 后，将提示所有已注册成员在他们下次登录时注册一个设备以用于 Duo 方式的两步登录。

{% hint style="info" %}
Bitwarden 将仅识别具有电子邮件地址用户名的用户。没有电子邮件地址作为主要用户名的 Duo 用户将需要一个。请参考 [Duo 用户名别名配置指南](https://help.duo.com/s/article/aliases-guide?language=en\_US)以获取更多信息和说明。
{% endhint %}

### 获取 Duo 密钥 <a href="#retrieve-duo-keys" id="retrieve-duo-keys"></a>

您需要一个 Duo 帐户才能获取 Bitwarden 所需的一些信息以完成设置。[免费注册](https://signup.duo.com/)，或登录到现有的 [Duo Admin Panel](https://admin.duosecurity.com/login)。要配置 Duo：

1. 在左侧菜单中，导航至 **Applications**。
2. 选择 **Protect an Application** 按钮。
3. 在应用程序列表中查找或检索 **Bitwarden**，然后选择 **Protect** 按钮。您将被重定向到一个 Bitwarden 应用程序页面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/35CpllTrg8k1IIQrL4Jf5m/d62f04d003eb8e6f6d7ef1da2a9f7e9b/2024-03-01_11-42-32.png?_a=BAJFJtWIB" %}
Duo Bitwarden 应用程序
{% endembed %}

记录下 **Integration key**、**Secret key** 和 **API hostname**。当您在 Bitwarden 中设置 Duo 时，需要参考这些值。

### 在 Bitwarden 中设置 Duo <a href="#setup-duo-in-bitwarden" id="setup-duo-in-bitwarden"></a>

{% hint style="warning" %}
最初配置和设置 Duo 后，在从 Duo 管理面板进行任何进一步的应用程序配置更改之前，为组织禁用它**非常重要**。进行配置更改；在 Bitwarden 中禁用 Duo，在 Duo 管理面板中进行必要的更改，然后在 Bitwarden 中重新启用 Duo。

这是因为 Duo for organizations 目前不支持[恢复代码](../recovery-codes.md)。相反，您将需要依靠 Duo 管理面板来绕过无法访问 Duo 的成员的两步登录。在 Duo 处于活动状态时从 Duo 管理面板更改应用程序配置可能会失去绕过您或您组织的成员的两步登录的能力。
{% endhint %}

您必须是[组织所有者](../../admin-console/user-management/member-roles-and-permissions.md)才能为您的组织设置 Duo。要为您的组织启用 Duo 方式的两步登录：

1、登录到 Bitwarden 网页密码库。

2、使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/f9368992bf9f9089e981c52f3065a551/Screenshot_2024-02-27_at_9.02.16_AM.png?_a=BAJFJtWIB" %}
产品切换器
{% endembed %}

3、从导航栏选择**设置** → **两步登录**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4RhAdJgvxpRiLtv0P0XrWT/49162158430b59232d6a86d89edc3b93/Screenshot_2024-02-27_at_9.01.49_AM.png?_a=BAJFJtWIB" %}
管理用于组织的 Duo
{% endembed %}

4、定位到 **Duo（组织）** 选项然后选择**管理**按钮。

5、将提示您输入主密码以继续。

6、输入从 Duo Admin Portal 中获得的以下值：

* **Client ID** 输入到 **Integration Key** 字段
* **Client Secret** 输入到 **Secret Key** 字段
* 输入 **API Hostname**

7、选择**启用**按钮。

一个绿色的 `已启用` 消息表明已为您的密码库成功启用了 Duo。通过选择**关闭**按钮并看到 **Duo** 选项上有一个绿色的复选标记（**✔️**）以再次检查。

{% hint style="info" %}
在气隙网络上运行的自托管实例可能需要额外的设置才能保持与 Duo 服务器的通信。
{% endhint %}

### 注册设备 <a href="#register-a-device" id="register-a-device"></a>

设置好 Duo 后，打开网页密码库。如果 Duo 是您[优先级最高的启用方式](../two-step-login-methods.md#using-multiple-methods)，您将在下次登录时被要求注册一个两步登录设备：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1PNSfz6l3pjpOUHYd7Dv8e/53c4c5186b28a361132d1bdf663caf5c/duo_indv.png?_a=BAJFJtWIB" %}

系统会要求您注册两步登录设备，按照屏幕上的提示将辅助设备配置为使用 Duo（例如，注册和发送 SMS 或发送推送通知的设备类型）。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5Mm1G5tjfPmzs5V8obaxl1/7f482a7643742c5adefed45630ad6f1f/register.png?_a=BAJFJtWIB" %}
Duo 2FA 设置
{% endembed %}

如果您尚未下载 Duo 移动应用程序，建议您下载：

* [下载 iOS 版](https://itunes.apple.com/us/app/duo-mobile/id422663827?mt=8)
* [下载 Android 版](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile)
{% endtab %}
{% endtabs %}

## 使用 Duo <a href="#use-duo" id="use-duo"></a>

以下内容假设 **Duo** 是您[已启用的最高优先级方式](../two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用两步登录访问您的密码库：

1. 在任一个 Bitwarden 应用程序上输入您的电子邮件地址和主密码以登录密码库。系统会出现提示，要求您启动 Duo。启动后，将出现一个 Duo 界面，开始您的两步登录验证。
2. 根据您的 Duo 的配置方式，通过以下方式完成验证请求：
   * 从您已注册的设备上批准 **Duo Push** 请求。
   * 在您的 **Duo 移动应用**或**短信**中找到 6 位验证码，并在密码库登录界面输入此验证码。

{% hint style="success" %}
勾选**记住我**复选框，以记住您的设备，为期 30 天。记住你的设备意味着你不会被要求完成两步登陆步骤。
{% endhint %}

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../your-vault/vault-timeout-options.md)。

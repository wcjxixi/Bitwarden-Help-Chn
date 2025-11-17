# 登录到多个账户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-switching/)
{% endhint %}

您知道吗？您可以在 Bitwarden 浏览器扩展、桌面 App 和移动 App 中同时登录**多达 5 个** Bitwarden 账户。使用账户切换功能，在个人账户和工作账户等 Bitwarden 账户之间无缝切换。

{% tabs %}
{% tab title="移动端" %}
要登录第二个（或第三个、第四个或第五个）账户，请从顶部菜单栏中选择当前已登录的账户，然后选择 **🞤添加账户**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/56xAZhiS6wZqKktMlFwbVn/9af5d0ce782af44fc48ebfd8057ddc4c/2025-01-21_14-58-15.png?_a=DAJCwlWIZAAB" %}
移动端账户切换
{% endembed %}

选择 **🞤添加账户**将带您进入登录界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/112EwzW6sPKPGu65R8rKHc/679b2686d9b67e5ccb37a2ebf56ea062/2025-01-21_15-04-00.png?_a=DAJCwlWIZAAB" %}
移动端登录
{% endembed %}

{% hint style="success" %}
如果您在多台服务器上拥有账户，例如，如果自托管 Bitwarden 的雇主向您发放了[家庭组织赞助](../../../plans-and-pricing/password-manager/families-for-enterprise.md)，请使用登录界面上的**服务器选择器下拉菜单**，选择**自托管**菜单，将**服务器 URL** 更改为账户的 URL。

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1Bc4QseUed27nuuhbeD7WR/1822635ca4cdd527903a0f9d5b85d271/2023-08-29_08-48-42.png?_a=DAJCwlWIZAAB" alt="自托管域名选择器" data-size="original">

在此示例中，您的工作账户可能使用诸如 `https://your.company.bitwarden.com`，而您的家庭组织账户可能使用 `https://vault.bitwarden.com`。
{% endhint %}

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除，除非[密码库超时](../vault-timeout-options.md)设置为注销。

{% hint style="info" %}
大多数密码库操作，包括添加新项目或文件夹、同步、自动填充以及[密码库超时](../vault-timeout-options.md)和解锁（[PIN](../more-unlock-options/unlock-with-pin.md) 或[生物识别](../more-unlock-options/unlocking-with-biometrics.md)）等设置仅适用&#x4E8E;_&#x6D3B;&#x52A8;_&#x8D26;户，您可以通过应用程序顶部菜单栏中显示的图标来确定活动账户。

但某些**选项**，例如[主题](../../../password-manager/more/change-app-theme.md)，则适用于**所有账户**。
{% endhint %}

## 自动填充 <a href="#auto-fill" id="auto-fill"></a>

如果您正使用账户切换，您的移动 App 将默认自动填充当前活动账户账户的凭据，但是，您可以在自动填充期间从一个账户切换到另一个账户。
{% endtab %}

{% tab title="桌面端" %}
要登录第二个（或第三个、第四个或第五个）账户，请从桌面 App 顶部右上角选择当前已登录的账户，然后选择 **🞤添加账户**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7fpUmakpNIByzoWQa1cU8L/3673552e2fcc77ea3c0a8cae7fbd2b83/Screen_Shot_2022-05-18_at_3.33.08_PM.png?_a=DAJCwlWIZAAB" %}
桌面端账户切换
{% endembed %}

选择 **🞤添加账户**将带您进入登录界面：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3gAo9PEjSXwgf4VY0Ew3TZ/11e2e56da3fa052e41f7606a029a004b/Screen_Shot_2022-05-12_at_10.58.33_AM.png?_a=DAJCwlWIZAAB" %}
桌面端账户切换
{% endembed %}

{% hint style="success" %}
如果您在多台服务器上拥有账户，例如，如果自托管 Bitwarden 的雇主向您发放了[家庭组织赞助](../../../plans-and-pricing/password-manager/families-for-enterprise.md)，请使用登录界面上的**服务器选择器下拉菜单**，选择**自托管**菜单，将**服务器 URL** 更改为账户的 URL。

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1Bc4QseUed27nuuhbeD7WR/1822635ca4cdd527903a0f9d5b85d271/2023-08-29_08-48-42.png?_a=DAJCwlWIZAAB" alt="自托管域名选择器" data-size="original">

在此示例中，您的工作账户可能使用诸如 `https://your.company.bitwarden.com`，而您的家庭组织账户可能使用 `https://vault.bitwarden.com`。
{% endhint %}

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除。

{% hint style="info" %}
大多数密码库操作，包括添加新项目或文件夹、同步、搜索以及[密码库超时](../vault-timeout-options.md)和解锁（[PIN](../more-unlock-options/unlock-with-pin.md) 或[生物识别](../more-unlock-options/unlocking-with-biometrics.md)）等设置仅适用&#x4E8E;_&#x6D3B;&#x52A8;_&#x8D26;户，您可以通过显示在应用程序右上角中的电子邮件来确定活动账户。

但某些**偏好设置**，则适用于**所有账户**：

<img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4tZUuuDPHnHQh5RNihx0TB/d82c343ba033d122e0910a6fe7a23f76/Screen_Shot_2022-01-31_at_11.18.49_AM.png?_a=DAJCwlWIZAAB" alt="桌面 App 首选项" data-size="original">
{% endhint %}
{% endtab %}

{% tab title="浏览器扩展" %}
要登录第二个（或第三个、第四个或第五个）账户，请从顶部菜单选择当前已登录的账户：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7xbbMZ89zcTHz6ee0cA1MK/4cb688e3d593e379ddd8192c6545d5b6/2024-12-02_10-49-10.png?_a=DAJCwlWIZAAB" %}
浏览器扩展账户切换
{% endembed %}

选择账户图标后，从账户切换菜单中选择 **🞤添加账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/343trVk3zLCF7Z12uA5wjO/332a681bf34d66dee8b032812f0f85ad/2024-12-02_10-50-07.png?_a=DAJCwlWIZAAB" %}
浏览器扩展添加账户
{% endembed %}

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除。

## 自动填充 <a href="#auto-fill" id="auto-fill"></a>

如果您正使用账户切换，浏览器扩展将默认自动填充当前活动账户账户的凭据。
{% endtab %}
{% endtabs %}

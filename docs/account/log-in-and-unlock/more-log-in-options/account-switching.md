# 登录到多个账户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-switching/)
{% endhint %}

您知道吗？您可以在 Bitwarden 浏览器扩展、桌面 App 和移动 App 中同时登录**最多 5 个** Bitwarden 账户。使用账户切换功能，在个人账户和工作账户等 Bitwarden 账户之间无缝切换。

{% tabs %}
{% tab title="移动端" %}
要登录第二个（或第三个、第四个或第五个）账户，请从顶部菜单栏中选择当前已登录的账户，然后选择 **➕添加账户**。

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/56xAZhiS6wZqKktMlFwbVn/9af5d0ce782af44fc48ebfd8057ddc4c/2025-01-21_14-58-15.png?w=713&#x26;fm=avif" alt=""><figcaption><p>移动端账户切换</p></figcaption></figure></div>

选择 **➕添加账户**将带您进入登录界面：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/112EwzW6sPKPGu65R8rKHc/679b2686d9b67e5ccb37a2ebf56ea062/2025-01-21_15-04-00.png?w=710&#x26;fm=avif" alt=""><figcaption><p>移动端登录</p></figcaption></figure></div>

{% hint style="success" %}
如果您在多台服务器上拥有账户，例如，如果自托管 Bitwarden 的雇主向您发放了[家庭组织赞助](../../../admin-console/manage-members/sponsored-families/sponsored-families-for-members.md)，请使用登录界面上的**服务器选择器下拉菜单**，选择**自托管**菜单，将**服务器 URL** 更改为账户的 URL。

<img src="https://bitwarden.com/assets/1Bc4QseUed27nuuhbeD7WR/e5dbca7997cb8efe1ebbff001813354e/2026-01-28_09-16-56.png?w=1001&#x26;fm=avif" alt="" data-size="original">

在此示例中，您的工作账户可能使用诸如 `https://your.company.bitwarden.com`，而您的家庭组织账户可能使用 `https://vault.bitwarden.com`。
{% endhint %}

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除，除非[密码库超时](../vault-timeout-options.md)设置为注销。

{% hint style="info" %}
大多数密码库操作，包括添加新项目或文件夹、同步、自动填充以及[密码库超时](../vault-timeout-options.md)和解锁（[PIN 码](../more-unlock-options/unlock-with-pin.md) 或[生物识别](../more-unlock-options/unlocking-with-biometrics.md)）等设置仅适用于活动账户，您可以通过 App 顶部菜单栏中显示的图标来确定活动账户。

但某些选项，例如[主题](../../../password-manager/your-vault/appearance/change-app-appearance.md)，则适用于所有账户。
{% endhint %}

## 自动填充 <a href="#auto-fill" id="auto-fill"></a>

如果您正使用账户切换，您的移动 App 将默认自动填充当前活动账户账户的凭据，但是，您可以在自动填充期间从一个账户切换到另一个账户。
{% endtab %}

{% tab title="桌面端" %}
要登录第二个（或第三个、第四个或第五个）账户，请从桌面 App 顶部右上角选择当前已登录的账户，然后选择 **➕添加账户**。

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7fpUmakpNIByzoWQa1cU8L/bd9e35756805bba8bd35bc43c7630aaf/2026-04-23_09-27-28.png?w=800&#x26;fm=avif" alt=""><figcaption><p>桌面 App 账户切换</p></figcaption></figure></div>

选择 **➕添加账户**将带您进入登录界面：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6Dvz7SzKBp90RDcROWgBhW/2407b5d1399cc1b8d0780b31dcbd95ee/2026-04-23_09-29-54.png?w=800&#x26;fm=avif" alt=""><figcaption><p>桌面 App 账户切换</p></figcaption></figure></div>

{% hint style="success" %}
如果您在多台服务器上拥有账户，例如，如果自托管 Bitwarden 的雇主向您发放了[家庭组织赞助](../../../admin-console/manage-members/sponsored-families/sponsored-families-for-members.md)，请使用登录界面上的**服务器选择器下拉菜单**，选择**自托管**菜单，将**服务器 URL** 更改为账户的 URL。

<img src="https://bitwarden.com/assets/1Bc4QseUed27nuuhbeD7WR/e5dbca7997cb8efe1ebbff001813354e/2026-01-28_09-16-56.png?w=1001&#x26;fm=avif" alt="" data-size="original">

在此示例中，您的工作账户可能使用诸如 `https://your.company.bitwarden.com`，而您的家庭组织账户可能使用 `https://vault.bitwarden.com`。
{% endhint %}

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除。

{% hint style="info" %}
大多数密码库操作，包括添加新项目或文件夹、同步、搜索以及[密码库超时](../vault-timeout-options.md)和解锁（[PIN 码](../more-unlock-options/unlock-with-pin.md) 或[生物识别](../more-unlock-options/unlocking-with-biometrics.md)）等设置仅适用于活动账户，您可以通过显示在 App 右上角中的电子邮件来确定活动账户。

但某些**偏好设置**，则适用于**所有账户**：

<img src="https://bitwarden.com/assets/4tZUuuDPHnHQh5RNihx0TB/e20745ac076e7274ec0652692159c4e1/2026-04-23_09-34-58.png?w=800&#x26;fm=avif" alt="" data-size="original">
{% endhint %}
{% endtab %}

{% tab title="浏览器扩展" %}
要登录第二个（或第三个、第四个或第五个）账户，请从顶部菜单选择当前已登录的账户：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7xbbMZ89zcTHz6ee0cA1MK/8d8972a6b995b3fd7367f248c9c60d69/screenshot_3.png?w=440&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展账户切换</p></figcaption></figure></div>

选择账户图标后，从账户切换菜单中选择 **➕添加账户**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/343trVk3zLCF7Z12uA5wjO/ac2f56fc907372335f30d1dbf68116a1/screenshot_4.png?w=438&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展添加账户</p></figcaption></figure></div>

登录第二个账户后，您可以从同一菜单中快速切换它们，该菜单还将显示每个账户的密码库的当前状态（已锁定或已解锁）。如果您注销其中一个账户，它将从列表中移除。

{% hint style="info" %}
~~目前 Safari 上不支持通过浏览器扩展进行账户切换。~~
{% endhint %}

## 自动填充 <a href="#auto-fill" id="auto-fill"></a>

如果您正使用账户切换，浏览器扩展将默认自动填充当前活动账户账户的凭据。
{% endtab %}
{% endtabs %}

# 团队成员

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/courses/password-manager-team-member/)
{% endhint %}

您的管理员已为您的组织或家庭设置了 Bitwarden，现在是时候让它为您服务了。本课程向您展示如何自动保存密码、安全地共享凭据以及将 Bitwarden 集成到您的日常工作流程中，从而轻松保持安全。

{% tabs %}
{% tab title="企业版" %}
{% hint style="success" %}
您还可以参加[公共培训课程](https://bitwarden.com/events/tag/demo/)。
{% endhint %}

## 开始使用 <a href="#get-started" id="get-started"></a>

### 加入您的组织 <a href="#join-your-organization" id="join-your-organization"></a>

有几种不同的方式可以加入 Bitwarden 组织；您需要使用哪种方式取决于您的组织的独特设置。有些组织允许您使用单点登录 (SSO) 账户注册，有些组织则会向您的工作收件箱发送电子邮件邀请：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/58e2ece3acfe37eaffa4bc55611eb414/Screen_Shot_2023-04-28_at_10.40.35_AM.png?_a=DAJCwlWIZAAB" %}
邀请加入
{% endembed %}

如果您不确定，请向公司的 IT 团队或您的经理询问有关如何加入 Bitwarden 的信息。

{% embed url="https://vimeo.com/1086379394?fl=pl&fe=sh" %}

视频章节：

* **00:06**：概述
* **00:29**：1、从 Bitwarden 主页创建
* **01:26**：2、从 Bitwarden 客户端创建
* **01:36**：3、从邀请/SSO 创建
* **02:26**：Bitwarden 学习中心

### 主密码和受信任设备 <a href="#master-password-vs-trusted-devices" id="master-password-vs-trusted-devices"></a>

#### 您的主密码 <a href="#your-master-password" id="your-master-password"></a>

大多数情况下，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2pST1WXY0Xk7GQ4GpwzELn/59b88f130a5d65b51c75bbe3a742a702/2024-12-02_10-20-39.png?_a=DAJCwlWIZAAB" %}
设置主密码
{% endembed %}

#### 受信任设备 <a href="#trusted-devices" id="trusted-devices"></a>

在其他情况下，登录 Bitwarden 需要将登录设备注册为受信任设备。当您加入组织时，您用来加入的设备会自动注册为受信任设备，但您应该[熟悉添加更多受信任设备的流程](../../../docs/account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)，这样您就可以随时随地安全地访问公司凭据了。

### 了解您的密码库 <a href="#get-to-know-your-vault" id="get-to-know-your-vault"></a>

Bitwarden Password Manager 网页 App 将列出您的所有密码库项目，包括[登录、支付卡、身份和安全笔记](../../../docs/password-manager/your-vault/vault-items/vault-items.md)：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2xTpSA11EOCzx8VIuVffcF/d3bc18e7fc3c3cb0bf1779fad9262cd3/2024-12-02_13-42-14.png?_a=DAJCwlWIZAAB" %}
Password Manager 网页 App
{% endembed %}

您可以通过网页 App 在密码库中填入需要保护的信息，整理您的凭据以便于访问，等等。您在任何 Bitwarden App 中添加的项目都会同步到您登录的其他 Bitwarden  App，因此您可以在任何地方登录账户。

### 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

您是否将密码保存在浏览器（如 Chrome 浏览器）中？或者您是从其他密码管理器来到 Bitwarden 的？ 您可以直接将登录信息导入到 Bitwarden，从而[避免了复制粘贴的痛苦](../../../docs/secrets-manager/import-export/import-data.md)。

或者，如果您将密码保存在纸上或脑中，让我们开始[添加更多项目到您的密码库](../../../docs/password-manager/getting-started/getting-started-webvault.md#first-steps)吧。

### 与您的企业共享 <a href="#share-with-your-team" id="share-with-your-team"></a>

作为组织成员，您可以与团队成员安全共享诸如公司信用卡和登录凭据等信息。共享项目可通过一个独立的密码库访问，该密码库在您加入组织时被添加到您的 Bitwarden App 中：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?_a=DAJCwlWIZAAB" %}
组织密码库
{% endembed %}

共享项目被组合成集合，团队可根据业务单元（如「销售团队」）、业务功能（如「社交媒体登录」）、系统（如「AWS 凭据」）等进行组织。

了解[如何与您的团队共享凭据](../../../docs/password-manager/organization-members/sharing.md)。

### 浏览网页时使用 Bitwarden <a href="#use-bitwarden-while-browsing" id="use-bitwarden-while-browsing"></a>

Bitwarden 浏览器扩展具有自动填充的魔力，使您可以轻松地使用已保存的密码快速登录您的账户。[下载](https://bitwarden.com/download/)浏览器扩展并了解在浏览网页时[如何自动填充密码](../../../docs/password-manager/autofill/autofill-from/autofill-from-browser-extensions.md)。

{% embed url="https://bitwarden.com/assets/1pamjhdWn7obh8UBxXcIPF/1841242fa5299a780d53f3ae70e546b3/screenshot_5.png?w=395&fm=avif" %}

{% embed url="https://vimeo.com/1084695614?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/getting-started/getting-started-browserext.md)了解更多有关浏览器扩展入门的信息。

* **00:11**：安装 Bitwarden
* **00:23**：固定扩展
* **00:32**：登录或创建账户
* **00:37**：禁用浏览器的密码管理器
* **00:50**：导入项目
* **01:11**：创建新项目
* **01:42**：附加字段
* **01:52**：使用文件夹
* **02:11**：收藏项目
* **02:17**：自动填充
* **02:39**：自动保存弹出窗口
* **02:45**：PIN 码和生物识别
* **02:58**：账户切换
* **03:07**：自定义 Bitwarden

最好[禁用浏览器的内置密码管理器](../../../docs/password-manager/getting-started/getting-started-browserext.md#disable-a-built-in-password-manager)，以确保 Bitwarden 始终是您的首选密码管理器。

#### Chrome

{% embed url="https://vimeo.com/1077612510?fl=pl&fe=sh" %}

#### Microsoft Edge

{% embed url="https://vimeo.com/1077612658?fl=pl&fe=sh" %}

### 随身携带 Bitwarden <a href="#take-bitwarden-on-the-go" id="take-bitwarden-on-the-go"></a>

安全无处不在！获取 Bitwarden 移动 App，这样您就可以在外出时安全地使用您的密码。[下载](https://bitwarden.com/download/)移动 App 并了解在 [iOS](../../../docs/password-manager/autofill/autofill-from/autofill-from-ios.md) 或 [Android](../../../docs/password-manager/autofill/autofill-from/autofill-from-android.md) 上如何自动填充密码：

### 将安全浏览带入家庭 <a href="#bring-secure-browsing-home" id="bring-secure-browsing-home"></a>

一些企业组织为成员提供了一个免费的赞助家庭组织，这样员工就可以与最多 5 位朋友或家人安全地共享个人密码箱项目。了解[如何兑换您的赞助](../../../docs/plans-and-pricing/password-manager/families-for-enterprise.md#redeem-your-sponsorship)，确保您的家人实践安全浏览。

## 了解更多 <a href="#learn-more" id="learn-more"></a>

### 更改默认语言 <a href="#change-the-default-language" id="change-the-default-language"></a>

{% embed url="https://vimeo.com/795737043?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/more/localization.md)了解更多有关更改 App 语言的信息。

* **00:15**：更改网页 App 中的语言设置
* **00:56**：更改桌面 App 中的语言设置

### 为您所有设备获取 Bitwarden <a href="#get-bitwarden-for-all-your-devices" id="get-bitwarden-for-all-your-devices"></a>

{% embed url="https://vimeo.com/795737043?fl=pl&fe=sh" %}

[此处](https://bitwarden.com/download/)下载适用于您所有设备的 Bitwarden App。

### 使用 Bitwarden Send 分享安全链接 <a href="#sharing-secure-links-with-bitwarden-send" id="sharing-secure-links-with-bitwarden-send"></a>

{% embed url="https://vimeo.com/797850224?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/bitwarden-send/about-send.md)了解更多有关 Bitwarden Send 的信息。

* **00:25**：使用 Bitwarden Send
* **01:26**：安全和访问控制

### 使用自定义字段 <a href="#using-custom-fields" id="using-custom-fields"></a>

{% embed url="https://vimeo.com/821402921?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/your-vault/vault-items/custom-fields.md)了解更多有关使用自定义字段的信息。

* **00:07**：自定义字段的创建和类型
* **00:41**：自定义字段的使用和链接
* **01:30**：添加自定义字段
{% endtab %}

{% tab title="团队版" %}
{% hint style="success" %}
您还可以参加[公共培训课程](https://bitwarden.com/events/tag/demo/)。
{% endhint %}

## 开始使用 <a href="#get-started" id="get-started"></a>

### 加入您的团队 <a href="#join-your-team" id="join-your-team"></a>

检查收件箱，查看新组织的邀请函！如果您已有账户，那就太好了！您只需接受邀请即可。如果没有，在接受邀请后，系统会提示您创建一个账户：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/58e2ece3acfe37eaffa4bc55611eb414/Screen_Shot_2023-04-28_at_10.40.35_AM.png?_a=DAJCwlWIZAAB" %}
邀请加入
{% endembed %}

{% embed url="https://vimeo.com/1086379394?fl=pl&fe=sh" %}

视频章节：

* **00:06**：概述
* **00:29**：1、从 Bitwarden 主页创建
* **01:26**：2、从 Bitwarden 客户端创建
* **01:36**：3、从邀请/SSO 创建
* **02:26**：Bitwarden 学习中心

### 您的主密码 <a href="#your-master-password" id="your-master-password"></a>

注册时，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2pST1WXY0Xk7GQ4GpwzELn/59b88f130a5d65b51c75bbe3a742a702/2024-12-02_10-20-39.png?_a=DAJCwlWIZAAB" %}
设置主密码
{% endembed %}

### 了解您的密码库 <a href="#get-to-know-your-vault" id="get-to-know-your-vault"></a>

Bitwarden Password Manager 网页 App 将列出您的所有密码库项目，包括[登录、支付卡、身份和安全笔记](../../../docs/password-manager/your-vault/vault-items/vault-items.md)：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2xTpSA11EOCzx8VIuVffcF/d3bc18e7fc3c3cb0bf1779fad9262cd3/2024-12-02_13-42-14.png?_a=DAJCwlWIZAAB" %}
Password Manager 网页 App
{% endembed %}

您可以通过网页 App 在密码库中填入需要保护的信息，整理您的凭据以便于访问，等等。您在任何 Bitwarden App 中添加的项目都会同步到您登录的其他 Bitwarden  App，因此您可以在任何地方登录账户。

### 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

您是否将密码保存在浏览器（如 Chrome 浏览器）中？或者您是从其他密码管理器来到 Bitwarden 的？ 您可以直接将登录信息导入到 Bitwarden，从而[避免了复制粘贴的痛苦](../../../docs/secrets-manager/import-export/import-data.md)。

或者，如果您将密码保存在纸上或脑中，让我们开始[添加更多项目到您的密码库](../../../docs/password-manager/getting-started/getting-started-webvault.md#first-steps)吧。

### 与您的团队共享 <a href="#share-with-your-team" id="share-with-your-team"></a>

作为组织成员，您可以与团队成员安全共享诸如公司信用卡和登录凭据等信息。共享项目可通过一个独立的密码库访问，该密码库在您加入组织时被添加到您的 Bitwarden App 中：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?_a=DAJCwlWIZAAB" %}
组织密码库
{% endembed %}

共享项目被组合成集合，团队可根据业务单元（如「销售团队」）、业务功能（如「社交媒体登录」）、系统（如「AWS 凭据」）等进行组织。

了解[如何与您的团队共享凭据](../../../docs/password-manager/organization-members/sharing.md)。

### 浏览网页时使用 Bitwarden <a href="#use-bitwarden-while-browsing" id="use-bitwarden-while-browsing"></a>

Bitwarden 浏览器扩展具有自动填充的魔力，使您可以轻松地使用已保存的密码快速登录您的账户。[下载](https://bitwarden.com/download/)浏览器扩展并了解在浏览网页时[如何自动填充密码](../../../docs/password-manager/autofill/autofill-from/autofill-from-browser-extensions.md)。

{% embed url="https://bitwarden.com/assets/1pamjhdWn7obh8UBxXcIPF/1841242fa5299a780d53f3ae70e546b3/screenshot_5.png?w=395&fm=avif" %}

{% embed url="https://vimeo.com/1084695614?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/getting-started/getting-started-browserext.md)了解更多有关浏览器扩展入门的信息。

* **00:11**：安装 Bitwarden
* **00:23**：固定扩展
* **00:32**：登录或创建账户
* **00:37**：禁用浏览器的密码管理器
* **00:50**：导入项目
* **01:11**：创建新项目
* **01:42**：附加字段
* **01:52**：使用文件夹
* **02:11**：收藏项目
* **02:17**：自动填充
* **02:39**：自动保存弹出窗口
* **02:45**：PIN 码和生物识别
* **02:58**：账户切换
* **03:07**：自定义 Bitwarden

最好[禁用浏览器的内置密码管理器](../../../docs/password-manager/getting-started/getting-started-browserext.md#disable-a-built-in-password-manager)，以确保 Bitwarden 始终是您的首选密码管理器。

#### Chrome

{% embed url="https://vimeo.com/1077612510?fl=pl&fe=sh" %}

#### Microsoft Edge

{% embed url="https://vimeo.com/1077612658?fl=pl&fe=sh" %}

### 随身携带 Bitwarden <a href="#take-bitwarden-on-the-go" id="take-bitwarden-on-the-go"></a>

安全无处不在！获取 Bitwarden 移动 App，这样您就可以在外出时安全地使用您的密码。[下载](https://bitwarden.com/download/)移动 App 并了解在 [iOS](../../../docs/password-manager/autofill/autofill-from/autofill-from-ios.md) 或 [Android](../../../docs/password-manager/autofill/autofill-from/autofill-from-android.md) 上如何自动填充密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/53OzJZ4klYWemxUepHMtq4/5ab47331f033259bd2e82817a99e992f/2025-01-21_15-22-10.png?_a=DAJCwlWIZAAB" %}
iOS 和 Android 上的 Bitwarden
{% endembed %}

## 了解更多 <a href="#learn-more" id="learn-more"></a>

### 更改默认语言 <a href="#change-the-default-language" id="change-the-default-language"></a>

{% embed url="https://vimeo.com/795737043?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/more/localization.md)了解更多有关更改 App 语言的信息。

* **00:15**：更改网页 App 中的语言设置
* **00:56**：更改桌面 App 中的语言设置

### 为您所有设备获取 Bitwarden <a href="#get-bitwarden-for-all-your-devices" id="get-bitwarden-for-all-your-devices"></a>

{% embed url="https://vimeo.com/795737043?fl=pl&fe=sh" %}

[此处](https://bitwarden.com/download/)下载适用于您所有设备的 Bitwarden App。

### 使用 Bitwarden Send 分享安全链接 <a href="#sharing-secure-links-with-bitwarden-send" id="sharing-secure-links-with-bitwarden-send"></a>

{% embed url="https://vimeo.com/797850224?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/bitwarden-send/about-send.md)了解更多有关 Bitwarden Send 的信息。

* **00:25**：使用 Bitwarden Send
* **01:26**：安全和访问控制

### 使用自定义字段 <a href="#using-custom-fields" id="using-custom-fields"></a>

{% embed url="https://vimeo.com/821402921?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/your-vault/vault-items/custom-fields.md)了解更多有关使用自定义字段的信息。

* **00:07**：自定义字段的创建和类型
* **00:41**：自定义字段的使用和链接
* **01:30**：添加自定义字段
{% endtab %}

{% tab title="家庭版" %}
## 开始使用 <a href="#get-started" id="get-started"></a>

### 加入您的家庭 <a href="#join-your-family" id="join-your-family"></a>

检查收件箱，查看新组织的邀请函！如果您已有账户，那就太好了！您只需接受邀请即可。如果没有，在接受邀请后，系统会提示您创建一个账户：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4Fe96NuWb7yRe6muKf7UbZ/58e2ece3acfe37eaffa4bc55611eb414/Screen_Shot_2023-04-28_at_10.40.35_AM.png?_a=DAJCwlWIZAAB" %}
邀请加入
{% endembed %}

### 您的主密码 <a href="#your-master-password" id="your-master-password"></a>

注册时，您将创建一个用于登录 Bitwarden 的主密码。您的主密码必须是：

* **易记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记您的主密码！**
* **强大**：保护账户的最佳方式是使用更长、更复杂、更不常见的密码。Bitwarden 提供了一个免费的[密码强度测试工具](https://bitwarden.com/password-strength/)，可以测试您正在考虑的一些易记的密码的强度。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2pST1WXY0Xk7GQ4GpwzELn/59b88f130a5d65b51c75bbe3a742a702/2024-12-02_10-20-39.png?_a=DAJCwlWIZAAB" %}
设置主密码
{% endembed %}

### 了解您的密码库 <a href="#get-to-know-your-vault" id="get-to-know-your-vault"></a>

Bitwarden Password Manager 网页 App 将列出您的所有密码库项目，包括[登录、支付卡、身份和安全笔记](../../../docs/password-manager/your-vault/vault-items/vault-items.md)：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2xTpSA11EOCzx8VIuVffcF/d3bc18e7fc3c3cb0bf1779fad9262cd3/2024-12-02_13-42-14.png?_a=DAJCwlWIZAAB" %}
Password Manager 网页 App
{% endembed %}

您可以通过网页 App 在密码库中填入需要保护的信息，整理您的凭据以便于访问，等等。您在任何 Bitwarden App 中添加的项目都会同步到您登录的其他 Bitwarden  App，因此您可以在任何地方登录账户。

### 导入您的数据 <a href="#import-your-data" id="import-your-data"></a>

您是否将密码保存在浏览器（如 Chrome 浏览器）中？或者您是从其他密码管理器来到 Bitwarden 的？ 您可以直接将登录信息导入到 Bitwarden，从而[避免了复制粘贴的痛苦](../../../docs/secrets-manager/import-export/import-data.md)。

或者，如果您将密码保存在纸上或脑中，让我们开始[添加更多项目到您的密码库](../../../docs/password-manager/getting-started/getting-started-webvault.md#first-steps)吧。

### 与您的家庭共享 <a href="#share-with-your-family" id="share-with-your-family"></a>

作为家庭成员，您可以与家庭成员安全共享诸如信用卡和登录凭据等信息。共享项目可通过一个独立的密码库访问，该密码库在您加入家庭时被添加到您的 Bitwarden App 中：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?_a=DAJCwlWIZAAB" %}
组织密码库
{% endembed %}

共享项目被组合成集合，家庭可根据谁具有访问权限的单元（如「仅限父母」）、包含的登录类型（如「流媒体登录」）等进行组织。

了解[如何与您的团队共享凭据](../../../docs/password-manager/organization-members/sharing.md)。

### 浏览网页时使用 Bitwarden <a href="#use-bitwarden-while-browsing" id="use-bitwarden-while-browsing"></a>

Bitwarden 浏览器扩展具有自动填充的魔力，使您可以轻松地使用已保存的密码快速登录您的账户。[下载](https://bitwarden.com/download/)浏览器扩展并了解在浏览网页时[如何自动填充密码](../../../docs/password-manager/autofill/autofill-from/autofill-from-browser-extensions.md)。

{% embed url="https://bitwarden.com/assets/1pamjhdWn7obh8UBxXcIPF/1841242fa5299a780d53f3ae70e546b3/screenshot_5.png?w=395&fm=avif" %}

{% embed url="https://vimeo.com/1084695614?fl=pl&fe=sh" %}

[此处](../../../docs/password-manager/getting-started/getting-started-browserext.md)了解更多有关浏览器扩展入门的信息。

* **00:11**：安装 Bitwarden
* **00:23**：固定扩展
* **00:32**：登录或创建账户
* **00:37**：禁用浏览器的密码管理器
* **00:50**：导入项目
* **01:11**：创建新项目
* **01:42**：附加字段
* **01:52**：使用文件夹
* **02:11**：收藏项目
* **02:17**：自动填充
* **02:39**：自动保存弹出窗口
* **02:45**：PIN 码和生物识别
* **02:58**：账户切换
* **03:07**：自定义 Bitwarden

最好[禁用浏览器的内置密码管理器](../../../docs/password-manager/getting-started/getting-started-browserext.md#disable-a-built-in-password-manager)，以确保 Bitwarden 始终是您的首选密码管理器。

#### Chrome

{% embed url="https://vimeo.com/1077612510?fl=pl&fe=sh" %}

#### Microsoft Edge

{% embed url="https://vimeo.com/1077612658?fl=pl&fe=sh" %}

### 随身携带 Bitwarden <a href="#take-bitwarden-on-the-go" id="take-bitwarden-on-the-go"></a>

安全无处不在！获取 Bitwarden 移动 App，这样您就可以在外出时安全地使用您的密码。[下载](https://bitwarden.com/download/)移动 App 并了解在 [iOS](../../../docs/password-manager/autofill/autofill-from/autofill-from-ios.md) 或 [Android](../../../docs/password-manager/autofill/autofill-from/autofill-from-android.md) 上如何自动填充密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/53OzJZ4klYWemxUepHMtq4/5ab47331f033259bd2e82817a99e992f/2025-01-21_15-22-10.png?_a=DAJCwlWIZAAB" %}
iOS 和 Android 上的 Bitwarden
{% endembed %}
{% endtab %}
{% endtabs %}

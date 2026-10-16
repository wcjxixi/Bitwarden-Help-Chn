# 共享项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/sharing/)
{% endhint %}

Bitwarden 提供了两种共享密码库项目的方式：将其添加到组织集合中，以便成员能够持续访问；或者创建一个链接，让任何人可以临时访问该项目内容的副本。本文将介绍这两种方式，帮助您根据接收者的实际需求选择最合适的方案。

* 使用[组织集合](sharing.md#organization-sharing)共享：使用集合共享，通过共享权限来给予组织成员对集合项目的持续访问权限。
* [通过链接](sharing.md#share-via-link)共享：通过链接共享会创建一个包含密码库项目副本的 Send。接收者可以在链接失效前查看此副本，但无法访问或更改原始项目。通过链接共享适用于浏览器扩展、桌面 App 和网页 App。

## 组织共享 <a href="#organization-sharing" id="organization-sharing"></a>

使用集合共享要求[组织](../../admin-console/organizations-overview.md)成员资格。使用 Bitwarden，共享项目意味着两件事：

* 将项目添加到一个[组织](../../admin-console/organizations-overview.md)。这将把项目的所有权转移给与您共享项目的组织。
* 将项目添加到一个或多个[集合](../../admin-console/manage-shared-items/collections/about-collections.md)。这些集合的**访问权限**设置决定了谁可以访问它。

使用集合共享要求组织成员资格。

### 共享新项目 <a href="#share-new-items" id="share-new-items"></a>

无论是向组织**添加项目**，还是向组织**导入项目**，您都可以从一开始就指定共享对象。您可以将项目添加或导入到任何拥有合适[权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)的集合中：

{% tabs %}
{% tab title="添加项目" %}
要从网页 App、浏览器扩展、移动端或桌面端添加新的共享项目：

1、在任何 Bitwarden App 的**密码库**视图中，选择 <i class="fa-plus">:plus:</i>**新增**按钮，然后选择所需的项目类型。

{% hint style="success" icon="lightbulb" %}
组织[所有者、管理员和某些自定义用户](../../admin-console/manage-members/member-roles.md)也可以直接从 **Admin Console** 执行此步骤，以跳过此过程中的一些步骤。
{% endhint %}

2、使用**所有者**下拉菜单选择希望此项目归属的组织。

3、使用**集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

4、填写项目的其他相关信息，然后选择**保存**完成共享。

{% hint style="info" %}
**提醒**：共享某个项目涉及将其所有权交给组织。管理团队应妥善管理[集合的权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)，因为拥有正确权限级别的成员有能力更改或删除已共享的项目。您可以通过项目名称旁边的徽标来判断该项目是否为共享项目：

<img src="https://bitwarden.com/assets/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?w=604&#x26;fm=avif&#x26;q=80" alt="" data-size="original">
{% endhint %}
{% endtab %}

{% tab title="导入项目" %}
向 Password Manager 导入项目时，可以直接导入到共享上下文。如果要导入的项目不止几个，建议参考[导入到组织](../../admin-console/manage-shared-items/import-organization-items/import-to-organization.md)一文。

1、导航至**工具** → **导入数据**。

{% hint style="success" %}
组织[所有者、管理员和某些自定义用户](../../admin-console/manage-members/member-roles.md)也可以直接从 **Admin Console** 执行此步骤，以跳过此过程中的一些步骤。
{% endhint %}

2、使用**密码库**下拉菜单选择希望此项目归属的组织。

3、使用**集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

4、选择**文件格式**然后选择**导入文件**。

5、选择**导入数据**以完成共享。

{% hint style="info" %}
**提醒**：共享某个项目涉及将其所有权交给组织。管理团队应妥善管理[集合的权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)，因为拥有正确权限级别的成员有能力更改或删除已共享的项目。您可以通过项目名称旁边的徽标来判断该项目是否为共享项目：

<img src="https://bitwarden.com/assets/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?w=604&#x26;fm=avif&#x26;q=80" alt="" data-size="original">
{% endhint %}
{% endtab %}
{% endtabs %}

### 共享现有项目 <a href="#share-existing-items" id="share-existing-items"></a>

您可能会发现，您当前拥有的项目需要与您组织中的其他成员共享。您可以在任何 Bitwarden App 中，与任何拥有合适[权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)的集合共享项目：

{% tabs %}
{% tab title="网页 App" %}
使用网页 App 是共享现有项目的最通用方法，可用于共享组织的全新项目，或简单地将更多集合添加到共享列表中：

1、在**密码库**视图中，使用复选框选择要共享的项目。

{% hint style="success" icon="lightbulb" %}
组织[所有者、管理员和某些自定义用户](../../admin-console/manage-members/member-roles.md)也可以直接从 **Admin Console** 执行此步骤，以跳过此过程中的一些步骤。
{% endhint %}

2、使用操作栏，选择**分配到集合**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/stm9byteqzZn9dvqonHrc/000099fa7e49dffd712f1c94b966fa09/assign_to_collections.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>分配到集合</p></figcaption></figure></div>

3、在**分配到集合**弹出窗口中：

* 使用**移动到组织**下拉菜单选择希望此项目归属的组织。
* 使用**选择要分配的集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

4、点击**分配**以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

前面介绍的方法是最通用、最简单的方法，不过还有其他一些共享您拥有访问权限的项目的方法：

* **从 Admin Console 共享**：如前所述，组织所有者、管理员和某些自定义用户可以直接从 Admin Console 进行共享，从而简化共享过程：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1u6EPNgAlCnvC9DcmUIosQ/e403afa9610a8fc26176d9f4223d8392/Assign_to_collections_in_bulk_edited.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>批量分配到集合</p></figcaption></figure></div>

* **直接编辑项目**：如果您需要在共享某个项目之前对其进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单选择要与之共享的对象，同时进行必要的更改：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/34zUaUOVRSXEv90fQiq5mD/e1e41fb5b40e3efcd974c770b101ad55/2025-01-28_10-40-03.png?w=1027&#x26;fm=avif" alt=""><figcaption><p>更改项目所有权</p></figcaption></figure></div>
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展共享现有项目：

1、在**密码库**视图中，使用 **≡**&#x9009;项菜单选择要共享的项目，然后选择**分配到集合**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7t3FoxPnpWGQAEzH1ERVDi/6c5622df8525848c0b4eb9bba330b70f/2024-12-02_15-32-47.png?w=1016&#x26;fm=avif" alt=""><figcaption><p>分配到集合</p></figcaption></figure></div>

2、在**分配到集合**弹出窗口中：

* 使用**移动到组织**下拉菜单选择希望此项目归属的组织。
* 使用**选择要分配的集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

3、点击**分配**以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

还有其他一些共享项目的方法：

* **直接编辑项目**：如果您需要在共享某个项目之前对其进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单选择要与之共享的对象，同时进行必要的更改：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/X73xPwnn5yKQtHhAC8U0H/480609793077866d21105593767d7448/2025-07-29_09-33-57.png?w=882&#x26;fm=avif" alt=""><figcaption><p>编辑共享</p></figcaption></figure></div>
{% endtab %}

{% tab title="移动端" %}
要从移动 App 共享现有项目：

1. 点击要共享的密码库项目，以显示**查看项目**面板。
2. 点击 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i> 选项菜单，然后选择**移动到组织**选项。
3. 在**移动到组织**面板上：
   * 使用**组织**下拉菜单选择希望此项目归属的组织。
   * 使用**集合**选择器选择要与之共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。
4. 点击移动以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

还有其他一些共享项目的方法：

* **直接编辑项目**：如果您需要在共享某个项目之前对其进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单选择要与之共享的对象，同时进行必要的更改。
{% endtab %}

{% tab title="桌面端" %}
要从桌面 App共享现有项目：

1、在**密码库**视图中，右键单击要共享的项目，然后从操作栏中选择**分配到集合**：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2RRhv9udtSa49Uxzv6rRAQ/e5b579af047113cf7ea1eb60bbbb533e/2026-07-15_11-18-04.png?w=1308&#x26;fm=avif" alt=""><figcaption><p>分配到集合</p></figcaption></figure></div>

2、在**分配到集合**弹出窗口中：

* 使用**移动到组织**下拉菜单选择希望此项目归属的组织。
* 使用**选择要分配的集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

3、点击**分配**以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

还有其他一些共享项目的方法：

* **直接编辑项目**：如果您需要在共享某个项目之前对其进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单选择要与之共享的对象，同时进行必要的更改：

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4U6pHkqLgt3miuwFLJ9tkH/caeb931f14a8a6b10ba7e299a705e083/2026-04-23_11-41-17.png?w=800&#x26;fm=avif" alt=""><figcaption><p>编辑共享</p></figcaption></figure></div>
{% endtab %}

{% tab title="CLI" %}
要移动项目，请使用以下命令：

```bash
bw move <itemid> <organizationid> [encodedJson]
```

其中：

* `itemid` 代表项目的唯一标识符。
* `Organizationid` 代表要将项目移动到的组织的唯一标识符。

更多详情，请参阅 Bitwarden [CLI 文档](../developer-tools/cli/password-manager-cli.md#move)。
{% endtab %}
{% endtabs %}

### 项目共享后 <a href="#after-items-are-shared" id="after-items-are-shared"></a>

{% hint style="info" %}
**提醒**：共享某个项目涉及将其所有权交给组织。管理团队应妥善管理[集合的权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)，因为拥有正确权限级别的成员有能力更改或删除已共享的项目。您可以通过项目名称旁边的徽标来判断该项目是否为共享项目：

<img src="https://bitwarden.com/assets/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?w=604&#x26;fm=avif" alt="" data-size="original">
{% endhint %}

### 收回共享项目的所有权 <a href="#reclaimed-shared-item-ownership" id="reclaimed-shared-item-ownership"></a>

拥有项目所存储的集合的[管理集合权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)的用户可以选择停止与组织共享项目：

1. 使用项目的 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i> 选项菜单然后选择**克隆**，以克隆该项目。
2. 在**添加项目**面板上，使用**所有者**下拉菜单选择您的账户电子邮箱。这将确保项目被克隆到非共享上下文中。
3. **保存**克隆的项目。
4. 使用项目的 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i> 选项菜单然后选择**删除**，以删除原始项目。

请注意，在某些情况下，将项目移动到具有更高访问控制限制的集合中，或移动到只有您才能访问的集合中，可能比直接从组织中移除项目更有效。

## 通过链接共享 <a href="#share-via-link" id="share-via-link"></a>

使用**通过链接共享**，以授予他人对密码库项目副本的临时访问权限，而原始项目仍保留在您的密码库中。通过链接共享会创建一个包含项目内容的 [Send](../bitwarden-send/about-send.md)，您可以通过任何渠道分享该 Send。通过链接共享适用于[高级版用户](../../plans-and-pricing/password-manager/about-bitwarden-plans.md)或付费版组织（家庭版、团队版或企业版）的成员。此外，组织管理员可以使用管理 Send 和共享策略来配置此功能的访问权限。

{% hint style="info" %}
**通过链接共享**不适用于 SSH 密钥项目、归档中的项目和回收站中的项目。要共享已归档或已删除的某个项目，请先将其取消归档或从回收站中恢复。要共享一个或多个集合中的某个项目，您需要至少其中一个集合的编辑权限。
{% endhint %}

要与一个或多个不需要持续访问组织集合的人员共享密码库中的项目：

1、选择要共享的项目的 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i> 菜单，然后选择**通过链接共享**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7LURUsVmunZxNFPjWwXAJn/fc31a656e4ec94b6fa6f7aa37648b1fa/web_share_link.png?w=800&#x26;fm=avif" alt=""><figcaption><p>通过链接共享</p></figcaption></figure></div>

2、输入接收者的电子邮箱地址。如果发送给多个接收者，使用逗号分隔电子邮箱地址：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/3vTrnas77a2ZHgWOBu65Xc/ecf1b5c7761351eb9adf207805c00f43/share_link_menu_web_app.png?w=800&#x26;fm=avif" alt=""><figcaption><p>通过链接共享菜单</p></figcaption></figure></div>

3、配置共享规则：

* **链接有效期**：选择链接的有效时长。

{% hint style="info" %}
过期日期仅影响共享链接本身。如果接收者在链接有效期间保存了共享的密码库项目，即使链接过期，他们仍然可以访问该项目。
{% endhint %}

* **一次性共享**：仅允许链接打开一次。

4、准备好共享链接后，选择**复制链接**然后将其粘贴到您首选的沟通渠道中。之前生成的链接将显示在**活动链接**列表中。

### 编辑密码库项目共享 <a href="#edit-a-vault-item-share" id="edit-a-vault-item-share"></a>

创建链接后，您可以对其进行编辑，以更改其设置或添加选项：

1. 导航至 **Send** 页面，然后选择共享的密码库项目。
2. 选择**编辑**。

编辑密码库项目共享时，您可以配置共享链接的其他设置：

* **最大访问次数**：配置链接可以访问的次数。
* **对接收者隐藏我的电子邮箱地址**：选择此选项将在接收者打开共享链接时隐藏发送者的电子邮箱地址。
* **私密备注**：将任何其他私密备注添加到此 Send。

{% hint style="info" %}
**通过链接分享**发送的项目副本与创建链接时相同。之后对原始项目的任何编辑都不会更新接收者的副本。
{% endhint %}

### 从共享链接接收项目 <a href="#receive-an-item-from-a-shared-link" id="receive-an-item-from-a-shared-link"></a>

当您收到共享的项目链接时：

1、打开此链接，输入您的电子邮箱地址，然后选择**发送验证码**。您的电子邮箱地址必须与发送者输入的电子邮箱地址一致才能收到验证码。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4TYGXZJtn13F7PZzULJ5IY/d3fc9be6b3c299f7ffa002c2472b8685/enter_email_receive_send.png?w=800&#x26;fm=avif" alt=""><figcaption><p>输入电子邮箱地址进行验证</p></figcaption></figure></div>

2、收到验证码后，请将其输入到**验证码**字段中。

3、验证码通过后，您可以复制该项目的内容以供使用，或将其粘贴到您的密码库的新项目中长期存储。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/7g7mG243hYSCQDrmUMP6dv/7d7f8594e7cdd233b30920af1d8a9eba/Share_with_link_content.png?w=800&#x26;fm=avif" alt=""><figcaption><p><strong>通过链接分享的内容</strong></p></figcaption></figure></div>

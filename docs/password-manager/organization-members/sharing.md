# 共享项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/sharing/)
{% endhint %}

使用 Bitwarden，共享一个项目意味着两件事：

* 将项目添加到一个[组织](../../admin-console/organizations-overview.md)。这将把项目的所有权转移给与您共享项目的组织。
* 将项目添加到一个或多个[集合](../../admin-console/manage-shared-items/collections/about-collections.md)。这些集合的**访问权限**设置决定了谁可以访问它。

使用 Bitwarden 共享项目有许多不同的方法。在本文中，我们将介绍这些方法。无论哪种方法最适合您的工作流程，请记住您需要成为组织的成员才能共享。

## 共享新项目 <a href="#share-new-items" id="share-new-items"></a>

无论是向组织**添加项目**，还是向组织**导入项目**，您都可以从一开始就指定共享对象。您可以将项目添加或导入到任何拥有合适[权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)的集合中：

{% tabs %}
{% tab title="添加项目" %}
要从网页 App、浏览器扩展、移动端或桌面端添加新的共享项目，请执行以下操作：

1、在任何 Bitwarden App 的**密码库**视图中，选择 **✚新增**按钮，然后选择所需的项目类型。

{% hint style="success" %}
组织[所有者、管理员和某些自定义用户](../../admin-console/manage-members/member-roles.md)也可以直接从**管理控制台**执行此步骤，以跳过此过程中的一些步骤。
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
组织[所有者、管理员和某些自定义用户](../../admin-console/manage-members/member-roles.md)也可以直接从**管理控制台**执行此步骤，以跳过此过程中的一些步骤。
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

## 共享现有项目 <a href="#share-existing-items" id="share-existing-items"></a>

您可能会发现，您当前拥有的项目需要与您组织中的其他成员共享。您可以在任何 Bitwarden App 中，与任何拥有合适[权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)的集合共享项目：

{% tabs %}
{% tab title="网页 App" %}
使用网页 App 是共享现有项目的最通用方法，可用于共享组织的全新项目，或简单地将更多集合添加到共享列表中：

1、在**密码库**视图中，使用复选框选择要共享的项目。

{% hint style="success" %}
组织[所有者、管理员和某些自定义用户](../../admin-console/manage-members/member-roles.md)也可以直接从**管理控制台**执行此步骤，以跳过此过程中的一些步骤。
{% endhint %}

2、使用 **≡**&#x83DC;单，选择**分配到集合**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/stm9byteqzZn9dvqonHrc/0da481b0cf1f54457d08ae02fd917377/2024-12-02_14-33-34.png?_a=DAJCwlWIZAAB" %}
分配到集合
{% endembed %}

3、在**分配到集合**弹出窗口中：

* 使用**移动到组织**下拉菜单选择希望此项目归属的组织。
* 使用**选择要分配的集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

4、点击**分配**以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

前面介绍的方法是最通用、最简化的方法，不过您还可以使用其他一些共享方法：

* **从管理控制台共享**：如前所述，组织所有者、管理员和某些自定义用户可以直接从管理控制台进行共享，从而简化共享过程：

{% embed url="https://bitwarden.com/assets/1u6EPNgAlCnvC9DcmUIosQ/327c0c24e09dce687540499a8eaa5aac/2024-12-02_15-47-21.png?w=1200&fm=avif&q=80" %}
批量分配到集合
{% endembed %}

* **直接编辑项目**：如果需要在共享之前对个人项目进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单，在进行必要更改时选择与谁共享：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/34zUaUOVRSXEv90fQiq5mD/e1e41fb5b40e3efcd974c770b101ad55/2025-01-28_10-40-03.png?_a=DAJCwlWIZAAB" %}
更改项目所有权
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展共享现有项目：

1、在**密码库**视图中，使用 **≡**&#x9009;项菜单选择要共享的项目，然后选择**分配到集合**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7t3FoxPnpWGQAEzH1ERVDi/6c5622df8525848c0b4eb9bba330b70f/2024-12-02_15-32-47.png?_a=DAJCwlWIZAAB" %}
浏览器扩展分配到集合
{% endembed %}

2、在**分配到集合**弹出窗口中：

* 使用**移动到组织**下拉菜单选择希望此项目归属的组织。
* 使用**选择要分配的集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

3、点击**分配**以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

还有其他一些共享项目的方法：

* **直接编辑项目**：如果需要在共享之前对个人项目进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单，在进行必要更改时选择与谁共享：

{% embed url="https://bitwarden.com/assets/X73xPwnn5yKQtHhAC8U0H/480609793077866d21105593767d7448/2025-07-29_09-33-57.png?w=882&fm=avif&q=80" %}
在浏览器上编辑共享
{% endembed %}
{% endtab %}

{% tab title="移动 App" %}
要从移动 App 共享现有项目：

1. 点击要共享的密码库项目，以显示**查看项目**面板。
2. 点击 **≡**&#x9009;项菜单，然后选择**移动到组织**选项。
3. 在**移动到组织**面板上：
   * 使用**组织**下拉菜单选择希望此项目归属的组织。
   * 使用**集合**选择器选择要与之共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。
4. 点击移动以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

还有其他一些共享项目的方法：

* **直接编辑项目**：如果需要在共享之前对个人项目进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单，在进行必要更改时选择与谁共享。
{% endtab %}

{% tab title="桌面 App" %}
要从桌面 App共享现有项目：

1、在**密码库**视图中，右键单击要共享的项目，然后从菜单中选择**分配到集合**：

{% embed url="https://bitwarden.com/assets/2RRhv9udtSa49Uxzv6rRAQ/578b56235e63558046f0b52d9095707c/2025-07-29_09-22-41.png?w=1085&fm=avif&q=80" %}
从桌面共享
{% endembed %}

2、在**分配到集合**弹出窗口中：

* 使用**移动到组织**下拉菜单选择希望此项目归属的组织。
* 使用**选择要分配的集合**下拉菜单选择要共享此项目的集合。在这些集合上设置的**访问权限**设置将决定谁可以访问该项目。

3、点击**分配**以完成共享。

### 更多共享方法 <a href="#more-methods-for-sharing" id="more-methods-for-sharing"></a>

还有其他一些共享项目的方法：

* **直接编辑项目**：如果需要在共享之前对个人项目进行更改，请打开该项目，然后在**编辑**视图中使用**所有者**和**集合**下拉菜单，在进行必要更改时选择与谁共享：

{% embed url="https://bitwarden.com/assets/4U6pHkqLgt3miuwFLJ9tkH/21a99fb65ad0fa94d3f0693c3a10382c/2025-07-29_09-25-53.png?w=1086&fm=avif&q=80" %}
在浏桌面端编辑共享
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
要移动项目，请使用以下命令：

```shellscript
bw move <itemid> <organizationid> [encodedJson]
```

其中：

* `itemid` 代表项目的唯一标识符。
* `Organizationid` 代表要将项目移动到的组织的唯一标识符。

更多详情，请参阅 Bitwarden [CLI 文档](../developer-tools/cli/password-manager-cli.md#move)。
{% endtab %}
{% endtabs %}

## 项目共享后 <a href="#after-items-are-shared" id="after-items-are-shared"></a>

{% hint style="info" %}
**提醒**：共享某个项目涉及将其所有权交给组织。管理团队应妥善管理[集合的权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)，因为拥有正确权限级别的成员有能力更改或删除已共享的项目。您可以通过项目名称旁边的徽标来判断该项目是否为共享项目：

<img src="https://bitwarden.com/assets/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?w=604&#x26;fm=avif&#x26;q=80" alt="" data-size="original">
{% endhint %}

### 回收共享项目的所有权 <a href="#reclaimed-shared-item-ownership" id="reclaimed-shared-item-ownership"></a>

拥有项目所存储的集合的[管理集合权限](../../admin-console/manage-shared-items/collections/collection-permissions.md)的用户可以选择停止与组织共享项目：

1. 使用项目的 **≡**&#x9009;项菜单然后选择**克隆**，以克隆该项目。
2. 在**新建项目**面板上，使用**所有者**下拉菜单选择您的账户电子邮箱。这将确保项目被克隆到非共享上下文中。
3. **保存**克隆的项目。
4. 使用项目的 **≡**&#x9009;项菜单然后选择**删除**，以删除原始项目。

请注意，在某些情况下，将项目移动到具有更高访问控制限制的集合中，或移动到只有您才能访问的集合中，可能比直接从组织中移除项目更有效。

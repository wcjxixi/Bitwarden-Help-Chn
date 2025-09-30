# =共享项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/sharing/)
{% endhint %}

使用 Bitwarden，共享一个项目意味着两件事：

* 将项目添加到一个[组织](../admin-console/organizations-overview.md)。这将把项目的所有权转移给与您共享项目的组织。
* 将项目添加到一个或多个[集合](../admin-console/manage-shared-items/collections/about-collections.md)。这些集合的**访问权限**设置决定了谁可以访问它。

使用 Bitwarden 共享项目有许多不同的方法。在本文中，我们将介绍这些方法。无论哪种方法最适合您的工作流程，请记住您需要成为组织的成员才能共享。

## 共享新项目 <a href="#share-new-items" id="share-new-items"></a>

## 共享现有项目 <a href="#share-existing-items" id="share-existing-items"></a>

组织成员可以将项目移动到任何已分配的集合，除非他们被赋予了此集合的[可以查看](../admin-console/manage-members/member-roles.md#permissions)权限。要移动项目到组织：

{% tabs %}
{% tab title="网页 App" %}
从网页 App 将项目移动到组织有两种方法：

## 分配到集合 <a href="#assign-to-collections" id="assign-to-collections"></a>

此方法最适合与某个组织共享多个项目，前提是您不需要对任何项目的属性或值进行更改：

1、选择要分配给组织集合的项目。

2、使用 **≡**&#x83DC;单，选择**分配到集合**选项：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/stm9byteqzZn9dvqonHrc/0da481b0cf1f54457d08ae02fd917377/2024-12-02_14-33-34.png?_a=DAJCwlWIZAAB" %}
分配到集合
{% endembed %}

3、在**分配到集合**界面：

* 选择您要与之共享此项目的组织。
* 选中一个或多个集合，以将此项目共享到其中。您必须至少选择一个集合。

4、点击**分配**以完成移动此项目以进行共享。

## 更改项目所有权 <a href="#change-item-ownership" id="change-item-ownership"></a>

此方法最适合共享单个项目，而且您还需要在共享之前对其进行更改：

1、打开要更改所有权的项目，然后选择**编辑**按钮。

2、从所有者下拉菜单中，选择打算拥有此项目的组织：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/34zUaUOVRSXEv90fQiq5mD/e1e41fb5b40e3efcd974c770b101ad55/2025-01-28_10-40-03.png?_a=DAJCwlWIZAAB" %}
更改项目所有权
{% endembed %}

3、选择该密码库项目应包含在哪个（些）集合中。您必须至少选择一个集合。

4、对密码库项目进行其他必要更改，然后选择**保存**。
{% endtab %}

{% tab title="浏览器扩展" %}
1、在**密码库**视图中，使用您要移动到组织的项目的 **≡选项**菜单，然后选择**分配到集合**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7t3FoxPnpWGQAEzH1ERVDi/6c5622df8525848c0b4eb9bba330b70f/2024-12-02_15-32-47.png?_a=DAJCwlWIZAAB" %}
浏览器扩展分配到集合
{% endembed %}

2、在**分配到集合**界面：

* 选择您要与之共享此项目的组织。如果您只加入了一个组织，则无法更改。
* 选中一个或多个集合，以将此项目共享到其中。您必须至少选择一个集合。
{% endtab %}

{% tab title="桌面 App" %}
1. 选择要移动到组织的项目。
2. 选择要移动的密码库项目的 **✏️编辑**图标。
3. 选择 **→移动**按钮。
4. 在**移动到组织**界面：
   * 选择您要与之共享此项目的组织。
   * 选中一个或多个集合，以将此项目共享到其中。您必须至少选择一个集合。
{% endtab %}

{% tab title="移动 App" %}
1. 选择要移动到组织的项目。
2. 选择屏幕右上角的 **≡选项**菜单。
3. 选择 **→移动到组织**选项。
4. 在**移动到组织**界面：
   * 选择您要与之共享此项目的组织。
   * 选中一个或多个集合，以将此项目共享到其中。您必须至少选择一个集合。
{% endtab %}

{% tab title="CLI" %}
要移动项目，请使用以下命令：

```batch
bw move <itemid> <organizationid> [encodedJson]
```

其中：

* `itemid` 代表项目的唯一标识符。
* `Organizationid` 代表要将项目移动到的组织的唯一标识符。

更多详情，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/cli/password-manager-cli.md#move)。
{% endtab %}
{% endtabs %}

## 项目共享后 <a href="#after-items-are-shared" id="after-items-are-shared"></a>

{% hint style="info" %}
**提醒**：共享某个项目涉及将其所有权交给组织。管理团队应妥善管理[集合的权限](../admin-console/manage-shared-items/collections/collection-permissions.md)，因为拥有正确权限级别的成员有能力更改或删除已共享的项目。您可以通过项目名称旁边的徽章来判断该项目是否为共享项目：

<img src="https://bitwarden.com/assets/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?w=604&#x26;fm=avif&#x26;q=80" alt="" data-size="original">
{% endhint %}

### 回收共享项目的所有权 <a href="#reclaimed-shared-item-ownership" id="reclaimed-shared-item-ownership"></a>

拥有项目所存储的集合的[管理集合权限](../admin-console/manage-shared-items/collections/collection-permissions.md)的用户可以选择停止与组织共享项目：

1. 使用项目的 **≡**&#x9009;项菜单然后选择**克隆**，以克隆该项目。
2. 在**新建项目**面板上，使用**所有者**下拉菜单选择您的账户电子邮箱。这将确保项目被克隆到非共享上下文中。
3. **保存**克隆的项目。
4. 使用项目的 **≡**&#x9009;项菜单然后选择**删除**，以删除原始项目。

请注意，在某些情况下，将项目移动到具有更高访问控制限制的集合中，或移动到只有您才能访问的集合中，可能比直接从组织中移除项目更有效。

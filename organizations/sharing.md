# 共享

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/sharing/)
{% endhint %}

{% hint style="info" %}
要共享项目，您需要是组织的成员。了解更多关于[组织](organizations.md)或了解如何[创建自己的两个人的组织](../admin-console/organizations-quick-start.md)。
{% endhint %}

使用 Bitwarden 共享项目意味要着将它们移动到组织和集合中，集合是用于将共享的项目、笔记、支付卡和身份集中到一起，以供多个用户访问的一种结构。您可以通过几种不同的方式创建用于共享的组织项目：

## 移动项目到组织 <a href="#move-an-item-to-an-organization" id="move-an-item-to-an-organization"></a>

组织成员可以将项目移动到任何已分配的集合，除非他们被赋予了此集合的[可以查看](../admin-console/user-management/member-roles-and-permissions.md#permissions)权限。要移动项目到组织：

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

## 项目共享后 <a href="#once-an-item-is-shared" id="once-an-item-is-shared"></a>

将项目移动到某个组织**会将所有权转移到该组织**。这意味着任何有权限的人都可以更改或删除该项目，它也将其从您的密码库中删除。您可以通过项目名称旁边的卡片来判断该项目是否为共享项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?_a=DAJCwlWIZAAB" %}
已共享的项目图标
{% endembed %}
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

更多详情，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/password-manager-cli.md#move)。
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
将项目移动到某个组织会将所有权转移该组织。组织中拥有适当[权限](../admin-console/user-management/member-roles-and-permissions.md#permissions)的任何人都可以编辑或删除该项目，删除此项目将导致原所有者的项目也被删除。
{% endhint %}

## 创建组织项目 <a href="#create-an-organization-item" id="create-an-organization-item"></a>

组织成员可以直接为任何已分配的集合创建新的项目，除非他们被赋予了此集合的[可以查看](../admin-console/user-management/member-roles-and-permissions.md#permissions)权限。要从网页密码库创建组织拥有的项目：：

{% tabs %}
{% tab title="我的密码库视图" %}
要创建一个新的共享项目：

1. 在**密码库**页面，选择 **🞤新增**按钮然后选择所需的项目类型。
2. 为这个新的密码库项目填写所有相关信息。
3. 在添加项目面板顶部的**所有权**部分，选择要与之共享此项目的组织。
4. 选中一个或多个集合，以将此项目共享到其中。您必须至少选择一个集合。
5. 点击**保存**以完成共享项目的创建。

创建一个共享项目**将把所有权设置为这个组织**。这意味着任何有权限的人都可以更改或删除该项目，这也将从您的密码库中移除该项目。您可以通过项目名称旁边的卡片来判断该项目是否为共享项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?_a=DAJCwlWIZAAB" %}
已共享的项目图标
{% endembed %}
{% endtab %}

{% tab title="组织视图" %}
要创建一个新的共享项目：

1. 在您的组织的 **🔒密码库**选项卡，选择**新建**按钮并从下拉列表中选择项目类型。
2. 为这个新的密码库项目填写所有相关信息。
3. 使用此方式时，项目的所有权会自动设置为组织，因此您所要做的就是选中一个或多个集合，以将此项目共享到其中。您必须至少选择一个集合。
4. 点击**保存**以完成共享项目的创建。

创建一个共享项目**将把所有权设置为这个组织**。这意味着任何有权限的人都可以更改或删除该项目，这也将从您的密码库中移除该项目。您可以通过项目名称旁边的卡片来判断该项目是否为共享项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6tnBV4hUxUNtWvGNAp8eua/215f54e0a26f5a1b2d41e18119fdcd71/2024-12-02_15-31-38.png?_a=DAJCwlWIZAAB" %}
已共享的项目图标
{% endembed %}
{% endtab %}
{% endtabs %}

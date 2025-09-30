# 关于集合

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/about-collections/)
{% endhint %}

集合汇集了从组织内[安全共享](../../../organizations/sharing.md)的登录、笔记、支付卡和身份信息。集合可以由任何组织类型创建和管理。集合是[文件夹](../../../your-vault/folders.md)的组织等效物，但有几个关键的区别：

* 组织可以定义对集合的访问权限，允许用户或[群组](../../manage-members/groups.md)仅能访问他们所需的项目。
* 存储在组织集合中的项目不属于任何个人用户，而是属于组织。
* 组织所拥有的项目**必须**至少被包括在一个集合中。

组织成员可以在**密码库**视图中找到共享项目和个人项目，还可以使用多种方法筛选项目列表，以仅显示组织项目或特定集合中的项目，例如在网页 App 中：

{% embed url="https://bitwarden.com/assets/4D2tlh9YKPzDY20SYGVKcG/dff56b66549d29405b1af211860f698e/2024-12-03_14-07-28.png?w=1197&fm=avif&q=80" %}
组织密码库
{% endembed %}

## 嵌套集合 <a href="#nested-collections" id="nested-collections"></a>

在创建集合时，集合可以被「嵌套」，以方便在您的组织中逻辑地组织它们。嵌套集合**仅用于显示目的**。嵌套的集合不会从他们的「父」集合中继承项目、访问或权限。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7EXnVptHEKQkSfKY1FsOmI/d012cd9d0d414528bfbd267d25f04a6f/Screenshot_2024-02-27_at_10.56.41_AM.png?_a=BAJFJtWIB" %}
嵌套的集合
{% endembed %}

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 从概念层面[了解集合](about-collections.md)。
* 通过新的集合[与组织成员共享项目](../../../organizations/sharing.md)。
* 为新集合[分配群组和成员访问权限](assign-users-to-collections.md)。
* 为集合[配置群组和成员权限](collection-permissions.md)。
* 为组织[配置集合管理设置](collection-settings.md)。

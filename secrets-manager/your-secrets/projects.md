# 工程

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/projects/)
{% endhint %}

工程是按逻辑组合在一起的[机密](secrets.md)的集合，由您的 DevOps 和网络安全团队对其进行访问权限的管理。您的用户账户有权访问的工程列在主要的 Secrets Manager 视图中，也可以通过从导航中选择**工程**来列出：

{% embed url="https://bitwarden.com/_gatsby/image/be01e421b3a70b1813b335da8b6a4155/e681e48097835dcdff2f106983d95d69/Screen%20Shot%202023-03-22%20at%209.44.51%20AM.webp?eu=8a8a55e6b2ccaa8e0b6da587687a656ee63702f9f65262d63e31edfa46fbcad52df04b5021c672b72b6c538ad2b147b966c57b621ce7d88f92b519f5ee33ad01018408ed6eb77000592dcda8e3a705403ac31850f0879c01f53f788ca1f7f733134f0372f52befd4afb76620e6d26c71bff2e5303b97ef67e75000078d4270aa6ce6d7d92c19ef92d9799d99badf7fb4cfb66843129eab642b2c4d005bef2bb9a0ba57763d28415334c9ab0cc56496b66a4a61260a5701a1616bd600e40f6281b1aeff32ba2224a5c7cb317285deae83f018ae4527a3a02eb7863f640b0cc362d0a23ba985&a=w%3D850%26h%3D320%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A45%3A13.968Z" %}
工程
{% endembed %}

打开一个工程将列出与其相关联的**机密**、**人员**和**服务账户**：

{% embed url="https://bitwarden.com/_gatsby/image/4a8729f679afad48f632b4b4c93300ba/e681e48097835dcdff2f106983d95d69/Screen%20Shot%202023-03-22%20at%209.44.47%20AM.webp?eu=dd8f04b4e4c9a8d50a61a1836c27623db33751fdf60737d23d63e3fc1afa96802cfb485774932eb07a3d58ded3b245ba61c5296648ead58ec2b510a1ea32ab0a07830eba33e52653072fc2a8b1f357423c94180ca18bc80ef7687681e0e2bd285d145c68a265a7d8b1f86231f39d7c76bce7e56d3086e866be471a4bcc5a2faf22e191883b43a9c9af1896ba94c841c4d5bf65423fdea5635305116411ac79a4a1b056273f7b4808309cfc5ece3794b13c4e34265b5a50f76668d007ff6833cbfb98f21f8c2f258ecb916e34e9c1ae82ee07ac296be5cd48f8c654731009a80da9bb1486af7a4650d6&a=w%3D850%26h%3D320%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A45%3A28.422Z" %}
工程内部
{% endembed %}

## 创建工程 <a href="#create-a-project" id="create-a-project"></a>

要创建一个新的工程：

1、使用**新增**下拉菜单选择**工程**：

{% embed url="https://bitwarden.com/_gatsby/image/9ec307c2cd6c1b17138196203755eb3e/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.31.44%20PM.webp?eu=8add57e4e29afbd35d6ea38b3a746261e16e52f9ab5262d53b61ecab47acc88470f3115c76c12cb1793853ded6b645ba31c171634ae886d8c0bd1aa2b83ca25e51830fec35b52402577f95adb6f104146fc14b0ea5879b00a0387581b4e1e6774d571923fa73b185e9ae3736b8d57a60ece5a47d31c6ab2ee511540c8f5c31bf6ea48f876e4fb99bf301bca2b8f84a8ec9a36e191e8eb72a2535124c1eb72cedadef4376262a172c62bdc63cc712c1d53f611a52000878833865ac4aaa3d31caedf2a65b88287ab0abcd30238792a6d3ea1bf82f72b5ce24fcd03878116eff51f8e92598b13c594aee28fa974faf030728428673d8604fdb265c8d1980e528f355e22e7861&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.727Z" %}
创建工程
{% endembed %}

2、输入**工程名称**。您可以随时使用「工程」页面上的 (**≡**) 选项菜单更改工程名称。

3、选择**保存**按钮。

## 添加机密到工程 <a href="#add-secrets-to-a-project" id="add-secrets-to-a-project"></a>

{% tabs %}
{% tab title="添加现有的机密" %}
要将现有机密添加到您的工程：

1. 导航到「机密」视图然后选择要添加的机密。
2. 在「编辑机密」窗口中，打开「工程」选项卡然后输入或选择要与机密关联的工程。每一个机密一次只能与一个工程相关联。
3. 完成后，选择**保存**按钮。
{% endtab %}

{% tab title="添加已有的机密" %}
要为您的工程创建新的机密：

1、使用**新增**下拉菜单选择**机密**：

{% embed url="https://bitwarden.com/_gatsby/image/8af613589a3b92f196f52d537516d9ba/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.33.39%20PM.webp?eu=dbd802b3eacafe825c6fa1823b746769b36c05f8fa523e846e32b1fd1dab9c8624f71b5c29967ab0243c09d6d1b44ae862c02a681cba86d2c0e81afde935f85a50d75bed6fb0250e5022c1ffb5a103443a90180ba187ce5da13f7ad2e7e5b5214f551c2ef973b2d9a8ed7527ba9c306bb7e7f17b26dcf83cb6431d179e5c32e23aeed4c1345cb09df645eeb0e6f44eca83e4687213b1f442270b4e7b229029daf2cf5907532d3844649ba95e953492e03514612a0c0c02a2613dd600ad6862c6b6f2f20f8f7f7ce9b7aa6232d396f0ef8e42f36e19e5cf25aa9f3b78130fa87cfcf814f5cc670510822395f531ac435b62&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.762Z" %}
创建机密
{% endembed %}

2、在「新增机密」窗口的名称/值对选项卡上，输入**名称**和**值**。可选添加**备注**。

3、选择「工程」选项卡然后输入或选择要与机密关联的工程。几个关键点。

* 只有有权访问该工程的组织成员才能查看或操作此机密。
* 只有有权访问该工程的服务账户才能创建注入此机密的途径。
* 每一个机密一次只能与一个工程相关联。

4、完成后，选择**保存**按钮。
{% endtab %}
{% endtabs %}

## 添加人员到工程 <a href="#add-people-to-a-project" id="add-people-to-a-project"></a>

将组织成员添加到您的工程将允许这些人与此工程的机密进行交互。要将人员添加到您的工程：

1、在「工程」中，选择**人员**选项卡。

2、从「人员」下拉列表中，键入或选择要添加到工程的成员或群组。选择合适的人员后，选择**添加**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/e9bb73e3052de06a4e8b28867b6975e5/e681e48097835dcdff2f106983d95d69/Screen%20Shot%202023-03-22%20at%209.44.33%20AM.webp?eu=898a59e5b6c8f4810b6da8813b75693be16b51faac5337d13532b0ae1efccd8224a61f5326962fe72b6e53d6dae147e833c12d6719e6848e96b918f6ed64a90100865bb835e77003502fc5adb7f1524261c4120ba6d5cd5cab6575d4e3b4e5244f56157ffc2bba85eeae3f3cf4c76f71e0a9b9773893fc2da30c0d109d4932bf31ffd3c06d4baad1b75db1b5a8f3089b94ba6a005fdf95702b30096d0ce57eeed0f8032b602e26596eb6c547c0619eb23e186420575857f460388103ad3f32c3ecf9a2088f2c73e0ab9b337099a0fdc2b84ff24515bf9063c6803b780d10ac10b0be7998832069079f2efe8b4fb16c74485ec242de&a=w%3D850%26h%3D320%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A44%3A53.961Z" %}
将人员添加到工程
{% endembed %}

3、将成员或群组添加到工程后，为这些成员或群组设置**权限**级别。成员和群组可以具有以下权限级别之一：

* **可以读取**：成员/群组将能够查看此工程中的现有机密。
* **可以读取、写入**：成员/群组将能够查看此工程中的现有机密，以及在此工程中创建新的机密。

## 添加服务账户到工程 <a href="#add-service-accounts-to-a-project" id="add-service-accounts-to-a-project"></a>

您可以将新的和现有的[服务账户](service-accounts.md)添加到工程中：

{% tabs %}
{% tab title="添加现有的服务账户" %}
要将现有服务账户添加到您的工程：

1、在「工程」中，选择**服务账户**选项卡。

2、从「服务账户」下拉列表中，键输入或选择要添加到工程的服务账户。选择正确的服务账户后，选择**添加**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/58a53eab30d34ef88d67d58e45ecf470/a0c0982145c3a7fab9286d7eb4a4e79a/Screen%20Shot%202023-02-24%20at%202.48.06%20PM.webp?eu=d8dd51b4e7c8fc8f0f6fa182617a3269b63701aefc0733d83d30e3fc19fa9c8672f41d5121c17db72f3d098dd3b244e834c270334dba81d2c9b51ca7e967ad0a518a5dbb66e07900022dc1f8e1a450426192485bf287c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bbae9a44d6beab2c36092a78fea78b0ee8e5679459ba62a2325481b0bbb25e8f0e702223d7c135c34c7fb0b953397e33f1462235c5e01f178598317ae396fac87a3fe19b6787be3abd431729bc1aaefbc5ec32868e3c739a984541a7313ec4dfa&a=w%3D850%26h%3D268%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.614Z" %}
添加服务账户
{% endembed %}

{% hint style="info" %}
对于测试版，服务账户将被限制为对工程的只读访问权限。
{% endhint %}
{% endtab %}

{% tab title="添加已有的服务账户" %}
要为此工程添加服务账户：

1、使用新**新增**下拉菜单选择**服务账户**：

{% embed url="https://bitwarden.com/_gatsby/image/9b5074ec4c99b594233e0c1540706f8f/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.33.47%20PM.webp?eu=8d8853efe69badd1076da6d76d263661b16e04a8ff046085696de7af1dfe9ed277f11f0728962eb2246c0eddd1e747be36927b691fecd0d894ed18a6b834fc01578458ec6ee07107512cc3fee5a453443ace4e59f0d6ca0dab6c74d3b1b7b67510571c2eaa2cb8d3e6f17120f0c0252df5effb7f3297e866b3560805885b24b827a5ce8b7701e98cee4ca9bcefff0190dbe0327b11bdb46c71250d471ebf71e2cdd2597765763f3e2a9dfc58916895b36f1b66765f0b01f2663a8255fd3f38c3b6f3a30edf2f7bb3fed65223c496fbde8279f4753288cd27ab81267a0c10ae17c2ed3f98d07a050d9f2efdfa2ccf1d456b17&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.906Z" %}
新增服务账户
{% endembed %}

&#x20;2、输入**服务账户名称**，然后在「访问权限」部分中，输入或选择该服务账户应该能够访问的工程名称和/或个人机密。

{% hint style="info" %}
对于测试版，服务账户将被限制为对工程的只读访问权限。
{% endhint %}
{% endtab %}
{% endtabs %}

## 删除工程 <a href="#delete-a-project" id="delete-a-project"></a>

要删除工程，请使用要删除的工程的 (**≡**) 选项菜单选择**删除工程**。删除工程不会删除与其关联的机密。工程一旦删除就会被完全删除，**不会**像[机密那样被发送到回收站](secrets.md#delete-a-secret)。

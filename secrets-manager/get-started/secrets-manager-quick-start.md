# =机密管理器快速入门

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-quick-start/)
{% endhint %}

Bitwarden Secrets Manager 使开发人员、DevOps 和网络安全团队能够大规模集中存储、管理和部署机密。

**Secrets Manager 网页应用程序**将是您设置机密管理基础设施的主页。您将使用它来添加和组织[机密](secrets-manager-quick-start.md#add-secrets)、创建适合您需要的[权限系统](secrets-manager-quick-start.md#assign-members-to-your-project)，以及生成供您的应用程序使用的[访问令牌](secrets-manager-quick-start.md#create-an-access-token)。完成后，您将继续阅读[开发者快速入门指南](developer-quick-start.md)，以了解如何将机密注入您的机器和应用程序。

{% hint style="info" %}
Bitwarden Secrets Manager 目前作为测试程序提供。在[此处](beta-signup.md)了解有关测试版的更多信息，进而更好地使用本文档学习 Secrets Manager 网页密码库入门。
{% endhint %}

## 欢迎使用 Beta 版 <a href="#welcome-to-the-beta" id="welcome-to-the-beta"></a>

### 激活 Secrets Manager <a href="#activate-secrets-manager" id="activate-secrets-manager"></a>

Secrets Manager 可以从您组织的**计费** → **订阅**页面激活。您必须是组织的所有者才能执行此操作：

{% embed url="https://bitwarden.com/_gatsby/image/02a63b8db104aef1d4ec68d6dab4f68e/386e310bdde8d6cc3a1de335b535fdf0/activate-sm.webp?eu=898f59b3e2c0fed65e68a7836a71653ae33e01fdfb0560d06c63b5a81cab99d021a04a5323c17ce5243d5cdf85e34bbd63c27f651abcd2d392bb1bfdb93daa5b54d552ec6eba2500072b90afe3f201163dc71000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41d378620e0e9dd521aa8a4c24b8fa0b2d261ccf8b0541845daf166227f1f1651b97ebfa2e400753f2e410a63c7ab0dce65c7b338486222410e50b33e7c8111ae71729efabbff0a&a=w%3D850%26h%3D492%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.835Z" %}
激活 Secrets Manager
{% endembed %}

激活后，通过网页 ([https://vault.bitwarden.com](https://vault.bitwarden.com/)) 上的新版产品切换器可以切换到 Secrets Manager：

{% embed url="https://bitwarden.com/_gatsby/image/c2437774c5a9e867285a6527fa20b4f0/dbf13f712f25a111d687c1fb316d3dfc/product-switcher-1.webp?eu=d7d851e2e4c9ad8e0c3da6813e72363ae43b56abfa0331d56b37e1a848fa9a8121fa4c5774c37ae42e685a8bd2e846bb33c779374bebd1d9c2ee19f4ef61af005b8a52ea66ba7355517ac4fdb4f504456d90480af781cd5baa3e2786b6b3be211f571922f972ee86eda16730b38a256aaef2e66d6fddb421bd430901880622b832ead39d665aadd0ee4aabf9e9eb579edabd2c514886b4323d72346912af6de7c6bb7a16797301214ecbfa23a61cc1a96d4e62215d5b03f5356bd904fa6862cbe6f3a50fd8737fe8a0983074d5c0af80f25aee7522a29c63b4c17c234a5ef446efa17ae9923a51&a=w%3D850%26h%3D310%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.814Z" %}
产品切换器
{% endembed %}

在您使用 Secrets Manager 迈出第一步之前，您需要明确邀请一些组织成员加入。

### 给予成员访问权限 <a href="#give-members-access" id="give-members-access"></a>

{% hint style="success" %}
在继续之前，我们建议为 Secrets Manager 的用户设置一个或多个群组。您需要单独授予成员访问权限，但一旦您的密码库被填充，您可以使用群组来大规模地分配对机密的访问权限。
{% endhint %}

要授予成员对 Secrets Manager 的访问权限，您必须是组织的所有者或者管理员：

1、打开您组织的**成员**选项卡，然后使用 (**≡**) 选项菜单打开您的**成员角色**面板。

2、在面板底部，勾选**此用户可以访问 Secrets Manager Beta**：

{% embed url="https://bitwarden.com/_gatsby/image/16428fa0dec70919daa1ff46235f2795/fd47c23b1af4ee88e1f2061428b4f6b1/give-member-access.webp?eu=df8f51e4b5ccfa8e063cf58769756061b63653faab5536d96b6ce7aa1bfc98d775f41d0772c67fb32e3a588a87e340ec63c72a604bbcd4d3c5b519f5e830f95d53d10cbd62e225065278ccafe4a754423c93120aa6879e5af16d20d6e5e0bd285d145c68a265a7d8b1f86231f39d7c76bce7e56d3086e866be471a4bcc5a2faf22e191883b43a9c9af1dee9c88eb7dc9d6b22a55079ff77657324a7c25846fa4f3e104763d7c135a31c9ab5ac46394b3691a3320585f05a6353a865da86b38c6fbacf81b8c6726b4f59b64329b92fdd3b859ef3436b998&a=w%3D850%26h%3D675%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.653Z" %}
分配对 beta 版的访问权限
{% endembed %}

对要授予 Secrets Manager 访问权限的任何其他组织成员重复这些步骤。

## 第一步 <a href="#first-steps" id="first-steps"></a>

### 您的机密密码库 <a href="#your-secrets-vault" id="your-secrets-vault"></a>

使用产品切换器打开 Secrets Manager 网页应用程序。如果这是您第一次打开该应用程序，您将看到一个空的密码库，但最终它将充满您的工程和机密：

{% embed url="https://bitwarden.com/_gatsby/image/4ee0e3286a978b55a86a210bfa86d8e8/a2abe2db17d0078d7a820976a35c1dbe/Screen%20Shot%202023-03-22%20at%209.46.39%20AM.webp?eu=de8a06e0e6c8fdd3076ff1866b26313db56c52a2ac5160823a64b5fa4aa8978126a5115623967bb12560088bd3e440e960947b694aebd68e92e81ca6ed3daf0e52870bea62b22552072990f8b0f154446ec61b0ea9d29e5cf73e73d0e5b3b6721308586fe839b29ef3f06835e7d66c2cb9f2f07f2681fe3ca30c00018f0776be3ae8d6843248e693f718f0e0eaad48a4dfb87a6117dbb9715e2c261658be56dbfcad07206b2f485e3ccda759c36893e33f193422080c52a4653a8652a8646590e4aebe3e8a382eb4f6a65228d987c182ed18af3776e4d225abed6a3e6104b217aba278febd157b10c174ad&a=w%3D850%26h%3D563%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A47%3A03.932Z" %}
机密密码库
{% endembed %}

让我们开始填充您的密码库吧。

### 新增工程 <a href="#add-a-project" id="add-a-project"></a>

工程是按逻辑组合在一起的机密的集合，由您的 DevOps、网络安全或其他内部团队进行访问权限的管理。重要的是要考虑到，在创建工程时，工程将是您分配成员访问秘密的主要结构。要创建一个工程：

1、使用**新增**下拉菜单选择**工程**：

2、输入**工程名称**。

3、选择**保存**按钮。：

### 分配成员到工程 <a href="#assign-members-to-your-project" id="assign-members-to-your-project"></a>

### 新增机密 <a href="#add-secrets" id="add-secrets"></a>

### 新增服务账户 <a href="#add-a-service-account" id="add-a-service-account"></a>

### 创建访问令牌 <a href="#create-an-access-token" id="create-an-access-token"></a>

## 下一步 <a href="#next-steps" id="next-steps"></a>

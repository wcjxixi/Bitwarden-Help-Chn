# Secrets Manager 快速入门

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

2、在面板底部，选中**此用户可以访问 Secrets Manager Beta 版**：

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

工程是按逻辑组合在一起的机密的集合，由您的 DevOps、网络安全或其他内部团队进行访问权限的管理。重要的是要考虑到，在创建工程时，工程将是**您分配的成员访问机密的主要机构**。要创建一个工程：

1、使用**新增**下拉菜单选择**工程**：

{% embed url="https://bitwarden.com/_gatsby/image/9ec307c2cd6c1b17138196203755eb3e/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.31.44%20PM.webp?eu=d8da54b2b7ceff805c6fa6856a7b653fe93b56adf85833816931eda647ae99802df3110371c72ee72b3a5ad8d7e514bc34c07c651eeed6dc96ea4da5e235ae5e518a09bf34b070060478c5a8e2a101416dc31350a78acb0df73c7bdce7b2e17911021e7dfc7dbfd4e4aa3c31e6d0256aaef2e66d6fddb421bd430901880622b832ead39d665aadd0ee4aabf9e9eb579edabd2c514886b4323d741b680f9e44dfa5c153123a543b2a6b99d42c983eeaa96d4d612a575604f13668d104f8683090e5aaa90ede7b2fe4ac9b3073d391ad82f279ff6823b29148cada643e610fac11aea17bf5cf660261d06e959752b1021b3144ed7cf43a60876f&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.727Z" %}
创建一个工程
{% endembed %}

2、输入**工程名称**。

3、选择**保存**按钮。

### 分配成员到工程 <a href="#assign-members-to-your-project" id="assign-members-to-your-project"></a>

将组织成员添加到您的工程将允许这些用户与此工程的机密进行交互。要将人员添加到您的工程：

1、在「新增工程」中，选择**人员**选项卡。

2、从「人员」下拉列表中，输入或选择要添加到工程的成员或群组。选择了合适的人员后，选择**添加**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/e9bb73e3052de06a4e8b28867b6975e5/e681e48097835dcdff2f106983d95d69/Screen%20Shot%202023-03-22%20at%209.44.33%20AM.webp?eu=8c8856e6b29cff870a6aa4816c756961b66a5ef8fb0333d03d36b5fb49f9998772f21103739572b92e6053d981b341e962977f3748bbd38f92bd10f7eb30fc0802875cba66e7720f552e96fab0f20c1d2c825a1bab9cd751fe3c2581a6ade4344f015f68fd3efb9fb2fc717bb7c17161aceca7786d9fec7fff163811c25f348e30b3c38b4654e994e91889e4b5d163d29be7250342dff6362b70181c5fef7cedf3e10771312b430e6398a759c43394b6237f32610b0a5d9804628f11946e31c1e7e6a15ec478798ef98d5e7998c7aa9eee19c35b0bf98f79fe&a=w%3D850%26h%3D320%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A44%3A53.961Z" %}
将人员添加到工程
{% endembed %}

3、将成员或组添加到工程后，为这些成员或群组设置**权限**级别。成员和群组可以具有以下权限级别之一：

* **可以读取**：成员/群组将能够查看 \[_以及编辑_] 此工程中的现有机密。
* **可以读取、写入**：成员/群组将能够查看现有机密并在此工程中创建新的机密。

### 新增机密 <a href="#add-secrets" id="add-secrets"></a>

您的工程中已经有一些成员可以帮助您管理它了，现在让我们向该工程添加一些**机密**。机密是存储在您的密码库中的敏感键值对，通常是永远不应以纯代码公开或通过未加密通道传输的东西，例如：

* API 密钥
* 应用配置
* 数据库连接字符串
* 环境变量

您可以将机密作为 `.json` 文件直接导入您的密码库或手动添加机密：

{% tabs %}
{% tab title="导入机密" %}
要导入您的机密：

1、查看[此文档](../import-export/import-data.md)以帮助正确格式化导入的文件。

2、从左侧导航中选择**设置** → **导入数据**：

{% embed url="https://bitwarden.com/_gatsby/image/dddea76f1081f886b571e53d9c758815/8a7169edff092ec6b001e02265ff4469/import%20(2).webp?eu=df8f05e4eaccfa80093df5d26127656db63b05fdf6533fd03d30e3fe46a8ca8322a51d5d75927ee728610b8dd1e642b931927b351dead2dcc6b84efded31ad5e5b820cba6eba7907507ac1ffe4f455133a93130da4d7ce0ef76524d7b6b0b4214b521c22fd72bdd2e9fd6631badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec344b16094631ac45c2e0db6d06384d00336aadd507a27e9ebf6a496876595705f56f69d75dfb386296e2f2f554dd287fe0fd9f6071d0c5b1d9b05af3683288a025c69c7b2459&a=w%3D850%26h%3D243%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.646Z" %}
导入数据
{% endembed %}

3、选择**选择文件**然后选择要导入的 `.json` 文件。
{% endtab %}

{% tab title="手动添加机密" %}
要手动添加机密：

1、使用**新增**下拉菜单选择**机密**：

2、在「新增机密」窗口的最顶部部分，输入**名称**和**值**。可选添加**备注**。

3、在「工程」部分，输入或选择要与此机密关联的工程。几个关键点：

* 每一个机密一次只能与一个工程相关联。
* 只有有权访问该工程的组织成员才能查看或操作此机密。
* 只有有权访问该工程的服务账户才能创建注入此机密的途径（[稍后会详细介绍](secrets-manager-quick-start.md#add-a-service-account)）。

4、完成后，选择**保存**按钮。

对要添加到密码库的所有机密，重复此过程。
{% endtab %}
{% endtabs %}

### 新增服务账户 <a href="#add-a-service-account" id="add-a-service-account"></a>

现在您已经有了一个填满机密的工程了，是时候开始构建对这些机密的机器访问了。**服务账户**代表非人类机器用户或一组机器用户，他们需要以编程方式访问存储在您的保管库中的某些机密。服务账户用于：

* 适当地限制机器用户对一定范围的机密的访问权限。
* 发布访问令牌以促进对机密的编程访问和解密能力。

要为此工程添加服务账户：

1、使用**新增**下拉菜单选择**服务账户**：

{% embed url="https://bitwarden.com/_gatsby/image/9b5074ec4c99b594233e0c1540706f8f/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.33.47%20PM.webp?eu=dbdc01e1b0cefa815a3af1863e726469e23855f8f75962d83e6de4af4fa89dd075f61f0074977bb52d6a0cdcd0e24ab932c4706910ee83d2c2ba1ca7eb35fc0905855aec61b573075022c1f7b8f20e4c6dc0490df7d59a0af76c7081ede0b7254c57492da17cb2d9a8ed7527ba9c306bb7e7f17b26dcf83cb6431d179e5c32e23aeed4c1345cb09df645eeb0e6f44eca839b7c610782a067632f0a4d04b445dbf8b4582e464c5f0866cef951c464c5b13b4960775c5a02f7353ad606f26c63cbe6a8a708d9282dfecb9a7325d39dc1e3b545e84574e7cd24b48239670c09c342e9d379e9d167180a86459ae852f25d52&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.906Z" %}
新增服务账户
{% endembed %}

2、输入**服务账户名称**，然后在「访问权限」部分，输入或选择该服务账户应该能够访问的工程的名称和/或个人机密。

{% hint style="info" %}
对于测试版，服务账户将被限制为对工程的只读访问权限。
{% endhint %}

### 创建访问令牌 <a href="#create-an-access-token" id="create-an-access-token"></a>

**访问令牌**有助于以编程方式访问和解密存储在您的密码库中的机密。访问令牌颁发给特定的服务账户，并将赋予应用它们的任何机器仅能访问**与该服务账户相关联的机密**的能力。要创建访问令牌：

1、从导航中选择**服务账户**。

2、选择要为其创建访问令牌的服务账户，然后打开**访问令牌**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/9ce9ddc8aa45160b5caff34b37a3e9d2/70a07780b34d25e1c964fd2e853af8e1/Screen%20Shot%202023-02-24%20at%2010.12.38%20AM.webp?eu=d9df50b0e0c8fa84086fa7873e236638b26b05aeaa0567d56f65b7a81ca89fd026f11c52239c28e77e6059d8d2b54bbf67957d601ae7d58bc8e94af5ea35a2595a8a09ec34b17853557d92afb0a3034761904e5aa386c800f23971d2e4bab02248051e79fc2be9d4eafd3267b6802d61eae2a62e6cc3f97de9465c53cf4d7ba420ffd09d3901f197ed4eb8b3adb75a89cab66e44159fb02b7c2208005faf73e8e3e805273174075c2ac8da21b915c7de657c0063571e62a4183c9154b12834dcb1f9f408d8787fe2aac86322d591fd80b913a4237fb6c92ea8853f7d5b0ef915b2df28b587315861e272a5d123b00307365d821e942624b6691be30684ff469136ff6649474cdebc4406&a=w%3D850%26h%3D329%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.853Z" %}
创建访问令牌
{% endembed %}

3、选择**创建访问令牌**按钮。

4、在「创建访问令牌」面板上，提供以下信息：

* 令牌的**名称**。
* 令牌的**权限**级别。在 Beta 期间，只有**读取**访问权限可用。
* 令牌的**到期**时间。默认为`从不`。

5、完成令牌配置后，选择**创建访问令牌**按钮。

6、将出现一个显示访问令牌的窗口。关闭此窗口之前请将您的令牌复制到安全的地方，因为您的令牌**以后无法获取**：

{% embed url="https://bitwarden.com/_gatsby/image/36952bd7fa3514dc9b301eba61b3f256/02b860cb3c232ecb9c257c521dbb8153/Screen%20Shot%202023-02-24%20at%2010.16.14%20AM.webp?eu=d9df59b4b5ceaf870e6ef6d66f77366de86904abfe5760d93b32e4a94ca99ed376f54a53229328e22f3d0ed7dae84abf639371651ae986da91ed4ea0e337f85e57d10fe761b67a5f156f84bdbaea191c35974d0de29d9b4cf53c3197b0f7f46e47055834af38e6d2aaf33432b8de6835f5b5c7782596c819b14b5c0cbd5a168b30ccf382527c90d1e54bbde4e8a85d9fcae57e0547d2f1332b704b1d5ee979b2a4b30d753e7a410e2aadfc1a9234c8d95f443e67315d03f56427d057e66e35acb5bfce5cd9647ae7b6c8351ff7beb0c0b34d&a=w%3D850%26h%3D587%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.747Z" %}
访问令牌示例
{% endembed %}

此访问令牌是身份验证工具，通过它您可以编写机密注入脚本到您的机器和应用程序中。

## 下一步 <a href="#next-steps" id="next-steps"></a>

现在您已经掌握了创建用于安全地管理机密的基础设施以及为机器访问机密创建路径的诀窍，让我们继续阅读[开发人员快速入门](developer-quick-start.md)指南。

# 服务账户

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/service-accounts/)
{% endhint %}

服务账户代表非人类机器用户，例如，需要以编程方式访问一组谨慎的[机密](secrets.md)的应用程序或部署管道。服务账户可用于：

* 适当地限制机器用户对一定范围的机密的访问权限。
* 发布[访问令牌](access-tokens.md)以促进对机密的编程访问和解密能力。

您的用户账户有权访问的机密列在主要 Secrets Manager 视图中，也可以通过从导航中选择**服务账户**来列出：

{% embed url="https://bitwarden.com/_gatsby/image/ff89a3da8877202b736c84c193ccd6b7/e512f395a569a4da8e6165e0eb34e02f/Screen%20Shot%202023-02-27%20at%209.22.17%20AM.webp?eu=8ad803e0b6c8fdd25d3bf4d66b76336be03a05acfc0230843c6de6fd1ea1ca8e23f3195d729028e0796d53d7d1e310bc64c378634ce8d1d295b949f5ef36fb0a53d552ed33b07a5f156f84bdbaea191c35974d0de29d9b4cf53c3197b0f7f46e47055834af38e6d2aaf33432b8de6835f5b5df4f2fb4dc2be9445a2bba4730ba1ed8c79c466cb0d1b24be7e3eca10fc8cfe6290646dff363207e1f165de925bbf6b25674302c470d2aadfc1a9234c8d95f443e67315d03f56427d057e66e36acb5bfce54c77879ffa9ce5e01fbddeedeba&a=w%3D850%26h%3D258%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.733Z" %}
服务账户
{% endembed %}

打开服务账户将列出服务账户有权访问的**机密**和**人员**，以及任何已生成的**访问令牌**：

{% embed url="https://bitwarden.com/_gatsby/image/a21156feb050647663ed04d1ff38dc14/8edca8a5097cc14b22b9d9515be0f778/Screen%20Shot%202023-02-27%20at%209.22.55%20AM.webp?eu=d9d854b4b59dadd40c3ea9803e73313fe13603a8f8523ed93f60e3fa1efbccd223a6110124947ce07e3c0888d1e544b2339579654bbdd28892ee18f4b934ff5e5a865dbd31ba23020423c5feb0a3004469921858a3d09a59a46b20d7e7b7be254b564f29ab7fbf81edac3432e5822b33b9b3ac762186eb3bea0d410d964926a927a5c39a654fad8de55bacf8b0fc4dd29ba573540681f2632a2a0b1847ee51b2d0c57905672e172c44b3f65b8226e2b74165013c5c5851f3606fd956a86b37c2b6ffa95ddf2f78e6facb6775d7c7a789e419fa2269849c65fcd765156d55f357c2be7bf5d179060c9c28fdfa1df66c0c2b4280028c214fa84541cc59d3&a=w%3D850%26h%3D261%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.740Z" %}
服务账户内部
{% endembed %}

## 创建服务账户 <a href="#create-a-service-account" id="create-a-service-account"></a>

要创建一个新的服务账户：

1、使用**新增**下拉菜单选择**服务账户**：

{% embed url="https://bitwarden.com/_gatsby/image/9b5074ec4c99b594233e0c1540706f8f/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.33.47%20PM.webp?eu=dddb50e5e1caf8d2093cf4d03b7a366ce23b55aafd0360d16937b0af4ca19b8425f11a0423c32fb2253f08da80e016e965922c681ae8d0d894b810a7e232f95b538609ef32ba2400562ac6fcb0f2001161c31b0af5d69b00a6687ad6e6e6e6721b061423a873ee84eba83030b0852f33b8e7a47f6dc6a120a4561e17c1076ea539eac78b7000bd8ae64eaca5bbed4ad3c2b269184799ad66642d4d4950b06abcbace55177e7013097496e90a9b38fed6611a3d7c213a1ca4343a865cf86962c4e3aea009db7f7ae1fac937238fc3fc88ef49aa7f76b59938cad1792f5b53c370f5e33f98d064040d9c2af8884eb66c54712f80028a273edd3f30ec7a9aa119c4&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.906Z" %}
新增服务账户
{% endembed %}

2、输入**服务账户名称**，然后然后选择**保存**。

3、打开「服务账户」，然后在**工程**选项卡中键入或选择该服务账户应能够访问的工程的名称。对于每个添加的工程，选择一个**权限**级别：

* **可以读取**：服务账户可以从分配的工程中检索机密。
* **可以读取、写入**：服务账户可以从分配的工程中检索和编辑机密，在分配的工程中创建新的机密，或者完全创建新的工程。

{% hint style="success" %}
服务账户的写入​​访问权限的充分利用取决于即将发布的 [CLI](../developer-tools/secrets-manager-cli.md) 版本。目前，这只是在 UI 中提供了此选项。请继续关注[发行说明](../../release-notes.md)以获取更多信息。
{% endhint %}

## 添加人员到服务账户 <a href="#add-people-to-a-service-account" id="add-people-to-a-service-account"></a>

将组织成员添加到服务账户将允许他们为服务账户生成访问令牌并与服务账户具有访问权限的所有机密进行交互。要将人员添加到您的服务账户：

1、在「服务账户」中，选择**人员**选项卡。

2、从「人员」下拉列表中，输入或选择要添加到工程的成员或群组。选择了合适的人员后，选择**添加**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/3e1c05a001f099fbdba16b050d4292ac/e681e48097835dcdff2f106983d95d69/Screen%20Shot%202023-02-27%20at%202.38.41%20PM.webp?eu=8ddb52e2b29eaf825a3df3d56e73363be73f52ada85936d46b65b6aa19ad9b832ca64d5422c37de02d6a0e8a85e344bd639229301febd08cc3ea1df6bb30fe015a835aec60e02500587fccf9e4f500423dc0480ea0d7990aa5687680e5b3e17318024e7ea928edd5eefb6460b3822931bce3f52d6c90a120a4561e17c1076ea539eac78b7000bd8ae64eaca5bbed4ad3c2b269184799ad66642d4d4950b06abcbab1603362751e28748bf0119915eec0541a3f5956181cfe6f3c8404f9653595e1adf45e8d7378b2fe98657987c1a7d4bb18aa2b23e6c638cad1792f5b53c370f5e33f98d064040d9c2af8884eb56c54712f80028a2c3edd3930ec7a9aa119c4&a=w%3D850%26h%3D320%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.754Z" %}
将组织成员添加到服务账户
{% endembed %}

## 添加工程到服务账户 <a href="#add-projects-to-a-service-account" id="add-projects-to-a-service-account"></a>

将工程添加到服务账户将允许使用访问令牌以编程方式访问包含的机密。您可以将新工程和现有工程添加到服务账户：

{% tabs %}
{% tab title="添加现有的工程" %}
要将现有项目添加到您的服务账户：

1、在「服务账户」中，选择**工程**选项卡。

2、从「工程」下拉菜单中，键入或选择要添加到服务账户的工程。选择正确的工程后，选择**添加**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/7ed364426c705bbce4e122ac8ca26d9b/9e89d9a1d2ec58602058cc0325fd5006/Screen%20Shot%202023-03-22%20at%209.49.13%20AM.webp?eu=da8850b7b79df5d5086aa6d26e736269e73e5ef9aa5565d83837b2ae4cfacad370f44a56239273e5793a5fdbdab446ee67c57a631fbad2d296ef1da0b860aa0102830fef35b078520329cdadb1fc52106ec21000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41b198b3fdad4dd4e4a90b6ed6eb09d92c161a5e19075184088a06026244a4c5dea28eda3e45025302e465d60cdab5bc461c7e7394e3575413c50b5326f8e3a98346e878bf9a15fda677be2b5cb331fd787c189f31ea53477e4a056d49c7b2459&a=w%3D850%26h%3D386%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A49%3A25.224Z" %}
添加工程
{% endembed %}

3、打开「服务账户」，然后在**工程**选项卡中键入或选择该服务账户应能够访问的工程的名称。对于每个添加的工程，选择一个**权限**级别：

* **可以读取**：服务账户可以从分配的工程中检索机密。
* **可以读取、写入**：服务账户可以从分配的工程中检索和编辑机密，在分配的工程中创建新的机密，或者完全创建新的工程。
{% endtab %}

{% tab title="添加新的工程" %}
要为此工程添加新的服务账户：

1、使用**新增**下拉菜单选择**服务账户**：

{% embed url="https://bitwarden.com/_gatsby/image/9b5074ec4c99b594233e0c1540706f8f/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.33.47%20PM.webp?eu=8bdd06b4e4c0ae810d60a0866a76643fb63c53aff90434d26f67e0fa4aa19c8377f44d5225957be07e6c0bded4e142b332ce2d6711bdd0dd91e919a6bf64ac5c53835be960b77302557e90fce1a6071768c01000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d464209a23e2c38c7246a89cec468786b3af5592e382325413dba53c21721f185fb82cefa7b705716b2946083ccefd50c53290e33c4e373c3d0c41a23264bf36a33375ace6fba35ec47a79fcaacd5e21c2acac9eee19b22e7188af5ab7c2652d&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.906Z" %}
新增服务账户
{% endembed %}

2、输入**服务账户名称**，然后选择**保存**。

3、打开「服务账户」，然后在**工程**部分中，使用下拉菜单键入或选择要添加到服务账户的工程。选择正确的工程后，选择**添加**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/7ed364426c705bbce4e122ac8ca26d9b/9e89d9a1d2ec58602058cc0325fd5006/Screen%20Shot%202023-03-22%20at%209.49.13%20AM.webp?eu=dd8959e1e5c0a8815968f3866d73636be06a52acfb043ed23937e1ab49a8cbd22df6115c739479e3786e52dd80e011bf34c279344dedd0dcc5ed10fdb931af0e54825bbc35b17201542ac4afb2fd524c6a954f5aa681cb0af6682380b4e7b5781308586fe839b29ef3f06835e7d66c2cb9f2f07f2681fe3ca30c00018f0776be3ae8d6843248e693f718f0e586de52acd8e450533ea3ae447d0c3077308550ccfdad04226a7c4408339daa5fc23790e068486824585956f46339d355aa3d3491b0adbe3e8a382eb4f6a65228d987c182ed18af3776e4d225abed6a3e6104b217a4a27af4bd157b10c174ad&a=w%3D850%26h%3D386%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A49%3A25.224Z" %}
添加工程
{% endembed %}

4、打开「服务账户」，然后在**工程**选项卡中键入或选择该服务账户应能够访问的工程的名称。对于每个添加的工程，选择一个**权限**级别：

* **可以读取**：服务账户可以从分配的工程中检索机密。
* **可以读取、写入**：服务账户可以从分配的工程中检索和编辑机密，在分配的工程中创建新的机密，或者完全创建新的工程。
{% endtab %}
{% endtabs %}

## 删除服务账户 <a href="#delete-a-service-account" id="delete-a-service-account"></a>

要删除服务账户，请使用要删除的服务账户的 (**≡**) 选项菜单选择**删除服务账户**。删除服务账户不会删除与其关联的机密。服务账户一旦删除就会被完全移除，**不会**像[机密那样被发送到回收站](secrets.md#delete-a-secret)。

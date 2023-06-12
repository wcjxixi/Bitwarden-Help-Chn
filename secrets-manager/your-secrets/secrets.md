# 机密

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets/)
{% endhint %}

机密是您的组织需要安全存储、永远不应该以明码形式公开或通过未加密的渠道传输的敏感键值对，例如：

* API 密钥
* 应用配置
* 数据库连接字符串
* 环境变量

您的用户账户通过[已分配的工程](projects.md)可以访问的机密列在主要的 Secrets Manager 视图中，也可以通过从导航中选择**机密**来列出：

{% embed url="https://bitwarden.com/_gatsby/image/bfb2c763a99fd70ea1d4dcf9632ff570/557d3f27253653e121d356eb9a00ff16/Screen%20Shot%202023-02-24%20at%202.59.58%20PM.webp?eu=da8a59e3e69ba8d15b6fa0d63a24653ce33f02f9f70764d43d30e1a846a1cc8722f7190421c12be72d6c5cdad3e945eb34c62e634bbad589c8ed1ca7bf3cff0c50d65eef64e02600592ac5feb1f403146ec21f0cf482cf08f73e7687e4b4b72511504a2ca222fcc5acea3f7bafda7263bde3e5303686fd29a3510b1088062fa920a4979c6d4da894b149e7bba9ae16cbcde2444209ddb949262e1a4a18ac49cee2f17c124536455d32cdac0bc53796be6e4a69265d5e04f2336c8106f26b38cbb2aef00bd87c6482fb8b6425d8accdd8b25ec32876e5cc3aa98026780a62fd57c2be65f2db7a0306ee4a878b0cec54&a=w%3D850%26h%3D273%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.847Z" %}
机密
{% endembed %}

## 创建机密 <a href="#create-a-secret" id="create-a-secret"></a>

要创建一个新的机密：

1、使用**新增**下拉菜单选择**机密**：

{% embed url="https://bitwarden.com/_gatsby/image/8af613589a3b92f196f52d537516d9ba/928e30c874b06e59f97b658b618bcd66/Screen%20Shot%202023-02-24%20at%202.33.39%20PM.webp?eu=898e06e6e5caf9855a69a78a3a7a6169b23902a8fa5762d53560e1fe1af9cdd02da54d5727c47db4783d0bd7d3b114ef6f932b6948bf84dac3bd19f7e931a95907d55eec64e22106542b91f7b1a30c1d2c825a1bab9cd751fe3c2581a6ade4344f015f68fd3efb9fb2fc717bb7c17161aceca7786d9fec7fff111b219872768b61c792ba4963eaafe762b29084ad71d2cdb22b01128ef7632b7f4c160abe2ceea3b502246f2d135e67c7fc0a916491be237f32610b0a5d9804628f11946e31c1e7e6a15fc4787f8ef98d5e7298c0ad9eee13c34a0bf98f79fe&a=w%3D850%26h%3D124%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.762Z" %}
新增机密
{% endembed %}

2、在「新增机密」窗口的最顶部部分，输入**名称**和**值**。可选添加**备注**。

3、在「工程」部分，选择一个现有[工程以关联机密](secrets.md#add-secrets-to-a-project)或创建一个将包含机密的新工程。每一个机密一次只能与一个工程相关联。

4、完成后，选择**保存**按钮。

## 添加机密到工程 <a href="#add-secrets-to-a-project" id="add-secrets-to-a-project"></a>

机密一次只能分配给一个工程。通过向工程添加机密：

* 有权访问该工程的组织成员将能够查看或操作此机密。
* 有权访问该工程的服务帐户将能够创建注入此机密的途径。

要将您的机密添加到工程中：

1. 导航到**机密**视图然后选择要添加的机密。
2. 在「编辑机密」窗口中，打开**工程**选项卡然后输入或选择要与机密关联的工程。
3. 完成后，选择**保存**按钮。

## 删除机密 <a href="#delete-a-secret" id="delete-a-secret"></a>

要删除机密，请使用要删除的机密的 (**≡**) 选项菜单选择**删除机密**。删除的机密将被发送到回收站，删除后它们会保留 30 天。 30 天过去后，机密将被永久删除且不可恢复。

在回收站中，您可以在 30 天等待期之前将机密恢复到您的密码库或永久删除：

{% embed url="https://bitwarden.com/_gatsby/image/a974d592151e5e0c650902e1e57886dc/7af6ce9d46e9da4efee61775882c45c8/Screen%20Shot%202023-02-24%20at%203.17.06%20PM.webp?eu=8d8c01b5e4cbfb830c6bf4853973633bb16c05aaaa0765d93437e3fe48fa998f76a5105473c078b02d6e09ded3b341ba6ec570601cbfd7dfc1bf4bf2ed66a35c578253eb31b77254057d96ace2f257456a971f51a0849909f7647bd0b6e5b02211591879af2fbdd5e8a93c64b9d57a3bb9beaf7b34c2fd2cb547540c8f5c31bf6ea48f876e4fb99bf301bca2b8f84a8ec9a36e191e8eb72a2535124c1eb72cedadef4376262a45205f9aed02c427c3b64964275c2d5f5da52f5e864aaa3967c5b1aea40fd9297ce1fec1657982c6fad6e91eab2e75b39a74fc866a29116eff51f8e92598b13c594aee28fa974faf030728428673d8604fda265e8b1984e728f355e22e7861&a=w%3D850%26h%3D210%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.714Z" %}
回收站
{% endembed %}

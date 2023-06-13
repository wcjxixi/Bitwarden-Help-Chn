# 两步登录-Duo

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-duo/)
{% endhint %}

使用 Duo 的两步登录在[可用的两步登录方式](../two-step-login-methods.md)中是比较独特的，因为它可以为个人账户启用（与其他方式一样），对[团队和企业](../../organizations/organizations.md)组织来说，可以为整个组织启用。

## 设置 Duo <a href="#setup-duo" id="setup-duo"></a>

在 Bitwarden 中设置 Duo 的方法略有不同，这取决于您是为您的个人密码库还是为您的组织启用。选择下面的选项卡获取相应的介绍：

{% tabs %}
{% tab title="个人用户" %}
### 获取 Duo 密钥 <a href="#retrieve-duo-keys" id="retrieve-duo-keys"></a>

您需要一个 Duo 帐户才能获取 Bitwarden 所需的一些信息以完成设置。[免费注册](https://signup.duo.com/)，或登录到现有的 [Duo Admin Panel](https://admin.duosecurity.com/login)。要配置 Duo：

1. 在左侧菜单中，导航至 **Applications**。
2. 选择 **Protect an Application** 按钮。
3. 在应用程序列表中查找或检索 **Bitwarden**，然后选择 **Protect** 按钮。您将被重定向到一个 Bitwarden 应用程序页面：

{% embed url="https://bitwarden.com/_gatsby/image/9f7f3d534579519a1e5f1e88dfdae69b/ad1f942ee0d9e57b07b48b3c8bcc2548/duoportal.webp?eu=d78650b3e19bfad2066af2d63c216168b36d55aef95334d46b31edad48aaccd427f44f0475932fb1283d088a86e645b260937c641ce9d388c2bb49fced33ae0a05d25fed62b12654562b96fab4a452113ec54c58f0839e0da16b7addefebf33459131634b723e5d0bbfc767ae3c77963a9f5f36a26dcf52da40d5916954b37a665ed98837419f1cdf5668fb388db4bbceaaf5f5a12a2a45655114b7d0cf27bb3f3e600756a28485b329bac58c73590e53c4934250f5707a6613ed455fb6c2e97a1a4e1029b3e2abdb6896f27&a=w%3D850%26h%3D474%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A18%3A20.314Z" %}
Bitwarden 应用程序页面
{% endembed %}

记录下 **Integration key**、**Secret key** 和 **API hostname**。当您在 Bitwarden 中设置 Duo 时，需要参考这些值。

### 在 Bitwarden 中设置 Duo <a href="#setup-duo-in-bitwarden" id="setup-duo-in-bitwarden"></a>

{% hint style="warning" %}
**丢失对启用了 Duo 的设备的访问会永久性将您锁定在您的密码库之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

完成如下步骤之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。
{% endhint %}

要为你的个人密码库启用 Duo 方式的两步登录：

1、登录您的[网页密码库](https://vault.bitwarden.com/)。

2、选择个人资料图标并然后下拉列表中选择**账户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?eu=8adb56b0eaccf885076fa2d66f746161e56956aaac0032d43465b6f94bfe9b8e71fa1151289528b0796d528bd7e816bc31c67d691befd18991bc4af4be3da80d07835fb836b07807052ec4fde4a1574d60c11b5fa8d1c90ca76a21ddb4b4e47711571b23ae7ebbd7e8fa3064badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec3226050d762c882bfad0bb5137732f072e7fc6d45fae7e91b13f4934705f0c03a5673a8555fb3863c7b0aef509da7e7ee7fdc06073d0cab1e3be58f97f2888ac7ff6c654780e0fae0eadb966f6d10b574aee2bfa8b4fb61d04352ff36197647e8e&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A24%3A03.707Z" %}
账户设置
{% endembed %}

3、选择**安全**页面和**两步登录**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/825426d227e1afce2f4b644e6a3e9e84/3cbf2a88c5de2a53993ef05ef68dd09e/Screen%20Shot%202022-05-16%20at%2011.13.53%20AM.webp?eu=d8df06efe1ceae815b3ca28a6e76643bb43851ada85931853e36b2a94ffc9e832ca64f5c719328b229695ed7d3b443bc60927d614fe6d58f92bf4af6e33ca35954d05cea61e22452037e91aae3a30e4168c41c50f7d1c95bf66b27d4e2b7e4241b051a28a97ab2d9a8ed7527ba9c306bb7e7f17b26dcf83cb6431d179e5c32e23aeed4c1345cb09df645eeb0e6f44eca83e55f443b98fb3675731f42019e48fcede406206d21434436cbaa0ecf3090b13e4e33220c0b02fe67388452ae6c36c5b5fca45bde2e73e5b7aa6232d396f0ef8e42f36e19e5cf25ab9f3b7f130caa7cfcf814f6d37a070d9f2ff9fa3dcf1d456b17&a=w%3D779%26h%3D301%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.371Z" %}
两步登录
{% endembed %}

4、定位到 **Duo** 选项然后选择**管理**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/60ca7a602b3ed2213b146b44932a6f8b/9cd93fc2542897e9860b9a4630f212f1/twostep-options-duooverlay.webp?eu=d88a58e3e0cbaa855d3df58b61716969b23656a8aa5164d7386decfe1bfb98d576a61007759d2eb024685b8b85e045bc31ce29611fe6d088c8bb1da5b933a90e5bd150b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af862b63bcfedf2e17c1f979bc5456308a6b0fa319e2f3c13219e69db819ecb3b8a10b999de42500148df03274244e195beb7beaf3b30078266d0704768afa18da3ed6f265433f60430b46a8387c8517a73d78dda4a5f6&a=w%3D754%26h%3D391%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A18%3A20.295Z" %}
选择管理按钮
{% endembed %}

将提示您输入主密码以继续。

5、输入从您的 Duo Admin Portal 中获得的 **Integration Key**、**Secret Key** 和 **API Hostname**。

6、选择**启用**按钮。

一个绿色的 `已启用` 消息表明已为您的密码库成功启用了 Duo。通过选择**关闭**按钮并看到 **Duo** 选项上有一个绿色的复选标记（**✔️**）以再次检查。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，你应该注销所有的 Bitwarden 应用程序，以为每个应用程序立即激活两步登录。您最终会被自动注销。
{% endhint %}

### 注册设备 <a href="#register-a-device" id="register-a-device"></a>

设置好 Duo 后，打开网页密码库。如果 Duo 是您[优先级最高的启用方式](../two-step-login-methods.md#using-multiple-methods)，您将在下次登录时被要求注册一个两步登录设备：

{% embed url="https://bitwarden.com/_gatsby/image/c9db5133a3be5e27ee3d1d3c97c088ce/1fbd04ec18b898571b2ab06a02b263ca/unnamed.webp?eu=da8602b0b6c1a9d10f6ca18b6974696ce73d05a3fd0336826935ecad1aaccc8375f01c5d259128e0246808d686e044ec36977c304cbd83ddc2e84efde837ae0b5a8250b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af86526febc1a36a3f94cb25aa515b32c34723ad2ce791c1621eec9bb91abeb4bdf8589f95b629004789f53127734e4d5fe87cb8f3b60324266c1e056493fa0cd921c8e1&a=w%3D750%26h%3D507%26fm%3Dwebp%26q%3D75&cd=2023-03-10T17%3A12%3A19.760Z" %}
Duo 2FA 设置
{% endembed %}

按照屏幕上的提示将辅助设备配置为使用 Duo（例如，注册和发送 SMS 或发送推送通知的设备类型）。如果您尚未下载 Duo 移动应用程序，建议您下载：

* [下载 iOS 版](https://itunes.apple.com/us/app/duo-mobile/id422663827?mt=8)
* [下载 Android 版](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile)
{% endtab %}

{% tab title="组织用户" %}
### 注册设备 <a href="#register-a-device" id="register-a-device"></a>

您的组织管理员设置了 Duo 后，您将在下次登录网页密码库时被要求注册一个两步登录设备：

{% embed url="https://bitwarden.com/_gatsby/image/c9db5133a3be5e27ee3d1d3c97c088ce/1fbd04ec18b898571b2ab06a02b263ca/unnamed.webp?eu=da8602b0b6c1a9d10f6ca18b6974696ce73d05a3fd0336826935ecad1aaccc8375f01c5d259128e0246808d686e044ec36977c304cbd83ddc2e84efde837ae0b5a8250b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af86526febc1a36a3f94cb25aa515b32c34723ad2ce791c1621eec9bb91abeb4bdf8589f95b629004789f53127734e4d5fe87cb8f3b60324266c1e056493fa0cd921c8e1&a=w%3D750%26h%3D507%26fm%3Dwebp%26q%3D75&cd=2023-03-10T17%3A12%3A19.760Z" %}
Duo 2FA 设置
{% endembed %}

{% hint style="success" %}
如果 Duo 没有要求您注册设备，请尝试使用隐身或隐私浏览窗口登录。
{% endhint %}

按照屏幕上的提示将辅助设备配置为使用 Duo（例如，注册和发送 SMS 或发送推送通知的设备类型）。如果您尚未下载 Duo 移动应用程序，建议您下载：

* [下载 iOS 版](https://itunes.apple.com/us/app/duo-mobile/id422663827?mt=8)
* [下载 Android 版](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile)
{% endtab %}

{% tab title="组织管理员" %}
为一个组织启用 Duo 后，将提示所有已注册成员在他们下次登录时注册一个设备以用于 Duo 方式的两步登录。

{% hint style="info" %}
Bitwarden 将仅识别具有电子邮件地址用户名的用户。没有电子邮件地址作为主要用户名的 Duo 用户将需要一个。请参考 [Duo 用户名别名配置指南](https://help.duo.com/s/article/aliases-guide?language=en\_US)以获取更多信息和说明。
{% endhint %}

### 获取 Duo 密钥 <a href="#retrieve-duo-keys" id="retrieve-duo-keys"></a>

您需要一个 Duo 帐户才能获取 Bitwarden 所需的一些信息以完成设置。[免费注册](https://signup.duo.com/)，或登录到现有的 [Duo Admin Panel](https://admin.duosecurity.com/login)。要配置 Duo：

1. 在左侧菜单中，导航至 **Applications**。
2. 选择 **Protect an Application** 按钮。
3. 在应用程序列表中查找或检索 **Bitwarden**，然后选择 **Protect** 按钮。您将被重定向到一个 Bitwarden 应用程序页面：

{% embed url="https://bitwarden.com/_gatsby/image/9f7f3d534579519a1e5f1e88dfdae69b/ad1f942ee0d9e57b07b48b3c8bcc2548/duoportal.webp?eu=d78650b3e19bfad2066af2d63c216168b36d55aef95334d46b31edad48aaccd427f44f0475932fb1283d088a86e645b260937c641ce9d388c2bb49fced33ae0a05d25fed62b12654562b96fab4a452113ec54c58f0839e0da16b7addefebf33459131634b723e5d0bbfc767ae3c77963a9f5f36a26dcf52da40d5916954b37a665ed98837419f1cdf5668fb388db4bbceaaf5f5a12a2a45655114b7d0cf27bb3f3e600756a28485b329bac58c73590e53c4934250f5707a6613ed455fb6c2e97a1a4e1029b3e2abdb6896f27&a=w%3D850%26h%3D474%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A18%3A20.314Z" %}
Bitwarden 应用程序页面
{% endembed %}

记录下 **Integration key**、**Secret key** 和 **API hostname**。当您在 Bitwarden 中设置 Duo 时，需要参考这些值。

### 在 Bitwarden 中设置 Duo <a href="#setup-duo-in-bitwarden" id="setup-duo-in-bitwarden"></a>

{% hint style="warning" %}
最初配置和设置 Duo 后，在从 Duo 管理面板进行任何进一步的应用程序配置更改之前，为组织禁用它**非常重要**。进行配置更改；在 Bitwarden 中禁用 Duo，在 Duo 管理面板中进行必要的更改，然后在 Bitwarden 中重新启用 Duo。

这是因为 Duo for organizations 目前不支持恢复代码。相反，您将需要依靠 Duo 管理面板来绕过无法访问 Duo 的成员的两步登录。在 Duo 处于活动状态时从 Duo 管理面板更改应用程序配置可能会失去绕过您或您组织的成员的两步登录的能力。
{% endhint %}

您必须是组织所有者才能为您的组织设置 Duo。要为您的组织启用 Duo 方式的两步登录：

1、登录您的[网页密码库](https://vault.bitwarden.com/)。

2、打开您的组织然后下拉列表中选择**设置**选项卡。

3、从左侧的设置菜单中选择**两步登录**。

4、定位到 **Duo（组织）** 选项然后选择**管理**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/4bbaa84515dbd8b1b65979c4976ddb00/02be0a0a1922d2ed743e4c57a532c5a9/Screen_Shot_2023-01-31_at_1.45.03_PM.webp?eu=d9dd05b4b79cf9810968a4826075666db23f51a3fa5667866e30b2fd46fe9f8571f11955239d78e02e3d5a8ad0e541bf32932e604bec82dac6ed1ff3ea36a35d51d70ee831e57651567dc3abb8a10e1460c4125cf0d5cd5ea53b7082e0b6bd285d145c68a265a7d8b1f86231f39d7c76bce7e56d3086e866be471a4bcc5a2faf22e191883b43a9c9af1b8dbe9ffd739adaaf6d6519a7b77322174c771a8a49a4adb204773b78140d609aaa599361c5b33e496421585f02f06469d603a83d33c7fb98f21f8c2f258ecb916e34e9c1ae82ee07ac2b6be4ce48f8c6547b1009a90dadbf1497af7a4650d6&a=w%3D850%26h%3D413%26fm%3Dwebp%26q%3D75&cd=2023-02-15T12%3A50%3A03.956Z" %}
为组织管理 Duo
{% endembed %}

将提示您输入主密码以继续。

5、输入从您的 Duo Admin Portal 中获得的 **Integration Key**、**Secret Key** 和 **API Hostname**。

6、选择**启用**按钮。

一个绿色的 `已启用` 消息表明已为您的密码库成功启用了 Duo。通过选择**关闭**按钮并看到 **Duo** 选项上有一个绿色的复选标记（**✔️**）以再次检查。

### 注册设备 <a href="#register-a-device" id="register-a-device"></a>

设置好 Duo 后，您和您的组织成员在下次登录网页密码库时将被要求注册一个两步登录设备：

{% embed url="https://bitwarden.com/_gatsby/image/3b87d5667ea87939c39287d0b2b4b655/b051da7e8d478e8d593b21d1cd47c6e4/enroll1.webp?eu=d8dd02e3b6c9aa86076bf4806f73346ce33f57f8f70560813a60e1ac4bfe9bd02cf4110427c32ce27f6159da85e011be63972b351eb8d2de94ef10f0eb66fc0d5b835cb865e770545079c2fab6a705166f954e58a48b9a0ea1687b85b3bae1781a064f2cf972bd81e4ae3f3cf4c76f71e0a9b9773893fc2da30c0d109d4932bf31ffd3c06d4baad1b75db1b5a8f3089b94ba6a005fde81605b36335d1dbe45bbcce965254b411d0e71a7d8479167c5e46d1e69255f5751a2606b8655fb6f64c2b7fda70bde7b7bb2ad9b33229996f0c2b246f02b68a79170&a=w%3D756%26h%3D569%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A18%3A20.316Z" %}
Duo 设置界面
{% endembed %}

{% hint style="success" %}
如果 Duo 没有要求您注册设备，请尝试使用隐身或隐私浏览窗口登录。
{% endhint %}

按照屏幕上的提示将辅助设备配置为使用 Duo（例如，注册和发送 SMS 或发送推送通知的设备类型）。如果您尚未下载 Duo 移动应用程序，建议您下载：

* [下载 iOS 版](https://itunes.apple.com/us/app/duo-mobile/id422663827?mt=8)
* [下载 Android 版](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile)
{% endtab %}
{% endtabs %}

## 使用 Duo <a href="#use-duo" id="use-duo"></a>

以下内容假设 **Duo** 是您[已启用的最高优先级方式](../two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用两步登录访问您的密码库：

1. 在任一个 Bitwarden 应用程序上输入您的电子邮件地址和主密码以登录密码库。\
   将显示一个 Duo 界面以开始您的两步登录验证。&#x20;
2. 根据您的 Duo 的配置方式，通过以下方式完成验证请求：
   * 从您已注册的设备上批准 **Duo Push** 请求。
   * 在您的 **Duo 移动应用**或**短信**中找到 6 位验证码，并在密码库登录界面输入此验证码。

{% hint style="info" %}
勾选**记住我**方框，以记住您的设备，为期30天。记住你的设备意味着你不会被要求完成两步登陆步骤。
{% endhint %}

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../your-vault/vault-timeout-options.md)。

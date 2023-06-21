# 两步登录-电子邮件

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/setup-two-step-login-email/)
{% endhint %}

电子邮件方式的两步登录对于所有 Bitwarden 用户是免费的。

{% hint style="warning" %}
如果您使用 SSO 登录，则不建议使用电子邮件方式的两步登录，因为使用多个方法会导致错误。可以考虑改为设置[免费的验证器应用程序方式的两步登录](two-step-login-via-authenticator.md)。
{% endhint %}

## 设置电子邮件验证 <a href="#setup-email-verification" id="setup-email-verification"></a>

要启用电子邮件方式的两步登录：

{% hint style="warning" %}
**丢失对两步登录所绑定的电子邮件的访问会永久性将您锁定在您的账户之外**，除非您将您的两步登录恢复代码写下并将其保存在安全的地方，或拥有已启用并可用的备用两步登录方式。

启用任何方式之后，应立即通过**两步登录**界面[获取您的恢复代码](../recovery-codes.md)。
{% endhint %}

1、登录您的[网页密码库](https://vault.bitwarden.com/)。

2、选择个人资料图标并然后下拉列表中选择**账户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?eu=8adb56b0eaccf885076fa2d66f746161e56956aaac0032d43465b6f94bfe9b8e71fa1151289528b0796d528bd7e816bc31c67d691befd18991bc4af4be3da80d07835fb836b07807052ec4fde4a1574d60c11b5fa8d1c90ca76a21ddb4b4e47711571b23ae7ebbd7e8fa3064badb6b76aaf5ac317a9bf629b7471d4a985c27ad27f8c59a7000b09bf400e8a4b0fa4f979db1255a07dcec3226050d762c882bfad0bb5137732f072e7fc6d45fae7e91b13f4934705f0c03a5673a8555fb3863c7b0aef509da7e7ee7fdc06073d0cab1e3be58f97f2888ac7ff6c654780e0fae0eadb966f6d10b574aee2bfa8b4fb61d04352ff36197647e8e&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A24%3A03.707Z" %}
账户设置
{% endembed %}

3、选择**安全**页面和**两步登录**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/825426d227e1afce2f4b644e6a3e9e84/3cbf2a88c5de2a53993ef05ef68dd09e/Screen%20Shot%202022-05-16%20at%2011.13.53%20AM.webp?eu=d8df06efe1ceae815b3ca28a6e76643bb43851ada85931853e36b2a94ffc9e832ca64f5c719328b229695ed7d3b443bc60927d614fe6d58f92bf4af6e33ca35954d05cea61e22452037e91aae3a30e4168c41c50f7d1c95bf66b27d4e2b7e4241b051a28a97ab2d9a8ed7527ba9c306bb7e7f17b26dcf83cb6431d179e5c32e23aeed4c1345cb09df645eeb0e6f44eca83e55f443b98fb3675731f42019e48fcede406206d21434436cbaa0ecf3090b13e4e33220c0b02fe67388452ae6c36c5b5fca45bde2e73e5b7aa6232d396f0ef8e42f36e19e5cf25ab9f3b7f130caa7cfcf814f6d37a070d9f2ff9fa3dcf1d456b17&a=w%3D779%26h%3D301%26fm%3Dwebp%26q%3D75&cd=2022-06-01T12%3A31%3A35.371Z" %}
两步登录
{% endembed %}

4、定位到**电子邮件**选项然后选择**管理**按钮：

{% embed url="https://bitwarden.com/_gatsby/image/3937e1847f4eb5394da447d4a764999e/9cd93fc2542897e9860b9a4630f212f1/twostep-options-emailoverlay.webp?eu=8adb02b2e39afbd40e6ef387607b343de23e55a3fd5164826c67b1fb4baacf8f77f51b0720c02cb97d6f0c8a86b217ec64942d6510bad8dcc6ed11f6ee30a30e07820ebb60b67751592e95fce6a3574c60c31a0ea584ce5da9353690a5f0bd6f0609417aff2ffb9fbfed6335f3c07a76a9a8f87b21ddac3abe41180eca4e79a123bc8fdc524aa484f76be7e5b2f56acbdeb36b7814b8a53d5b684e4b58e925b3a5e30d763c2e110a30caaf5bc565c2b26f1562720b5606f3613ccf11bc337287b1bbbc02993e22bef68a2c25db92f7dcb25cf9682ab68639e9dc6c&a=w%3D754%26h%3D391%26fm%3Dwebp%26q%3D75&cd=2022-01-19T18%3A14%3A59.095Z" %}
选择管理按钮
{% endembed %}

输入主密码以继续。

5、输入您用于接收验证码的电子邮件地址，然后点击**发送电子邮件**按钮。

{% hint style="info" %}
如果您有多个电子邮件地址，用于两步登录的地址不必使用与注册 Bitwarden 时使用的地址相同。
{% endhint %}

6、检查您的收件箱接收到的 6 位验证码，将此代码填入网页密码库的对话框中并选择**启用**按钮。

一个绿色的 `已启用` 消息表明电子邮件方式的两步登录已被启用。

7、单击**关闭**按钮，并确认**电子邮件**选项现在已被启用（通过一个绿色勾号 **✔️** 指示）。

{% hint style="info" %}
我们建议在继续测试两步登录之前保持活动的网页密码库选项卡为打开状态，以防出现配置错误的情况。当您确认它正常工作后，你应该注销所有的 Bitwarden 应用程序，以为每个应用程序立即激活两步登录。您最终会被自动注销。
{% endhint %}

## 使用电子邮件验证 <a href="#use-email-verification" id="use-email-verification"></a>

以下内容假设**电子邮件**是您[已启用的最高优先级方式](../two-step-login-methods.md#using-multiple-methods)。完成以下步骤，以使用两步登录访问您的密码库：

1、在任一个 Bitwarden 应用程序上输入您的电子邮件地址和主密码以登录密码库。\
将提示您**输入发送到你配置的电子邮件的 6 位验证码**。

2、检查您的收件箱接收到的 6 位数验证码。在密码库登录界面输入此代码。

{% hint style="info" %}
勾选**记住我**方框，以记住您的设备，为期30天。记住你的设备意味着你不会被要求完成两步登陆步骤。
{% endhint %}

3、选择**继续**以完成登录。

登录后，您将不会被要求完成第二步的两步登录步骤就可以**解锁**您的密码库。有关配置注销和锁定行为的帮助，请参阅[密码库超时选项](../../your-vault/vault-timeout-options.md)。

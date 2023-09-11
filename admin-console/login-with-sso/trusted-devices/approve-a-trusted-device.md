# 批准受信任设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/approve-a-trusted-device/)
{% endhint %}

当某个组织成员登录新设备时，他们需要批准或信任该设备。其中一种方法是选择**请求管理员批准**选项，将设备批准请求发送给组织内的管理员和所有者进行批准。

{% embed url="https://bitwarden.com/_gatsby/image/2ae6ef9b326ba69fa7233cda5cd242b6/46e040f6b375ce8ca8c6e3e1ae8af9f6/request%20admin%20approval.webp?eu=8e8f50e7b0c0a886093df58a6173616ae76902a2fa5031863932b5ac47aacb8e21a51e04209c7ee3246b59d887e643be32c77f6218ef82dd94ea4aa1eb3daa0b50865eec31b17654032ac0abe5a303173cc11a5ea68ace0df66d74dce0b0e5214d031b2afc7eb082e6f17120f0c0252df5effb7f3297e866b3560805885b24b827a5ce8b7701e98cee4ca9bcefff0190dbe0320239a6894743080e4404be52fed9d47131684b460c5dd1f959c169c0b334193477085b06f735398450a93d38c7b5fbf40c8d737ee2ac9c2e32d382ebd5ae5ec37b22ba9679c6d37b3a4c52ea42f1a23ba985&a=w%3D493%26h%3D550%26fm%3Dwebp%26q%3D75&cd=2023-08-31T17%3A56%3A38.040Z" %}
请求管理员批准
{% endembed %}

作为组织管理员、所有者或具有**管理账户恢复**权限的自定义用户，要批准请求：

1. 航到您的组织管理控制台然后打开**设置** → **设备批准**页面。
2. 选择选项 **☷** 菜单，然后选择 **✔︎批准请求**。

{% embed url="https://bitwarden.com/_gatsby/image/9ffe0eb89aeb96d9c29d4bb930dd3ae6/5049bdb7e379e8a62dd2e6972d51571e/approve%20tde%20edited.webp?eu=8cdc55e7e49ef9855c3aa6803923666ce83650fff95667816936e7af4aaacfd226a61e5122957fe57e600eddd3b243be6f937c6219bcd88f92e91ffceb35aa0b01820be967e779515b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b92f3ca2ee3ab5410917906738b864c5e7aa5147babccd00ece2e8ac0ec59ae27c0541ddf1602a774c1c5aea78bfa3e00627302f110d35cfb0098721d4e97a490e670a0a6ca233639400af72719db3&a=w%3D850%26h%3D422%26fm%3Dwebp%26q%3D75&cd=2023-08-31T17%3A56%3A55.015Z" %}
批准 TDE 请求
{% endembed %}

{% hint style="info" %}
当成员请求设备批准时，指纹短语会显示在成员的设备上。可以通过检查该指纹短语与成员栏中显示的指纹短语是否一致来执行附加验证。此方法是可选的，需要提出请求的成员与管理员之间**进行同步通信**。
{% endhint %}

当设备请求获得批准后，请求用户会收到一封电子邮件，通知他们可以继续在该设备登录。用户必须在 12 小时内登录新设备，否则批准将失效。

未批准的请求将在 1 周后失效。您可以通过选择 **✘拒绝请求**来拒绝登录尝试，或者通过选择最上面的选项 **☷** 菜单然后选择 **✘拒绝所有请求**来拒绝所有现有请求。

事件在以下情况下被记录：

* 用户请求设备批准。
* 设备请求被批准。
* 设备请求被拒绝。

# 批准受信任设备

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/approve-a-trusted-device/)
{% endhint %}

当某个组织成员登录新设备时，他们需要[批准或信任该设备](../../../account/log-in-and-unlock/using-single-sign-on/add-a-trusted-device.md)。其中一种方法是选择**请求管理员批准**选项，将设备批准请求发送给组织内的管理员和所有者进行批准。

{% embed url="https://bitwarden.com/_gatsby/image/2ae6ef9b326ba69fa7233cda5cd242b6/46e040f6b375ce8ca8c6e3e1ae8af9f6/request%20admin%20approval.webp?eu=8e8f50e7b0c0a886093df58a6173616ae76902a2fa5031863932b5ac47aacb8e21a51e04209c7ee3246b59d887e643be32c77f6218ef82dd94ea4aa1eb3daa0b50865eec31b17654032ac0abe5a303173cc11a5ea68ace0df66d74dce0b0e5214d031b2afc7eb082e6f17120f0c0252df5effb7f3297e866b3560805885b24b827a5ce8b7701e98cee4ca9bcefff0190dbe0320239a6894743080e4404be52fed9d47131684b460c5dd1f959c169c0b334193477085b06f735398450a93d38c7b5fbf40c8d737ee2ac9c2e32d382ebd5ae5ec37b22ba9679c6d37b3a4c52ea42f1a23ba985&a=w%3D493%26h%3D550%26fm%3Dwebp%26q%3D75&cd=2023-08-31T17%3A56%3A38.040Z" %}
请求管理员批准
{% endembed %}

作为组织管理员、所有者或具有**管理账户恢复**权限的[自定义用户](../../user-management/member-roles-and-permissions.md#custom-role)，要批准请求：

1、登录到 Bitwarden 网页 App 然后使用产品切换器打开「管理控制台」：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、从导航栏选择**设置** → **设备批准**。

3、使用选项 **☷** 菜单，选择 **✔︎批准请求**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1iPurecgskOyt0NGDRidBM/3a85c233b2a208dc2c939c8e79fd9b4f/Screenshot_2024-02-29_at_10.52.50_AM.png?_a=DAJAUVWIZAAB" %}
批准设备请求
{% endembed %}

{% hint style="info" %}
当成员请求设备批准时，指纹短语会显示在成员的设备上。可以通过检查该指纹短语与成员栏中显示的指纹短语是否一致来执行附加验证。此方法是可选的，需要提出请求的成员与管理员之间**进行同步通信**。
{% endhint %}

## 批量批准请求 <a href="#bulk-approve-requests" id="bulk-approve-requests"></a>

使用顶部的选项 **☷** 菜单然后选择 **✔︎批准所有请求**，可以一次批准多个设备请求。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4ozBvrFFLPYcRmuCWNCuCz/504a206008a06c4e98d0058478f21d26/TDE_Bulk_Device_sc3.png?_a=DAJAUVWIZAAB" %}
批准或批量批准设备
{% endembed %}

{% hint style="danger" %}
使用**批准所有请求**选项进行批量设备批准可能会忽略管理员为确保请求合法而执行的验证步骤，例如检查用户报告的指纹短语。

Bitwarden 建议在启用和使用批量设备批准之前，先审查重要的安全控制措施，例如 IdP 凭证标准、IdP MFA 以及 IdP 设备注册和信任。
{% endhint %}

当设备请求获得批准后，请求用户会收到一封电子邮件，通知他们可以继续在该设备登录。用户必须在 12 小时内登录新设备，否则批准将失效。

未批准的请求将在 1 周后失效。您可以通过选择 **✘拒绝请求**来拒绝登录尝试，或者通过选择最上面的选项 **≡**&#x83DC;单然后选择 **✘拒绝所有请求**来拒绝所有现有请求。

[事件](../../reporting/event-logs.md)在以下情况下被记录：

* 用户请求了设备批准。
* 设备请求被批准。
* 设备请求被拒绝。

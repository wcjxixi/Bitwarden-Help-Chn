# 更改成员的账户电子邮箱 & 名称

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/change-members-account-email-and-name/)
{% endhint %}

在企业版方案中，组织可以直接从 Admin Console 更新符合条件的成员的账户电子邮箱地址和名称。这让管理员能够在成员发生法律名称更新等变更后保持成员记录的准确性，节省时间并保留成员现有密码库的访问权限。

此选项仅适用于使用 Key Connector SSO 或受信任设备 SSO 而非主密码的已声明的账户。虽然拥有主密码的账户不符合此选项的条件，但这些成员可以[更新其自己的主密码](../../account/master-password.md#change-your-master-password)。

## 要求 <a href="#requirements" id="requirements"></a>

[所有者、管理员](member-roles.md#default-roles)或拥有[管理用户权限](member-roles.md#custom-roles)的自定义用户可以更新成员的账户电子邮箱地址和名称。

要符合管理员更新的条件，成员的账户必须满足两个要求：

* 该账户必须是[已声明的账户](../oversight-visibility/claimed-domains/claimed-accounts.md)，且属于[已声明的域名](../oversight-visibility/claimed-domains/claimed-domains.md)。
* 该账户不能设置主密码。这意味着您的组织必须使用 [Key Connector](../../self-hosting/key-connector/about-key-connector.md) 或[受信任设备](../login-with-sso/trusted-devices/about-trusted-devices.md)，并且该特定成员未设置或保留主密码。例如，在配置受信任设备之前加入的成员可能仍设置有主密码。在这种情况下，其账户不符合由管理员更改电子邮箱的条件。

{% hint style="info" %}
如果成员设置有主密码，您仍然可以更新名称。但是，您将无法更新账户电子邮箱。
{% endhint %}

## 更改成员的账户电子邮箱 & 名称 <a href="#change-a-member-s-email-and-name" id="change-a-member-s-email-and-name"></a>

要更改[符合条件的成员](change-members-account-email-and-name.md#requirements)的账户电子邮箱地址或名称：

1、登录 Bitwarden 网页 App，然后使用产品切换器打开 Admin Console：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?w=1013&#x26;fm=avif" alt=""><figcaption><p>产品切换器</p></figcaption></figure></div>

2、在 Admin Console 中，选择**成员**。

3、选择您要更新的成员。将出现一个弹出窗口。

4、根据需要更新的内容：

* 输入新的**名称**。
* 输入新的**电子邮箱**。电子邮箱必须使用您组织已声明的域名。

5、选择**保存**。

您的更改被保存后：

* 该成员的活动会话会保持登录状态。
* [事件日志](../oversight-visibility/event-logging/event-logs.md#organization-events)会记录谁编辑了该成员。如果电子邮箱被更改，第二条事件日志会记录谁进行了此更新。
* 如果您更新了电子邮箱，Bitwarden 会向该成员的原始电子邮箱地址发送一条消息。该消息说明管理员更改了其账户电子邮箱，并包含新的地址。此消息不会提及名称变更，如果您仅更新名称，Bitwarden 不会发送任何消息。

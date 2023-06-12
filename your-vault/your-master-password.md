# 主密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/master-password/)
{% endhint %}

主密码是访问密码库的主要方法。您的主密码非常重要：

* **好记**：Bitwarden 的员工以及 Bitwarden 系统对您的主密码一无所知、没有办法找回或重置您的主密码。**千万不要忘记你的主密码！**
* **强大**：您的主密码越长、越复杂、越不常见，您的密码库数据就越安全。使用我们提供的免费[**密码强度测试工具**](https://bitwarden.com/password-strength)来测试您考虑使用的密码的强度。

{% hint style="success" %}
担心忘记您的主密码吗？这里有一些建议：

* **设置主密码提示**。如果您需要提醒，可以在登录屏界面请求主密码提示电子邮件。确保使用只有您自己能理解的提示。
* **指定一个**[**可信紧急联系人**](../security/emergency-access.md)。具有高级访问权限的用户可以在紧急情况下将密码库的访问权限授予朋友或家人。
{% endhint %}

## 更改主密码 <a href="#change-your-master-password" id="change-your-master-password"></a>

如果您知道当前的主密码，您可以通过[网页密码库](../getting-started/getting-started-webvault.md)更改它：

{% hint style="info" %}
如果您不知道主密码，请参阅[我忘记了主密码](i-forgot-my-master-password.md)**。**
{% endhint %}

1、在您的网页密码库中，选择配置文件图标并从下拉菜单中选择**帐户设置**：

{% embed url="https://bitwarden.com/_gatsby/image/551bb080111e018406d626c015cebc1a/3c147dfab42b00c5b359562da41d2951/Screen%20Shot%202022-05-13%20at%2010.34.10%20AM.webp?eu=deda01b4b0ccfcd35b6ea18b6a77323fb56e02fdaa0434813b64e0a61bad9d8125f64a50749379b0286d08dad5e247bb6fc679611ebad7d2c2e84bf6ee61fc09548458ec64b32207022897fdb5f650166dc21d5da883c250e7293297efaca82944014b7eeb64ebc5baf87627e5c76c2cb4e3e2316280f52ba6485f02c34536fb7bbc94ac72779aabb65e9aefbbef43cbdb92670f3bdc9a2a25704f4a0dbe2ce8a5e004716c29400f67cafb0d933595b2391a342a0f5c55fe78598317ae396fac87a3fe19b6787be3aad431759bc2adefbc5ec32b76f9cc23b7833b157f70b253f3eb&a=w%3D773%26h%3D226%26fm%3Dwebp%26q%3D75&cd=2022-12-09T16%3A24%3A03.707Z" %}
帐户设置
{% endembed %}

2、从帐户设置菜单中，选择**安全**页面然后选择**主密码**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/82dc1e10acd6b282f4317b244932e543/d92f5b96435267bda87757fbeaa7f5a5/Screen%20Shot%202023-03-06%20at%202.05.47%20PM.webp?eu=dcdc03e5b2cdfcd6086ff3833a72326ee93f04aea85764856c6ce4ac19a1988525a51b57239d29e4786a5ddbd2b541bd63942c601bbad0dcc9be1ca0b930ff5a548758e632b2760e5823c5fab5a402426e901000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41a12ba22bbf0996f66e797b77c8c9de9aa5d91daee5c18118efb3577741f1a5fe824bef3b202723e7d495f309ffd58956895b66f183277413c50b5326f8e3a98346e878bf9a15fda677be2b5c9371fd787c182f31aa93472e0a047d49c7b2459&a=w%3D850%26h%3D548%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.660Z" %}
更改主密码
{% endembed %}

3、输入您的**当前主密码**。

4、输入并确认您的**新主密码**。

5、如果您想在提交主密码之前通过 HIBP 检查您的主密码，请选中**检查密码的已知数据泄露**（[了解更多](vault-health-reports.md#data-breach-report-individual-vaults-only)）复选框。要运行此报告，您的主密码的哈希值将发送到 HIBP，并与存储的公开哈希值进行比较。 Bitwarden 永远不会暴露您的主密码本身。

{% hint style="warning" %}
除非您完全了解其后果和所需的后续步骤，否则请不要选中**同时轮换帐户加密密钥**复选框。[了解更多](../security/account-encryption-key.md)。
{% endhint %}

6、选择**更改主密码**按钮。

更改主密码将会自动注销网页密码库会话，并要求您使用新的主密码重新登录。当前已登录的客户端应用程序可能保持活动状态长达一小时，但最终也会要求您使用新的主密码重新登录。

## 我忘记了主密码 <a href="#i-forgot-my-master-password" id="i-forgot-my-master-password"></a>

了解如果您[忘记了主密码](i-forgot-my-master-password.md)该怎么做。

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

现在您已经创建了**好记**且**强大**的主密码，我们建议：

* [通过两步登录进一步保护您的密码库](../two-step-login/two-step-login-methods.md)
* [启用紧急访问](../security/emergency-access.md)（需要付费）

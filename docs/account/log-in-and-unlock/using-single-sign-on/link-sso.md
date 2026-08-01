# 链接 SSO

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/link-sso/)
{% endhint %}

通常情况下，只有在您使用**已有的 Bitwarden 账户**加入组织时，或组织未强制[要求使用 SSO](../../../admin-console/oversight-visibility/enterprise-policies.md#require-single-sign-on-authentication) 时，才需要链接 SSO。要链接到 SSO：

1、打开网页 App，点击您的组织旁的 <i class="fa-ellipsis-vertical">:ellipsis-vertical:</i>**选项**菜单。

2、从下拉菜单中，选择 <i class="fa-link">:link:</i>**链接 SSO**。

<div data-with-frame="true"><figure><img src="https://bitwarden.com/assets/cv0DGhcgyEbQEn4MvdJp5/fefb4158c09be8cf9804ed5579c2d7dc/Screenshot_2024-02-26_at_2.07.03_PM.png?w=1331&#x26;fm=avif" alt=""><figcaption><p>连接 SSO</p></figcaption></figure></div>

链接完成后，您即可以[使用 SSO 登录到账户](using-login-with-sso.md)了。

{% hint style="info" %}
链接后，您可以从同一菜单**取消链接 SSO**。此功能主要适用于以下场景：您的身份提供程序 (IdP)（例如 Google、Azure) 或 Bitwarden 中的电子邮件地址发生更改，导致 SSO 失效时；或者 IdP 身份链接到了错误的 Bitwarden 账户时，需先断开现有链接才能建立正确的链接。
{% endhint %}

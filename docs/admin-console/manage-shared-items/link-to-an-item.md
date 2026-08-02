# 组织项目超链接

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/link-to-an-item/)
{% endhint %}

当您需要将组织的成员定向到特定的密码库项目时，例如在文档中，您可以复制项目的 URL 以用作**拥有此项目的访问权限**的用户的直接链接。

{% hint style="success" icon="lightbulb" %}
项目链接不是组织独有的！如果您觉得有用，可以将链接保存到您的个人密码库中，但是只有您自己可以访问它们。
{% endhint %}

当您在网络密码库中查看某个项目时，地址栏中的 URL 将包含一个查询参数，例如 `?cipherId=fced56b3-d83c-4b01-8751-ae9301551da7`，其中的 `cipherId` 的值代表唯一的项目标识符：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6v3WH6FljmTFOlSqOjjAqZ/a9c1ae50155e6692d52987fe4f0cc888/2024-12-04_09-55-51.png?w=1175&#x26;fm=avif" alt=""><figcaption><p>项目链接</p></figcaption></figure></div>

复制地址栏中的完整值并使用该链接将组织成员直接定向到该项目。当用户使用此链接时，此项目将在他们登录后自动打开。要成功使用链接，用户**必须已经拥有此项目的访问权限**。

{% hint style="info" %}
除非用户在已登录了 Bitwarden 的浏览器选项卡中打开该链接，否则**他们需要登录**。例如，大多数浏览器默认在新选项卡中打开单击的链接，因此需要用户登录。登录后，密码库项目将自动打开。
{% endhint %}

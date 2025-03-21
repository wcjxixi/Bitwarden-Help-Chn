# 链接到项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/link-to-an-item/)
{% endhint %}

当您需要将组织的成员定向到特定的密码库项目时，例如在文档中，您可以复制项目的 URL 以用作**有权访问此项目**的用户的直接链接。

{% hint style="success" %}
项目链接不是组织独有的！如果您觉得有用，可以将链接保存到您的个人密码库中，但是只有您自己可以访问它们。
{% endhint %}

当您在网络密码库中查看某个项目时，地址栏中的 URL 将包含一个查询参数，例如 `?cipherId=fced56b3-d83c-4b01-8751-ae9301551da7`，其中的 `cipherId` 的值代表唯一的项目标识符：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6v3WH6FljmTFOlSqOjjAqZ/a9c1ae50155e6692d52987fe4f0cc888/2024-12-04_09-55-51.png?_a=DAJCwlWIZAAB" %}
项目链接
{% endembed %}

复制地址栏中的完整值并使用该链接将组织成员直接定向到该项目。当用户使用此链接时，此项目将在他们登录后自动打开。要成功使用链接，用户**必须已经拥有该项目的访问权限**。

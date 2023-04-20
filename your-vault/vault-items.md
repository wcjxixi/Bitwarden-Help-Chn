# 密码库项目

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/managing-items/)
{% endhint %}

有效地管理密码库中的项目，是确保安全且无缝访问您的信息，并与朋友、家人、团队和同事安全地共享信息的关键。在密码库中可以存储 4 种类型的项目：登录、支付卡、身份和安全笔记：

{% tabs %}
{% tab title="登录" %}
登录项目常用于存储用户名和密码的组合，并支持针对高级用户的 [TOTP 种子](totp.md)。无论您使用的是何种计划，我们都建议为每个登录提供[一个用于方便自动填充的 URI](../auto-fill/using-uris.md)：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5VGRnEvX53BOXa9CCgrhRx/53011df37187b2f37484bf25cce5490c/login-item.png?fm=webp&h=363&q=50&w=732" %}
{% endtab %}

{% tab title="支付卡" %}
支付卡项目可用于存储信用卡或借记卡信息：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/UW8udnRVCQlJyIaCtmG2a/d68082b5cb70787d850843e57dcd812f/card-item.png?fm=webp&h=403&q=50&w=728" %}
{% endtab %}

{% tab title="身份" %}
身份信息可用于存储账单信息、邮寄信息或其他任何你在填写在线表格时可能需要访问的信息：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6R14M0PBJL8RaAP4ye3P4O/246db985ed503b232ce67aae4a5728c1/identity-item.png?fm=webp&h=810&q=50&w=728" %}
{% endtab %}

{% tab title="安全笔记" %}
安全记事本可用于存储被加密的你想要保护的任何自由格式的文本信息：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7dkefRm7YAdn1e3FmxgCeN/7691989f4535bf2a5931f8a0fbfa4cd3/note-item.png?fm=webp&h=368&q=50&w=728" %}
{% endtab %}
{% endtabs %}

{% hint style="success" %}
您可以从大多数密码管理器或 Web 浏览器将项目直接导入到您的密码库。[了解更多](../import-export/import-data-to-your-vault.md)。
{% endhint %}

## 管理密码库项目 <a href="#manage-vault-items" id="manage-vault-items"></a>

您可以通过任何 Bitwarden 客户端应用程序添加、编辑和删除密码库项目：

{% tabs %}
{% tab title="网页密码库" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3DW8eh1BQbXObEReorFMW4/d9b74fb434903047f0bd1105ec0fa9be/manage-webvault.png?fm=webp&h=480&q=50&w=764" %}
管理项目
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/1OddsCwTDlM6yeTNM9GABo/5e5d5da58061d5530643e13aa5a36e7d/manage-be.png?fm=webp&h=821&q=50&w=1070" %}
{% endtab %}

{% tab title="移动端" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6l8JWKYvh6tVEAY98V5z91/37f876d8250817ea3cf16f00339cefad/manage-mobile-1.png?fm=webp&h=1461&q=50&w=1899" %}
{% endtab %}

{% tab title="桌面端" %}
{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/25mBh7DRc8X3eZGWFPFZVf/47f8887ca55d06a2ebcfe7dac2b8137b/manage-desktop.png?fm=webp&h=681&q=50&w=980" %}
{% endtab %}

{% tab title="CLI" %}
更多信息，请参阅 [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

除了添加、编辑和删除密码库项目之外，您还可以[克隆](vault-items.md#clone)项目以创建副本、[移动项目](vault-items.md#move-to-organization)到组织以及[保护个人项目](vault-items.md#protect-individual-items)。

### 克隆 <a href="#clone" id="clone"></a>

如果您想创建一个项目的副本，您可以克隆对其具有**所有权**的任何密码库项目：

{% tabs %}
{% tab title="网页密码库" %}
在悬停 **⚙️齿轮**下拉菜单中选择**克隆**。
{% endtab %}

{% tab title="浏览器扩展" %}
打开项目然后选择 :dividers:**克隆项目**选项。
{% endtab %}

{% tab title="移动端" %}
打开项目然后在 **≡菜单**中选择**克隆**。
{% endtab %}

{% tab title="桌面端" %}
打开项目然后选择 :dividers:**克隆项目**选项。
{% endtab %}
{% endtabs %}

要克隆组织拥有的项目，必须从[组织密码库视图](../admin-console/organizations-quick-start.md#get-to-know-your-organization)中克隆它。

### 移动到组织 <a href="#move-to-organization" id="move-to-organization"></a>

如果您是[组织](../organizations/organizations.md)的成员，您可以将密码库项目移动到组织，以便于与其他成员共享。了解更多关于[组织](broken-reference)、[集合](../organizations/collections.md)和[共享](../organizations/sharing.md)的信息。

### 保护个人项目 <a href="#protect-individual-items" id="protect-individual-items"></a>

对于任何项目，您可以从添加/编辑界面激活**主密码重新提示**选项，以要求验证您的主密码以访问或自动填充敏感的密码库项目：

{% hint style="warning" %}
主密码重新提示**并非**一种加密机制。此功能是一个仅限于界面的防护栏，老练的用户可能会找到解决方法。我们建议您在无人看守或在共享工作站上，不要让您的密码库处于解锁状态。
{% endhint %}

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/sgKb0RX5hGdrdKLmXcR0R/b3f47ef1fd351c7f02b3a9b86baf3bca/reprompt.gif?fm=gif&h=818&q=50&w=1036" %}
主密码重新提示
{% endembed %}

## 密码库回收站 <a href="#vault-trash" id="vault-trash"></a>

已删除的项目将被发送到回收站，删除后它们会保留 30 天。30 天过后，该项目将被永久删除且不可恢复。

在回收站中，您可以在 30 天等待期之前将项目**恢复**到您的密码库或**永久删除**它：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/36mo5LyroRq1BhOcjSsBb7/4d558b0fdcc22a09e52e08f5fc754a9f/item-trash-restore-delete.png?fm=webp&h=227&q=50&w=570" %}
回收站
{% endembed %}

## 后续步骤 <a href="#next-steps" id="next-steps"></a>

现在，您已了解密码库项目使用的基础知识，我们建议：

* 使用[收藏](favorites.md)和[文件夹](folders.md)组织您的密码库项目
* 将[自定义字段](custom-fields.md)、[TOTP 种子](totp.md)和[文件附件](file-attachments.md)添加到密码库项目

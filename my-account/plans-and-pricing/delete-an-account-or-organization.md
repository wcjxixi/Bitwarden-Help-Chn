# 删除账户或组织

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/delete-your-account/)
{% endhint %}

删除 Bitwarden 账户或组织将永久删除该账户或组织以及**与之相关联的所有数据**。Bitwarden不会「软删除」任何数据。

删除账户或组织并不会自动取消订阅。如果你要离开 Bitwarden，你应该先从**设置** → **高级会员**或**组织设置** → **订阅**页面取消你的订阅。

如果您被锁定在您的密码库之外，并且想删除您的帐户，以便您可以创建一个新的帐户，请[联系我们](https://bitwarden.com/contact/)，我们可以帮助将您的订阅转移到新的帐户。

{% hint style="warning" %}
此操作是永久性的，无法撤消。
{% endhint %}

## 删除个人账户 <a href="#delete-your-personal-account" id="delete-your-personal-account"></a>

{% tabs %}
{% tab title="无需登陆" %}
要无需登录删除您的帐户（例如，如果您丢失了主密码）：

1. 在网页浏览器中打开 [https://vault.bitwarden.com/#/recover-delete](https://vault.bitwarden.com/#/recover-delete)。
2. 输入与帐户关联的**电子邮件地址**以发送一个删除确认的电子邮件。
3. 在您的收件箱中，打开邮件并确认您要删除此 Bitwarden 账户。

如果您删除帐户后要创建一个新的帐户，请执行后续步骤：

* 如果您删除了与高级订阅相关联的 Bitwarden 帐户，请[联系我们](https://bitwarden.com/contact/)，我们会将您现有的订阅重新应用到新的帐户中。
* 如果您能够在删除前成功导出密码库数据，则可以轻松地将其[导入新的帐户](../../password-manager/import-and-export/import-data-to-your-vault.md)。
{% endtab %}

{% tab title="网页密码库" %}
要从网页密码库中删除您的 Bitwarden 帐户：

1、选择配置文件图标然后从下拉列表中选择**帐户设置**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/74BqYDU6qE9evz6wEz8K7Y/773eec1c0b00e00db4dedd3456e9a3f9/Screen_Shot_2022-05-13_at_10.34.10_AM.png?fm=webp&h=226&q=50&w=773" %}
账户设置
{% endembed %}

2、在**我的帐户**页面上，向下滚动到**危险区域**并选择**删除帐户**。

将提示您输入主密码，以确认您有权执行此操作。
{% endtab %}

{% tab title="移动端" %}
要从移动应用程序中删除您的 Bitwarden 帐户：

1. 选择**设置**选项卡。
2. 滚动到底部并选择**删除帐户**。
3. 选择**删除帐户**按钮。

将提示您输入主密码，以确认您有权执行此操作。
{% endtab %}
{% endtabs %}

## 删除组织 <a href="#delete-an-organization" id="delete-an-organization"></a>

{% hint style="info" %}
只有组织的**所有者**才有权删除组织。更多信息，请参阅[用户类型和访问控制](../../admin-console/user-management/user-types-and-access-control.md)。
{% endhint %}

1. 在[网页密码库](https://vault.bitwarden.com/)中，打开您的组织。
2. 在组织密码库中，选择**设置**标签。
3. 在**我的组织**页面，向下滚动到**危险操作区**然后选择**删除组织**。

将提示您输入主密码，以确认您有权执行此操作。

# 删除账户或组织

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/delete-your-account/)
{% endhint %}

删除 Bitwarden 账户或组织将永久删除该账户或组织以及**与之相关联的所有数据**。Bitwarden不会「软删除」任何数据。

删除账户或组织并不会自动取消订阅。如果你要离开 Bitwarden，你应该先从**设置** → **高级会员**或**组织设置** → **订阅**页面取消你的订阅。

如果您被锁定在您的密码库之外，并且想删除您的账户，以便您可以创建一个新的账户，请[联系我们](https://bitwarden.com/contact/)，我们可以帮助将您的订阅转移到新的账户。

{% hint style="warning" %}
此操作是永久性的，无法撤消。
{% endhint %}

## 删除个人账户 <a href="#delete-your-personal-account" id="delete-your-personal-account"></a>

{% tabs %}
{% tab title="无需登陆" %}
要无需登录删除您的账户（例如，如果您丢失了主密码）：

1. 在网页浏览器中打开 [https://vault.bitwarden.com/#/recover-delete](https://vault.bitwarden.com/#/recover-delete)（或 [https://vault.bitwarden.eu/#/recover-delete](https://vault.bitwarden.eu/#/recover-delete)）。
2. 输入与账户关联的**电子邮箱地址**以发送一个删除确认的电子邮件。
3. 在您的收件箱中，打开邮件并确认您要删除此 Bitwarden 账户。

如果您删除账户后要创建一个新的账户，请执行后续步骤：

* 如果您删除了与高级订阅相关联的 Bitwarden 账户，请[联系我们](https://bitwarden.com/contact/)，我们会将您现有的订阅重新应用到新的账户中。
* 如果您能够在删除前成功导出密码库数据，则可以轻松地将其[导入新的账户](../password-manager/import-and-export/import-data.md)。
{% endtab %}

{% tab title="网页 App" %}
要从网页 App 删除您的 Bitwarden 账户：

1、导航到**设置** → **我的账户**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/74BqYDU6qE9evz6wEz8K7Y/739550589956c63e6916a41907f43a77/2024-12-04_10-31-23.png?_a=DAJCwlWIZAAB" %}
我的账户
{% endembed %}

2、向下滚动到**危险区域**并选择**删除账户**。

将提示您输入主密码，以确认您有权执行此操作。
{% endtab %}

{% tab title="移动端" %}
要从移动 App 删除您的 Bitwarden 账户：

1. 选择**设置**选项卡。
2. 选择**账户安全**。
3. 滚动到底部并选择**删除账户**。
4. 确认您要**删除账户**。

将提示您输入主密码，以确认您有权执行此操作。
{% endtab %}
{% endtabs %}

## 删除组织 <a href="#delete-an-organization" id="delete-an-organization"></a>

{% hint style="info" %}
只有[组织的所有者](../admin-console/manage-members/member-roles-and-permissions.md)才有权执行这个操作。
{% endhint %}

1、使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**设置** → **组织信息**。

3、向下滚动到**危险操作区**然后选择**删除组织**。

将提示您输入主密码，以确认您有权执行此操作。

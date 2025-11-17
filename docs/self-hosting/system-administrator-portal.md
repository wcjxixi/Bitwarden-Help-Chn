# 系统管理员门户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/admin-portal/)
{% endhint %}

Bitwarden 系统管理员门户可以用于：

* 检查[当前已安装的版本和最新的可用版本](../security/software-development/versioning.md#self-hosted-server-version)。
* 查看[环境配置设置](deploy-and-configure/configuration-options/environment-variables.md)。
* 查看和[删除已注册的用户](../admin-console/manage-members/revoke-remove/delete-member-accounts.md)。
* 查看和删除已注册的组织。

{% hint style="info" %}
系统管理员门户**不提供**对服务器用户或组织的受保护数据（例如密码库项目）的访问权限。
{% endhint %}

## 配置用户访问权限 <a href="#configure-user-access" id="configure-user-access"></a>

用户将使用发送到其电子邮箱收件箱的安全魔术链接登录系统管理员门户。要配置谁有权访问权限，请添加授权的电子邮箱地址：

{% hint style="success" %}
由于系统管理员门户使用电子邮箱来授权用户的访问权限，因此您需要在任何用户尝试登录门户之前设置 SMTP 邮件服务器。

另请注意，授权使用系统管理员门户的电子邮箱不需要是在您的服务器上使用相同电子邮箱地址的 Bitwarden 账户。
{% endhint %}

{% tabs %}
{% tab title="Docker" %}
将以逗号分隔的授权电子邮箱地址列表添加到您的 `global.override.env` 文件中的 `adminSettings__admins=` 变量中：

```systemd
adminSettings__admins=john@example.com,bill@example.com,tom@example.com
```

**每当您对 `global.override.env` 进行更改时，请执行 `./bitwarden.sh restart` 以应用您的配置更改。**
{% endtab %}

{% tab title="Helm" %}
将以逗号分隔的授权电子邮箱地址列表添加到您的 `my-values.yaml` 文件中的 `general.admins:` 值中：

```systemd
...
# Comma-separated list of email addresses for Admin users
  admins: john@example.com,bill@example.com,tom@example.com
...
```

**每当您对 `my-values.yaml` 进行更改时，请执行 `helm upgrade` 以应用您的配置更改。**
{% endtab %}
{% endtabs %}

### 配置 SMTP 邮件服务器 <a href="#configure-smtp-mail-server" id="configure-smtp-mail-server"></a>

系统管理员门户使用电子邮件来提供安全的链接用于验证。因此，在尝试登录到管理门户之前，您需要配置实例的 SMTP 邮件服务器设置。有关更多信息，请参阅[配置环境变量](deploy-and-configure/configuration-options/environment-variables.md)。

## 访问管理门户 <a href="#access-the-admin-portal" id="access-the-admin-portal"></a>

您的服务器的系统管理员门户位于 `https://<your.domain.com>/admin`。当某个用户尝试登录时，**仅**当使用上述过程授权的电子邮箱地址时，才会将安全链接发送到其电子邮箱地址。

点击该临时链接（在尝试登录后 15 分钟内有效）将使该用户登录到系统管理员门户。

# 系统管理员门户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/admin-portal/)
{% endhint %}

Bitwarden 系统管理员门户可以用于：

* 检查当前已安装的版本和最新的可用版本。
* 查看环境配置设置（更多信息，请参阅[配置环境变量](configure-environment-variables.md)）。
* 查看和删除已注册的用户。
* 查看和删除已注册的组织。

{% hint style="info" %}
已配置的管理员无法查看在任何用户或组织的密码库中受保护（加密）的敏感数据。
{% endhint %}

## 配置用户 <a href="#configure-users" id="configure-users"></a>

通过编辑位于 `./bwdata/env/global.override.env` 的环境文件来配置对管理门户的访问权限。

在位于 `global.override.env` 底部的 `adminSettings__admins=` 中添加电子邮箱地址，将为该电子邮箱地址提供访问管理门户的权限。您可以在该字段中指定多个管理员。例如：

```systemd
adminSettings__admins=john@example.com,bill@gmail.com,tom@example.com
```

这些电子邮箱地址**不需要**是在您的 Bitwarden 实例上已注册的帐户。

### 配置 SMTP 邮件服务器 <a href="#configure-smtp-mail-server" id="configure-smtp-mail-server"></a>

系统管理员门户使用电子邮件来提供安全的链接用于验证。因此，在尝试登录到管理门户之前，您需要配置您的实例的 SMTP 邮件服务器设置。有关更多信息，请参阅[配置环境变量](configure-environment-variables.md)。

## 访问管理门户 <a href="#access-the-admin-portal" id="access-the-admin-portal"></a>

您的实例的系统管理员门户位于 `https://your.domain.com/admin`。

该门户使用安全的无密码认证方式。当用户尝试登录时，**仅**向在 `adminSettings__admins=` 中指定的电子邮箱地址发送一个安全链接。

点击该临时链接将使该用户登录到系统管理员门户。该链接在尝试登录后的 15 分钟内有效。

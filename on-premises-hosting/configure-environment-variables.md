# 配置环境变量

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/environment-variables/)
{% endhint %}

Bitwarden 的某些功能无法使用安装程序 `bitwarden.sh` 来配置，需要通过编辑环境文件（`./bwdata/env/global.override.env`）来配置这些设置。`global.override.env` 中预置了一些可配置的变量（参阅[已有变量](configure-environment-variables.md#included-variables)），还有一些额外的变量可以手动添加（参阅[可选变量](configure-environment-variables.md#optional-variables)）。

**每当您对 `global.override.env` 做了修改后，请执行 `./bitwarden.sh rebuild` 以应用您的更改。**

{% hint style="info" %}
本文不会定义每一个环境变量，而是重点介绍大多数安装所使用或配置的环境变量。
{% endhint %}

## 已有变量 <a href="#included-variables" id="included-variables"></a>

以下变量是 `global.override.env` 中已经存在的变量：

| 变量                                               | 描述                                                                                                                                                                                                                                    |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| globalSettings\_\_sqlServer\_\_connectionString= | 使用此字段[连接到外部 MSSQL 数据库](connect-to-an-external-mssql-database.md)。                                                                                                                                                                     |
| globalSettings\_\_oidcIdentityClientKey=         | 随机生成的 OpenID Connect 客户端密钥。有关更多信息，请参阅 [OpenID 文档](https://openid.net/specs/openid-connect-registration-1\_0.html#RegistrationResponse)。                                                                                               |
| globalSettings\_\_duo\_\_aKey=                   | 随机生成的 Duo 密钥。有关更多信息，请参阅 [Duo 文档](https://duo.com/docs/duoweb-v2#1.-generate-an-akey)。                                                                                                                                                 |
| globalSettings\_\_yubico\_\_clientId=            | <p>YubiCloud 验证服务或自托管的 Yubico 验证服务器的客户端 ID。</p><p><br>如果是 YubiCloud，请在<a href="https://upgrade.yubico.com/getapikey/">此处</a>获取您的客户端 ID 和安全密钥。<br>如果是自托管 Yubico 验证服务器，请参阅可选变量 <code>globalSettings__yubico__validationUrls</code>。</p> |
| globalSettings\_\_yubico\_\_key=                 | <p>YubiCloud 验证服务或自托管的 Yubico 验证服务器的安全密钥。</p><p><br>如果是 YubiCloud，请在<a href="https://upgrade.yubico.com/getapikey/">此处</a>获取您的客户端 ID 和安全密钥。<br>如果是自托管 Yubico 验证服务器，请参阅可选变量 <code>globalSettings__yubico__validationUrls</code>。</p>   |
| globalSettings\_\_mail\_\_replyToEmail=          | 用于邀请的电子邮件地址，通常为 `no_reply@smpt__host`。                                                                                                                                                                                                |
| globalSettings\_\_mail\_\_smtp\_\_host=          | 您的 SMTP 服务器的主机名（建议）或 IP 地址。                                                                                                                                                                                                           |
| globalSettings\_\_mail\_\_smtp\_\_port=          | SMTP 服务器使用的 SMTP 端口。                                                                                                                                                                                                                  |
| globalSettings\_\_mail\_\_smtp\_\_ssl=           | <p>（布尔值）您的 SMTP 服务器是否使用加密协议：<br><code>true</code> = SSL<br><code>false</code> = TLS</p>                                                                                                                                               |
| globalSettings\_\_mail\_\_smtp\_\_username=      | `smtp__host` 的有效用户名。                                                                                                                                                                                                                  |
| globalSettings\_\_mail\_\_smtp\_\_password=      | `smtp__host` 的有效密码。                                                                                                                                                                                                                   |
| globalSettings\_\_disableUserRegistration=       | 指定为 `true` 将禁用新用户通过注册页面在此实例上注册账户。                                                                                                                                                                                                     |
| globalSettings\_\_hibpApiKey=                    | 您的 HaveIBeenPwned (HIBP) API 密钥，参阅[此处](https://haveibeenpwned.com/API/Key)。                                                                                                                                                           |
| adminSettings\_\_admins=                         | 可以访问[系统管理员门户](system-administrator-portal.md)的电子邮件地址。                                                                                                                                                                                 |

## 可选变量 <a href="#optional-variables" id="optional-variables"></a>

以下变量在 `global.override.env` 中尚不存在，但可以手动添加：

| 变量                                                    | 描述                                                                                                                                                                                                                                                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| globalSettings\_\_logDirectory=                       | 指定日志文件的保存目录。默认为 `globalSettings__logDirectory=bwdata/logs`。                                                                                                                                                                                                                                |
| globalSettings\_\_logRollBySizeLimit=                 | 指定用于滚动日志文件的大小限制，以字节为单位（例如 `globalSettings__logRollBySizeLimit=1073741824`）。                                                                                                                                                                                                                |
| globalSettings\_\_syslog\_\_destination=              | 指定要将日志文件发送到的 Syslog 服务器或端点（例如 `globalSettings__syslog__destination=udp://example.com:514`）。                                                                                                                                                                                                |
| globalSettings\_\_mail\_\_smtp\_\_trustServer=        | 指定为 `true` 将以显式信任 SMTP 服务器提供的证书（**不建议用于生产中**）。                                                                                                                                                                                                                                             |
| globalSettings\_\_mail\_\_smtp\_\_sslOverride=        | 指定为 `true` 将在端口 25 上使用 SSL（而不是 TLS）。                                                                                                                                                                                                                                                       |
| globalSettings\_\_mail\_\_smtp\_\_startTls=           | 指定为 `true` 将强制 STARTTLS（随机 TLS）。                                                                                                                                                                                                                                                           |
| globalSettings\_\_organizationInviteExpirationHours=  | 指定组织邀请到期的小时数。默认为 `120` 小时。                                                                                                                                                                                                                                                                 |
| globalSettings\_\_yubico\_\_validationUrls\_\_0=      | <p>自托管 Yubico 验证服务器的主要地址。例如：<code>globalSettings__yubico__validationUrls__0=https://your.url.com/wsapi/2.0/verify</code>。</p><p></p><p>通过创建递增的环境变量来添加其他验证服务器 URL，例如：  <code>globalSettings__yubico__validationUrls__1=</code>，<code>globalSettings__yubico__validationUrls__2=</code>。</p> |
| globalSettings\_\_enableCloudCommunication=           | 设置为 `true` 以允许您的服务器和我们的云系统之间进行通信。目前仅适用于[企业版家庭赞助](self-hosting-families-sponsorships.md)。                                                                                                                                                                                                   |
| adminSettings\_\_deleteTrashDaysAgo=                  | 指定多少天后从回收站永久删除项目。默认为 `30` 天。                                                                                                                                                                                                                                                               |
| globalSettings\_\_sso\_\_enforceSsoPolicyForAllUsers= | 指定 `true` 以对所有者和管理员角色强制执行[需要 SSO 身份验证](../admin-console/organization-basics/enterprise-policies.md#require-single-sign-on-authentication)策略。                                                                                                                                               |

# 使用 AD 或 LDAP 同步

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/ldap-directory/)
{% endhint %}

本文将帮助您使用目录连接器将您的 LDAP 或 Active Directory 服务中的用户和群组同步到您的 Bitwarden 组织。Bitwarden 为最受欢迎的 LDAP 目录服务器提供了内置连接器，这些目录服务器包括：

* Microsoft Active Directory
* Apache Directory Server (ApacheDS)
* Apple Open Directory
* Fedora Directory Server
* Novell eDirectory
* OpenDS
* OpenLDAP
* Sun Directory Server Enterprise Edition (DSEE)
* 任何通用 LDAP 目录服务器

## 连接到您的服务器 <a href="#connect-to-your-server" id="connect-to-your-server"></a>

完成以下步骤，将目录连接器配置为使用 LDAP 或 Active Directory：

1. 打开目录连接器[桌面版应用程序](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 标签页。
3. 从 **Type** 下拉列表中选择 **Active Directory / LDAP**。\
   此部分中的可用字段将根据您选择的类型而变化。
4. 配置以下表格中的选项：

| 选项                                       | 描述                                                                                                                                                                                                                | 示例                                                                                                                                                                                                     |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Server Hostname                          | 目录服务器的主机名。                                                                                                                                                                                                        | <p><code>ad.example.com</code></p><p></p><p><code>ldap.company.local</code></p>                                                                                                                        |
| Server Port                              | 目录服务器侦听的端口。                                                                                                                                                                                                       | 389 或 10389                                                                                                                                                                                            |
| Root Path                                | 目录连接器应在其中启动所有查询的根路径。                                                                                                                                                                                              | <p><code>cn=users</code>，</p><p><code>dc=ad</code>，</p><p><code>dc=example</code>，</p><p><code>dc=com</code>，</p><p><code>dc=ldap</code>，</p><p><code>dc=company</code>，</p><p><code>dc=org</code></p> |
| This server uses Active Directory        | 如果服务器是活动目录服务器，则选中此框。                                                                                                                                                                                              |                                                                                                                                                                                                        |
| This server pages search results         | 如果服务器对搜索结果进行分页，请选中此框（_仅  LDAP_）。                                                                                                                                                                                  |                                                                                                                                                                                                        |
| This server uses an encrypted connection | <p>选中此框将提示您选择以下选项之一：</p><p></p><p><strong>Use SSL</strong>(LDAPS) - 如果您的 LDAPS 服务器使用不受信任的证书，则可以在此屏幕上配置证书选项。</p><p></p><p><strong>Use TLS</strong>(STARTTLS) - 如果您的 LDAP 服务器使用 STARTTLS 的自签名证书，则可以在此屏幕上配置证书选项。</p> |                                                                                                                                                                                                        |
| Username                                 | 应用程序在连接到目录服务器时，使用的管理用户的专有名称。对于 **Active Directory**，用户应该是内置管理员群组的成员。                                                                                                                                              |                                                                                                                                                                                                        |
| Password                                 | 上面指定的用户的密码。此密码安全地存储在操作系统的本机凭据管理器中。                                                                                                                                                                                |                                                                                                                                                                                                        |

## 配置同步选项 <a href="#configure-sync-options" id="configure-sync-options"></a>

{% hint style="success" %}
完成配置后，请导航至 **More** 标签页，然后选择 **Clear Sync Cache** 按钮，以防止与先前的同步操作发生潜在冲突。有关更多信息，请参阅[清除同步缓存](clear-sync-cache.md)。
{% endhint %}

完成以下步骤，以配置当使用目录连接器同步时的设置：

{% hint style="info" %}
如果您使用的是 Active Directory，则其中许多设置是为您预先确定的，因此不会显示。
{% endhint %}

1. 打开目录连接器[桌面版应用程序](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 标签页。
3. 在 **Sync** 部分，根据需要配置如下选项：

| 选项                                                                                             | 描述                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Interval                                                                                       | 自动同步检查的时间间隔（分钟为单位）。                                                                                                                                                                                                             |
| Remove disabled users during sync                                                              | 选中此框以从 Bitwarden 组织中删除已在您的组织中禁用的用户。                                                                                                                                                                                             |
| Overwrite existing organization users based on current sync settings                           | <p>选中此框以始终执行完全同步，如果任何用户不在同步用户集中，则将其从 Bitwarden 组织中移除。</p><p></p><p><strong>如果在启用此选项时出于任何原因运行了空同步，则目录连接器将移除所有用户。</strong>启用此选项以始终在同步之前运行<a href="sync-with-active-directory-or-ldap.md#test-a-sync-start-automati">测试同步</a>。</p> |
| Member Attribute                                                                               | 目录用此属性名称来定义群组的成员资格（例如 `uniqueMember`）                                                                                                                                                                                           |
| Creation Date Attribute                                                                        | 目录用此属性名称来指定条目创建的时间（例如 `whenCreated`）                                                                                                                                                                                            |
| Revision Date Attribute                                                                        | 目录用此属性名称来指定条目上次的修改时间（例如 `whenChanged`）                                                                                                                                                                                          |
| If a user has no email address, combine a username prefix with a suffix value to form an email | <p>选中此框可为没有电子邮箱地址的用户生成有效的电子邮箱选项。<strong>没有真实或没有生成电子邮箱地址的用户将被目录连接器跳过。</strong></p><p></p><p>生成的电子邮箱 = <strong>Email Prefix Attribute</strong> + <strong>Email Suffix</strong></p>                                                |
| Email Prefix Attribute                                                                         | 用于生成电子邮箱地址时创建前缀。                                                                                                                                                                                                                |
| Email Suffix                                                                                   | 用于生成电子邮箱地址时创建后缀的字符串（ `@example.com`）。                                                                                                                                                                                           |
| Sync Users                                                                                     | <p>选中此框以将用户同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>用户筛选器</strong>、<strong>用户路径</strong>、<strong>用户对象类</strong>以及<strong>用户电子邮箱属性</strong>。</p>                                                                                  |
| User Filter                                                                                    | 参阅[指定同步筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)。                                                                                                                                                        |
| User Path                                                                                      | 与指定的**根路径**一起使用的属性，用于搜索用户（例如 `ou=users`）。如果未提供任何值，则子树搜索将从根路径开始。                                                                                                                                                                 |
| User Object Class                                                                              | 用于 LDAP 用户对象类的名称（例如 `user`）。                                                                                                                                                                                                    |
| User Email Attribute                                                                           | 用于加载用户电子邮箱地址时使用的属性。                                                                                                                                                                                                             |
| Sync Groups                                                                                    | <p>选中此框以将群组同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>群组筛选器</strong>、<strong>群组路径</strong>、<strong>群组对象类</strong>以及<strong>群组名称属性</strong>。</p>                                                                                    |
| Group Filter                                                                                   | 参阅[指定同步筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)。                                                                                                                                                        |
| Group Path                                                                                     | 与指定的**根路径**一起使用的属性，用于搜索群组（例如 `ou=groups`）。如果未提供任何值，则子树搜索将从根路径开始。                                                                                                                                                                |
| Group Object Class                                                                             | 用于 LDAP 群组对象类的名称（例如 `groupOfUniqueNames`）。                                                                                                                                                                                      |
| Group Name Attribute                                                                           | 目录使用此属性名称来定义群组的名称（例如 `name`）                                                                                                                                                                                                    |

## 指定同步筛选器 <a href="#specify-sync-filters" id="specify-sync-filters"></a>

用户和群组筛选器可以是任何 LDAP 兼容的搜索筛选器形式。

与标准 LDAP 指导相比，Active Directory 提供了一些用于编写搜索筛选器时使用的高级选项和限制。在[此处](https://docs.microsoft.com/en-us/windows/win32/adsi/search-filter-syntax?redirectedfrom=MSDN)了解有关编写 Active Directory 搜索筛选器的更多信息。

### 示例 <a href="#samples" id="samples"></a>

要为具有包含 `Marketing` 的 `cn`（通用名称）以及具有 `objectClass=user` 的所有条目筛选同步：

```systemd
(&(objectClass=user)(cn=*Marketing*))
```

&#x20;（仅对于 **LDAP**）要为具有 \
`ou`（组织单元）组件（他们的 `dn`（专有名词）是 `Miami` 或 `Orlando`）的所有条目筛选同步：

```systemd
(|(ou:dn:=Miami)(ou:dn:=Orlando))
```

（仅对于 **LDAP**）要排除与表达式相匹配的条目，例如所有 `ou=Chicago` 但排除同样匹配 `ou=Wrigleyville` 的条目：

```systemd
(&(ou:dn:=Chicago)(!(ou:dn:=Wrigleyville)))
```

（仅对于 **AD**）要为 `Heroes` 群组中的用户筛选同步：

```systemd
(&(objectCategory=Person)(sAMAccountName=*)(memberOf=cn=Heroes,ou=users,dc=company,dc=com))
```

&#x20;（仅对于 **AD**）要通过目录或嵌套为 `Heroes` 群组成员的用户筛选同步：

```systemd
(&(objectCategory=Person)(sAMAccountName=*)(memberOf:1.2.840.113556.1.4.1941:=cn=Heroes,ou=users,dc=company,dc=com))
```

## 测试同步 <a href="#test-a-sync-start-automati" id="test-a-sync-start-automati"></a>

要测试目录连接器是否成功连接到您的目录并返回所需的用户和群组，导航到 **Dashboard** 标签页并选择 **Test Now** 按钮。如果成功，则用户和群组将根据指定的[同步选项](sync-with-active-directory-or-ldap.md#configure-sync-options)和[筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)显示在目录连接器窗口中：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5QYMxvtCPhjbluuoLcCapD/96e9c630ead9ceba5124b55f9d2764a3/dc-okta-test.png?fm=webp&h=439&q=50&w=500" %}
测试同步的结果
{% endembed %}

## 启动自动同步 <a href="#start-automatic-sync" id="start-automatic-sync"></a>

配置并测试[同步选项](sync-with-active-directory-or-ldap.md#configure-sync-options)和[筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)后，就可以开始同步了。完成以下步骤以使用目录连接器启动自动同步：

1. 打开目录连接器[桌面版应用程序](directory-connector-desktop-app.md)。
2. 导航到 **Dashboard** 标签页。
3. 在 **Sync** 部分选择 **Start Now** 按钮。\
   或者你可以选择 **Sync Now** 按钮以运行一次性手动同步。

目录连接器将根据配置的[同步选项](sync-with-active-directory-or-ldap.md#configure-sync-options)和[筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)开始轮询目录。

如果您退出或关闭了目录连接器，自动同步将停止。最小化或隐藏此程序到系统托盘，以保持后台运行。

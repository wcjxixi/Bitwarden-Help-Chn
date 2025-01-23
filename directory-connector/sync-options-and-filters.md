# 同步选项和筛选器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/user-group-filters/)
{% endhint %}

配置目录连接器应用程序时，可以使用各种同步选项和筛选器来自定义同步操作，并将要处理的用户和/或群组限制为您的 Bitwarden 组织。

每一种目录服务器类型的可用同步选项和筛选器语法都不同。请参阅以下文章之一中的**配置同步选项**和**指定同步筛选器**部分以获取帮助：

* [与 AD 或 LDAP 同步](sync-with-active-directory-or-ldap.md)
* [与 Azure AD 同步](../admin-console/user-management/directory-connector/sync-with-microsoft-entra-id.md)
* [与 G Suite（Google）同步](sync-with-google-workspace.md)
* [与 Okta 同步](sync-with-okta.md)
* [与 OneLogin 同步](sync-with-onelogin.md)

{% hint style="success" %}
如果您使用的是目录连接器 CLI，请参阅[目录连接器文件存储](directory-connector-file-storage.md)以获取有关编辑 `data.json` 配置文件的帮助。
{% endhint %}

## 大型同步 <a href="#large-syncs" id="large-syncs"></a>

无论您从哪一种目录同步，请启用 **More than 2000 users or groups are expected to sync** 选项。此选项向目录连接器发出信号，表明您需要同步大量的用户或群组：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2vEokum2rZLMpp59jsAjKz/f87501bba4f4a05ee14dc8fe61d07f06/largesync.png?fm=webp&h=1070&q=50&w=2242" %}
大型同步信号
{% endembed %}

您也可以通过设置 `"largeImport": true` 直接在目录连接器[配置文件](directory-connector-file-storage.md#config-file)（`data.json`）中启用此选项：

```json
"syncConfig": {
  ...,
  ...,
  ...,
  "largeImport": true
  },"
```

{% hint style="info" %}
如果您不启用此选项，目录连接器会将同步限制为 2000 个用户或群组。
{% endhint %}

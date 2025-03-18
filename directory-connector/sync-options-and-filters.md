# 同步选项和筛选器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/user-group-filters/)
{% endhint %}

配置目录连接器应用程序时，可以使用各种同步选项和筛选器来自定义同步操作，并将要处理的用户和/或群组限制为您的 Bitwarden 组织。

每一种目录服务器类型的可用同步选项和筛选器语法都不同。请参阅以下文章之一中的**配置同步选项**和**指定同步筛选器**部分以获取帮助：

* [使用 AD 或 LDAP 同步](sync-with-active-directory-or-ldap.md)
* [使用 Microsoft Entra ID 同步](../admin-console/user-management/directory-connector/sync-with-microsoft-entra-id.md)
* [使用 Google Workspace 同步](sync-with-google-workspace.md)
* [使用 Okta 同步](sync-with-okta.md)
* [使用 OneLogin 同步](sync-with-onelogin.md)

{% hint style="success" %}
如果您使用的是目录连接器 CLI，请参阅[目录连接器文件存储](directory-connector-file-storage.md)以获取有关编辑 `data.json` 配置文件的帮助。
{% endhint %}

## 大型同步 <a href="#large-syncs" id="large-syncs"></a>

无论您从哪一种目录同步，请启用 **More than 2000 users or groups are expected to sync**（预计超过 2000 个用户或群组需要同步）选项。此选项向目录连接器发出信号，表明您需要同步大量的用户或群组：

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

## 覆盖同步 <a href="#overwriting-syncs" id="overwriting-syncs"></a>

{% hint style="danger" %}
该选项用于非常特殊的用例或调试目的，默认为禁用。
{% endhint %}

通过激活 **Remove and re-add organization users during the next sync**（下次同步时移除并重新添加组织用户）选项，除一个所有者用户外的所有用户以及所有群组将在同步过程中被移除并重新添加，替换为从源目录获取的用户列表和/或群组列表。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/sM0wG9htsgHvpsXx1E1t9/929c1601a0f6d6c55a576e6154d89d31/2024-12-12_10-58-15.png?_a=DAJCwlWIZAAB" %}
下次同步时移除并重新添加组织用户
{% endembed %}

您也可以通过设置 `"overwriteExisting": true`，直接在目录连接器配置文件 (`data.json`) 中启用该选项：

```bash
"syncConfig": {
  ...,
  ...,
  ...,
  "overwriteExisting": true
  },"
```

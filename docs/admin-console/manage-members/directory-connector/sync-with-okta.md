# 使用 Okta 同步

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/okta-directory/)
{% endhint %}

本文将帮助您使用 Directory Connector 将您的 Okta 目录中的用户和群组同步到您的 Bitwarden 组织。

## 创建 Okta API 令牌 <a href="#create-an-api-token" id="create-an-api-token"></a>

Directory Connector 需要 Okta 生成的令牌的信息才能连接到您的目录。完成以下步骤以创建和获取供 Directory Connector 使用的 Okta API 令牌：

1. 从您的 Okta Developer Console (`https://yourdomain-admin.okta.com`) 导航到 **Security** → **API** → **Tokens**。
2. 选择 **Create Token** 按钮，然后给您的令牌指定一个专用于 Bitwarden 的名称（比如 `bitwartden-dc`）。
3. 将生成的 **Token Value** 复制到剪贴板。

{% hint style="warning" %}
您的 Token Value 不会再次显示。请将其粘贴到某个安全的地方以防丢失。
{% endhint %}

## 连接到您的目录 <a href="#connect-to-your-directory" id="connect-to-your-directory"></a>

完成以下步骤以配置 Directory Connector 使用您的 Okta 目录：

1. 打开 Directory Connector [桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 选项卡。
3. 从 **Type** 下拉菜单中，选择 **Okta**。\
   此部分中的可用字段将根据您选择的类型而变化。
4. 在 **Organization URL** 字段中输入您的 Okta Organization URL（比如 `https://yourdomain.okta.com`）。
5. 将 API Token Value 粘帖到 **Token** 字段中。

## 配置同步选项 <a href="#configure-sync-options" id="configure-sync-options"></a>

{% hint style="success" icon="lightbulb" %}
完成配置后，请导航至 **More** 标签页，然后选择 **Clear Sync Cache** 按钮，以防止与先前的同步操作发生潜在的冲突。更多信息，请参阅[清除同步缓存](clear-sync-cache.md)。
{% endhint %}

完成以下步骤以配置当使用 Directory Connector 同步时要使用的设置：

1. 打开 Directory Connector [桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 选项卡。
3. 在 **Sync** 部分，根据需要配置如下选项：

<table data-search="false"><thead><tr><th>选项</th><th>描述</th></tr></thead><tbody><tr><td>Interval</td><td>自动同步检查的时间间隔（分钟为单位）。</td></tr><tr><td>Remove disabled users during sync</td><td>选中此框以从 Bitwarden 组织中删除已在您的组织中禁用的用户。</td></tr><tr><td>Overwrite existing organization users based on current sync settings</td><td>选中此框以始终执行完全同步，如果任何用户不在同步用户集中，则将其从 Bitwarden 组织中移除。</td></tr><tr><td>More than 2000 users or groups are expected to sync</td><td>如果预计同步 2000 个以上用户或群组，请选中此框。如果不勾选此框，Directory Connector 会将同步限制在 2000 个用户或群组。</td></tr><tr><td>Sync Users</td><td><p>选中此框以将用户同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>用户筛选器</strong>。</p></td></tr><tr><td>User Filter</td><td>参阅<a href="sync-with-okta.md#specify-sync-filters">指定同步筛选器</a>。</td></tr><tr><td>Sync Groups</td><td><p>选中此框以将群组同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>群组筛选器</strong>。</p></td></tr><tr><td>Group Filter</td><td>参阅<a href="sync-with-okta.md#specify-sync-filters">指定同步筛选器</a>。</td></tr></tbody></table>

### 指定同步筛选器 <a href="#specify-sync-filters" id="specify-sync-filters"></a>

使用逗号分隔的列表可根据用户电子邮箱、群组名称在同步中包含或排除。此外，Okta API 为用户和群组提供了有限的筛选功能，这些功能可以在 Directory Connector 筛选器字段中使用。

有关为[用户](https://developer.okta.com/docs/api/resources/users#list-users-with-a-filter)和[群组](https://developer.okta.com/docs/api/resources/groups#filters)使用 `filter` 参数的更多信息，请查阅 Okta 文档。

#### 用户筛选器 <a href="#user-filters" id="user-filters"></a>

**按电子邮箱包含/排除用户**

要基于电子邮箱地址在同步中包含或排除特定用户：

```
include:joe@example.com,bill@example.com,tom@example.com
```

```
exclude:joe@example.com,bill@example,tom@example.com
```

**使用 `filter` 连接**

要使用 `filter` 参数连接用户筛选器，请使用管道符 (`|`)：

```
include:john@example.com,bill@example.com|profile.firstName eq "John"
```

```
exclude:john@example.com,bill@example.com|profile.firstName eq "John"
```

**只使用 `filter`**

要只使用 `filter` 参数，请在查询前加上管道符 (`|`)：

```
|profile.lastName eq "Smith"
```

#### 群组筛选器 <a href="#group-filters" id="group-filters"></a>

{% hint style="info" %}
Okta 不支持嵌套群组。
{% endhint %}

**包含/排除群组**

要基于群组名称包含或排除群组：

```systemd
include:Group A,Group B
```

```python
exclude:Group A,Group B
```

**使用 `filter` 连接**

要使用 `filter` 参数连接群组筛选器，请使用管道符 (`|`)：

```
include:Group A|type eq "APP_GROUP"
```

```
exclude:Group A|type eq "APP_GROUP"
```

**只使用 `filter`**

要只使用 `filter` 参数，请在查询前加上管道符 (`|`)：

```
|type eq "BUILT_IN"
```

## 测试同步 <a href="#test-a-sync" id="test-a-sync"></a>

{% hint style="success" icon="lightbulb" %}
在测试或执行同步之前，请检查 Directory Connector 是否连接到正确的云服务器（如 US 或 EU）或自托管服务器。了解如何使用[桌面 App](directory-connector-desktop-app.md) 或 [CLI](directory-connector-cli.md) 进行检查。
{% endhint %}

要测试 Directory Connector 是否成功连接到您的目录并返回所需的用户和群组，导航到 **Dashboard** 选项卡，然后选择 **Test Now** 按钮。如果成功，则用户和群组将根据指定的[同步选项](sync-with-ldap-or-ad.md#configure-sync-options)和[筛选器](sync-with-ldap-or-ad.md#specify-sync-filters)显示在 Directory Connector 窗口中：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/6LbdKcCZucynwqW7eoOetT/331b88e5bc07cbe92f67a2a92f2d807d/dc-okta-test.png?w=800&#x26;fm=avif" alt=""><figcaption><p>测试同步的结果</p></figcaption></figure></div>

## 启动自动同步 <a href="#start-automatic-sync" id="start-automatic-sync"></a>

配置并测试[同步选项](sync-with-ldap-or-ad.md#configure-sync-options)和[筛选器](sync-with-ldap-or-ad.md#specify-sync-filters)后，就可以开始同步了。完成以下步骤以使用 Directory Connector 启动自动同步：

1. 打开 Directory Connector [桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Dashboard** 选项卡。
3. 在 **Sync** 部分，选择 **Start Now** 按钮。\
   或者您可以选择 **Sync Now** 按钮以运行一次性手动同步。

Directory Connector 将根据配置的[同步选项](sync-with-ldap-or-ad.md#configure-sync-options)和[筛选器](sync-with-ldap-or-ad.md#specify-sync-filters)开始轮询目录。

如果您退出或关闭了 Directory Connector，自动同步将停止。最小化或隐藏此程序到系统托盘，以保持后台运行。

{% hint style="info" %}
如果您使用的是[团队入门版](../../../plans-and-pricing/password-manager/about-bitwarden-plans.md#teams-starter-organizations)方案，则成员数量限制为 10 人。如果您尝试同步超过 10 名成员，Directory Connector 将显示错误并停止同步。

**该方案已不再提供购买**。此错误不适用于团队版方案。
{% endhint %}

# 使用 Microsoft Entra ID 同步

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/microsoft-entra-id/)
{% endhint %}

本文将帮助您使用 Directory Connector 将您的 Azure Entra ID 目录中的用户和群组同步到您的 Bitwarden 组织。

## Microsoft Entra ID Directory 设置 <a href="#microsoft-entra-id-directory-setup" id="microsoft-entra-id-directory-setup"></a>

在配置 Directory Connector 之前，请从 [Microsoft Azure 门户](https://portal.azure.com/)完成以下流程。Directory Connector 需要从这些流程中获得的信息才能正常运行。

### 创建应用程序注册 <a href="#create-app-registration" id="create-app-registration"></a>

完成以下步骤，为 Directory Connector 创建一个应用程序注册：

1. 从您的 [Microsoft Azure 门户](https://portal.azure.com/)，导航到 **Azure Entra ID** 目录。
2. 从左侧导航选择**应用程序注册**或在搜索栏中输入**应用程序注册**。
3. 选择**新建注册**按钮并为您的注册指定一个专用于 Bitwarden 的名称（比如 `bitwarden-dc`）。
4. 选择**注册**。

### 授予应用程序权限 <a href="#grant-app-permissions" id="grant-app-permissions"></a>

完成以下步骤以为已创建的应用程序注册授予所需的权限：

1. 在已创建的 Bitwarden 应用程序中，从左侧导航选择 **API 权限**。
2. 选择**添加权限**按钮。
3. 当提示您选择一个 API 时，选择 **Microsoft Graph**。
4. 设置如下的**委托权限**：
   * User > User.ReadBasic.All（读取所有用户的基本配置）
   * User > User.Read.All（读取所有用户的全部配置）
   * Group > Group.Read.All（读取所有群组）
   * AdministrativeUnit > AdministrativeUnit.Read.All（仅当您要同步[管理单元](sync-with-microsoft-entra-id.md#specify-sync-filters)时才需要）
5. 设置如下的**应用程序权限**：
   * User > User.Read.All（读取所有用户的全部配置）
   * Group > Group.Read.All（读取所有群组）
   * AdministrativeUnit > AdministrativeUnit.Read.All（仅当您要同步[管理单元](sync-with-microsoft-entra-id.md#specify-sync-filters)时才需要）
6. 返回 API 权限页面，选择**为 ... 授予管理员同意**按钮。

### 创建应用程序密钥 <a href="#create-app-secret-key" id="create-app-secret-key"></a>

完成以下步骤以创建 Directory Connector 要使用的密钥：

1. 在已创建的 Bitwarden 应用程序中，从左侧导航选择**证书和密码**。
2. 选择**新建客户端密码**按钮，并添加一个 Bitwarden 专用描述（例如 `bitwarden-dc-secret`）和到期日期，我们建议选择**用不**。
3. 填写完成后选择**保存**。
4. 将密码的**值**复制到安全的地方，稍后将使用它。

> **\[译者注]**：注意客户端密码的值必须及时备份，退出此页面后您将无法再次查看。

### 获取应用程序 ID <a href="#get-app-id" id="get-app-id"></a>

完成以下步骤以获取 Directory Connector 要使用的应用程序 ID：

1. 在已创建的 Bitwarden 应用程序中，从左侧导航选择**概览**。
2. 将**应用程序（客户端）ID** 复制到安全的地方，稍后将使用它。

### 获取租户主机名 <a href="#get-tenant-hostname" id="get-tenant-hostname"></a>

完成以下步骤以获取 Directory Connector 要使用的租户主机名：

1. 在 Microsoft Azure 门户的任意页面，点击右上角导航栏的 **⚙️**图标。
2. 从左侧菜单栏选择**目录和订阅**筛选器按钮。
3. 将**当前目录：**&#x7684;值复制到安全位置以备后续使用。

## 连接到您的目录 <a href="#connect-to-your-directory" id="connect-to-your-directory"></a>

完成以下步骤以配置 Directory Connector 使用您的 Azure Active Directory。如果尚未准备好，请执行适当的 [Azure AD 设置](sync-with-microsoft-entra-id.md#azure-ad-setup)步骤，然后继续：

1. 打开 Directory Connector [桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 选项卡。
3. 从 **Type** 下拉菜单中，选择 **Azure Active Directory**。\
   此部分中的可用字段将根据您选择的类型而变化。
4. 输入收集到的[**租户主机名**](sync-with-microsoft-entra-id.md#get-tenant-hostname)、[**应用程序 ID**](sync-with-microsoft-entra-id.md#get-app-id) 以及[**安全密钥**](sync-with-microsoft-entra-id.md#create-app-secret-key)。

## 配置同步选项 <a href="#configure-sync-options" id="configure-sync-options"></a>

{% hint style="success" icon="lightbulb" %}
完成配置后，请导航至 **More** 标签页，然后选择 **Clear Sync Cache** 按钮，以防止与先前的同步操作发生潜在的冲突。更多信息，请参阅[清除同步缓存](clear-sync-cache.md)。
{% endhint %}

完成以下步骤以配置当使用 Directory Connector 同步时要使用的设置：

1. 打开 Directory Connector [桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 选项卡。
3. 在 **Sync** 部分，根据需要配置如下选项：

<table data-search="false"><thead><tr><th width="332.75477397414636">选项</th><th>描述</th></tr></thead><tbody><tr><td>Interval</td><td>自动同步检查的时间间隔（分钟为单位）。</td></tr><tr><td>Remove disabled users during sync</td><td>选中此框以从 Bitwarden 组织中删除已在您的组织中禁用的用户。</td></tr><tr><td>Overwrite existing organization users based on current sync settings</td><td>选中此框以始终执行完全同步，如果任何用户不在同步用户集中，则将其从 Bitwarden 组织中移除。</td></tr><tr><td>More than 2000 users or groups are expected to sync</td><td>如果预计同步 2000 个以上用户或群组，请选中此框。如果不勾选此框，Directory Connector 会将同步限制在 2000 个用户或群组。</td></tr><tr><td>Sync Users</td><td><p>选中此框以将用户同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>用户筛选器</strong>。</p></td></tr><tr><td>User Filter</td><td>参阅<a href="sync-with-microsoft-entra-id.md#specify-sync-filters">指定同步筛选器</a>。</td></tr><tr><td>Sync Groups</td><td><p>选中此框以将群组同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>群组筛选器</strong>。</p></td></tr><tr><td>Group Filter</td><td>参阅<a href="sync-with-microsoft-entra-id.md#specify-sync-filters">指定同步筛选器</a>。</td></tr></tbody></table>

### 指定同步筛选器 <a href="#specify-sync-filters" id="specify-sync-filters"></a>

使用逗号分隔的列表可根据用户电子邮箱、群组名称或群组成员资格在同步中包含或排除：

#### 用户筛选器 <a href="#user-filters" id="user-filters"></a>

在 **User Filter** 字段中使用以下筛选语法：

**按电子邮箱包含/排除用户**

要基于电子邮箱地址在同步中包含或排除特定用户：

```systemd
include:joe@example.com,bill@example.com,tom@example.com
```

```systemd
exclude:jow@example.com,bill@example.com,tom@example.com
```

**按群组成员资格筛选用户**

您可以使用 `includeGroup` 和 `excludeGroup` 关键词根据 Azure Active Directory 群组成员资格在同步中包含或排除用户。`includeGroup` 和 `excludeGroup` 使用群组对象 ID，此 ID 可从 [Azure 门户](https://portal.azure.com/)中的群组**概览**页面或通过 [Azure AD Powershell](https://docs.microsoft.com/en-us/powershell/module/azuread/get-azureadgroup?view=azureadps-2.0) 获得：

```systemd
includeGroup:963b5acd-9540-446c-8e99-29d68fcba8eb,9d05a51c-f173-4087-9741-a7543b0fd3bc
```

```systemd
excludeGroup:963b5acd-9540-446c-8e99-29d68fcba8eb,9d05a51c-f173-4087-9741-a7543b0fd3bc
```

#### 群组筛选器 <a href="#group-filters" id="group-filters"></a>

{% hint style="info" %}
嵌套的群组可以在 Directory Connector 中通过单一引用同步多个组对象。具体操作是创建一个包含所有列出的组的管理单元。
{% endhint %}

在 **Group Filter** 字段中使用以下筛选语法：

**包含/排除群组**

要基于群组名称在同步中包含或排除群组：

```systemd
include:Group A,Group B
```

```systemd
exclude:Group A,Group B
```

**按管理单元 (AU) 筛选群组**

您可以使用 `includeadministrativeunit` 和 `excludeadministrativeunit` 关键词根据已标记的 [Azure Active Directory 管理单元 (AU)](https://docs.microsoft.com/en-us/azure/active-directory/roles/administrative-units) 在同步中包含或排除群组。`includeadministrativeunit`  和 `excludeadministrativeunit` 使用管理单元的 **Object ID**（对象 ID）：

```systemd
includeadministrativeunit:7ckcq6e5-d733-4b96-be17-5bad81fe679d
```

```systemd
excludeadministrativeunit:7ckcq6e5-d733-4b96-be17-5bad81fe679d
```

## 测试同步 <a href="#test-a-sync" id="test-a-sync"></a>

{% hint style="success" icon="lightbulb" %}
在测试或执行同步之前，请检查 Directory Connector 是否连接到正确的云服务器（如 US 或 EU）或自托管服务器。了解如何使用[桌面 App](directory-connector-desktop-app.md) 或 [CLI](directory-connector-cli.md) 进行检查。
{% endhint %}

要测试 Directory Connector 是否成功连接到您的目录并返回所需的用户和群组，导航到 **Dashboard** 选项卡，然后选择 **Test Now** 按钮。如果成功，则用户和群组将根据指定的[同步选项](sync-with-ldap-or-ad.md#configure-sync-options)和[筛选器](sync-with-ldap-or-ad.md#specify-sync-filters)显示在 Directory Connector 窗口中。

授予的权限最多可能需要 15 分钟才能正确传递到您的应用程序。在此期间，您可能会收到 `Insufficient privileges to complete the operation`（权限不足，无法完成此操作）的错误。

{% hint style="info" %}
如果您收到 `Resource <user id> does not exist or one of its queried reference-property objects are not present` 的错误信息，您需要永久删除或还原具有 `<user id>` 的用户。**请注意**，此问题已在最新版本的 Directory Connector 中修复。如果您仍遇到此错误，请更新您的应用程序。
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5QYMxvtCPhjbluuoLcCapD/96e9c630ead9ceba5124b55f9d2764a3/dc-okta-test.png?w=500&#x26;fm=avif" alt=""><figcaption><p>测试同步的结果</p></figcaption></figure></div>

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

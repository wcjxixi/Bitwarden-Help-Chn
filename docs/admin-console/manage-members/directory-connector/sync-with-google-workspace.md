# 使用 Google Workspace 同步

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/gsuite-directory/)
{% endhint %}

本文将帮助您使用 Directory Connector 将您的 Google Workplace（以前叫 G Suite）中的用户和群组同步到您的 Bitwarden 组织。

## Google Workspace 设置 <a href="#google-workspace-setup" id="google-workspace-setup"></a>

要设置与 Google Workplace（以前叫 G Suite）的目录同步，您需要访问 **Google Workspace Admin Portal** 和 **Google Cloud Platform Console**。Directory Connector 需要从这些流程中获得的信息才能正常运行。

### 创建 Cloud 项目 <a href="#create-a-cloud-project" id="create-a-cloud-project"></a>

完成以下步骤来创建 Google Cloud 项目，用于将 Directory Connector 连接到您的目录。如果您已经有可用的 Google Cloud 项目，请跳至[启用 Admin SDK](sync-with-google-workspace.md#enable-admin-sdk)：

1. 在 [GCP Console](https://console.cloud.google.com/home) 中，使用左侧导航栏选择 **IAM & Admin** → **管理资源**。
2. 选择**创建项目**按钮。
3. 在新建项目界面：
   * 为此项目输入一个专用于 Bitwarden 的名称（比如 `bitwarden-dc-project`）。
   * 选择一个组织，将项目关联至该组织。
   * 选择上级组织或文件夹。
   * 选择**创建**按钮。

### 启用 Admin SDK <a href="#enable-admin-sdk" id="enable-admin-sdk"></a>

完成以下步骤以启用 Admin SDK API，Directory Connector 将向其发送请求：

1. 在 [GCP Console](https://console.cloud.google.com/home) 中，选择已创建或已存在的项目。
2. 从左侧导航中，选择 **API 和服务** → **库**。
3. 在搜索框中输入 `Admin SDK`，然后打开 **Admin SDK API** 服务。
4. 选择**启用**按钮。

### 创建服务帐号 <a href="#create-service-account" id="create-service-account"></a>

完成以下步骤以创建一个在 API 调用时使用的服务账号：

1. 在 [GCP Console](https://console.cloud.google.com/home) 中，选择已创建或已存在的项目。
2. 从左侧导航中，选择 **API 和服务** → **凭据**。
3. 选择**创建凭据**按钮，然后从下拉菜单中选择**服务账号**。
4. 填写**服务账号详情**部分，然后选择**创建**按钮。
5. 在**授予此服务账号对项目的访问权限**部分，从**角色**下拉菜单中选择 **Project** → **Owner**，然后选择**继续**按钮。
6. 选择**完成**按钮。

### 获取服务账号凭据 <a href="#obtain-service-account-credentials" id="obtain-service-account-credentials"></a>

完成以下步骤，为已创建的服务账号获取相应的权限：

1、在 [GCP Console](https://console.cloud.google.com/home) 中，选择已创建或已存在的项目。

2、从左侧导航中，选择 **IMA 和服务** → **服务账号**。

3、选择已创建或已存在的服务账号。

4、在**密钥**选项卡中，选择**添加密钥**按钮，然后从下拉菜单中选择**创建新密钥**。

5、选择密钥类型为 **JSON**，然后选择**创建**按钮，将 JSON 格式的密钥下载到您的本地计算机。

6、返回您的服务账号**详情**选项卡，选择**高级设置**下拉菜单。

7、滚动至 **Google Workspace Marketplace OAuth 客户端**部分，选择**创建与 Google Workspace Marketplace 兼容的 OAuth 客户端**，或者，如果您看到显示「必须配置 OAuth 同意界面才能创建 OAuth 客户端」的提示框，请选择**配置**。

8、选择**开始使用**，在项目配置中：

* 输入请求授权的 App 名称（例如 `Bitwarden Directory Connector` ）。
* 择一个**用户支持电子邮箱**。
* 在**受众**部分，选择**内部**。
* 继续完成向导以创建同意界面。

9、创建后，打开**数据访问**选项卡，选择**添加或删除范围**。

10、在**手动添加范围**部分，粘贴以下内容：

```
https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.group.readonly,https://www.googleapis.com/auth/admin.directory.group.member.readonly
```

选择**添加到表格**，然后选择**更新**。

11、点击**保存**。

#### CLI 使用服务账号凭证 <a href="#using-service-account-credentials-with-the-cli" id="using-service-account-credentials-with-the-cli"></a>

**如果您打算使用 Directory Connector CLI**，您下载的 JSON 格式密钥将用于 `bwdc config gsuite.key` 命令，但需要中间步骤才能让 CLI 可以使用密钥文件中的私钥：

* **对于 Linux**，运行命令 `bwdc config gsuite.key "\n$(cat projectid-key.json | jq -r '.private_key')"`，请务必将 `projectid-key.json` 替换为您的 `.json` 文件名，该文件名通常是项目 ID 和密钥的组合。
* **对于其他 OS**：
  1. 将 `private_key` 的值复制到一个单独的 `.crt` 文件中，例如命名为 `google-bwdc-key.crt` 。
  2. 运行命令 `bwdc config gsuite.key "\n$(cat google-bwdc-key.crt)\n"`，确保将 `.crt` 文件名替换为您创建的文件名。

### 允许对 Google Workspace 的读取访问权限 <a href="#allow-read-access-to-google-workspace" id="allow-read-access-to-google-workspace"></a>

完成以下步骤以授权客户端读取您的目录：

1、打开 [Google Admin Portal](https://admin.google.com/u/5/ac/home)。

2、从左侧导航中，选择**安全** → **访问和数据控制** → **API 控制**。

3、选择**管理全网域委派**按钮。

4、选择**新增**按钮。

5、粘帖已创建的**客户端 ID** 到客户端 ID 字段中。

6、在客户端 ID 字段中，粘贴您创建的 **Unique ID**，您可以通过打开 [GCP Console](https://console.cloud.google.com/home) ，导航至 **API 和服务** → **凭据**，打开您的服务账户并查找 **Unique ID** 来找到它。\
要查看已创建的客户端 ID，请打开 [GCP Console](https://console.cloud.google.com/home) 并导航到 **API 和服务** → **凭据**。

7、在 OAuth 范围字段中，粘贴以下值以仅授予读取访问权限。

```
https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.group.readonly,https://www.googleapis.com/auth/admin.directory.group.member.readonly
```

8、选择**授权**按钮。

## 连接到您的目录 <a href="#connect-to-your-directory" id="connect-to-your-directory"></a>

完成以下步骤以配置 Directory Connector 使用您的 Google 目录：

1. 打开 Directory Connector [桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 选项卡。
3. 从 **Type** 下拉菜单中，选择 **G Suite（Google）**。\
   此部分中的可用字段将根据您选择的类型而变化。
4. 输入您的 Google 账号的 **Domain**。
5. 输入对您的 Google 目录具有完全访问权限的 **Admin User** 的电子邮箱地址。
6. 如果您有，请输入目录的**客户 ID**。许多用户没有或不需要输入客户 ID。
7. 选择**选择文件**按钮，然后选择[已下载的 JSON  密钥文件](sync-with-google-workspace.md#Obtain-Service-Account-Credentials-)。

## 配置同步选项 <a href="#configure-sync-options" id="configure-sync-options"></a>

{% hint style="success" icon="lightbulb" %}
完成配置后，请导航至 **More** 标签页，然后选择 **Clear Sync Cache** 按钮，以防止与先前的同步操作发生潜在的冲突。更多信息，请参阅[清除同步缓存](clear-sync-cache.md)。
{% endhint %}

完成以下步骤以配置当使用 Directory Connector 同步时要使用的设置：

1. 打开 Directory Connector [桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 选项卡。
3. 在 **Sync** 部分，根据需要配置如下选项：

<table data-search="false"><thead><tr><th>选项</th><th>描述</th></tr></thead><tbody><tr><td>Interval</td><td>自动同步检查的时间间隔（分钟为单位）。</td></tr><tr><td>Remove disabled users during sync</td><td>选中此框以从 Bitwarden 组织中删除已在您的组织中禁用的用户。</td></tr><tr><td>Overwrite existing organization users based on current sync settings</td><td>选中此框以始终执行完全同步，如果任何用户不在同步用户集中，则将其从 Bitwarden 组织中移除。</td></tr><tr><td>More than 2000 users or groups are expected to sync</td><td>如果预计同步 2000 个以上用户或群组，请选中此框。如果不勾选此框，Directory Connector 会将同步限制在 2000 个用户或群组。</td></tr><tr><td>Sync Users</td><td><p>选中此框以将用户同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>用户筛选器</strong>。</p></td></tr><tr><td>User Filter</td><td>参阅<a href="sync-with-google-workspace.md#specify-sync-filters">指定同步筛选器</a>。</td></tr><tr><td>Sync Groups</td><td><p>选中此框以将群组同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>群组筛选器</strong>。</p></td></tr><tr><td>Group Filter</td><td>参阅<a href="sync-with-google-workspace.md#specify-sync-filters">指定同步筛选器</a>。</td></tr></tbody></table>

### 指定同步筛选器 <a href="#specify-sync-filters" id="specify-sync-filters"></a>

#### 用户筛选器 <a href="#user-filters" id="user-filters"></a>

使用逗号分隔的列表来指定同步包含或排除的筛选条件。Google Workspace Directory API 允许您根据电子邮箱同步用户，并根据组织单位同步用户批次。要同步目录中的部分用户，Bitwarden 建议创建一个组织单位并将相关用户移至其中。

**同步特定组织单位**

要同步分配给特定组织单位 (OU) 的用户，例如 OU `EngineeringUsers` ，请使用管道符 (`|`) 声明查询参数。在**用户筛选器**开头声明查询表示仅同步符合查询条件的匹配项：

```
|orgUnitPath=/Engineering
```

您的根组（组织单位嵌套于其下）在 `orgUnitPath` 中始终被称为 `/` 。使用查询 `|orgUnitPath=/` 等同于不使用任何用户筛选器。

基于组织单位的同步可以结合额外筛选条件，以确定要同步该组织单位中的哪些特定用户，例如同步具有特定 `orgTitle` 的组织单位中的用户

```
|orgUnitPath=/Engineering orgTitle:Manager
```

超过 `orgTitle` 的更多的用户属性可以与 OU 查询结合使用，以确定要同步哪些用户，这些属性可在 [Google Directory API 文档](https://developers.google.com/workspace/admin/directory/v1/guides/search-users?hl=zh-cn)中找到。

**按电子邮箱包含/排除用户**

用于包含或排除特定用户的筛选器可以与组织单位查询结合使用，或单独使用，但任何 `include:` 或 `exclude:` 筛选器必须放在任何查询声明 (`|`) 之前。例如，要从具有特定 `orgTitle` 的用户组织单位同步中排除特定用户：

```
exclude:bill@example.com|orgUnitPath=/Engineering orgTitle:Manager
```

或者，仅根据用户的 `email` 同步选定用户：

```
include:joe@example.com,bill@example.com,tom@example.com
```

请注意，在最后一个示例中，由于没有声明其他查询参数（例如 OU 或 `orgTitle` ），因此不需要查询声明 (`|`)。

#### 群组筛选器 <a href="#group-filters" id="group-filters"></a>

使用逗号分隔的列表来指定同步包含或排除的筛选条件。Google Workspace Directory API 允许您根据群组名称和其他一些群组属性来同步群组，这些属性可在 [Google Directory API 文档](https://developers.google.com/workspace/admin/directory/v1/guides/search-groups?hl=zh-cn)中找到。

当使用**群组筛选器**时，被**用户筛选器**捕获的任何用户，其群组成员资格将针对被**群组筛选器**捕获的群组进行同步。

{% hint style="info" %}
Google Workspace 不支持同步嵌套群组。
{% endhint %}

**按名称同步群组**

可以通过专门筛选其 `name` 属性来将单个群组包含在同步中，例如：

```
include:Group A,Group B
```

使用管道符 (`|`) 声明查询参数时，也可通过匹配任意被通配符包围的术语 (`*`) 来同步部分群组。在**群组筛选器**起始位置添加查询声明，表示仅同步符合查询条件的匹配项，例如仅同步名称包含术语 `engineering` 的所有群组：

```
|name:*engineering*
```

通配符可在术语的任意一侧或两侧使用，且匹配不区分大小写。

**按成员密钥同步群组**

memberKey 属性可用于同步指定密钥所标识用户所属的所有群组。例如，若仅同步 `user@company` 所属的群组：

```
|memberKey=user@company.com
```

再次提醒，**群组筛选器**开头的查询声明表示仅同步与查询匹配的群组，且在此上下文中亦可使用通配符。

用于包含或排除特定群组的筛选器可与更广泛的查询结合使用，但任何 `include:` 或 `exclude:` 筛选器必须置于任何查询声明 (`|`) 之前。例如，要同步 `user@company` 所属的群组，但排除 `Group A` ：

```
exclude:Group A|memberKey:user@company
```

**按群组电子邮箱同步群组**

这些**群组筛选器**原则同样适用于基于群组的电子邮箱地址进行同步，例如：

```
exclude:Group B|email:admin*
```

## 测试同步 <a href="#test-a-sync" id="test-a-sync"></a>

{% hint style="success" icon="lightbulb" %}
在测试或执行同步之前，请检查 Directory Connector 是否连接到正确的云服务器（如 US 或 EU）或自托管服务器。了解如何使用[桌面 App](directory-connector-desktop-app.md) 或 [CLI](directory-connector-cli.md) 进行检查。
{% endhint %}

要测试 Directory Connector 是否成功连接到您的目录并返回所需的用户和群组，导航到 **Dashboard** 选项卡，然后选择 **Test Now** 按钮。如果成功，则用户和群组将根据指定的[同步选项](sync-with-ldap-or-ad.md#configure-sync-options)和[筛选器](sync-with-ldap-or-ad.md#specify-sync-filters)显示在 Directory Connector 窗口中：

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

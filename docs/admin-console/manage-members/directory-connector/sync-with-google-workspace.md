# 使用 Google Workspace 同步

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/gsuite-directory/)
{% endhint %}

本文将帮助您使用目录连接器将您的 Google Workplace（以前叫 G Suite）中的用户和群组同步到您的 Bitwarden 组织。

## Google Workspace 设置 <a href="#google-workspace-setup" id="google-workspace-setup"></a>

要设置与 Google Workplace（以前叫 G Suite）的目录同步，您需要访问 **Google Workspace Admin Portal** 和 **Google Cloud Platform Console**。目录连接器需要从这些过程中获得的信息才能正常运行。

### 创建 Cloud 项目 <a href="#create-a-cloud-project" id="create-a-cloud-project"></a>

完成以下步骤来创建用于将连目录连接器连接到您的目录的 Google Cloud 项目。如果您已经有可用的 Google Cloud 项目，请跳至[启用Admin SDK](sync-with-google-workspace.md#enable-admin-sdk)：

1. 在 [GCP Console](https://console.cloud.google.com/home) 中，选择**创建项目**按钮。
2. 为此项目输入一个 Bitwarden 专有名称（比如 `bitwarden-dc-project`）并选择**创建**按钮。

### 启用 Admin SDK <a href="#enable-admin-sdk" id="enable-admin-sdk"></a>

完成以下步骤以启用 Admin SDK API，目录连接器将向其发出请求：

1. 在 [GCP Console](https://console.cloud.google.com/home) 中，选择已创建或已存在的项目。
2. 从左侧导航中，选择 **API 和服务** → **库**。
3. 在搜索框中输入 `Admin SDK` 并打开 **Admin SDK API** 服务。
4. 选择**启用**按钮。

### 创建服务帐号 <a href="#create-service-account" id="create-service-account"></a>

完成以下步骤以创建一个在 API 调用时使用的服务账号：

1. 在 [GCP Console](https://console.cloud.google.com/home) 中，选择已创建或已存在的项目。
2. 从左侧导航中，选择 **API 和服务** → **凭据**。
3. 选择**创建凭据**按钮，并从下拉列表中选择**服务账号**。
4. 填写**服务账号详情**部分，并选择**创建**按钮。
5. 在**向此服务帐号授予对项目的访问权限**部分，从**角色**下拉列表中选择 **Project** → **Owner** 并选择**继续**按钮。
6. 选择**完成**按钮。

### 获取服务帐号凭据 <a href="#obtain-service-account-credentials" id="obtain-service-account-credentials"></a>

完成以下步骤，为已创建的服务帐号获取适当的权限：

1. 在 [GCP Console](https://console.cloud.google.com/home) 中，选择已创建或已存在的项目。
2. 从左侧导航中，选择 **IMA 和服务** → **服务账号**。
3. 选择已创建的服务账号。
4. 在服务账号详情页面，选择**添加密钥**按钮并从下拉列表中选择**创建新密钥**按钮。
5. 选择密钥类型为 **JSON** 并选择**创建**按钮，将 JSON 格式的密钥下载到您的本地计算机。
6. 返回您的服务账号的I详情页面，选择**显示全网域授权**下拉条。
7. 选中**启用全网域授权**框。
8. 输入一个**同意屏幕产品名称**。
9. 选择**保存**。

### 允许对 Google Workspace 的读取访问 <a href="#allow-read-access-to-google-workspace" id="allow-read-access-to-google-workspace"></a>

完成以下步骤以授权客户端读取您的目录：

1. 打开 [Google Admin Portal](https://admin.google.com/u/5/ac/home)。
2. 从左侧导航中，选择**安全** → **API 控制**。
3. 选择**管理全网域授权**按钮。
4. 选择**新增**按钮。
5. 粘帖已创建的**客户端 ID** 到客户端 ID 字段中。\
   要查看已创建的客户端 ID，请打开 [GCP Console](https://console.cloud.google.com/home) 并导航到 **API 和服务** → **凭据**。
6. 在 OAuth 范围字段中，粘贴以下值以仅授予读取访问权限。
7. 选择**授权**按钮。

```
https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.group.readonly,https://www.googleapis.com/auth/admin.directory.group.member.readonly
```

## 连接到您的目录 <a href="#connect-to-your-directory" id="connect-to-your-directory"></a>

完成以下步骤以配置目录连接器使用您的 Google 目录：

1. 打开目录连接器[桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 标签页。
3. 从 **Type** 下拉列表中选择 **G Suite（Google）**。\
   此部分中的可用字段将根据您选择的类型而变化。
4. 输入您的 Google 账号的 **Domain**。
5. 输入对您的 Google 目录具有完全访问权限的 **Admin User** 的电子邮箱地址。
6. 如果您有，请输入目录的**客户 ID**。许多用户没有或不需要输入客户 ID。
7. 选择**选择文件**按钮并选择[已下载的 JSON  密钥文件](sync-with-google-workspace.md#Obtain-Service-Account-Credentials-)。

## 配置同步选项 <a href="#configure-sync-options" id="configure-sync-options"></a>

{% hint style="success" %}
完成配置后，请导航至 **More** 标签页，然后选择 **Clear Sync Cache** 按钮，以防止与先前的同步操作发生潜在冲突。有关更多信息，请参阅[清除同步缓存](clear-sync-cache.md)。
{% endhint %}

完成以下步骤以配置当使用目录连接器同步时要使用的设置：

1. 打开目录连接器[桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Setting** 标签页。
3. 在 **Sync** 部分，根据需要配置如下选项：

| 选项                                                                   | 描述                                                                     |
| -------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Interval                                                             | 自动同步检查的时间间隔（分钟为单位）。                                                    |
| Remove disabled users during sync                                    | 选中此框以从 Bitwarden 组织中删除已在您的组织中禁用的用户。                                    |
| Overwrite existing organization users based on current sync settings | 选中此框以始终执行完全同步，如果任何用户不在同步用户集中，则将其从 Bitwarden 组织中移除。                     |
| More than 2000 users or groups are expected to sync                  | 如果预计同步 2000 个以上用户或群组，请选中此框。如果不勾选此框，目录连接器会将同步限制在 2000 个用户或群组。           |
| Sync Users                                                           | <p>选中此框以将用户同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>用户筛选器</strong>。</p> |
| User Filter                                                          | 参阅[指定同步筛选器](sync-with-google-workspace.md#specify-sync-filters)。       |
| Sync Groups                                                          | <p>选中此框以将群组同步到您的组织。</p><p></p><p>选中此框将允许您指定<strong>群组筛选器</strong>。</p> |
| Group Filter                                                         | 参阅[指定同步筛选器](sync-with-google-workspace.md#specify-sync-filters)。       |

### 指定同步筛选器 <a href="#specify-sync-filters" id="specify-sync-filters"></a>

使用逗号分隔的列表可根据用户电子邮箱、群组名称或群组成员资格在同步中包含或排除。

Admin SDK API 通过一个 `query` 参数为用户和裙组提供有限的筛选功能。了解更多：

* [搜索用户](https://developers.google.com/admin-sdk/directory/v1/guides/search-users)
* [搜索群组](https://developers.google.com/admin-sdk/directory/v1/guides/search-groups)

### 用户筛选器 <a href="#user-filters" id="user-filters"></a>

在 **User Filter** 字段中使用以下筛选语法：

#### 通过电子邮箱包含/排除用户 <a href="#include-exclude-users-by-email" id="include-exclude-users-by-email"></a>

要基于电子邮箱地址在同步中包含或排除特定用户：

```systemd
include:joe@example.com,bill@example.com,tom@example.com
```

```systemd
exclude:joe@example.com,bill@example,tom@example.com
```

#### 使用 `query` 连接 <a href="#concatenate-with-query" id="concatenate-with-query"></a>

要使用 `query` 参数连接用户筛选器，请使用竖线（`|`）：

```systemd
include:john@example.com,bill@example.com|orgName=Engineering orgTitle:Manager
```

```systemd
exclude:john@example.com,bill@example.com|orgName=Engineering orgTitle:Manager
```

#### 只使用 `query` <a href="#use-only-query" id="use-only-query"></a>

要只使用 `query` 参数，请在查询前加上竖线（`|`）：

```systemd
|orgName=Engineering orgTitle:Manager
```

### 群组筛选器 <a href="#group-filters" id="group-filters"></a>

在 **Group Filter** 字段中使用以下筛选语法：

#### 包含/排除群组 <a href="#include-exclude-groups" id="include-exclude-groups"></a>

要基于群组名称在同步中包含或排除群组：

```systemd
include:Group A,Group B
```

```systemd
exclude:Group A,Group B
```

#### 使用 `query` 连接 <a href="#concatenate-with-query" id="concatenate-with-query"></a>

要使用 `query` 参数连接群组筛选器，请使用竖线（`|`）：

```
include:name='Engineering'|email:admin*
```

```
exclude:name='Engineering'|email:admin*
```

#### 只使用 `query` <a href="#use-only-query" id="use-only-query"></a>

要只使用 `query` 参数，请在查询前加上竖线（`|`）：

```
|memberKey=user@company.com
```

## 测试同步 <a href="#test-a-sync" id="test-a-sync"></a>

{% hint style="success" %}
在测试或执行同步之前，请检查目录连接器是否连接到正确的云服务器（如 US 或 EU）或自托管服务器。了解如何使用[桌面 App](directory-connector-desktop-app.md) 或 [CLI](directory-connector-cli.md) 进行检查。
{% endhint %}

要测试目录连接器是否成功连接到您的目录并返回所需的用户和群组，导航到 **Dashboard** 标签页并选择 **Test Now** 按钮。如果成功，则用户和群组将根据指定的[同步选项](sync-with-active-directory-or-ldap.md#configure-sync-options)和[筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)显示在目录连接器窗口中：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5QYMxvtCPhjbluuoLcCapD/96e9c630ead9ceba5124b55f9d2764a3/dc-okta-test.png?fm=webp&h=439&q=50&w=500" %}
测试同步的结果
{% endembed %}

## 启动自动同步 <a href="#start-automatic-sync" id="start-automatic-sync"></a>

配置并测试[同步选项](sync-with-active-directory-or-ldap.md#configure-sync-options)和[筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)后，就可以开始同步了。完成以下步骤以使用目录连接器启动自动同步：

1. 打开目录连接器[桌面 App](directory-connector-desktop-app.md)。
2. 导航到 **Dashboard** 标签页。
3. 在 **Sync** 部分选择 **Start Now** 按钮。\
   或者你可以选择 **Sync Now** 按钮以运行一次性手动同步。

目录连接器将根据配置的[同步选项](sync-with-active-directory-or-ldap.md#configure-sync-options)和[筛选器](sync-with-active-directory-or-ldap.md#specify-sync-filters)开始轮询目录。

如果您退出或关闭了目录连接器，自动同步将停止。最小化或隐藏此程序到系统托盘，以保持后台运行。

{% hint style="info" %}
如果您使用的是[团队入门版](../../../plans-and-pricing/password-manager/about-bitwarden-plans.md#teams-starter-organizations)计划，则只能同步 10 个成员。如果您尝试同步超过 10 名成员，目录连接器将显示错误并停止同步。

**该计划已不再提供购买**。此错误不适用于团队版计划。
{% endhint %}

# 付费功能许可证

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/licensing-on-premise/)
{% endhint %}

自托管 Bitwarden 是免费的，但是有些功能必须在您的自托管实例中通过注册的许可证文件才能解锁。许可证文件可以由高级个人订阅账户或组织的所有者从 Bitwarden 托管的[网页密码库](https://vault.bitwarden.com/)中获取。

使用[个人许可证](licensing-for-paid-features.md#individual-license)与使用[组织许可证](licensing-for-paid-features.md#organization-license)时的步骤不同。

{% hint style="info" %}
本文中的过程假定您已经开始了一个 Bitwarden 付费订阅。如果还没有，请参阅[关于 Bitwarden 计划](../plans-and-pricing/password-manager/about-bitwarden-plans.md)以及[哪种计划适合我？](../plans-and-pricing/what-plan-is-right-for-me.md)。
{% endhint %}

## 个人许可证 <a href="#individual-license" id="individual-license"></a>

使用高级订阅的个人许可证时，请遵循这些步骤。您将需要同时访问云端网页密码库和自托管网页密码库，并且您的账户电子邮箱地址需一致。

### 获取个人许可证 <a href="#retrieve-individual-license" id="retrieve-individual-license"></a>

在自托管服务器上创建账户后，从云端网页 App 获取您的个人许可证：

1. 登录然后从导航中选择**设置** → **订阅**。
2. 选择**下载许可证**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/bXoVGOMEI1d8iCVoy5fmI/af545e3c083aeebaf12c751fc38a59ea/2024-12-04_10-02-56.png?_a=DAJCwlWIZAAB" %}
下载个人许可证
{% endembed %}

### 应用个人许可证 <a href="#apply-individual-license" id="apply-individual-license"></a>

接下来，登录到您的自托管 Bitwarden 服务器以应用已下载的许可证：

1. 如果您还没有验证您的电子邮箱地址，请在继续之前先验证。需要已经[配置了 SMTP 相关的环境变量](configure-environment-variables.md)。
2. 从导航中选择**设置** → **订阅**。
3. 在「许可证文件」部分中，选择**浏览...**&#x6216;**选择文件**按钮添加您刚才下载的许可证文件。
4. 选择**提交**按钮以应用您的高级许可证。

### 更新个人许可证 <a href="#update-individual-license" id="update-individual-license"></a>

如果出于任何原因您需要更新您的个人许可证文件，例如当它过期时：

1. 按照步骤再次**获取您的许可证**。
2. 按照步骤再次**应用您的许可证**，只有此时您才会看到**更新许可证**按钮，而不是浏览新许可证的按钮。

## 组织许可证 <a href="#organization-license" id="organization-license"></a>

使用家庭、团队或企业的组织许可证时，请遵循这些步骤。

{% hint style="info" %}
您必须是[组织的所有者](../admin-console/user-management/member-roles-and-permissions.md)才能获取、应用和更新许可证。
{% endhint %}

### 获取组织许可证 <a href="#retrieve-organization-license" id="retrieve-organization-license"></a>

在您的自托管服务器上开始一个组织之前，从云端网页 App 获取您的组织许可证：

1、在 Bitwarden 网页 App 中，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
管理控制台
{% endembed %}

2、导航到**计费** → **订阅**。

3、滚动到最下面然后选择**下载许可证**按钮。

4、提示时，输入安装自托管服务器时使用的安装 ID 然后选择**提交**。如果您不知道安装 ID，可以从 `./bwdata/env/global.override.env` 获取。

{% hint style="info" %}
确保您从 bitwarden.com/host 获取的安装 ID 使用的数据区域与您的组织所在的数据区域相同。
{% endhint %}

### 应用组织许可证 <a href="#apply-organization-license" id="apply-organization-license"></a>

在自托管服务器中应用您的许可证意味着您将要创建一个自托管组织。从您的自托管网页密码库：

1. 通过选择 **🞤新增组织**以在您的自托管实例中创建一个新的组织。
2. 选择**浏览...**&#x6216;**选择文件**按钮，添加已下载的许可证文件，然后选择**提交**。

{% hint style="info" %}
如果您收到一条 `version not supported`（版本不支持）的错误消息，请更新您的服务器并尝试再次上传您的许可证文件。要更新您的服务器，请备份 `bwdata` 目录，然后按照[这些说明](update-your-instance.md)进行操作。
{% endhint %}

### 更新组织许可证 <a href="#update-organization-license" id="update-organization-license"></a>

例如当添加用户席位或当您的许可证到期时，组织需要更新其自托管服务器上的许可证文件。当您的许可证到期以及您的组织续订时，您有 60 天的时间将已更新的许可证文件应用到您的自托管组织。

有两种方法可以这样操作，但是**家庭组织只能手动更新**：

{% tabs %}
{% tab title="自动同步" %}
自动计费同步用于解锁家庭赞助（仅适用于企业）和简化许可证更新，管理员无需手动重新上传许可证，例如在组织续订的情况下。要设置自动同步：

{% hint style="info" %}
要成功设置自动计费同步，需要有一个有效的订阅许可证。如果自托管组织是由仍处于试用期的云托管设置设置的，则必须下载许可证，然后在试用期结束后应用到自托管组织。[此处](../plans-and-pricing/password-manager/about-bitwarden-plans.md)了解更多有关付费订阅的信息。
{% endhint %}

### 第 1 步：启用云端通信 <a href="#step-1-enable-cloud-communication" id="step-1-enable-cloud-communication"></a>

首先，您需要配置您的服务器以允许与我们的云端系统进行通信。

{% hint style="info" %}
此步骤必须由有权访问您的自托管实例的配置文件的人员完成。
{% endhint %}

要启用云端通信，请将 `bwdata/env/global.override.env` 中的以下行设置为 `true`：

```systemd
globalSettings__enableCloudCommunication=true
```

设置此值后，运行 `./bitwarden.sh rebuild` 命令以应用您的更改。使用 `./bitwarden.sh start` 命令重启您的服务器。

{% hint style="info" %}
启用自动同步需要与 Bitwarden 的云端系统进行通信。如果您的环境使用防火墙阻止了出站流量，则需要允许 `https://api.bitwarden.com` 或 `https://api.bitwarden.eu` 和 `https://identity.bitwarden.com` 或 `https://identity.bitwarden.eu`。
{% endhint %}

### 第 2 步：获取计费同步令牌 <a href="#step-2-retrieve-billing-sync-token" id="step-2-retrieve-billing-sync-token"></a>

在服务器层面启用云端通信后，需要将同步令牌从用于计费的云端组织传递到您的自托管组织。要从云端 App 获取您的同步令牌：

1、登录到 Bitwarden 网页 App ，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**计费** → **订阅**。

3、向下滚动到「自托管」部分，选择**设置计费同步**按钮。

4、输入主密码然后选择**生成令牌**。

5、复制生成的令牌。

### 第 3 步：应用计费同步令牌 <a href="#step-3-apply-billing-sync-token" id="step-3-apply-billing-sync-token"></a>

要将计费同步令牌应用到您的自托管组织：

1、打开管理控制台，导航到**计费** → **订阅**。

2、在「许可证和计费管理」部分，选择**自动同步**选项。

3、选择**管理计费同步**按钮。

4、粘贴您生成的**计费同步令牌**然后选择**保存**。

{% hint style="info" %}
触发第一次同步后，[企业版家庭](https://help.ppgg.in/self-hosting/self-hosting-families-sponsorships)将每天同步一次。在您触发第一次同步之前，本部分中的**上次同步**字段将报告为**从不**。

用于许可证更新的同步必须始终通过选择**同步许可证**按钮来手动完成（详情请参阅下一部分）。
{% endhint %}

### 第 4 步：触发同步 <a href="#step-4-trigger-sync" id="step-4-trigger-sync"></a>

完成设置后以及**每次需要更新许可证时**都需要触发同步。企业版家庭将**每天**同步一次。要触发同步：

1. 打开自托管管理控制台并导航至**组织** → **计费**。
2. 选择**同步许可证**按钮。

完成设置后请触发同步。计费同步将**每天**进行一次，但您也可以随时手动触发同步。要触发同步：

{% hint style="info" %}
如果您收到一条 `version not supported`（版本不支持）的错误消息，请更新您的服务器并尝试再次上传您的许可证文件。要更新您的服务器，请备份 `bwdata` 目录，然后按照[这些说明](https://help.ppgg.in/self-hosting/update-your-instance)进行操作。
{% endhint %}
{% endtab %}

{% tab title="手动更新" %}
要手动重新上传许可证文件：

1. 按照步骤再次**获取您的许可证**。
2. 打开自托管组织的**计费**选项卡，然后从左侧菜单中选择**订阅**。
3. 在许可证和计费管理部分，选择**手动上传**选项。
4. 选择**浏览...**&#x6216;**选择文件**按钮以添加您的许可证文件。
5. 选择**提交**。

{% hint style="info" %}
如果您收到一个 `version not supported`（版本不受支持）的错误消息，请更新您的服务器并尝试再次上传您的许可证文件。要更新您的服务器，请备份 `bwdata` 目录并按照[这些说明](update-your-instance.md)进行操作。
{% endhint %}
{% endtab %}
{% endtabs %}


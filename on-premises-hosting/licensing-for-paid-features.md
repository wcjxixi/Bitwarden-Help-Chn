# =付费功能许可证

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/licensing-on-premise/)
{% endhint %}

自托管 Bitwarden 是免费的，但是有些功能必须在您的自托管实例中通过注册的许可证文件才能解锁。许可证文件可以由高级个人订阅账户，也可以由组织的所有者从 Bitwarden 托管的[网页密码库](https://vault.bitwarden.com/)中获取。

{% hint style="info" %}
本文中的过程假定您已经开始了一个 Bitwarden 付费订阅。如果还没有，请参阅[关于 Bitwarden 计划](../my-account/plans-and-pricing/about-bitwarden-plans.md)以及[那种计划适合我？](../my-account/plans-and-pricing/what-plan-is-right-for-me.md)。
{% endhint %}

## 个人许可证 <a href="#individual-license" id="individual-license"></a>

要从您的云端帐户获取您的许可证并将其应用于您的自托管服务器：

### 获取您的许可证 <a href="#retrieve-your-license" id="retrieve-your-license"></a>

1. 在云端[网页密码库](https://vault.bitwarden.com/)中，从顶部导航条选择**设置**。
2. 从左侧菜单选择**高级会员**。
3. 选择**下载许可证**按钮。

### 应用您的许可证 <a href="#apply-your-license" id="apply-your-license"></a>

1.  使用与您下载许可证的云托管账户相匹配的电子邮件地址登录到您的自托管网页密码库。

    如果您还没有，请在继续之前先验证您的电子邮件地址。需要已经[配置 SMTP 相关的环境变量](configure-environment-variables.md)。
2. 从顶部导航条选择**设置**。
3. 从左侧菜单选择**高级会员**。
4. 在**许可证文件**部分中，选择**浏览...**按钮，然后添加您刚才下载的许可证文件。
5. 选择**提交**按钮以应用您的高级许可证。

## 组织许可证 <a href="#organization-license" id="organization-license"></a>

要从您的云组织获取您的组织许可证并将其应用于您的自托管服务器：

{% hint style="info" %}
您必须是[组织的所有者](../admin-console/user-management/user-types-and-access-control.md)才能获取和应用许可证。
{% endhint %}

### 获取您的许可证 <a href="#retrieve-your-license" id="retrieve-your-license"></a>

1. 在云端[网页密码库](https://vault.bitwarden.com/)中，打开您的组织。
2. 在您的组织中，打开**设置**标签并从左侧菜单选择**订阅**。
3. 选择**下载许可证**按钮。
4. 提示时，输入安装自托管实例时使用的安装 ID 然后选择**提交**。\
   如果您不知道安装 ID，可以从 `./bwdata/env/global.override.env` 获取。

### 应用您的许可证 <a href="#apply-your-license" id="apply-your-license"></a>

1. 登录到您的自托管网页密码库。
2. 通过选择 **🞤新的组织**以在您的自托管实例中添加一个新的组织。
3. 提示时，上传组织许可证文件然后选择**提交**。

{% hint style="info" %}
如果您收到一个 `version not supported`（版本不受支持）的错误消息，请更新您的服务器并尝试再次上传您的组织许可证文件。要更新您的服务器，请先备份 `bwdata` 目录然后按照[这些说明](update-your-instance.md)进行操作。
{% endhint %}

### 更新已续费的组织许可证 <a href="#update-a-renewed-organization-license" id="update-a-renewed-organization-license"></a>

当您的许可证到期并且您的组织续订时，您有 2 个月的时间将更新后的许可证文件应用到您的自托管组织总。要应用更新后的许可证，请从云托管的 Bitwarden 组织密码库下载新的许可证文件（**上面的步骤 1-3**）。

下载后，打开您的自托管网页密码库然后从组织**设置** → **订阅**页面更新许可证：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6BMl40XY4F6eYF22Ztngwu/5e445c5410c7ea4cca4322d11f820c2c/update-license.png?fm=webp&h=1296&q=50&w=2040" %}
更新自托管许可证
{% endembed %}

如果您收到 `version not supported` 的错误消息，您需要在继续操作之前更新您的服务器。备份或复制 `bwdata` 目录，然后按照[这些说明](update-your-instance.md)进行操作。

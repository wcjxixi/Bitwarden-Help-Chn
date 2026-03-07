# =Huntress SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/huntress-siem/)
{% endhint %}

Huntress 是一个提供威胁检测、调查和响应能力的托管安全平台。Huntress 托管 SIEM 可以集中管理环境中所有日志数据，并能与 Bitwarden 集成，使安全团队能够统一查看密码管理活动以及其安全环境中的其他内容。

## 要求 <a href="#requirements" id="requirements"></a>

要在 Huntress 中设置 Bitwarden 作为日志源，您必须：

* 拥有 Bitwarden 团队版或企业版组织。
* 拥有包含托管的 SIEM 的 Huntress 组织。
* 对 Bitwarden 和 Huntress 均拥有管理权限。

{% hint style="info" %}
Bitwarden 和 Huntress 均使用「组织」一词来描述将用户和数据联系起来的实体。由于在设置过程中需要同时访问这两个系统，本文档将在适用情况下区分 Bitwarden 组织和 Huntress 组织。
{% endhint %}

## 将 Bitwarden 添加为源 <a href="#add-bitwarden-as-a-source" id="add-bitwarden-as-a-source"></a>

要将 Bitwarden 添加为 Huntress 托管的 SIEM 平台上的日志源：

1、在 Huntress 中，导航至 **SIEM** → **数据源管理** 。

{% embed url="https://bitwarden.com/assets/30FE7CyWJrv4aztO5zNLXV/b5f85e14faaeb34f5023afe16ba7d54a/2026-02-18_13-12-18.png?w=800&fm=avif" %}
源管理
{% endembed %}

2、选择**添加源** ，从下拉菜单中选择 **Bitwarden**。

{% embed url="https://bitwarden.com/assets/33tJYy7Wg9swFU36TmSfsp/4a4d8198c5ee47f52f003c93d147623e/2026-02-18_13-13-34.png?w=800&fm=avif" %}
添加源
{% endembed %}

3、选择**添加** 。如果你有其他现有的 Bitwarden 日志源，它们也会列在这一页上。

4、选择配置方法。您选择的方法将取决于您的 Bitwarden 组织是在 Bitwarden 云服务器上还是在自托管服务器上：

{% tabs %}
{% tab title="云托管" %}
如果你的 Bitwarden 组织位于 Bitwarden 云服务器（美国或欧盟）上：

1、选择**我正在使用 Bitwarden 的云托管** ，然后选择**下一步** 。

2、从**组织**下拉菜单中，选择一个包含管理式 SIEM 的 Huntress 组织。

3、提供一个**名称** ，用于识别集成，可选地，提供一个**描述** 。

4、选择**保存** 。

5、在下一页，记下 **HTTP 事件收集器 URL** 和 **HTTP 事件收集器令牌** 。在后续步骤中，您需要使用这些值。

6、在 Bitwarden 中，打开管理控制台，导航至**集成** 页面和**事件管理**标签页。

7、向下滚动到 Huntress 卡片，并选择**连接 Huntress** 按钮：

8、将 Huntress 中的 **HTTP Event Collector URL** 和 **HTTP Event Collector Token** 复制并粘贴到 Bitwarden 中的 **Connect Huntress** 面板。

9、选择**保存** 。
{% endtab %}

{% tab title="自托管" %}
如果您的 Bitwarden 组织使用自托管的 Bitwarden 服务器：

1. 选择**我有一个 Bitwarden 的自托管域名** ，然后选择**下一步** 。
2. 从**组织**下拉菜单中，选择一个包含管理式 SIEM 的 Huntress 组织。
3. 提供一个**名称** ，用于识别集成，可选地，提供一个**描述** 。
4. 输入您自托管服务器上 API 的**基本 URL**。
5. 输入您的 Bitwarden 组织的[客户端 ID 和客户端密钥 ](https://bitwarden.com/help/public-api/#authentication)，这些将用于身份验证。
6. 选择**保存** 。
{% endtab %}
{% endtabs %}

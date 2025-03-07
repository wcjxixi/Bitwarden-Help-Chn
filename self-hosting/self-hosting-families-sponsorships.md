# 自托管家庭赞助

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/families-for-enterprise-self-hosted/)
{% endhint %}

企业组织成员可获得**免费的家庭组织**赞助，适用于新的或现有的家庭组织，可直接从网页密码库兑换。&#x20;

{% hint style="info" %}
如果您想了解有关如何为非赞助自托管家庭组织更新许可证的信息，请参阅[此处](licensing-for-paid-features.md#update-organization-license)。
{% endhint %}

您需要启用自动账单同步，以允许您的自托管企业组织为云家庭组织发放赞助。要设置自动同步：

## 第 1 步：启用云端通信 <a href="#step-1-enable-cloud-communication" id="step-1-enable-cloud-communication"></a>

首先，您需要对服务器进行配置，以允许与我们的云系统进行通信。

{% hint style="info" %}
此步骤必须由有权限访问您的自托管实例配置文件的人员完成。
{% endhint %}

要启用云通信，请将 `bwdata/env/global.override.env` 中的以下行设置为 `true`：

```systemd
globalSettings__enableCloudCommunication=true
```

如果您的云组织是在欧盟服务器上创建的，您还需要设置以下值：

```systemd
globalSettings__baseServiceUri__cloudRegion=EU
globalSettings__installation__identityUri=https://identity.bitwarden.eu
globalSettings__installation__apiUri=https://api.bitwarden.eu
globalSettings__pushRelayBaseUri=https://push.bitwarden.eu
```

{% hint style="info" %}
`globalSettings__baseServiceUri__cloudRegion` 的值必须与获取安装 ID 和密钥时选择的数据区域一致。
{% endhint %}

设置这些值后，运行 `./bitwarden.sh rebuild` 命令以应用您的更改。

{% hint style="info" %}
启用自动同步需要与 Bitwarden 的云系统进行通信。如果您的环境使用防火墙阻止了出站流量，则需要允许 `https://api.bitwarden.com` 或 `https://api.bitwarden.eu` 和 `https://identity.bitwarden.com` 或 `https://identity.bitwarden.eu`。
{% endhint %}

## 第 2 步：获取计费同步令牌 <a href="#step-2-retrieve-billing-sync-token" id="step-2-retrieve-billing-sync-token"></a>

在服务器层面启用云端通信后，需要将同步令牌从用于计费的云组织传递到自托管组织。要从云网页密码库获取同步令牌，您必须是组织的所有者。要获取令牌：

1、打开云云网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、导航到**计费** → **订阅**。

3、向下滚动到「自托管」部分，选择**设置计费同步**按钮。

4、输入主密码然后选择**生成令牌**。

5、复制生成的令牌。

## 第 3 步：应用计费同步令牌 <a href="#step-3-apply-billing-sync-token" id="step-3-apply-billing-sync-token"></a>

要将计费同步令牌应用到您的自托管组织：

{% hint style="danger" %}
在此阶段，如果您要从早期版本升级您的自托管部署，可能需要在继续之前[手动更新您的许可证文件](licensing-for-paid-features.md#organization-license)。
{% endhint %}

1、打开管理控制台，导航到**计费** → **订阅**。

2、在「许可证和计费管理」部分，选择**自动同步**选项。

3、选择**管理计费同步**按钮。

4、粘贴您生成的**计费同步令牌**然后选择**保存**。

{% hint style="info" %}
触发第一次同步后，企业版家庭将每天同步一次。在您触发第一次同步之前，本部分中的**上次同步**字段将报告为**从不**。

许可证更新的同步必须始终通过选择**同步许可证**按钮手动完成（详情请参阅下一部分）。
{% endhint %}

## 第 4 步：触发同步 <a href="#step-4-trigger-sync" id="step-4-trigger-sync"></a>

完成设置后请触发同步。计费同步将**每天**进行一次，但您也可以随时手动触发同步。要触发同步：

1. 打开自托管[系统管理员门户](system-administrator-portal.md)，导航到**组织**然后选择您的企业组织。
2. 找到连接部分然后选择**手动同步**按钮。

{% hint style="info" %}
如果您收到 `version not supported`（版本不支持）错误信息，请更新您的服务器并尝试再次上传您的许可证文件。要更新您的服务器，请备份 `bwdata` 目录，然后按照[这些说明](update-your-instance.md)进行操作。
{% endhint %}

在两次同步之间，兑换或更改赞助后，用户可能会看到 `Awaiting Sync`（等待同步）状态信息。这指示您的自托管 Bitwarden 服务器正在等待与 Bitwarden 云同步，然后赞助才能完全兑换或更改。

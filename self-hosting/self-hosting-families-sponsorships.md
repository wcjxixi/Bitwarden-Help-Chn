# 自托管家庭赞助

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/families-for-enterprise-self-hosted/)
{% endhint %}

如果您自托管 Bitwarden 企业组织，您需要完成一个简短的设置过程，以允许您的用户[兑换家庭组织赞助](../plans-and-pricing/password-manager/redeem-families-sponsorship.md)。

## 第 1 步：启用云端通信 <a href="#step-1-enable-cloud-communication" id="step-1-enable-cloud-communication"></a>

要允许您的自托管企业组织为云端家庭组织颁发赞助，您的服务器需要将有资格获得赞助的用户通告给我们的云端系统通信。

{% hint style="info" %}
此步骤必须由有权限访问您的自托管实例配置文件的人员完成。
{% endhint %}

要启用云通信，请将 `bwdata/env/global.override.env` 中的以下行设置为 `true`：

```systemd
globalSettings__enableCloudCommunication=true
```

设置此值后，运行 `./bitwarden.sh rebuild` 命令以应用更改。

## 第 2 步：更新许可证 <a href="#step-2-update-your-license" id="step-2-update-your-license"></a>

继续操作之前，先[更新您的自托管组织许可证](licensing-for-paid-features.md#organization-license)：

1. 登录云端网页密码库 (`https://vault.bitwarden.com`) 然后导航到您组织的**设置** → **订阅**页面。
2. 选择**下载许可证**按钮。
3. 出现提示时，请输入用于安装您的自托管服务器的安装 ID，然后选择**提交**。\
   如果您一时不知道安装 ID，可以从 `./bwdata/env/global.override.env` 中获取。
4. 登录到您的自托管网页密码库（例如 `https://company.bitwarden.com`）然后导航到您组织的**设置** → **订阅**页面。
5. 选择**更新许可证**按钮并上传更新后的许可证。

## 第 3 步：设置计费同步 <a href="#step-3-setup-billing-sync" id="step-3-setup-billing-sync"></a>

在服务器层面启用云端通信后，需要将同步令牌从用于计费的云端组织传递到自托管组织：

1. 云端网页密码库 (`https://vault.bitwarden.com`) 然后导航到您组织的**设置** → **订阅**页面。
2. 向下滚动到「自托管」部分，然后选择**设置计费同步**按钮。
3. 输入您的主密码并选择**生成令牌**。
4. 复制生成的**计费同步令牌**。
5. 登录到您的自托管网页密码库（例如 `https://company.bitwarden.com`）然后导航到您组织的**设置** → **订阅**页面。
6. 选择**管理计费同步**按钮。
7. 粘贴您生成的**计费同步令牌**然后选择**保存**。

## 第 4 步：触发计费同步 <a href="#step-3-trigger-a-billing-sync" id="step-3-trigger-a-billing-sync"></a>

计费同步后，当某个用户请求赞助时，他们将被允许使用他们的赞助。计费同步将**每天**进行一次，但您可以随时手动触发同步。我们建议您在[设置计费同步](self-hosting-families-sponsorships.md#step-3-setup-billing-sync)后触发一次计费同步：

1. 打开您的[系统管理员门户](system-administrator-portal.md)。
2. 选择 **Organizations** 选项卡然后打开您的企业组织。
3. 向下滚动到「Connections」表，然后在「Billing Sync」条目中选择 **Manually Sync** 按钮。

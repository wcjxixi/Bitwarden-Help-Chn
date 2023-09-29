# 服务器地理位置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/server-geographies/)
{% endhint %}

Bitwarden 云可在全球范围内使用，数据存储在**美国**和**欧盟**地区。无论您使用哪个区域的服务器，Bitwarden 用于保护您的敏感数据采取的措施都是相同的。详细了解 [Bitwarden 如何保护您的数据](storage.md)。

## 选择您的云服务器 <a href="#choose-your-cloud-server" id="choose-your-cloud-server"></a>

要选择在哪个 Bitwarden 服务器地理位置上创建您的账户或组织，请选择登录或注册界面上的**服务器**下拉菜单，然后选择您所需的区域，例如在 Web 应用程序中：

{% embed url="https://bitwarden.com/_gatsby/image/e90a48f400781ce31b6f64c26bd5fb00/9dfed6e43dcce5bd724dfb6bf4af0789/Screen%20Shot%202023-08-14%20at%209.35.12%20AM.webp?eu=898805e0e0c0a9835a6bf1876c7a673db53d51a9a8593ed3696db2f91bfc9fd372fb100476907fb42e6f09dddae140bd33c27c304ae8d2dec0b418f2be67f90050d009bf35b52402557dcea6f4b1460662d90501fcd29f5de0732190b3e2f4334c145f35f62ffc9eebeb6b37f6d92e64e2ebe1297ac1ab1fe3605e05b15171a82ec4909e487abfbcf218b7f9bcaf0e9b98e72e02118df2312b254a1d5aed2deaa1b502796b7d480f349da95fd802c5f469493f4c3d075cb30838d057f87131cbf9faa532883e14e8b6ca346e87c1c1f19004ec7421&a=w%3D850%26h%3D505%26fm%3Dwebp%26q%3D75&cd=2023-08-16T11%3A53%3A15.653Z" %}
区域选择器
{% endembed %}

### 连接您的自托管服务器 <a href="#connect-your-self-hosted-server" id="connect-your-self-hosted-server"></a>

自托管 Bitwarden 组织或个人高级计划需要首先在云服务器上启动订阅，然后[上传许可证文件](../self-hosting/licensing-for-paid-features.md)到您的自托管实例。如果您在 EU 服务器上创建订阅，请将以下[环境变量](../self-hosting/configure-environment-variables.md)添加到服务器的 `./bwdata/env/global.override.env` 文件中，以确保与正确的服务器通信：

```
globalSettings__baseServiceUri__cloudRegion=EU
globalSettings__installation__identityUri=https://identity.bitwarden.eu
globalSettings__installation__apiUri=https://api.bitwarden.eu
globalSettings__pushRelayBaseUri=https://push.bitwarden.eu
```

## 迁移到另一个云 <a href="#migrate-to-another-cloud" id="migrate-to-another-cloud"></a>

要从一个 Bitwarden 云服务器迁移到另一个，例如从美国服务器迁移到欧盟服务器：

1、[导出您的组织密码库](../import-export/export-vault-data.md#export-an-organization-vault)并指导所有组织成员[导出其个人密码库](../import-export/export-vault-data.md#export-a-personal-vault)。

{% hint style="success" %}
单独下载密码库项目的所有文件附件并记下它们属于哪些项目。
{% endhint %}

2、在所需区域创建新的 Bitwarden 账户并开始试用组织。当您准备好时，Bitwarden 支持会将您的订阅迁移到这个新的组织。

3、设置您的新组织，配置企业策略、SSO 登录，构建群组 - 集合关系以及使用目录连接器或 SCIM 邀请用户等。如需帮助，请参阅[概念验证清单](../business-resources/proof-of-concept-project-checklist.md)。

4、导入在**步骤 1** 中获得的组织密码库数据，然后指导组织成员也导入其个人密码库。

{% hint style="info" %}
将**步骤 1** 中获得的文件附件手动上传回与其相关联的密码库项目。
{% endhint %}

5、[请联系 Bitwarden 支持](https://bitwarden.com/contact/)，让您的新组织停止试用并在新的区域恢复订阅。

### 迁移常见问题 <a href="#migration-faqs" id="migration-faqs"></a>

#### 问：我需要迁移吗？

**答**：不需要迁移区域。区域选择器允许组织指定密码库数据的地理位置。不同区域的特性和功能是相同的。

#### 问：有迁移流程吗？

**答**：Bitwarden 区域是不同的云环境。与零知识加密相结合，Bitwarden 无法为客户迁移账户。组织可以使用脚本来帮助完成迁移。

#### 问：迁移脚本有什么作用？

**答**：该脚本与 Bitwarden CLI 配合使用，将数据从一个安装移动到另一个安装。[本文](../miscellaneous/migration-script.md)中提供了说明。此脚本迁移所有组织密码库数据，包括附件、成员角色（不包括自定义角色）以及分配给成员和群组的集合权限。如果您不使用目录集成进行自动配置，该脚本还会自动在新组织中重新创建您的群组。请注意，这不包括单个用户密码库的迁移。

#### 问：手动迁移是什么样的？

**答**：完整的手动迁移涉及在首选区域创建新账户并开始新组织创建过程。配置新组织后，重新邀请用户，然后从旧组织导出密码库数据并导入到新组织中。用户需要手动导出/导入其个人密码库。

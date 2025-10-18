# 为生产准备试用组织

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/prepare-your-org-for-prod/)
{% endhint %}

本指南将帮助指导您的企业在成功试用 Bitwarden 后，为 Bitwarden 的生产实施做好准备。如果您刚开始试用期，我们建议您在使用本指南之前，先从[概念验证项目清单](../../business-resources/proof-of-concept-project-checklist.md)开始。

## 第 1 步： 升级或重新创建新组织 <a href="#step-1-upgrade-or-restart-your-organization" id="step-1-upgrade-or-restart-your-organization"></a>

当您准备好将试用组织转移到业务生产中时，您可以就地升级现有组织或从头开始创建一个新的组织。

大多数客户在将所有共享数据导入生产（**步骤 4a**）之前，会就地升级现有组织并清除试用期间使用的测试数据。

| 步骤 | 持续时间（小时） | 操作          | 描述                                                                                                                            |
| -- | -------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1a | 0.5      | 升级或从头创建您的组织 | [升级您的组织](../organizations-overview.md#upgrade-an-organization)或[创建新的组织](../organizations-overview.md#create-an-organization)。 |

{% hint style="success" %}
如果您选择为生产实施从头开始创建一个新的组织，请再次查看[概念验证项目核对表](../../business-resources/proof-of-concept-project-checklist.md)，并在继续之前完成这些步骤。
{% endhint %}

## 第 2 步：为更广泛的入职做好准备 <a href="#step-2-prep-for-broader-onboarding" id="step-2-prep-for-broader-onboarding"></a>

虽然您的试用组织中可能有一些成员，但大多数企业在转向生产时都会增加更多用户。有鉴于此，在团队其他成员入职之前，您应该采取以下几个关键步骤：

| 步骤 | 持续时间（小时） | 操作       | 描述                                                                                                  |
| -- | -------- | -------- | --------------------------------------------------------------------------------------------------- |
| 2a | 0.5      | 检查您的策略配置 | 为确保配置的策略在所有成员加入后可以立即应用，请检查是否启用了所有需要的策略。                                                             |
| 2b | 0.25     | 激活账户恢复   | 许多组织都认为账户恢复策略至关重要，因为它能够恢复忘记主密码或被剥夺的用户的账户。[马上激活该策略。](../oversight-visibility/enterprise-policies.md) |

## 第 3 步：获取产品许可证 <a href="#step-3-get-a-production-license" id="step-3-get-a-production-license"></a>

**这一步只适用于您自行托管 Bitwarden 的情况**。在试用 Bitwarden 期间，您使用的是一个特殊的试用许可证，需要升级到生产许可证。将自托管服务器升级到生产许可证后，您就可以激活许可证自动同步。请按照以下步骤操作：

| 步骤 | 持续时间（小时） | 操作        | 描述                                                                                                   |
| -- | -------- | --------- | ---------------------------------------------------------------------------------------------------- |
| 3a | 0.25     | 获取您的生产许可证 | 按照[这些步骤](../../self-hosting/licensing.md#retrieve-organization-license)从 Bitwarden 云网页 App 中获取生产许可证。 |
| 3b | 0.25     | 手动更新许可证文件 | 按照[此处](../../self-hosting/licensing.md#update-organization-license)的**手动更新**步骤，将获取到的许可证上传到您的自托管服务器。  |
| 3c | 0.5      | 激活计费同步    | 按照[此处](../../self-hosting/licensing.md#update-organization-license)的**自动同步**步骤设置您的组织，以便将来自动拉取许可证文件。  |

## 第 4 步：导入数据 <a href="#step-4-import-your-data" id="step-4-import-your-data"></a>

在团队其他成员入职前，确保在组织中收集了所有必要的凭证，并确保成员入职后只能访问他们需要的内容。

大多数客户在将所有共享数据导入生产（**步骤 4a**）之前，都会清除试用期间使用的测试数据。可以在组织的**设置** → **组织信息**视图中清除密码库数据，这样可以防止创建重复数据，并帮助您从零开始。

您可能已经完成了大部分或全部步骤，但我们建议您仔细检查这些步骤是否完成得令您满意：

| 步骤 | 持续时间（小时） | 操作   | 描述                                                                                                   |
| -- | -------- | ---- | ---------------------------------------------------------------------------------------------------- |
| 4a | 0.5      | 导入数据 | [导入所有共享数据](../manage-shared-items/import-organization-items/import-data-to-an-organization.md)到生产组织。 |
| 4b | 0.5      | 审计集合 | 在授予更广泛的访问权限之前，确保您的[集合](../manage-shared-items/collections/about-collections.md)包含了正确的密码库项目。          |
| 4c | 0.5      | 审计群组 | 在分配更多用户之前，确保已将您的[群组](../manage-members/groups.md)分配给了正确的集合。                                          |

此外，现在也是检查您管理团队中个人用户的特权的好时机。现在，为会员角色和权限定义良好的做法，一旦您开始入职更多员工，促进用户就会变得更加容易：

| 步骤 | 持续时间（小时） | 操作         | 描述                                                                                                                                                  |
| -- | -------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 4d | 0.75     | 审查成员角色分配   | 审查 Bitwarden 中可用的预定义[成员角色](../manage-members/member-roles.md)，并确定哪个角色适合 IT、管理人员等。                                                                   |
| 4e | 1        | 设置自定义管理员账户 | 许多组织发现，为管理员创建自定义角色非常有用，可以为用户分配细粒度的权限。请查看[本指南](https://bitwarden.com/resources/setting-up-administrative-accounts-with-lesser-privileges/)，了解一些最佳做法。 |

## 第 5 步：配置客户端 App <a href="#step-5-configure-client-apps" id="step-5-configure-client-apps"></a>

由于很快就会有大量用户开始使用 Bitwarden，因此设置某些过程以集中配置和部署关键 Bitwarden 应用程序可能会很有用：

| 步骤 | 持续时间（小时） | 操作            | 描述                                                                                                                                         |
| -- | -------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| 5a | 1        | 为自托管配置客户端     | **仅限自托管**。Bitwarden 客户端可预先配置为指向您的自托管服务器。为此，请按照[这些说明](../deploy-client-apps/connect-managed-devices.md)操作。                                  |
| 5b | 1        | 在受管设备上部署浏览器扩展 | Bitwarden 浏览器扩展是终端用户在日常工作流程中最常用的应用程序，可以自动部署到用户的设备上。为此，请按照[这些说明](../deploy-client-apps/deploy-browser-extensions/browserext-deploy.md)进行操作。 |

## 第 6 步：团队入职 <a href="#step-6-onboard-your-team" id="step-6-onboard-your-team"></a>

现在，您的组织已准备好在生产中使用了，接下来请引导其他用户加入。取决于您在试用期间设置组织的方式，您可能需要：

* [使用 SCIM](../manage-members/scim/about-scim.md)
* [使用目录连接器](../manage-members/directory-connector/about-directory-connector.md)
* [使用手动邀请](../manage-members/user-management.md#onboard-users)

我们强烈建议您在入职其余用户之前，先查看或重新查看[入职和继任](../manage-members/onboarding-and-succession.md)指南。

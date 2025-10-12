# 自托管 Bitwarden

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/self-host-bitwarden/)
{% endhint %}

在查看部署方法之前，与自托管 Bitwarden 所需的关键利益相关方保持一致很重要。在继续之前，请与您的团队一起审查并完成以下文档：

* [自托管检查清单](self-host-setup-checklist.md)

## 云部署 <a href="#cloud-deployment" id="cloud-deployment"></a>

Bitwarden 通过多租户 SaaS 模式提供云端托管服务，提供易于使用和维护的平台，以提高安全性。在考虑托管选项时，下表提供了 Bitwarden 云托管与本文档中后面描述的自托管选项的比较。

| 目标受众          | 所需技能水平 | 预期知识 |
| ------------- | ------ | ---- |
| IT 专业人士，系统管理员 | 最少     | 最少   |

## 自托管部署 <a href="#self-host-deployment" id="self-host-deployment"></a>

对于某些客户而言，出于偏好、监管合规需求或安全策略等原因，需要将 Bitwarden 等平台部署在内网环境，而非使用云端托管模式。

为满足此类需求，Bitwarden 提供基于[源代码](../../security/compliance-audits-and-certifications.md#open-source-codebase)构建的 Docker 容器镜像，并托管于 GitHub Container Registry (GHCR)。用户可以在多种不同的平台上部署和管理此 Docker 容器。本文档概述了在您的环境中自托管 Bitwarden 的支持选项。

{% hint style="success" %}
Bitwarden 的企业版计划包含无额外费用的自托管服务。
{% endhint %}

希望为组织或个人自托管 Bitwarden 服务器的客户有多种部署选项，包括：

* 部署 Bitwarden 的服务器和基础设施。
* 服务器使用的数据库。
* 服务器使用的证书。

### Linux 部署 <a href="#linux-deployment" id="linux-deployment"></a>

#### Linux 标准部署 <a href="#linux-standard-deployment" id="linux-standard-deployment"></a>

使用提供的 Bash 设置脚本将 Bitwarden 部署到 Linux 服务器上，以自动化 Bitwarden 容器部署和维护。适合有 Linux 系统及命令行操作经验的人员。提供对部署环境的灵活性和控制。[立即开始](../deploy-and-configure/docker/linux-standard-deployment.md)。

| 目标受众          | 所需技能水平 | 预期知识            |
| ------------- | ------ | --------------- |
| IT 专业人士，系统管理员 | 中级到高级  | Linux 命令行、服务器管理 |

#### Linux 手动部署 <a href="#linux-manual-deployment" id="linux-manual-deployment"></a>

通过手动配置和构建可下载的安装工件中的容器和运行时环境，将 Bitwarden 部署到 Linux 服务器上。适合集成到现有的 Docker 容器管理和流程中，但维护和升级需要额外的手动步骤。[开始使用](../deploy-and-configure/docker/linux-standard-deployment-1.md)。

| 目标受众                   | 所需技能水平 | 预期知识                            |
| ---------------------- | ------ | ------------------------------- |
| 具有现有 Docker 管理经验的系统管理员 | 高级     | Linux 命令行、服务器维护、使用 Docker 的容器管理 |

#### Linux 离线部署 <a href="#linux-offline-deployment" id="linux-offline-deployment"></a>

通过配置可下载的安装工件中的容器和运行时环境，将 Bitwarden 部署到离线或断网的 Linux 服务器环境。适用于集成到现有的自托管 Docker 仓库中，并需要额外的手动步骤进行维护和升级。[开始使用](../deploy-and-configure/docker/linux-offline-deployment.md)。

| 目标受众                      | 所需技能水平 | 预期知识                                    |
| ------------------------- | ------ | --------------------------------------- |
| 具有现有 Docker 管理经验的网络和系统管理员 | 高级     | Linux 命令行、服务器维护、使用 Docker 的容器管理、网络设计与设置 |

### Windows 部署 <a href="#windows-deployment" id="windows-deployment"></a>

#### Windows 标准部署 <a href="#windows-standard-deployment" id="windows-standard-deployment"></a>

使用提供的 Powershell 设置脚本，通过 Docker Desktop 将 Bitwarden 部署到 Windows 服务器上。适合熟悉 Windows 服务器环境的用户。需要了解 Windows 特定的安装和配置流程。[开始使用](../deploy-and-configure/docker/windows-standard-deployment.md)。

| 目标受众          | 所需技能水平 | 预期知识                         |
| ------------- | ------ | ---------------------------- |
| IT 专业人士，系统管理员 | 中级     | Windows Server 管理、PowerShell |

#### Windows 离线部署 <a href="#windows-offline-deployment" id="windows-offline-deployment"></a>

通过配置可下载的安装工件中的容器和运行时环境，将 Bitwarden 部署到离线或断网的 Windows 服务器环境。适用于集成到现有的自托管 Docker 仓库中，维护和升级需要额外的手动步骤。[开始使用](../deploy-and-configure/docker/windows-offline-deployment.md)。

| 目标受众                      | 所需技能水平 | 预期知识                             |
| ------------------------- | ------ | -------------------------------- |
| 具有现有 Docker 管理经验的网络和系统管理员 | 高级     | Windows 服务器管理、Powershell、网络设计和配置 |

### Bitwarden Unified 部署 (beta) <a href="#bitwarden-unified-deployment" id="bitwarden-unified-deployment"></a>

将 Bitwarden 部署为单个 Docker 容器。适合个人用户、家庭实验室或轻量级共享。[立即开始](../deploy-and-configure/docker/unified-deployment-beta.md)。

| 目标受众 | 所需技能水平 | 预期知识                      |
| ---- | ------ | ------------------------- |
| 产消者  | 中级     | Linux 命令行、使用 Docker 的容器管理 |

### Kubernetes & Helm 部署 <a href="#kubernetes-and-helm-deployments" id="kubernetes-and-helm-deployments"></a>

使用 Helm 图表在不同 Kubernetes 环境中部署 Bitwarden。专为高可用性和容器化部署设计，适用于云原生和大规模的共享或专用集群部署。兼容多种 Kubernetes 基础组件（如存储和 Ingress 配置），但需要相关设置知识。

| 目标受众            | 所需技能水平 | 预期知识                  |
| --------------- | ------ | --------------------- |
| DevOps 工程师，云管理员 | 高级     | Kubernetes 编排、Helm 图表 |

开始使用：

* [Azure AKS 部署](../deploy-and-configure/helm/azure-aks-deployment.md)
* [OpenShift 部署](../deploy-and-configure/helm/openshift-deployment.md)
* [AWS EKS 部署](../deploy-and-configure/helm/aws-eks-deployment.md)

## 更多选项 <a href="#further-options" id="further-options"></a>

### 数据库选项 <a href="#database-options" id="database-options"></a>

所有 Bitwarden 自托管服务器部署，除 [Unified](../deploy-and-configure/docker/unified-deployment-beta.md) 部署外，默认使用 MSSQL Express 镜像，但客户可以连接到 2019 版本或更高版本的 MSSQL 外部服务器或集群。[了解更多](../deploy-and-configure/configuration-options/database-options.md)。

### 证书选项 <a href="#certificate-options" id="certificate-options"></a>

自托管 Bitwarden 的客户可以选择多种不同的 SSL 证书选项部署 Bitwarden。[了解更多](../deploy-and-configure/configuration-options/certificate-options.md)。

## 下一步 <a href="#next-steps" id="next-steps"></a>

* 使用上面链接的**安装和部署指南**之一来部署 Bitwarden。
* 如果您为组织托管 Bitwarden，请使用[此指南](self-host-an-organization.md)来为推广到用户做好准备。
* 与您的团队一起完成 [Bitwarden 自托管检查清单](self-host-setup-checklist.md)。此文档将帮助确保您在部署过程中涉及的各方保持一致，并且可以下载为 PDF 格式。

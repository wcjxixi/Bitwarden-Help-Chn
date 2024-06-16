# =Secrets Manager Kubernetes Operator

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-kubernetes-operator/)
{% endhint %}

{% hint style="danger" %}
Bitwarden Secrets Manager Helm 集成目前处于 **Beta 状态**。某些功能目前可能无法提供完整功能。
{% endhint %}

Bitwarden Secrets Manager Kubernetes Operator 将允许团队安全高效地将 Secrets Manager 集成到 Kubernetes 工作流中。使用 Helm 包管理器部署的 operator，可以从 Secrets Manager 中存储和检索机密。

`sm-operator` 使用控制器将 Bitwarden 机密同步到 Kubernetes 机密中。operator 将 Custom Resource Definition: `BitwardenSecret` 注册到 Kubernetes 集群中。集群将侦听新注册的 `BitwardenSecret` ，并按可配置的时间间隔进行同步。

## 要求 <a href="#requirements" id="requirements"></a>

首先，需要一个具有 [Secrets Manager](../secrets-manager-overview.md) 的活动 Bitwarden 组织。此外，还需要一个或多个与[机器账户](../your-secrets/machine-accounts.md)关联的[访问令牌](../your-secrets/access-tokens.md)。

**额外的依赖**

* [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)
* [Helm 3](https://v3.helm.sh/docs/intro/install/)

## 将存储库添加到 Helm <a href="#add-the-repository-to-helm" id="add-the-repository-to-helm"></a>

## 安装 <a href="#installation" id="installation"></a>

### 创建配置文件 <a href="#create-a-configuration-file" id="create-a-configuration-file"></a>

### 更新配置文件 <a href="#pdate-configuration-file" id="pdate-configuration-file"></a>

## 升级 Helm 图表 <a href="#upgrade-helm-chart" id="upgrade-helm-chart"></a>

## 创建 Bitwarden 机密 <a href="#create-bitwarden-secrets" id="create-bitwarden-secrets"></a>

## 部署 BitwardenSecret <a href="#deploy-bitwardensecret" id="deploy-bitwardensecret"></a>

## 图表使用示例 <a href="#example-usage-chart" id="example-usage-chart"></a>

# Secrets Manager Kubernetes Operator

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-kubernetes-operator/)
{% endhint %}

{% hint style="danger" %}
Bitwarden Secrets Manager Helm 集成目前处于 **Beta 状态**。某些功能目前可能无法提供完整功能。
{% endhint %}

Bitwarden Secrets Manager Kubernetes Operator 允许团队安全高效地将 Secrets Manager 集成到 Kubernetes 工作流中。使用 Helm 包管理器部署的 operator，可以从 Secrets Manager 中存储和检索机密。

`sm-operator` 使用控制器将 Bitwarden 机密同步到 Kubernetes 机密中。operator 将 Custom Resource Definition: `BitwardenSecret` 注册到 Kubernetes 集群中。集群将侦听新注册的 `BitwardenSecret` ，并按可配置的时间间隔进行同步。

## 要求 <a href="#requirements" id="requirements"></a>

首先，需要一个具有 [Secrets Manager](../secrets-manager-overview.md) 的活动 Bitwarden 组织。此外，还需要一个或多个与[机器账户](../your-secrets/machine-accounts.md)关联的[访问令牌](../your-secrets/access-tokens.md)。

**额外的依赖**

* [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)
* [Helm 3](https://v3.helm.sh/docs/intro/install/)

## 将存储库添加到 Helm <a href="#add-the-repository-to-helm" id="add-the-repository-to-helm"></a>

添加 Bitwarden Secrets Manager 图表存储库：

```bash
helm repo add bitwarden https://charts.bitwarden.com/
```

更新本地可用图表的信息：

```bash
helm repo update
```

## 安装 <a href="#installation" id="installation"></a>

### 创建配置文件 <a href="#create-a-configuration-file" id="create-a-configuration-file"></a>

创建用于部署的自定义值文件：

```bash
helm show values bitwarden/sm-operator > my-values.yaml
```

### 更新配置文件 <a href="#pdate-configuration-file" id="pdate-configuration-file"></a>

定位到 `my-values.yaml` 并填写所需的值。[Bitwarden 存储库](https://github.com/bitwarden/helm-charts/blob/535ad726cfc9dd5c9cd18531c15008d0d939ed74/charts/sm-operator/values.yaml)中提供了一个示例。我们建议根据您的设置调整以下值：

| 值                                               | 描述                                                                                                                                                                                                                                                                            |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `settings.bwSecretsManagerRefreshInterval`      | 机密同步的频率（以秒为单位）。最小值为 180。                                                                                                                                                                                                                                                      |
| `settings.cloudRegion`                          | 自托管用户设置为 `US` 或 `EU` 云区域以用于同步。有关更多信息，请参阅[启用云通信](../../self-hosting/self-hosting-families-sponsorships.md#step-1-enable-cloud-communication)。                                                                                                                                  |
| `settings.bwApiUrlOverride`                     | 仅适用于自托管用户。这是您的实例 API 的 URL。                                                                                                                                                                                                                                                   |
| `settings.bwIdentityUrlOverride`                | 仅适用于自托管用户。这是您的实例的身份服务的 URL。                                                                                                                                                                                                                                                   |
| `containers.enableSeccompProfileRuntimeDefault` | <p>设置为 <code>false</code> 以在较旧的 Kubernetes 版本 (&#x3C; 1.19) 或默认情况下不支持此字段的供应商版本（例如 OpenShift &#x3C; 4.11）上工作。</p><p>对于不需要升级权限来限制容器的大多数常见情况，建议使用此设置。有关更多信息，请参阅 <a href="https://kubernetes.io/docs/concepts/security/pod-security-standards/#restricted">Kubernetes 文档</a>。</p> |

{% hint style="info" %}
要使用与图表中包含的版本不同的操作映像版本，请更新：\
`containers.manager.image.tag`.
{% endhint %}

## 升级 Helm 图表 <a href="#upgrade-helm-chart" id="upgrade-helm-chart"></a>

配置 `values.yaml` 文件后，通过运行以下命令将版本升级到新图表：

```bash
helm upgrade sm-operator bitwarden/sm-operator -i --debug -n sm-operator-system --create-namespace --values my-values.yaml
```

此命令在命名空间 `sm-operator-system` 中安装或升级名为 `sm-operator` 的版本，其值来自 `my-values.yaml` 。

{% hint style="info" %}
要查看 `helm install` 或 `helm upgrade` 命令的信息，请运行 `helm install --help` 或 `helm upgrade --help` 。
{% endhint %}

## 创建 Bitwarden 机密 <a href="#create-bitwarden-secrets" id="create-bitwarden-secrets"></a>

要将存储在 Bitwarden Secrets Manager 中的机密同步到 Kubernetes 机密中，我们必须创建一个 BitwardenSecret 对象。

创建 Kubernetes 机密以使用 Secrets Manager 进行身份验证：

```bash
kubectl create secret generic bw-auth-token -n <YOUR_NAMESPACE> --from-literal=token="<TOKEN_HERE>"
```

{% hint style="danger" %}
该命令记录在您的 shell 历史记录中。为了避免暴露访问令牌数据，请考虑使用临时管道代理进行部署。
{% endhint %}

## 部署 BitwardenSecret <a href="#deploy-bitwardensecret" id="deploy-bitwardensecret"></a>

`BitwardenSecret` 对象是同步设置，operator 将使用它来创建和同步 Kubernetes 机密。 Kubernetes 机密属于命名空间，并将被注入 Secrets Manager [机器账户](../your-secrets/machine-accounts.md)有权访问的数据。

使用自定义映射的 BitwardenSecret 部署示例：

```bash
cat <<EOF | kubectl apply -n <YOUR_NAMESPACE> -f -
apiVersion: k8s.bitwarden.com/v1
kind: BitwardenSecret
metadata:
  labels:
    app.kubernetes.io/name: bitwardensecret
    app.kubernetes.io/instance: bitwardensecret-sample
    app.kubernetes.io/part-of: sm-operator
    app.kubernetes.io/managed-by: kustomize
    app.kubernetes.io/created-by: sm-operator
  name: bitwardensecret-sample
spec:
  organizationId: "a08a8157-129e-4002-bab4-b118014ca9c7"
  secretName: bw-sample-secret
  map:
    - bwSecretId: 6c230265-d472-45f7-b763-b11b01023ca6
    secretKeyName: test__secret__1
    - bwSecretId: d132a5ed-12bd-49af-9b74-b11b01025d58
    secretKeyName: test__secret__2
  authToken:
    secretName: bw-auth-token
    secretKey: token
EOF
```

在 BitwardenSecret 部署示例中， `custom map` 元素是可选的。

| 设置                    | 描述                                                                                 |
| --------------------- | ---------------------------------------------------------------------------------- |
| `metadata.name`       | 您正在部署的 BitwardenSecret 对象的名称。                                                      |
| `spec.organizationId` | 您从中提取 Secrets Manager 数据的 Bitwarden 组织 ID。                                         |
| `spec.secretName`     | 将创建并注入 Secrets Manager 数据的 Kubernetes 机密的名称。                                       |
| `spec.authToken`      | BitwardenSecrets 对象部署到的 Kubernetes 命名空间内的机密名称，其中包含跨机密使用的 Secrets Manager 机器账户授权令牌。 |

{% hint style="danger" %}
Secrets Manager 不保证跨工程的唯一机密名称。默认情况下，将使用 Secrets Manager 机密 UUID 用作密钥来创建机密。
{% endhint %}

为了使生成的机密更易于使用，您可以创建 Bitwarden Secrets ID 到 Kubernetes 机密密钥的映射。生成的机密将用您提供的映射名称替换 Bitwarden 机密 ID。

Available map settings: 可用的图标设置：

| 设置              | 描述                                                                                                            |
| --------------- | ------------------------------------------------------------------------------------------------------------- |
| `bwSecretId`    | 这是 Secrets Manager 中机密的 UUID（通用唯一标识符）。这可以在 Secrets Manager Web 门户中的机密名称下或使用 Bitwarden Secrets Manager CLI 找到。 |
| `secretKeyName` | Kubernetes 机密中生成的密钥替换了 UUID。                                                                                  |

## 图表使用示例 <a href="#example-usage-chart" id="example-usage-chart"></a>

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
  labels:
    app: my-deployment
spec:
  selector:
    matchLabels:
      app: my-deployment
  template:
    metadata:
      labels:
        app: my-deployment
    spec:
      containers:
      - name: my-deployment
        image: <some-image>
      imagePullSecrets:
      - name: <my-secret-name>
      envFrom:
      - secretRef:
          name: bw-sample-secret
```

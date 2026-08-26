# =使用 Helm 自托管

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/self-host-with-helm/)
{% endhint %}

本文将指导您使用 Helm chart 在不同的 Kubernetes 部署中安装和部署 Bitwarden。

本文将介绍在 Kubernetes 上托管 Bitwarden 的通用步骤。提供了特定于提供商的指南，可帮助您深入了解如何根据每个提供商的特定产品来调整部署：

* [Azure AKS 部署](azure-aks-deployment.md)
* [OpenShift 部署](openshift-deployment.md)
* [AWS EKS 部署](aws-eks-deployment.md)

## 要求 <a href="#requirements" id="requirements"></a>

在继续安装之前，请确保满足以下要求：

* 已安装 [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)。
* 已安装 [Helm 3](https://helm.sh/docs/intro/install/)。
* 您拥有 SSL 证书和密钥，或者可以通过证书提供程序创建 SSL 证书和密钥。
* 您拥有 SMTP 服务器或可以访问云端 SMTP 提供程序。
* 一个支持 ReadWriteMany 的[存储类](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)。
* 您已从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取了安装 ID 和密钥。

### 无根模式要求 <a href="#rootless-requirements" id="rootless-requirements"></a>

Bitwarden 会在启动时检测您的环境是否限制了用户容器的运行身份，并在检测到限制时自动以无根模式启动部署。要成功以无根模式部署，需满足以下两个选项之一：

* 部署[外部 MSSQL 数据库](../configuration-options/connect-to-an-external-mssql-database.md)，而不是 Helm chart 中默认包含的 SQL 容器。
* 使用[服务账户](../configuration-options/kubernetes-service-accounts.md)、[Pod 安全上下文](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/#set-the-security-context-for-a-pod)或其他方法为包含的 SQL 容器分配升的权限。

{% hint style="info" %}
虽然 Microsoft 要求 SQL 容器必须以 root 身份运行，但容器启动后会在执行应用程序代码前逐步降级为非 root 用户。
{% endhint %}

## 准备图表 <a href="#prepare-the-chart" id="prepare-the-chart"></a>

### 将存储库添加到 Helm <a href="#add-the-repo-to-helm" id="add-the-repo-to-helm"></a>

使用以下命令将存储库添加到 Helm：

```bash
helm repo add bitwarden https://charts.bitwarden.com/
helm repo update
```

### 创建命名空间 <a href="#create-a-namespace" id="create-a-namespace"></a>

创建一个命名空间来部署 Bitwarden。我们的文档假定名称空间名为 `bitwarden`，因此如果您选择不同的名称，请务必修改相应的命令。

```bash
kubectl create namespace bitwarden
```

### 创建配置 <a href="#create-a-configuration" id="create-a-configuration"></a>

使用以下命令创建一个 `my-values.yaml` 配置文件，用于自定义部署：

```bash
helm show values bitwarden/self-host > my-values.yaml
```

您必须在您的 `my-values.yaml` 文件中至少配置下表中的值，但是，您可以在[此处](https://github.com/bitwarden/helm-charts/blob/main/charts/self-host/values.yaml)找到完整的值列表。

#### 必需变量 <a href="#required-variables" id="required-variables"></a>

<table data-search="true"><thead><tr><th>值</th><th>描述</th></tr></thead><tbody><tr><td><code>general.domain:</code></td><td>指向您群集的公共 IP 地址的域名。</td></tr><tr><td><code>general.ingress.enabled:</code></td><td>是否使用图表中定义的 nginx 入口控制器（<a href="self-host-with-helm.md#adding-rawmanifest-files">请参阅使用未包含的入口控制器的示例</a>）。</td></tr><tr><td><code>general.ingress.className:</code></td><td>例如，<code>"nginx"</code> 或 <code>"azure-application-gateway"</code>（<a href="azure-aks-deployment.md#azure-application-gateway">示例</a>）。设置为 <code>general.ingress.enabled: false</code> 以使用其他入口控制器。</td></tr><tr><td><code>general.ingress.annotations:</code></td><td>添加到入口控制器的注释。如果您使用包含的 nginx 控制器，则提供了默认值，您必须取消注释并可以根据需要进行自定义。</td></tr><tr><td><code>general.ingress.paths:</code></td><td>如果您使用默认的 nginx 控制器，则提供了默认值，您可以根据需要进行自定义。</td></tr><tr><td><code>general.ingress.cert.tls.name:</code></td><td>您的 TLS 证书的名称。我们将通过<a href="self-host-with-helm.md#example-certificate-setup">一个示例</a>进行演示，如果您已经有，请现在输入，或者稍后再回来修改。</td></tr><tr><td><code>general.ingress.cert.tls.clusterIssuer:</code></td><td>您的 TLS 证书颁发者的名称。稍后我们将通过<a href="self-host-with-helm.md#example-certificate-setup">一个示例</a>进行演示，如果您已经有，请现在输入，或者稍后再回来修改。</td></tr><tr><td><code>general.email.replyToEmail:</code></td><td>用于发送邀请的电子邮箱地址，通常为 <code>no_reply@smtp_host</code>。</td></tr><tr><td><code>general.email.smtpHost:</code></td><td>您的 SMTP 服务器主机名或 IP 地址。</td></tr><tr><td><code>general.email.smtpPort:</code></td><td>SMTP 服务器使用的 SMTP 端口。</td></tr><tr><td><code>general.email.smtpSsl:</code></td><td>您的 SMTP 服务器是否使用加密协议（<code>true</code> = SSL、<code>false</code> = TLS）。</td></tr><tr><td><code>enableCloudCommunication:</code></td><td>设置为 <code>true</code> 以允许您的服务器与我们的云系统进行通信。这样做可以<a href="../../plan-for-deployment/self-host-an-organization.md#step-4-setup-billing-and-license-sync">启用计费和许可证同步</a>。</td></tr><tr><td><code>cloudRegion:</code></td><td>默认为 <code>US</code> 。如果您的组织是通过<a href="../../../security/server-geographies.md">欧盟云服务器</a>启动的，请设置为 <code>EU</code> 。</td></tr><tr><td><code>sharedStorageClassName:</code></td><td>您需要提供的共享存储类的名称，并且必须支持 <a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes">ReadWriteMany</a>（<a href="azure-aks-deployment.md#creating-a-storage-class">请参阅使用 Azure 文件存储的示例</a>），除非它是单节点集群。</td></tr><tr><td><code>secrets.secretName:</code></td><td>您的 <a href="https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#define-container-environment-variables-using-secret-data">Kubernetes 机密对象</a>的名称。您将在下一步创建此对象，因此现在确定一个名称，或者稍后再回来修改这个值。</td></tr><tr><td><code>database.enabled:</code></td><td>是否使用图表中包含的 SQL Pod。如果使用外部 SQL 服务器，则只需设置为 <code>false</code> 。</td></tr><tr><td><code>component.scim.enabled</code></td><td>SCIM Pod 默认是禁用的。要启用 SCIM Pod，请将值设置为 <code>= true</code> 。</td></tr><tr><td><code>component.volume.logs.enabled:</code></td><td>虽然不是必需的，但出于故障排除目的，我们建议设置为 <code>true</code> 。</td></tr></tbody></table>

### 创建机密对象 <a href="#create-a-secret-object" id="create-a-secret-object"></a>

创建一个 [Kubernetes 机密对象](https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#define-container-environment-variables-using-secret-data)，至少设置以下值：

<table data-search="true"><thead><tr><th>值</th><th>描述</th></tr></thead><tbody><tr><td><code>globalSettings__installation__id</code></td><td>从 <a href="https://bitwarden.com/host/">https://bitwarden.com/host</a> 获取到的有效安装 ID。更多信息，请参阅<a href="../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for">我的安装 ID 和安装密钥是用来干什么的？</a></td></tr><tr><td><code>globalSettings__installation__key</code></td><td>从 <a href="https://bitwarden.com/host/">https://bitwarden.com/host</a> 获取到的有效安装密钥。更多信息，请参阅<a href="../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for">我的安装 ID 和安装密钥是用来干什么的？</a></td></tr><tr><td><code>globalSettings__mail__smtp__username</code></td><td>您的 SMTP 服务器的有效用户名。</td></tr><tr><td><code>globalSettings__mail__smtp__password</code></td><td>输入的 SMTP 服务器用户名的有效密码。</td></tr><tr><td><code>globalSettings__yubico__clientId</code></td><td>YubiCloud 验证服务或自托管 Yubico 验证服务器的客户端 ID。如果是 YubiCloud，请在<a href="https://upgrade.yubico.com/getapikey/">这里</a>获取您的客户端 ID 和密钥。</td></tr><tr><td><code>globalSettings__yubico__key</code></td><td>YubiCloud 验证服务或自托管 Yubico 验证服务器的密钥。如果是 YubiCloud，请在<a href="https://upgrade.yubico.com/getapikey/">这里</a>获取您的客户端 ID 和密钥。</td></tr><tr><td><code>globalSettings__hibpApiKey</code></td><td>的 HaveIBeenPwned (HIBP) API 密钥，可<a href="https://haveibeenpwned.com/API/Key">在此处</a>获取。此密钥允许用户在创账户时运行<a href="../../../password-manager/your-vault/security-tools/vault-health-reports.md#data-breach-report-individual-vaults-only">数据泄露报告</a>并检查其主密码是否存在泄露。</td></tr><tr><td><p>如果您使用的是 Bitwarden SQL pod，<code>SA_PASSWORD</code></p><p>如果您使用自己的 SQL 服务器，<code>globalSettings__sqlServer__connectionString</code></p></td><td>连接到 Bitwarden 实例的数据库的凭据。所需内容取决于您使用的是附带的 SQL Pod 还是外部 SQL 服务器。</td></tr></tbody></table>

使用 `kubectl create secret` 命令设置这些值的示例如下所示：

{% hint style="warning" %}
此示例会将命令记录到您的 shell 历史记录中。可以考虑使用其他方法来安全地设置机密。
{% endhint %}

```bash
kubectl create secret generic custom-secret -n bitwarden \
    --from-literal=globalSettings__installation__id="REPLACE" \
    --from-literal=globalSettings__installation__key="REPLACE" \
    --from-literal=globalSettings__mail__smtp__username="REPLACE" \
    --from-literal=globalSettings__mail__smtp__password="REPLACE" \
    --from-literal=globalSettings__yubico__clientId="REPLACE" \
    --from-literal=globalSettings__yubico__key="REPLACE" \
    --from-literal=globalSettings__hibpApiKey="REPLACE" \
    --from-literal=SA_PASSWORD="REPLACE"
```

不要忘记将 `secrets.secretName:` 中的值设置为 `my-values.yaml` 中创建的机密的名称，在本例中为 `custom-secret`。

### 证书设置示例 <a href="#example-certificate-setup" id="example-certificate-setup"></a>

部署需要 TLS 证书和密钥，或者通过证书提供商创建一个。以下示例将引导您使用 [cert-manager](https://cert-manager.io/docs/) 生成一个由 Let's Encrypt 签发的证书：

1、使用以下命令在集群上安装 cert-manager：

```bash
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.11.0/cert-manager.yaml
```

2、定义证书颁发者。在您的 DNS 记录指向您的集群之前，Bitwarden 建议在此示例中使用 **Staging** 配置。请务必将占位符 `email:` 替换为有效值：

{% tabs %}
{% tab title="Staging" %}
```bash
cat <<EOF | kubectl apply -n bitwarden -f -
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: letsencrypt-staging
spec:
  acme:
    server: https://acme-staging-v02.api.letsencrypt.org/directory
    email: me@example.com
    privateKeySecretRef:
      name: tls-secret
    solvers:
      - http01:
          ingress:
            class: nginx #use "azure/application-gateway" for Application Gateway ingress
EOF
```
{% endtab %}

{% tab title="Production" %}
```bash
cat <<EOF | kubectl apply -n bitwarden -f -
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: letsencrypt-production
spec:
  acme:
    server: https://acme-v02.api.letsencrypt.org/directory
    email: me@example.com
    privateKeySecretRef:
      name: tls-secret
    solvers:
      - http01:
          ingress:
            class: nginx #use "azure/application-gateway" for Application Gateway ingress
EOF
```
{% endtab %}
{% endtabs %}

3、如果尚未设置，请确保在 `my-values.yaml` 中设置 `general.ingress.cert.tls.name:` 和 `general.ingress.cert.tls.clusterIssuer:` 的值。在这个例子中，您需要设置为：

* `general.ingress.cert.tls.name: tls-secret`
* `general.ingress.cert.tls.clusterIssuer: letsencrypt-staging`

### 添加 rawManifest 文件 <a href="#adding-rawmanifest-files" id="adding-rawmanifest-files"></a>

Bitwarden 自托管 Helm 图表允许您在安装之前或之后包含其他 Kubernetes 清单文件。为此，请更新图表的 `rawManifests` 部分（[了解更多](add-rawmanifest-files.md)）。例如，在您想使用除默认定义的 nginx 控制器以外的其他入口控制器的情况下，这非常有用。

## 安装图表 <a href="#install-the-chart" id="install-the-chart"></a>

要使用 `my-values.yaml` 中的配置安装 Bitwarden，请运行以下命令：

```bash
helm upgrade bitwarden bitwarden/self-host --install --namespace bitwarden --values my-values.yaml
```

恭喜！Bitwarden 现已启动并在 `https://your.domain.com` 上正常运行了，如在 `my-values.yaml` 中所定义的那样。请在浏览器中访问网页密码库以确认其正在运行。您现在可以注册一个新账户然后登录。

您需要设置 SMTP 配置和相关的机密信息，以便验证您的新账户的电子邮箱。

## 下一步 <a href="#next-steps" id="next-steps"></a>

### 数据库备份与恢复 <a href="#database-backup-and-restore" id="database-backup-and-restore"></a>

在[此存储库](https://github.com/bitwarden/helm-charts/tree/main/examples)中，我们提供了两个示例作业，用于在 Bitwarden 数据库 Pod 中备份和恢复数据库。如果您正在使用的是未作为此 Helm 图表的一部分部署的自己的 SQL Server 实例，请遵循您公司的备份和恢复策略。

数据库备份和备份策略最终由实施者决定。备份可以在集群之外按照一定的时间间隔进行调度，也可以修改为在 Kubernetes 中创建 CronJob 对象进行调度。

备份作业将为以前的备份创建带有时间戳的版本。当前备份简单地称为 `vault.bak` 。这些文件放在 MS SQL 备份持久卷中。恢复作业将在同一持久卷中查找 `vault.bak` 。

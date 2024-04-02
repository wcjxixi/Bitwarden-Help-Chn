# =使用 Helm 自托管

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/self-host-with-helm/)
{% endhint %}

本文将指导您完成使用 Helm 图表在不同 Kubernetes 部署中安装和部署 Bitwarden 的过程。

本文将描述在 Kubernetes 上托管 Bitwarden 的通用步骤。提供了特定于提供商的指南，可帮助您深入了解如何根据每个提供商的特定产品来更改部署：

* [Azure AKS 部署](azure-aks-deployment.md)
* [OpenShift 部署](openshift-deployment.md)
* [AWS EKS 部署](aws-eks-deployment.md)

## 要求 <a href="#requirements" id="requirements"></a>

在继续安装之前，请确保满足以下要求：

* 已安装 [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)。
* 已安装 [Helm 3](https://helm.sh/docs/intro/install/)。
* 您拥有 SSL 证书和密钥，或者可以通过证书提供商创建 SSL 证书和密钥。
* 您拥有 SMTP 服务器或可以访问云 SMTP 提供商。
* 一个支持 ReadWriteMany 的[存储类](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)。
* 您有一个从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取到的安装 ID 和密钥。

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

使用以下命令创建一个 `my-values.yaml` 配置文件，您将使用该文件来自定义部署：

```bash
helm show values bitwarden/self-host --devel > my-values.yaml
```

您必须在 `my-values.yaml` 文件中至少配置以下值：

| 值                                         | 描述                                                                                                                                                                                                             |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `general.domain:`                         | 指向您群集的公共 IP 地址的域名。                                                                                                                                                                                             |
| `general.ingress.enabled:`                | 是否使用图表中定义的 nginx 入口控制器（[请参阅使用未包含的入口控制器的示例](self-host-with-helm.md#adding-rawmanifest-files)）。                                                                                                                  |
| `general.ingress.className:`              | 例如，`"nginx"` 或 `"azure-application-gateway"`（[示例](azure-aks-deployment.md#azure-application-gateway)）。设置为 `general.ingress.enabled: false` 以使用其他入口控制器。                                                         |
| `general.ingress.annotations:`            | 添加到入口控制器的注释。如果您使用包含的 nginx 控制器，则提供了默认值，您必须取消注释并可以根据需要进行自定义。                                                                                                                                                    |
| `general.ingress.paths:`                  | 如果您使用默认的 nginx 控制器，则提供了默认值，您可以根据需要进行自定义。                                                                                                                                                                       |
| `general.ingress.cert.tls.name:`          | 您的 TLS 证书的名称。我们将通过[一个示例](self-host-with-helm.md#example-certificate-setup)进行演示，如果您已经有，请现在输入，或者稍后再回来修改。                                                                                                         |
| `general.ingress.cert.tls.clusterIssuer:` | 您的 TLS 证书颁发者的名称。稍后我们将通过[一个示例](self-host-with-helm.md#example-certificate-setup)进行演示，如果您已经有，请现在输入，或者稍后再回来修改。                                                                                                    |
| `general.email.replyToEmail:`             | 用于邀请的电子邮件地址，通常为 `no_reply@smtp_host`。                                                                                                                                                                          |
| `general.email.smtpHost:`                 | 您的 SMTP 服务器主机名或 IP 地址。                                                                                                                                                                                         |
| `general.email.smtpPort:`                 | SMTP 服务器使用的 SMTP 端口。                                                                                                                                                                                           |
| `general.email.smtpSsl:`                  | 您的 SMTP 服务器是否使用加密协议（`true` = SSL、`false` = TLS）。                                                                                                                                                               |
| `enableCloudCommunication:`               | 设置为 `true` 以允许您的服务器与我们的云系统进行通信。这样做可以[启用计费和许可证同步](../../self-host-an-organization.md#step-4-setup-billing-and-license-sync)。                                                                                    |
| `cloudRegion:`                            | 默认为 `US` 。如果您的组织是通过[欧盟云服务器](../../../security/server-geographies.md)启动的，请设置为 `EU` 。                                                                                                                            |
| `sharedStorageClassName:`                 | 您需要提供的共享存储类的名称，并且必须支持 [ReadWriteMany](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)（[请参阅使用 Azure 文件存储的示例](azure-aks-deployment.md#creating-a-storage-class)），除非它是单节点集群。        |
| `secrets.secretName:`                     | 您的 [Kubernetes 机密对象](https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#define-container-environment-variables-using-secret-data)的名称。您将在下一步创建此对象，因此现在确定一个名称，或者稍后再回来修改这个值。 |
| `database.enabled:`                       | 是否使用图表中包含的 SQL pod。如果使用外部 SQL 服务器，则只需设置为 `false` 。                                                                                                                                                             |
| `component.scim.enabled`                  | SCIM Pod 默认是禁用的。要启用 SCIM Pod，请设置值 `= true` 。                                                                                                                                                                   |
| `component.volume.logs.enabled:`          | 虽然不是必需的，但我们建议出于故障排除的目的将其设置为 `true` 。                                                                                                                                                                           |

### 创建机密对象 <a href="#create-a-secret-object" id="create-a-secret-object"></a>

创建一个 [Kubernetes 机密对象](https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#define-container-environment-variables-using-secret-data)，至少设置以下值：

| 值                                                                                                                                         | 描述                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `globalSettings__installation__id`                                                                                                        | 从 [https://bitwarden.com/host](https://bitwarden.com/host/) 获取到的有效安装 ID  。有关更多信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)          |
| `globalSettings__installation__key`                                                                                                       | 从 [https://bitwarden.com/host](https://bitwarden.com/host/) 获取到的有效安装密钥  。有关更多信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)           |
| `globalSettings__mail__smtp__username`                                                                                                    | 您的 SMTP 服务器的有效用户名。                                                                                                                                                                                      |
| `globalSettings__mail__smtp__password`                                                                                                    | 输入的 SMTP 服务器用户名的有效密码。                                                                                                                                                                                   |
| `globalSettings__yubico__clientId`                                                                                                        | YubiCloud 验证服务或自托管 Yubico 验证服务器的客户端 ID。如果是 YubiCloud，请在[这里](https://upgrade.yubico.com/getapikey/)获取您的客户端 ID 和密钥。                                                                                       |
| `globalSettings__yubico__key`                                                                                                             | YubiCloud 验证服务或自托管 Yubico 验证服务器的密钥。如果是 YubiCloud，请在[这里](https://upgrade.yubico.com/getapikey/)获取您的客户端 ID 和密钥。                                                                                           |
| `globalSettings__hibpApiKey`                                                                                                              | 的 HaveIBeenPwned (HIBP) API 密钥，可[在此处](https://haveibeenpwned.com/API/Key)获取。此密钥允许用户在创账户时运行[数据泄露报告](../../../your-vault/vault-health-reports.md#data-breach-report-individual-vaults-only)并检查其主密码是否存在泄露。 |
| <p>如果您使用的是 Bitwarden SQL pod，<code>SA_PASSWORD</code></p><p>如果您使用自己的 SQL 服务器，<code>globalSettings__sqlServer__connectionString</code></p> | 连接到 Bitwarden 实例的数据库的凭据。所需内容取决于您使用的是附带的 SQL pod 还是外部 SQL 服务器。                                                                                                                                           |

使用 `kubectl create secret` 命令设置这些值的示例将如下所示：

{% hint style="warning" %}
此示例将命令记录到您的 shell 历史记录中。可以考虑其他方法来安全地设置机密。
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

### 添加 rawManifest 文件 <a href="#adding-rawmanifest-files" id="adding-rawmanifest-files"></a>

## 安装图表 <a href="#install-the-chart" id="install-the-chart"></a>

## 下一步 <a href="#next-steps" id="next-steps"></a>

### 数据库备份与恢复 <a href="#database-backup-and-restore" id="database-backup-and-restore"></a>

# AWS EKS 部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/aws-eks-deployment/)
{% endhint %}

本文探讨了如何根据特定于 AWS 和弹性 Kubernetes 服务 (Elastic Kubernetes Service - EKS) 调整您的 [Bitwarden 自托管 Helm Chart 部署](self-host-with-helm.md)。

请注意，本文中记录的某些附加组件要求您的 EKS 集群至少已启动一个节点。

## 入口控制器 <a href="#ingress-controller" id="ingress-controller"></a>

默认情况下， `my-values.yaml` 中定义了一个 nginx 控制器，并且需要一个 AWS 网络负载均衡器。目前不推荐使用 AWS 应用负载均衡器 (Application Load Balancer - ALB)，因为它们不支持路径重写和基于路径的路由。

{% hint style="info" %}
以下假设您在 AWS 证书管理器中保存有一个 SSL 证书，因为您将需要证书 Amazon 资源名称 (ARN)。

您的集群中还必须至少有一个节点正在运行。
{% endhint %}

要将网络负载均衡器连接到您的集群：

1、按照[这些说明](https://docs.aws.amazon.com/eks/latest/userguide/aws-load-balancer-controller.html)创建一个 IAM 策略和角色，然后在集群中安装 AWS 负载均衡器控制器。

2、运行以下命令为您的集群设置一个入口控制器。这将创建一个 AWS 网络负载均衡器。请注意，在此示例命令中，有些值**必须**替换，以配置为满足您的需求：

```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm upgrade ingress-nginx ingress-nginx/ingress-nginx -i \
  --namespace kube-system \
  --set-string controller.service.annotations.'service\.beta\.kubernetes\.io/aws-load-balancer-backend-protocol'="ssl" \
  --set-string controller.service.annotations.'service\.beta\.kubernetes\.io/aws-load-balancer-cross-zone-load-balancing-enabled'="true" \
  --set-string controller.service.annotations.'service\.beta\.kubernetes\.io/aws-load-balancer-type'="external" \
  --set-string controller.service.annotations.'service\.beta\.kubernetes\.io/aws-load-balancer-nlb-target-type'="instance" \
  --set-string controller.service.annotations.'service\.beta\.kubernetes\.io/aws-load-balancer-scheme'="internet-facing" \
  --set-string controller.service.annotations.'service\.beta\.kubernetes\.io/aws-load-balancer-ssl-cert'="arn:aws:acm:REPLACEME:REPLACEME:certificate/REPLACEME" \ #Replace with the ARN for your certificate
  --set-string controller.service.annotations.'service\.beta\.kubernetes\.io/aws-load-balancer-ssl-ports'="443" \
  --set controller.service.externalTrafficPolicy="Local"
```

3、根据以下示例更新您的 `my-values.yaml` 文件，确保替换所有 `REPLACE` 占位符：

```bash
general:
  domain: "REPLACEME.com"
  ingress:
    enabled: true
    className: "nginx"
     ## - Annotations to add to the Ingress resource
    annotations:
      nginx.ingress.kubernetes.io/ssl-redirect: "true"
      nginx.ingress.kubernetes.io/use-regex: "true"
      nginx.ingress.kubernetes.io/rewrite-target: /$1
    ## - Labels to add to the Ingress resource
    labels: {}
    # Certificate options
    tls:
      # TLS certificate secret name
      name: # Handled via the NLB defined in the ingress controller
      # Cluster cert issuer (ex. Let's Encrypt) name if one exists
      clusterIssuer:
    paths:
      web:
        path: /(.*)
        pathType: ImplementationSpecific
      attachments:
        path: /attachments/(.*)
        pathType: ImplementationSpecific
      api:
        path: /api/(.*)
        pathType: ImplementationSpecific
      icons:
        path: /icons/(.*)
        pathType: ImplementationSpecific
      notifications:
        path: /notifications/(.*)
        pathType: ImplementationSpecific
      events:
        path: /events/(.*)
        pathType: ImplementationSpecific
      scim:
        path: /scim/(.*)
        pathType: ImplementationSpecific
      sso:
        path: /(sso/.*)
        pathType: ImplementationSpecific
      identity:
        path: /(identity/.*)
        pathType: ImplementationSpecific
      admin:
        path: /(admin/?.*)
        pathType: ImplementationSpecific
```

## 创建存储类 <a href="#create-a-storage-class" id="create-a-storage-class"></a>

部署需要您提供的共享存储类，该存储类必须支持 [ReadWriteMany](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)。以下是如何创建符合要求的存储类的示例：

{% hint style="success" %}
以下假设您已创建了一个 AWS 弹性文件系统 (Elastic File System - EFS)。如果还没有，请立即[创建一个](https://docs.aws.amazon.com/efs/latest/ug/gs-step-two-create-efs-resources.html)。无论哪种情况，请记下您的 EFS **文件系统 ID**，在此过程中您将需要用到它。
{% endhint %}

1、获取适用于您的 EKS 集群的 [Amazon EFS CSI 驱动程序插件](https://docs.aws.amazon.com/eks/latest/userguide/managing-add-ons.html#creating-an-add-on)。这将要求您为您的集群[创建一个 OIDC 提供程序](https://docs.aws.amazon.com/eks/latest/userguide/enable-iam-roles-for-service-accounts.html)，并为驱动程序[创建一个 IAM 角色](https://docs.aws.amazon.com/eks/latest/userguide/efs-csi.html#efs-create-iam-resources)。

2、在 AWS CloudShell 中，替换以下脚本中的 `file_system_id= "REPLACE"` 变量并在 AWS CloudShell 中运行它：

{% hint style="warning" %}
以下只是一个说明性示例，请务必根据您自己的安全需求分配权限。
{% endhint %}

```bash
file_system_id="REPLACE"

cat << EOF | kubectl apply -n bitwarden -f -
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: shared-storage
provisioner: efs.csi.aws.com
parameters:
  provisioningMode: efs-ap
  fileSystemId: $file_system_id
  directoryPerms: "777" # Change for your use case
  uid: "2000" # Change for your use case
  gid: "2000" # Change for your use case
  basePath: "/dyn1"
  subPathPattern: "\${.PVC.name}"
  ensureUniqueDirectory: "false"
  reuseAccessPoint: "false"
mountOptions:
  - iam
  - tls
EOF
```

3、将 `my-values.yaml` 中的 `sharedStorageClassName` 的值设置为您在 `metadata.name:` 中指定的类的名称，例如：

```bash
sharedStorageClassName: "shared-storage"
```

## 使用 AWS Secrets Manager <a href="#using-aws-secrets-manager" id="using-aws-secrets-manager"></a>

部署需要使用 Kubernetes secrets 对象来设置敏感值。虽然可以使用 `kubectl create secret` 命令来设置 secrets，但 AWS 客户可能倾向于使用 AWS Secrets Manager 和适用于 Kubernetes Secrets Store CSI 驱动程序的 AWS Secrets 和 Configuration Provider (ACSP)。

您需要将以下机密存储在 AWS Secrets Manager 中。请注意，您可以更改此处使用的**密钥**，但如果您这样做，还必须对后续步骤进行更改：

| 密钥                                                                                                                 | 值                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `installationid`                                                                                                   | 从 [https://bitwarden.com/host](https://bitwarden.com/host/) 获取到的有效安装 ID  。有关更多信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)           |
| `installationkey`                                                                                                  | 从 [https://bitwarden.com/host](https://bitwarden.com/host/) 获取到的有效安装密钥 。有关更多信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)             |
| `smtpusername`                                                                                                     | 您的 SMTP 服务器的有效用户名。                                                                                                                                                                                       |
| `smtppassword`                                                                                                     | 输入的 SMTP 服务器用户名的有效密码。                                                                                                                                                                                    |
| `yubicoclientid`                                                                                                   | YubiCloud 验证服务或自托管 Yubico 验证服务器的客户端 ID。如果使用 YubiCloud，请[在此处](https://upgrade.yubico.com/getapikey/)获取您的客户端 ID 和密钥 。                                                                                      |
| `yubicokey`                                                                                                        | YubiCloud 验证服务或自托管 Yubico 验证服务器的机密密钥。如果使用 YubiCloud，请[在此处](https://upgrade.yubico.com/getapikey/)获取您的客户端 ID 和密钥 。                                                                                        |
| globalSettings\_\_hibpApiKey                                                                                       | 您的 HaveIBeenPwned (HIBP) API 密钥，可[在此处](https://haveibeenpwned.com/API/Key)获取。此密钥允许用户在创账户时运行[数据泄露报告](../../../your-vault/vault-health-reports.md#data-breach-report-individual-vaults-only)并检查其主密码是否存在泄露。 |
| <p>如果您使用 Bitwarden SQL pod  <code>sapassword</code>，.</p><p>如果您使用自己的 SQL 服务器， <code>dbconnectionString.</code></p> | 连接到 Bitwarden 实例的数据库的凭据。所需内容取决于您使用的是附带的 SQL pod 还是外部 SQL 服务器。                                                                                                                                            |

1、安全存储您的机密后，[安装 ACSP](https://docs.aws.amazon.com/secretsmanager/latest/userguide/integrating\_csi\_driver.html#integrating\_csi\_driver\_install)。

2、创建权限策略以允许访问您的机密。该策略**必须**授予 `secretsmanager:GetSecretValue` 和 `secretsmanager:DescribeSecret` 权限，例如：

```bash
{
   "Version": "2012-10-17",
   "Statement": {
     "Effect": "Allow",
     "Action": [
       "secretsmanager:DescribeSecret",
       "secretsmanager:GetSecretValue"
     ],
     "Resource": "arn:aws:secretsmanager:REPLACEME:REPLACEME:secret:REPLACEME"
   }
}
```

3、创建一个可以通过已创建的权限策略访问您的机密的服务账户，例如：

```bash
CLUSTER_NAME="REPLACE"
ACCOUNT_ID="REPLACE" # replace with your AWS account ID
ROLE_NAME="REPLACE" # name of a role that will be created in IAM
POLICY_NAME="REPLACE" # the name of the policy you created earlier
eksctl create iamserviceaccount \
  --cluster=$CLUSTER_NAME \
  --namespace=bitwarden \
  --name=bitwarden-sa \
  --role-name $ROLE_NAME \
  --attach-policy-arn=arn:aws:iam::$ACCOUNT_ID:policy/$POLICY_NAME \
  --approve
```

4、接下来，创建 SecretProviderClass，如以下示例所示。请务必将 `region` 替换为您所在的区域，并将`objectName` 替换为您创建的 Secrets Manager 机密的名称（**步骤 1**）：

```bash
cat <<EOF | kubectl apply -n bitwarden -f -
apiVersion: secrets-store.csi.x-k8s.io/v1
kind: SecretProviderClass
metadata:
  name: bitwarden-secrets-manager-csi
  labels:
    app.kubernetes.io/component: secrets
  annotations:
spec:
  provider: aws
  parameters:
    region: REPLACE
    objects: |
      - objectName: "REPLACE"
        objectType: "secretsmanager"
        objectVersionLabel: "AWSCURRENT"
        jmesPath:
          - path: installationid
            objectAlias: installationid
          - path: installationkey
            objectAlias: installationkey
          - path: smtpusername
            objectAlias: smtpusername
          - path: smtppassword
            objectAlias: smtppassword
          - path: yubicoclientid
            objectAlias: yubicoclientid
          - path: yubicokey
            objectAlias: yubicokey
          - path: hibpapikey
             objectAlias: hibpapikey
          - path: sapassword #-OR- dbconnectionstring if external SQL
            objectAlias: sapassword #-OR- dbconnectionstring if external SQL
  secretObjects:
  - secretName: "bitwarden-secret"
    type: Opaque
    data:
    - objectName: installationid
       key: globalSettings__installation__id
    - objectName: installationkey
       key: globalSettings__installation__key
    - objectName: smtpusername
       key: globalSettings__mail__smtp__username
    - objectName: smtppassword
       key: globalSettings__mail__smtp__password
    - objectName: yubicoclientid
       key: globalSettings__yubico__clientId
    - objectName: yubicokey
       key: globalSettings__yubico__key
    - objectName: hibpapikey
       key: globalSettings__hibpApiKey
    - objectName: sapassword #-OR- dbconnectionstring if external SQL
       key: SA_PASSWORD #-OR- globalSettings__sqlServer__connectionString if external SQL
EOF
```

5、在您的 `my-values.yaml` 文件中，设置以下值：

* `secrets.secretName` ：设置为 SecretProviderClass 中定义的 `secretName` （步骤 3）。
* `secrets.secretProviderClass` ：设置为 SecretProviderClass 中定义的 `metedata.name` （第 3 步）。
* `component.admin.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.api.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.attachments.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.events.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.icons.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.identity.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.notifications.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.scim.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.sso.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `component.web.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `database.podServiceAccount` ：设置为为您的服务账户定义的名称（步骤 2）。
* `serviceAccount.name` ：设置为为您的服务账户定义的名称（步骤 2）。
* `serviceAccount.deployRolesOnly` ：设置为 `true` 。

# Azure AKS 部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/azure-aks-deployment/)
{% endhint %}

本文将指导您完成使用 Azure 和 AKS 的特定功能来修改您的 [Bitwarden 自托管 Helm Chart 部署](self-host-with-helm.md)。

## 入口控制器 <a href="#ingress-controllers" id="ingress-controllers"></a>

### nginx <a href="#nginx" id="nginx"></a>

默认情况下在 `my-values.yaml` 中定义了一个 nginx 入口控制器。如果您使用这个选项：

1. 创建一个基本的 nginx 入口控制器。
2. 在 `general.ingress.annotations:` 部分取消注释数值，并根据需要进行自定义。

### Azure 应用程序网关 <a href="#azure-application-gateway" id="azure-application-gateway"></a>

Azure 客户可能更倾向于使用 Azure 应用程序网关作为他们 AKS 集群的入口控制器。

#### 安装图表前 <a href="#before-installing-the-chart" id="before-installing-the-chart"></a>

如果您喜欢这个选项，在[安装图表](self-host-with-helm.md#install-the-chart)**之前**，您必须：

1、[为您的群集启用 Azure 应用程序网关入口控制器](https://learn.microsoft.com/en-us/azure/application-gateway/tutorial-ingress-controller-add-on-existing)。

2、更新您的 my-values.yaml 文件，特别是 `general.ingress.className:` ， `general.ingress.annotations:` 和 `general.ingress.paths:` ：

```bash
general:
  domain: "replaceme.com"
  ingress:
    enabled: true
    className: "azure-application-gateway" # This value might be different depending on how you created your ingress controller.  Use "kubectl get ingressclasses -A" to find the name if unsure.
     ## - Annotations to add to the Ingress resource.
    annotations:
      appgw.ingress.kubernetes.io/ssl-redirect: "true"
      appgw.ingress.kubernetes.io/use-private-ip: "false" # This might be true depending on your setup.
      appgw.ingress.kubernetes.io/rewrite-rule-set: "bitwarden-ingress" # Make note of whatever you set this value to.  It will be used later.
      appgw.ingress.kubernetes.io/connection-draining: "true" # Update as necessary.
      appgw.ingress.kubernetes.io/connection-draining-timeout: "30" # Update as necessary.
    ## - Labels to add to the Ingress resource.
    labels: {}
    # Certificate options.
    tls:
      # TLS certificate secret name.
      name: tls-secret
      # Cluster cert issuer (e.g. Let's Encrypt) name if one exists.
      clusterIssuer: letsencrypt-staging
    paths:
      web:
        path: /*
        pathType: ImplementationSpecific
      attachments:
        path: /attachments/*
        pathType: ImplementationSpecific
      api:
        path: /api/*
        pathType: ImplementationSpecific
      icons:
        path: /icons/*
        pathType: ImplementationSpecific
      notifications:
        path: /notifications/*
        pathType: ImplementationSpecific
      events:
        path: /events/*
        pathType: ImplementationSpecific
      scim:
         path: /scim/*
         pathType: ImplementationSpecific
      sso:
        path: /sso/*
        pathType: ImplementationSpecific
      identity:
        path: /identity/*
        pathType: ImplementationSpecific
      admin:
        path: /admin*
        pathType: ImplementationSpecific
```

3、如果您要使用提供的 Let's Encrypt 示例来生成 TLS 证书，请将[此处链接](self-host-with-helm.md#example-certificate-setup)的脚本中的 `spec.acme.solvers.ingress.class:` 的值更新为 `"azure/application-gateway"` 。

4、在 Azure 门户中为应用程序网关创建一个空的重写集：

1. 转到 Azure 门户中的**负载均衡** → **应用程序网关**，选择您的应用程序网关。
2. 选择**重写**选项卡。
3. 选择**重写集**按钮。
4. 在此示例中，将名称设置为 `my-values.yaml` 中 `appgw.ingress.kubernetes.io/rewrite-rule-set:` 指定的值，即 `bitwarden-ingress` 。
5. 选择**下一步**然后选择**创建**。

#### 安装图表后 <a href="#after-installing-the-chart" id="after-installing-the-chart"></a>

[安装图表](self-host-with-helm.md#install-the-chart)**之后**，您还需要为重写集创建规则：

1、重新打开您在安装图表之前创建的空重写集。

2、选择所有以 `pr-bitwarden-self-host-ingress...` 开头的路由路径，取消选择任何不以该前缀开头的路径，然后选择**下一步**。

3、选择**添加重写规则**按钮。您可以为重写规则指定任何名称和任何顺序。

4、添加以下条件：

* **要检查的变量类型**：服务器变量
* **服务器变量**：uri\_path
* **区分大小写**：否
* **操作符**：等于 (=)
* **Pattern to match**：`^(\/(?!admin)(?!identity)(?!sso)[^\/]*)\/(.*)`

5、添加以下操作：

* **重写类型**：URL
* **操作类型**：设置
* **组件**：URL 路径
* **URL 路径值**： `/{var_uri_path_2}`
* **重新评估路径图**：未选中

6、选择**创建**。

## 创建存储类 <a href="#creating-a-storage-class" id="creating-a-storage-class"></a>

部署需要使用您提供的支持 [ReadWriteMany](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes) 的共享存储类。以下示例是一个可以在 Azure Cloud Shell 中运行的脚本，用于创建满足要求的 Azure 文件存储类。

{% hint style="warning" %}
以下是一个说明性的示例，请根据您自己的安全要求分配权限。
{% endhint %}

```bash
cat <<EOF | kubectl apply -n bitwarden -f -
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: azure-file
  namespace: bitwarden
provisioner: file.csi.azure.com
allowVolumeExpansion: true
mountOptions:
  - dir_mode=0777
  - file_mode=0777
  - uid=0
  - gid=0
  - mfsymlinks
  - cache=strict
  - actimeo=30
parameters:
  skuName: Standard_LRS
EOF
```

您必须在 `my-values.yaml` 中设置 `sharedStorageClassName` 的值，值应与您给予类的名称相同，在本例中为：

```bash
sharedStorageClassName: "azure-file"
```

## 使用 Azure Key Vault CSI 驱动程序 <a href="#using-azure-key-vault-csi-driver" id="using-azure-key-vault-csi-driver"></a>

部署需要使用 Kubernetes secrets 对象为您的部署设置敏感值。虽然 `kubectl create secret` 命令可用于设置机密，但 Azure 客户可能更倾向于使用 Azure Key Vault 和 AKS Secrets Store CSI Driver。

{% hint style="success" %}
这些说明假设您已经设置了 Azure Key Vault。如果没有，请[立即创建一个](https://learn.microsoft.com/en-us/azure/aks/csi-secrets-store-driver#create-or-use-an-existing-azure-key-vault)。
{% endhint %}

1、使用以下命令为您的集群添加 Secrets Store CSI Driver 支持：

```bash
az aks enable-addons --addons azure-keyvault-secrets-provider --name myAKSCluster --resource-group myResourceGroup
```

该插件创建了一个用户分配的托管身份，您可以用它来进行密钥库的身份验证，然而您还有其他选择来进行身份访问控制。如果您使用已创建的用户分配的托管身份，您需要显式地为其分配 **Secret** > **Get** 的访问权限（[点击这里了解](https://learn.microsoft.com/en-us/azure/key-vault/general/assign-access-policy?tabs=azure-portal)）。

2、创建一个 SecretProviderClass，就像以下示例中所示。请注意，这个示例包含了必须替换的 `<REPLACE>` 占位符，其取决于您使用的是附带的 SQL pod 还是使用您自己的 SQL 服务器。

```bash
cat <<EOF | kubectl apply -n bitwarden -f -
apiVersion: secrets-store.csi.x-k8s.io/v1
kind: SecretProviderClass
metadata:
  name: bitwarden-azure-keyvault-csi
  labels:
    app.kubernetes.io/component: secrets
  annotations:
spec:
  provider: azure
  parameters:
    useVMManagedIdentity: "true" # Set to false for workload identity
    userAssignedIdentityID: "<REPLACE>" # Set the clientID of the user-assigned managed identity to use
    # clientID: "<REPLACE>" # Setting this to use workload identity
    keyvaultName: "<REPLACE>"
    cloudName: "AzurePublicCloud"
    objects: |
      array:
        - |
          objectName: installationid
          objectAlias: installationid
          objectType: secret
          objectVersion: ""
        - |
          objectName: installationkey
          objectAlias: installationkey
          objectType: secret
          objectVersion: ""
        - |
          objectName: smtpusername
          objectAlias: smtpusername
          objectType: secret
          objectVersion: ""
        - |
          objectName: smtppassword
          objectAlias: smtppassword
          objectType: secret
          objectVersion: ""
        - |
          objectName: yubicoclientid
          objectAlias: yubicoclientid
          objectType: secret
          objectVersion: ""
        - |          
          objectName: yubicokey
          objectAlias: yubicokey
          objectType: secret
          objectVersion: ""
        - |
          objectName: hibpapikey
          objectAlias: hibpapikay
          objectType: secret
          objectVersion: ""
        - |          
          objectName: sapassword #-OR- dbconnectionstring if external SQL
          objectAlias: sapassword #-OR- dbconnectionstring if external SQL
          objectType: secret
          objectVersion: ""
    tenantId: "<REPLACE>"
  secretObjects:
  - secretName: "bitwarden-secret"
    type: Opaque
    data:
    - objectName: installationid
      key: globalSettings__installation__id
    - objectName: installationkey
      key: globalSettings__installation__key
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

3、使用下列命令在密钥库中设置所需的机密值：

{% hint style="warning" %}
此示例将命令记录到您的 shell 历史记录中。可以考虑使用其他方法来安全地设置机密。
{% endhint %}

```bash
kvname=<REPLACE>
az keyvault secret set --name installationid --vault-name $kvname --value <REPLACE>
az keyvault secret set --name installationkey --vault-name $kvname --value <REPLACE>
az keyvault secret set --name smtpusername --vault-name $kvname --value <REPLACE>
az keyvault secret set --name smtppassword --vault-name $kvname --value <REPLACE>
az keyvault secret set --name yubicoclientid --vault-name $kvname --value <REPLACE>
az keyvault secret set --name yubicokey --vault-name $kvname --value <REPLACE>
az keyvault secret set --name hibpapikey --vault-name $kvname --value <REPLACE>
az keyvault secret set --name sapassword --vault-name $kvname --value <REPLACE>
# - OR -
# az keyvault secret set --name dbconnectionstring --vault-name $kvname --value <REPLACE>
```

4、在您的 `my-values.yaml` 文件中，设置以下值：

* `secrets.secretName` ：将此值设置为 SecretProviderClass 中定义的 `secretName` 值。
* `secrets.secretProviderClass` ：将此值设置为 SecretProviderClass 中定义的 `metadata.name` 值。

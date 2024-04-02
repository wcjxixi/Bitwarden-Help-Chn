# OpenShift 部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/openshift-deployment/)
{% endhint %}

本文探讨了如何根据 OpenShift 特定功能调整您的 [Bitwarden 自托管 Helm Chart 部署](self-host-with-helm.md)。

## OpenShift 路由 <a href="#openshift-routes" id="openshift-routes"></a>

这个示例将演示 [OpenShift 路由](https://docs.openshift.com/container-platform/3.11/architecture/networking/routes.html#overview)而不是默认的入口控制器。

### 禁用默认入口 <a href="#disable-default-ingress" id="disable-default-ingress"></a>

1、访问 `my-values.yaml` 。

2、通过指定 `ingress.enabled: false` 禁用默认的入口

```bash
general:
  domain: "replaceme.com"
  ingress:
    enabled: false
```

剩下的入口值不需要做修改，因为设置 `ingress.enabled: false` 后将提示图表忽略它们。

### 添加路由的 raw manifest <a href="#add-raw-manifest-for-routes" id="add-raw-manifest-for-routes"></a>

在 `my-values.yaml` 中找到 `rawManifests` 部分。这部分是指定 OpenShift Route 清单的地方。

可以 **⬇️**下载一个使用 OpenShift 路由的 `rawManifests` 部分的示例文件。

{% hint style="info" %}
在上面提供的示例中， `destinationCACertificate` 被设置为空字符串。这将使用 OpenShift 中的默认证书设置。也可以在此处指定证书名称，或者按照[该指南](https://developer.ibm.com/tutorials/secure-red-hat-openshift-routes-with-lets-encrypt/)使用 Let's Encrypt。如果这样做，您将需要为每个路由的注释中添加 `kubernetes.io/tls-acme: "true"` 。
{% endhint %}

## 共享存储类 <a href="#shared-storage-class" id="shared-storage-class"></a>

大多数 OpenShift 部署都需要一个共享的存储类。必须启用 `ReadWriteMany` 存储。这可以通过您选择的方法来完成，其中一个选项是使用 [NFS Subdir 外部预配程序](https://github.com/kubernetes-sigs/nfs-subdir-external-provisioner/blob/master/charts/nfs-subdir-external-provisioner/README.md)。

## 机密 <a href="#secrets" id="secrets"></a>

可以使用 `oc` 命令来部署机密。有效的安装 ID 和密钥可以从 [bitwarden.com/host/](https://bitwarden.com/host/) 获取。有关更多信息，请参阅[我的安装 ID 和安装密钥是用来干什么的？](../../hosting-faqs.md#q-what-are-my-installation-id-and-installation-key-used-for)

以下命令是一个示例：

{% hint style="danger" %}
这个示例会记录命令到你的 shell 历史记录中。其他方法可能被考虑用来安全地设置一个机密。
{% endhint %}

```bash
oc create secret generic custom-secret -n bitwarden \
    --from-literal=globalSettings__installation__id="REPLACE" \
    --from-literal=globalSettings__installation__key="REPLACE" \
    --from-literal=globalSettings__mail__smtp__username="REPLACE" \
    --from-literal=globalSettings__mail__smtp__password="REPLACE" \
    --from-literal=globalSettings__yubico__clientId="REPLACE" \
    --from-literal=globalSettings__yubico__key="REPLACE" \
    --from-literal=globalSettings__hibpApiKey="REPLACE" \
    --from-literal=SA_PASSWORD="REPLACE" # If using SQL pod 
    # --from-literal=globalSettings__sqlServer__connectionString="REPLACE" # If using your own SQL server
```

## 创建服务账户 <a href="#create-a-service-account" id="create-a-service-account"></a>

OpenShift 中需要一个服务账户，因为每个容器都需要在启动时运行提升的命令。这些命令被 OpenShift 的受限 SCC 所阻止。我们需要创建一个服务账户并将其分配给 `anyuid` SCC。

1、请使用 `oc` 命令行工具运行以下命令：

```bash
oc create sa bitwarden-sa
oc adm policy add-scc-to-user anyuid -z bitwarden-sa
```

2、接下来，更新 `my-values.yaml` 以使用新的服务账户。将以下键设置为上一步创建的服务账户 `bitwarden-sa` 的名称：

```bash
component.admin.podServiceAccount
component.api.podServiceAccount
component.attachments.podServiceAccount
component.events.podServiceAccount
component.icons.podServiceAccount
component.identity.podServiceAccount
component.notifications.podServiceAccount
component.scim.podServiceAccount
component.sso.podServiceAccount
component.web.podServiceAccount
database.podServiceAccount
```

这是在 `my-values.yaml` 文件中的一个例子：

```bash
component:
  # The Admin component
  admin:
    # Additional deployment labels
    labels: {}
    # Image name, tag, and pull policy
    image:
      name: bitwarden/admin
    resources:
      requests:
        memory: "64Mi"
        cpu: "50m"
      limits:
        memory: "128Mi"
        cpu: "100m"
    securityContext:
    podServiceAccount: bitwarden-sa
```

{% hint style="info" %}
您可以创建自己的 SCC 来微调这些 Pod 的安全性。[在 OpenShift 中管理 SCC](https://cloud.redhat.com/blog/managing-sccs-in-openshift) 描述了开箱即用的 SSC，以及如何根据需要创建自己的 SSC。
{% endhint %}

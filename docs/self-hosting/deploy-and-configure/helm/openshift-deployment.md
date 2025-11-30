# OpenShift 部署

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/openshift-deployment/)
{% endhint %}

本文探讨了如何根据 OpenShift 特定功能调整您的 [Bitwarden 自托管 Helm Chart 部署](self-host-with-helm.md)。

## 要求 <a href="#requirements" id="requirements"></a>

在继续安装之前，请确保满足以下要求：

* 已安装 [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)。
* 已安装 [Helm 3](https://helm.sh/docs/intro/install/)。
* 您拥有 SSL 证书和密钥，或者可以通过证书提供商创建 SSL 证书和密钥。
* 您拥有 SMTP 服务器或可以访问云 SMTP 提供商。
* 一个支持 ReadWriteMany 的[存储类](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)。
* 您有一个从 [https://bitwarden.com/host](https://bitwarden.com/host) 获取到的安装 ID 和密钥。

### 无根模式要求 <a href="#rootless-requirements" id="rootless-requirements"></a>

Bitwarden 会在启动时检测您的环境是否限制了用户容器的运行身份，并在检测到限制时自动以无根模式启动部署。要成功以无根模式部署，需满足以下两个选项之一：

* 部署外部 MSSQL 数据库，而不是 Helm 图表中默认包含的 SQL 容器。
* 使用服务账户、pod 安全上下文或其他方法为包含的 SQL 容器分配高级权限。

{% hint style="info" %}
虽然 Microsoft 要求 SQL 容器必须以 root 身份运行，但在执行应用程序代码之前，容器启动将逐步降级至非 root 用户。
{% endhint %}

## OpenShift 路由 <a href="#openshift-routes" id="openshift-routes"></a>

这个示例将演示 [OpenShift 路由](https://docs.openshift.com/container-platform/3.11/architecture/networking/routes.html#overview)而不是默认的入口控制器。

### 禁用默认入口 <a href="#disable-default-ingress" id="disable-default-ingress"></a>

1、访问 `my-values.yaml` 。

2、通过指定 `ingress.enabled: false` 禁用默认的入口

```yml
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
此示例将命令记录到您的 shell 历史记录中。可以考虑使用其他方法来安全地设置机密。
{% endhint %}

```yml
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

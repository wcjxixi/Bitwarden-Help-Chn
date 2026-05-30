# 流量路由

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/traffic-routing/)
{% endhint %}

{% hint style="info" %}
NGINX Ingress 已达到 EOL，不再提供支持。Bitwarden 已在 `my-values.yaml` 中添加了 Gateway API 的配置。请参阅 Kubernetes 关于 NGINX Ingress 弃用的[官方声明](https://kubernetes.io/blog/2026/01/29/ingress-nginx-statement/)。
{% endhint %}

> **\[译者注]**：EOL - End of Life，生命周期。在软件领域，它表示某个软件版本或产品已经停止维护和支持。
>
> 当一个软件进入 EOL 状态后，一般将：
>
> * 不再发布新功能
> * 不再修复漏洞
> * 不再提供技术支持
> * 继续使用会有安全风险

本文提供了基于 Kubernetes 的 Bitwarden 部署的流量路由配置示例，且应与 [Helm 自托管](self-host-with-helm.md)配合使用。本文涵盖了标准的 Gateway API 设置，以及需要执行的迁移步骤，如果您正在运行已弃用的 NGINX Ingress 配置。

## 先决条件 <a href="#prerequisites" id="prerequisites"></a>

在进行 Gateway API 设置之前，请确保已在 [Helm 自托管](self-host-with-helm.md)中完成以下要求和初始设置：

* [创建了 Bitwarden 命名空间](self-host-with-helm.md#create-a-namespace)
* [创建了机密](self-host-with-helm.md#create-a-secret-object)
* [创建并安装了证书](self-host-with-helm.md#example-certificate-setup)

## NGINX Gateway Fabric <a href="#nginx-gateway-fabric" id="nginx-gateway-fabric"></a>

以下各章节包含从 NGINX Ingress [设置](traffic-routing.md#install-the-gateway-api-custom-resource-definition)或[迁移](traffic-routing.md#migrating-from-nginx-ingress-to-gateway-api)到 NGINX Gateway Fabric 的说明。请按照以下步骤为您的 Bitwarden Helm 部署配置 Gateway API：

* **新部署**：请按顺序执行以下步骤。
* **从 NGINX Ingress 迁移：**&#x5B8C;成创建 Gateway 资源之前的步骤，然后跳转至[从 NGINX Ingress 迁移](traffic-routing.md#migrating-from-nginx-ingress-to-gateway-api)到 [NGINX Gateway Fabric](traffic-routing.md#nginx-gateway-fabric)。

### 安装 Gateway API 自定义资源定义 <a href="#install-the-gateway-api-custom-resource-definition" id="install-the-gateway-api-custom-resource-definition"></a>

在部署 Gateway Controller 之前，请先安装 Gateway API 自定义资源定义。以下示例使用 NGINX Gateway Fabric v2.4.2：

```shellscript
kubectl kustomize "https://github.com/nginx/nginx-gateway-fabric/config/crd/gateway-api/standard?ref=v2.4.2" | kubectl apply -f -
```

{% hint style="info" %}
CRD 版本与 Gateway Controller 版本是绑定的。运行此命令前，请查阅 Controller 文档以确认兼容的 CRD 版本。在本示例中，CRD 版本与 NGINX Gateway Fabric 绑定。
{% endhint %}

> **\[译者注]**：CRD - Custom Resource Definition，自定义资源定义。

更多实施选项请参阅 Gateway API 文档。

### 安装 Gateway Controller <a href="#install-a-gateway-controller" id="install-a-gateway-controller"></a>

Gateway Controller 负责处理流量路由。要使用 Helm 安装 NGINX Gateway Fabric，请执行：

```shellscript
helm install ngf oci://ghcr.io/nginx/charts/nginx-gateway-fabric \
  --create-namespace \
  -n nginx-gateway \
  --set nginx.service.type=LoadBalancer
```

### 创建 Gateway 资源 <a href="#create-the-gateway-resource" id="create-the-gateway-resource"></a>

在 `bitwarden` 命名空间中创建一个 `Gateway` 资源。该 Gateway 使用在[先决条件设置](self-host-with-helm.md)期间创建的 `self-signed-cert` 机密来终止 TLS，并将附加路由限制在同一命名空间内。

```yaml
apiVersion: gateway.networking.k8s.io/v1
kind: Gateway
metadata:
  name: bw-gateway
  namespace: bitwarden
spec:
  # Change this if your controller uses a different GatewayClass.
  # For example, many environments will NOT use "nginx" here.
  gatewayClassName: nginx
  listeners:
    - name: http
      hostname: bw.localtest.me       # change this value
      port: 80
      protocol: HTTP
      allowedRoutes:
        namespaces:
          from: Same
    - name: https
      hostname: bw.localtest.me    # change this value
      port: 443
      protocol: HTTPS
      tls:
        mode: Terminate
        certificateRefs:
          - kind: Secret
            name: self-signed-cert
      allowedRoutes:
        namespaces:
          from: Same
```

如果您的设置需要将 HTTP 重定向到 HTTPS，您可以使用以下附加路由来指向 `redirect.yaml` 文件：

将 HTTP 应用于 HTTPS：

应用清单：

```shellscript
kubectl apply -f gateway.yaml
```

要列出 Controller 安装的 `GatewayClass` 资源，请运行：

上述 `gatewayClassName` 值必须与以下值之一匹配。

{% hint style="info" %}
此时，如果您要从 NGINX Ingress 设置迁移，请继续执行从 NGINX Ingress 迁移到 Gateway API 的操作。
{% endhint %}

### 为 Gateway API 配置 Helm Chart <a href="#configure-the-helm-chart-for-gateway-api" id="configure-the-helm-chart-for-gateway-api"></a>

更新 `my-values.yaml` 文件以禁用已弃用的 Ingress，并启用 Gateway API HTTPRoute。设置 `parentRefs` 指向 Gateway：

```yaml
general:
  ingress:
    # Ingress is deprecated. Disable it when using Gateway API.
    enabled: false
  gateway:
    # Set to true to create an HTTPRoute resource managed by the Helm chart.
    enabled: true
    # parentRefs attach the HTTPRoute to the Gateway.
    parentRefs:
      - name: bw-gateway        # Must match the Gateway metadata.name
        namespace: bitwarden    # Must match the Gateway metadata.namespace
        sectionName: https      # Must match the listener name in the Gateway spec
```

应用更改：

```shellscript
helm upgrade bitwarden bitwarden/self-host \
  --install \
  --namespace bitwarden \
  --values my-values.yaml
```

{% hint style="info" %}
提供的 `my-values.yaml` 文件包含了 Ingress 和 Gateway API 的配置信息。您可以根据具体的架构需求同时使用这两种方法。
{% endhint %}

### HTTPRoute 功能 <a href="#httproute-functionality" id="httproute-functionality"></a>

当 `general.gateway.enabled` 为 `true` 时，Helm Chart 会在 `bitwarden` 命名空间中创建一个 `HTTPRoute` 资源。该 `HTTPRoute` 会附加到 `parentRefs` 中定义的 Gateway，并根据路径前缀将流量路由到各个 Bitwarden 服务。您可以[在此处](https://bitwarden.com/assets/2BFMWDWYdIOkE0AwvxN5Jr/357fdcbfcdbde5fe76c6a02659c5e10b/HTTPRoute.yaml)查看配置生成的 HTTPRoute Chart。

{% hint style="info" %}
TLS 在 Gateway 层进行处理，而不是在 HTTPRoute 层。请勿向 HTTPRoute 资源添加 TLS 配置。
{% endhint %}

## 从 NGINX Ingress 迁移到 Gateway API <a href="#migrating-from-nginx-ingress-to-gateway-api" id="migrating-from-nginx-ingress-to-gateway-api"></a>

如果您拥有使用已弃用的 `general.ingress` 配置的 Bitwarden Helm 部署，则可以迁移到 Gateway API。如果您尚未完成上述步骤中的[安装 NGINX Gateway Fabric](traffic-routing.md#install-a-gateway-controller) 和[创建 Gateway 资源](traffic-routing.md#create-the-gateway-resource)操作，请先完成这些操作，然后再返回本章节。

1、接下来，更新您的 values 文件以禁用 Ingress 并启用 Gateway：

```yaml
general:
  ingress:
    enabled: false
  gateway:
    enabled: true
    parentRefs:
      - name: bw-gateway
        namespace: bitwarden
        sectionName: https
```

2、应用更改：

```shellscript
helm upgrade bitwarden bitwarden/self-host \
  --namespace bitwarden \
  --values my-values.yaml
```

该图表将删除旧的 `Ingress` 资源，并在其位置创建 `HTTPRoute` 。

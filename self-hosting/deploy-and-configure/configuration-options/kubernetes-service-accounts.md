# Kubernetes 服务账户

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/kubernetes-service-accounts/)
{% endhint %}

Kubernetes 服务账户可用于将特定的安全环境应用于特定的 pod。例如，在您需要以无根模式运行 BitWarden 服务器的情况下，这就非常有用，因为其中包含的 SQL 容器需要提升权限。

创建并配置了具有所需权限的服务账户后，请更改 `my-values.yaml` 文件中的任何 pod 服务账户名称（例如，`database.podServiceAccount`）。例如，将 `component.admin.podServiceAccount` 指定为 `bitwarden-sa` 服务账户的 `my-values.yaml` 文件应如下所示：

```bash
component:
  # The Admin component
  admin:
    # Additional deployment labels
    labels: {}
    # Image name, tag, and pull policy
    image:
      name: ghcr.io/bitwarden/admin
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

符合服务账户指定资格的 pod 包括：

* `component.admin.podServiceAccount`
* `component.api.podServiceAccount`
* `component.attachments.podServiceAccount`
* `component.events.podServiceAccount`
* `component.icons.podServiceAccount`
* `component.identity.podServiceAccount`
* `component.notifications.podServiceAccount`
* `component.scim.podServiceAccount`
* `component.sso.podServiceAccount`
* `component.web.podServiceAccount`
* `database.podServiceAccount`

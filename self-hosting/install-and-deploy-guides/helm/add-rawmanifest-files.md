# 添加 rawManifest 文件

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/add-rawmanifest-files/)
{% endhint %}

Bitwarden 自托管 Helm Chart 允许您在安装之前或安装之后包含其他 Kubernetes 清单文件。为此，请更新图表中的 `rawManifests` 部分。

## Traefik IngressRoute 示例 <a href="#traefik-ingressroute-example" id="traefik-ingressroute-example"></a>

例如，要安装 Traefik 的 IngressRoute 作为 Kubernetes 的 Ingress 控制器的替代，请添加以下内容：

{% hint style="info" %}
在此示例中，您还需要在您的 `my-values.yaml` 文件中的 `general.ingress.enabled` 处禁用入口控制器。
{% endhint %}

```bash
rawManifests:
  preInstall: []
  postInstall:
  - apiVersion: traefik.containo.us/v1alpha1
    kind: Middleware
    metadata:
      name: "bitwarden-self-host-middleware-stripprefix"
    spec:
      stripPrefix:
        prefixes:
          - /api
          - /attachements
          - /icons
          - /notifications
          - /events
          - /scim
          ##### NOTE:  Admin, Identity, and SSO will not function correctly with path strip middleware
  - apiVersion: traefik.containo.us/v1alpha1
    kind: IngressRoute
    metadata:
      name: "bitwarden-self-host-ingress"
    spec:
      entryPoints:
        - websecure
      routes:
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/`)
          services:
            - kind: Service
              name: bitwarden-self-host-web
              passHostHeader: true
              port: 5000
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/api/`)
          services:
            - kind: Service
              name: bitwarden-self-host-api
              port: 5000
          middlewares:
            - name: "bitwarden-self-host-middleware-stripprefix"
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/attachments/`)
          services:
            - kind: Service
              name: bitwarden-self-host-api
              port: 5000
          middlewares:
            - name: "bitwarden-self-host-middleware-stripprefix"
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/icons/`)
          services:
            - kind: Service
              name: bitwarden-self-host-icons
              port: 5000
          middlewares:
            - name: "bitwarden-self-host-middleware-stripprefix"
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/notifications/`)
          services:
            - kind: Service
              name: bitwarden-self-host-notifications
              port: 5000
          middlewares:
            - name: "bitwarden-self-host-middleware-stripprefix"
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/events/`)
          services:
            - kind: Service
              name: bitwarden-self-host-events
              port: 5000
          middlewares:
            - name: "bitwarden-self-host-middleware-stripprefix"
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/scim/`)
          services:
            - kind: Service
              name: bitwarden-self-host-scim
              port: 5000
          middlewares:
            - name: "bitwarden-self-host-middleware-stripprefix"
        ##### NOTE:  SSO will not function correctly with path strip middleware
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/sso/`)
          services:
            - kind: Service
              name: bitwarden-self-host-sso
              port: 5000
        ##### NOTE:  Identity will not function correctly with path strip middleware
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/identity/`)
          services:
            - kind: Service
              name: bitwarden-self-host-identity
              port: 5000
        ##### NOTE:  Admin will not function correctly with path strip middleware
        - kind: Rule
          match: Host(`REPLACEME.COM`) && PathPrefix(`/admin`)
          services:
            - kind: Service
              name: bitwarden-self-host-admin
              port: 5000
      tls:
        certResolver: letsencrypt
```

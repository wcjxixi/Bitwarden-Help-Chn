# 添加 rawManifest 文件

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/add-rawmanifest-files/)
{% endhint %}

Bitwarden 自托管 Helm Chart 允许您在安装之前或安装之后包含其他 Kubernetes 清单文件。为此，请更新图表中的 `rawManifests` 部分。本文包含一些有关如何使用 rawManifests 的示例：

## 验证服务器证书 <a href="#validate-server-certificate" id="validate-server-certificate"></a>

例如，要配置 Bitwarden 来验证您的 MSSQL 数据库服务器的证书：

{% hint style="info" %}
在此示例中，您还需要在 `my-values.yaml` 文件中设置值 `caCertificate.enabled: true`。
{% endhint %}

```yml
rawManifests:
  preInstall:
  - kind: ConfigMap
    apiVersion: v1
    metadata:
      name: cacert
    data:
      rootca.crt: |
        -----BEGIN CERTIFICATE-----
         ...
        -----END CERTIFICATE-----
  postInstall:
```

## Traefik IngressRoute <a href="#traefik-ingressroute" id="traefik-ingressroute"></a>

例如，要安装 Traefik 的 IngressRoute 作为 Kubernetes 的 Ingress 控制器的替代，请添加以下内容：

{% hint style="info" %}
在此示例中，您还需要在您的 `my-values.yaml` 文件中的 `general.ingress.enabled` 处禁用入口控制器。
{% endhint %}

```yml
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

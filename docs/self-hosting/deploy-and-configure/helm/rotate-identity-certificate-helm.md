# 轮换 Helm 身份证书密码

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/rotate-identity-certificate-helm/)
{% endhint %}

本文介绍了针对部分自托管 Helm chart 部署的 Bitwarden 服务器的**已修复漏洞** 。该问题仅限于符合以下条件的特定安装：

{% hint style="warning" %}
符合**以下所有条件的**部署**需要**轮换：

* 您使用 `bitwarden/self-host` Helm chart 进行的部署。
* 您的部署**最初安装**在**低于** `2.0.0` 版本的 Chart 上。
* 您使用默认的 Chart  生成的证书 (`secrets.identityCertificate.generate: true`)。
{% endhint %}

## 背景 <a href="#background" id="background"></a>

Bitwarden 身份服务器使用 PKCS#12 (`.pfx`) 证书对其访问令牌和刷新令牌进行签名。在 Helm chart 中，该证书及其密码在安装期间生成，并存储在两个 Kubernetes Secret 中。

`2.0.0` 之前的 Chart 版本存在一个缺陷，每次安装时都会将 `.pfx` 密码设置为固定值 `map[]` 。由于该值是公开的且在所有地方都相同，因此任何获取到您的 `identity.pfx` 文件（通过备份、快照、支持包或 Pod 访问权限）的人都可以对其进行解密，并恢复您的令牌签名私钥。

该缺陷已在 `2.0.0` 及更高版本中修复（密码现在每次安装都会生成随机值），但升级不会轮换现有密码——密码只生成一次，并在升级过程中保持不变。因此，如果您最初安装的版本早于 `2.0.0` ，则您的证书将一直保留 `map[]` 密码，**直到您轮换密码为止**。轮换密码后，现有证书将使用新的随机密码重新加密。

此问题已在 `2.0.0` 及更高版本中得到修复，这些版本中默认的 Chart 生成的证书现在会为每个安装生成随机密码。如果您最初使用早期版本的 Helm Chart 和默认证书安装了 Bitwarden 服务器，**则必须手动轮换**证书密码，因为升级过程不会自动轮换证书密码。

Chart 版本 `2.3.0` 及以上包含一项检测检查，如果您的 `.pfx` 密码仍然是有缺陷的值，该检查将自动中止升级。

## 轮换您的证书密码 <a href="#rotate-your-certificate-password" id="rotate-your-certificate-password"></a>

{% hint style="info" %}
在以下所有部分中，请将 `<release>` 和 `<namespace>` 替换为您自己的值。如果您不确定发布名称或命名空间，请运行 `helm list -A`，以列出所有 Helm 发布及其命名空间。

您还需要：

* 能够通过 `kubectl` 访问集群和命名空间，并拥有读取、删除和创建机密以及重启部署的权限。
* 本地可使用 `openssl`。
{% endhint %}

### 检查您的证书密码 <a href="#check-your-certificate-password" id="check-your-certificate-password"></a>

上述警告中记录的规则可以帮助您确定您是否受到影响，但是如果您想自行确认，可以解码存储的证书密码：

```bash
kubectl get secret <release>-identity-cert-password -n <namespace> -o jsonpath='{.data.globalSettings__identityServer__certificatePassword}' | base64 -d; echo
```

如果命令返回 `map[]` ，则表示您的证书受到影响，应尽快开始处理。如果命令返回一个长的随机字母数字字符串，则表示您的证书已设置强密码，无需采取任何措施。

### 轮换后会发生什么 <a href="#what-happens-after-you-rotate" id="what-happens-after-you-rotate"></a>

轮换证书密码需要重启 `identity` 和 `sso` Pod，因此登录和令牌刷新功能可能会短暂中断。建议您在专门标记的维护窗口或流量较低的时段进行轮换。颁发给用户的访问令牌将保持可验证状态，这意味着不会发生意外注销。

### 推荐流程 <a href="#recommended-procedure" id="recommended-procedure"></a>

以下步骤使用新密码重新加密现有证书：

1、从集群中导出您的证书，特别是其中的 -identity-cert 机密：

```bash
kubectl get secret <release>-identity-cert -n bitwarden -o jsonpath='{.data.identity\.pfx}' | base64 -d > identity.pfx
```

导出后，请检查文件是否为空：

```bash
wc -c < identity.pfx
```

返回的大小为 `0` 表示未找到机密或 `identity.pfx` ，这通常是由于机密名称拼写错误造成的。

2、生成新密码并使用新密码重新加密证书。以下三条命令必须**逐字逐句地**在**同一个 shell 会话**中**独立**运行：

```bash
export NEW_PASSWORD=$(openssl rand -base64 24)
openssl pkcs12 -in identity.pfx -out identity.pem -nodes -passin pass:'map[]'
openssl pkcs12 -export -out identity-rotated.pfx -in identity.pem -passout env:NEW_PASSWORD
```

{% hint style="warning" %}
如果由于无法读取证书而导致此步骤失败，请使用以下命令生成替换证书，并将其加载到 `-identity-cert` 和 `-identity-cert-password` 机密中（**步骤 3**）：

```bash
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout identity.key -out identity.crt -subj "/CN=Bitwarden IdentityServer" -days 10950
openssl pkcs12 -export -out ./identity/identity.pfx -inkey identity.key -in identity.crt -passout pass:<your-pfx-password>
```

请注意，实施**新证书将使所有已颁发的令牌失效** ，这意味着所有用户都将被注销，需要重新登录。仅当无法重新加密时才执行此操作。
{% endhint %}

3、就地更新 `-identity-cert` 和 `-identity-cert-password` 机密：

```bash
kubectl create secret generic <release>-identity-cert -n bitwarden --from-file=identity.pfx=./identity-rotated.pfx --dry-run=client -o yaml | kubectl apply -f -
kubectl create secret generic <release>-identity-cert-password -n bitwarden --from-literal=globalSettings__identityServer__certificatePassword="$NEW_PASSWORD" --dry-run=client -o yaml | kubectl apply -f -
```

这两个命令都应该返回一个 `resource secrets/... is missing the kubectl.kubernetes.io/last-applied-configuration annotation` 警告，该警告可以忽略。

4、确认新密码机密现在包含一个新的随机值：

```bash
kubectl get secret <release>-identity-cert-password -n bitwarden -o jsonpath='{.data.globalSettings__identityServer__certificatePassword}' | base64 -d; echo
```

5、重启使用该证书的组件，即 `identity` 和 `sso` Pod：

```bash
kubectl rollout restart deployment/<release>-identity -n bitwarden
kubectl rollout restart deployment/<release>-sso -n bitwarden

kubectl rollout status deployment/<release>-identity -n bitwarden
kubectl rollout status deployment/<release>-sso -n bitwarden
```

6、待两个滚动更新均成功完成后，删除本地工作文件。尤其需要删除 `identity.pem` ，因为它包含未加密的私钥：

```bash
rm identity.pfx identity.pem identity-rotated.pfx
```

所有步骤完成后，您可以像往常一样继续进行 `helm upgrade`。

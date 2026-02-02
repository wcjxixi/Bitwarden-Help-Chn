# SMTP 配置

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/smtp-configurations/)
{% endhint %}

本指南涵盖 Bitwarden 自托管服务器的 SMTP（简单邮件传输协议）设置和常见配置问题。SMTP 通过 `api`、`identity`、`admin` 和 `notifications` 容器进行处理。所有设置均在 `global.override.env` 中配置。

{% hint style="info" %}
在自托管部署中，SMTP 是必需的，因为它是发送[来自 Bitwarden 的电子邮件](../../../security/trusted-communications/emails-from-bitwarden-servers.md)和便于[系统管理员门户](../../system-administrator-portal.md)访问所必需的。
{% endhint %}

## 配置位置 <a href="#configuration-location" id="configuration-location"></a>

通过访问 `global.override.env` 文件来管理和更新您的 SMTP 设置。

## SMTP 设置最佳实践 <a href="#smtp-setup-best-practices" id="smtp-setup-best-practices"></a>

### 使用端口 587 用于电子邮件提交 <a href="#use-port-587-for-email-submission" id="use-port-587-for-email-submission"></a>

端口 587 是默认的电子邮件提交端口。该端口是电子邮件提交的行业标准，支持 TLS 加密，并遵循 IETF 指南。

{% hint style="info" %}
除非您有特定的技术要求以及获得托管提供商的明确批准，否则请始终将 Bitwarden 配置为使用端口 587。
{% endhint %}

### 避免端口 25 用于应用程序电子邮件 <a href="#avoid-port-25-for-application-email" id="avoid-port-25-for-application-email"></a>

端口 25 不应用于 Bitwarden 电子邮件配置，也不适用于应用程序级别的电子邮件提交。此端口仅用于服务器到服务器的 SMTP 中继，它通常会被住宅 ISP 和云托管提供商屏蔽。

## 安全配置最佳实践 <a href="#security-configuration-best-practices" id="security-configuration-best-practices"></a>

### 启用 TLS 加密 <a href="#enable-tls-encryption" id="enable-tls-encryption"></a>

始终使用 TLS 加密来保护电子邮件内容和凭据：

```systemd
globalSettings__mail__smtp__port=587
globalSettings__mail__smtp__ssl=false
globalSettings__mail__smtp__startTls=true
```

端口 587 默认通过 `startTls` 使用 TLS。使用 `startTls` 时，请设置 `ssl=false` 。

### 证书处理 <a href="#certificate-handling" id="certificate-handling"></a>

对于生产环境，请确保您的 SMTP 服务器拥有有效且受信任的 SSL/TLS 证书。对于使用自签名证书的故障排除、开发或测试环境，您可以使用：

```systemd
globalSettings__mail__smtp__trustServer=true
```

{% hint style="danger" %}
仅在受控的开发环境中使用 `trustServer=true` 。对于生产系统，务必使用经过正确验证的证书，以防止中间人攻击。
{% endhint %}

### 验证服务器证书 <a href="#validate-a-server-certificate" id="validate-a-server-certificate"></a>

配置 Bitwarden 以验证您的服务器证书：

{% tabs %}
{% tab title="Docker" %}
1. 将您的根 CA 证书复制到 `./bwdata/ca-certificates` 中。
2. 运行 `./bitwarden.sh restart` 命令将证书应用到您的容器并重启服务器。
{% endtab %}

{% tab title="Helm" %}
1. 在您的 `my-values.yaml` 配置文件中，设置值 `caCertificate.enabled: true` 。
2. 创建一个包含证书文件的 ConfigMap 对象。最简单的方法是在 `my-values.yaml` 文件中添加 `preInstall` [RawManifest](../helm/add-rawmanifest-files.md)，如下例所示：

```yaml
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
{% endtab %}
{% endtabs %}

## 推荐配置 <a href="#recommended-configurations" id="recommended-configurations"></a>

该部分演示了在设置自托管环境时可参考的常见 SMTP 配置。

### 标准企业 SMTP 配置 <a href="#standard-enterprise-smtp-configuration" id="standard-enterprise-smtp-configuration"></a>

以下是一个标准 SMTP 配置示例：

```systemd
globalSettings__mail__replyToEmail=no-reply@yourdomain.com
globalSettings__mail__smtp__host=mail.yourdomain.com
globalSettings__mail__smtp__port=587
globalSettings__mail__smtp__ssl=false
globalSettings__mail__smtp__startTls=true
globalSettings__mail__smtp__username=bitwarden@yourdomain.com
globalSettings__mail__smtp__password=your-secure-password
```

### Office 365 配置示例 <a href="#example-office-365-configuration" id="example-office-365-configuration"></a>

对于使用 Microsoft Office 365 的组织：

```systemd
globalSettings__mail__replyToEmail=bitwarden@yourdomain.com
globalSettings__mail__smtp__host=smtp.office365.com
globalSettings__mail__smtp__port=587
globalSettings__mail__smtp__ssl=false
globalSettings__mail__smtp__username=bitwarden@yourdomain.com
globalSettings__mail__smtp__password=your-secure-password
```

Microsoft 建议使用专用服务账户，而不是个人电子邮箱。有关详细的设置指南，请参考[配置多功能设备](https://learn.microsoft.com/zh-cn/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365)或应用程序的 Microsoft 文档。

### 应用配置更改 <a href="#apply-configuration-changes" id="apply-configuration-changes"></a>

配置更改需要重启服务器才能生效。请将配置更改应用到 `global.override.env` ，然后执行重启以应用更改：

```shellscript
./bitwarden.sh restart
```

{% hint style="info" %}
仅重启单个容器将不会应用配置更改。
{% endhint %}

### 验证容器健康状况 <a href="#verify-container-health" id="verify-container-health"></a>

在部署到生产环境之前，务必验证所有容器是否运行正常：

```shellscript
docker ps
```

### 测试 SMTP 连接 <a href="#test-smtp-connectivity" id="test-smtp-connectivity"></a>

上线前，请从 API 容器内测试 SMTP 连接，以确保网络路径畅通且身份验证正常工作。

1、访问 API 容器：

```shellscript
sudo docker ps
sudo docker exec -it <CONTAINER_ID> sh
```

2、安装测试工具：

```shellscript
apk update
apk add busybox-extras
```

3、测试连接性：

```shellscript
telnet <smtp_server> 587
```

成功的连接表明网络连接和防火墙规则已正确配置。

### 监控电子邮件日志 <a href="#monitor-email-logs" id="monitor-email-logs"></a>

定期查看以下位置的电子邮件相关日志，以便及早发现问题：

* `./bwdata/logs/admin/`
* `./bwdata/logs/api/`
* `./bwdata/logs/identity/`
* `./bwdata/logs/notifications/`

在生产环境中实施电子邮件发送失败的日志监控或警报。

## 其他配置选项 <a href="#additional-configuration-options" id="additional-configuration-options"></a>

Bitwarden 支持额外的 [SMTP 环境](environment-variables.md#optional-variables)变量。请查看这些选项，根据您组织的需求自定义电子邮件行为。

## 摘要检查清单 <a href="#summary-checklist" id="summary-checklist"></a>

在部署 Bitwarden SMTP 配置之前，请检查以下最佳实践：

* 已配置用于电子邮件提交的端口（例如端口 587）
* 已启用 TLS 加密
* 已配置强大且唯一的 SMTP 凭据
* 已设置专门的回复地址
* 通过 API 容器测试了连接性
* 所有容器均显示健康
* 通过服务器完全重启应用了配置。
* 已实施日志监控
* 正在使用有效的 SSL/TLS 证书（生产环境）
* 文档已更新为包含配置详细信息

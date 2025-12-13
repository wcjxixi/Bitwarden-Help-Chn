# 使用转发代理配置自托管环境

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/configure-self-hosted-environment-with-forward-proxy/)
{% endhint %}

{% hint style="info" %}
转发代理的配置仅应由高级用户完成。本指南不涉及转发代理本身的设置。
{% endhint %}

本文演示了将 Bitwarden 自托管实例的流量路由到转发代理所需的必要配置。目前，仅 Linux Docker Compose 环境支持此代理环境。

{% hint style="info" %}
配置转发代理前，请先完成 Bitwarden 自托管实例的部署步骤（包括[创建 Bitwarden 本地用户和目录](linux-standard-deployment.md#create-bitwarden-local-user-and-directory)）。
{% endhint %}

* [Linux 标准部署](linux-standard-deployment.md)
* [Linux 手动部署](linux-standard-deployment-1.md)
* [Linux 离线部署](linux-offline-deployment.md)

通过**创建 Bitwarden 本地用户和目录**步骤配置您的自托管环境后，您可以返回到本指南并继续进行转发代理配置。

## 配置 Docker 以转发到您的代理 <a href="#configure-docker-to-forward-to-your-proxy" id="configure-docker-to-forward-to-your-proxy"></a>

配置 Docker 以通过我们配置的代理路由流量：

1、创建并访问 `systemd` 覆盖文件：

```shellscript
# Create directory for docker.service.d 
sudo mkdir -p /etc/systemd/system/docker.service.d

# create and edit http-proxy.conf in the new directory
sudo nano -w /etc/systemd/system/docker.service.d/http-proxy.conf 
```

2、在新文件中，我们将添加配置来指示代理通过代理环境拉取 `HTTP` 和 `HTTPS` 请求，例如：

```systemd
[Service]
Environment="HTTP_PROXY=http://10.138.0.3:3128"
Environment="HTTPS_PROXY=http://10.138.0.3:3128"
Environment="NO_PROXY=localhost,nginx,admin,mssql,sso,web,attachments,icons,notifications,icons"
```

{% hint style="info" %}
从代理配置文件中获取 `docker.service.d` 文件的信息。
{% endhint %}

3、应用更改：

```shellscript
sudo systemctl daemon-reload
```

{% hint style="info" %}
配置代理和任何特定于构建的防火墙配置将需要 root 访问权限和 sudo 权限。这些步骤应在安装 Bitwarden 之前完成。安装和设置 Bitwarden 自托管实例时，需要使用专用的 Bitwarden 用户。
{% endhint %}

4、重新启动 Docker：

```shellscript
systemctl restart docker
```

## 编辑 Bitwarden 本地用户和目录 <a href="#edit-bitwarden-local-user-and-directory" id="edit-bitwarden-local-user-and-directory"></a>

现在您已将 Docker 配置为通过转发代理发送流量，转发代理设置将需要额外的客户端配置：

1、在 `/opt/bitwarden/.docker` 和 `/home/bitwarden/.docker` 位置创建 `.config` 目录：

```shellscript
mkdir /opt/bitwarden/.docker && mkdir /home/bitwarden/.docker
```

2、创建 `config.json` 文件并为 Docker 客户端添加配置：

```shellscript
sudo nano -w /opt/bitwarden/.docker/config.json

# add configurations to config.json 
{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://10.138.0.3:3128",
     "httpsProxy": "http://10.138.0.3:3128",
     "noProxy": "localhost,nginx,admin,mssql,sso,web,attachments,icons,notifications,identity,api,events"
   }
 }
}
```

3、将 `config.json` 复制到 `bitwarden` 用户的 `/home/` 目录：

```shellscript
sudo cp /opt/bitwarden/.docker/config.json /home/bitwarden/.docker
```

## 下一步 <a href="#next-steps" id="next-steps"></a>

Docker 配置完成后，我们可以继续 Linux 自托管安装过程。对于每钟部署指南（[Linux 标准部署](linux-standard-deployment.md)、[Linux 手动部署](linux-standard-deployment-1.md)和 [Linux 离线部署](linux-offline-deployment.md)），用户需在完成**创建 Bitwarden 本地用户和目录**步骤后，继续执行后续操作以完成自托管安装。

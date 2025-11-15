# 证书选项

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/certificates/)
{% endhint %}

本文定义了 Bitwarden 自托管实例可用的证书选项。您可以在安装过程中选择证书选项。**设置或更改证书配置总是需要**您在启动 Bitwarden 之前运行 `./bitwarden.sh rebuild` 或 `.\bitwarden.ps1 -rebuild` 命令来应用对 config.yml 文件的更改。

{% hint style="info" %}
本文中的信息可能不适用于 Bitwarden Unified 自托管部署。
{% endhint %}

## 使用 Let’s Encrypt 生成证书 <a href="#generate-a-certificate-with-lets-encrypt" id="generate-a-certificate-with-lets-encrypt"></a>

[Let's Encrypt](https://letsencrypt.org/how-it-works/) 是一个证书颁发机构（CA - Certificate Authority），可以为任何域名颁发免费的可信的 SSL 证书。Bitwarden 安装脚本提供了使用 Let's Encrypt 和 [Certbot](https://certbot.eff.org/) 为你的域名生成可信 SSL 证书的选项。

每次重新启动 Bitwarden 时，都会进行证书更新检查。使用 Let's Encyrpt 会要求你输入一个电子邮箱地址来获取证书到期提醒。

{% hint style="danger" %}
Let's Encrypt 是一个第三方证书颁发机构，它要求 80 和 443 端口可以从互联网访问，以便验证你的域名并颁发证书。如果您没有或不想设置互联网入站访问，您可以使用本文档中的其他证书选项。
{% endhint %}

### 手动更新 Let's Encrypt 证书 <a href="#manually-update-a-lets-encrypt-certificate" id="manually-update-a-lets-encrypt-certificate"></a>

如果您更改了 Bitwarden 服务器的域名，则需要手动更新已生成的证书。运行以下命令以创建备份、更新证书并重建 Bitwarden：

<img src="../../../../.gitbook/assets/linux-24.png" alt="" data-size="line"><img src="../../../../.gitbook/assets/apple-24.png" alt="" data-size="line"> **Bash**

```bash
./bitwarden.sh stop
mv ./bwdata/letsencrypt ./bwdata/letsencrypt_backup
mkdir ./bwdata/letsencrypt
chown -R bitwarden:bitwarden ./bwdata/letsencrypt
chmod -R 740 ./bwdata/letsencrypt
docker pull certbot/certbot
docker run -i --rm --name certbot -p 443:443 -p 80:80 -v <Full Path from / >/bwdata/letsencrypt:/etc/letsencrypt/ certbot/certbot certonly --email <user@email.com> --logs-dir /etc/letsencrypt/logs
```

选择 1，然后按照说明进行操作：

```shell
openssl dhparam -out ./bwdata/letsencrypt/live/<your.domain.com>/dhparam.pem 2048
./bitwarden.sh rebuild
./bitwarden.sh start
```

<img src="../../../../.gitbook/assets/os-windows-24.png" alt="" data-size="line"> PowerShell

{% hint style="info" %}
需要安装适用于 Windows 的 OpenSSL 构建。
{% endhint %}

```powershell
.\bitwarden.ps1 -stop
mv .\bwdata\letsencrypt .\bwdata\letsencrypt_backup
mkdir .\bwdata\letsencrypt
docker pull certbot/certbot
docker run -i --rm --name certbot -p 443:443 -p 80:80 -v <Full Path from \ >\bwdata\letsencrypt\:/etc/letsencrypt/ certbot/certbot certonly --email <user@email.com> --logs-dir /etc/letsencrypt/logs
Select 1, then follow instructions
<path/to/openssl.exe> dhparam -out .\bwdata\letsencrypt\live\<your.domain.com>\dhparam.pem 2048
.\bitwarden.ps1 -rebuild
.\bitwarden.ps1 -start
```

## 使用现有的 SSL 证书 <a href="#use-an-existing-ssl-certificate" id="use-an-existing-ssl-certificate"></a>

您也可以选择使用现有的 SSL 证书，这要求您已经拥有如下的文件：

* 服务器证书（`certificate.crt`）
* 私钥（`private.key`）
* CA 证书（`ca.crt`）

您可能需要将主证书与中间 CA 证书捆绑在一起，以防止 SSL 信任错误。当使用根 CA 和中间 CA 证书时，所有证书都应该包含在服务器证书文件中。

在默认配置下，将您的文件放在 `./bwdata/ssl/your.domain` 中。您可以通过编辑 `./bwdata/config.yml` 中的以下值来指定证书文件的不同位置：

```yaml
ssl_certificate_path: <path>
ssl_key_path: <path>
ssl_ca_path: <path>
```

{% hint style="info" %}
`config.yml` 中定义的值代表了 NGINX 容器内的位置，主机上的目录被映射到 NGINX 容器内的目录。在默认配置下，映射如下：

`config.yml` 中的以下值：

```yaml
ssl_certificate_path: /etc/ssl/your.domain/certificate.crt
ssl_key_path: /etc/ssl/your.domain/private.key
ssl_ca_path: /etc/ssl/your.domain/ca.crt
```

映射到主机上的以下文件：

```yaml
./bwdata/ssl/your.domain/certificate.crt
./bwdata/ssl/your.domain/private.key
./bwdata/ssl/your.domain/ca/crt
```

**您只需要在 `./bwdata/ssl/` 中处理这些文件。不建议直接在 NGINX 容器中处理这些文件。**
{% endhint %}

### 使用 Diffie-Hellman 密钥交换 <a href="#using-diffie-hellman-key-exchange" id="using-diffie-hellman-key-exchange"></a>

（_可选_）如果使用 Diffie Hellman 密钥交换生成临时参数：

* 在同一目录中包含 `dhparam.pem` 文件。
* 在 `config.yml` 中设置 `ssl_diffie_hellman_path:` 值。

{% hint style="info" %}
您可以使用 OpenSSL 的 `openssl dhparam -out ./dhparam.pem 2048` 命令来生成自己的 `dhparam.pem` 文件。
{% endhint %}

## 使用自签名证书 <a href="#using-a-self-signed-certificate" id="using-a-self-signed-certificate"></a>

您也可以选择使用自签名证书，但这只建议用于测试。

默认情况下，Bitwarden 客户端应用程序不会信任自签名证书。您需要手动将该证书安装到您计划使用 Bitwarden 的每一个设备的受信任存储中。

生成自签名证书：

```shell
mkdir ./bwdata/ssl/bitwarden.example.com
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -days 365 \
  -keyout ./ssl/bitwarden.example.com/private.key \
  -out ./ssl/bitwarden.example.com/certificate.crt \
  -reqexts SAN -extensions SAN \
  -config <(cat /usr/lib/ssl/openssl.cnf <(printf '[SAN]\nsubjectAltName=DNS:bitwarden.example.com\nbasicConstraints=CA:true')) \
  -subj "/C=US/ST=New York/L=New York/O=Company Name/OU=Bitwarden/CN=bitwarden.example.com"
```

您的自签名证书（`.crt`）和私钥（`private.key`）文件可以放置于 `./bwdata/ssl/self/your.domain` 目录并将其配置到 `./bwdata/config.yml` 中：

```yaml
ssl_certificate_path: /etc/ssl/bitwarden.example.com/certificate.crt
ssl_key_path: /etc/ssl/bitwarden.example.com/private.key
```

### 信任自签名证书 <a href="#trust-a-self-signed-certificate" id="trust-a-self-signed-certificate"></a>

#### Windows

要在 Windows 上信任自签名证书，请运行 `certmgr.msc` 并将证书导入受信任的根证书颁发机构中。

#### Linux

要在 Linux 上信任自签名证书，请将证书添加到以下目录中：

```yaml
/usr/local/share/ca-certificates/
/usr/share/ca-certificates/
```

然后进行以下命令：

```shell
sudo dpkg-reconfigure ca-certificates
sudo update-ca-certificates
```

对于 Bitwarden Linux 桌面 App，请使用基于 Chromium 的浏览器和 Directory Connector 桌面 App 访问网页密码库，您还需要完成[此 Linux 证书管理过程](https://chromium.googlesource.com/chromium/src/+/refs/heads/master/docs/linux/cert_management.md)。

对于 [Bitwarden CLI](../../../password-manager/developer-tools/cli/password-manager-cli.md) 和[目录连接器 CLI](../../../admin-console/manage-members/directory-connector/directory-connector-cli.md)，您的自签名证书必须存储在本地文件中并由 `NODE_EXTRA_CA_CERTS=` 环境变量引用，例如：

```shell
export NODE_EXTRA_CA_CERTS=~/.config/Bitwarden/certificate.crt
```

#### Android

要信任 Android 设备上的自签名证书，请参阅 Google 文档：[添加和移除证书](https://support.google.com/pixelphone/answer/2844832?hl=zh-Hans)。

{% hint style="info" %}
如果您不是自托管并且在您的 Android 设备上遇到以下证书错误：

```yaml
Exception message: java.security.cert.CertPathValidatorException: Trust anchor for certification path not found.
```

您需要将 Bitwarden 证书上传到您的设备中。有关查找证书的帮助信息，请参阅[此社区话题](https://community.bitwarden.com/t/android-client-login-bitwarden-https-cert-problem/12132)。
{% endhint %}

## 不使用证书 <a href="#use-no-certificate" id="use-no-certificate"></a>

{% hint style="warning" %}
如果您选择不使用证书，则**必须在您的 Bitwarden 安装的前端使用 SSL 代理**。这是因为 Bitwarden 需要 HTTPS。尝试在没有 HTTPS 协议的情况下使用 Bitwarden 将触发错误。
{% endhint %}

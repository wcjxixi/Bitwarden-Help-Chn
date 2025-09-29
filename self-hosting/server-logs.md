# 服务器日志

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/server-logs/)
{% endhint %}

本文包含有关访问和配置服务器日志存储的信息。具体内容取决于您的部署方法：

{% tabs %}
{% tab title="Docker" %}
## 实时日志 <a href="#logs-in-real-time" id="logs-in-real-time"></a>

如果您使用 Docker 部署 Bitwarden，请使用 `docker compose logs -f` 命令从终端或命令行实时查看日志。请注意，此命令应从 `/bwdata/docker` 目录运行：

```bash
cd /opt/bitwarden/bwdata/docker
docker compose logs -f
```

## 存储日志 <a href="#logs-in-storage" id="logs-in-storage"></a>

自托管 Bitwarden 服务器生成的日志默认存储在 `bwdata/logs/` 。

要更改默认的日志存储位置，请访问您的 `global.override.env` 文件并将环境变量 `globalSettings__logDirectory=` 设置为所需位置。

更改环境变量后，您需要重启服务器以应用新的配置：

* 如果您使用的是标准部署方法，请使用 `bitwarden.sh` 或 `bitwarden.ps1 restart` 命令。
* 如果您手动或离线部署 Bitwarden，请使用 `docker compose down` 并回退 `up` ，例如：

```bash
docker compose -f ./docker/docker-compose.yml down && docker compose -f ./docker/docker-compose.yml up -d
```

## 下载日志 <a href="#download-logs" id="download-logs"></a>

如果您使用 `bitwarden.sh` 或 `bitwarden.ps1` 安装脚本通过 Docker 部署了 Bitwarden，您还可以使用 `compresslogs` 命令下载所有服务器日志的 tarball，或指定日期范围内的所有服务器日志：

```bash
./bitwarden.sh compresslogs 20240304 20240305
.\bitwarden.ps1 -compresslogs 20240304 20240305
```
{% endtab %}

{% tab title="Helm" %}
## 实时日志 <a href="#logs-in-real-time" id="logs-in-real-time"></a>

默认情况下，Helm 部署的日志是临时的，不会存储在中央位置。服务器运行时，可以通过容器的 stdout 实时访问日志，例如运行以下命令：

```bash
kubectl logs pod api
```

## 存储日志 <a href="#logs-in-storage" id="logs-in-storage"></a>

您可以通过将您的 `my-values.yaml` 文件中的 `volume.logs.enabled:` 值设置为 `true` 来配置服务器将日志保存到持久卷 (PVC)。默认情况下，日志会保存到新的 PVC，但您可以通过配置 `volume.logs.existingClaim:` 值来使用现有的 PVC。
{% endtab %}
{% endtabs %}


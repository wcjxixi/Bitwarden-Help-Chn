# 调度同步

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/schedule-directory-sync/)
{% endhint %}

对于使用目录连接器 CLI 的组织，可以根据定义的时间间隔安排自动同步，以替代使用桌面 App 的**间隔**设置。这在无头环境或桌面应用程序不能在后台运行的情况下特别有用。

要调度同步，请在类 Unix 环境（包括 Linux 和 MacOS）中使用 **Cron**，在 Windows 环境中使用**任务计划程序**：

{% tabs %}
{% tab title="Cron" %}
### Cron 权限 <a href="#cron-permissions" id="cron-permissions"></a>

运行 cron 作业时，我们建议以一个专用的目录连接器用户的身份执行此操作。创建一个 `bwdc` 用户（如果还没有的话），然后将该用户添加到 `etc/cron.allow` 列表中。这将允许非 root 用户设置和运行 cron 作业。

接下来您还需要组织 [API 密钥](../../bitwarden-public-api.md#authentication)的 `client_id` 和 `client_secret` 值，组织**所有者**可以从网页密码库导航到组织**设置** → **我的组织**获取它们。

### 设置同步脚本 <a href="#setup-a-sync-script" id="setup-a-sync-script"></a>

为了避免会话超时，我们建议创建一个 shell 脚本通过 cron 来运行。此脚本应安全地读取您的 `client_secret` 以完成登录，然后运行 `bwdc sync` 命令并将输出写入 `bwdc.log` 文件。

{% hint style="success" %}
需要从多个目录同步吗？在同步脚本中，您可以指定多个文件夹，每个文件夹都必须包含一个带有目录同步设置的 `data.json` 文件。

然后，您可以通过执行多个 `bwdc sync` 操作来指定要同步的每个目录，例如：

```shell
BITWARDENCLI_CONNECTOR_APPDATA_DIR="./instance-1" bwdc sync
BITWARDENCLI_CONNECTOR_APPDATA_DIR="./instance-2" bwdc sync
```
{% endhint %}

### 设置 Cron 作业 <a href="#setup-the-cron-job" id="setup-the-cron-job"></a>

作为被允许的 `bwdc` 用户：

1. 通过在终端中输入 `crontab -e` 来编辑用户的 crontab 文件，或者以任何用户身份通过输入 `crontab -u <bwdc_username> -e` 来编辑 crontab 文件。
2. 向 crontab 添加一行，其中包括：
   * 一个[调度表达式](schedule-a-sync.md#cron-job-scheduling-expressions)，它将确定执行所需命令的时间/重复间隔（例如 `0 0 * * 2` 表示在每个星期二的午夜运行）。
   * 在指定的时间/重复间隔执行的命令。在这种情况下，执行[之前创建的同步脚本](schedule-a-sync.md#setup-a-sync-script)（例如 `bwdcSyncService.sh`）。

例如，要在每周一的 12:00 运行同步脚本：

```systemd
# 0 12 * * 1 bwdcSyncService.sh
```

### Cron 作业调度表达式 <a href="#cron-job-scheduling-expressions" id="cron-job-scheduling-expressions"></a>

在通过 cron 调度同步时，请使用以下参考，以确保把它们调度到所需的时间：

```
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of the month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday;
# │ │ │ │ │                                   7 is also Sunday on some systems)
# │ │ │ │ │
# │ │ │ │ │
# * * * * * <command to execute>
```

{% hint style="success" %}
如果您还不熟悉 cron 作业调度表达式，请查看 [https://crontab.guru/](https://crontab.guru/) 以获取帮助。

请注意，这是第三方资源，并非由 Bitwarden 运营或维护。
{% endhint %}
{% endtab %}

{% tab title="任务计划程序" %}
### 任务计划程序权限

运行任务时，我们建议以一个专用的目录连接器用户的身份执行此操作。创建一个 `bwdc` 用户（如果还没有的话）。

接下来您还需要组织 [API 密钥](../../bitwarden-public-api.md#authentication)的 `client_id` 和 `client_secret` 值，组织**所有者**可以从网页密码库导航到组织**设置** → **我的组织**获取它们。

### 设置同步脚本 <a href="#setup-a-sync-script" id="setup-a-sync-script"></a>

为了避免会话超时，您需要创建一个脚本以作为任务计划程序操作运行。此脚本应安全地读取您的 `client_secret` 以完成登录，然后运行 `bwdc sync` 命令并将输出写入 `bwdc.log` 文件。

{% hint style="success" %}
需要从多个目录同步吗？在同步脚本中，您可以指定多个文件夹，每个文件夹都必须包含一个带有目录同步设置的 `data.json` 文件。

然后，您可以通过执行多个 `bwdc sync` 操作来指定要同步的每个目录，例如：

```shell
BITWARDENCLI_CONNECTOR_APPDATA_DIR="./instance-1" bwdc sync
BITWARDENCLI_CONNECTOR_APPDATA_DIR="./instance-2" bwdc sync
```
{% endhint %}

### 创建一个任务

作为被允许的 `bwdc` 用户：

1、打开任务计划程序并从操作菜单中选择**创建任务**。

2、使用以下安全选项配置此任务：

* 将任务设置为使用已创建的 `bwdc` 用户。
* 将任务设置为**不管用户是否登录都要运行**。

3、选择**触发器**选项卡并选择**新建...** 按钮以创建适合您的目录同步需求的触发器。

{% hint style="success" %}
例如，您可以创建一个每周日晚上 8:00 运行的每周触发器：



![](<../../../../.gitbook/assets/image (6).png>)
{% endhint %}

4、选择**操作**选项卡，然后选择**新建...** 按钮以创建一个用于运行已创建的同步脚本的操作。

5、选择**确定**以完成定时任务的创建。
{% endtab %}
{% endtabs %}

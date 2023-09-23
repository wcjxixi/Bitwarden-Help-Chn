# 迁移脚本

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/migration-script/)
{% endhint %}

[Bitwarden 公共 API](../organizations/bitwarden-public-api.md) 允许管理员使用脚本自动执行管理任务。本文所描述的脚本是为了帮助 Bitwarden 客户将现有的设置从之前的 Bitwarden 密码管理器环境迁移到新的组织而编写的，提供了一种将组织密码库数据、群组以及相关联的群组和成员的权限迁移到新安装的方法。

该脚本使用 Python 编写，可以在任何安装了 Python v3 的操作系统上运行。在[此处](https://assets.ctfassets.net/7rncvj1f8mw7/76zQs7igKMkSy7W2lpgbGv/645d32aef0a13268b322a03ee4324592/bwAdminTools.zip)下载脚本和示例配置文件。

## 安装和设置 <a href="#installation-and-setup" id="installation-and-setup"></a>

### 系统要求 <a href="#system-requirements" id="system-requirements"></a>

除了大多数 Python 发行版附带的默认库（Linux 和 macOS 上默认包含，Windows 也[可用](https://www.python.org/downloads/windows/)）之外，此脚本还需要安装一个名为 `requests` 的附加模块，然后才能成功运行该脚本。

安装 Python 模块的常用工具称为 pip。要使用 pip 安装此模块：

```batch
pip3 install requests
```

{% hint style="info" %}
`pip3` - 有些机器会安装多个版本的 Python。使用 `pip3`（而不仅仅是 `pip`）指定您使用 Python v3 安装 `requests`。如果您的计算机仅安装了一个 Python 版本，请改用 `pip`。
{% endhint %}

### 所需文件 <a href="#required-files" id="required-files"></a>

上述下载包含两个文件：

* `bwAdminTools.py`：这是执行迁移所需的脚本。它需要一个完整配置的配置文件。
* `config-example.cfg`：这是迁移所需的配置文件，您需要在运行脚本之前创建和设置该文件。

解压 `.zip` 并将这些文件保存到同一目录中。完成后，将以下文件添加到同一目录：

* Bitwarden 密码管理器 [CLI 本机可执行文件](../password-manager/developer-tools/password-manager-cli.md#download-and-install)。

### 创建目标组织 <a href="#create-destination-organization" id="create-destination-organization"></a>

在继续之前，您必须创建要迁移到的目标组织。[了解如何创建组织](../organizations/organizations.md#create-an-organization)。

### 环境配置 <a href="#environment-configuration" id="environment-configuration"></a>

在运行任何 `bwAdminTools.py` [脚本函数](migration-script.md#script-functions)之前，您需要创建一个配置文件。将 `config-example.cfg` 的内容复制到同一目录中的新 `config.cfg` 文件中，并填写以下变量。请注意，由于这是迁移脚本，因此本文档中的变量分为**源**和**目标**两部分：

| 源组织变量                    | 变量描述                                                                                                                                               |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| bw\_vault\_uri=          | 您的来源网页密码库的 FQDN，例如如果您是自托管，为 https://company.bitwarden.com；如果您使用的是美国区域的 Bitwarden 云服务，则为 https://vault.bitwarden.com。                               |
| bw\_org\_client\_id=     | 源组织 API 密钥客户端 ID。[了解在哪里可以找到它](../organizations/bitwarden-public-api.md#authentication)。                                                            |
| bw\_org\_client\_secret= | 源组织 API 密钥客户端机密。[了解在哪里可以找到它](../organizations/bitwarden-public-api.md#authentication)。                                                             |
| bw\_org\_id=             | 源组织的 GUID。复制 `_client_id=` 值并删除 `organization.` 块。                                                                                                 |
| bw\_acc\_client\_id      | 源组织管理员或所有者的个人 API 密钥客户端 ID。[了解在哪里可以找到它](../password-manager/developer-tools/personal-api-key-for-cli-authentication.md#get-your-personal-api-key)。 |
| bw\_acc\_client\_secret= | 源组织管理员或所有者的个人 API 密钥客户端机密。[了解在哪里可以找到它](../password-manager/developer-tools/personal-api-key-for-cli-authentication.md#get-your-personal-api-key)。  |

| 目标组织变量                         | 变量描述                                                                                                                                                |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| dest\_bw\_vault\_uri=          | 您的目标网页密码库的 FQDN，例如如果您是自托管，为 https://company.bitwarden.com；如果您使用的是欧盟区域的 Bitwarden 云服务，则为 https://vault.bitwarden.eu。                                 |
| dest\_bw\_org\_client\_id=     | 目标组织 API 密钥客户端 ID。[了解在哪里可以找到它](../organizations/bitwarden-public-api.md#authentication)。                                                            |
| dest\_bw\_org\_client\_secret= | 目标组织 API 密钥客户端机密。[了解在哪里可以找到它](../organizations/bitwarden-public-api.md#authentication)。                                                             |
| dest\_bw\_org\_id=             | 目标组织的 GUID。复制 `_client_id=` 值并删除 `organization.` 块。                                                                                                 |
| dest\_bw\_acc\_client\_id=     | 目标组织管理员或所有者的个人 API 密钥客户端 ID。[了解在哪里可以找到它](../password-manager/developer-tools/personal-api-key-for-cli-authentication.md#get-your-personal-api-key)。 |
| dest\_bw\_ac\_client\_secret=  | 目标组织管理员或所有者的个人 API 密钥客户端机密。[了解在哪里可以找到它](../password-manager/developer-tools/personal-api-key-for-cli-authentication.md#get-your-personal-api-key)。  |

## 脚本功能 <a href="#script-functions" id="script-functions"></a>

从存储 `bwAdminTools.py` 文件、`config.cfg` 文件和密码管理器 CLI 可执行文件的目录中，您可以运行以下命令：

{% hint style="info" %}
`python3` - 有些机器会安装多个版本的 Python。使用 `python3`（而不仅仅是 `python`）指定命令使用 Python v3 运行。如果您的计算机仅安装了一个 Python 版本，请改用 `python`。某些发行版还将提供 `python` 而不是 v3 的 `python3` 二进制文件。
{% endhint %}

要显示脚本帮助文本：

```batch
python3 bwAdminTools.py -h
```

要比较源组织和目标组织：

```batch
python3 bwAdminTools.py -c diffbw
```

要将组织库数据、群组和群组权限从源组织迁移到目标组织：

```batch
python3 bwAdminTools.py -c migratebw
```

要将成员的权限（群组以外的）从源组织迁移到目标组织：

```batch
python3 bwAdminTools.py -c migratebwusers
```

要从源组织中删除所有集合：

```batch
python3 bwAdminTools.py -c purgecol
```

要从目标组织中删除所有集合：

```batch
python3 bwAdminTools.py -c purgecoldest
```

要从源组织中删除所有群组：

```batch
python3 bwAdminTools.py -c purgegroup
```

要从目标组织中删除所有群组：

```batch
python3 bwAdminTools.py -c purgegroupdest
```

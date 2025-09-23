# 自托管 SCIM

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/self-hosting-scim/)
{% endhint %}

本文所述步骤适用于 Docker 标准部署，在 Helm 部署中，您需要在 `values.yaml` 文件中设置 `scim: true` 以启用 SCIM。

要在您的自托管 Bitwarden 组织中使用 [SCIM](../../../admin-console/manage-members/scim/about-scim.md) 自动配置和取消配置成员和群组，您需要在 `config.yml` 文件中开启一个标志。要为您的 Bitwarden 服务器启用 SCIM：

1、至少保存一个 `.bwdata/mssql` 的[备份](../../backup-server-data.md)。一旦 SCIM 投入使用，建议您拥有访问备份映像的权限以防出现问题。

{% hint style="info" %}
如果您使用的是[外部 MSSQL 数据库](../configuration-options/connect-to-an-external-mssql-database.md)，请以适合您的实施的任何方式备份您的数据库。
{% endhint %}

2、更新您的自托管 Bitwarden 安装以获取最新的更改：

```
./bitwarden.sh update
```

3、编辑 `.bwdata/config.yml` 文件并将 `enable_scim` 的值切换为 `true` 以启用 SCIM。

```
nano bwdata/config.yml
```

4、重建您的自托管 Bitwarden 安装：

```
./bitwarden.sh rebuild
```

5、再次更新您的自托管 Bitwarden 安装以应用更改：

```
./bitwarden.sh update
```

现在您的服务器已启用 SCIM 了，请使用我们的 SCIM 集成指南之一将您的 Bitwarden 组织与其集成：

* [Azure Entra ID](../../../admin-console/manage-members/scim/microsoft-entra-id-scim-integration.md)
* [Okta](../../../admin-console/manage-members/scim/okta-scim-integration.md)
* [OneLogin](../../../admin-console/manage-members/scim/onelogin-scim-integration.md)
* [JumpCloud](../../../admin-console/manage-members/scim/jumpcloud-scim-integration.md)

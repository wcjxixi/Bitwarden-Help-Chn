# 导出数据

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/export-secrets-data/)
{% endhint %}

您可以将您的机密数据从网页密码库导出为 `.json` 文件。导出将包括[工程](../your-secrets/projects.md)和[机密](../your-secrets/secrets.md)，但不包括[服务账户](../your-secrets/machine-accounts.md)和[访问令牌](../your-secrets/access-tokens.md)。只会导出从组织选择器中选择的当前组织相关联的 Secrets Manager 数据。其他产品中或来自其他组织的项目将不包括在内。

要导出数据：

{% hint style="info" %}
要导出 Secrets Manager 数据，您的用户账户必须是组织内的所有者或管理员。
{% endhint %}

1、从左侧导航中选择**设置** → **导出数据**：

{% embed url="https://bitwarden.com/_gatsby/image/c9f811c7c9a61cc7fdfa3ae5e94cde47/66586c29051791eb30927eba73e299f1/Screen%20Shot%202023-02-27%20at%2010.17.14%20AM.webp?eu=8c8e53e7b0cdfed20a3af68a3b246060e06c06aeaf5964d03d64b1a61eaa9dd32ca1110427c37ce32c3b0ed9d3e340be6e927f6619b8d2df91b51ff4be61fc5d06d20fe76ee17802522ac5afb0a1521439c01e0da1829b0bab3f77d7b6b2bd285d145c68a265a7d8b1f86231f39d7c76bce7e56d3086e866be471a4bcc5a2faf22e191883b43a9c9af1b8a829cdb5b929ca56f46229fb05c410511462b9164a4a2e105256a7c115f67cea80ec76396be384e32200a5b04f46f3cd754fe6c35c6fb98f21f8c2f258ecb916e34e9c1ae82ee07ac286be5c848f8c6547b0e13ad14b3bd7f98a319184edf7d&a=w%3D850%26h%3D238%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.786Z" %}
导出数据
{% endembed %}

2、从下拉列表中选择**文件格式**。对于测试版，仅支持 `.json`。

3、选择**导出数据**按钮。根据提示，输入您的主密码。

# 导出数据

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/export-secrets-data/)
{% endhint %}

您可以将您的机密数据从网页密码库导出为 `.json` 文件。导出将包括[工程](../your-secrets/projects.md)和[机密](../your-secrets/secrets.md)，但不包括[机器账户](../your-secrets/machine-accounts.md)和[访问令牌](../your-secrets/access-tokens.md)。只会导出从组织选择器中选择的当前组织相关联的 Secrets Manager 数据。其他产品中或来自其他组织的项目将不包括在内。

要导出您的数据：

{% hint style="info" %}
要导出 Secrets Manager 数据，您的用户账户必须是组织内的所有者或管理员。
{% endhint %}

1、从左侧导航中选择**设置** → **导出数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4UTBBbo0rrqRtsYSBmiCLy/9aac6ff493e1fe9de93791516d5c6847/Screenshot_2024-04-10_at_9.56.08_AM.png?_a=BAJFJtWIB" %}
导出数据
{% endembed %}

2、从下拉列表中选择**文件格式**。对于测试版，仅支持 `.json`。

3、选择**导出数据**按钮。根据提示，输入您的主密码。

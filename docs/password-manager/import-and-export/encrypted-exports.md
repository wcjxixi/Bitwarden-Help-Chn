# 加密导出

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/encrypted-export/)
{% endhint %}

密码库数据可以导出为[用于个人](export-vault-data.md)和[用于组织](../../admin-console/manage-shared-items/export-organization-items/)的加密的 `.json` 文件。提供两种加密导出类型：

* **账户限制**：导出加密文件，只能重新导入到生成加密导出文件的 Bitwarden 账户或组织。此过程使用专用的受限导出的相关账户或组织的加密密钥。。
* **密码保护**：使用您选择的密码保护导出的加密文件。该文件使用您选择的密码解密，并且可以导入任何 Bitwarden 账户。此指定的密码经过加盐处理，使用 PBKDF2 以 100,000 次迭代派生出加密密钥，最后使用 HDKF 拉伸为一个新的加密密钥，用于加密您的数据以及消息身份验证代码 (MAC)。

{% hint style="danger" %}
**账户限制**的导出不能导入到其他账户。此外，[轮换您账户的加密密钥](../../security/encryption/encryption-key-rotation.md)将导致已加密的导出无法解密。**如果您轮换了您的加密密钥，请使用新的加密密钥导出新文件以替换所有旧文件。**

如果您希望将加密的 `.json` 文件导入不同的 Bitwarden 账户，请在创建导出时选择**密码保护**的导出类型。
{% endhint %}

加密导出将包含所有密码库数据，包括登录、支付卡、安全笔记和身份。比如如下明文的登录项目：

```yaml
{
      ...
      "login": {
        "username": "mylogin",
        "password": "mypassword",
        "totp": "otpauth://totp/my-secret-key"
      },
      ...
```

加密导出后看起来会像这样：

```yaml
{
      ...
      "login": {
        "username": "9.dZwQ+b9Zasp98dnfp[g|dHZZ1p19783bn1KzkEsA=l52bcWB/w9unvCt2zE/kCwdpiubAOf104os}",
        "password": "1o8y3oqsp8n8986HmW7qA=oiCZo872b3dbp0nzT/Pw=|A2lgso87bfDBCys049ano278ebdmTe4:",
        "totp": "2CIUxtpo870B)*^GW2ta/xb0IYyepO(*&G(&BB84LZ5ByZxu0E9hTTs6PHg0=8q5DHEPU&bp9&*bns3EYgETXpiu9898sxO78l"
      },
      ...
```

## 下一步 <a href="#next-steps" id="next-steps"></a>

* [作为个人用户创建加密导出](export-vault-data.md)。
* [创建您组织数据的加密导出](../../admin-console/manage-shared-items/export-organization-items/export-organization-items.md)。
* [作为个人用户重新导入加密导出](import-data.md)。
* [以组织身份重新导入加密导出](../../admin-console/manage-shared-items/import-organization-items/import-to-organization.md)。

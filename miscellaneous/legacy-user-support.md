# 旧版用户支持

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/legacy-user-support/)
{% endhint %}

{% hint style="danger" %}
随着在 2025 年 06 月 24 日部署了 2025.6.2 服务器版本，Bitwarden 已正式停止对旧版用户的支持。

* **若您的账户创建于 2017 年之后**，则不受此次变更的影响。
* **若您的账户创建于 2017 年之前**，只要您在 2023 年后曾登录过网页 App，则不受到此次变更的影响。
{% endhint %}

**2017 年之前创建的账户**采用了一种直接使用主密码派生的密钥来加密账户数据的加密方案。这种加密方式缺乏灵活性，并存在潜在安全风险。2017 年，Bitwarden 更新了[加密方案](../security/bitwarden-security-whitepaper.md#hashing-key-derivation-and-encryption)以解决这些问题。更新后：

* （2017 年）网页 App 中增加了自动将账户迁移至新加密方案的工作流程。
* （2023 年）Bitwarden 客户端（除网页版外）进行了变更，阻止旧版用户的登录。系统会提示错误信息，并引导用户登录网页 App 完成迁移。
* （2025 年）Bitwarden 服务器进行了变更，使剩余的旧版用户退出当前会话，要求他们在网页 App 上执行迁移。受影响的用户在变更后收到了邮件通知。

基于这些措施，截至 2025.6.1 版本，几乎不存在仍在使用旧版加密方案的活跃 Bitwarden 账户。

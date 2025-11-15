# 加密的数据

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/vault-data/)
{% endhint %}

所有的密码库数据在存储到任何地方之前都会被 Bitwarden 加密。要了解是如何加密的，请参阅 [Bitwarden 安全白皮书](../bitwarden-security-whitepaper.md)。Bitwarden 是一种零知识的解决方案，这意味着您是唯一能够获得您的密钥并能够解密您的密码库数据的一方。

下面列出了加密数据的示例以及加密数据演示的下载链接。

{% hint style="success" %}
我们鼓励您查看我们的[隐私政策](https://bitwarden.com/privacy)页面以了解更多信息。
{% endhint %}

加密的密码库数据包括：

* 对于所有项目：
  * 项目名称
  * 备注
  * 附件
    * 附件名称
    * 文件内容
    * 文件加密密钥
  * 自定义字段名称和值
* 对于[登录](https://assets.ctfassets.net/7rncvj1f8mw7/yfr02nYyvD0GmjXzXjAu5/7e1091a1f05638807caa3268e3333038/login1__1_.json)：
  * 用户名
  * 密码
    * 密码历史记录
  * URI（即匹配检测字符串）
  * 身份验证器密钥（即 TOTP 机密）
* 对于[支付卡](https://assets.ctfassets.net/7rncvj1f8mw7/5HYmBCBzT1qVE4yeqwY1F3/7330978a17d92c36e9765cda6834d8d5/card1.json)：
  * 持卡人姓名
  * 号码
  * 品牌
  * 到期日期
  * 安全码
* 对于[身份](https://assets.ctfassets.net/7rncvj1f8mw7/5ltDUVHgqqx1yfHIzv5e4k/40f8ae52b2c74feeab2d19e02ea87310/id1.json)：
  * 姓名（头衔/名字/中间名/姓氏）
  * 用户名
  * 公司
  * 社会安全号码、护照号码和驾照号码
  * 电子邮箱和电话
  * 地址 1、地址 2、地址 3、城市/城镇、州/省、邮政编码、国家/地区
* 对于 [Send](https://assets.ctfassets.net/7rncvj1f8mw7/5QUNWhFSzC7EIo8CaHjxta/681e78b34a6beba57e0e7e753a3c5ce3/send1.json)：
  * Send 名称
  * Send 文本
  * Send 文件
  * Send 备注
  * Send 加密密钥（[了解更多](../../password-manager/bitwarden-send/send-encryption.md)）
* [文件夹](https://assets.ctfassets.net/7rncvj1f8mw7/6qRBtIOjOOjDryxVo35sQF/d3412d19a841da5ee13b9c73818f6a4c/folders1.json)名称
* [集合](https://assets.ctfassets.net/7rncvj1f8mw7/3KT79LDVKbIhF5cpNk5tL/5097c78255b6abd435233163085cda58/collection1.json)名称

加密的 [Secrets Manager](../../secrets-manager/secrets-manager-overview.md) 数据包括：

* 对于[机密](../../secrets-manager/your-secrets/secrets.md)：
  * 机密名称
  * 机密值
  * 机密备注
* [工程](../../secrets-manager/your-secrets/projects.md)名称
* [服务账户](../../secrets-manager/your-secrets/machine-accounts.md)名称
* [访问令牌](../../secrets-manager/your-secrets/access-tokens.md)名称（Bitwarden 永远不会存储访问令牌的值）

某些数据，但**绝非密码库或机密数据**，用于向您提供 Bitwarden 服务，这被称为管理数据，可被 Bitwarden 访问。[了解更多](administrative-data.md)。

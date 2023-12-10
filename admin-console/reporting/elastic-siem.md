# Elastic SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/elastic-siem/)
{% endhint %}

Elastic 是一种可提供搜索和可观察选项的解决方案，用于监控您的 Bitwarden 组织。通过与 Elastic Bitwarden 的集成，Elastic Agent 提供了监控 `collection`、`event`、`group` 和 `policy` 信息的功能。

## 设置 <a href="#setup" id="setup"></a>

### 创建一个 Elastic 账户 <a href="#create-a-elastic-account" id="create-a-elastic-account"></a>

首先，创建一个 Elastic 账户。要通过 Elastic 的云托管服务（推荐）或内部部署服务设置仪表板以监控数据，需要执行此步骤。

### 添加 Bitwarden 集成 <a href="#add-bitwarden-integration" id="add-bitwarden-integration"></a>

监控数据需要使用 Elastic Search 和 Kibana 来可视化数据。

1、在 Elastic 主界面上，向下滚动然后找到 **Add Integrations**。

{% embed url="https://bitwarden.com/_gatsby/image/a625c675d98dc2ac464791b240de13a0/35e52b1d1ae6b8f567f061c4d4f12f29/2023-09-08_10-15-52.webp?eu=df8b59efe6ccae870d39f4d26d70343ae13c05a3ad0530d16e31e4a647a8998e25f31a0627c77bb62c6052d686e74ab96e937b3048ec84d9c5ef4bf3ef37fe5b538152ef61e02405502a95aab8f10f466dc4120aa983c100f66e74ddb1e1be7910521673ec3ef8c2e6b62a3dedd27867a9a8f56a3393e83bb5561d4a954d35e363f9ce8d7544ef98b842a8e1f1aa729c948d78470a9fb944637e25462f9752bce5d1796e312e4908339da95fc668c3e76f1c602a085b56a562398650f8643291e7aea85fc6787be3abd431799bc3a6efec1ab12b73faca25b7c2652d&a=w%3D850%26h%3D213%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.489Z" %}
添加 Elastic 集成
{% endembed %}

2、进入集成目录后，在搜索字段中输入 **Bitwarden** 然后选择 Bitwarden。

{% embed url="https://bitwarden.com/_gatsby/image/886eb47656b4d3df17bfbf7463fa5373/d8e979df780001c66022f23ae08b06b0/2023-09-08_10-21-12.webp?eu=de8852e2e1c0ff8e0668a4833926663de33d50aaaa533e856b35e2af1ba9cdd776f3180472c178b42d6b58de80b345b96ecf7f331be685dec7bb1bf7bf3cff5b05840eee60b778520528c6afbaad420128851047beda9559f43831cab6f7e1215a13496feb64e6d4a8b63226eed06968ebe0ae7322c5b47dbd4e2310885f30a524bee68c601784cdf519a59086b608999ee72f0f48d8f730207345160de528eaadb706276b20110835cffa5fc73089b43c1e623e5e561ef76f55d155e66e30dee5f9bf1d872d&a=w%3D850%26h%3D398%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.492Z" %}
Bitwarden Elastic 集成
{% endembed %}

3、选择 **Add Bitwarden** 按钮来安装集成。

4、如果这是您第一次运行 Elastic 集成，则需要安装 Elastic Agent。在以下界面上，选择 Install Elastic Agent 然后按照安装说明进行操作。

{% embed url="https://bitwarden.com/_gatsby/image/40634aca157c5f34616d3edb5c8dabb4/e6e4fa4772e717496252877322331d72/2023-09-08_10-24-05.webp?eu=db8f58e2e7cff58e5d6da7836820606de36c06abaf0231d23962eca74badca8e23a64f5d22917fe029605b88d5b110b96ecf71641ce9d08fc6b510f1b964f85e05d652e961b57053572d91fdb5f45543629e5e1ce1c0c217bc342f85b2e6f46e4a144a7aeb39edc5afb76b31f49c2870b4e5e0746494a325a71541568d1b38fd36edd187454ab5ccc816be9a9bf573cf9af87b0f4689a2312623191658bc7be8f6b103243a21135b33ccac5b963596e03b1c7e215e5d00ea6733cd55f30330c3f9f9a540d97f65a1f69e&a=w%3D850%26h%3D411%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.486Z" %}
安装 Elastic 代理
{% endembed %}

5、要运行 Bitwarden 集成，需要使用 Elastic Agent 来维护集成数据。安装完成后，Elastic 会检测安装是否成功。成功设置代理后，选择 **Add the integration**。

{% embed url="https://bitwarden.com/_gatsby/image/ce6743ea64b82be184e0f37c9e406d5a/61d7e14fc604d565a03d8d4e26ab5850/2023-11-07_11-55-35.webp?eu=dd8a05e6e2c9f4810c6fa3803975333ce23957a3f80534d53536e2fc4afa97d02da64f5772c67de72d6a598adbe84bb36497716748e8818b94ee4efce967a90d54d153bc63e62406052fcea6f4b1460662d90501fcd29f5de0732190b3e2f4334c145f35f62ffc9eebeb6b37f6d92e64e2ebe1297ac0ae3888510b35bf581bbc6ce1cc973b4598b5c95abdf9ecab0bc89bb2290641dda63325214d1d5ee92aeaa7e70772392e410964cda80ed86396b43f016022435f0498663bcd50fe7132c6fabbff0a&a=w%3D850%26h%3D392%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.481Z" %}
Elastic 设置
{% endembed %}

### 将集成连接到 Bitwarden <a href="#connect-integration-to-bitwarden" id="connect-integration-to-bitwarden"></a>

添加 Bitwarden 集成后，您将进入设置界面配置集成。在此步骤中，您需要访问组织的 API 信息。打开您的组织，导航至**设置** → **组织信息** → **查看 API 密钥**。系统会要求您重新输入主密码，以访问 API 密钥信息。

{% embed url="https://bitwarden.com/_gatsby/image/315d5b501b7ed05fa4559a26973023cc/cd1cb57dd86ba6f41cae5995f3e3dd6f/API%20key.webp?eu=d9db59e4b2cdfd8e5e6ba3826074683de13a03a9fa5034d93965b5fa47ac968470a1195522c772b67d6f5d8b85e245b360c3716811bfd1d891ba1bf4bf32ac0f5b855fbf65b52302552ac5fae4f206426dc61a09f4849c5ca16921ddb4b3b0771a551b79aa29ed81eba16067b6d7256aaef2e66d6fddb421bd430901880622b832ead39d665aadd0ee4aabf9e9eb579edabd2c514886b4323d711b67029c64faf2e74505632f253b51c8fe0f8413eda96f4860265b0e0bf733698552f83f35c3e2f2f459dc7378b2a0ca65768fc6fa87f26bcc5319bc9a6eb7c2652d&a=w%3D400%26h%3D397%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.496Z" %}
组织 API 信息
{% endembed %}

在相应字段中输入以下信息：

| Elastic 字段    | 值                                                                                                                                                  |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| URL           | <p>对于 Bitwarden 云用户，默认 URL 为 <code>https://api.bitwarden.com</code>。</p><p>对于自托管 Bitwarden 用户，请输入您的自托管 URL。确保 URL 末尾不包含任何尾部正斜杠「<code>/</code>」</p> |
| Client ID     | 输入从 Bitwarden 组织 API KEY 窗口获取的 `client_id` 值。                                                                                                      |
| Client Secret | 输入从 Bitwarden 组织 API KEY 窗口获取的 `client_secret` 值。                                                                                                  |

{% hint style="info" %}
您的组织 API 密钥信息是敏感数据。不要在不安全的位置共享这些值。
{% endhint %}

完成必填字段后，继续向下滚动页面以应用所需的数据收集设置。完成后选择 **Confirm incoming data**。

{% hint style="info" %}
此时可使用其他高级选项进行配置。上面突出显示了添加 Bitwarden 集成所需的最少字段。要在以后访问集成以编辑设置，请转至菜单然后选择 **Integrations** → **Installed integrations** → **Bitwarden** → **Integration policies**。
{% endhint %}

如果所有数据输入正确，Elastic 将确认传入的数据并提供传入数据的预览。选择 **View assets** 以监控您的数据。

### 开始监控数据 <a href="#start-monitoring-data" id="start-monitoring-data"></a>

设置完成后，您就可以开始查看您的 Bitwarden 组织数据了。选择任何一个 Bitwarden 仪表板来监控与仪表板相关的数据。以下是每个仪表板监控数据的简要概述：

| 日志                                     | 描述                                          |
| -------------------------------------- | ------------------------------------------- |
| \[Logs Bitwarden] Policy               | 查看组织的策略变更，如启用、禁用或更新组织策略。                    |
| \[Logs Bitwarden] Group and Collection | 监控与组织相关的群组和集合的记录事件。                         |
| \[Logs Bitwarden] Event                | 监控组织事件日志。在[此处](event-logs.md)了解有关事件日志的更多信息。 |

### 了解仪表板 <a href="#understanding-the-dashboards" id="understanding-the-dashboards"></a>

#### 查询 <a href="#queries" id="queries"></a>

弹性数据监控利用 Kibana 查询语言 (KQL) 来过滤数据。要了解有关查询和搜索的更多信息，请参阅 Elastic 查询文档。

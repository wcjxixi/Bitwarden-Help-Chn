# =Elastic SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/elastic-siem/)
{% endhint %}

Elastic 是一种解决方案，可以提供用于监控 Bitwarden 组织的搜索和可观察性选项。Elastic Agent 提供了通过 Elastic Bitwarden 集成监控 `collection`、`event`、`group` 和 `policy` 信息的功能。

## 设置 <a href="#setup" id="setup"></a>

### 创建一个 Elastic 账户 <a href="#create-a-elastic-account" id="create-a-elastic-account"></a>

首先，首先创建一个 Elastic 账户。为了设置仪表板以使用 Elastic 的云托管服务（推荐）或本地服务监控数据，需要执行此步骤。

### 添加 Bitwarden 集成 <a href="#add-bitwarden-integration" id="add-bitwarden-integration"></a>

监控数据需要使用 Elastic Search 和 Kibana 来可视化数据。

1、在 Elastic 主屏幕上，向下滚动并找到添加集成。

{% embed url="https://bitwarden.com/_gatsby/image/a625c675d98dc2ac464791b240de13a0/35e52b1d1ae6b8f567f061c4d4f12f29/2023-09-08_10-15-52.webp?eu=df8b59efe6ccae870d39f4d26d70343ae13c05a3ad0530d16e31e4a647a8998e25f31a0627c77bb62c6052d686e74ab96e937b3048ec84d9c5ef4bf3ef37fe5b538152ef61e02405502a95aab8f10f466dc4120aa983c100f66e74ddb1e1be7910521673ec3ef8c2e6b62a3dedd27867a9a8f56a3393e83bb5561d4a954d35e363f9ce8d7544ef98b842a8e1f1aa729c948d78470a9fb944637e25462f9752bce5d1796e312e4908339da95fc668c3e76f1c602a085b56a562398650f8643291e7aea85fc6787be3abd431799bc3a6efec1ab12b73faca25b7c2652d&a=w%3D850%26h%3D213%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.489Z" %}
添加 Elastic 集成
{% endembed %}

2、进入集成目录后，在搜索字段中输入 Bitwarden 并选择 Bitwarden。

{% embed url="https://bitwarden.com/_gatsby/image/886eb47656b4d3df17bfbf7463fa5373/d8e979df780001c66022f23ae08b06b0/2023-09-08_10-21-12.webp?eu=de8852e2e1c0ff8e0668a4833926663de33d50aaaa533e856b35e2af1ba9cdd776f3180472c178b42d6b58de80b345b96ecf7f331be685dec7bb1bf7bf3cff5b05840eee60b778520528c6afbaad420128851047beda9559f43831cab6f7e1215a13496feb64e6d4a8b63226eed06968ebe0ae7322c5b47dbd4e2310885f30a524bee68c601784cdf519a59086b608999ee72f0f48d8f730207345160de528eaadb706276b20110835cffa5fc73089b43c1e623e5e561ef76f55d155e66e30dee5f9bf1d872d&a=w%3D850%26h%3D398%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.492Z" %}
Bitwarden Elastic 集成
{% endembed %}

3、选择“添加 Bitwarden”按钮来安装集成。

4、如果这是您的第一次 Elastic 集成，您将需要安装 Elastic Agent。在以下屏幕上，选择安装 Elastic Agent 并按照安装说明进行操作。

{% embed url="https://bitwarden.com/_gatsby/image/40634aca157c5f34616d3edb5c8dabb4/e6e4fa4772e717496252877322331d72/2023-09-08_10-24-05.webp?eu=db8f58e2e7cff58e5d6da7836820606de36c06abaf0231d23962eca74badca8e23a64f5d22917fe029605b88d5b110b96ecf71641ce9d08fc6b510f1b964f85e05d652e961b57053572d91fdb5f45543629e5e1ce1c0c217bc342f85b2e6f46e4a144a7aeb39edc5afb76b31f49c2870b4e5e0746494a325a71541568d1b38fd36edd187454ab5ccc816be9a9bf573cf9af87b0f4689a2312623191658bc7be8f6b103243a21135b33ccac5b963596e03b1c7e215e5d00ea6733cd55f30330c3f9f9a540d97f65a1f69e&a=w%3D850%26h%3D411%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.486Z" %}
安装 Elastic 代理
{% endembed %}

5、为了运行 Bitwarden 集成，Elastic Agent 需要维护集成数据。安装完成后，Elastic会检测到安装成功。成功设置代理后，选择添加集成。

{% embed url="https://bitwarden.com/_gatsby/image/ce6743ea64b82be184e0f37c9e406d5a/61d7e14fc604d565a03d8d4e26ab5850/2023-11-07_11-55-35.webp?eu=dd8a05e6e2c9f4810c6fa3803975333ce23957a3f80534d53536e2fc4afa97d02da64f5772c67de72d6a598adbe84bb36497716748e8818b94ee4efce967a90d54d153bc63e62406052fcea6f4b1460662d90501fcd29f5de0732190b3e2f4334c145f35f62ffc9eebeb6b37f6d92e64e2ebe1297ac0ae3888510b35bf581bbc6ce1cc973b4598b5c95abdf9ecab0bc89bb2290641dda63325214d1d5ee92aeaa7e70772392e410964cda80ed86396b43f016022435f0498663bcd50fe7132c6fabbff0a&a=w%3D850%26h%3D392%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.481Z" %}
Elastic 设置
{% endembed %}

### 将集成连接到 Bitwarden <a href="#connect-integration-to-bitwarden" id="connect-integration-to-bitwarden"></a>

添加 Bitwarden 集成后，您将进入设置屏幕以配置集成。对于此步骤，您将需要访问您的组织 API 信息。打开您的组织并导航至设置 → 组织信息 → 查看 API 密钥。系统将要求您重新输入主密码才能访问您的 API 密钥信息。

{% embed url="https://bitwarden.com/_gatsby/image/315d5b501b7ed05fa4559a26973023cc/cd1cb57dd86ba6f41cae5995f3e3dd6f/API%20key.webp?eu=d9db59e4b2cdfd8e5e6ba3826074683de13a03a9fa5034d93965b5fa47ac968470a1195522c772b67d6f5d8b85e245b360c3716811bfd1d891ba1bf4bf32ac0f5b855fbf65b52302552ac5fae4f206426dc61a09f4849c5ca16921ddb4b3b0771a551b79aa29ed81eba16067b6d7256aaef2e66d6fddb421bd430901880622b832ead39d665aadd0ee4aabf9e9eb579edabd2c514886b4323d711b67029c64faf2e74505632f253b51c8fe0f8413eda96f4860265b0e0bf733698552f83f35c3e2f2f459dc7378b2a0ca65768fc6fa87f26bcc5319bc9a6eb7c2652d&a=w%3D400%26h%3D397%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.496Z" %}
组织 API 信息
{% endembed %}

在相应字段中输入以下信息：

|               |                                                                                                                                                                                                                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Elastic Field | Value                                                                                                                                                                                                                                                                           |
| URL           | <p>For Bitwarden cloud users, the default url will be . <code>https://api.bitwarden.com</code></p><p>For self-hosted Bitwarden users, input your self-hosted URL. Be sure that the URL does not include any trailing forward slashes at the end of the URL "<code>/</code>"</p> |
| Client ID     | Input the value for from the Bitwarden organization API KEY window. `client_id`                                                                                                                                                                                                 |
| Client Secret | Input the value for from the Bitwarden organization API KEY window.`client_secret`                                                                                                                                                                                              |

{% hint style="info" %}
您的组织 API 密钥信息是敏感数据。不要在不安全的位置共享这些值。
{% endhint %}

完成必填字段后，继续向下滚动页面以应用所需的数据收集设置。完成后选择确认传入数据。

{% hint style="info" %}
此时可使用其他高级选项进行配置。上面突出显示了添加 Bitwarden 集成所需的最少字段。要稍后访问集成以编辑设置，请转至菜单并选择集成 → 已安装的集成 → Bitwarden → 集成策略。
{% endhint %}

如果所有数据输入正确，Elastic 将确认传入数据并提供传入数据的预览。选择查看资产以监控您的数据。

### 开始监控数据 <a href="#start-monitoring-data" id="start-monitoring-data"></a>

设置完成后，您可以开始查看您的 Bitwarden 组织数据。选择任何 Bitwarden 仪表板来监控与仪表板相关的数据。以下是每个仪表板监控数据的简要概述：

|                                        |                                                                                                                |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Log                                    | Description                                                                                                    |
| \[Logs Bitwarden] Policy               | Review policy changes for an organization such as enabling, disabling, or updating organizational policies.    |
| \[Logs Bitwarden] Group and Collection | Monitor recorded event for groups and collections related to the organization.                                 |
| \[Logs Bitwarden] Event                | Monitor organizational event logs. Learn more about event logs [here](https://bitwarden.com/help/event-logs/). |

### 了解仪表板 <a href="#understanding-the-dashboards" id="understanding-the-dashboards"></a>

#### 查询 <a href="#queries" id="queries"></a>

弹性数据监控利用 Kibana 查询语言 (KQL) 来过滤数据。要了解有关查询和搜索的更多信息，请参阅 Elastic 查询文档。

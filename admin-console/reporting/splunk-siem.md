# Splunk SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/splunk-siem/)
{% endhint %}

Splunk Enterprise 是一个安全信息和事件管理 (SIEM) 平台，可与 Bitwarden 组织一起使用。组织可以在 Splunk Enterprise 仪表板上监埪 Bitwarden 应用程序的[事件](event-logs.md)活动。

{% hint style="info" %}
**本地 Splunk Enterprise** 目前支持 Bitwarden Splunk 集成。
{% endhint %}

## 设置 <a href="#setup" id="setup"></a>

### 创建 Splunk 账户 <a href="#create-a-splunk-account" id="create-a-splunk-account"></a>

在 Splunk Enterprise 上安装 Bitwarden 应用程序要求 [Splunk Base](https://www.splunk.com/en\_us/sign-up.html) 账户。

### 安装 Splunk <a href="#install-splunk" id="install-splunk"></a>

拥有 Splunk Base 账户后，下一步就是安装 Splunk Enterprise。按照 [Splunk 文档](https://docs.splunk.com/Documentation/Splunk/9.0.4/SearchTutorial/InstallSplunk)完成自托管企业软件的安装。

{% hint style="info" %}
Bitwarden 应用目前在 Splunk Enterprise 的 Linux x64 架构上受支持。
{% endhint %}

### 创建索引 <a href="#create-an-index" id="create-an-index"></a>

在将您的 Bitwarden 组织连接到 Splunk Enterprise 之前，需要先创建索引来维护 Bitwarden 数据。

1、打开位于顶部导航栏上的 **Settings** 菜单，然后选择 **Indexes**。

2、进入索引界面后，选择 **New Index**。

3、将出现一个供您为 Bitwarden 应用程序创建新索引的窗口。

{% embed url="https://bitwarden.com/_gatsby/image/b504c8836a0052414f9d7fc9b17fba02/c3537e6693e1452f2fe92addd8ff18c3/image.webp?eu=da8605b0ebcea9800668a9813d23673db33651f8ab5132d66c67e7ab4bafcfd420f31f06299d2cb8796e0f8881b647eb6f947f681fbdd7d8c8ed1fa2be3daa0d06855dbd33e12300587ec1feb4f20c1d2c825a1bab9cd751fe3c2581a6ade4344f015f68fd3efb9fb2fc717bb7c17161aceca7786d9fec7fff145b07b0450ea403dbc38d4918ed88b8588b87bacf5bd2cdb52e0f498af73176231e185de42dbea2e407276c7c150d649caf5f916796e523453c72090a1db7396d&a=w%3D816%26h%3D993%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.422Z" %}
Splunk 索引
{% endembed %}

4、在 **Index Name** 字段中，输入 `bitwarden_events`。

{% hint style="info" %}
创建索引唯一需要的字段是 **Index Name**。其余字段可以根据需要进行调整。
{% endhint %}

5、完成后，选择 **Save**。

### 安装 Splunk Enterprise Bitwarden 应用程序 <a href="#install-the-splunk-enterprise-bitwarden-app" id="install-the-splunk-enterprise-bitwarden-app"></a>

创建 Bitwarden 索引后，导航到 Splunk Enterprise 仪表板。

1、选择 **Apps** 旁边的 **⚙️**齿轮图标。

{% embed url="https://bitwarden.com/_gatsby/image/ad02977ff33b97a4cdedd14fc71bc58d/520f908a5350182f3069b47fbf6ad3a6/Screenshot%202023-03-23%20at%204.05.24%20PM.webp?eu=ddd851eee79bf9840e6da4d03c716668b36a54a2fb5337813e31edac1da1ccd372a51f5173c772e22d6a59ded7b344bf32c471671ce983d893bd4af4be67a801018b0beb31b423015b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b9572690d37bbf4d5722a2472ca464c2ceaa6978a98aaf1ee6e7ebf8019c95b4240240d9a23422704d4a0de82cbfa7b603206b29135830d1cc0b8534c3e87f443e67315d03f56427d056e66e32acb5bfce59c77a7effaacd5e10fbddeedeba&a=w%3D850%26h%3D390%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.461Z" %}
Splunk 应用仪表板
{% endembed %}

2、选择位于屏幕右上角的 **Browse more apps**。

{% embed url="https://bitwarden.com/_gatsby/image/bf8bf4a8baa29cda0a6c6caa8574a472/2e927d37ec748e42c6890199db51d03e/Screenshot%202023-04-13%20at%202.07.55%20PM%20(2).webp?eu=d78d01efb0c0ae815b6ca984607a336ab53701abad5734d46b36b5ab1aabcf8221fa1e5d76912cb57e600edad3e210bc62c07a6311e7d4d2c2e818fced33a35d57d05fed66b07352042f92aae5f307476dc51000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41f2fb426c4c79a7358b6c6d368bea084f55599e19c6e18488fa26326211d490bed7beaf3b152796f7b415835caae589330c4e33e1b3571413c50b5326f8e16a33375ace6fba35ec47a7ffca9ca5e21c2acac9eed1db22f7388af5ac6ed3915104df244&a=w%3D850%26h%3D162%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.445Z" %}
Splunk 浏览所有应用程序
{% endembed %}

3、在应用程序目录中搜索 **Bitwarden Event Logs**。为 **Bitwarden Event Logs - Linux x64** 应用程序选择 **Install**。

{% embed url="https://bitwarden.com/_gatsby/image/b5a6f101127d38fed1016c6b89f87819/bba51ee77d44fe0879cc389c61c8dee6/Screenshot%202023-04-25%20at%203.45.18%20PM%20(2).webp?eu=dfdd54e3e5ceafd45c6ef2d56821633fb36b55acaa5331853c36b5af1ca9cb8327a1180624922bb6796d5ad6dae314eb60c47e371abdd48bc6b44dfdeb63ab095ad608ef36e17856042fcea6f4b1460662d90501fcd29f5de0732190b3e2f4334c145f35f62ffc9eebeb6b37f6d92e64e2ebe1297ac7d23282562a038b512a8e04d192df427b9490f84d95f9bfae0dc9c8e17b01128ff6312a26444d58e479efa1b00c24312d465b60cfa60ed802c5f469493f6006004798653ad256e66c35dee6fece0c9d1578ffaccc2f718eaccefd8275ae4568a79170&a=w%3D350%26h%3D119%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.396Z" %}
Bitwarden 事件日志应用程序
{% endembed %}

4、为了完成安装，您需要输入您的 [Splunk Base](https://splunkbase.splunk.com/) 账户。您的 Splunk Base 账户可能与用于登录自托管 Splunk Enterprise 实例的凭据不同。

{% embed url="https://bitwarden.com/_gatsby/image/561cfd31fd83d56a2ce96f63f9d7194a/07e4afd0081b5cdef815dbbbb5c63177/Screenshot%202023-03-23%20at%204.08.07%20PM.webp?eu=8e8d54e1e39ef985083da1d53a24336ae13b51faa85132d73b61e6ab1eab9ad270a51a5c29937db02e3d5addd6b614be6ec47a6010ed82d893bb4af4b866fc0855815dbc67b175075929c2abb6f70e1761c11c0ca5859e5af73b7087b6b4b47110534a7fab2fbd81e6f17120f0c0252df5effb7f3297e866b3560805885b24b827a5ce8b7701e98cee4ca9bcefff0190dbe032063b84f36047323e555a9c44c2fab25f0f7c61340454d1fe59c1669ee76f4d6375565900f46239d752f86f62c7b1fdf55d8c7228e8f9c12e13d581fbd5b359f4753288cd27ab81267a0d10ae10c2ed3f98d67a06069f2afdfa2ccf1d456b17&a=w%3D600%26h%3D663%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.346Z" %}
在 Splunk 上登录并安装 Bitwarden 应用程序
{% endembed %}

5、输入信息后，选择 **Agree and Install**。

{% hint style="info" %}
安装 Bitwarden 应用程序后，您可能需要重新启动 Splunk。
{% endhint %}

### 连接您的 Bitwarden 组织 <a href="#connect-your-bitwarden-organization" id="connect-your-bitwarden-organization"></a>

在您的 Splunk Enterprise 实例中安装 Bitwarden 事件日志应用程序后，您可以使用 Bitwarden [API 密钥](../../organizations/bitwarden-public-api.md#authentication)连接您的 Bitwarden 组织。

1、转到仪表板主页然后选择 **Bitwarden Event Logs** 应用程序。

{% embed url="https://bitwarden.com/_gatsby/image/d84d8916c6fdb1836dbd85fb6081d085/8f0cd05d807e8c95144a155c328bf8f7/Screenshot%202023-03-24%20at%201.27.20%20PM%20(2).webp?eu=d8da54efb1c0f9d30869a2826970663fe73a57feaa043e856f63e4a748ac9ad277f74d5472952fe02e3d53dcd0e546e835c72b3318eb81df91b510f1b934a2595bd650b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af874744aff1e1723f82d92fbc4d195cbc5b209500e8f0c1311eebc6b949b9b4b8a10d9994e17e5612d3f0607025484e58ed7bbff7b40779264a1319609bf11b9f3ed2d93e1c6320435f00ea653ebf04bf0330dde6fcbf5fd9151b9cc7a6331f9883f0d7&a=w%3D850%26h%3D300%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.382Z" %}
Splunk 仪表板上的 Bitwarden
{% endembed %}

2、接下来从顶部导航菜单中选择 **Setup**。这里是您添加 Bitwarden 组织信息的地方。

{% embed url="https://bitwarden.com/_gatsby/image/7b91c9b6433add070566257168f62557/873687b79630e2547cdcae6eaf34d543/Screenshot%202023-03-23%20at%204.13.05%20PM.webp?eu=8d8f57e2e1c8afd20d3ef3d56176363de1395ef8fe5260d33f32ecfd48ac968422f44b5c73922fe72c600cdd81e247b3369329341cec8389c1bc4afce236ab0d05d650b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af877c32eab6ae5c6298cf1ea0123e358f5878fb24bbc8c16648efc8b449e6b5bda80ccc9aee7b0f1389f0362570481c5bee2feff7b20c77264a1319609bf11b9f3ed2d93e1c6320435f00ea6539bf04bf0335dde5f8bf5ddc151b9cb6896f27&a=w%3D600%26h%3D558%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.373Z" %}
设置 Bitwarden 菜单
{% endembed %}

3、保持此界面打开，在另一个选项卡上，访问您的 Bitwarden 网页密码库。打开您的组织并导航到**设置**、**组织信息**然后**查看 API 密钥**。您将被要求重新输入您的主密码以访问您的 API 密钥信息。

{% embed url="https://bitwarden.com/_gatsby/image/315d5b501b7ed05fa4559a26973023cc/cd1cb57dd86ba6f41cae5995f3e3dd6f/API%20key.webp?eu=8a8d58b3e09bfcd30960a2806b27646db43b5efdad0762d83d67b5ae4aac9a802ca5185628c079b37f3f52d682e342e96fc770611aebd0d8c9bc1da1e233ae5905d00fee32b12103057ac5fde1f6534669901000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41e26843ecad99f644bafbaea198a868aaf589adf955618138ff2302726441f0cbe78bca6e100713f20155f30c7ac0bcf62c2b035193524412e638e0861851ce52c6f94&a=w%3D400%26h%3D397%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.429Z" %}
组织 api 信息
{% endembed %}

4、将 `client_id` 和 `client_secret` 值复制并粘贴到 Splunk 设置页面上的相应位置。

按如下方式完成附加字段：

| 字段         | 值                                                                                                                                      |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Index      | 选择之前在指南中创建的索引：`bitwarden_events`。                                                                                                      |
| Server URL | <p>对于自托管 Bitwarden 用户，请输入您的自托管 URL。请确保该 URL 在末尾不包含正斜杠 「<code>/</code>」。<br><br>对于云托管组织，请使用 URL <code>https://bitwarden.com</code>。</p> |

{% hint style="danger" %}
组织 API 密钥拥有对您的组织的所有访问权限。确保您的 API 密钥的私密。如果您认为您的 API 密钥已被泄露，请选择此姐买你上的**轮换 API 密钥**按钮。当前 API 密钥的活动实施在使用前需要使用新密钥重新配置。
{% endhint %}

5、选择 **Submit**。

6、完成设置后，请转到 **Settings** → **Server controls** → **Restart Splunk**，重新启动 Splunk Enterprise。

### 使用搜索宏开始监控数据 <a href="#start-monitoring-data-with-a-search-macro" id="start-monitoring-data-with-a-search-macro"></a>

要开始查看数据，您可以设置搜索宏。Splunk 搜索宏是可重复使用的搜索查询，可应用于您的仪表板。

1、要添加搜索宏，请转到顶部导航栏上的 **Settings**。然后，选择 **Advanced Search**。

{% embed url="https://bitwarden.com/_gatsby/image/c7d9dc1fa717803f3f90f1768c63807c/d8c0d241072dfd6de87bfadae8dcf374/Screenshot%202023-03-28%20at%209.12.33%20AM%20(2).webp?eu=d98f59e0e19afd810760a4863e71683db33801a2f85632d86c63e1aa1ca9cd8670f51f55739c79b12b3c08db86b44bef32c72e344fbb85d8c6ed19f3eb36fe015ad052ee67b2760f582ec7ade6f255446bce1c58a981c808a9353690a5f0bd6f0609417aff2ffb9fbfed6335f3c07a76a9a8f87b21ddac3abe41180eca4e79a123bc8fdc767486cfcc1cef908ca148b6c8e1246137dcba4043684b170aea2fbef0e400203a2b485c31c8a90a9334c5b4694e68770f5851ff6f3dcf36a82e6496bab8f9029d1579e1aaca2c7085deac88824be8457ff9ce25b78138157f70c37cafd365b78c33&a=w%3D850%26h%3D155%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.358Z" %}
创建 Splunk 搜索宏
{% endembed %}

2、接下来，选择 ✚**Add new**。进入创建宏屏界面后，请填写以下字段：

| 字段                       | 定义                                                                                                                                                              |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Destination app          | 将应用此宏的应用程序。 Bitwarden 目标应用程序是 `bitwarden_event_logs`。                                                                                                           |
| Name                     | 宏的名称。您正在使用的宏采用附加到宏名称的参数。 Bitwarden 的宏名称是 `bitwarden_event_logs_index`。                                                                                          |
| Definition               | <p>该字段将包含搜索宏在搜索中引用时扩展的字符串。包含的参数将用美元符号括起来，例如 $arg$。</p><p>输入 <code>index=*</code> 以在宏中进行广泛搜索。搜索中需要通配符 <code>*</code>。可以在宏设置之后从<strong>搜索</strong>功能执行更具体的查询。</p> |
| Arguments                | <p>在以逗号分隔的参数名称字符串中输入参数。参数名称只能包含字母数字、「_」和「-」字符。</p><p><strong>创建宏不需要此字段。</strong></p>                                                                            |
| Validation Expression    | <p>输入运行宏参数的 eval 或布尔表达式。<br><strong>创建宏不需要此字段。</strong></p>                                                                                                     |
| Validation Error Message | <p>输入验证表达式返回 <code>false</code> 时要显示的消息。<br><strong>创建宏不需要此字段。</strong></p>                                                                                     |

3、将所有信息输入宏字段后，选择 **Save**。

### 搜索宏权限 <a href="#search-macro-permissions" id="search-macro-permissions"></a>

接下来，设置哪些用户角色有权使用宏：

1、通过选择 **Settings** → **Advanced Search** → **Search macros** 来查看宏。

{% embed url="https://bitwarden.com/_gatsby/image/71ae0b519db5c68ec3dfcc1f2e256401/f59301796013eaec748a37f6adf36665/Screenshot%202023-03-28%20at%204.22.43%20PM%20(2).webp?eu=d98f53e0e59aa881076af6d53e203168e63c05a2f65564d23f64b0fa46ac998027f61103259d2fb67f3a0ed887e446bd63cf78354cec86d9c2bf1fa2ec3cff0b53d60fbf63ba7706072b97fdb0f206166094190bf583c10ea33c26dcecb0b2261006482bac79bf85efac3564b0d62b36edb3f4783497af7aea4a1a108b5b7be37be2cd8f644badd0e35bb9b7adea5c89dff9735204c4f4777c240a4559bb25e6e2b51b773b5424317cafce19b11cd0de3f413f4016564b9d0325d403ae6d3497b0faa65fda722eb4a89b36768796a6d5b91ea42c72b6ce72aad124195d4ff946f3ff23a8960b040e8329e7954faf010d5a11c6738d3a22db265b8f68e49c28fc2a9370666866&a=w%3D850%26h%3D404%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.416Z" %}
Splunk 宏访问权限
{% endembed %}

2、在要编辑的宏上选择 **Permissions**。

{% embed url="https://bitwarden.com/_gatsby/image/b1a51a05157acd8c09bfb03af5858257/a1fa57b19f119128f67208718102a414/Screenshot%202023-03-28%20at%204.32.41%20PM%20(2).webp?eu=d88a52e7e2c9ffd50a6da9d53c24363fb63750adad0230866c35b7ad1cadca8226a24d5d289078e3243a5cdcdae745e8629370614be6848c91be4da0ed34ac5b50d10fea32bb7054072ac3fcb4f5504d61c5195fa58aca59ab3f71d3e6b6b5224a55152aa92cee82bea93137b0d12861bbb5a3266f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32b8f1d55a104a5f245b7d89f32c9b3ac7fc5b5c61541a4056a2653cd355f36837c2e7f3a10ed97e2fb3adcc38238f96ff85ef4fad7827b3d044fac06e2f504ef44ce9d379f7d0671b0e8237f89d23e3476a315e811e972021b65822e368868e59d376ab&a=w%3D450%26h%3D248%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.366Z" %}
Splunk 宏权限
{% endembed %}

3、编辑以下权限：

| 字段                      | 描述                                                              |
| ----------------------- | --------------------------------------------------------------- |
| Object should appear in | 要在事件搜索中使用宏，请选择 **This app only**。如果选择了 **Keep private**，宏将不会应用。 |
| Permissions             | 为具有**读取**和**写入**访问权限的用户角色选择所需的权限。                               |

4、编辑所需权限后，选择 **Save**。

{% hint style="info" %}
在给定时间，只有一个搜索宏可以在应用程序上运行。
{% endhint %}

## 了解仪表板 <a href="#understanding-the-dashboards" id="understanding-the-dashboards"></a>

仪表板将提供多个用于监控和可视化 Bitwarden 组织数据的选项。数据监控的三个主要类别包括：

* Bitwarden 身份验证事件
* Bitwarden 密码库项目事件
* Bitwarden 组织事件

仪表板上显示的数据将为各种搜索提供信息和可视化。可以通过选择仪表板顶部的 **Search** 选项卡来完成更复杂的查询。

### 时间范围 <a href="#timeframe" id="timeframe"></a>

从 **Search** 页面或 **Dashboards** 进行搜索时，可以将搜索指定为特定的时间范围。

{% embed url="https://bitwarden.com/_gatsby/image/661504e62f418a403c8e56d2604caf0f/443e70b244e110e4962a249995637452/Screenshot%202023-04-13%20at%203.24.28%20PM%20(2).webp?eu=d7dc05b3e5caf5d15d39a78b3920323db23b04f9a85663d13960b5fd4cfc9d8172f51c5476977bb879605fdc80b311e960c72d6448bcd3db96e949fdbf66f85b538108b832b72506052c90f8b5a4571168971a5ea3d19d0cf03e26ddede6be224f061e2aa222fcc5acea3f7bafda7263bde3e5303686fd29a3510b1088062fa920a4979c6d4da894b149e7bba9ae1687c5ad494408818048592b381b3c8551e6fcb0611b2628155264c8fd0cc160c2bf3d196227595b03f2363c8204f33d3492b1a8a55d886518b2ea9c642ec59bf1c48218ac2875facf23b48338155f49c310b3be7fe9d06c696efc45959723ac435b62&a=w%3D687%26h%3D557%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.470Z" %}
Splunk 时间范围搜索
{% endembed %}

Bitwarden 事件日志搜索支持以下时间范围：

* Month to date
* Year to date
* Previous week
* Previous business week
* Previous month
* Previous year
* Last 30 days
* All time

## 查询参数 <a href="#query-parameters" id="query-parameters"></a>

通过包含搜索查询来设置特定搜索。Spunk 利用其搜索处理语言 (SPL) 方式进行搜索。有关搜索的更多详细信息，请参阅 [Splunk 文档](https://docs.splunk.com/Documentation/Splunk/9.0.4/Search/GetstartedwithSearch)。

**搜索的结构**：

```
search | commands1 arguments1 | commands2 arguments2 | ...
```

标准搜索结果对象的示例：

{% embed url="https://bitwarden.com/_gatsby/image/b0dc490428336e1c22c23898ec5c53c0/7b6ddbd28c872b817094089b57feaa32/query%20data.webp?eu=d88f52efe3ccfdd55b3ef6d06d7a6260b16a50a8ab5934d23a60b1fc4afbcc8476f64d54719278b32b6d0c88d1e643b364927d3048e6d7da96ef19f1be3caf5b07815eba35b27007502892fbb5fd001668c11b51abdb8c4ce32e78cbfaeaea214e055f35fb3eeed0afea6020f39d7167aea9a16c3b91ed22e14456098c1f6efa66bbead9621fe99bd878b7bdb9f27ab2d6a7744f25c4a23227261f4a0eeb2dbca1e155723978405a31c6ae59c46795e56e1f6770560e1cb6226f921c94386087b5e5e1038e&a=w%3D500%26h%3D117%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.403Z" %}
Splunk 搜索结果对象
{% endembed %}

标准搜索对象中显示的字段可以包含在任何特定搜索中。包括以下所有值：

| 值                 | 示例结果                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `actingUserEmail` | 执行操作的用户的电子邮件。                                                                                                             |
| `actingUserId`    | 执行操作的用户的唯一 ID。                                                                                                            |
| `actingUserName`  | 执行操作的用户的名称。                                                                                                               |
| `date`            | 以 `YYYY-MM-DD TT:TT:TT` 格式显示的事件日期。                                                                                        |
| `device`          | 用于标识执行操作的设备的数字。                                                                                                           |
| `hash`            | Splunk 计算的数据哈希。在[此处](https://docs.splunk.com/Documentation/Splunk/9.0.4/Security/Dataintegritycontrol)详细了解 Splunk 的数据完整性。 |
| `ipAddress`       | 执行事件的 IP 地址。                                                                                                              |
| `memberEmail`     | 操作针对的组织成员的电子邮件。                                                                                                           |
| `memberId`        | 操作针对的组织成员的唯一 ID。                                                                                                          |
| `memberName`      | 操作针对的组织成员的名称。                                                                                                             |
| `type`            | 表示发生的组织事件的事件类型代码。在[此处](event-logs.md)查看完整的事件代码列表和说明。                                                                      |

**搜索所有**：

```
sourcetype="bitwarden:events" type=*
```

**按特定字段过滤结果**：

在以下示例中，搜索正在查找带有 `*` 通配符的 `actingUserName`，这将显示所有带有 `actingUserName` 的结果。

```
sourcetype="bitwarden:events" actingUserName=*Text 
```

**AND 运算符**隐含在 Splunk 搜索中。以下查询将搜索包含 `type` 类型和 `actingUserName` 的结果。

```
sourcetype="bitwarden:events" type=1000 actingUserName="John Doe"
```

通过使用 `|` 分隔符来包含多个命令。以下将显示最高值为 `ipAddress` 的结果。

```
sourcetype="bitwarden:events" type=1115 actingUserName="John Doe" | top ipAddress
```

## 附加资源 <a href="#additional-resources" id="additional-resources"></a>

### 设置用户角色 <a href="#set-user-roles" id="set-user-roles"></a>

管理用户角色以允许个人执行特定任务。要编辑用户角色：

1. 打开顶部导航栏上的 **Settings** 菜单。
2. 从菜单右下角选择 **Users**。
3. 在用户界面，找到您要为其编辑权限的用户并选择 **Edit**。

{% embed url="https://bitwarden.com/_gatsby/image/d6876931b415646afcd841fad11c388c/2ae999effaef555b74dc063772dba4f4/Screenshot%202023-04-13%20at%209.48.48%20AM%20(2).webp?eu=d78a58b3e09aa98f0869a1833d746469b33e02feaf5964d53b31e0fe48ab998520f61154769629e728680bd9d7b310eb36cf2d3719ecd4d896ba1ff1ef33ac0d50d05eec61b37603552ec6f9baad420128851047beda9559f43831cab6f7e1215a13496feb64e6d4a8b63226eed06968ebe0ae7322c5b47d934c3a1e8c5829bd02eece8f515be8cdb85a89b997b608c89db22f0e458aa13477774a4909b928b8a3bb0c233f2d480a669df95dc76189d56f5e3476001c5ba82355d255f96f2cc3e0e6a05eb62b3f8ea1d7357898c7a6ef9c67c3457488d167f7d5&a=w%3D450%26h%3D488%26fm%3Dwebp%26q%3D75&cd=2023-04-26T11%3A56%3A43.390Z" %}
Splunk 编辑用户权限
{% endembed %}

在此界面，可以填写用户的详细信息。`admin`、`power` 以及 `can_delete` 等权限也可以在此处单独分配。

### 删除数据 <a href="#delete-data" id="delete-data"></a>

通过使用 SSH 访问清除索引来删除 Bitwarden 搜索数据。在更改被监视的组织等实例中可能需要清除数据。

1. 访问 Splunk 目录然后 `stop` Splunk 进程。
2. 使用 `-index` 标志清除 `bitwarden_events` 索引。
3. 重新启动 Splunk 进程。

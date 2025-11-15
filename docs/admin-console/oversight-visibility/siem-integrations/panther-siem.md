# Panther SIEM

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/panther-siem/)
{% endhint %}

Panther 是一个安全信息和事件管理 (SIEM) 平台，可与 Bitwarden 组织一起使用。组织用户可以使用 Panther 监控系统上的 Bitwarden App 监控[事件](../event-logging/event-logs.md)活动。

## 设置 <a href="#setup" id="setup"></a>

### 创建一个 Panther 账户 <a href="#create-a-panther-account" id="create-a-panther-account"></a>

首先，您需要一个 Panther 账户和仪表板。在他们的[网站](https://panther.com/)上创建一个 Panther 账户。

### 初始化 Panther Bitwarden 日志源 <a href="#initialize-panther-bitwarden-log-source" id="initialize-panther-bitwarden-log-source"></a>

1、访问 Panther 仪表板。

2、在菜单上，打开 **Configure** 下拉列表然后选择 **Log Sources**。

{% embed url="https://bitwarden.com/_gatsby/image/3689678b2f13ecd6f8e4d52596f2d839/355ae2215cf9cf1c799a8f9d4077210c/Panther%20Log%20sources.webp?eu=dbdf55b7e3c9aad40d6ba1873b756661e43704a9f85532d6396db6a748a0998075f44f00259579b978385dda85e011b834977b614dbfd8dc91be10f1e367aa5b5ad65fe967b07a5f156f84bdbaea191c35974d0de29d9b4cf53c3197b0f7f46e47055834af38e6d2aaf33432b8de6835f5b4cc5b60c5ef00b35b5653ad18308e1fe9f597687c91d1e31fbdb0e8a15fccc8b62a0313d3fa3327714e4950ea7cb3a0bb0171382a48082aaefe068339c3f453603e74311c5cb225698516e52c6f94&a=w%3D289%26h%3D500%26fm%3Dwebp%26q%3D75&cd=2023-07-27T21%3A13%3A09.611Z" %}
Panther 日志源
{% endembed %}

3、选择 **Onboard your logs**。

{% embed url="https://bitwarden.com/_gatsby/image/32d1383c4bd0b796fd58f67bc9348a8b/b0a95e30dca9e0b43e12c10499df5e09/Panther%20integration%20marketplace.webp?eu=8c8f01e0e4c8f8815d68a5d269266938b56c06f9fa0530d03f37b2aa4bfa9e8470f34c5424902ee4246d59dedbb247bd36c67f3419e6d1dbc7bd4aa7e867f95c54d758ba34b57807582accfee5f6074239cf1c5ef0d79e0cf26924d7e2b4b77011521a2cfa7cb8d0bdaa3266e4802c36e0eee26a2581a167ff4b03059c4d32e237ffc68f705dbb8af301b1b3aab60e8fc2b46b5d418dfb686570531b05b87bdff4b543064043462066c8ad259168c9c8790330715e5b00a4363fd457fb6f37c3edfda759de7c7eb3fb9a317185c1af85e54eb34a27b98b7ffcc054235049f944efed3fae8d3a6953d068a1c008f25f5466159c5cd773&a=w%3D850%26h%3D621%26fm%3Dwebp%26q%3D75&cd=2023-07-27T21%3A13%3A09.624Z" %}
Panther 载入日志
{% endembed %}

4、在目录中搜索 **Bitwarden**。

{% embed url="https://bitwarden.com/_gatsby/image/52821ccb79a99003e3fe18011c0da187/4af4e8ed1673967d8b7daae7cd91fa52/bitwarden%20app.webp?eu=dc8e59e7b79df88e5c3ca7823e75356fb13904adfc0431d83e35e3ac1ea89d802df54b0121952eb67a695f8ad2e44ae864c22c601ebbd08f96ef1ff2ec30fe0d57d15bba60e0740f052b92f7b0f657436a92135bf58ac800a0687580b6e2e6244a011d22a178eed7b9ff3630e6d52f37e0eee26a2581a167ff4b03059c4d32e237ffc68f705dbb8af301b1b3aab60e8fc2b46b5d418dfb686570531c1b8e53fdc0c445264721141c40a9ed0e9261f3c04103372a0d5e07f0646fd154f83f38cbe1faf258d97c7ce3a8c03872d295fbd6ef4bb3782fa38876ebd66e24615cec53b3fc25a0&a=w%3D850%26h%3D449%26fm%3Dwebp%26q%3D75&cd=2023-07-27T21%3A13%3A09.622Z" %}
Bitwarden 日志集成
{% endembed %}

5、单击 **Bitwarden** 集成然后选择 **Start Setup**。

### 连接您的 Bitwarden 组织 <a href="#connect-your-bitwarden-organization" id="connect-your-bitwarden-organization"></a>

选择 **Start Setup** 后，将进入配置界面。

{% hint style="info" %}
Panther SIEM 服务仅适用于 Bitwarden 云托管组织。
{% endhint %}

1、输入集成的名称，然后选择 **Setup**。

2、接下来，您必须访问 Bitwarden 组织的**客户端 ID** 和**客户端密钥**。保持此界面打开，在另一个选项卡上访问您的 Bitwarden 网络密码库。打开您的组织，导航至**设置** → **组织信息** → **查看 API 密钥**。系统会要求您重新输入主密码，以访问 API 密钥信息。

{% embed url="https://bitwarden.com/_gatsby/image/315d5b501b7ed05fa4559a26973023cc/cd1cb57dd86ba6f41cae5995f3e3dd6f/API%20key.webp?eu=de8957efe69afd805b68a8826124646ab23b50a2fd5835d6686db6aa47fe988f70a11d5472c47de3286f53d780b640bd67947d341fecd5df96bd10f0ee63ac09558053e633e124515b7380baf0b60c5a779f4709f6d68b16f0292485a6f0e2345a4e427eec65bfc3b2fa733eb1d5276fadb1b92832baf109a95309018a6c2bfa01dbf4d86249adbccb00bcb2efac0c9c94e7795415dcf06626774a160de928b2a6e10c726d2f495e61c9b029a718f9ed69557f630008&a=w%3D400%26h%3D397%26fm%3Dwebp%26q%3D75&cd=2023-12-06T13%3A28%3A13.496Z" %}
组织 API 信息
{% endembed %}

3、将 `client_id` 和 `client_secret` 值复制并粘贴到 Bitwarden 应用程序设置页面上各自的位置。输入信息后，再次选择 **Setup** 以继续。

4、Panther 将对集成进行测试。成功完成测试后，您将可以选择调整偏好。按下 **View Log Source** 完成设置。

{% hint style="info" %}
在 Bitwarden 应用程序设置完成后，Panther 可能需要长达 10 分钟的时间来提取数据。
{% endhint %}

### 开始监控数据 <a href="#start-monitoring-data" id="start-monitoring-data"></a>

1、要开始监控数据，请转到主仪表板然后选择 **🔍Investigate** 和 **Data Explorer**。

2、在 **Data Explorer**（数据资源管理器）页面上，从下拉菜单中选择 `panther_logs.public` 数据库。确保 `bitwarden_events` 也可见。

{% embed url="https://bitwarden.com/_gatsby/image/4ad05fcf985ed62b1b690b915110dcf0/e3cd471c67058ca74c0b7762f0c2334e/data%20explorer.webp?eu=d8df50e1e699f5870839a4d06a75366ce33f50acfb053fd73f31eca949fb99832da0185774917eb7796c0c8fd7b516bd67c329371ce7d4d291bb18a2b830a25b50800fbf6deb34431168cee1afac5b143f935946f2c79e59e02e2790a6ade9255d4f1b69f629fedbedff3d39f7843031b7f4e66d0d8af311884b3e2c891d238d20b9e4886801e7cdb119b9e0e6fc5d999be6240641d3f3342573441951b92ebca7b400763c2b5f0f648afe379229d6ea635e3461401f5da0&a=w%3D850%26h%3D525%26fm%3Dwebp%26q%3D75&cd=2023-07-27T21%3A13%3A09.619Z" %}
Panther Data Explorer
{% endembed %}

3、完成所有必需的选择后，选择 **Run Query**。

您还也可以 **Save as** 以便下次使用此查询。

4、屏幕底部将生成 Bitwarden 事件列表。

{% embed url="https://bitwarden.com/_gatsby/image/58a006305366b7719072b1b2d7456359/14462549b504432f8d9963b56575d8a5/Panther%20event%20logs.webp?eu=d6df01b7e2cff9875d3ea8843a74326bb46a5fabab5134833a64ecfc1bad968171a61a0621c17ae4793d53dad0e914ba31972c3711b8d08cc7e81ff4b83dfc0955840bec63b575005578cdadb5a1501469c71f0ea585c00ba46d7682efebf33459131634b723e5d0bbfc767ae3c77963a9f5f36a26dcf52da40d5916954b37a665ed98837419f1cde956a6efbdf17ba4c9b96f473adeab46651137600cf22eb3a0e703253c2a445333ccae0ac03293be3a1868755e5900f5313bd95da96e2ea3b5a5e5058c3814b4ee9c6f34e99ff1d7ae04ec7421&a=w%3D850%26h%3D334%26fm%3Dwebp%26q%3D75&cd=2023-07-27T21%3A13%3A09.615Z" %}
Panther  事件日志
{% endembed %}

5、通过选择 **View JSON**，可以以 JSON 格式展开和查看事件。

{% embed url="https://bitwarden.com/_gatsby/image/84911113846d3d7e1aa3ae43eb06295f/7251308761e74779823900edfa7cc202/Panther%20JSON%20Object.webp?eu=d78751eeb29dafd2593ea4836976683fe43d54f8f95167d63931ecab47fe9d8576a14850299d7cb62e3b5cd9d2b544b864cf7e3219bb838ec4b81fa6eb31ff0f078b58bc33e22406032b92ade1f057176bc11909a380c05bf7647282b1e2bd285d145c68a265a7d8b1f86231f39d7c76bce7e56d3086e866be471a4bcc5a2faf22e191883b43a9c9af1ea89e9afc088ec29157033ea9f24223742a6d3d9f5ea4a6b30675312c445f61caac5a946295e53d143726580a04a1353cd855fb393192fb9bf0039d222ea3c7b3520ff8acd1d2b74fff6e68a79170&a=w%3D644%26h%3D480%26fm%3Dwebp%26q%3D75&cd=2023-07-27T21%3A13%3A09.600Z" %}
Panther JSON 对象
{% endembed %}

有关 Bitwarden 组织活动的更多信息，请参阅[此处](../event-logging/event-logs.md#organization-events)。有关针对特定查询的其他选项，请参阅 [Panther Data Explorer](https://docs.panther.com/search/data-explorer) 文档以获取更多信息。


# 用户名 & 密码生成器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/generator/)
{% endhint %}

使用 Bitwarden 生成器工具可以轻松创建强密码和唯一用户名。密码生成器可在所有 Bitwarden 客户端中使用，用户名生成器可在网页 App、浏览器扩展、桌面 App 和移动 App 中使用。

如果您目前还不是 Bitwarden 用户，您也可以在 [https://bitwarden.com/password-generator/](https://bitwarden.com/password-generator/) 测试我们的免费密码生成器。

## 生成密码 <a href="#generate-a-password" id="generate-a-password"></a>

要生成强的密码：

{% tabs %}
{% tab title="网页 App" %}
从导航栏中选择**工具** → **生成器**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/70bx0hWvxAvkz5RJdIj04n/44fa449c9573f69cc5e63d04d6d90646/2024-12-02_14-42-39.png?_a=DAJCwlWIZAAB" %}
网页 App 的密码生成器
{% endembed %}

您在此页面上[指定的选项](generator.md#password-types)将保存，即使您注销网页 App。您也可以使用相同的选项直接从添加或编辑项目界面使用 **⟳生成**按钮快速生成强密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5ZVBOSK13MaXJ2S8iJTOMX/1324db87fd867667cbb6e8c1c1f4539a/2024-12-02_14-44-30.png?_a=DAJCwlWIZAAB" %}
网页 App 的密码生成器
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择 **⟳生成器**标签页：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6eOmI3kZOdnfw9i5JinfUD/f1a7129244f49c7d904664632e329076/2024-10-29_10-34-01.png?_a=DAJCwlWIZAAB" %}
浏览器扩展的密码生成器
{% endembed %}

您也可以从添加/编辑项目的界面使用 **⟳生成**按钮生成强密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2Cbja6OBxW2S6GVxLOqlYh/b71de03b37f5a4f4960e344a5b17cc01/2024-10-29_10-35-25.png?_a=DAJCwlWIZAAB" %}
浏览器扩展的密码生成器
{% endembed %}

如果您创建的账户没有存储在 Bitwarden 中，您也可以使用内嵌自动填充菜单，在**填充已生成的密码**提示下生成并自动填写密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2JcceqWgFbk4ViLCMe6qm5/ce116e8ff337f90fbbd57b52aa15fdcd/2024-11-05_10-07-08.png?_a=DAJCwlWIZAAB" %}
填充已生成的密码
{% endembed %}

使用内嵌功能时，请使用 **⟳生成**按钮生成新的密码，直到您满意为止。确保在提示时选择**新增登录**，以便将登录信息保存到 Bitwarden。[了解更多](../auto-fill/auto-fill-basics/auto-fill-logins-in-browser-extensions.md#inline-auto-fill-menu)。
{% endtab %}

{% tab title="桌面端" %}
从菜单栏中选择**查看** → **生成器**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6cFQ3iojZXLy1ZIdIXp6Zr/f69517b01aa7f370f91dc823e7a403b5/2025-01-13_16-26-13.png?_a=DAJCwlWIZAAB" %}
桌面 App 的密码生成器
{% endembed %}

您也可以从添加/编辑项目的界面使用 **⟳生成**按钮生成强密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6VInVRr9tZBOndfe4VrpXf/6cc882381f85a2e275e841a8521d4eea/2025-01-13_16-27-33.png?_a=DAJCwlWIZAAB" %}
桌面 App 的密码生成器
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
选择 **⟳生成器**标签页：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/Cqrt6OGquQLRJvZDuqtCk/5b42dad11498bc5c62a749c4fc096fc9/2025-01-21_15-49-19.png?_a=DAJCwlWIZAAB" %}

您也可以从添加/编辑项目的界面生成强密码，以及通过从 iOS 应用程序扩展点按共享图标，使用 **⟳生成**按钮生成强密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4NeVmiRcKfedg6Fzwp0N1Y/f91ad1097dcd379925cedee724dc7592/2025-01-21_15-51-01.png?_a=DAJCwlWIZAAB" %}
移动端的密码生成
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用 generate 命令生成密码：

```batch
bw generate -uln --length 14
```

生成密码的附加选项标志包括：

* `--minNumber`
* `--minSpecial`
* `--ambiguous`

有关详细信息，请参阅 Bitwarden [CLI 文档](../developer-tools/password-manager-cli.md)。
{% endtab %}
{% endtabs %}



### 密码类型 <a href="#password-types" id="password-types"></a>

#### 密码 <a href="#password" id="password"></a>

密码是随机生成的一组可自定义字符类型的字符串。密码的选项包括：

* **长度**：密码中字符的数量。
* **最少数字**：如果启用，则密码中数字 **0-9** 的最少数量。
* **最少特殊字符**：如果启用，则密码中特殊字符 **!@#$%^&\*** 的最少数量。
* **A-Z**：在密码中包含大写字母。
* **a-z**：在密码中包含小写字母。
* **0-9**：在密码中包含数字。
* **!@#$%^&\***：在密码中包含特殊字符。
* **避免模棱两可的字符**：防止您的密码同时包含 `1` 和 `l` 或同时包含 `0` 和 `o`。

{% hint style="warning" %}
除非您需要满足网站的特定密码要求，否则我们建议将**最少数字**和**最少特殊字符**保持尽可能低 (0-1)，因为过度约束会限制生成密码的强度。
{% endhint %}

#### 密码短语 <a href="#passphrase" id="passphrase"></a>

密码短语是随机生成的词组，例如 `panda-lunchroom-uplifting-resisting`。密码短语的选项包括：

* **单词数量**：密码中的单词数量。
* **单词分隔符**：用于分隔密码中单词的字符（在上面的示例中为 `-`）。
* **大写**：将密码中每个单词的首字母大写。
* **包含数字**：在您的密码中包含一个数字字符。

## 生成用户名 <a href="#generate-a-username" id="generate-a-username"></a>

要生成用户名：

{% tabs %}
{% tab title="网页 App" %}
从导航栏中选择**工具** → **生成器**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2862v5xPV5qQM7XfdUvNlI/7481cc930fd05b05580ae5226825b613/2024-12-02_14-43-42.png?_a=DAJCwlWIZAAB" %}
网页 App 用户名生成器
{% endembed %}

您也可以从添加/编辑项目界面使用 **⟳生成**按钮生成用户名：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1zpNFR8fu9DBo2krqln5hr/e893f1f3e8d85d58d20c8e316f247666/2024-12-02_14-44-30.png?_a=DAJCwlWIZAAB" %}
网页 App 用户名生成器
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择 **⟳生成器器**选项卡然后选择**用户名**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/3WEaJYUplgEdjgoSxlQ842/40d3eed8347cb6b0a600d06f42cc1941/2024-10-29_10-39-00.png?_a=DAJCwlWIZAAB" %}
浏览器扩展用户名生成器
{% endembed %}

您还可以从添加/编辑项目界面使用 **⟳生成器**按钮生成用户名：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/23CDvd3ErFQIZNYwgh000F/c19c373ecb6ca2d6aad2587a1b16dd12/2024-10-29_10-39-56.png?_a=DAJCwlWIZAAB" %}
浏览器扩展用户名生成器
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
从菜单栏中选择**查看** → **生成器**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2VGPd4WOwydbovDJdyVT51/7978eb9934404198e94c030e2633dc3f/2025-01-13_16-28-11.png?_a=DAJCwlWIZAAB" %}
桌面 App 用户名生成器
{% endembed %}

您还可以从添加/编辑项目界面使用 **⟳生成器**按钮生成用户名：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7xTg7VVE7CgTZhBl5LlYui/e8e8d7abb103f07671015847f63521c8/2025-01-13_16-27-19.png?_a=DAJCwlWIZAAB" %}
桌面 App 用户名生成器
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
选择 **⟳生成器器**选项卡：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6nfsTiHypQvXrfz7qI7AKI/6e41b1fedea81895497268b0fd825215/2025-01-21_15-56-24.png?_a=DAJCwlWIZAAB" %}
移动 App 用户名生成器
{% endembed %}

您还可以从添加/编辑项目界面使用 **⟳生成器**按钮即时生成用户名：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2Obfpm7UdBizkwASepMS6j/998c1448556484b867160f7412aa984c/2025-01-21_15-51-01.png?_a=DAJCwlWIZAAB" %}
移动 App 用户名生成器
{% endembed %}
{% endtab %}
{% endtabs %}

### 用户名类型 <a href="#username-types" id="username-types"></a>

#### 附加地址电子邮箱 <a href="#plus-addressed-email" id="plus-addressed-email"></a>

选择此类型以使用您的电子邮箱提供商的子地址（也称为「附加寻址」或「别名」）功能。这将基于您指定的**电子邮箱地址**生成一个附加地址（以 `+` 和随机字符串命名）的用户名。

在浏览器扩展和桌面 App 的添加/编辑项目界面，您可以选择使用**随机字符串**（例如 `alice+gsd4aqqe@bitwarden.com`）生成用户名，或基于项目的**网站名称**（例如 `alice+github.com@ bitwarden.com`）生成用户名。**电子邮箱地址**仅限于浏览器和桌面上的添加/编辑界面，因为它需要知道登录的 [URI](../../auto-fill/using-uris.md)，在其他位置，用户名生成器默认为**随机**。

{% hint style="success" %}
**为什么要使用附加地址电子邮箱？**

附加地址电子邮箱可以让您在注册新的服务时过滤您的电子邮箱中的所有垃圾邮件。使用用户名 `alice+rnok6xsh@bitwarden.com` 注册服务时，仍会向 `alice@bitwarden.com` 发送电子邮件，但您可以轻松过滤包含 `+rnok6xsh` 的电子邮件，以防止它们堵塞您的收件箱。
{% endhint %}

#### Catch-all 电子邮箱 <a href="#catch-all-email" id="catch-all-email"></a>

选择此类型以使用您的域名配置的 Catch-all 收件箱。这将在您指定的**域名**中生成一个随机的电子邮箱地址。

在浏览器扩展和桌面 App 的添加/编辑项目界面，您可以选择使用**随机**（例如 `bqzjlero@gardenllc.com`）字符串生成用户名，或基于项目的**网站名称**（例如 `twitter.com@gardenllc.com`）生成用户名。**网站名称**仅限于浏览器和桌面上的添加/编辑界面，因为它需要知道登录的 [URI](../../auto-fill/using-uris.md)，在其他位置，用户名生成器默认为**随机**。

{% hint style="success" %}
**为什么要使用 Catch-all 电子邮件？**

在某些情况下，拥有自己域名（例如 `@bitwarden.com`）的公司可以使用 Catch-all 收件箱避免电子邮件进入您的个人收件箱，而是将它们路由到一个已共享的（有时未经检查）公司收件箱，以备万一将来需要他们的这些记录。

在其他情况下，拥有自己域名（例如 `@gardenllc.com`）的个人可以使用 Catch-all 设置将电子邮件从具有面向隐私的用户名（例如 `github.com@gardenllc.com`）的账户路由到他们的实际收件箱。
{% endhint %}

#### 转发的电子邮箱别名 <a href="#forwarded-email-alias" id="forwarded-email-alias"></a>

选择此类型以将用户名生成器与您的外部别名服务集成。大多数 Bitwarden 应用程序支持与 SimpleLogin、AnonAddy、Firefox Relay、Fastmail、Forward Email 和 DuckDuckGo 集成。移动 App 目前支持与 SimpleLogin、AnonAddy 和 Firefox Relay 集成。

{% hint style="success" %}
**为什么使用转发的电子邮箱别名？**

使用 [SimpleLogin](https://simplelogin.io/) 和 [Addy.io](https://addy.io/) 等电子邮箱别名服务时，您可以使用匿名地址（例如，`nobody-knows-its-me.d0p0r@slmail.me`）来注册网络账户，邮件将转发到您实际的收件箱（例如，`alice@bitwarden.com`）。这可以防止网站或服务在您注册时收集个人信息（在此示例中，名称 Alice 以及她在 Bitwarden 工作的事实）。
{% endhint %}

要设置您的电子邮箱别名集成：

{% tabs %}
{% tab title="SimpleLogin" %}
1、登录到您的 SimpleLogin 账户。

2、从导航中选择 **API Keys**。SimpleLogin 会要求您输入密码以创建 API 密钥。

3、在「New API Key」部分中，输入表明将由 Bitwarden 使用的新密钥的名称，然后选择 **Create**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6ie1Qpk8LYapG6JRX3X1dD/06c1083c6e146c2822f0e4a47b507785/Screen_Shot_2022-06-30_at_3.17.59_PM.png?_a=DAJCwlWIZAAB" %}
SimpleLogin API Keys
{% endembed %}

4、**Copy** 此 API 密钥然后将其粘贴到 Bitwarden 用户名生成器的 **API 密钥**字段中。

5、Password Manager 浏览器扩展、移动 App 和桌面 App 可以连接到自托管的 SimpleLogin 服务器。如果您自托管 SimpleLogin，请输入**服务器 URL**。

6、选择**重新生成用户名**以生成一个用户名并同时自动在 SimpleLogin 中自动创建相应的别名。
{% endtab %}

{% tab title="AnonAddy" %}
1、登录到您的 Addy.io 账户。

2、在 Addy.io 中，从导航菜单选择 **Setting**。

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/18PUguJXkABllufHgtNEJi/564febbfe28d3f0cd491c3216d62db9e/addy_settings.png?_a=DAJCwlWIZAAB" %}
AnonAddy Settings
{% endembed %}

3、在「Setting」界面的 **General** 选项卡上，向下滚动到 **Update Default Alias Domain**。选择您希望用作别名的默认域名。

{% hint style="info" %}
此处选择的默认域名必须与 Bitwarden 用户名生成器中使用的域名匹配。
{% endhint %}

4、选择 **API Keys** 选项卡然后点击 **Create New API Key** 按钮。

5、在「Create New API Key」对话框中，输入指示 Bitwarden 将使用的新令牌的 **Name**、**Expiration**，然后确认您的 Addy.io 账户密码。完成必填字段后，选择 **Create API Key**。

{% embed url="https://bitwarden.com/_gatsby/image/e82cb1df3adb1f0def837940f40c51d7/786ab7d80d66d99858f32b660cb0e593/create%20new%20api%20key.webp?eu=d98c06e2b6cdf88e066ca9d2607b6668e7365ffdf70036816962e3aa1aa9cad324fa1b5722c47ee3786a5c8a87e916eb65957c301cba818e93b549fcbe3cfb59538052e864b42303542ec0ade1f257166ac01000e5c7884ba9726d8db8e2e0255a4e4f6ffe2bfbc2b9ed767aeed66b2dedf4f87d2398aa2ee84f1953d41e2ef464b991a55a6db68bb645a59399ef6c9ff493551812def53c25701f1d5ebc29bff7b607703d21465c3cc8fc0ac36890b36a1e6277410c41a2367e853aa53976acb5bbf832822f32ffe89766&a=w%3D850%26h%3D889%26fm%3Dwebp%26q%3D75&cd=2023-09-20T11%3A59%3A54.220Z" %}
AnonAddy 生成令牌
{% endembed %}

6、复制「Personal Access Key」然后将其粘贴到 Bitwarden 用户名生成器的 **API 访问令牌**字段中。

{% hint style="success" %}
我们建议将此个人访问令牌添加到您的 Bitwarden 中的 Addy.io 密码库项目中，因为该令牌只会在 Addy.io 中显示一次。
{% endhint %}

7、在**域名**字段中，输入您在**步骤 3** 中选择的 Addy.io 域名。作为 Addy.io 的免费用户，您的选项为 `anonaddy.me`、`<username>.anonaddy.me` 或 `<username>.anonaddy.com`。

8、Password Manager 浏览器扩展、移动 App 和桌面 App 可以连接到自托管的 Addy.io 服务器。如果您自托管 SimpleLogin，请输入**服务器 URL**。

9、选择**重新生成用户名**以生成一个用户名并同时自动在 Addy.io 中自动创建相应的别名。
{% endtab %}

{% tab title="Firefox Relay" %}
1、登录到您的 Firefox Relay 账户。

2、选择配置文件图标并从下拉列表中选择 **Setting**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3jK0OhlASgzDZo1Xu2c97O/f24ae0b64e7fe7736e757b33a89510c6/Screen_Shot_2022-06-01_at_3.38.56_PM.png?fm=webp&h=1010&q=50&w=2276" %}
Firefox Relay Settings 菜单
{% endembed %}

3、将 **API Key** 复制到 Bitwarden 用户名生成器的 **API 访问令牌**字段中。

4、选择**重新生成用户名**以生成一个用户名并同时自动在 Firefox Relay 中自动创建相应的掩码。
{% endtab %}

{% tab title="Fastmail" %}
1、登录到您的 Fastmail 账户。

2、选择配置文件图标并从下拉列表中选择 **Setting**。

3、从导航菜单中，选择 **Password & Security**，然后选择 **Manage API tokens**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/J1fPSFIIO7FgPyAyBgpbh/d4dd85f7f7201731936de872ff4a5134/2024-12-23_15-17-17.png?_a=DAJCwlWIZAAB" %}
Fastmail API 令牌
{% endembed %}

4、选择 **New API token** 然后生成 API 令牌：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1FieLCzKTItKNqDIhWBrbH/2816de1ec7580e2e90cf80e38d311993/2024-12-23_15-18-50.png?_a=DAJCwlWIZAAB" %}
**New API token**
{% endembed %}

包含以下信息：

* **Read-only access** **disabled**
* **Masked Email enabled**

5、将 **API Key** 复制到 Bitwarden 用户名生成器的 **API 访问令牌**字段中。

6、选择**重新生成用户名**以生成用户名并在 Fastmail 中自动创建相应的别名。
{% endtab %}

{% tab title="Forward Email" %}
1、登录您的 [Forward Email](https://forwardemail.net/) 账户。

2、Forward Email 使用默认域名 `hideaddress.net`，但是如果您有已注册的域名，则可以将其连接到该服务。详细信息，请参阅 [Forward Email 设置指南](https://forwardemail.net/zh/guides)。

3、在 Forward Email 中，导航至**我的账户** → **安全**页面然后复制「**开发人员访问 API 令牌**」：

{% embed url="https://bitwarden.com/_gatsby/image/8656d578f3f917b02cd90966b05e2e4b/dda4d7d526374ccc43f8b195172906e9/Screen%20Shot%202023-06-30%20at%201.06.04%20PM.webp?eu=d68951b7b5cdfd8f086fa1d63c20346fb43f03abad503385396cb7f91dac9b8570f21b0120c77ae0296f59da85e241ba34c67d6948b8d88cc1bf1cfce331fb08508558ec34e62452057fc4afe1f101463d95495ea084cd59f23f7a81b7e1e4711a504f79a02bb2d9a8ed7527ba9c306bb7e7f17b26dcf83cb6431d179e5c32e23aeed4c1345cb09df645eeb0e6f44eca83e77f6e0a87a97570230d675f9c79cde4c65c767a6b5f0d31cdfe5ac564c3b33a1d65725e5f51f6336ed35cfa3a30c4b2a9f554d87c2ffecb9a7325d39dc1e3b545e84574e7cd24b4823d670d0dc342e9d37ae9d262180e85459ae852f25d52&a=w%3D850%26h%3D528%26fm%3Dwebp%26q%3D75&cd=2023-07-12T12%3A18%3A44.529Z" %}
复制 Forward Email API 令牌
{% endembed %}

4、在 Bitwarden 用户名生成器中，将复制的令牌粘贴到 **API 访问令牌**中，然后输入 `hideaddress.net` 或您的**已注册的域名**。

5、选择**重新生成用户名**以生成用户名并在 Forward Email 中自动创建相应的别名。
{% endtab %}

{% tab title="DuckDuckGo" %}
1、遵循 [DuckDuckGo 说明](https://duckduckgo.com/email/)设置您的 Duck 地址。

2、设置好 Duck 地址后，选择 DuckDuckGo 电子邮件保护页面上的**自动填充**选项卡，然后打开 Web 浏览器的开发人员工具。

3、单击 **Generate Private Duck Address** 按钮并查看开发人员工具窗口中的 **Network** 选项卡。选择 API POST 请求的「地址」调用，并定位到 API 授权项目。该项目看起来像这样：`authorization: Bearer <API token value>.`

{% embed url="https://bitwarden.com/_gatsby/image/b1575c9eb8c753620d1eb1871e706cfe/e3d693f91ce7fe46d7812c6de101a6b7/DDG%20generate%20private%20address.webp?eu=d78d04e2b7c1a9d25c3ba98b3b26646ae86a57a3fe0064853d64b0fc4da1cdd424a51d0175c473b0246b5ad687e945ef34c570324aef818b92be19f0e361ac0155d65cba31bb2554517991f6e5a054403ec54c09a180995aa13b7b80b7bae3761b551673ec3ef8c2e6b62a3dedd27867a9a8f56a3393e83bb5561d4a954d35e363f9ce8d7544ef98b842a8e1f1ac6b9795af6f67028cb33421171016239a68eae5b56e6e312c450d64ccf9589334c0e5381d3025560d06f66568d957fb6e3691b2fea55dc60e0f96c79e642ed381ffc4b875ec682fa19e63fced6a2e5a4ff950eea23ba985&a=w%3D850%26h%3D926%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.229Z" %}
生成 DuckDuckGo 电子邮箱别名
{% endembed %}

4、复制 API 授权令牌的值然后将其粘贴到 Bitwarden 生成器的 API 密钥字段中。

5、选择**重新生成用户名**以生成一个用户名并在 DuckDuckGo 中自动创建对应的别名。
{% endtab %}
{% endtabs %}

#### 随机单词 <a href="#random-word" id="random-word"></a>

选择此类型可为您的用户名生成一个随机单词。随机单词的选项包括：

* **大写**：将您的用户名首字母大写。
* **包含数字**：在您的用户名中包含一个 4 位数的数字。

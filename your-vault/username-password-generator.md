# 用户名和密码生成器

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/generator/)
{% endhint %}

使用 Bitwarden 生成器工具可以轻松创建强密码和唯一用户名。密码生成器可用于所有 Bitwarden 客户端，用户名生成器可用于网页密码库、浏览器扩展和桌面应用程序。

如果您目前还不是 Bitwarden 用户，您也可以在 [https://bitwarden.com/password-generator/](https://bitwarden.com/password-generator/) 测试我们的免费密码生成器。

## 生成密码 <a href="#generate-a-password" id="generate-a-password"></a>

要生成强的密码：

{% tabs %}
{% tab title="网页密码库" %}
从导航栏中选择**工具**，然后从工具菜单中选择**生成器**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/70bx0hWvxAvkz5RJdIj04n/5589ecb7c330ceb94334ee73bb56283d/Screen_Shot_2022-04-05_at_9.08.15_AM.png?fm=webp&h=470&q=50&w=776" %}
网页密码库的密码生成器
{% endembed %}

您在此页面上[指定的选项](username-password-generator.md#password-types)将保存以供密码生成器将来使用。您也可以使用相同的选项直接从添加/编辑项目界面使用 **⟳生成**按钮快速生成强密码：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5ZVBOSK13MaXJ2S8iJTOMX/59d4f77d47be9ecfd5957d00b70655e7/Screen_Shot_2022-04-05_at_9.09.39_AM.png?fm=webp&h=242&q=50&w=776" %}
网页密码库的密码生成器
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择 **⟳生成器**标签页：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6eOmI3kZOdnfw9i5JinfUD/1e378c15585598ba8f38f18c9a02e0a4/Screen_Shot_2022-04-05_at_10.22.19_AM.png?fm=webp&h=749&q=50&w=1210" %}
浏览器扩展的密码生成器
{% endembed %}

您也可以从添加/编辑项目的界面使用 **⟳生成**按钮即时生成强密码：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2Cbja6OBxW2S6GVxLOqlYh/bd200dbd854ddf5058d034ae9a374075/Screen_Shot_2022-04-05_at_10.26.34_AM.png?fm=webp&h=749&q=50&w=1210" %}
浏览器扩展的密码生成器
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
从菜单栏中选择查看 → 生成器：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6cFQ3iojZXLy1ZIdIXp6Zr/20841fa4babfccc3d7dc6ef4e9b307ca/Screen_Shot_2022-04-05_at_10.43.06_AM.png?fm=webp&h=630&q=50&w=992" %}
桌面应用程序的密码生成器
{% endembed %}

您也可以从添加/编辑项目的界面使用 **⟳生成**按钮即时生成强密码：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6VInVRr9tZBOndfe4VrpXf/546300d02cb377a2089f3583c4838aa2/Screen_Shot_2022-04-05_at_10.48.00_AM.png?fm=webp&h=603&q=50&w=983" %}
桌面应用程序的密码生成器
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
选择 **⟳生成器**标签页：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/lRJGxcbGbpu5FkVlPkhkC/17c76d7587bda6b2d8f9ce30d55dabbf/bitwarden-mobile-generator.png?fm=webp&h=1461&q=50&w=1899" %}
移动端的密码生成器
{% endembed %}

您也可以从添加/编辑项目的界面使用 **⟳生成**按钮即时生成强密码：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/Q08IQ6qRaeN41EnbL7oJd/98324b437286e0e5f14b72ba8cebf973/bitwarden-mobile-generator2.png?fm=webp&h=1461&q=50&w=1899" %}
移动端的密码生成器
{% endembed %}
{% endtab %}

{% tab title="CLI" %}
使用 generate 命令生成密码：

```
bw generate -uln --length 14
```

有关详细信息，请参阅我们的 [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

### 密码类型 <a href="#password-types" id="password-types"></a>

#### 密码 <a href="#password" id="password"></a>

密码是随机生成的一组可自定义字符类型的字符串。密码的选项包括：

* **长度**：密码中字符的数量。
* **最少数字**：如果启用 0-9，则密码中数字的最少数量。
* **最少特殊字符**：如果启用了 **!@#$%^&\***，则密码中特殊字符的最少数量。
* **A-Z**：在密码中包含大写字母。
* **a-z**：在密码中包含小写字母。
* **0-9**：在密码中包含数字。
* **!@#$%^&\***：在密码中包含特殊字符。
* **避免模棱两可的字符**：防止您的密码同时包含 `1` 和 `l` 或同时包含 `0` 和 `o`。

#### 密码短语 <a href="#passphrase" id="passphrase"></a>

密码短语是随机生成的词组，例如 `panda-lunchroom-uplifting-resisting`。密码短语的选项包括：

* **单词数量**：密码中的单词数量。
* **单词分隔符**：用于分隔密码中单词的字符（在上面的示例中为 `-`）。
* **大写**：将密码中每个单词的首字母大写。
* **包含数字**：在您的密码中包含一个数字字符。

## 生成用户名 <a href="#generate-a-username" id="generate-a-username"></a>

要生成用户名：

{% tabs %}
{% tab title="网页密码库" %}
从导航栏中选择**工具**，然后从工具菜单中选择**生成器**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2862v5xPV5qQM7XfdUvNlI/e041328a88535315aff51fa2d688d395/Screen_Shot_2022-05-10_at_9.43.01_AM.png?fm=webp&h=465&q=50&w=831" %}
网页密码库用户名生
{% endembed %}
{% endtab %}

{% tab title="浏览器扩展" %}
选择 **⟳生成器器**选项卡：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3WEaJYUplgEdjgoSxlQ842/6f7df712204ed7d3bf2141b166aeb616/Screen_Shot_2022-05-10_at_9.45.26_AM.png?fm=webp&h=810&q=50&w=1235" %}
浏览器扩展用户名生成器
{% endembed %}

您还可以从添加/编辑项目界面使用 **⟳生成器**按钮即时生成用户名：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/23CDvd3ErFQIZNYwgh000F/cefb90b6cc43ce537d0fc688a5623e58/Screen_Shot_2022-04-05_at_10.24.15_AM.png?fm=webp&h=749&q=50&w=1210" %}
浏览器扩展用户名生成器
{% endembed %}
{% endtab %}

{% tab title="桌面端" %}
从菜单栏中选择**查看** → **生成器**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2VGPd4WOwydbovDJdyVT51/7ad41a976c1b1beda1440f152f5068af/Screen_Shot_2022-05-19_at_9.24.13_AM.png?fm=webp&h=804&q=50&w=1088" %}
桌面应用程序用户名生成器
{% endembed %}

您还可以从添加/编辑项目界面使用 **⟳生成器**按钮即时生成用户名：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7xTg7VVE7CgTZhBl5LlYui/d4dbe3adf0d8d52a803e45b28acf97bc/Screen_Shot_2022-05-19_at_9.23.45_AM.png?fm=webp&h=777&q=50&w=1077" %}
桌面应用程序用户名生成器
{% endembed %}
{% endtab %}

{% tab title="移动端" %}
选择 **⟳生成器器**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/b550176ea2a69ea56a0a51b954e8bde8/f733d76482dc17b25769efd395e73745/a.webp?eu=898e57b2e3c8add50c39a6866c7a693db33801fff75733d43e62e2fa4ba1cd8423f44d5776917db87d685a8881e245b834c37f3318b8d089c4bb1ea6bb35ff5c5b8b58e960e12601027992fcb1a601466e901b5ca88a9a0ef06f21d0e4e7b5761e554d2af972e983bdad636cb68b2e61e2e7f72a64caae2de7410f57c14035b824f89ac12c47b39fe74aacf8bded5f9cdfa4784303c5ad6066684b5d06be6be1a4e40c2c7e2e5f5d6b98ec3c9e19dff65d5a0961081504b61e3da12e827360cbb0fda75edb797bb0a0cf35758591a988bc4fa42871b6cc25fc823c7d5859b342b3fc25a0&a=w%3D850%26h%3D654%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.209Z" %}
移动应用程序用户名生成器
{% endembed %}

您还可以从添加/编辑项目界面使用 **⟳生成器**按钮即时生成用户名：

{% embed url="https://bitwarden.com/_gatsby/image/cedb7a4d2d75ace960469ecc208b25e0/f733d76482dc17b25769efd395e73745/d.webp?eu=d9db01b2e7c8a8870a3ef1816170343ae56c04a2ac0063853862b1fa4daac8d42da5115425957cb17f3a5bddd0b316be34c22e624dbbd38ec5ba18fced36fb0f068750b623f730445b34dba7eda451102bd8491cf7d28b4bf62931cabbe6f36f1e124278ee20b9d7e4f47263af815060bcf6fb290096d921aa491925a84d318107bdcac1351ee89bb819e8e0effb5bc998e32a0548d2fa31712548195bb87cbcf1e30723267d5e1b6b99&a=w%3D850%26h%3D654%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.203Z" %}
移动应用程序用户名生成器
{% endembed %}
{% endtab %}
{% endtabs %}

### 用户名类型 <a href="#username-types" id="username-types"></a>

#### 附加地址电子邮件 <a href="#plus-addressed-email" id="plus-addressed-email"></a>

选择此类型以使用您的电子邮件提供商的子地址（也称为「附加寻址」或「别名」）功能。这将基于您指定的**电子邮件地址**生成一个附加地址（以 `+` 和随机字符串命名）的用户名。

在浏览器扩展和桌面应用程序的添加/编辑项目界面，您可以选择使用**随机字符串**（例如 `alice+gsd4aqqe@bitwarden.com`）生成用户名，或基于项目的**网站名称**（例如 `alice+github.com@ bitwarden.com`）生成用户名。**网站名称**仅限于浏览器和桌面上的添加/编辑界面，因为它需要知道登录的 [URI](../auto-fill/using-uris.md)，在其他位置，用户名生成器默认为**随机**。

{% hint style="success" %}
**为什么要使用附加地址电子邮件？**

附加地址电子邮件可以让您在注册新的服务时过滤您的电子邮件中的所有垃圾邮件。使用用户名 `alice+rnok6xsh@bitwarden.com` 注册服务时，仍会向 `alice@bitwarden.com` 发送电子邮件，但您可以轻松过滤包含 `+rnok6xsh` 的电子邮件，以防止它们堵塞您的收件箱。
{% endhint %}

#### Catch-all 电子邮件 <a href="#catch-all-email" id="catch-all-email"></a>

选择此类型以使用您的域名配置的 Catch-all 收件箱。这将在您指定的**域名**中生成一个随机的电子邮件地址。

在浏览器扩展和桌面应用程序的添加/编辑项目界面，您可以选择使用**随机字符串**（例如 `bqzjlero@gardenllc.com`）生成用户名，或基于项目的**网站名称**（例如 `twitter.com@gardenllc.com`）生成用户名。**网站名称**仅限于浏览器和桌面上的添加/编辑界面，因为它需要知道登录的 [URI](../auto-fill/using-uris.md)，在其他位置，用户名生成器默认为**随机**。

{% hint style="success" %}
**为什么要使用 Catch-all 电子邮件？**

在某些情况下，拥有自己域名（例如 `@bitwarden.com`）的公司可以使用 Catch-all 收件箱避免电子邮件进入您的个人收件箱，而是将它们路由到一个已共享的（有时未经检查）公司收件箱，以备万一将来需要他们的这些记录。

在其他情况下，拥有自己域名（例如 `@gardenllc.com`）的个人可以使用 Catch-all 设置将电子邮件从具有面向隐私的用户名（例如 `github.com@gardenllc.com`）的账户路由到他们的实际收件箱。
{% endhint %}

#### 转发的电子邮件别名 <a href="#forwarded-email-alias" id="forwarded-email-alias"></a>

选择此类型以将用户名生成器与您的外部别名服务集成。目前，Bitwarden 支持与 SimpleLogin、AnonAddy 和 Firefox Relay 的集成。

{% hint style="success" %}
**为什么使用转发的电子邮件别名？**

使用 [SimpleLogin](https://simplelogin.io/) 和 [AnonAddy](https://anonaddy.com/) 等电子邮件别名服务时，您可以使用匿名地址（例如，`nobody-knows-its-me.d0p0r@slmail.me`）来注册网络账户，邮件将转发到您实际的收件箱（例如， `alice@bitwarden.com`）。这可以防止网站或服务在您注册时收集个人信息（在此示例中，名称 Alice 以及她在 Bitwarden 工作的事实）。
{% endhint %}

要设置您的电子邮件别名集成：

{% tabs %}
{% tab title="SimpleLogin" %}
1、登录到您的 SimpleLogin 账户。

2、从导航中选择 **API Keys**。SimpleLogin 会要求您输入密码以创建 API 密钥。

3、在 New API Key 部分中，输入表明将由 Bitwarden 使用的新密钥的名称，然后选择 **Create**。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6ie1Qpk8LYapG6JRX3X1dD/b57640b302390d4ccce78f088c1058b0/Screen_Shot_2022-05-09_at_10.10.08_AM.png?fm=webp&h=714&q=50&w=1017" %}
SimpleLogin API Keys
{% endembed %}

4、**Copy** 此 API 密钥然后将其粘贴到 Bitwarden 用户名生成器的 **API 密钥**字段中。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7qXbdBMRQPYKnxqiSvbjvo/8932be630a3111902524bc38bcc13293/Screen_Shot_2022-05-09_at_10.13.23_AM.png?fm=webp&h=586&q=50&w=830" %}
SimpleLogin API 密钥
{% endembed %}

5、选择**重新生成用户名**以生成一个用户名并同时自动在 SimpleLogin 中自动创建相应的别名。
{% endtab %}

{% tab title="AnonAddy" %}
1、登录到您的 AnonAddy 账户。

2、在 AnonAddy 中，选择 **Settings** 并向下滚动到 API 部分。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/18PUguJXkABllufHgtNEJi/4f5f00f9c210197941f4bb41fe0a42e0/Screen_Shot_2022-05-09_at_11.22.59_AM.png?fm=webp&h=355&q=50&w=1009" %}
AnonAddy Settings
{% endembed %}

3、选择 **Generate New Token** 按钮。

4、在 Create New Token 对话框中，输入表明将由 Bitwarden 使用的新密钥的 **Name**，然后选择 **Generate Token**。

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/6o8021KYChu6jzEGvUbXDH/e08ba5185e3d65d3428b3ba7a2e7ff18/Screen_Shot_2022-05-09_at_10.57.09_AM.png?fm=webp&h=639&q=50&w=1002" %}
Anon Addy 生成令牌
{% endembed %}

5、复制个人访问令牌然后将其粘贴到 Bitwarden 用户名生成器的 **API 访问令牌**字段中。

{% hint style="success" %}
我们建议将此个人访问令牌添加到您的 Bitwarden 中的 AnonAddy 密码库项目中，因为该令牌只会在 AnonAddy 中显示一次。
{% endhint %}

6、在**域名**字段中，输入有效的 AnonAddy 域名。作为 AnonAddy 的免费用户，您可以选择 `anonaddy.me`、`<username>.anonaddy.me` 或 `<username>.anonaddy.com`。

7、选择**重新生成用户名**以生成一个用户名并同时自动在 AnonAddy 中自动创建相应的别名。
{% endtab %}

{% tab title="Firefox Relay" %}
{% hint style="success" %}
由于 Firefox Relay 的配置设置，此集成只能在 Bitwarden 浏览器扩展和桌面应用程序中使用。
{% endhint %}

1、登录到您的 Firefox Relay 账户账户。

2、选择配置文件图标并从下拉列表中选择 **Setting**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3jK0OhlASgzDZo1Xu2c97O/f24ae0b64e7fe7736e757b33a89510c6/Screen_Shot_2022-06-01_at_3.38.56_PM.png?fm=webp&h=1010&q=50&w=2276" %}
Firefox Relay Settings 菜单
{% endembed %}

3、将 **API Key** 复制到 Bitwarden 用户名生成器的 **API 访问令牌**字段中。

4、选择**重新生成用户名**以生成一个用户名并同时自动在 Firefox Relay 中自动创建相应的掩码。
{% endtab %}

{% tab title="Fastmail" %}
1、登录到您的 Fastmail 账户。

2、选择配置文件图标并从下拉列表中选择 **Setting**：

{% embed url="https://bitwarden.com/_gatsby/image/ebf74c05938c6e03718e16266da3f8c1/69e413a31ee98f34df0f3cfa0b1c9018/Fastmail%20SS1%20copy.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2F2BWxxG9WkZbOd3VbxiRqFb%2F1af6bc251249507276b76fabcf938d89%2FFastmail_SS1_copy.png&a=w%3D249%26h%3D320%26fm%3Dwebp%26q%3D75&cd=2022-09-09T16%3A06%3A41.371Z" %}
Fastmail 设置
{% endembed %}

3、从导航菜单中，选择 **Password & Security**，然后在 API Tokens 部分中选择 **Add**：

{% embed url="https://bitwarden.com/_gatsby/image/1c82e7f0b1993021d77a8211281de7aa/caae18263fc82827ba034be99e6f2a73/Fastmail%20SS%202.webp?u=https%3A%2F%2Fimages.ctfassets.net%2F7rncvj1f8mw7%2FJ1fPSFIIO7FgPyAyBgpbh%2Fc47bb478ec7c3e255a9b4dda8b59e3b2%2FFastmail_SS_2.png&a=w%3D850%26h%3D521%26fm%3Dwebp%26q%3D75&cd=2022-09-09T16%3A06%3A41.384Z" %}
Fastmail API 令牌
{% endembed %}

4、选择 **New API token** 然后生成一个具有如下属性的新 API 令牌：

* **Read-only access** **disabled**。
* **Masked Email enabled**。

5、将 **API Key** 复制到 Bitwarden 用户名生成器的 **API 访问令牌**字段中。

6、选择**重新生成用户名**以生成用户名并在 Fastmail 中自动创建相应的别名。
{% endtab %}

{% tab title="Forward Email" %}
1、登录您的 [Forward Email](https://forwardemail.net/) 账户。

2、Forward Email 使用默认域名 `hideaddress.net`，但是如果您有已注册的域名，则可以将其连接到该服务。有关详细信息，请参阅 [Forward Email 设置指南](https://forwardemail.net/en/guides)。

3、在 Forward Email 中，导航至**我的账户** → **安全**页面并复制开发人员访问 API 令牌：

{% embed url="https://bitwarden.com/_gatsby/image/8656d578f3f917b02cd90966b05e2e4b/dda4d7d526374ccc43f8b195172906e9/Screen%20Shot%202023-06-30%20at%201.06.04%20PM.webp?eu=d68951b7b5cdfd8f086fa1d63c20346fb43f03abad503385396cb7f91dac9b8570f21b0120c77ae0296f59da85e241ba34c67d6948b8d88cc1bf1cfce331fb08508558ec34e62452057fc4afe1f101463d95495ea084cd59f23f7a81b7e1e4711a504f79a02bb2d9a8ed7527ba9c306bb7e7f17b26dcf83cb6431d179e5c32e23aeed4c1345cb09df645eeb0e6f44eca83e77f6e0a87a97570230d675f9c79cde4c65c767a6b5f0d31cdfe5ac564c3b33a1d65725e5f51f6336ed35cfa3a30c4b2a9f554d87c2ffecb9a7325d39dc1e3b545e84574e7cd24b4823d670d0dc342e9d37ae9d262180e85459ae852f25d52&a=w%3D850%26h%3D528%26fm%3Dwebp%26q%3D75&cd=2023-07-12T12%3A18%3A44.529Z" %}
复制 Forward Email API 令牌
{% endembed %}

4、在 Bitwarden 用户名生成器中，将复制的令牌粘贴到 **API 访问令牌**中，然后输入 `hideaddress.net` 或您的**已注册的域名**。

5、选择**重新生成用户名**以生成用户名并在 Forward Email 中自动创建相应的别名。
{% endtab %}

{% tab title="DuckDuckGo" %}
1、按照 [DuckDuckGo 说明](https://duckduckgo.com/email/)设置您的 Duck 地址。

2、设置好 Duck 地址后，选择 DuckDuckGo 电子邮件保护页面上的**自动填充**选项卡，然后打开 Web 浏览器的开发人员工具。

3、单击 **Generate Private Duck Address** 按钮并查看开发人员工具窗口中的 **Network** 选项卡。选择 API POST 请求的“地址”调用，并定位到 API 授权项。该项目看起来像这样：`authorization: Bearer <API token value>.`

{% embed url="https://bitwarden.com/_gatsby/image/b1575c9eb8c753620d1eb1871e706cfe/e3d693f91ce7fe46d7812c6de101a6b7/DDG%20generate%20private%20address.webp?eu=d78d04e2b7c1a9d25c3ba98b3b26646ae86a57a3fe0064853d64b0fc4da1cdd424a51d0175c473b0246b5ad687e945ef34c570324aef818b92be19f0e361ac0155d65cba31bb2554517991f6e5a054403ec54c09a180995aa13b7b80b7bae3761b551673ec3ef8c2e6b62a3dedd27867a9a8f56a3393e83bb5561d4a954d35e363f9ce8d7544ef98b842a8e1f1ac6b9795af6f67028cb33421171016239a68eae5b56e6e312c450d64ccf9589334c0e5381d3025560d06f66568d957fb6e3691b2fea55dc60e0f96c79e642ed381ffc4b875ec682fa19e63fced6a2e5a4ff950eea23ba985&a=w%3D850%26h%3D926%26fm%3Dwebp%26q%3D75&cd=2022-10-12T12%3A26%3A53.229Z" %}
生成 DuckDuckGo 电子邮件别名
{% endembed %}

4、复制 API 授权令牌的值然后将其粘贴到 Bitwarden 生成器的 API 密钥字段中。

5、选择**重新生成用户名**以生成一个用户名并在 DuckDuckGo 中自动创建对应的别名。
{% endtab %}
{% endtabs %}

#### 随机单词 <a href="#random-word" id="random-word"></a>

选择此类型可为您的用户名生成一个随机单词。随机单词的选项包括：

* **大写**：将您的用户名首字母大写。
* **包含数字**：在您的用户名中包含一个 4 位数的数字。

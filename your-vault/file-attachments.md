# 文件附件

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/attachments/)
{% endhint %}

{% hint style="info" %}
高级用户和付费组织成员可使用文件附件功能。这些付费用户拥有 1GB 加密存储空间用于存储文件附件。也可按 1GB 的增量购买[更多存储空间](file-attachments.md#add-storage-space)。
{% endhint %}

可通过任何 Bitwarden App 将文件附加到密码库项目。单个文件附件不能大于 500 MB（从移动 App 上传是 100 MB）。附件在本地进行加密和解密，这意味着未加密的附件数据不会通过互联网传输或由服务器存储。

{% hint style="info" %}
个人密码库项目和所有 Send 的附件使用高级订阅或组织授予的个人存储空间。组织拥有的项目上的附件使用共享的组织存储空间。了解如何[添加存储空间](file-attachments.md#add-storage-space)。
{% endhint %}

{% hint style="warning" %}
**关于 2021 年 5 月 11 日之后创建的附件的说明：**

由于附件升级，通过最新的客户端上传的附件无法在某些旧版本的客户端上打开。如果你发现你无法访问最近创建的附件，请将你的客户端升级到最新版本。（**提示**：云网页密码库总是为最新版本。）

**冻结的或旧版的客户端**，包括 Safari 13（或更早）macOS 桌面应用程序和应用程序扩展，将不支持访问这些附件。
{% endhint %}

## 上传文件 <a href="#upload-a-file" id="upload-a-file"></a>

要附加一个文件到密码库项目：

{% tabs %}
{% tab title="网页 App" %}
要从网页 App 附加文件：

1. 选择要附加文件的项目的 **≡选项**菜单。
2. 从下拉菜单中选择 **🔗附件**。
3. 在「附件」面板中，**浏览...** 您要附加的文件。
4. 选择**保存**按钮。

项目附加了文件后，从 **≡选项**菜单中选择 **🔗附件**将显示该密码库项目已附加的文件列表。
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展附加文件：

1. 打开您要附加文件的项目，然后选择**编辑**按钮。
2. 滚动到「编辑」界面的底部，然后选择 **🔗附件**。
3. 在「附件」面板中，选择**选择文件**。
4. 选择要上传的文件，然后选择**上传**按钮。

项目附加了文件后，选择 **🔗附件**将显示该密码库项目已附加的文件列表。
{% endtab %}

{% tab title="移动端" %}
要从移动 App 附加文件：

1. 打开您想要附加文件的项目，然后选择  **≡菜单**按钮。
2. 选择 **🔗附件**。
3. 在「附件」面板中，选择**选择文件**按钮然后浏览您的文件。
4. 选择**保存**按钮。

项目附加了文件后，从 **≡菜单**下拉菜单选择 **🔗附件**将显示该密码库项目已附加的文件列表。
{% endtab %}

{% tab title="桌面端" %}
要从桌面 App 附加文件：

1. 打开您想要附加文件的项目，然后选择**编辑**按钮。
2. 选择 **🔗附件**。
3. 在「附件」面板中，**浏览...** 您要附加的文件。
4. 选择**保存**按钮。

项目附加了文件后，选择 **🔗附件**将显示该密码库项目已附加的文件列表。
{% endtab %}

{% tab title="CLI" %}
使用 `bw create attachment` 以附加文件到现有的密码库项目，示例：

```batch
bw create attachment --file /path/to/myfile.ext --itemid <itemid>
```

更多详情，请参阅 Bitwarden [CLI ](../password-manager/developer-tools/password-manager-cli.md)
{% endtab %}
{% endtabs %}

## 下载文件 <a href="#download-a-file" id="download-a-file"></a>

要下载文件附件：

{% tabs %}
{% tab title="网页 App" %}
要从网页 App 下载附件：

1. 选择要从中下载附件的项目的 **≡选项**菜单。
2. 从下拉菜单中选择 **🔗附件**。
3. 选择要下载的附件。
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展下载附件：

1. 打开您要从中下载附件的项目。
2. 滚动到「编辑」界面的底部，然后选择 **🔗附件**。
3. 对要下载的附件，选择 **⬇️下载**按钮。
{% endtab %}

{% tab title="移动端" %}
要从移动 App 下载附件：

1. 打开您要从中下载附件的项目。
2. 对要下载的附件，选择 **⬇️下载**按钮。
{% endtab %}

{% tab title="桌面端" %}
要从桌面 App 下载附件：

1. 打开您要从中下载附件的项目。
2. 滚动到「附件」部分，然后选择要下载的项目的 **⬇️下载**按钮。
{% endtab %}

{% tab title="CLI" %}
使用 `bw get attachment` 来下载文件，示例：

```batch
bw get attachment photo.png --itemid 99ee88d2-6046-4ea7-92c2-acac464b1412 --output /Users/myaccount/Pictures/
```

更多详情，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

## 导出所有附件 <a href="#export-all-attachments" id="export-all-attachments"></a>

要创建包含附件的导出：

{% tabs %}
{% tab title="网页 App" %}
要从网页 App 导出附件：

1、从导航中选择**工具** → **导出密码库**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/5PUGzasNsQnABG9gtso4o3/9be00b37afafd779c20fd9624dd9512d/2024-12-03_08-59-25.png" %}
导出个人密码库
{% endembed %}

2、从**文件格式**下拉菜单中选择 `.zip (with attachments)`。目前，只能从个人密码库中导出附件。

3、选择**确认格式**，然后选择**导出密码库**按钮以完成。您需要使用主密码或电子邮件验证码确认您的权限。

导出文件将被发送到您的「下载」文件夹或网络浏览器设置为下载文件的位置。
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展导出附件：

1、打开**设置**选项卡。

2、选择**密码库选项**，然后选择**导出密码库**：

3、从**文件格式**下拉菜单中选择 `.zip (with attachments)`。目前，只能从个人密码库中导出附件。

4、选择**导出密码库**按钮以完成。您需要使用主密码或电子邮件验证码确认您的权限。

导出文件将被发送到您的「下载」文件夹或网络浏览器设置为下载文件的位置。
{% endtab %}

{% tab title="桌面 App" %}
要从桌面 App 导出附件：

1、从菜单栏中，导航到**文件** → **导出密码库**。

2、从**文件格式**下拉菜单中选择 `.zip (with attachments)`。目前，只能从个人密码库中导出附件。

3、选择**导出密码库**按钮以完成。您需要使用主密码或电子邮件验证码确认您的权限。

导出文件将被发送到您的「下载」文件夹或网络浏览器设置为下载文件的位置。
{% endtab %}

{% tab title="CLI" %}
要从桌面 App 导出附件，使用如下命令：

```bash
bw export --format zip
```
{% endtab %}
{% endtabs %}

## 删除文件 <a href="#delete-a-file" id="delete-a-file"></a>

要删除文件附件：

{% tabs %}
{% tab title="网页 App" %}
要从网页 App 删除附件：

1. 选择要从中删除附件的项目的 **≡选项**菜单。
2. 从下拉菜单中选择 **🔗附件**。
3. 选择要删除的附件旁边的 **🗑️删除**图标。
{% endtab %}

{% tab title="浏览器扩展" %}
要从浏览器扩展删除附件：

1. 打开您要删除附件的项目。
2. 滚动到「编辑」界面的底部，然后选择**附件**。
3. 对要删除的附件，选择 **🗑️删除**按钮。
{% endtab %}

{% tab title="移动端" %}
要从移动 App 删除附件：

1. 打开您要删除附件的项目然后选择 **≡菜单**图标。
2. 选择 **🔗附件**。
3. 在「附件」面板上，选择要删除的附件的 **🗑️删除**图标。
{% endtab %}

{% tab title="桌面端" %}
要从桌面 App 删除附件：

1. 打开您要删除附件的项目然后选择**编辑**图标。
2. 选择 **🔗附件**。
3. 在「附件」面板上，选择要删除的附件的 **🗑️删除**图标。
{% endtab %}

{% tab title="CLI" %}
使用 `bw delete attachment` 来删除文件附件，示例：

```batch
bw delete attachment 7063feab-4b10-472e-b64c-785e2b870b92
```

更多详情，请参阅 Bitwarden [CLI 文档](../password-manager/developer-tools/password-manager-cli.md)。
{% endtab %}
{% endtabs %}

## 添加存储空间 <a href="#add-storage-space" id="add-storage-space"></a>

付费用户和付费组织的成员拥有 1GB 加密存储空间用于存储文件附件。个人和组织可以通过完成以下步骤购买额外的存储空间：

{% hint style="info" %}
添加存储空间将调整您的计费总金额并立即通过您的付款方式收取费用。第一次更改将在当前计费周期的剩余时间内按比例分配。
{% endhint %}

{% tabs %}
{% tab title="个人" %}
要为您的个人密码库添加存储空间：

1、在 Bitwarden 网页 App 中，导航到**设置** → **订阅**。

2、在「存储」部分，选择**添加存储**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/113yhHwt2fIgkjWjmPgCa4/868beec72cf9e007512178cc82b325a5/2024-12-02_15-26-55.png?_a=DAJCwlWIZAAB" %}
为个人密码库添加存储空间
{% endembed %}

3、使用计数器，选择 **GB 存储空间将添加**的数量，然后选择**提交**。
{% endtab %}

{% tab title="组织" %}
要为您的组织密码库添加存储空间：

1、打开 Bitwarden 网页 App，使用产品切换器打开管理控制台：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/2uxBDdQa6lu0IgIEfcwMPP/e3de3361749b6496155e25edcfdcf08b/2024-12-02_11-19-56.png?_a=DAJCwlWIZAAB" %}
产品切换器
{% endembed %}

2、从导航选择**计费** → **订阅**。

3、在「管理订阅」部分，选择**添加存储**按钮：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6tMMQEzEKXIRSa9fIUXuoh/3d9f81b717d3cee9681f1feda97d1b91/2024-12-02_15-28-55.png?_a=DAJCwlWIZAAB" %}
为组织密码库添加存储空间
{% endembed %}

4、使用计数器，选择 **GB 存储空间将添加**的数量，然后选择**提交**。
{% endtab %}

{% tab title="自托管" %}
虽然自托管时附件存储仍与付费用户或组织成员绑定，但**存储空间的大小**仅受包含附件目录的卷可用空间的限制，上限为 10 TB（10240 GB）。用户和管理员**无需**更改任何值来增加该限制。
{% endtab %}
{% endtabs %}

## 修复旧附件 <a href="#fixing-old-attachments" id="fixing-old-attachments"></a>

在 2018 年 12月 之前，文件附件使用另外一种方式加密数据。从那以后，我们已经转向一种更新更好的加密文件附件的方式。使用旧加密方式的所有附件在密码库清单中都将标识一个 **⚠️**警告图标。您应该将这些旧附件升级为新的加密方式，以便其他与账户相关的功能可以正常运行：

1. 打开附件编辑页面。
2. 单击旧附件旁边的**修复**按钮。此过程将下载附件并使用新的加密方法对其进行重新加密，将附件重新上传回您的密码库，然后删除该附件的旧版本。

附件成功升级后，**⚠️**警告图标和修复按钮会消失。

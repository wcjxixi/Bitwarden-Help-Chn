# 使用 Intune 部署浏览器扩展

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/deploy-browser-extensions-with-intune/)
{% endhint %}

在商业环境中操作 Bitwarden 时，管理员可能希望通过 **Microsoft Intune** 向用户自动部署 Bitwarden 浏览器扩展。本文将介绍如何使用 Intune 将 Bitwarden Password Manager 浏览器扩展部署到您的终端。

## 获取扩展 ID 和更新 URL <a href="#get-extension-id-and-update-url" id="get-extension-id-and-update-url"></a>

要使用 Intune 部署 Bitwarden 浏览器扩展，您需要一个扩展 ID 和更新 URL。每种浏览器的标识符都不相同：

{% tabs %}
{% tab title="Chrome" %}
* 扩展 ID：`nngceckbapebfimnlniiiahkandclblb`
* 更新 URL：`https://clients2.google.com/service/update2/crx`
{% endtab %}

{% tab title="Edge" %}
* 扩展 ID：`jbkfoedolllekgbhcbcoahefnbanhhlh`
* 更新 URL：`https://edge.microsoft.com/extensionwebstorebase/v1/crx`
{% endtab %}
{% endtabs %}

## 创建配置文件 <a href="#create-configuration-profile" id="create-configuration-profile"></a>

接下来，打开 Microsoft Intune 门户并完成以下步骤：

1、在 Intune 门户中，导航至**设备** → **配置**，然后选择**创建** → **新建策略**。

2、在创建配置文件窗口中：

* 选择**平台**（例如，**Windows 10 及更高版本**）。
* 从**配置文件类型**下拉菜单中，选择**设置目录**。

3、选择**创建**。

4、在下一个界面，为配置文件指定一个**名称**和**描述**，然后选择**下一步**。

5、在配置设置界面，选择**添加设置**。

6、在设置选择器中：

* 对于 Google Chrome 浏览器，搜索**配置强制安装的应用程序和扩展程序列表**，选择 **Google Chrome 浏览器扩展**类别，然后将该选项切换为开启。
* 对于 Microsoft Edge，搜索控制哪些扩展会被静默安装，选择 **Microsoft Edge/扩展**类别，然后将该选项切换为开启。

7、关闭设置选择器。

8、仍然在配置设置界面，启用你选择的任何选项，并输入检索到的扩展 ID 和更新 URL，例如：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6lBFbAyf4DqoUbZL2mL6mb/e7c1f91a37d589610b57556666541858/2024-09-05_10-00-46.png?_a=DAJCwlWIZAAB" %}
使用 Intune 部署浏览器扩展
{% endembed %}

9、选择**下一步**。

10、在范围标记界面，输入希望应用于配置的任何范围，然后选择**下一步**。

11、在分配界面，为配置添加组或用户，然后选择下一步。

12、在**审查 + 创建**界面，选择**创建**。

# 使用 Intune 部署桌面端 App

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/deploy-desktop-apps-with-intune/)
{% endhint %}

在商业环境中操作 Bitwarden 时，管理员可能希望通过 **Microsoft Intune** 向用户自动部署 Bitwarden 桌面 App。本文将介绍如何使用 Intune 将 Bitwarden Password Manager 桌面 App 部署到您的端点。

可以使用 Win32 应用程序（推荐）或通过 Microsoft App Store 将 Bitwarden 桌面 App 部署到端点：

{% tabs %}
{% tab title="Win32 App" %}
要部署 Win32  App 版本的 Bitwarden Password Manager，请完成以下步骤：

1. 从 [bitwarden.com/download/](https://bitwarden.com/download/) 下载最新的 Bitwarden Windows 桌面 App 安装程序。
2. 使用 [Microsoft Win32 Content Prep Tool](https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool) 将安装程序转换为所需的 `.intunewin` 格式（[了解更多](https://learn.microsoft.com/zh-cn/mem/intune/apps/apps-win32-prepare)）。
3. 打开 Intune 门户，导航到**应用程序** → **Windows** 然后选择 ✚**添加**。
4. 在选择应用程序类型窗口中，使用**应用程序类型**下拉菜单选择 **Windows 应用程序 (Win32)**。
5. 点击**选择**。
6. 在应用程序信息界面，选择**选择应用程序软件包文件**。
7. 在应用程序软件包文件窗口中，使用文件资源管理器选择转换后的 `.intunewininstaller` 然后选择**确定**。
8. 继续之前请注意应用程序的**名称**，尤其是可执行文件中的版本号。
9. 选择**下一步**。
10. 在程序界面：
    * 指定以下**安装命令**：`Bitwarden-installer-{version}.exe /allusers /S`。确保将 `{version}` 替换为应用程序的正确版本，例如 `2024.8.0`，如应用程序名称所示（步骤 8）。
    * 指定以下**卸载命令**：`C:\Program Files\Bitwarden\Uninstall Bitwarden.exe /allusers /S`。
    * 选择一个**安装行为**，更多信息可以通过悬停在该页面上的 **⚠️**图标找到。
11. 选择**下一步**。
12. 在需求界面：
    * 指定**操作系统架构**为 **64 位/32 位**。
    * 指定**最低操作系统**为 **Windows 10 1607**。
13. 选择**下一步**。
14. 在检测规则界面：
    * 从**规则**下拉菜单中，选择**手动配置检测规则**。
    * 选择**添加**。
    * 从**规则类型**下拉菜单中，选择**文件**。
    * 指定**路径**为 `C:\Program Files\Bitwarden`。
    * 指定**文件或文件夹**为 `Bitwarden.exe`。
    * 从**检测方法**下拉菜单中，选择**存在文件或文件夹**。
    * 对于**在 64 位客户端上关联 32 位应用程序**，请选择**否**。
15. 选择**下一步**。
16. 在依赖关系界面，选择**下一步**。
17. 在分配界面，向配置中添加群组或用户，然后选择**下一步**。
18. 在**审查 + 创建**界面，选择**创建**。
{% endtab %}

{% tab title="App Store" %}
{% hint style="success" %}
要使用这种方式，端点设备必须能够访问 Microsoft App Store，并且必须支持 Intune 管理扩展 (IME)。

请注意，Microsoft App Store 中的 Bitwarden 桌面 App 目前不支持浏览器扩展生物识别集成（[了解更多](../../../your-vault/unlocking-with-biometrics.md)）。
{% endhint %}

要部署 Microsoft App Store 版本的 Bitwarden Password Manager，请打开 Microsoft Intune 门户然后完成以下步骤：

1. 在 Intune 门户中，导航至**应用程序** → **Windows** 然后选择 ✚**添加**。
2. 在选择应用程序类型窗口中，使用**应用程序类型**下拉菜单选择 **Microsoft Store 应用程序（新）**。
3. 点击**选择**。
4. 在应用程序信息界面，选择**搜索 Microsoft Store 应用程序（新）**。
5. 搜索 Bitwarden，找到并高亮显示后点击**选择**。
6. 选择一个**安装行为**，更多信息可以通过悬停在该页面上的 **⚠️**图标找到。
7. 选择**下一步**。
8. 在分配界面，向配置中添加群组或用户，然后选择**下一步**。
9. 在**审查 + 创建**界面，选择**创建**。
{% endtab %}
{% endtabs %}

# 桌面 App 功能支持

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/desktop-app-feature-support/)
{% endhint %}

Bitwarden 桌面 App 可通过多种渠道或安装方式在 Windows、macOS 和 Linux 上使用，但不同渠道提供的功能可能有所不同。本文将介绍各个渠道所支持的功能，用于帮助您决定使用哪种方式来安装桌面 App：

{% hint style="success" %}
请跳转至本页底部查看表格中列出的[各项功能的描述](desktop-app-feature-support.md#feature-descriptions)。
{% endhint %}

## 操作系统 <a href="#operating-systems" id="operating-systems"></a>

> 下载桌面 App：
>
> * Windows：[安装包 (.exe)](https://bitwarden.com/download/#downloads-desktop)、[Microsoft Store](https://apps.microsoft.com/detail/9pjsdv0vpk04?hl=en-US\&gl=US)、[便携版 App (.exe)](https://bitwarden.com/download/#downloads-desktop)
> * macOS：[安装包 (.dmg)](https://bitwarden.com/download/#downloads-desktop)、[App Store](https://apps.apple.com/us/app/bitwarden/id1352778147?mt=12)
> * Linux：[AppImage](https://bitwarden.com/download/#downloads-desktop)、[Snap](https://snapcraft.io/bitwarden)、[Flatpak](https://flathub.org/apps/com.bitwarden.desktop)、[.deb](https://bitwarden.com/download/#downloads-desktop)、[.rpm](https://bitwarden.com/download/#downloads-desktop)

### Windows

| 功能      | 安装包 (.exe)             | Microsoft Store      | 便携版 App (.exe)       |
| ------- | ---------------------- | -------------------- | -------------------- |
| 自动更新    | :white\_check\_mark:更改 | :white\_check\_mark: |                      |
| 桌面生物识别  | :white\_check\_mark:   |                      | :white\_check\_mark: |
| 扩展生物识别  | :white\_check\_mark:   |                      | :white\_check\_mark: |
| 与操作系统集成 | :white\_check\_mark:   | :white\_check\_mark: | :white\_check\_mark: |
| 启动时启动   | :white\_check\_mark:   |                      | :white\_check\_mark: |
| 直接导入器   | :white\_check\_mark:   |                      |                      |
| 安全存储    | :white\_check\_mark:   | :white\_check\_mark: |                      |
| 进程隔离    | :white\_check\_mark:   | :white\_check\_mark: |                      |

### macOS

| 功能      | 安装包 (.dmg)           | App Store            |
| ------- | -------------------- | -------------------- |
| 自动更新    | :white\_check\_mark: | :white\_check\_mark: |
| 桌面生物识别  |                      | :white\_check\_mark: |
| 扩展生物识别  |                      | :white\_check\_mark: |
| 与操作系统集成 | :white\_check\_mark: | :white\_check\_mark: |
| 启动时启动   | :white\_check\_mark: | :white\_check\_mark: |
| 直接导入器   | :white\_check\_mark: |                      |
| 安全存储    | :white\_check\_mark: | :white\_check\_mark: |
| 进程隔离    | :white\_check\_mark: | :white\_check\_mark: |

### Linux

<table><thead><tr><th>功能</th><th width="115.7265625">AppImage</th><th width="82.9921875">Snap</th><th width="96.6640625">Flatpak</th><th width="81.42578125">.deb</th><th width="82.4140625">.rpm</th></tr></thead><tbody><tr><td>自动更新</td><td>*</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td></td><td></td></tr><tr><td>桌面生物识别</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>**</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td></tr><tr><td>扩展生物识别</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td></tr><tr><td>与操作系统集成</td><td>*</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td></tr><tr><td>启动时启动</td><td></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td></tr><tr><td>直接导入器</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td></td><td></td><td></td><td></td></tr><tr><td>安全存储</td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>***</td><td>***</td><td>***</td><td>***</td></tr><tr><td>进程隔离</td><td>****</td><td></td><td><span data-gb-custom-inline data-tag="emoji" data-code="2705">✅</span></td><td>****</td><td>****</td></tr></tbody></table>

\* - 可以使用 AppImageLauncher 等应用程序进行设置。

\*\* - 需要通过 Polkit 手动安装[此策略 ](https://github.com/bitwarden/clients/blob/main/apps/desktop/resources/com.bitwarden.desktop.policy)。

\*\*\* - 需要安装 `libsecret` 。

\*\*\*\* - 只有 `main` 进程会被隔离。

## 功能描述 <a href="#feature-descriptions" id="feature-descriptions"></a>

| 功能      | 描述                                                                                                                                                |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 自动更新    | 桌面 App 会在有最新版本可用时自动更新。                                                                                                                            |
| 桌面生物识别  | 可以使用生物识别解锁桌面 App。                                                                                                                                 |
| 扩展生物识别  | 桌面 App 可使用生物识别解锁浏览器扩展。                                                                                                                            |
| 与操作系统集成 | 桌面 App 将自动与您的桌面集成，以支持桌面快捷方式和应用程序快捷方式等功能。                                                                                                          |
| 启动时启动   | 可以将桌面 App 设置为在设备启动时自动启动。                                                                                                                          |
| 直接导入器   | 桌面 App 可以直接从受支持的网页浏览器凭据管理器（例如 Google Password Manager）导入数据。                                                                                       |
| 安全存储    | <p>桌面 App 将根据操作系统方法安全地存储访问令牌和生物识别解锁数据：</p><p>- 在 Windows 中，使用 Windows 凭据管理器。<br>- 在 macOS 中，使用钥匙串。<br>- 在 Linux 中，使用 <code>libsecret</code> 。</p> |
| 进程隔离    | 桌面 App 将组件分离到不同的沙盒进程中，这样即使某个组件被攻破，攻击者也无法轻易访问其他进程中的敏感数据（例如加密密钥）或系统资源。                                                                              |

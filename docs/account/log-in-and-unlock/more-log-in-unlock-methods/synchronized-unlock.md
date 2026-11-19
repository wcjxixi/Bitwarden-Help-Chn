# =同步解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/synchronized-unlock/)
{% endhint %}

同步解锁功能可将同一设备上 Bitwarden 网页 App、浏览器扩展和桌面 App 的锁定状态关联起来。当您锁定或解锁其中一个已连接的 App 时，其他 App 也会同步锁定或解锁。

{% hint style="info" %}
同步解锁需要浏览器扩展、桌面 App 和网页 App 的 2026.11.0 或更高版本。
{% endhint %}

## 激活同步解锁 <a href="#activate-synchronized-unlock" id="activate-synchronized-unlock"></a>

浏览器扩展和网页 App 之间的同步解锁功能**始终开启**。要同时与桌面 App 同步：

1、请确保 Bitwarden 桌面 App 已安装、正在运行，并且登录到与浏览器扩展相同的账户。

2、在浏览器扩展中，选择**设置** → **账户安全**。

3、开启**与桌面同步解锁**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/5uoOeDjt0aLoFxbYUEOin2/09a633499b6e43959e63ee6d15170e1c/2026-11-12_15-41-42.png?w=1400&#x26;fm=avif" alt=""><figcaption><p>激活同步解锁</p></figcaption></figure></div>

4、如果您的浏览器询问是否允许 Bitwarden 与协作的本地应用程序通信的权限，请选择**允许**。

要使同步解锁功能生效，桌面 App 必须处于运行状态。打开桌面 App 的设置，然后激活**登录时自动启动**选项，以使使用过程更加顺畅。

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

### App 间连接 <a href="#connecting-between-apps" id="connecting-between-apps"></a>

同步解锁共享**解锁状态**，而非登录状态，因此您需要先登录每一个 App。App 成对连接：

* 浏览器扩展和网页 App 在同一浏览器中打开时。
* 浏览器扩展和桌面 App。

{% hint style="info" %}
同步解锁仅适用于同一台计算机上的 App。移动 App 不会与计算机上的 App 共享信任关系或解锁状态。
{% endhint %}

网页 App 和桌面 App 不直接连接，而是通过浏览器扩展保持同步。由于连接是链式的，因此计算机上所有已连接的 App 共享同一个锁定状态。



同步解锁功能适用于登录到同一账户的 App 之间。如果您登录了多个账户，则每个账户会单独同步。

### 支持的 App <a href="#supported-apps" id="supported-apps"></a>

Windows、macOS 和 Linux 系统均支持同步解锁：

| 浏览器    | 与桌面 App 同步 | 与网页 App 同步 |
| ------ | ---------- | ---------- |
| Chrome | 是          | 是          |
| Edge   | 是          | 是          |
| Safari | 否          | 否          |

以下平台目前不受支持：

* 在 Linux 上以 Snap 格式安装的浏览器
* 从 Microsoft Store 安装的桌面 App
* Safari
* Bitwarden CLI
* 移动 App

### 对其他设置的影响 <a href="#impact-on-other-settings" id="impact-on-other-settings"></a>

#### 生物识别 <a href="#biometrics" id="biometrics"></a>

同步解锁会取代浏览器扩展的生物识别解锁设置。如果**与桌面同步解锁**已开启，并且桌面 App 中的**使用生物识别解锁**也已开启，则您也可以使用生物识别解锁浏览器扩展。更多信息，请参阅[使用生物识别解锁](unlocking-with-biometrics.md)。

#### PIN 码 <a href="#pin" id="pin"></a>

App 之间的 PIN 码互不共享，每个 App 都拥有自己的 PIN 码。使用 PIN 码解锁任何一个 App，即可解锁所有已连接的 App。

#### 会话超时 <a href="#session-timeout" id="session-timeout"></a>

如果开启了同步解锁，则一个 App 的会话超时将应用于所有已连接的 App，其他 App 中的超时设置将不可用：

* 当浏览器扩展和网页 App 连接时，以浏览器扩展的超时设置为准。
* 当浏览器扩展和桌面 App 连接时，以桌面 App 的超时设置位为准。这也使得**系统锁定时**选项同时适用于浏览器扩展和网页 App。

更多信息，请参阅[自动注销或锁定](../vault-timeout-options.md)。

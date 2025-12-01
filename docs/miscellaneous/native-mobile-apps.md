# 原生移动 App

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/native-mobile-apps-release/)
{% endhint %}

在**将来的**发布中，通过 Apple App Store 和 Google Play Store 下载的 Bitwarden Password Manager 移动 App 将升级为 [iOS 和 Android 原生移动应用程序](https://bitwarden.com/blog/native-mobile-apps/)：

* 在此发布之后**安装** Bitwarden 的用户将始终获得新的原生应用程序。
* 设备上**已经安装了 Bitwarden** 的用户将分阶段接收到新的原生应用程序。

{% hint style="danger" %}
原生移动应用程序对操作系统的要求比 Xamarin 应用程序更严格：

* Android 用户必须使用 Android 10 或更高版本。了解[如何检查您的 Android 版本](https://support.google.com/android/answer/7680439?hl=zh-Hans)。
* iOS 用户必须使用 iOS 15.0 或更高版本。了解[如何检查您的 iOS 版本](https://support.apple.com/zh-cn/109065)。

如果您的设备不符合这些版本要求，您的 Bitwarden 移动 App 将保留为在此更改之前可用的最新版本。
{% endhint %}

> **\[译者注]**：
>
> * Native Applications：原生应用程序。专门为特定移动操作系统（如 iOS 或 Android）开发的应用程序。能够充分利用设备的硬件和操作系统功能，提供高性能和流畅的用户体验。
> * Xamarin Applications：使用跨平台开发工具 Xamarin 框架开发的移动应用程序。

**\[译者注]**：

**Xamarin Applications 和 Native Mobile Applications 的区别：**

| 特性       | Native Applications                       | Xamarin Applications     |
| -------- | ----------------------------------------- | ------------------------ |
| **开发语言** | iOS：Swift/Objective-C；Android：Java/Kotlin | 使用 C# 和 .NET             |
| **代码共享** | 每个平台需单独编写代码，无法共享                          | 可以共享大部分业务逻辑代码，UI 代码需部分定制 |
| **性能**   | 最佳性能，直接调用平台原生 API                         | 接近原生性能，但可能略低于纯原生 App     |
| **开发效率** | 较低，需为每个平台单独开发                             | 较高，一套代码可覆盖多个平台           |
| **维护成本** | 较高，需为每个平台单独维护                             | 较低，只需维护一套代码库             |
| **用户体验** | 完全符合平台设计规范，用户体验最佳                         | 接近原生，但可能略有差异             |
| **适用场景** | 适合对性能和用户体验要求极高的项目                         | 适合需要快速开发且预算有限的项目         |


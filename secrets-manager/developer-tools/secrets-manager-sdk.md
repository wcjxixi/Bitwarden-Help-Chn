# 机密管理器 SDK

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-sdk/)
{% endhint %}

Secrets Manager 软件开发工具包 (SDK) 可帮助开发人员创建用于机密管理的应用程序。Bitwarden 团队将使用 Secrets Manager SDK 来构建与 [GitHub Actions](https://bitwarden.com/help/github-actions-integration/) 等流行产品的离散集成，并且社区可以使用它来构建自己的应用程序。

核心 SDK（可在[这里](https://github.com/bitwarden/sdk)找到）是用 Rust 编写的，并提供 Rust API、CLI 和 Node-API 绑定。选择 Rust 是因为它的内存安全性、对我们计划构建集成的编程语言的大量绑定，以及它对 WebAssembly 的支持。

测试版发布时提供的 SDK，如构建在其上的 Secrets Manager CLI，可用于执行以下操作：

* 使用[访问令牌](../your-secrets/access-tokens.md)进行身份验证。
* 获取[工程](../your-secrets/projects.md)中的单个或所有[机密](../your-secrets/secrets.md)。
* 列出所有机密，工程中的机密，或工程。

[立即开始使用 SDK](https://github.com/bitwarden/sdk)。

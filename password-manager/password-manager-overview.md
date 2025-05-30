# Password Manager 概述

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/password-manager-overview/)
{% endhint %}

Bitwarden Password Manager 使企业和个人能够在面临不断上升的网络犯罪威胁时保护其在线数据。使用 Bitwarden Password Manager 为您在线使用的每个账户生成强大而唯一的密码。这样一来，如果一个站点遭受数据泄露，您的其他账户都不会受到损害。Password Manager 通过创建、保存和自动填充这些强密码，让您可以轻松地做到这一点，这样您就不必担心记住它们。

## 主要特点 <a href="#key-features" id="key-features"></a>

对于个人和最终用户，Bitwarden Password Manager 提供了一些最受欢迎的功能：

* **轻松导入**：从几乎任何密码管理解决方案中[导入](../import-export/import-data-to-your-vault.md)您的凭据。
* **健全的自动填充**：使用密码管理器从[浏览器扩展](autofill/autofill-from/autofill-from-browser-extensions.md)和[移动 App](autofill/autofill-from/autofill-from-ios.md) 更轻松地登录网站。
* **凭据生成器**：在注册新网站时，使用[用户名和密码生成器](vault-basics/generator.md)自信地创建安全凭据。
* **集成身份验证**：直接从 Bitwarden Password Manager [生成并自动填写 2FA 的 TOTP 代码](../your-vault/totp.md)。
* **两步登录选项**：设置各种[两步登录方法](../two-step-login/two-step-login-methods.md)（包括免费选项），以确保您的重要凭据的安全。

对于企业和管理员，Bitwarden Password Manager 提供的一些最受欢迎的功能是：

* **轻松导入**：从几乎任何密码管理解决方案[导入](../import-export/import-data-to-an-organization.md)公司的共享凭据。
* **用户管理集成**：使用众多[跨域身份管理 (SCIM)](../scim/about-scim.md) 或[直接到目录](../directory-connector/about-directory-connector.md)集成之一来将最终用户同步到您的 Bitwarden 组织。
* **SSO 登录**：通过任何 SAML 2.0 或 OIDC 身份提供程序，[使用现有 SSO 设置对最终用户进行身份验证](../login-with-sso/about-login-with-sso.md)。
* **健全的策略**：为您的最终用户实施安全实践，例如使用企业策略为管理员设置恢复丢失账户的功能。

## 安全第一原则 <a href="#security-first-principles" id="security-first-principles"></a>

Bitwarden 致力于打造安全第一的产品。密码管理器是：

* **开源**：所有源代码都托管在 GitHub 上，任何人都可以免费查看和审核。第三方审计公司和安全研究人员有偿定期进行审计。
* **端到端加密**：密码库数据的所有加密和解密均在客户端完成，这意味着任何敏感数据都不会未经加密而进入我们的服务器。
* **零知识加密**：Bitwarden 团队成员无法查看您的密码库数据，包括密码管理器中未加密的 URL 等数据，以及您的主密码。

## 客户端 <a href="#clients" id="clients"></a>

Password Manager 为大多数设备和许多用例提供客户端应用程序：

* **网页 App**：Password Manager 网页 App 是您进行密码库管理和组织管理的主页。[立即开始入门](../getting-started/getting-started-webvault.md)。
* **浏览器扩展**：Password Manager 浏览器扩展非常适合自动填写和无缝创建凭证，使网上冲浪更加轻松。立即开始[入门](../getting-started/getting-started-browserext.md)。
* **移动 App**：Password Manager 移动 App 旨在帮助您随时随地安全地获取凭据。立即开始[入门](../getting-started/getting-started-mobile.md)。
* **桌面 App**：Password Manager 桌面 App 为您的桌面带来完整、优雅的密码库体验。立即开始[入门](../getting-started/getting-started-desktop.md)。
* **CLI**：Password Manager CLI 是一款功能强大、功能齐全的工具，可用于访问和管理您的密码库，并且非常适合帮助自动化或开发工作流程。立即开始[入门](developer-tools/password-manager-cli.md)。

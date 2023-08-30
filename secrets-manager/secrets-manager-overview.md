# Secrets Manager 概述

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/secrets-manager-overview/)
{% endhint %}

Bitwarden Secrets Manager 使开发人员、DevOps 和网络安全团队能够大规模集中存储、管理和部署机密。使用 Secrets Manager 可以：

* **在整个开发生命周期中管理和部署机密**。开发一种安全且系统的方法来为您的所有资源和应用程序创建和自动化机密。
* **提高工作效率，安全协作**。在您的开发团队中安全地共享、检索和分配秘密 - 不再需要硬编码机密或通过电子邮件、git 或消息系统共享它们。
* **提升保护水平**。为实现全面的企业安全覆盖，将机密管理功能与密码管理相结合。

## 关键概念 <a href="#key-concepts" id="key-concepts"></a>

Secrets Manager 使用的核心范例是以下关系：

* [**机密**](your-secrets/secrets.md)：敏感的键值对，如 API 密钥，您的组织需要安全地存储它们，并且永远不应以明码形式公开或通过未加密的渠道传输。
* [**工程**](your-secrets/projects.md)：按逻辑组合在一起的机密集合，供您的 DevOps 和网络安全团队进行可管理的访问。
* [**服务账户**](your-secrets/service-accounts.md)：非人类机器用户，如应用程序或部署管道，需要对一组谨慎的机密进行编程式访问。
* [**访问令牌**](your-secrets/access-tokens.md)：一组密钥，有助于服务账户访问和解密存储在您的密码库中的机密。

Secrets Manager 旨在保护和管理您在特权开发人员环境中高度敏感的凭据。多向访问层和权限级别将确保只有经过身份验证的机器和具有正确权限的人员才能查看或操作存储在您的密码库中的机密：

{% embed url="https://bitwarden.com/_gatsby/image/0a35ee7adec51f22639ee5a0cb8d40a8/df3d74ff52a7f409cfdddc70d8d1be60/Marketing%20Diagrams%202023%20-%20Baylor%20WIP%20(1).webp?eu=dcdc56e1e5cbfb860f68a0d16d24326ab13952f8f70731d66962ecfe4af99ed377f41d53739c2ce2253a098bd2e117b263c17b691fe7d08e94ee1bf3bc32a308028a08ea66bb2156037d90fbb2fc0e4d61c7130cf3d7c95ba56d7085e7e7b7791e501b23fa7cb986e8ff666ce4877a64e2bea37d6f9aef3ca051544bd4412cad33eed3c0605ab89ff35cbaa2adb75798d8f82a451e88b56f232144421fea32b9c2c304036d49172a46b4d706a567eeb45f6d37265c4050fe3633d804ad3a63c0e4aaa55dd97d7fe1fc9d38738fc2fd82e412aa2822e2d05af8c0602f4a54f244c2c822a685265753c245f8954eb16c185a32d355d57b62b65f26ec68ebe0288d68a239&a=w%3D850%26h%3D478%26fm%3Dwebp%26q%3D75&cd=2023-03-22T18%3A51%3A20.506Z" %}
Secrets Manager 示意图
{% endembed %}

## 安全第一原则 <a href="#security-first-principles" id="security-first-principles"></a>

Bitwarden 致力于打造安全至上的产品。与 Password Manager 一样，Secrets Manager 也具有：

* **开源**：所有源代码都托管在 GitHub 上，任何人都可以免费查看和审计。第三方审计公司和安全研究人员会定期获得报酬。
* **端到端加密**：机密数据的所有加密和解密都在客户端完成，这意味着敏感数据不会在未加密的情况下到达我们的服务器。
* **零知识加密**：Bitwarden 团队成员无法看到您的机密、您的密码或您的主密码。

## 客户端 <a href="#clients" id="clients"></a>

在测试期间，Secrets Manager 将提供 Web 应用程序、CLI 和 SDK。未来会支持更多的 SDK 库。

### 网页密码库 <a href="#web-vault" id="web-vault"></a>

[Secrets Manager Web 应用程序](get-started/secrets-manager-quick-start.md)是您设置机密管理基础设施的主页。您将使用它来添加和组织机密、创建适合您需要的权限系统，以及生成供您的应用程序使用的访问令牌。

### CLI

[Secrets Manager CLI](developer-tools/secrets-manager-cli.md) 是将机密信息注入应用程序和基础设施的主要工具。您将使用它编写脚本，通过经过身份验证的服务账户将机密注入到您的应用程序中。

### SDK

[Secrets Manager 软件开发工具包 (SDK)](developer-tools/secrets-manager-sdk.md) 可帮助开发人员创建用于机密管理的应用程序。Bitwarden 团队使用 Secrets Manager SDK 构建与 GitHub Actions 等流行产品的谨慎集成，并且社区可以使用它来构建自己的应用程序。

## 开始吧 <a href="#get-started-today" id="get-started-today"></a>

我们很高兴能参与您的机密管理之旅，也很高兴您能加入我们的新冒险之旅。Secrets Manager 目前在公开测试计划中。[立即了解如何加入](../miscellaneous/beta-signup.md)。

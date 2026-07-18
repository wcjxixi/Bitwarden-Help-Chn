# 企业版 Bitwarden 功能数据表

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/enterprise-feature-list/)
{% endhint %}

本文档描述并引用了 [Bitwarden 企业版组织](https://bitwarden.com/products/business/)在以下几个类别中可用的功能：

## 应用程序范围和易用性 <a href="#application-range-and-ease-of-use" id="application-range-and-ease-of-use"></a>

<table><thead><tr><th width="305.15182672540476">企业版功能</th><th>描述</th></tr></thead><tbody><tr><td>部署选项</td><td>云、私有云，以及自托管。</td></tr><tr><td>网页应用程序</td><td><a href="https://vault.bitwarden.com">https://vault.bitwarden.com</a> 或您的自托管服务器上的完全加密的云端网页 App。</td></tr><tr><td>移动 App（带有移动登录控制）</td><td>适用于 iOS 和 Android，<a href="../../password-manager/getting-started/getting-started-mobile.md">了解更多</a>。</td></tr><tr><td>浏览器扩展</td><td>适用于 Chrome、Firefox、Opera、Edge、Vivaldi、Brave、Tor，以及 Safari。<a href="../../password-manager/getting-started/getting-started-browserext.md">了解更多</a>。</td></tr><tr><td>桌面应用程序</td><td>适用于 Windows、Mac 和 Linux。<a href="../../password-manager/getting-started/getting-started-desktop.md">了解更多</a>。</td></tr><tr><td>命令行界面 (CLI)</td><td>适用于 Windows、Mac 和 Linux。<a href="../../password-manager/developer-tools/cli/password-manager-cli.md">了解更多</a>。</td></tr></tbody></table>

## 管理功能和管理能力 <a href="#administrative-features-and-capabilities" id="administrative-features-and-capabilities"></a>

<table><thead><tr><th width="194.57409144628053">企业版功能</th><th>描述</th></tr></thead><tbody><tr><td>简易用户管理</td><td>直接从网页密码库添加或删除席位以及入职或离职用户。<a href="../manage-members/user-management.md">了解更多</a>。</td></tr><tr><td>基于角色的访问控制</td><td>为组织用户分配基于角色的访问权限，包括自定义角色和精细化权限（例如隐藏密码、只读）。<a href="../manage-members/member-roles.md">了解更多</a>。</td></tr><tr><td>目录同步</td><td>将您的 Bitwarden 组织与您现有的用户目录同步。布建和取消布建用户、群组，以及群组关联。<a href="../manage-members/directory-connector/about-directory-connector.md">了解更多</a>。</td></tr><tr><td>SCIM 支持</td><td>使用 SCIM 协议从身份提供程序或目录服务管理和配置 Bitwarden 用户、群组和群组关联，以方便入职和员工继任。<a href="../manage-members/scim/about-scim.md">了解更多</a>。</td></tr><tr><td>账户恢复管理</td><td>如果员工丢失了访问权限，指定的管理员可以重置最终用户账户的主密码。<a href="../manage-members/account-recovery/about-account-recovery.md">了解更多</a>。</td></tr><tr><td>具有精选访问权限和基于角色的访问控制 (RBAC) 的集合</td><td>创建包含无限数量密码的无限数量密码集合。 集合可分配给群组或个人用户。<a href="../manage-shared-items/collections/about-collections.md">了解更多</a>。</td></tr><tr><td>企业策略</td><td>为所有用户强制执行安全规则，例如强制使用两步登录。<a href="../oversight-visibility/enterprise-policies.md">了解更多</a>。</td></tr><tr><td>声明域名与账户</td><td>管理员可以声明电子邮箱域名的所有权，从而让组织能够控制使用公司电子邮箱地址注册的 Bitwarden 账户，即使这些用户尚未正式入职。<a href="../oversight-visibility/claimed-domains/claimed-domains.md">了解更多</a>。</td></tr><tr><td>临时密码共享和生成</td><td>使用 Bitwarden Send 创建和共享临时数据。<a href="../../password-manager/bitwarden-send/about-send.md">了解更多</a>。</td></tr><tr><td>托管客户端部署支持</td><td>使用 Microsoft Intune、GPO 和 Linux/macOS 策略文件等 MDM 工具，大规模部署浏览器扩展、桌面 App 和移动 App。<a href="../deploy-client-apps/deploy-browser-extensions-with-intune.md">了解更多</a>。</td></tr><tr><td>适用于用户的免费家庭版方案</td><td>所有企业用户均可获得一份免费的家庭版方案，供个人在工作场所之外使用，以培养良好的安全习惯。<a href="../manage-members/sponsored-families/sponsored-families-for-members.md">了解更多</a>。</td></tr></tbody></table>

## 报告 <a href="#reporting" id="reporting"></a>

<table><thead><tr><th width="179.2770448548813">企业版功能</th><th>描述</th></tr></thead><tbody><tr><td>Access Intelligence</td><td>获取组织密码库中风险或异常访问模式的可操作的可见性，帮助安全团队主动识别并解决凭据健康问题。Access Intelligence。</td></tr><tr><td>密码库健康报告</td><td>运行报告以检测泄露密码、重复使用密码、弱密码等问题。<a href="../../password-manager/your-vault/security-tools/vault-health-reports.md">了解更多</a>。</td></tr><tr><td>数据泄露报告</td><td>运行报告以检测在已知泄露事件中数据泄露（电子邮箱地址、密码、信用卡、DoB 等）。<a href="../../password-manager/your-vault/security-tools/vault-health-reports.md">了解更多</a>。</td></tr><tr><td>可审计的事件日志及 SIEM 集成</td><td><p>获取组织密码库内发生的带时间戳的事件记录，以便在网页密码库中直接使用或由 SIEM 工具进行数据摄取。</p><p></p><p>内置集成包括 Splunk、Microsoft Sentinel、Elastic、Rapid7、Panther 和 Sumo Logic。其他工具可通过 API 调用获得支持。<a href="../oversight-visibility/event-logging/event-logs.md">了解更多</a>。</p></td></tr></tbody></table>

## 身份验证 <a href="#authentication" id="authentication"></a>

<table><thead><tr><th width="200.92256676823803">企业版功能</th><th>描述</th></tr></thead><tbody><tr><td>使用于个人的 2FA</td><td>适用于任何 Bitwarden 用户的一组强大的 2FA 选项。<a href="../../account/two-step-login/setup-two-step-login/two-step-login-methods.md">了解更多</a>。</td></tr><tr><td>组织层面的 2FA</td><td>通过 Duo 为整个组织启用 2FA。<a href="../../account/two-step-login/setup-two-step-login/two-step-login-via-duo.md">了解更多</a>。</td></tr><tr><td>生物识别验证</td><td>适用于浏览器扩展、桌面和移动 App。<a href="../../account/log-in-and-unlock/more-log-in-unlock-options/unlocking-with-biometrics.md">了解更多</a>。</td></tr><tr><td>设备登录</td><td>用户可通过受信任设备批准登录，而无需输入主密码，在保持安全性的同时减少操作。<a href="../../account/log-in-and-unlock/more-log-in-unlock-options/log-in-with-device.md">了解更多</a>。</td></tr><tr><td>通行密钥登录</td><td>用户可以通过支持 WebAuthn PRF 扩展的 FIDO 兼容的通行密钥，在网页 App 和浏览器扩展（适用于兼容浏览器）中登录。通行密钥登录不需要两步登录、主密码和登录电子邮箱，因此该方法非常适合作为应急管理员账户。<a href="../../account/log-in-and-unlock/more-log-in-unlock-options/log-in-with-passkeys.md">了解更多</a>。</td></tr><tr><td>新设备登录验证</td><td>当从未识别的设备发起登录尝试，且账户未设置两步登录或不受 SSO 策略约束时，系统会要求验证以防止未经授权的访问。<a href="../../account/log-in-and-unlock/new-device-protection.md">了解更多</a>。</td></tr><tr><td>受信任设备 SSO</td><td>受信任设备 SSO 允许用户使用 SSO 进行身份验证，并使用设备存储的加密密钥解密其密码库，而无需输入主密码。<a href="../login-with-sso/trusted-devices/about-trusted-devices.md">了解更多</a>。</td></tr><tr><td>SSO 登录</td><td>利用您现有的身份提供程序 (IdP) 通过 SAML 2.0 或 OpenID Connect (OIDC) 对您的 Bitwarden 组织用户进行身份验证。<a href="../login-with-sso/about-sso.md">了解更多</a>。<br><br>使用 SSO 登录，您可以选择两种解密选项之一来确定用户在通过身份验证后如何解密密码库数据。<a href="../login-with-sso/sso-decryption-options.md">了解更多</a>。</td></tr><tr><td>客户管理的加密 SSO</td><td>员工使用 SSO 凭据进行身份验证和解密，只需一个步骤。该方案将用户主密码的保管责任转移给企业，要求企业部署 Key Connector 来存储用户密钥。<a href="../../self-hosting/key-connector/about-key-connector.md">了解更多</a>。</td></tr></tbody></table>

## 安全性 <a href="#security" id="security"></a>

<table><thead><tr><th width="207">企业版功能</th><th>描述</th></tr></thead><tbody><tr><td>用于登录、笔记、支付卡和身份的安全存储</td><td>Bitwarden <a href="../../password-manager/your-vault/vault-items/vault-items.md">密码库项目</a>在存储在任何地方之前均经过加密处理。<a href="../../security/encryption/encryption-protocols.md">了解更多</a>。</td></tr><tr><td>零知识加密</td><td>所有密码库数据都采用端到端加密。<a href="https://bitwarden.com/blog/post/bitwarden-network-security-assessment-2020/">了解更多</a>。</td></tr><tr><td>安全的密码生成器</td><td>为每个密码库项目生成安全、随机且唯一的凭据。<a href="https://bitwarden.com/password-generator/">了解更多</a>。</td></tr><tr><td>加密导出</td><td>下载加密导出以安全地存储密码库数据备份。<a href="../../password-manager/import-and-export/encrypted-exports.md">了解更多</a>。</td></tr><tr><td>生物识别验证</td><td>适用于浏览器扩展、桌面和移动 App。<a href="../../account/log-in-and-unlock/more-log-in-unlock-options/unlocking-with-biometrics.md">了解更多</a>。</td></tr><tr><td>紧急访问</td><td>用户可以指定和管理受信任的紧急联系人，紧急联系人可以在紧急情况下请求访问他们的密码库。<a href="../../account/emergency-access/about-emergency-access.md">了解更多</a>。</td></tr><tr><td>账户指纹短语</td><td>在执行与加密相关或入职操作时唯一且安全地标识 Bitwarden 用户账户的一种安全措施。<a href="../../security/encryption/account-fingerprint-phrase.md">了解更多</a>。</td></tr><tr><td>密码库超时与锁定企业策略</td><td>强制执行组织范围内的超时和锁定设置，以降低非活动会话的暴露风险。<a href="../oversight-visibility/enterprise-policies.md#session-timeout">了解更多</a>。</td></tr><tr><td>分包商</td><td>查看完整的分包商列表：<a href="../../security/who-are-bitwardens-subprocessors.md">Bitwarden 的分包商</a>。</td></tr></tbody></table>

## 合规，审计，认证 <a href="#compliance-audits-certifications" id="compliance-audits-certifications"></a>

| 企业版功能                 | 描述                                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------- |
| SOC 2 Type II 和 SOC 3 | [了解 Bitwarden 的 SOC 认证](https://bitwarden.com/blog/bitwarden-achieves-soc-2-certification/)。      |
| ISO 27001             | Bitwarden 已获得 ISO 27001 认证，并符合围绕数据安全的 ISO 27001 控制集要求。                                            |
| 安全和合规性评估              | Bitwarden 投资每年的第三方审计、安全评估和其他合规标准。所有报告均可在 [Bitwarden 合规性页面](https://bitwarden.com/compliance/)上查阅。 |
| GDPR、CCPA、HIPAA 和隐私保护 | [了解 Bitwarden 对各种隐私框架的遵守情况](https://bitwarden.com/compliance/)。                                   |
| 白盒测试                  | 由单元测试和 QA 工程师执行。                                                                                  |
| 黑盒测试                  | 通过自动化或手动测试执行。                                                                                     |
| Bug 赏金计划              | 通过 HackerOne 实施。[了解更多](https://hackerone.com/bitwarden/?type=team)。                               |

## API 和可扩展性 <a href="#apis-and-extensibility" id="apis-and-extensibility"></a>

| 企业版功能           | 描述                                                                                                                                                                                                                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 编程无障碍           | 用于组织的公共和私有 API。[了解更多](../bitwarden-public-api.md)。                                                                                                                                                                    |
| 命令行界面           | 功能齐全的自文档命令行工具。[了解更多](../../password-manager/developer-tools/cli/password-manager-cli.md)。                                                                                                                             |
| 可扩展性支持          | 结合 API​​ 和 CLI 进行自动化工作流程。                                                                                                                                                                                             |
| SSH 代理          | Bitwarden 桌面 App 可作为 SSH 代理使用，安全地存储 SSH 密钥并将其提供给终端和开发工具，而无需将私钥暴露在磁盘上。[了解更多](../../password-manager/developer-tools/ssh/ssh-agent.md)。                                                                                 |
| Secrets Manager | 一款专为 DevOps 和工程团队设计的专用机密管理产品（需单独订阅），用于安全地存储、共享机密信息（如 API 密钥、令牌、凭证），并将其注入 CI/CD 流水线和基础设施工具中。支持与 GitHub Actions、GitLab CI/CD、Ansible、Terraform 及 Kubernetes 集成。[了解更多](https://bitwarden.com/products/secrets-manager/)。 |

## 适应性 <a href="#resiliciency" id="resiliciency"></a>

| 企业版功能       | 描述                                                                                                                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 服务器地理位置     | 选择将您的云端数据托管在基于 US 或 EU 的 Microsoft Azure 服务器上。[了解更多](../../security/server-geographies.md)。                                                                                     |
| 本地缓存 & 离线访问 | 已登录的客户端可以通过设备上保留 30 天的只读缓存访问 Bitwarden 密码库。[了解更多](../../security/security-faqs.md)。                                                                                             |
| 数据备份工具      | 除了可通过脚本执行的密码库导出功能外，自托管部署还可使用[工具集辅助数据备份](../../self-hosting/backup-server-data.md)与恢复。云端部署则依托 [Azure 时间点恢复策略](../../security/data/data-storage.md#on-bitwarden-servers)实现灾难恢复支持。 |
| 专属客户支持      | 企业客户享有优先支持，并可获取专属的客户成功资源，包括入职手册、[客户成功中心](../onboarding/customer-success-hub.md)及直接支持渠道。[了解更多](https://bitwarden.com/products/business-support/)。                                |

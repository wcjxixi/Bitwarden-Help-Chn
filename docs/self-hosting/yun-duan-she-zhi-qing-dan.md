# \*云端设置清单

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/cloud-setup-checklist/)
{% endhint %}

使用云托管，Bitwarden 管理基础设施、安全和运营责任。使用此清单了解云部署的组织和用户管理要求。

## 部署前规划 <a href="#pre-deployment-planning" id="pre-deployment-planning"></a>

* 确定云服务器区域（美国、欧盟）
* 选择认证策略（电子邮件或身份提供程序 SSO）
* 选择加密类型（主密码或可信任设备）
* 定义用户配置方法（手动、目录连接器、SCIM、即时 SSO）
* 定义密码库所有权策略（个人密码库与仅限组织）
* 确定分阶段推广的用户群组

**支持链接：**

* [服务器地理位置](../security/server-geographies.md)
* [Bitwarden 身份验证指南](https://bitwarden.com/resources/reference-guide-bitwarden-authentication/)
* [Bitwarden 实施指南](https://bitwarden.com/resources/bitwarden-enterprise-password-manager-implementation-guide/)

## 利益相关者选择 <a href="#stakeholder-selections" id="stakeholder-selections"></a>

选择关键角色：

* 项目负责人
* 身份提供程序管理员
* 执行赞助人
* 安全和合规管理员
* 支持/帮助台管理员
* 设备管理管理员（用于客户端部署）
* 业务连续性管理员
* 目录/用户管理管理员

## 安全和合规决策 <a href="#security-and-compliance-decisions" id="security-and-compliance-decisions"></a>

* 确定云服务器区域（美国、欧盟）
* 选择认证策略（电子邮件或身份提供程序 SSO）
* 选择加密类型（主密码或可信任设备）
* 定义用户配置方法（手动、目录连接器、SCIM、即时 SSO）
* 定义密码库所有权策略（个人密码库与仅限组织）
* 确定分阶段推广的用户群组

**支持链接：**

* [SSO 集成](../admin-console/login-with-sso/about-login-with-sso.md)
* [SCIM](../admin-console/manage-members/scim/about-scim.md)
* [目录连接器](../admin-console/manage-members/directory-connector/directory-connector-cli.md)

## 组织构建和配置 <a href="#organizational-build-out-and-configuration" id="organizational-build-out-and-configuration"></a>

* 确定组织所有者（建议两个以实现冗余）
* 向组织中添加其他管理员
* 在邀请用户前配置企业策略
* 选择集合管理设置
* 为管理员和用户创建集合以共享
* 为管理用户创建群组
* 将集合分配给群组
* 测试「只读」和「隐藏密码」选项
* 向集合中添加测试项目

**支持链接：**

* [Bitwarden 实施指南](https://bitwarden.com/resources/bitwarden-enterprise-password-manager-implementation-guide/)
* [最小权限访问](https://bitwarden.com/blog/additional-enterprise-options-for-least-privileged-access-control/#flexible-collections-options-for-your-organization)

## 用户配置和目录集成 <a href="#user-provisioning-and-directory-integration" id="user-provisioning-and-directory-integration"></a>

* 在管理控制台中启用 SCIM 配置
* 配置身份提供程序
* 映射用户属性和群组成员资格
* 测试 SCIM 同步
* 下载和安装目录连接器
* 配置同步筛选器，用户/群组映射

**支持链接：**

* [启用 SCIM 配置](../admin-console/manage-members/scim/about-scim.md)
* [Microsoft Entra ID SCIM 集成](../admin-console/manage-members/scim/microsoft-entra-id-scim-integration.md)
* [JumpCloud SCIM 集成](../admin-console/login-with-sso/sso-guides/jumpcloud-saml-implementation.md)
* OneLogin SCIM 集成
* [Ping Identity SCIM 集成](../admin-console/login-with-sso/sso-guides/ping-identity-saml-implementation.md)

## 部署和上线准备 <a href="#deployment-and-go-live-preparation" id="deployment-and-go-live-preparation"></a>

* 完成最终的安全审查并获得利益相关者的批准
* 设置生产监控和警报系统
* 与网络和安全团队协调上线

## 监控 <a href="#monitoring" id="monitoring"></a>

* 监控系统性能和采用指标
* 与利益相关者执行实施后回顾
* 计划持续维护和更新流程
* 记录经验教训和流程改进
* 安排定期安全审计和策略审查

**支持链接：**

* [密码库健康报告](../password-manager/your-vault/security-tools/vault-health-reports.md)

## 变更管理与培训 <a href="#change-management-and-training" id="change-management-and-training"></a>

* 为组织制定沟通计划
* 制定发布公告和里程碑的时间表
* 准备有关安全效益和投资回报率 (ROI) 的行政更新
* 安排管理员和最终用户培训
* 规划持续沟通和反馈渠道
* 建立支持流程和升级步骤

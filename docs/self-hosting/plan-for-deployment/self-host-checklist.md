# 自托管检查清单

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/self-host-checklist/)
{% endhint %}

使用此检查清单，确保在自托管环境中部署 Bitwarden 的关键利益相关方了解关键阶段和时间表。通过就这些主题达成一致，以降低延误和沟通不畅的风险。

## 利益相关者 <a href="#stakeholders" id="stakeholders"></a>

<table data-search="false"><thead><tr><th>角色</th><th>指定的团队或成员</th></tr></thead><tbody><tr><td>自托管项目负责人</td><td></td></tr><tr><td>执行发起人</td><td></td></tr><tr><td>服务器（Windows 或 Linux）管理员<br>Docker 或 Kubernetes 管理员<br>网络管理员<br>防火墙管理员<br>数据库管理员（可选）</td><td></td></tr><tr><td>身份提供程序和单点登录管理员</td><td></td></tr><tr><td>SMTP 管理员</td><td></td></tr><tr><td>安全 &#x26; 合规负责人<br>备份管理员</td><td></td></tr><tr><td>业务连续性<br>灾难恢复</td><td></td></tr><tr><td>设备管理管理员<br>支持或帮助台管理员</td><td></td></tr></tbody></table>

## 部署阶段 <a href="#deployment-stages" id="deployment-stages"></a>

### 服务器准备 <a href="#server-preparation" id="server-preparation"></a>

在部署您的 Bitwarden 服务器之&#x524D;_，_ 请先解决以下关键决策：

<table><thead><tr><th width="109.39996337890625">关键决策</th><th width="327.4000244140625">描述</th><th>指定的团队或成员</th><th>支持链接</th></tr></thead><tbody><tr><td>部署方式</td><td><p>您将在 Bitwarden 的 US 或 EU 云中部署吗？</p><p></p><p>或者在 Linux 或 Windows 上使用 Docker 自托管？或者使用 Kubernetes？</p></td><td></td><td><a href="self-host-bitwarden.md">自托管 Bitwarden</a></td></tr><tr><td>服务器配置</td><td><p>您将在服务器上使用哪些环境变量来满足组织的安全要求？</p><p></p><p>您会将服务器置于防火墙或代理后面吗？</p></td><td></td><td><a href="../deploy-and-configure/configuration-options/environment-variables.md">配置环境变量</a></td></tr><tr><td>数据库选择</td><td><p>您的服务器是否使用打包的 MSSQL 数据库或连接到单独的 MSSQL 数据库？</p><p></p><p>如果使用 Lite，您将使用不同的数据库平台吗？</p></td><td></td><td><a href="../deploy-and-configure/configuration-options/database-options.md">数据库选项</a></td></tr><tr><td>证书选择</td><td>您将使用哪种证书选项来保护传输中的数据？</td><td></td><td><a href="../deploy-and-configure/configuration-options/certificate-options.md">证书选项</a></td></tr></tbody></table>

### 推广准备 <a href="#rollout-preparation" id="rollout-preparation"></a>

在将用户入职到您的服务器之&#x524D;_，_ 请先解决以下关键决策：

<table><thead><tr><th width="107.79998779296875">关键决策</th><th width="331.4000244140625">描述</th><th>指定的团队或成员</th><th>支持链接</th></tr></thead><tbody><tr><td>管理团队</td><td>谁是管理和维护您的服务器的管理员？</td><td></td><td><a href="../system-administrator-portal.md">管理服务器</a></td></tr><tr><td>维护计划</td><td>您执行更新和执行安全审计以保证 Bitwarden 安全和最新的策略是什么？</td><td></td><td><a href="../update-a-server.md">更新服务器</a></td></tr><tr><td>备份计划</td><td><p>您对服务器、虚拟机和其他服务进行定期备份和自动备份的流程是什么？</p><p>您会进行用户级备份、虚拟机管理程序备份和数据库快照吗？</p></td><td></td><td><a href="../backup-server-data.md">备份服务器数据</a></td></tr><tr><td>灾难恢复计划</td><td>您的灾难恢复策略是什么？您将如何列举和测试灾难恢复场景？</td><td></td><td><a href="../../security/bitwarden-security-whitepaper.md#business-continuity-and-disaster-recovery">业务连续性和灾难恢复</a></td></tr><tr><td>测试</td><td>您将如何测试服务器-客户端连接、服务器性能以及维护、备份和 DR 计划？</td><td></td><td></td></tr><tr><td>合规 &#x26; 整合计划</td><td>您如何确保您的设置符合法规遵从性要求并与您现有的 IT 基础设施集成？</td><td></td><td></td></tr></tbody></table>

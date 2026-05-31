# 设置账户恢复

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery-enrollment/)
{% endhint %}

[账户恢复](about-account-recovery.md)可帮助组织成员重新获得对其账户的访问权限。企业策略激活后，成员需要注册该计划。注册会触发密钥交换，从而确保账户恢复的安全性。成员有两种注册方式：

* [自动注册](account-recovery-enrollment.md#automatic-enrollment)是最快的选项，但仅适用于策略启用后加入的成员。
* [自行注册](account-recovery-enrollment.md#self-enroll-in-account-recovery)允许成员通过网页 App 手动注册。

## 启用企业策略 <a href="#turn-on-enterprise-policy" id="turn-on-enterprise-policy"></a>

首先，启用[账户恢复管理](../../oversight-visibility/enterprise-policies.md#account-recovery-administration)策略。激活后，成员必须注册账户恢复。

## 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

当您启用**账户恢复管理**策略时，您可以选中**在账户恢复中自动注册新成员**选项。打开此设置将：

* 在新成员[进入接受状态](../user-management.md#accept)时，将自动在账户恢复中注册新成员。
* 阻止他们从账户恢复撤销。

{% hint style="danger" %}
Bitwarden 建议打开自动注册。但自动注册仅适用于策略激活**之后**加入的成员。如果您的组织在**策略启用之前**已有成员，则这些成员必须自行注册才有资格（使用账户恢复）。
{% endhint %}

如果您在账户恢复中自动注册成员，我们建议您通知他们。某些组织成员可以选择将个人凭据存储在他们自己的所有权下，并且应应该让他们该意识到账户恢复将允许管理员访问他们的个人项目。

## 自行注册 <a href="#self-enroll-in-account-recovery" id="self-enroll-in-account-recovery"></a>

如果[自动注册](account-recovery-enrollment.md#automatic-enrollment)已关闭或成员在自动注册打开之前已加入，成员必须主动选择加入。要注册账户恢复：

1、从网页 App 中，选择密码库视图中的组织旁边的 **≡选项**图标。

2、选择**注册账户恢复**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4ape19S5L7lf0tAAEyInGR/87fadad707f8c7acb5894e94e758c6c3/2024-12-03_15-33-13.png?w=1197&#x26;fm=avif" alt=""><figcaption><p>注册账户恢复</p></figcaption></figure></div>

3、输入您的**主密码**。

4、选择**提交**。

5、选择**信任**。

### 撤销注册 <a href="#withdraw-enrollment" id="withdraw-enrollment"></a>

打开了**为新成员启用自动注册**选项的组织成员**将不允许从账户恢复中撤销**，但未打开该选项的组织成员可以从用于注册的同一下拉菜单中**撤销**：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/4GR176lad9pre4sZN3rA35/642bdef55248fb84ddb24fc316875b11/2024-12-03_15-34-30.png?w=1197&#x26;fm=avif" alt=""><figcaption><p>撤销账户恢复</p></figcaption></figure></div>

手动更改您的主密码或[轮换您的加密密钥](../../../security/encryption/encryption-key-rotation.md)**不会**使成员从账户恢复中撤销。

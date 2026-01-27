# 账户恢复注册

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery-enrollment/)
{% endhint %}

成员必须注册该功能，才有资格使用[账户恢复](about-account-recovery.md)功能。注册会触发密钥交换，从而确保账户恢复的安全性。成员有两种注册方式：

* **自动注册**：当您开启[账户恢复管理策略](../../oversight-visibility/enterprise-policies.md#account-recovery-administration)时，您还可以打开**为新成员启用自动注册**选项。该选项将自动为新会员注册账户恢复。
* **自行注册**：组织成员可以按照快速流程自行注册账户恢复。

{% hint style="success" %}
Bitwarden 建议您开启自动注册功能，但在**账户恢复功能开启之前**已经加入您的组织的成员则需要自行注册。
{% endhint %}

## 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

打开**为新成员启用自动注册**选项将：

* 在新成员进入[接受](../user-management.md#accept)状态时，自动为其注册账户恢复功能。
* 阻止他们撤销账户恢复。

{% hint style="info" %}
如果您为成员使用自动注册账户恢复，我们强烈建议您通知他们这一功能。很多 Bitwarden 组织用户在他们的个人密码库中存储私人凭据，应该让他们知道账户恢复将允许管理员访问他们的个人项目。
{% endhint %}

## 自行注册 <a href="#self-enroll-in-account-recovery" id="self-enroll-in-account-recovery"></a>

如果您使用自动注册，那么在**开启账户恢复功能之前**已经是您的组织的成员将需要自行注册，或者如果您不使用自动注册，那么所有用户都将需要自行注册。

要注册账户恢复，在密码库视图种选择您的组织旁边的 **≡选项**菜单，然后选择**注册账户恢复**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4ape19S5L7lf0tAAEyInGR/87fadad707f8c7acb5894e94e758c6c3/2024-12-03_15-33-13.png?_a=DAJCwlWIZAAB" %}
注册账户恢复
{% endembed %}

### 撤销注册 <a href="#withdraw-enrollment" id="withdraw-enrollment"></a>

已打开自动注册选项的组织成员**将不允许从账户恢复中撤销**，但未打开该选项的组织成员可以从用于注册的同一下拉菜单中**撤销**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4GR176lad9pre4sZN3rA35/642bdef55248fb84ddb24fc316875b11/2024-12-03_15-34-30.png?_a=DAJCwlWIZAAB" %}
撤销账户恢复
{% endembed %}

手动更改您的主密码或[轮换您的加密密钥](../../../security/encryption/encryption-key-rotation.md)**不会**使成员从账户恢复撤销。

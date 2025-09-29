# =账户恢复注册

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/account-recovery-enrollment/)
{% endhint %}

### 自动注册 <a href="#automatic-enrollment" id="automatic-enrollment"></a>

启用自动注册策略选项将在新用户[加入组织的邀请被接受后](../user-management.md#accept)自动注册新用户的账户恢复功能。并且会阻止他们[撤销](about-account-recovery.md#withdraw-enrollment)账户恢复。

已经在组织中的用户不会被注册账户恢复，需要他们[自行注册](about-account-recovery.md#self-enroll-in-password-reset)。

{% hint style="success" %}
如果您为组织成员使用自动注册账户恢复，我们**强烈建议您通知他们这一功能**。很多 Bitwarden 组织用户在他们的个人密码库中存储私人凭据，应该让他们知道账户恢复将允许管理员访问他们的个人密码库。
{% endhint %}

### 自行注册账户恢复 <a href="#self-enroll-in-account-recovery" id="self-enroll-in-account-recovery"></a>

要注册账户恢复，在密码库视图种选择您的组织旁边的 **≡选项**菜单，然后选择**注册账户恢复**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4ape19S5L7lf0tAAEyInGR/87fadad707f8c7acb5894e94e758c6c3/2024-12-03_15-33-13.png?_a=DAJCwlWIZAAB" %}
注册账户恢复
{% endembed %}

如果您愿意，您可以在多个组织中注册账户恢复。

### 撤销注册 <a href="#withdraw-enrollment" id="withdraw-enrollment"></a>

注册后，您可以从用于注册的同一下拉菜单中**撤销**账户恢复：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4GR176lad9pre4sZN3rA35/642bdef55248fb84ddb24fc316875b11/2024-12-03_15-34-30.png?_a=DAJCwlWIZAAB" %}
撤销账户恢复
{% endembed %}

已启用[自动注册](about-account-recovery.md#automatic-enrollment)策略选项的组织中的用户将**不允许撤销**账户恢复。此外，手动更改您的主密码或[轮换您的加密密钥](../../../security/encryption/encryption-key-rotation.md)**不会**使您撤销账户恢复。

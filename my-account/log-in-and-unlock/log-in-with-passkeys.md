# =通行密钥登录（测试版）

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/login-with-passkeys/)
{% endhint %}

{% hint style="info" %}
通行密钥登录目前处于测试阶段。
{% endhint %}

通行密钥可以用来登录 Bitwarden，作为使用主密码和电子邮件的替代方式。用于登录 Bitwarden 的通行密钥需要用户验证，这意味着您需要使用生物识别因素或安全钥匙等来成功建立对通行密钥的访问。

通行密钥登录可以绕过 Bitwarden 的两步登录，但只有[支持 PRF](https://bitwarden.com/blog/prf-webauthn-and-its-role-in-passkeys/) 的浏览器和通行密钥组合才能用来设置使用通行密钥登录以进行密码库解密。不使用 PRF 的通行密钥需要在登录后输入主密码才能解密密码库。

通行密钥目前可用于登录 Bitwarden 网页应用程序，并计划在未来的版本中支持其他客户端应用程序。

{% hint style="info" %}
使用要求单点登录身份验证策略、受信任设备 SSO 或 Key Connector 的组织成员无法使用通行密钥登录。
{% endhint %}

## 创建通行密钥 <a href="#create-a-passkey" id="create-a-passkey"></a>

### 设置加密方式 <a href="#set-up-encryption" id="set-up-encryption"></a>

### 移除通行密钥 <a href="#remove-a-passkey" id="remove-a-passkey"></a>

## 使用通行密钥登录 <a href="#log-in-with-your-passkey" id="log-in-with-your-passkey"></a>

## 工作原理 <a href="#how-it-works" id="how-it-works"></a>

## 轮换加密密钥 <a href="#rotating-your-encryption-key" id="rotating-your-encryption-key"></a>

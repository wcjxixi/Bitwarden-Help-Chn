# 理解登录 & 解锁

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/understand-log-in-vs-unlock/)
{% endhint %}

Bitwarden 使用两种不同的流程来保护您的密码库，同时又不牺牲便利性：登录您的 Bitwarden 账户和解锁您的密码库。这种分离机制确保 Bitwarden [绝不会存储未经加密的数据](../../security/data/encrypted-data.md)在其服务器上。**当您的密码库既未解锁也未登录时**，您的密码库数据只以[加密形式](../../security/encryption/encryption-protocols.md)存在于服务器上。

## 登录 <a href="#logging-in" id="logging-in"></a>

**登录到** Bitwarden 可以获取已加密的密码库数据，并在本地设备上进行解密。在实践中，这意味着两件事：

* 登录始终需要使用您的主密码、[已批准的设备](more-log-in-unlock-options/log-in-with-device.md)或[已创建的通行密钥](more-log-in-unlock-options/log-in-with-passkeys.md)，以获取解密密码库数据所需的[账户加密密钥](../../security/encryption/encryption-key-rotation.md)。在此阶段也需要使用[任何已启用的两步登录方式](../two-step-login/setup-two-step-login/two-step-login-methods.md)。
* 登录始终需要连接到互联网（或者，如果是自托管，则需要连接到服务器），才能将加密的。库下载到磁盘然后，密码库将在您设备的内存中解密。。

## 解锁 <a href="#unlocking" id="unlocking"></a>

只有在您已登录的情况下才能**解锁**您的密码库。 这就意味着，根据上述章节，您的设备在磁盘上存储了**已加密**的密码库数据。在实践中，这意味着两件事：

* 您并不一定需要主密码。虽然主密码可以用来解锁密码库，但 PIN 码和生物识别等其他方式也可以用来解锁密码库。

{% hint style="info" %}
当您设置 PIN 码或生物识别时，从 PIN 码或生物识别因素中派生的新加密密钥将用于加密[账户加密密钥](../../security/encryption/encryption-key-rotation.md)，您登录后即可访问该密钥，并将其存储在磁盘<mark style="color:red;">**ª**</mark>。

**解锁**密码库会使用 PIN 码或生物识别密钥解密内存中的账户加密密钥。解密后的账户加密密钥将用于解密内存中的所有密码库数据。

**锁定**密码库会导致删除所有已解密的密码库数据，包括已解密的账户加密密钥。

<mark style="color:orange;">**ª**</mark> - 如果使用**重启时使用主密码锁定**选项，此密钥只会存储在内存中，而不会存储在磁盘上。
{% endhint %}

* 您不需要连接到互联网（或者，如果是自托管，则不需要连接到服务器）。

# 访问令牌

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/access-tokens/)
{% endhint %}

访问令牌是促进[服务账户](service-accounts.md)访问和解密存储在 Secrets Manager 中的[机密](secrets.md)的对象。访问令牌颁发给特定的服务账户，并将赋予应用它们的任何机器仅能访问**与该服务账户相关联的机密**的能力。

## 创建访问令牌 <a href="#create-an-access-token" id="create-an-access-token"></a>

访问令牌永远不会存储在 Bitwarden 数据库中并且无法检索，因此在生成访问令牌时请注意将其存储在安全的地方。要创建访问令牌：

1、从导航中选择**服务账户**。

2、选择要为其创建访问令牌的服务账户，然后打开**访问令牌**选项卡：

{% embed url="https://bitwarden.com/_gatsby/image/9ce9ddc8aa45160b5caff34b37a3e9d2/70a07780b34d25e1c964fd2e853af8e1/Screen%20Shot%202023-02-24%20at%2010.12.38%20AM.webp?eu=8edc06b7b2cdad820c6aa8d66b243469e63652fdaf073ed96832ecfa4daf9b852df41e0621902fe07d3a5a8c81e544ba35ce79691eb8d6d8c0ed1da6e361ae095b840bbb32ba7307047fc1acb7f404163e90495ca8d59a5cab6b21dce5b3e3701d061c2fa222fcc5acea3f7bafda7263bde3e5303686fd29a3510b1088062fa920a4979c6d4da894b149e7bba9ae16cbe99e537311b3aa554337455e39be52bde4b34e353c361559609bae5ac36294b76e4e32710d5f57fe6f33d904fd6530c4e0fcf45e8c7c6482fb8b6425d8accdd8b25ec32876e5cc3aa98026780a62fd57c2bd7be9d366180d89458be852f25d52&a=w%3D850%26h%3D329%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.853Z" %}
创建访问令牌
{% endembed %}

3、选择**创建访问令牌**按钮。

4、在创建访问令牌窗口中，提供以下信息：

* 令牌的**名称**。
* 令牌的**权限**级别。在 Beta 期间，只有 `可以读取` 访问权限可用。
* 当令牌**过期**时间。默认为 `从不`。

5、完成令牌配置后，选择**创建访问令牌**按钮。

6、将出现一个显示访问令牌的窗口。关闭此窗口之前请将您的令牌保存在安全的地方，因为您的令牌**不会被存储并且以后无法检索**：

{% embed url="https://bitwarden.com/_gatsby/image/36952bd7fa3514dc9b301eba61b3f256/02b860cb3c232ecb9c257c521dbb8153/Screen%20Shot%202023-02-24%20at%2010.16.14%20AM.webp?eu=dcd803e2e59bf8830e6fa7856e74666ab13805fffd0035d36f65e6af4afecb8427a2190324c72fb229685b8a86b54bbb649529331dec8688c0bf11f7b960f85906840ee864bb2105042395f6e4f70f4c60c21d5ff2819c5dab6e7280b0b2e6774d021c2fa12fee89e9ad3336b7d07e31eee0ac762186eb3bea0d410d964926a927a5c39a654fad8de55bacf8b0fc4dd29ba573540681f2632a2a0b1847ee4cede5e6671068704203438cc82f9316f5ea5d7e1f3c0b0b51f5613b8407ad6e62c1e3f2a35bd07d7ce3aecd657987c2a784ea49ad7f69849c65fcd765156d55f357c2be7bf5d179060c9c28fefa1df66c04355e831a972524b649229247dab6&a=w%3D850%26h%3D587%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.747Z" %}
访问令牌示例
{% endembed %}

此访问令牌是身份验证工具，通过它您可以编写机密注入脚本到您的机器和应用程序中。

## 使用访问令牌 <a href="#use-an-access-token" id="use-an-access-token"></a>

访问令牌用于 Secrets Manager CLI 的身份验证。您创建了访问令牌并将其值保存在安全的地方后，就可以通过 CLI 来使用它验证机密检索命令，以注入您的应用程序或基础设施。它可以：

*   将访问令牌导出到主机上的 `BWS_ACCESS_TOKEN` 环境变量。如下所示的 CLI 命令将自动检查具有该密钥的变量以进行身份​​验证：

    ```javascript
    bws get secret fc3a93f4-2a16-445b-b0c4-aeaf0102f0ffText C
    ```
*   在脚本中使用 `-access-token` 选项 `get` 和注入机密，例如包含以下行的内容：

    ```javascript
    ...
    export DB_PW=$(bws get secret fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff --access-token 0.48c78342-1635-48a6-accd-afbe01336365.C0tMmQqHnAp1h0gL8bngprlPOYutt0:B3h5D+YgLvFiQhWkIq6Bow== | .jq '.value')
    ...
    docker run -d database ... -env DB_PW=$DB_PW ... mysql:latest
    ```
* 使用我们专用的 [GitHub Actions 集成](../integrations/github-actions.md)将访问令牌保存为存储库机密，以便在您的工作流文件中使用。

## 吊销访问令牌 <a href="#revoke-an-access-token" id="revoke-an-access-token"></a>

您可以随时吊销访问令牌。吊销令牌将破坏当前使用它的任何机器检索和解密机密的能力。要吊销令牌：

1、从导航中选择**服务账户**，然后打开**访问令牌**选项卡。

2、对于要撤销的访问令牌，使用 (**☷**) 选项菜单选择**吊销访问令牌**：

{% embed url="https://bitwarden.com/_gatsby/image/78aa80da6a2461bb4c2c8574d66fb652/8edca8a5097cc14b22b9d9515be0f778/Screen%20Shot%202023-02-27%20at%209.34.40%20AM.webp?eu=da8906b7e599a9d20a3ca5836b27366ab13e5ff8fa5837853960e3aa1cae9c802df04c5029932be37f3d0bd686b545b831ce7e351dbdd5d9c1b44efcb936f95a5a8b5ae833e272045078c5f7b6f10c1d2c825a1bab9cd751fe3c2581a6ade4344f015f68fd3efb9fb2fc717bb7c17161aceca7786d9fec7fff131c11916c03bd1cc196825a57ecc8eb5eb28284ee0dd2ceee785115dff03625741a4d58ef28e9a4b20d226c7840593ccdab0cc469c3b3237f32610b0a5d9804628f11946e31c1e7e6a15fc4787c8ef98d5e7998c0aa9ee91ac35b0bf98f79fe&a=w%3D850%26h%3D261%26fm%3Dwebp%26q%3D75&cd=2023-03-22T13%3A13%3A20.623Z" %}
吊销访问令牌
{% endembed %}

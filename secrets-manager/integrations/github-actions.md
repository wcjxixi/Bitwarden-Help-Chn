# GitHub Actions

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/github-actions-integration/)
{% endhint %}

Bitwarden 提供与 GitHub Actions 的集成，以从 Secrets Manager 获取机密并将它们注入 GitHub Actions 工作流程。集成会将获取到的机密作为隐藏的环境变量注入到操作中。要设置集成：

## 保存访问令牌 <a href="#save-an-access-token" id="save-an-access-token"></a>

在此步骤中，我们将把访问令牌保存为 GitHub 加密密钥。可以为组织、存储库或存储库环境创建加密的秘密，并使其可用于 GitHub Actions 工作流程：

1. 在 GitHub 中，导航到您的存储库并选择 **Settings** 选项卡。
2. 在左侧导航的 Security 部分，选择 **Secrets and variables** → **Actions**。
3. 打开 Secrets 选项卡然后选择 **New repository secret** 按钮。
4. 在另一个选项卡中，打开 Secrets Manager Web 密码库然后[创建一个访问令牌](../your-secrets/service-accounts.md)。
5. 返回 GitHub，为您的机密命名，例如 `BW_ACCESS_TOKEN`，然后将步骤 4 中的访问令牌值粘贴到 **Secret** 输入框中。
6. 选择 **Add secret** 按钮。

## 添加到您的工作流程文件 <a href="#add-to-your-workflow-file" id="add-to-your-workflow-file"></a>

接下来，我们将向您的 GitHub Actions 工作流文件添加几个步骤。

### 获取机密 <a href="#get-secrets" id="get-secrets"></a>

要在您的工作流程中获取机密，请将包含以下信息的步骤添加到您的工作流程 YAML 文件中：

```
- name: Get Secrets
  uses: bitwarden/sm-action@v1
  with:
    access_token: ${{ secrets.BW_ACCESS_TOKEN }}
    secrets: |
      fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff > SECRET_NAME_1
      bdbb16bc-0b9b-472e-99fa-af4101309076 > SECRET_NAME_2
```

说明：

* `${{ secrets.BW_ACCESS_TOKEN }}` 是引用您之前保存的存储库机密。如果您没有将机密命名为 `BW_ACCESS_TOKEN`，则进行相应的更改。
* `fc3a93f4-2a16-445b-b0c4-aeaf0102f0ff` 和 `bdbb16bc-0b9b-472e-99fa-af4101309076` 是存储在 Secrets Manager 中的机密的参考标识符。您的访问令牌所属的服务帐户必须能够访问这些特定的机密。
* `SECRET_NAME_1` 和 `SECRET_NAME_2` 是您将在下一步中用来引用注入的机密值的名称。

### 使用机密 <a href="#use-secrets" id="use-secrets"></a>

最后，您可以通过在后续操作中引用指定的机密名称（`SECRET_NAME_1` 和 `SECRET_NAME_2`）作为参数来完成路径，例如：

```
- name: Use Secret
  run: SQLCMD -S MYSQLSERVER -U "$SECRET_NAME_1" -P "$SECRET_NAME_2"
```

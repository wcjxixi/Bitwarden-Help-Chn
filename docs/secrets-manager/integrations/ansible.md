# Ansible

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/ansible-integration/)
{% endhint %}

Bitwarden 提供与 Ansible 的集成，以从 Secrets Manager 中获取机密并将其注入到您的 Ansible playbook 中。lookup 插件会将获取到的机密作为隐藏的环境变量注入到 Ansible playbook 中。要设置集合：

## 要求 <a href="#requirements" id="requirements"></a>

* 我们建议在 [Python 虚拟环境](https://python.land/virtual-environments/virtualenv)中安装 Python 包。
* 您系统上已安装了 Ansible 的当前版本。
* 具有[活动的机器账户](../get-started/secrets-manager-quick-start.md#add-a-service-account)的 Bitwarden Secrets Manager。

在设置 Ansible 集合之前，我们建议您同时打开 Secrets Manager，以方便访问您的访问令牌以及您希望包含在设置中的任何机密。

## 安装 Bitwarden Ansible 集合 <a href="#install-the-bitwarden-ansible-collection" id="install-the-bitwarden-ansible-collection"></a>

以下指南是使用 Linux 机器设置 Bitwarden 集合的示例。

1、安装 Bitwarden SDK：

```bash
pip install bitwarden-sdk
```

2、安装 bitwarden.secrets 集合：

```bash
ansible-galaxy collection install bitwarden.secrets
```

现在 Ansible 集合已安装好，我们可以使用 `bitwarden.secrets.lookup` 从 Ansible playbook 中开始调用 Bitwarden 机密。以下部分将包含用于演示此过程的的示例。

{% hint style="info" %}
macOS 用户可能需要在 shell 中设置以下环境变量，以避免来自[上游的 Ansible 故障](https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#running-on-macos-as-a-control-node)。

* `export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES`
{% endhint %}

## 获取 Bitwarden 机密 <a href="#fetch-bitwarden-secrets" id="fetch-bitwarden-secrets"></a>

要从您的 playbook 中获取 Secrets Manager 中的机密，有两种方法：

### 将访问令牌保存为环境变量 <a href="#save-access-token-as-environment-variable" id="save-access-token-as-environment-variable"></a>

使用 Secrets Manager，我们可以将访问令牌安全地设置为 shell 中的环境变量，并使用 playbook 来检索机密。要[验证访问令牌](../get-started/developer-quick-start.md#authenticate)：

1、在 shell 中运行以下命令来设置您的访问令牌环境变量：

```bash
export BWS_ACCESS_TOKEN=<ACCESS_TOKEN_VALUE>
```

2、现在环境变量已经设置好，我们可以使用 lookup 插件来填充 playbook 中的变量。例如：

```yaml
  vars:
        database_password: "{{ lookup('bitwarden.secrets.lookup', '<SECRET_ID>') }}" 
```

{% hint style="info" %}
通过将 `BWS_ACCESS_TOKEN` 设置为环境变量，可以在 playbook 中引用访问令牌，而无需包含原始访问令牌值。
{% endhint %}

### 在 playbook 中提供访问令牌 <a href="#supply-access-token-in-playbook" id="supply-access-token-in-playbook"></a>

Secrets Manager 访问令牌也可以在 playbook 中被引用。这种方法不需要在您的 shell 中使用环境变量 `BWS_ACCESS_TOKEN` ，但访问令牌的值将存储在 playbook 中。

1、访问令牌可以包含在 playbook 中，示例如下：

```yaml
vars:
    password_with_a_different_access_token: "{{ lookup('bitwarden.secrets.lookup', '<SECRET_ID_VALUE>', 
access_token='<ACCESS_TOKEN_VALUE>') }}"     
```

使用此方法，可以在单个 playbook 中引用多个访问令牌。

## 从不同的服务器获取机密 <a href="#retrieve-secret-from-different-server" id="retrieve-secret-from-different-server"></a>

Bitwarden 自托管用户可以通过包含 `base_url,` `api_url` 和 `identity_url` 从他们的 Bitwarden 服务器中获取机密：

```yaml
vars:
    secret_from_other_server: "{{ lookup('bitwarden.secrets.lookup', '<SECRET_ID>', base_url='https://bitwarden.example.com' ) }}"
    secret_advanced: >-
      {{ lookup('bitwarden.secrets.lookup', '<SECRET_ID>',
        api_url='https://bitwarden.example.com/api',
        identity_url='https://bitwarden.example.com/identity' ) }}

```

## playbook 示例 <a href="#example-playbook" id="example-playbook"></a>

以下是一个具有多个配置选项的 playbook 文件的示例。

```yaml
---
- name: Using secrets from Bitwarden

  vars:
    bws_access_token: "{{ lookup('env', 'CUSTOM_ACCESS_TOKEN_VAR') }}"
    state_file_dir: "{{ '~/.config/bitwarden-sm' | expanduser }}"
    secret_id: "9165d7a8-2c22-476e-8add-b0d50162c5cc"

    secret: "{{ lookup('bitwarden.secrets.lookup', secret_id) }}"
    secret_with_field: "{{ lookup('bitwarden.secrets.lookup', secret_id, field='note' ) }}"
    secret_with_access_token: "{{ lookup('bitwarden.secrets.lookup', secret_id, access_token=bws_access_token ) }}"
    secret_with_state_file: "{{ lookup('bitwarden.secrets.lookup', secret_id, state_file_dir=state_file_dir ) }}"

  tasks:
    - name: Use the secret in a task
      include_tasks: tasks/add_db_user.yml # reference the secrets with "{{ secret }}", "{{ secret_with_field }}", etc.
```

{% hint style="info" %}
在上面的示例中，`CUSTOM_ACCESS_TOKEN_VAR` 演示了您可以包含多个不同的访问令牌。这些令牌不必是硬编码的，可以安全地提供给您的 playbook。
{% endhint %}

| 变量                         | 附加信息                                        |
| -------------------------- | ------------------------------------------- |
| `bws_access_token`         | 查找访问令牌 `env` 变量。                            |
| `state_file_dir`           | 一个可以缓存您的身份验证状态的目录。                          |
| `secret_id`                | 您希望查找的机密 ID。                                |
| `secret`                   | 查找一个机密值然后将其存储为名为 `"secret"` 的变量。            |
| `secret_with_field`        | 查找一个带有附加字段输出的机密。在这个例子中，查找将返回机密的 `'note'` 值。 |
| `secret_with_access_token` | 查找一个在请求中包含访问令牌值的机密。                         |
| `secret_with_state_file`   | 查找一个在请求中包含预配置状态文件的机密。                       |

## 附加请求和字段 <a href="#additional-requests-and-fields" id="additional-requests-and-fields"></a>

除了 `secret_id` 字段之外， `bitwarden.secrets.lookup` 中还可以包含其他好几个字段。以下 JSON 对象包含了在 playbook lookup 中可以引用的所有字段。

```json
{
  "id": "be8e0ad8-d545-4017-a55a-b02f014d4158",
  "organizationId": "10e8cbfa-7bd2-4361-bd6f-b02e013f9c41",
  "projectId": "e325ea69-a3ab-4dff-836f-b02e013fe530",
  "key": "SES_KEY",
  "value": "0.982492bc-7f37-4475-9e60",
  "note": "",
  "creationDate": "2023-06-28T20:13:20.643567Z",
  "revisionDate": "2023-06-28T20:13:20.643567Z"
}
```

要获取额外的字段，例如 `"note"` ，可以将以下命令添加到 playbook 中：

```yaml
  vars:
        database_password: "{{ lookup('bitwarden.secrets.lookup', '0037ed90-efbb-4d59-a798-b103012487a0', field='note') }}"
```

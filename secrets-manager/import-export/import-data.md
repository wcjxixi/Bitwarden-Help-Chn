# 导入数据

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/import-secrets-data/)
{% endhint %}

将数据导入您的机密密码库，以便从其他组织或机密管理解决方案轻松迁移。Secrets Manager 支持直接导入[机密](../your-secrets/secrets.md)和[工程](../your-secrets/projects.md)。无法导入[机器账户](../your-secrets/machine-accounts.md)和[访问令牌](../your-secrets/access-tokens.md)。

## 调整导入的文件 <a href="#condition-an-import-file" id="condition-an-import-file"></a>

Secrets Manager 当前支持将机密和工程作为 `.json` 文件直接导入。您的导入文件应根据以下架构和规则进行调整：

*   即使您只是导入机密，也必须包含一个空的数组对象 `"projects" :`，例如：

    ```javascript
    {
      "projects": [],
      "secrets": [
        {
          "key": "Secret for Import 1",
          "value": "this-is-my-value",
          "note": "These are some notes.",
          "id": "00000000-0000-0000-0000-000000000001",
          "projectIds": []
        },
        {
          "key": "Secret for Import 2",
          "value": "this-is-my-value",
          "note": "These are some notes.",
          "id": "00000000-0000-0000-0000-000000000002",
          "projectIds": []
        }
      ]
    }
    ```
* 目前，每一个机密只能与一个单独的工程相关联。
*   所有对象都必须具有与预期格式匹配的非空 `"id": ""` 属性。我们建议对第一个对象使用 `"00000000-0000-0000-0000-000000000001"`，并随着每个后续对象递增。导入时，将随机为每个对象生成新的标识符：

    ```javascript
    {
      "projects": [
        {
          "id": "00000000-0000-0000-0000-000000000001",
          "name": "New Project"
        },
        {
          "id": "00000000-0000-0000-0000-000000000002",
          "name": "Second New Project"
        }
      ],
      "secrets": [
        {
          "key": "Secret for Import",
          "value": "this-is-my-value",
          "note": "These are some notes.",
          "id": "00000000-0000-0000-0000-000000000003",
          "projectIds": []
        },
        {
          "key": "Second Secret for Import 2",
          "value": "this-is-my-value",
          "note": "These are some notes.",
          "id": "00000000-0000-0000-0000-000000000004",
          "projectIds": []
        }
      ]
    }
    ```
*   您可以使用 `"projectIds": ""` 属性将导入的机密与新导入的工程相关联：

    ```javascript
    {
      "projects": [
        {
          "id": "00000000-0000-0000-0000-000000000001",
          "name": "New Project"
        }
      ],
      "secrets": [
        {
          "key": "New Secret",
          "value": "this-is-my-value",
          "note": "This secret will go in the new project.",
          "id": "00000000-0000-0000-0000-000000000003",
          "projectIds": [
            "00000000-0000-0000-0000-000000000001"
          ]
        }
      ]
    } 
    ```

## 导入到 Secrets Manager <a href="#import-to-secrets-manager" id="import-to-secrets-manager"></a>

要将您的 `.json` 文件导入 Secrets Manager：

{% hint style="info" %}
要导入到 Secrets Manager，您的用户账户必须是组织内的所有者或管理员。
{% endhint %}

1、从左侧导航中选择**设置** → **导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1YQuiYqXIuYYG1TpXoSJoU/ccb036a10f2c5e7abf28aec1f772ee2b/Screenshot_2024-04-09_at_10.35.18_AM.png?_a=BAJFJtWIB" %}
导入数据
{% endembed %}

2、选择**选择文件**然后选择要导入的 `.json` 文件，或将要导入的内容复制并粘贴到输入框中。

3、选择**导入数据**按钮。根据提示，输入您的主密码。

{% hint style="danger" %}
导入不会检查要导入的文件中的对象是否已存在于您的密码库中。如果您导入多个文件或导入已包含您密码库中已有对象的文件，**这将创建重复项**。
{% endhint %}

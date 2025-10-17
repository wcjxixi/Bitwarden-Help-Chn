# 导入数据到个人密码库 & 集合

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/import-data/)
{% endhint %}

从不同的密码管理器、其他 Bitwarden 密码库或[加密导出](../../import-export/encrypted-exports.md)来导入登录和数据，即时传输信息，省去手动输入。您可以从任何允许导出的密码管理解决方案中导入数据。

## 常见密码管理器和文件类型导入 <a href="#common-password-manager-and-file-type-imports" id="common-password-manager-and-file-type-imports"></a>

Bitwarden 支持从许多常见的密码管理解决方案中导入数据，包括：

* [从 LastPass 导入](import-guides/import-data-from-lastpass.md)
* [从 1Password 导入](import-guides/import-data-from-1password.md)
* [从 Firefox 导入](import-guides/import-data-from-firefox.md)
* [从 Google Chrome、Edge 或 Chromium 导入](import-guides/import-data-from-chrome.md)
* [从 Password Safe 导入](../../import-export/import-guides/import-data-from-password-safe.md)
* [从其他 Bitwarden 密码库导入](../../import-export/export-vault-data.md)

来自其他密码管理器的[其他文件类型](../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)与 Bitwarden 兼容。如果您的解决方案未在列表中，但可以导出数据，请编辑文件以匹配[受支持的格式](../../import-export/condition-a-bitwarden-.csv-or-.json.md)。

{% hint style="success" %}
[将数据导入组织](../../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md)，以便大型团队共享。对于较小的团队，可[导入到集合](import-data.md#import-to-a-collection)。
{% endhint %}

{% hint style="info" %}
虽然某些项目类型无法导入，但您仍可将其添加到密码库：

* 将[文件附件](../../your-vault/file-attachments.md)单独上传到新的密码库。
* 在新的密码库中重新创建 [Send](../../bitwarden-send/about-send.md)。
{% endhint %}

## 导入到您的个人密码库 <a href="#import-to-your-personal-vault" id="import-to-your-personal-vault"></a>

数据可以从网页密码库、CLI、桌面 App 或浏览器扩展导入到 Bitwarden。数据在发送到服务器存储之前会在本地进行[加密](../../security/encryption/encryption-protocols.md)。要导入您的数据：

{% tabs %}
{% tab title="网页 App" %}
要将数据导入到您的密码库：

1、选择**工具**。

2、选择**导入数据**：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/1NbyPb9dN545ZqKGRZYB3x/7ed2e5650e9988bf7595bccebe8a5114/2024-12-03_08-52-08.png?_a=DAJCwlWIZAAB" %}
导入数据
{% endembed %}

3、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**或（可选）选择移动到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(需要[**可以管理**](../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

4、从**文件格式**下拉菜单中，选择[导入文件的格式](../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

5、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查重复。如果您多次导入同一文件或导入的项目已经存在于密码库中，则会创建重复的项目。
{% endhint %}

6、选择**导入数据**。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="浏览器扩展" %}
要将数据导入到您的密码库：

1、选择**设置**。

2、选择**密码库选项**。

3、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**或（可选）选择移动到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(需要[**可以管理**](../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

4、从**文件格式**下拉菜单中，选择[导入文件的格式](../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

5、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件将创建重复项目。
{% endhint %}

6、选择**导入数据**。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="移动 App" %}
在大多数情况下，在移动设备上导入数据需要通过在打开了网页 App 的移动浏览器中进行。您可以从 Password Manager 导航到**设置** → **密码库** → **导入项目**，快速到达该位置。

在 iOS 26 上，Bitwarden 支持使用 [Fido 凭证交换协议 (CXP)](https://fidoalliance.org/specifications-credential-exchange-specifications) 进行导入，以便直接、轻松地将凭证迁移到密码库中。您要从其导入的 App 也必须支持 CXP，导入步骤因应用程序而异。

例如，在 iOS 密码 App 上，使用 **⋯**&#x9009;项菜单选择**将数据导出到其他 App**，然后选择 Bitwarden。
{% endtab %}

{% tab title="桌面 App" %}
要将数据导入到您的密码库：

1、选择**文件**。

2、选择**导入数据**。

3、从**密码库**下拉菜单中，选择数据的保存目的地：

* **个人密码库**：选择**我的密码库**或（可选）选择移动到的**文件夹**。
* **组织密码库**：选择组织密码库名称然后选择一个**集合**。(需要[**可以管理**](../../admin-console/manage-shared-items/collections/about-collections.md#collections-permissions)权限）。

4、从**文件格式**下拉菜单中，选择[导入文件的格式](../../import-export/import-and-export-faqs.md#q-what-file-formats-does-bitwarden-support-for-import)。

5、选择**选择文件**然后选取一个文件，或将文件内容复制并粘贴到文本框中。

{% hint style="danger" %}
导入过程不会检查要导入的文件中的项目是否已存在于您的密码库中，因此多次导入文件或导入具有已存在于密码库中的项目的文件将创建重复项目。
{% endhint %}

6、选择**导入数据**。如果您要导入受密码保护的 .`json` 文件，请在出现的**确认密码库导入**窗口中输入密码。

7、成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}

{% tab title="CLI" %}
要将数据导入到您的密码库，请使用以下命令：

```batch
bw import <format> <path>
```

`bw import` 命令需要格式（使用 `bw import --formats` 获取格式列表）和路径，例如：

```batch
bw import lastpasscsv /Users/myaccount/Documents/mydata.csv
```

成功导入后，从您的计算机中将导入源文件删除。这将在您的计算机受到威胁时为您提供保护。
{% endtab %}
{% endtabs %}

## 导入到集合 <a href="#import-to-a-collection" id="import-to-a-collection"></a>

将数据导入集合，以与您的家人或直接队友等小型团队组织并共享项目。（对于较大的团队，[将数据导入组织](../../admin-console/manage-shared-items/import-organization-items/import-data-to-an-organization.md)）。当您组织的[数据所有权策略](../../admin-console/oversight-visibility/enterprise-policies.md#enforce-organization-data-ownership)限制个人密码库时，个人集合是一个很好的选择。

在**导入数据**页面，选择您组织的**密码库**然后选择**集合**：

{% embed url="https://bitwarden.com/assets/5i5K8TyWXdbpJLNlsfyd3v/2856adec442a941dfb67f58afb262da9/2025-05-07_13-14-59.png?w=650&fm=avif&q=80" %}
导入到个人密码库
{% endembed %}

## 导入错误故障排除 <a href="#troubleshoot-import-errors" id="troubleshoot-import-errors"></a>

如果超过限制或文件中包含未分配的项目，您将看到一个「导入错误」的消息。导入被拒绝时，不会将数据添加到您的密码库中。

### 文件限制 <a href="#file-limits" id="file-limits"></a>

导入的文件最多可包含：

* 4,000 个项目。
* 2,000 个文件夹。
* 2,000 个集合。
* 7,000 个项目-文件夹关系（例如，1 个项目存在于 3 个文件夹中，可以算作 3 个项目 - 文件夹关系）。
* 8,000 个项目-集合关系（例如，1 个项目存在于 3 个集合中，可以算作 3 个项目 - 集合关系）。

如果您的文件太大，请将其拆分为较小的文件然后分别导入。

### 字段长度限制 <a href="#field-length-limits" id="field-length-limits"></a>

如果文件（通常是 `.csv`）中的某个项目超过了字段的**加密**字符限制，Bitwarden 将不会导入其中的任何内容。系统将显示一个「导入错误」的消息，并详细说明具体的问题。

{% hint style="success" %}
导入时，Bitwarden 的加密过程会将文本扩展 30-50%，这可能会使您的字段超出字符限制。例如，最常见的`备注`字段可能会从 8,000 个字符增加到超过 10,000 个字符，从而超出限制并引发错误。
{% endhint %}

要修复此错误并上传数据：

1. 在文本编辑器或电子表格程序中打开 `.csv` 文件。
2. 查看错误信息的详细信息，找出导致问题的项目。例如，我们来解释以下错误：\
   `[2] [Login] “My New Item”: The field Notes exceeds the maximum encrypted value length of 10000 characters.`
   * `[2]` 标识违规项目所在的索引号，该索引号已调整为与大多数电子表格程序中的行号匹配
   * `[Login]` 标识违规项目的项目 `type`（类型）
   * `"My New Item"` 标识违规项目的 `name`（名称）
   * `Notes` 标识超出了字符数限制的字段（列）
   * `10000` 标识该字段（列）允许的字符数限制
3. 减少字符数或删除违规项目。
4. 保存文件。
5. 返回 Bitwarden 然后[导入更新后的文件](import-data.md#import-to-your-personal-vault)。

### 文件包含未分配的项目 <a href="#https-bitwarden.com-help-import-data-file-contains-unassigned-items" id="https-bitwarden.com-help-import-data-file-contains-unassigned-items"></a>

组织用户（不是[管理员或所有者](../../admin-console/manage-members/member-roles.md#member-roles)）必须将所有导入的凭证分配给至少一个集合。有两种方法可以解决此导入错误：

* 分配一个您拥有**可以管理**权限的现有集合。
* 为未指定的项目创建一个新的集合。通过输入一个新的集合名称来[自定义导入文件](../../import-export/condition-a-bitwarden-.csv-or-.json.md)。这将自动创建该集合并将项目添加到其中。

{% hint style="success" %}
要最大限度地减少此错误，请启用[限制为所有者和管理员可以创建集合](../../admin-console/manage-shared-items/collections/collection-settings.md#restrict-collection-creation-to-owners-and-admins)设置以阻止用户创建集合。
{% endhint %}

### 组织最多只能拥有俩个集合 <a href="#organization-can-only-have-a-maximum-of-two-collections" id="organization-can-only-have-a-maximum-of-two-collections"></a>

免费组织最多可以拥有两个[集合](../../admin-console/manage-shared-items/collections/about-collections.md)。如果您尝试导入的文件指定了两个以上的集合，则会出现导入错误。有几个选项可以纠正这个问题：

* 如果您尝试导入 `.csv` 或 `.json`，请[编辑该文件](../../import-export/condition-a-bitwarden-.csv-or-.json.md)以删除附加的集合。
* 升级您的计划，以便您可以创建更多集合并按原样导入文件。

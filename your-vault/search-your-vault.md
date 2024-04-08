# 检索密码库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/searching-vault/)
{% endhint %}

Bitwarden 密码库可以很容易地检索到相关的密码库项目。[基本检索](search-your-vault.md#applications-that-use-full-text-search)查询可以在任何 Bitwarden 客户端应用程序中使用，高级的[全文检索](search-your-vault.md#applications-that-use-full-text-search-1)查询可以在网页密码库、桌面应用程序和浏览器扩展中使用。

任何检索操作的潜在结果都取决于当前通过筛选器菜单或导航打开的内容。例如：

* 如果选择了 **☷所有项目**，则输入的检索查询将使用所有可能的密码库项目作为潜在结果。
* 如果选择的类型为**登录**，则输入的检索查询将使用所有登录项目作为潜在结果。
* 如果选择了**我的文件夹**，则输入的检索查询将使用该文件夹中的所有项目作为潜在结果（不包括[嵌套文件夹](folders.md)中的项目）。

检索框中的占位符文本将转换为指示当前检索的位置：

<figure><img src="https://res.cloudinary.com/bw-com/image/upload/f_auto/e_vectorize/q_auto/f_svg/v1/ctf/7rncvj1f8mw7/2Mdb392zQHEfC44zhwLmGl/60b1d764cbaefcc3b5c5614186c31338/Screenshot_2024-02-27_at_11.14.14_AM.png?_a=BATAUVAA0" alt=""><figcaption><p>搜索文件夹</p></figcaption></figure>

## 基本检索 <a href="#applications-that-use-full-text-search" id="applications-that-use-full-text-search"></a>

基本检索在所有 Bitwarden 客户端应用程序中均可使用。输入基本检索查询（例如 `Github` 或 `myusername`）将在密码库项目的以下字段中检索输入的字符串：

* 项目**名称**
* 对于登录为**用户名**
* 对于登录为 **URI**
* 对于支付卡为**品牌**或**数字**后四位
* 对于身份为**名称**

为方便您的使用，基本检索会自动包含前导和后导[通配符](search-your-vault.md#wildcards-and-advanced-search-parameters)。例如，检索 `mail` 将返回名称为 `gmail` 的密码库项目以及 `email`。

## 全文检索 <a href="#applications-that-use-full-text-search" id="applications-that-use-full-text-search"></a>

网页密码库库、桌面应用程序和浏览器扩展中的检索自动为[全文搜索](https://zh.wikipedia.org/wiki/%E5%85%A8%E6%96%87%E6%AA%A2%E7%B4%A2)，并且与基本检索一样，自动包括前导通配符和后导通配符。当在全文检索中找不到结果时，Bitwarden 将回退到基本检索。

### 索引字段 <a href="#indexed-fields" id="indexed-fields"></a>

全文搜索将为每个密码库项目搜索以下字段：：

* `shortid`：项目 ID 的前 8 个字符。
* `organizationid`：项目的组织 ID（如果它属于其中一个）。
* `name`：项目指定的名称。
* `subtitle`：取决于项目类型；登录为**用户名**，支付卡为**品牌**或后**数字**四位，以及身份为**名称**。
* `notes`：项目的备注。
* `fields`：名称和值。**仅包含`文本`类型字段值**。
* `attachments`：附件文件的名称。
* `login.username`：登录项目的用户名。
* `login.uris`：登录项目的 URI [主机名](https://developer.mozilla.org/en-US/docs/Web/API/HTMLHyperlinkElementUtils/hostname)的值。

### 检索特定字段 <a href="#searching-specific-fields" id="searching-specific-fields"></a>

您可以使用「大于」(`>`) 符号来开始检索查询，并按以下格式指示先前列出的字段，来检索特定字段中的数据：

* `>login.username:jsmith`：将检索**用户名**被指定为 `jsmith` 的登录项目。
* `>name:Turbo Tax`：将检索**名称**被指定为 `Turbo Tax` 的任何密码库项目。
* `>fields:Security Question`：将检索具有**名称**为 `Security Question` 的自定义文本字段的任何密码库项目。

### 通配符和高级检索参数 <a href="#wildcards-and-advanced-search-parameters" id="wildcards-and-advanced-search-parameters"></a>

检索特定字段时，您可以使用星号 (`*`) 作为特定检索值的通配符，例如：

* `>organizationid:*`：将检索属于组织的任何密码库项目。
* `>-organizationid:*`：将检索不属于组织的任何密码库项目。
* `>login.username:*@gmail.com`：将检索**用户名**以 `@gmail.com` 结尾的任何密码库项目。

{% hint style="success" %}
除通配符外，[Lunr](https://lunrjs.com/) 还提供了多种高级查询选项，包括：

* **术语组合**：使用 `+`（_必须包含_）或 `-`（_必须不包含_）前缀。\
  例如，如果你有多个 Gmail 账户，检索 `>name:Gmail -Work` 将会返回名为 `Personal Gmail` 的密码库项目，但不会返回名为 `Work Gmail` 的密码库项目。
* **模糊匹配**：使用波浪号 (`~`) 前缀结合一个编辑距离的整数。\
  例如，搜索 `>name:email~1` 将返回名称为 `email` 的密码库项目**以及**名称为 `gmail` 的密码库项目。

使用 [Lunr 搜索指南](https://lunrjs.com/guides/searching.html)了解更多关于编写高级检索查询的信息。
{% endhint %}

# 自动填充自定义字段

{% hint style="info" %}
对应的[官方文档地址](https://bitwarden.com/help/article/auto-fill-custom-fields/)
{% endhint %}

Bitwarden 可以做的不仅仅是[自动填充您的用户名和密码](auto-fill-logins-in-browser-extensions.md)！**Bitwarden 浏览器扩展**可以使用[独特的标签页视图](auto-fill-logins-in-browser-extensions.md)自动填充[自定义字段](../vault-basics/custom-fields.md)，以简化安全问题、PIN 等的填充。

此外，如果您的浏览器扩展在自动填充特定站点的用户名和密码时遇到问题，使用[链接型自定义字段](<Auto-fill Custom Fields.md#shi-yong-lian-jie-de-zi-ding-yi-zi-duan>)可以强制自动填充。

## 自动填充自定义字段 <a href="#auto-fill-custom-fields" id="auto-fill-custom-fields"></a>

{% hint style="success" %}
要使自动填充起作用，对自定义字段正确命名很重要。[了解更多](../vault-basics/custom-fields.md#custom-field-names)。
{% endhint %}

要自动填充自定义字段：

1、打开浏览器扩展，或者如果您的浏览器扩展已经打开，请导航到 **📁标签页**视图。

标签页视图会自动检测打开的标签页中显示的网页的 URI（例如 myverizon.com），并浮现所有具有相应 URI 的密码库项目。

2、选择包含要自动填充的自定义字段的项目：

{% embed url="https://bitwarden.com/help/images/autofill/auto-fill-custom-field.png" %}
带有自定义字段的项目
{% endembed %}

浏览器扩展将查找与[自定义字段名称](../vault-basics/custom-fields.md#custom-field-names)匹配的任何字段并自动填充该字段的值。

### 使用链接型自定义字段 <a href="#using-linked-custom-fields" id="using-linked-custom-fields"></a>

链接型自定义字段可用于解决浏览器扩展无法自动填充特定站点的用户名和密码时的问题。要创建和自动填充链接型自定义字段：

1、在密码库项目的**编辑项目**面板的**自定义字段**部分，从下拉列表中选择**链接型**然后选择 **🞤新建自定义字段**：

{% embed url="https://bitwarden.com/help/images/features/linked-custom-field.png" %}
链接型自定义字段
{% endembed %}

2、在**名称**输入框中，[为自定义字段指定一个名称](../vault-basics/custom-fields.md#custom-field-names)，使其与用户名或密码的 HTML 表单元素 `id`，`name`，`aria-label` 或 `placeholder` 相对应。

您可以通过右键单击表单元素并使用**复制自定义字段名称**上下文菜单选项来获取其正确的值：

{% embed url="https://bitwarden.com/help/images/features/custom-fields-contextmenu.png" %}
复制自定义字段名称
{% endembed %}

3、从**值**下拉列表中，根据您在自动填充时遇到问题的凭据类型选择**用户名**或**密码**。在许多情况下，您需要为每个类型创建一个链接型自定义字段。

4、**保存**对密码库项目的更改。

现在您已经创建了一个或多个链接型自定义字段，您可以使用[前面部分中描述的方法](<Auto-fill Custom Fields.md#auto-fill-custom-fields>)自动填充了。当您操作时，您的浏览器扩展将自动填充用户名、密码或两者到为字段名称指定的 HTML 表单元素中。

## 特殊自动填充场景 <a href="#special-auto-fill-scenarios" id="special-auto-fill-scenarios"></a>

### HTML `<span>` 元素 <a href="#html-span-elements" id="html-span-elements"></a>

自定义字段通常被填充到 HTML `<form>` 或 `<input>` 元素中，但是 Bitwarden 浏览器扩展也可以将自定义字段值自动填充到 HTML `<span>` 元素的 `innerText` 中。

为了自动填充到 `<span>` 元素中，打开的标签页必须具有 `data-bwautofill` 属性。因此，在以下场景中：

```html
<span data-bwautofill id="myspan">Bitwarden is great.</span>
```

具有**名称**为 `myspan` 的自定义字段将用自定义字段的**值**中保存的任何内容替换 `Bitwarden is great`。

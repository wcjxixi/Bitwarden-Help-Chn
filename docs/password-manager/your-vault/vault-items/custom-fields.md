# 自定义字段

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/custom-fields/)
{% endhint %}

自定义字段可在任何[项目类型](vault-items.md)上使用，使您可以在密码库项目中存储额外的结构良好的数据字段。自定义字段保存为 `Name:Value` 对，它可以是这三种类型之一：

* **文本型**：存储自由格式的输入（文本、数字等）的字段值
* **隐藏型**：存储从视图中隐藏的自由格式输入的字段值（对于使用[隐藏密码访问控制](../../../admin-console/manage-members/member-roles.md)的组织特别有用）
* **布尔型**：存储布尔值（真/假）的字段值
* **链接型**：链接到项目的用户名或密码的字段值。指定[正确的字段名称](custom-fields.md#custom-field-names)后，链接型自定义字段可用于解决浏览器扩展无法自动填充特定站点的用户名和密码的问题（[了解更多](../../autofill/more-autofill-options/auto-fill-custom-fields.md#using-linked-custom-fields)）。

{% hint style="success" %}
### 用于密钥的自定义字段 <a href="#custom-fields-for-keys" id="custom-fields-for-keys"></a>

除了常见的网页服务输入（例如 PIN 和安全问题）外，自定义字段还可用于存储**长度最多 5000 个字符**的值，例如 RSA 4096 位 SSH 密钥。

自定义字段值的字符限制是根据**加密后的字符数量**来计算的。例如，一个 3383 个字符的 RSA-4096 私有 SSH 密钥在加密并存储在你的密码库中时将增长到约 4400 个字符。
{% endhint %}

## 创建自定义字段 <a href="#creating-custom-fields" id="creating-custom-fields"></a>

可以在任何 Bitwarden 客户端中使用**编辑项目**面板中的**自定义字段**部分将自定义字段添加到密码库项目：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/NoGCwyAZcnzss1EeYXKD1/23a7e619dfdcb4baa023f54923335050/2024-12-02_14-52-43.png?_a=DAJCwlWIZAAB" %}
网页 App 中的自定义字段
{% endembed %}

### 自定义字段名称 <a href="#custom-field-names" id="custom-field-names"></a>

指定的**名称**对于成功[自动填充自定义字段](../../autofill/more-autofill-options/auto-fill-custom-fields.md)很重要。对于浏览器扩展，您可以使用上下文菜单中的**复制自定义字段名称**选项快速获取正确的字段名称（在大多数情况下，通过右键单击表单元素）：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/5nnPLqyzgAhDCinQNB0uUC/a721194f39f0a8fa919066d73ff9e2c8/2024-10-29_10-50-34.png?_a=DAJCwlWIZAAB" %}
复制自定义字段名称
{% endembed %}

选择此上下文菜单选项将复制表单元素的 `id`、`name`、`aria-label` 或 `placeholder` 的值（按优先顺序）。

保存自定义字段后，您可以[从浏览器扩展中自动填充它](../../autofill/more-autofill-options/auto-fill-custom-fields.md)。

#### 手动查找自定义字段名称 <a href="#find-custom-field-names-manually" id="find-custom-field-names-manually"></a>

如果您不使用浏览器扩展，查找字段名称的最佳方法是使用网页浏览器的开发人员工具，如下面的示例所示：

{% embed url="https://vimeo.com/1139125687?fl=pl&fe=sh" %}

要定位自定义字段名称：

1、在带有自定义字段的网页上，右键单击要自动填充的字段并选择**检查**。HTML 元素将打开并在开发人员控制台中突出显示。

2、查找并复制元素 `id`（查找 `id="xxx"`，其中 `xxx` 是元素的 `id` 值）。

3、在对应的密码库项目的**自定义字段**部分，选择适当的字段类型，然后选择 ✚**新增自定义字段**按钮：

4、在**名称**字段中粘贴已复制的元素 `id`。

5、在**值**字段中指定需要自动填充的信息（在上例中为电话号码）。

6、保存此密码库项目。

保存自定义字段后，您可以[从浏览器扩展中自动填充它](../../autofill/more-autofill-options/auto-fill-custom-fields.md)。

### 更多关于自定义字段名称 <a href="#more-about-custom-field-names" id="more-about-custom-field-names"></a>

#### 优先顺序 <a href="#order-of-preference" id="order-of-preference"></a>

如果您手动命名自定义字段，则应**按优先顺序**使用以下 HTML 表单元素属性/值之一：

1. HTML 表单元素的 `id` 属性
2. HTML 表单元素的 `name` 属性
3. HTML 表单元素的 `aria-label` 属性
4. HTML 表单元素的 `placeholder` 属性

#### 匹配 <a href="#matching" id="matching"></a>

字段名称的匹配是**精确**且**不区分大小写**的。例如，假如您的自定义字段的名称为 `PIN`：

* **提供自动填充**：对于 `pin`、`Pin`、`PIN` 等
* **不提供自动填充**：对于 `pin2` 或 `mypin`&#x20;

#### 前缀 <a href="#prefixing" id="prefixing"></a>

在两种情况下，您可以通过使用前缀对[匹配](custom-fields.md#matching)进行更多控制：

* **CSV**：使用 `csv=` 作为自定义字段名称的前缀，允许您指定多个名称来检索和比较以进行自动填充，例如 `csv=pin,mypin,pincode`。
* **正则表达式**：使用 `regex=` 作为自定义字段名称的前缀，将允许您在执行自动填充时执行[正则表达式](https://regexone.com/)比较。例如，`regex=^first.*name` 将为 `firstName`、`First_name` 和 `First Name` 提供自动填充。

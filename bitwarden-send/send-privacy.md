# Send 隐私

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/send-privacy/)
{% endhint %}

通过选择性的配置[访问密码](send-privacy.md#send-passwords)来保护您的 Send 内容，以防止无意的接收者看到其包含的信息，和/或[对接收者隐藏您的单子邮件](send-privacy.md#hide-email)。对于文本 Send，您还可以选择性地要求接收者[切换可见性](send-privacy.md#hide-text)，以防止暴露给无意的旁人。

**密码**、**隐藏电子邮件**和**隐藏文本**选项可在[删除](send-lifespan.md#deletion-behavior) Send 之前的任何时候，通过创建新 Send 视图或编辑 Send 视图进行配置。

## Send 密码 <a href="#send-passwords" id="send-passwords"></a>

对于任何 Send，您可以配置一个密码，接收者必须输入该密码才能访问其内容。使用密码保护 Send 是一种确保 Send 的内容不会暴露给意外的接收者的好方法：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/7DyqQ9YHNrAIvmlyDrOCmr/3de34755ad0fe2081fd34f63a79c08f6/send-pw-protected.png?fm=webp&h=390&q=50&w=403" %}
接收受密码保护的 Send
{% endembed %}

对 Send 进行密码保护后，您将无法再次查看已配置的密码，但是您可以随时[更改](send-privacy.md#change-send-passwords)或[移除](send-privacy.md#remove-send-passwords)它：

### 更改 Send 密码 <a href="#change-send-passwords" id="change-send-passwords"></a>

您可以随时在**编辑 Send** 视图中更改 Send 密码。更改 Send 密码**不会**要求您输入以前的密码。更改 Send 密码时，**密码**字段将更改为**新密码**：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/2cvuNz0NAQfyYTNHjGjZ3X/9937450f4c0cd252be13387c691e5717/send-new-pw.png?fm=webp&h=143&q=50&w=609" %}
设置 Send 密码
{% endembed %}

### 移除 Send 密码 <a href="#remove-send-passwords" id="remove-send-passwords"></a>

您可以随时使用 **⟲移除密码**菜单选项移除 Send 密码。移除 Send 密码**不会**要求您输入以前的密码。

## 隐藏电子邮件 <a href="#hide-email" id="hide-email"></a>

{% hint style="success" %}
对于企业组织，可以使用[企业策略](../organizations/enterprise-policies.md#send-options)设置此选项的可用性。
{% endhint %}

默认情况下，Send 对象将对接收者显示发送者的电子邮件地址：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3vaNmg2BXTYZ4L0g0nrIO5/e10bb70d2192d5e3ebc6279b796a4b52/send-email-visible.png?fm=webp&h=271&q=50&w=508" %}
发送者的电子邮件地址可见性
{% endembed %}

切换**对接收者隐藏我的电子邮件地址**选项，以从 Send 对象中移除您的电子邮件地址。Send 接收者可以通过将 **Send 链接**与其发送者交叉对比，来验证预期 Send 对象的可信度。隐藏了电子邮件的 Send 对象将向接收者发出警告，鼓励他们这样做：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/3lA2tlmm169K8S7DBw2ExF/79ad57ee7b3edb8eab5158d76c24b2fc/send-email-hidden.png?fm=webp&h=358&q=50&w=673" %}
发送者的电子邮件地址已隐藏
{% endembed %}

## 隐藏文本 <a href="#hide-text" id="hide-text"></a>

对于文本 Send，切换到**当访问 Send 时，默认隐藏文本**选项，以要求接收者 **👁‍🗨切换可见性**才能查看其内容。隐藏 Send 中的文本是一个很好的方法，它可以确保 Send 的内容不会暴露给无意的旁人：

{% embed url="https://images.ctfassets.net/7rncvj1f8mw7/4KcdIWqSnADnv1TMtsrSIr/c5933c2818d1132b38a79f5af3a9ed1a/send-hidden-text.png?fm=webp&h=530&q=50&w=380" %}
接收隐藏文本的 Send
{% endembed %}

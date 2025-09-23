# Send 隐私

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/article/send-privacy/)
{% endhint %}

通过选择性的配置[访问密码](send-privacy.md#send-passwords)来保护您的 Send 内容，以防止无意的接收者看到其包含的信息，和/或[对接收者隐藏您的单子邮件](send-privacy.md#hide-email)。对于文本 Send，您还可以选择性地要求接收者[切换可见性](send-privacy.md#hide-text)，以防止暴露给无意的旁人。

**密码**、**隐藏电子邮箱**和**隐藏文本**选项可在[删除](send-lifespan.md#deletion-behavior) Send 之前的任何时候，通过创建新 Send 视图或编辑 Send 视图进行配置。

## Send 密码 <a href="#send-passwords" id="send-passwords"></a>

对于任何 Send，您可以配置一个密码，接收者必须输入该密码才能访问其内容。使用密码保护 Send 是一种确保 Send 的内容不会暴露给意外的接收者的好方法：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/7DyqQ9YHNrAIvmlyDrOCmr/7969dc096a4612773a8c0a15dc2375dc/2024-12-03_10-43-18.png?_a=DAJCwlWIZAAB" %}
接收受密码保护的 Send
{% endembed %}

对 Send 进行密码保护后，您将无法再次查看已配置的密码，但是您可以随时[更改](send-privacy.md#change-send-passwords)或[移除](send-privacy.md#remove-send-passwords)它：

### 更改 Send 密码 <a href="#change-send-passwords" id="change-send-passwords"></a>

您可以随时在**编辑 Send** 视图中更改 Send 密码。更改 Send 密码**不会**要求您输入以前的密码。更改 Send 密码时，**密码**字段将更改为**新密码**。

### 移除 Send 密码 <a href="#remove-send-passwords" id="remove-send-passwords"></a>

您可以随时使用 **⟲移除密码**菜单选项移除 Send 密码。移除 Send 密码**不会**要求您输入以前的密码：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/6y6TJ0P7YbMza7p90kxu6X/929e10a4eac5d842b4cf283d46a41824/2024-12-03_10-09-52.png?_a=DAJCwlWIZAAB" %}
Send 选项
{% endembed %}

## 隐藏电子邮箱 <a href="#hide-email" id="hide-email"></a>

{% hint style="success" %}
对于企业组织，可以使用[企业策略](../admin-console/manage-shared-items/enterprise-policies.md#send-options)设置此选项的可用性。
{% endhint %}

默认情况下，Send 对象将对接收者显示发送者的电子邮箱地址：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/47RPmr6xOowzjJbG6JxVG3/98c803df88adcde39c96331cf34ab106/2024-12-03_10-23-03.png?_a=DAJCwlWIZAAB" %}
隐藏了电子邮箱的文本 Send
{% endembed %}

切换**对接收者隐藏我的电子邮箱地址**选项，以从 Send 对象中移除您的电子邮箱地址。Send 接收者可以通过将 **Send 链接**与其发送者交叉对比，来验证预期 Send 对象的可信度。隐藏了电子邮箱的 Send 对象将向接收者发出警告，鼓励他们这样做。

## 隐藏文本 <a href="#hide-text" id="hide-text"></a>

对于文本 Send，切换到**当访问 Send 时，默认隐藏文本**选项，以要求接收者 **👁‍🗨切换可见性**才能查看其内容。隐藏文本是一个很好的方法，它可以确保内容不会暴露给无意的旁人：

{% embed url="https://res.cloudinary.com/bw-com/image/upload/f_auto/v1/ctf/7rncvj1f8mw7/4KcdIWqSnADnv1TMtsrSIr/09abc9e81ae3bf64e7cd42c2916ef87a/2024-12-03_10-45-49.png?_a=DAJCwlWIZAAB" %}
接收隐藏文本的 Send
{% endembed %}

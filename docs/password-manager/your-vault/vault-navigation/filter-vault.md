# 筛选密码库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/filter-your-vault/)
{% endhint %}

筛选您的密码库将控制哪些项目会显示在密码库中或密码库视图中。要筛选密码库：

{% tabs %}
{% tab title="网页 App" %}
任选一个：

* 从**筛选器**列中选择一个特征（在下面的屏幕截图中，为**登录**）。
* 选择项目旁边的彩色卡片之一（在下面的屏幕截图中，为**我**或**我的组织**）。

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/1UhfLlwmahJgbi0bcBtPLT/b4b1875602b0ea555626c98a388779b8/2024-12-02_14-23-39.png?w=1038&#x26;fm=avif" alt=""><figcaption><p>网页 App 筛选器</p></figcaption></figure></div>
{% endtab %}

{% tab title="浏览器扩展" %}
使用 **🔒密码库**选项卡顶部的**密码库**、**集合**、**文件夹**或**类型**选择器。您可以使用 **☷**&#x6309;钮切换筛选器下拉菜单的可见性：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/12UsFuA2sxbUCBMIczJsxv/689221013fac56ddb555ed9dabddbdc9/screenshot_6.png?w=584&#x26;fm=avif" alt=""><figcaption><p>浏览器扩展筛选器和建议</p></figcaption></figure></div>
{% endtab %}

{% tab title="移动端" %}
通过选择**密码库**选项卡上的**密码库**菜单按钮 (**⋯**) 来选择一个密码库：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/44WqYfqzP9JOJPSZ4Yrzjb/9167f19bc2e27a158be5ed3fc29a5689/2025-01-21_15-38-59.png?w=714&#x26;fm=avif" alt=""><figcaption><p>移动 App 筛选器</p></figcaption></figure></div>
{% endtab %}

{% tab title="桌面端" %}
从最左边的列中选择筛选条件：

<div align="left" data-with-frame="true"><figure><img src="https://bitwarden.com/assets/2Lng0L2TRQ177CaU8EUQ1m/650d82f70422611353ce70a347a99c72/2026-04-23_10-14-43.png?w=800&#x26;fm=avif" alt=""><figcaption><p>桌面 App 筛选器</p></figcaption></figure></div>
{% endtab %}

{% tab title="CLI" %}
使用带有 `--organizationid` 选项的 `bw list` 命令，可以按密码库列出项目。该选项可以接受组织标识符或 `null` 值。[了解更多](../../developer-tools/cli/password-manager-cli.md#list)。
{% endtab %}
{% endtabs %}
